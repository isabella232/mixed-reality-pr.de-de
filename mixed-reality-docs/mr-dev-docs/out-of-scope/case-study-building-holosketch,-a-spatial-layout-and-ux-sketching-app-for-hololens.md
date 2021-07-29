---
title: 'Fallstudie: Erstellen von HoloSketch, einem räumlichen Layout und einer UX-Skizzierungs-App für HoloLens'
description: HoloSketch ist ein räumliches Layout und UX-Skizzierungstool für HoloLens, um holografische Erfahrungen zu erstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, Sketching, App
ms.openlocfilehash: 24929d38f97a3c02946a28184d7702c151dc22b2
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757322"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Fallstudie: Erstellen von HoloSketch, einem räumlichen Layout und einer UX-Skizzierungs-App für HoloLens

HoloSketch ist ein räumliches Layout und UX-Skizzierungstool für HoloLens, um holografische Erfahrungen zu erstellen. HoloSketch funktioniert mit einem gekoppelten Bluetooth Tastatur und Maus sowie Gesten- und Sprachbefehlen. Der Zweck von HoloSketch besteht darin, ein einfaches UX-Layouttool für die schnelle Visualisierung und Iteration bereitzustellen.

![HoloSketch: Eine Raumlayout- und UX-Skizzierungs-App für HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: App für räumliches Layout und UX-Skizzierung für HoloLens*

![Ein einfaches UX-Layouttool für schnelle Visualisierung und Iteration.](images/holosketch-image-02.png)<br>
*Ein einfaches UX-Layouttool für schnelle Visualisierung und Iteration*

## <a name="features"></a>Features

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitive für schnelle Untersuchungen und Skalierungsprototypen

![Verwenden primitiver Formen](images/holosketch-primitives-giphy.gif)

Verwenden Sie primitive Formen für schnelle Massenstudien und Skalierungsprototypen.

### <a name="import-objects-through-onedrive"></a>Importieren von Objekten über OneDrive

![Importieren von Objekten](images/holosketch-importobjects-giphy.gif)

Importieren Sie PNG-/JPG-Bilder oder 3D-FBX-Objekte (müssen in Unity verpackt werden) über OneDrive in den Mixed Reality-Raum.

### <a name="manipulate-objects"></a>Bearbeiten von Objekten

![Bearbeiten von Objekten](images/manipulate-objects-640px.jpg)

Bearbeiten von Objekten (Verschieben/Drehen/Skalieren) mit einer vertrauten 3D-Objektschnittstelle.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, Maus/Tastatur, Gesten und Sprachbefehle

![unterstützt Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch unterstützt Bluetooth Maus-/Tastatur-, Gesten- und Sprachbefehle.

## <a name="background"></a>Hintergrund

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Wichtigkeit des Entwurfs auf dem Gerät

Wenn Sie etwas für HoloLens entwerfen, ist es wichtig, Ihren Entwurf auf dem Gerät zu erleben. Eine der größten Herausforderungen beim Design von Mixed Reality-Apps besteht darin, dass es schwierig ist, das Gefühl von Skalierung, Position und Tiefe zu erhalten, insbesondere durch herkömmliche 2D-Zeichnungen.

### <a name="cost-of-2d-based-communication"></a>Kosten der 2D-basierten Kommunikation

Um UX-Flows und -Szenarien effektiv mit anderen zu kommunizieren, muss ein Designer möglicherweise viel Zeit mit der Erstellung von Ressourcen mit herkömmlichen 2D-Tools verbringen, z. B. MitHilfe von Bildern, Bildern und PowerPoint. Diese 2D-Entwürfe erfordern häufig zusätzlichen Aufwand, um sie in 3D zu konvertieren. Einige Ideen gehen bei dieser Übersetzung von 2D in 3D verloren.

### <a name="complex-deployment-process"></a>Komplexer Bereitstellungsprozess

Da Mixed Reality eine neue Canvas für uns ist, umfasst sie naturgemäß viele Designiterationen, Testversionen und Fehler. Für Designer, die nicht mit Tools wie Unity und Visual Studio vertraut sind, ist es nicht einfach, etwas in HoloLens zusammenzustellen. In der Regel müssen Sie den unten angegebenen Prozess durchlaufen, um Ihre 2D/3D-Grafik auf dem Gerät anzuzeigen. Dies war eine große Barriere für Designer, die ideen- und szenarioschnell iterieren.

![Komplexer Bereitstellungsprozess](images/holosketch-image-03-1000px.png)<br>
*Bereitstellungsprozess*

### <a name="simplified-process-with-holosketch"></a>Vereinfachter Prozess mit HoloSketch

Mit HoloSketch wollten wir diesen Prozess vereinfachen, ohne Entwicklungstools und Geräteportalpaare zu verwenden. Mit OneDrive können Benutzer 2D-/3D-Objekte problemlos in HoloLens.

![Vereinfachter Prozess mit HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Vereinfachter Prozess mit HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Fördern von dreidimensionalen Entwurfskonzepten und -lösungen

Wir haben angenommen, dass dieses Tool Designern die Möglichkeit geben würde, Lösungen in einem wirklich dreidimensionalen Raum zu untersuchen und nicht in 2D hängen zu bleiben. Sie müssen nicht darüber nachdenken, einen 3D-Hintergrund für ihre Benutzeroberfläche zu erstellen, da der Hintergrund im Fall von HoloLens die reale Welt ist. HoloSketch bietet Designern eine Möglichkeit, 3D-Design auf HoloLens zu untersuchen.

## <a name="get-started"></a>Erste Schritte

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Importieren von 2D-Bildern (JPG/PNG) in HoloSketch

* Hochladen JPG-/PNG-Bilder in Ihrem OneDrive Ordner "Documents/HoloSketch".
* Im menü OneDrive in HoloSketch können Sie das Bild auswählen und in der Umgebung platzieren.

![Importieren von 2D-Images](images/import-2d-images-1000px.jpg)<br>
*Importieren von Bildern und 3D-Objekten über OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Importieren von 3D-Objekten in HoloSketch

Führen Sie vor dem Hochladen in Ihren OneDrive Ordner die folgenden Schritte aus, um Ihre 3D-Objekte in ein Unity-Medienobjektpaket zu packen. Mit diesem Prozess können Sie Ihre FBX-/OBJ-Dateien aus 3D-Software wie Maya,Js 4D und Microsoft Paint 3D importieren.

>[!IMPORTANT]
>Derzeit wird die Erstellung von Medienobjektpaketen mit Unity-Version 5.4.5f1 unterstützt.

1. Laden Sie das Unity-Projekt ["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)herunter, und öffnen Sie es. Dieses Unity-Projekt enthält das Skript für die Generierung von Bundleobjekten.
2. Erstellen Sie ein neues GameObject.
3. Nennen Sie das GameObject basierend auf dem Inhalt.
4. Klicken Sie im Bereich Inspector auf "Add Component" (Komponente hinzufügen), und fügen Sie "Box Collider" hinzu. 

   ![Klicken Sie im Bereich Inspector auf "Add Component" (Komponente hinzufügen), und fügen Sie "Box Collider" hinzu.](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Klicken Sie im Bereich Inspector auf "Add Component" (Komponente hinzufügen), und fügen Sie "Box Collider" hinzu, #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importieren Sie die 3D-FBX-Datei, indem Sie sie in den Projektbereich ziehen.
6. Ziehen Sie das Objekt in den Hierarchiebereich **unter Dem neuen GameObject**.

   ![Ziehen Sie das Objekt in den Hierarchiebereich unter Ihrem neuen GameObject.](images/holosketch-12-assetbundles-1000px.png)

7. Passen Sie die Colliderdimension an, wenn sie nicht mit dem -Objekt übereinstimmt. Drehen Sie das -Objekt, um die **Z-Achse** zu sehen.

   ![Passen Sie die Colliderdimension an, wenn sie nicht mit dem -Objekt übereinstimmt.](images/holosketch-13-assetbundles-1000px.png)

8. Ziehen Sie das Objekt aus dem Hierarchiebereich in den bereich Project, um **es als Prefab** zu erstellen.
9. Klicken Sie unten im Inspektorbereich auf die Dropdownliste, erstellen Sie einen neuen eindeutigen Namen, und weisen Sie diesen zu. Das folgende Beispiel zeigt das Hinzufügen und Zuweisen von "brownchair" für den AssetBundle-Namen. 

   ![Klicken Sie unten im Inspektorbereich auf die Dropdownliste, und weisen Sie einen neuen eindeutigen Namen zu.](images/holosketch-14-assetbundles-1000px.png)

10. Bereiten Sie ein Miniaturbild für das Modellobjekt vor. 
   ![Ziehen Sie ein Bild in den Projektbereich, und weisen Sie den für das Objekt verwendeten Namen zu.](images/holosketch-15-assetbundles-1000px.png)

11. Erstellen Sie einen Ordner mit dem Namen "Assetbundles" im Ordner "Asset" des Unity-Projekts.

12. Wählen Sie im Menü Assets die Option "AssetBundles erstellen" aus, um eine Datei zu generieren. 
   ![Wählen Sie im Menü Assets die Option "AssetBundles erstellen" aus, um eine Datei zu generieren.](images/holosketch-15a-assetbundles.png)


13. **Hochladen die generierte Datei im Ordner /Files/Documents/HoloSketch auf OneDrive.** Hochladen nur die datei asset_unique_name. Sie müssen keine Manifestdateien oder AssetBundles-Dateien hochladen. <br>
![Dateien zum Ordner "Files/Documents/HoloSketch/" hinzufügen ](images/holosketch-onedriveupload-1000px.png)
 ![ Im HoloSketch-Menü OneDrive wird ein hinzugefügtes 3D-Objekt angezeigt.](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Bearbeiten der Objekte

HoloSketch unterstützt die herkömmliche Schnittstelle, die häufig in 3D-Software verwendet wird. Sie können die Objekte mit Gesten und einer Maus verschieben, drehen und skalieren. Sie können schnell zwischen verschiedenen Modi mit Sprache oder Tastatur wechseln.

### <a name="object-manipulation-modes"></a>Objektbearbeitungsmodi

![Bearbeiten der Objekte](images/holosketch-image-06-1000px.png)<br>
*Bearbeiten der Objekte*

### <a name="contextual-and-tool-belt-menus"></a>Kontext- und Toolbandmenüs

**Verwenden des Kontextmenüs**

Tippen Sie doppelt in die Luft, um das Kontextmenü zu öffnen. 

Menüelemente:
* **Layoutoberfläche:** Dies ist ein 3D-Rastersystem, in dem Sie mehrere Objekte layouten und als Gruppe verwalten können. Tippen Sie doppelt auf die Layoutoberfläche, um ihr Objekte hinzuzufügen.
* **Primitive:** Verwenden Sie Würfel, Kugeln, Zylinder und Kegel für Massenstudien.
* **OneDrive:** Öffnen Sie das Menü OneDrive, um Objekte zu importieren.
* **Hilfe:** Zeigt den Hilfebildschirm an.

![Kontextmenü](images/holosketch-image-07.png)<br>
*Kontextmenü*

**Verwenden des Menüs "Toolband"**

Die Szenen "Verschieben", "Drehen", "Skalieren", "Speichern" und "Laden" sind über das Menü "Toolband" verfügbar. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Verwenden von Tastatur, Gesten und Sprachbefehlen

![Tastatur, Gesten und Sprachbefehle](images/holosketch-image-08-1000px.png)<br>
*Tastatur, Gesten und Sprachbefehle*

## <a name="download-the-app"></a>Herunterladen der App

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Laden Sie die HoloSketch-App kostenlos herunter, und installieren Sie sie Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Bekannte Probleme
* Derzeit wird die Erstellung von Ressourcenpaketen mit **Unity Version 5.4.5f1 unterstützt.**
* Abhängig von der Datenmenge in Ihrer OneDrive kann die App so angezeigt werden, als ob sie beim Laden des Inhalts OneDrive wurde.
* Derzeit unterstützt die Funktion "Speichern und Laden" nur primitive Objekte.
* Die Menüs "Text", "Sound", "Video" und "Foto" sind im Kontextmenü deaktiviert.
* Mit der Schaltfläche "Wiedergabe" im Menü "ToolBand" werden die Manipulationsmoos entiert.

## <a name="sharing-your-sketches"></a>Teilen Ihrer Sketche

Sie können das Videoaufzeichnungsfeature in HoloLens verwenden, indem Sie "Hey Cortana, Start/Stop recording" (Hey Cortana, Aufzeichnung starten/beenden) sagen. Drücken Sie das Volume zusammen nach oben/unten, um ein Bild ihres Sketches zu machen.

## <a name="about-the-authors"></a>Über die Autoren

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon Park</b></a><br>UX-Designer @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Beimring</b><br>Entwickler @Microsoft</td>
</tr>
</table> 