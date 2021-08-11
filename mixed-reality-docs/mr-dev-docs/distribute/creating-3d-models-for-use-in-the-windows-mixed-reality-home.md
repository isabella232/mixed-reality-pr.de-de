---
title: Erstellen von 3D-Modellen zur Verwendung auf der Startseite
description: Ressourcenanforderungen und Erstellungsanleitungen für 3D-Modelle, die in der Windows Mixed Reality Home sowohl auf HoloLens als auch auf immersiven Headsets (VR) verwendet werden sollen.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, Modellierung, Modellierungsleitfaden, Ressourcenanforderungen, Erstellungsrichtlinien, Startfeld, 3D-Startfeld, Textur, Materialien, Komplexität, Dreiecke, Gittermodell, Polygone, Polyanzahl, Grenzwerte, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 9fdd485c67a757d40b049c08f114ce9982aafc27e9103c4b31c21fd8af08d186
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207680"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Erstellen von 3D-Modellen zur Verwendung auf der Startseite

Das [Windows Mixed Reality Home](../discover/navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen. Verwenden Sie beim Entwerfen Ihrer Anwendung für Windows Mixed Reality Headsets ein [3D-Modell als App-Startmodell,](implementing-3d-app-launchers.md) und platzieren Sie [deep 3D-Links im Windows Mixed Reality Startseite.](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) In diesem Artikel werden die Richtlinien zum Erstellen von 3D-Modellen beschrieben, die mit der Windows Mixed Reality Home kompatibel sind.

## <a name="asset-requirements-overview"></a>Ressourcenanforderungen – Übersicht

Beim Erstellen von 3D-Modellen für Windows Mixed Reality müssen alle Ressourcen einige Anforderungen erfüllen: 
1. [Exportieren:](#exporting-models) Ressourcen müssen im GLB-Dateiformat (binary glTF) übermittelt werden.
2. [Modellierung:](#modeling-guidelines) Ressourcen müssen kleiner als 10.000 Dreiecke sein, dürfen nicht mehr als 64 Knoten und 32 Untermeshes pro LOD aufweisen.
3. [Materialien:](#material-guidelines) Texturen dürfen nicht größer als 4.096 x 4096 sein, und die kleinste Mipmap darf in beiden Dimensionen nicht größer als 4 sein.
4. [Animation:](#animation-guidelines) Animationen dürfen bei 30 FPS (36.000 Keyframes) nicht länger als 20 Minuten sein und müssen <= 8192 Morphzielvertices enthalten.
5. [Optimieren:](#optimizations) Ressourcen sollten mithilfe von [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)optimiert werden. *Erforderlich für Windows Betriebssystemversionen <= 1709** und empfohlen für Windows Betriebssystemversionen >= 1803

Der Rest dieses Artikels enthält eine detaillierte Übersicht über diese Anforderungen und zusätzliche Richtlinien, um sicherzustellen, dass Ihre Modelle mit der Windows Mixed Reality Gut funktionieren. 

## <a name="detailed-guidance"></a>Ausführliche Anleitung

### <a name="exporting-models"></a>Exportieren von Modellen

Das Windows Mixed Reality Home erwartet, dass 3D-Objekte im GLB-Dateiformat mit eingebetteten Bildern und Binärdaten bereitgestellt werden. Glb ist die binäre Version des glTF-Formats, bei der es sich um einen kostenlosen kostenlosen Standard für die Übermittlung von 3D-Medienobjekten handelt, der von der Gruppe "Lbronos" verwaltet wird. Da glTF sich als Branchenstandard für interoperable 3D-Inhalte weiterentwickelt, wird auch die Unterstützung des Formats durch Microsoft über Windows Apps und Benutzererfahrungen hinweg unterstützt. Wenn Sie noch kein glTF-Medienobjekt erstellt haben, finden Sie eine [Liste der unterstützten Exporter und Konverter](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) auf der GitHub-Seite der glTF-Arbeitsgruppe.  

### <a name="modeling-guidelines"></a>Modellierungsrichtlinien

Windows erwartet, dass Ressourcen mithilfe der folgenden Modellierungsrichtlinien generiert werden, um die Kompatibilität mit der Mixed Reality Home-Erfahrung sicherzustellen. Beachten Sie bei der Modellierung in Ihrem Programm Ihrer Wahl die folgenden Empfehlungen und Einschränkungen:
1. Die Up-Achse sollte auf "Y" festgelegt werden.
2. Das Objekt sollte in Richtung der positiven Z-Achse "vorwärts" stehen.
3. Alle Objekte sollten auf der Bodenebene am Szenenursprung (0,0,0) erstellt werden.
4. Arbeitseinheiten sollten auf Meter und Ressourcen festgelegt werden, damit Ressourcen weltweit erstellt werden können.
5. Alle Gitternetze müssen nicht kombiniert werden, aber es wird empfohlen, wenn Sie auf Geräte mit eingeschränkten Ressourcen abzielen.
6. Alle Gitternetze sollten ein Material gemeinsam nutzen, wobei nur ein Textursatz für das gesamte Medienobjekt verwendet wird.
7. UVs müssen in einer quadratischen Anordnung im Bereich 0-1 angeordnet werden. Vermeiden Sie Kacheltexturen, obwohl sie zulässig sind.
8. Mehrere UVs werden nicht unterstützt.
9. Doppelseitige Materialien werden nicht unterstützt.

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Dreiecksanzahl und Detailebenen (LODs)

Das Windows Mixed Reality Home unterstützt keine Modelle mit mehr als 10.000 Dreiecken. Es wird empfohlen, ihre Gitternetze vor dem Export zu triangulieren, um sicherzustellen, dass diese Anzahl nicht überschritten wird. Windows MR unterstützt auch optionale Detailgeometrieebenen (LODs), um eine leistungsfähige und hochwertige Erfahrung zu gewährleisten. [WindowsMRAssetConverter hilft](https://github.com/Microsoft/glTF-Toolkit/releases) Ihnen, drei Versionen Ihres Modells in einem einzelnen GLB-Modell zu kombinieren. Windows bestimmt, welche LOD basierend auf der Größe der Bildschirmfläche angezeigt werden soll, die das Modell annimmt. Nur drei LOD-Ebenen werden mit den folgenden empfohlenen Dreieckszahlen unterstützt:
<br>

|  LOD-Ebene  |  Empfohlene Dreiecksanzahl  |  Maximale Anzahl von Dreiecken | 
|------|------|------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

### <a name="node-counts-and-submesh-limits"></a>Knotenanzahl und Untermeshgrenzwerte

Der Windows Mixed Reality Home unterstützt keine Modelle mit mehr als 64 Knoten oder 32 Untermeshes pro LOD. Knoten sind ein Konzept in der [glTF-Spezifikation,](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) das die Objekte in der Szene definiert. Untermeshes werden im Array von [Primitiven](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) im Gittermodell im -Objekt definiert. 

|  Funktion |  Beschreibung  |  Max. Unterstützt | Dokumentation |
|------|------|------|------|
|  Nodes |  Objekte in der glTF-Szene |  64 pro LOD | [Hier](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Untermeshes |  Summe der Primitive in allen Gitternetzen |  32 pro LOD | [Hier](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Materialrichtlinien

Texturen sollten mithilfe eines PBR-Metal-Rauheitsworkflows vorbereitet werden. Erstellen Sie zunächst einen vollständigen Satz von Texturen, einschließlich Albedo, Normal, Occlusion, Texture und Roughness. Windows Mixed Reality unterstützt Texturen mit Auflösungen von bis zu 4096 x 4096, es wird jedoch empfohlen, dass Sie mit 512 x 512 erstellen. Texturen sollten mit Auflösungen in Vielfachen von 4 erstellt werden. Dies ist eine Anforderung für das Komprimierungsformat, das in den unten beschriebenen Exportschritten auf Texturen angewendet wird. Beim Generieren von Mipmaps oder einer Textur muss der niedrigste Mip maximal 4x4 sein.
<br>

|  Empfohlene Texturgröße  |  Maximale Texturgröße | Niedrigster Mip
|----|----|----|
|  512 x 512  |  4096x4096 | max. 4x4|

### <a name="albedo-base-color-map"></a>Albedo-Karte (Basisfarbe)

Rohfarbe ohne Beleuchtungsinformationen. Diese Karte enthält auch die Reflektions- und diffusen Informationen für die Oberflächen Metal (weiß in der Kartenkarte) bzw. Desulators (schwarz auf der Karte).

### <a name="normal"></a>Normal

Tangens space Normal map

### <a name="roughness-map"></a>Rauheitskarte

Beschreibt die Microsurface des -Objekts. Weiß 1.0 ist ungefähr Schwarz 0,0 ist reibungslos. Diese Karte gibt dem Medienobjekt das meiste Zeichen, da es die Oberfläche wirklich beschreibt. Beispiele hierfür sind Scratchs, Fingerabdrücke, Smudges, Füge usw.

### <a name="ambient-occlusion-map"></a>Umgebungsverdeckungskarte

Wertskalakarte mit Bereichen von verdecktem Licht, die Reflektionen blockieren

### <a name="metallic-map"></a>Karte "Maps"

Teilt dem Shader mit, ob etwas metal ist oder nicht. Raw Metal = 1,0 weiß Non-Metal = 0,0 schwarz. Es können graue Übergangswerte vorhanden sein, die auf etwas hinweisen, das das Rohmaterial abdeckt, z. B. Bekleidung, aber im Allgemeinen sollte diese Karte nur schwarz und weiß sein.

## <a name="optimizations"></a>Optimierungen

Windows Mixed Reality Home bietet eine Reihe von Optimierungen auf der Grundlage der kernbezogenen glTF-Spezifikation, die mit benutzerdefinierten Erweiterungen definiert wurde. Diese Optimierungen sind für Windows Versionen <= 1709 erforderlich und werden für neuere Versionen von Windows. Sie können problemlos jedes glTF 2.0-Modell optimieren, indem Sie den [Windows Mixed Reality Asset Converter verwenden,](https://github.com/Microsoft/glTF-Toolkit/releases)der auf GitHub. Dieses Tool führt die richtigen Texturpackungen und Optimierungen aus, wie unten angegeben. Für die allgemeine Verwendung empfehlen wir die Verwendung von WindowsMRAssetConverter. Wenn Sie jedoch mehr Kontrolle über die Benutzererfahrung benötigen und eine eigene Optimierungspipeline erstellen möchten, können Sie die unten aufgeführte ausführliche Spezifikation verwenden.  

> [!NOTE]
> Eine definitive Liste der Möglichkeiten für genaue Modellgrenzwerte finden Sie im Artikel [zur 3D-Modelloptimierung](/dynamics365/mixed-reality/guides/3d-content-guidelines/optimize-models) für die Verwendung in Dynamics 365-Anwendungen.

### <a name="materials"></a>Materialien

Zur Verbesserung der Ladezeit von Medienstücken in Mixed Reality-Umgebungen unterstützt Windows MR das Rendern komprimierter DDS-Texturen, die gemäß dem in diesem Abschnitt definierten Texturpaketschema gepackt sind. Auf DDS-Texturen wird mithilfe der MSFT_texture_dds [verwiesen.](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds) Das Komprimieren von Texturen wird dringend empfohlen. 

#### <a name="hololens"></a>HoloLens

HoloLens Mixed Reality-Oberflächen erwarten, dass Texturen mithilfe eines 2-Textur-Setups gepackt werden, indem die folgende Füllspezifikation verwendet wird:
<br>

|  glTF-Eigenschaft  |  Struktur  |  Packschema | 
|----------|----------|----------|
|  pbrOrganicRoughness  |  baseColorTexture  |  Rot (R), Grün (G), Blau (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessOrganicTexture  |  Normal (RG), Rauheit (B), Piek (A) | 


Beim Komprimieren der DDS-Texturen wird auf jeder Karte die folgende Komprimierung erwartet:
<br>

|  Struktur  |  Erwartete Komprimierung | 
|------|------|
|  baseColorTexture, normalRoughnessOrganicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Immersive Headsets (VR)

PC-basierte Windows Mixed Reality für immersive Headsets (VR) erwarten, dass Texturen mithilfe eines 3-Textur-Setups gepackt werden, indem die folgende Gepacktsspezifikation verwendet wird:

##### <a name="windows-os--1803"></a>Windows Betriebssystem >= 1803

<br>

|  glTF-Eigenschaft  |  Struktur  |  Packschema | 
|----------|----------|----------|
|  pbrOrganicRoughness  |  baseColorTexture  |  Rot (R), Grün (G), Blau (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessAsseicTexture  |  Okklusion (R), Rauheit (G),Skript (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Beim Komprimieren der DDS-Texturen wird auf jeder Karte die folgende Komprimierung erwartet:
<br>

|  Struktur  |  Erwartete Komprimierung | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessAsseicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows Betriebssystem <= 1709
<br>

|  glTF-Eigenschaft  |  Struktur  |  Packschema | 
|----------|----------|----------|
|  pbrOrganicRoughness  |  baseColorTexture  |  Rot (R), Grün (G), Blau (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessDienicOcclusionTexture  |  Rauheit (R), Ecken (G), Okklusion (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Beim Komprimieren der DDS-Texturen wird auf jeder Karte die folgende Komprimierung erwartet:
<br>

|  Struktur  |  Erwartete Komprimierung | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughness (Rauheit)&160;&160;&160;&160;& | BC7 |

### <a name="adding-mesh-lods"></a>Hinzufügen von Mesh-LODs

Windows MR verwendet GEOMETRY-Knoten-LODs, um 3D-Modelle abhängig von der Bildschirmabdeckung in unterschiedlichen Detailebenen zu rendern. Obwohl dieses Feature technisch nicht erforderlich ist, wird es für alle Ressourcen empfohlen. Derzeit Windows drei Detailebenen unterstützt. Die Standard-LOD ist 0, was die höchste Qualität darstellt. Andere LODs werden sequenziell nummeriert, z. B. 1, 2, und die Qualität wird zunehmend niedriger. Der [Windows Mixed Reality Asset Converter](https://github.com/Microsoft/glTF-Toolkit/releases) unterstützt das Generieren von Ressourcen, die diese LOD-Spezifikation erfüllen, indem mehrere glTF-Modelle akzeptiert und zu einem einzelnen Asset mit gültigen LOD-Ebenen zusammengeführt werden. In der folgenden Tabelle werden die erwartete LOD-Reihenfolge und die Dreiecksziele beschrieben:
<br>

|  LOD-Ebene  |  Empfohlene Dreiecksanzahl  |  Maximale Anzahl von Dreiecken | 
|-------|-------|-------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

Geben Sie bei Verwendung von LODs immer 3 LOD-Ebenen an. Fehlende LODs führen dazu, dass das Modell nicht unerwartet gerendert wird, wenn das LOD-System auf die fehlende LOD-Ebene wechselt. glTF 2.0 unterstützt loDs derzeit nicht als Teil der Kernspezifikation. LODs sollten mithilfe der MSFT_LOD [definiert werden.](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)

### <a name="screen-coverage"></a>Bildschirmabdeckung

LODs werden in der Windows Mixed Reality basierend auf einem System angezeigt, das durch den für jede LOD festgelegten Bildschirmabdeckungswert gesteuert wird. Objekte, die derzeit einen größeren Teil des Bildschirmbereichs verbrauchen, werden auf einer höheren LOD-Ebene angezeigt. Die Bildschirmabdeckung ist nicht Teil der glTF 2.0-Kernspezifikation und muss mithilfe von MSFT_ScreenCoverage im Abschnitt "Extras" der MSFT_lod [angegeben werden.](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)
<br>

|  LOD-Ebene  |  Empfohlener Bereich  |  Standardbereich | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  0,5 | 
|  LOD 1 |  Unter 50 % bis 20 %  |  0,2 | 
|  LOD 2 |  Unter 20 % bis 1 %  |  0,01 | 
|  LOD 4  |  Unter 1 %  |  - | 

## <a name="animation-guidelines"></a>Richtlinien für Animationen

> [!NOTE]
> Dieses Feature wurde im Rahmen Windows 10 Update vom [April 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)hinzugefügt. Bei älteren Versionen von Windows werden diese Animationen nicht wiedergegeben. Sie werden jedoch weiterhin geladen, wenn sie gemäß der Anleitung in diesem Artikel erstellt wurden.  

Die Mixed Reality Startumgebung unterstützt animierte glTF-Objekte auf HoloLens und immersiven Headsets (VR). Wenn Sie Animationen für Ihr Modell auslösen möchten, müssen Sie die Animation Map-Erweiterung im glTF-Format verwenden. Mit dieser Erweiterung können Sie Animationen im glTF-Modell auslösen, die auf der Präsenz des Benutzers in der Welt basieren, z. B. eine Animation auslösen, wenn sich der Benutzer in der Nähe des Objekts befindet oder wenn er es ansieht. Wenn das glTF-Objekt Über Animationen verfügt, aber keine Trigger definiert, werden die Animationen nicht wiedergegeben. Im folgenden Abschnitt wird ein Workflow zum Hinzufügen dieser Trigger zu jedem animierten glTF-Objekt beschrieben.

### <a name="tools"></a>Tools

Laden Sie zunächst die folgenden Tools herunter, falls sie noch nicht vorhanden sind. Mit diesen Tools können Sie problemlos ein beliebiges glTF-Modell öffnen, eine Vorschau anzeigen, Änderungen vornehmen und als glTF oder .glb zurückspeichern:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [glTF-Tools für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Öffnen des Modells und Anzeigen einer Vorschau

Öffnen Sie zunächst das glTF-Modell in VSCode, indem Sie die GLTF-Datei in das Editorfenster ziehen. Wenn Sie über eine GLB-Datei anstelle einer GLTF-Datei verfügen, können Sie sie mithilfe des heruntergeladenen GlTF Tools-Add-Ons in VSCode importieren. Wechseln Sie zu "View -> Command Palette", und beginnen Sie dann mit der Eingabe von "glTF" in der Befehlspalette, und wählen Sie "glTF: Import from glb" aus. Daraufhin wird eine Dateiauswahl angezeigt, mit der Sie eine GLB importieren können. 

Nachdem Sie Ihr glTF-Modell geöffnet haben, sollte der JSON-Code im Editorfenster angezeigt werden. Sie können das Modell auch in einem Live-3D-Viewer anzeigen, indem Sie mit der rechten Maustaste auf den Dateinamen klicken und im Kontextmenü die Befehlsverknüpfung "glTF: Preview 3D Model" auswählen. 

### <a name="adding-the-triggers"></a>Hinzufügen der Trigger

Animationstrigger werden dem JSON-Code des glTF-Modells mithilfe der Animation Map-Erweiterung hinzugefügt. Die Animationskartenerweiterung ist [hier auf GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) öffentlich dokumentiert (HINWEIS: DIES IST EINE ENTWURFSERWEITERUNG). Um ihrem Modell die Erweiterung hinzuzufügen, scrollen Sie einfach zum Ende der glTF-Datei im Editor, und fügen Sie der Datei den Block "extensionsUsed" und "extensions" hinzu, sofern sie noch nicht vorhanden sind. Im Abschnitt "extensionsUsed" fügen Sie einen Verweis auf die Erweiterung "EXT_animation_map" und im Block "extensions" Ihre Zuordnungen zu den Animationen im Modell hinzu.

Wie [in der Spezifikation](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) erwähnt, definieren Sie, was die Animation mithilfe der "semantischen" Zeichenfolge in einer Liste von "Animationen" auslöst, bei der es sich um ein Array von Animationsindizes handelt. Im folgenden Beispiel haben wir die Animation angegeben, die wiedergegeben werden soll, während der Benutzer auf das -Objekt zeigt:

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
Die folgende Semantik für Animationstrigger wird vom Windows Mixed Reality Home unterstützt.  
* "ALWAYS": Eine Animation wird ständig in Schleife schleifen.
* "HELD": Ein Objekt wird während der gesamten Dauer in eine Schleife gepackt.
* "GAZE": Schleifen, während ein Objekt betrachtet wird
* "PROXIMITY": Schleifen, während sich ein Viewer in der Nähe eines Objekts befindet
* "POINTING": Schleifen, während ein Benutzer auf ein Objekt verweist

### <a name="saving-and-exporting"></a>Speichern und Exportieren

Nachdem Sie die Änderungen an Ihrem glTF-Modell vorgenommen haben, können Sie es direkt als glTF speichern. Sie können auch mit der rechten Maustaste auf den Namen der Datei im Editor klicken und "glTF: Export to GLB (binary file)" auswählen, um eine GLB zu exportieren. 

### <a name="restrictions"></a>Beschränkungen

Animationen dürfen nicht länger als 20 Minuten sein und dürfen nicht mehr als 36.000 Keyframes enthalten (20 Minuten bei 30 FPS). Wenn Sie zielbasierte Morph-Animationen verwenden, dürfen 8192 Morph-Zielvertices oder weniger nicht überschritten werden. Eine Überschreitung dieser Anzahl führt dazu, dass die animierte Ressource im Windows Mixed Reality Home nicht unterstützt wird. 

|Funktion|Maximum|
|-----|-----|
|Duration|20 Minuten|
|Keyframes|36.000| 
|Morph Target Vertices|8192|

## <a name="gltf-implementation-notes"></a>GlTF-Implementierungshinweise

Windows MR unterstützt das Spiegeln von Geometrien mit negativen Skalen nicht. Geometrie mit negativen Skalen führt wahrscheinlich zu visuellen Artefakten.

Das glTF-Medienobjekt MUSS mithilfe des Szenenattributs, das von Windows MR gerendert werden soll, auf die Standardszene verweisen. Darüber hinaus **erfordert** das Windows MR glTF-Ladeprogramm vor dem [Update vom Windows 10. April 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) Accessoren:
* Muss min- und max-Werte aufweisen.
* Typ SCALAR muss componentType UNSIGNED_SHORT (5123) oder UNSIGNED_INT (5125) sein.
* Typ VEC2 und VEC3 müssen componentType FLOAT (5126) sein.

Die folgenden Materialeigenschaften werden aus der GlTF 2.0-Kernspezifikation verwendet, sind jedoch nicht erforderlich:
* baseColorFactor,factorFactor, roughnessFactor
* baseColorTexture: Muss auf eine in dds gespeicherte Textur verweisen.
* emissiveTexture: Muss auf eine in dds gespeicherte Textur verweisen.
* emissiveFactor
* alphaMode

Die folgenden Materialeigenschaften werden von der Kernspezifikation ignoriert:
* Alle multi-UVs
* metalRoughnessTexture: Muss stattdessen die von Microsoft optimierte Texturfüllung verwenden, die unten definiert ist.
* normalTexture: Muss stattdessen die von Microsoft optimierte Texturfüllung verwenden, die unten definiert ist.
* normalScale
* occlusionTexture: Muss stattdessen die von Microsoft optimierte Texturfüllung verwenden, die unten definiert ist.
* occlusionStrength

Windows MR unterstützt keine Linien und Punkte im primitiven Modus. 

Es wird nur ein einzelnes UV-Scheitelpunktattribut unterstützt.

## <a name="more-resources"></a>Weitere Ressourcen

* [glTF-Exporter und -Konverter](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0-Spezifikation](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD-Erweiterungsspezifikation](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [Spezifikation für PC Mixed Reality Texture Packing Extensions](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens Spezifikation der Erweiterungen für Mixed Reality Texture Packing](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS Textures glTF extensions specification (Microsoft DDS Textures glTF-Erweiterungsspezifikation)](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Siehe auch

* [Implementieren von 3D-App-Startprogrammen (UWP-Apps)](implementing-3d-app-launchers.md)
* [Implementieren von 3D-App-Startprogrammen (Win32-Apps)](implementing-3d-app-launchers-win32.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)