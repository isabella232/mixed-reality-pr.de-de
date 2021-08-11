---
title: Volumengrafik
description: Erfahren Sie, wie Sie umfangreiche volumetrische Bilder mit Deckkraft und Farbe in Windows Mixed Reality effizient rendern.
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: volumetrisches Bild, Volumerendering, Leistung, Mixed Reality
ms.openlocfilehash: 3843f0f4e49a0564b41d834231630d281aa9e874df8d35c4feaa4fe5bba0ed68
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220928"
---
# <a name="volume-rendering"></a>Volumengrafik

Informationen zu medizinischen MRI- oder Engineering-Volumes finden Sie unter [Volume Rendering auf Wikipedia.](https://en.wikipedia.org/wiki/Volume_rendering) Diese "volumetrischen Bilder" enthalten umfassende Informationen mit Deckkraft und Farbe im gesamten Volume, die nicht einfach als Oberflächen wie [polygonale Gitternetze](https://en.wikipedia.org/wiki/Polygon_mesh)ausgedrückt werden können.

Wichtige Lösungen zur Verbesserung der Leistung
1. BAD: Naïve Approach: Show Whole Volume, generally runs too slowly
2. GUT: Schnittebene: Nur einen einzelnen Slice des Volumes anzeigen
3. GOOD: Cutting Sub-Volume: Nur wenige Ebenen des Volumes anzeigen
4. GUT: Verringern Sie die Auflösung des Volumerenderings (siehe "Szenenrendering mit gemischter Auflösung")

Es gibt nur eine bestimmte Menge an Informationen, die von der Anwendung auf den Bildschirm in einem bestimmten Frame übertragen werden können, d. h. die Gesamtspeicherbandbreite. Außerdem erfordert jede Verarbeitung (oder Schattierung), die zum Transformieren dieser Daten für die Darstellung erforderlich ist, Zeit. Die wichtigsten Aspekte beim Rendern von Volumes sind folgende:
* Screen-Width * Screen-Height * Screen-Count * Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame
* 1028 * 720 * 2 * 256 = 378961920 (100 %) (Vollständiges Res-Volume: zu viele Beispiele)
* 1028 * 720 * 2 * 1 = 1480320 (0,3 % voll) (schlankes Slice: 1 Stichprobe pro Pixel, wird reibungslos ausgeführt)
* 1028 * 720 * 2 * 10 = 14803200 (3,9 % voll) (teilvolumiger Slice: 10 Stichproben pro Pixel, verläuft ziemlich reibungslos, sieht 3d aus)
* 200 * 200 * 2 * 256 = 20480000 (5 % voll) (geringeres Res-Volume: weniger Pixel, vollständiges Volume, sieht 3D aus, sieht jedoch etwas unscharf aus)

## <a name="representing-3d-textures"></a>Darstellen von 3D-Texturen

Auf der CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

Auf der GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>Schattierung und Farbverläufe

Schattierung eines Volumes, z. B. MRI, zur nützlichen Visualisierung. Die primäre Methode besteht darin, ein "Intensitätsfenster" (min. und max.) zu haben, in dem Sie Dietensitäten anzeigen möchten, und einfach in diesen Raum zu skalieren, um die Schwarz-Weiß-Intensität anzuzeigen. Eine "Farbverlauf" kann dann auf die Werte innerhalb dieses Bereichs angewendet und als Textur gespeichert werden, sodass verschiedene Teile des Intensitätsspektrums unterschiedliche Farben schattiert werden können:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

In vielen unserer Anwendungen speichern wir in unserem Volume sowohl einen rohen Intensitätswert als auch einen "Segmentierungsindex" (um verschiedene Teile wie Skin und Skin zu segmentieren; diese Segmente werden von Experten in dedizierten Tools erstellt). Dies kann mit dem oben beschriebenen Ansatz kombiniert werden, um eine andere Farbe oder sogar eine andere Farbverlaufsverlauf für jeden Segmentindex zu verwenden:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Volumeslicing in einem Shader

Ein guter erster Schritt besteht darin, eine "Aufschneidende Ebene" zu erstellen, die sich durch das Volume bewegen, "aufschneiden" kann und wie die Scanwerte an jedem Punkt durchgeführt werden. Dabei wird davon ausgegangen, dass es einen VolumeSpace-Cube gibt, der darstellt, wo sich das Volume im Weltraum befindet, der als Verweis zum Platzieren der Punkte verwendet werden kann:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Volumeablaufverfolgung in Shadern

Gewusst wie: Verwenden der GPU für die Ablaufverfolgung von untergeordneten Läufen (durchläuft einige Voxel tief und dann Ebenen der Daten von zurück nach vorne):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>Rendering ganzer Volumes

Wenn Sie den obigen untergeordneten Code ändern, erhalten wir Folgendes:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Szenenrendering mit gemischter Auflösung

So rendern Sie einen Teil der Szene mit geringer Auflösung und setzen ihn wieder ein:
1. Richten Sie zwei Off-Screen-Kameras ein, eine, um jedem Auge zu folgen, das jeden Frame aktualisiert.
2. Einrichten von zwei Renderzielen mit niedriger Auflösung (d.b. jeweils 200 x 200), in die die Kameras gerendert werden
3. Einrichten eines Quaders, das sich vor dem Benutzer bewegt

Jeder Frame:
1. Zeichnen Sie die Renderziele für jedes Auge mit geringer Auflösung (Volumendaten, teure Shader usw.).
2. Zeichnen Sie die Szene normal als vollständige Auflösung (Gitternetze, Benutzeroberfläche usw.).
3. Zeichnen Sie ein Quader vor dem Benutzer, über die Szene, und pro project the low-res renders on that
4. Ergebnis: visuelle Kombination von Vollständigauflösungselementen mit Daten mit geringer Auflösung, aber hoher Dichte
