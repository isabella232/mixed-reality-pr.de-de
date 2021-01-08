---
title: Volumengrafik
description: Erfahren Sie, wie Sie Rich-Volumetrische-Bilder effizient mit Deckkraft und Farben in Windows Mixed Reality Renderings.
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: volumetribild, volumenrendering, Leistung, gemischte Realität
ms.openlocfilehash: 2a76be80d786aea0c8bc1bd364155fa37d37e151
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008780"
---
# <a name="volume-rendering"></a><span data-ttu-id="4f5db-104">Volumengrafik</span><span class="sxs-lookup"><span data-stu-id="4f5db-104">Volume rendering</span></span>

<span data-ttu-id="4f5db-105">Informationen zu medizinischen MRT-oder Engineering-Volumes finden Sie unter [Volume Rendering auf Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span><span class="sxs-lookup"><span data-stu-id="4f5db-105">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="4f5db-106">Diese "Volumetric Images" enthalten umfangreiche Informationen mit Deckkraft und farbiger Farbe im gesamten Volume, das nicht einfach als Oberflächen, wie z. b. [polygonale Netze](https://en.wikipedia.org/wiki/Polygon_mesh), ausgedrückt werden kann.</span><span class="sxs-lookup"><span data-stu-id="4f5db-106">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="4f5db-107">Wichtige Lösungen zum Verbessern der Leistung</span><span class="sxs-lookup"><span data-stu-id="4f5db-107">Key solutions to improve performance</span></span>
1. <span data-ttu-id="4f5db-108">Schlecht: naive Vorgehensweise: gesamtes Volume anzeigen, wird in der Regel zu langsam ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4f5db-108">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="4f5db-109">Gut: ausschnittsebene: nur ein einzelnes Slice des Volumes anzeigen</span><span class="sxs-lookup"><span data-stu-id="4f5db-109">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="4f5db-110">Gut: das untergeordnete Volume wird abgeschnitten: Es werden nur wenige Ebenen des Volumes angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4f5db-110">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="4f5db-111">Gut: Verringern der Auflösung des volumerendering (siehe ' Mixed Resolution Scene Rendering ')</span><span class="sxs-lookup"><span data-stu-id="4f5db-111">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="4f5db-112">Es gibt nur eine bestimmte Menge von Informationen, die von der Anwendung auf den Bildschirm in einem bestimmten Frame übertragen werden können. Dies ist die gesamte Arbeitsspeicher Bandbreite.</span><span class="sxs-lookup"><span data-stu-id="4f5db-112">There's only a certain amount of information that can be transferred from the application to the screen in any particular frame, which is the total memory bandwidth.</span></span> <span data-ttu-id="4f5db-113">Außerdem erfordert jede Verarbeitung (oder ' Schattierung '), die zum Transformieren der Daten für die Präsentation erforderlich ist, Zeit.</span><span class="sxs-lookup"><span data-stu-id="4f5db-113">Also, any processing (or 'shading') required to transform that data for presentation requires time.</span></span> <span data-ttu-id="4f5db-114">Die wichtigsten Überlegungen zum Rendern von Volumes lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4f5db-114">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="4f5db-115">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layer-on-this-Pixel = Total-Volume-Samples-per Frame</span><span class="sxs-lookup"><span data-stu-id="4f5db-115">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="4f5db-116">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (vollständiges res-Volume: zu viele Beispiele)</span><span class="sxs-lookup"><span data-stu-id="4f5db-116">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="4f5db-117">1028 \* 720 \* 2 \* 1 = 1480320 (0,3% vollständig) (dünner Slice: 1 Stichprobe pro Pixel, reibungsloses ausführen)</span><span class="sxs-lookup"><span data-stu-id="4f5db-117">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="4f5db-118">1028 \* 720 \* 2 \* 10 = 14803200 (3,9% vollständig) (subvolumeslice: 10 Stichproben pro Pixel, wird ziemlich reibungslos ausgeführt, sieht 3D aus)</span><span class="sxs-lookup"><span data-stu-id="4f5db-118">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (subvolume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="4f5db-119">200 \* 200 \* 2 \* 256 = 20480000 (5% vollständig) (niedrigeres Volume: weniger Pixel, vollständiges Volume, sieht 3D-, aber etwas verschwommen)</span><span class="sxs-lookup"><span data-stu-id="4f5db-119">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blurry)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="4f5db-120">Darstellen von 3D-Texturen</span><span class="sxs-lookup"><span data-stu-id="4f5db-120">Representing 3D Textures</span></span>

<span data-ttu-id="4f5db-121">Auf der CPU:</span><span class="sxs-lookup"><span data-stu-id="4f5db-121">On the CPU:</span></span>

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

<span data-ttu-id="4f5db-122">Auf der GPU:</span><span class="sxs-lookup"><span data-stu-id="4f5db-122">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="4f5db-123">Schattierung und Farbverläufe</span><span class="sxs-lookup"><span data-stu-id="4f5db-123">Shading and Gradients</span></span>

<span data-ttu-id="4f5db-124">Vorgehensweise beim schattieren eines Volumes (z. b. von MRT) für eine sinnvolle Visualisierung.</span><span class="sxs-lookup"><span data-stu-id="4f5db-124">How to shade a volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="4f5db-125">Die primäre Methode besteht darin, ein "Intensitäts Fenster" (min und max) zu haben, in dem Sie die Intensität anzeigen möchten, und einfach in diesen Bereich zu skalieren, um die schwarze und weiße Intensität anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4f5db-125">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="4f5db-126">Eine ' Color-Ramp ' kann dann auf die Werte in diesem Bereich angewendet und als Textur gespeichert werden, sodass verschiedene Teile des Intensität-Spektrums unterschiedliche Farben schattiert werden können:</span><span class="sxs-lookup"><span data-stu-id="4f5db-126">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="4f5db-127">In vielen unserer Anwendungen speichern wir unsere Volumes sowohl als rohintensität als auch als Segmentierungs Index (zum Segmentieren verschiedener Teile wie Skin und Bone). diese Segmente werden von Experten in dedizierten Tools erstellt.</span><span class="sxs-lookup"><span data-stu-id="4f5db-127">In many of our applications, we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone; these segments are created by experts in dedicated tools).</span></span> <span data-ttu-id="4f5db-128">Dies kann mit dem oben beschriebenen Ansatz kombiniert werden, um eine andere Farbe oder sogar eine andere Farbskala für jeden Segment Index zu platzieren:</span><span class="sxs-lookup"><span data-stu-id="4f5db-128">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="4f5db-129">Volumeslicing in einem Shader</span><span class="sxs-lookup"><span data-stu-id="4f5db-129">Volume Slicing in a Shader</span></span>

<span data-ttu-id="4f5db-130">Ein hervorragend erster Schritt besteht darin, eine "Slicing Plane" zu erstellen, die sich durch das Volume bewegen kann, "Slicing" und die Überprüfungs Werte an jedem Punkt.</span><span class="sxs-lookup"><span data-stu-id="4f5db-130">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="4f5db-131">Dabei wird davon ausgegangen, dass es einen "volumespace"-Cube gibt, der den Speicherort des Volumes im Raum der Welt darstellt, der als Verweis zum Platzieren der Punkte verwendet werden kann:</span><span class="sxs-lookup"><span data-stu-id="4f5db-131">This assumes that there's a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="4f5db-132">Volumeablauf Verfolgung in Shadern</span><span class="sxs-lookup"><span data-stu-id="4f5db-132">Volume Tracing in Shaders</span></span>

<span data-ttu-id="4f5db-133">Verwenden der GPU zum Durchführen einer subvolumenablaufverfolgung (durchläuft einige einige Voxels tief, dann Ebenen der Daten von hinten nach vorne):</span><span class="sxs-lookup"><span data-stu-id="4f5db-133">How to use the GPU to do subvolume tracing (walks a few voxels deep, then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="4f5db-134">Gesamtes volumenrendering</span><span class="sxs-lookup"><span data-stu-id="4f5db-134">Whole Volume Rendering</span></span>

<span data-ttu-id="4f5db-135">Wenn Sie den obigen Code ändern, wird Folgendes angezeigt:</span><span class="sxs-lookup"><span data-stu-id="4f5db-135">Modifying the subvolume code above, we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="4f5db-136">Rendern von gemischten Auflösungs Szenen</span><span class="sxs-lookup"><span data-stu-id="4f5db-136">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="4f5db-137">Gewusst wie: Rendering eines Teils der Szene mit niedriger Auflösung und Zurücksetzen der Szene:</span><span class="sxs-lookup"><span data-stu-id="4f5db-137">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="4f5db-138">Richten Sie zwei Off-Screen-Kameras ein, um jedes Auge zu verfolgen, das jeden Frame aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="4f5db-138">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="4f5db-139">Einrichten von zwei Renderingzielen mit niedriger Auflösung (d. h. 200 x 200), die von den Kameras dargestellt werden</span><span class="sxs-lookup"><span data-stu-id="4f5db-139">Setup two low-resolution render targets (that is, 200x200 each) that the cameras render into</span></span>
3. <span data-ttu-id="4f5db-140">Richten Sie einen Quad ein, der vor dem Benutzer wechselt.</span><span class="sxs-lookup"><span data-stu-id="4f5db-140">Set up a quad that moves in front of the user</span></span>

<span data-ttu-id="4f5db-141">Jeder Frame:</span><span class="sxs-lookup"><span data-stu-id="4f5db-141">Each Frame:</span></span>
1. <span data-ttu-id="4f5db-142">Zeichnen Sie die Renderziele für jedes Auge bei niedriger Auflösung (Volumedaten, teure Shaders usw.).</span><span class="sxs-lookup"><span data-stu-id="4f5db-142">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, and so on)</span></span>
2. <span data-ttu-id="4f5db-143">Zeichnen Sie die Szene normal als vollständige Auflösung (Meshes, UI usw.)</span><span class="sxs-lookup"><span data-stu-id="4f5db-143">Draw the scene normally as full resolution (meshes, UI, and so on)</span></span>
3. <span data-ttu-id="4f5db-144">Zeichnen Sie einen Quad vor dem Benutzer, über die Szene, und projizieren Sie die auf diese</span><span class="sxs-lookup"><span data-stu-id="4f5db-144">Draw a quad in front of the user, over the scene, and project the low-res renders onto that</span></span>
4. <span data-ttu-id="4f5db-145">Ergebnis: visuelle Kombination von Elementen mit vollständiger Auflösung mit geringer Auflösung, aber Volumedaten mit hoher Dichte</span><span class="sxs-lookup"><span data-stu-id="4f5db-145">Result: visual combination of full-resolution elements with low-resolution but high-density volume data</span></span>
