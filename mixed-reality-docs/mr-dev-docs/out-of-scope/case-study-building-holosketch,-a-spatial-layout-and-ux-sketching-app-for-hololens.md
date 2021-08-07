---
title: 'Fallstudie: Erstellen von HoloSketch, einer App für räumliches Layout und UX-Skizzieren für HoloLens'
description: HoloSketch ist ein tool zum Skizzieren von räumlichen Layouts und UX auf geräten für HoloLens, um holografische Erfahrungen zu erstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, Skizzieren, App
ms.openlocfilehash: 614572c91067399cc0235ef2570543aa81e2c24ab36a7b9e9bfa03b77e452420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213841"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Fallstudie: Erstellen von HoloSketch, einer App für räumliches Layout und UX-Skizzieren für HoloLens

HoloSketch ist ein tool zum Skizzieren von räumlichen Layouts und UX auf geräten für HoloLens, um holografische Erfahrungen zu erstellen. HoloSketch funktioniert mit einer gekoppelten Bluetooth Tastatur und Maus sowie Gesten- und Sprachbefehlen. Der Zweck von HoloSketch besteht in der Bereitstellung eines einfachen UX-Layouttools für schnelle Visualisierung und Iteration.

![HoloSketch: Eine App für räumliches Layout und UX-Sketching für HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: App für räumliches Layout und UX-Sketching für HoloLens*

![Ein einfaches UX-Layouttool für schnelle Visualisierung und Iteration.](images/holosketch-image-02.png)<br>
*Ein einfaches UX-Layouttool für schnelle Visualisierung und Iteration*

## <a name="features"></a>Funktionen

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Grundtypen für schnelle Studien und Skalierungs-/Prototyperstellung

![Verwenden primitiver Formen](images/holosketch-primitives-giphy.gif)

Verwenden Sie primitive Formen für schnelle Massenstudien und skalierungsbasierte Prototyperstellung.

### <a name="import-objects-through-onedrive"></a>Importieren von Objekten über OneDrive

![Importieren von Objekten](images/holosketch-importobjects-giphy.gif)

Importieren Sie PNG-/JPG-Bilder oder 3D-FBX-Objekte (erfordert die Paketierung in Unity) in den Mixed Reality-Raum über OneDrive.

### <a name="manipulate-objects"></a>Bearbeiten von Objekten

![Bearbeiten von Objekten](images/manipulate-objects-640px.jpg)

Bearbeiten von Objekten (Verschieben/Drehen/Skalieren) mit einer vertrauten 3D-Objektschnittstelle.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, Maus/Tastatur, Gesten und Sprachbefehle

![unterstützt Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch unterstützt Bluetooth Maus-/Tastatur-, Gesten- und Sprachbefehle.

## <a name="background"></a>Hintergrund

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Wichtigkeit der Erfahrung Ihres Entwurfs auf dem Gerät

Wenn Sie etwas für HoloLens entwerfen, ist es wichtig, dass Sie Ihr Design auf dem Gerät erleben. Eine der größten Herausforderungen beim Design von Mixed Reality-Apps ist, dass es schwierig ist, das Gefühl von Skalierung, Position und Tiefe zu erhalten, insbesondere durch herkömmliche 2D- Sketche.

### <a name="cost-of-2d-based-communication"></a>Kosten der 2D-basierten Kommunikation

Um UX-Flows und -Szenarien effektiv mit anderen zu kommunizieren, kann ein Designer viel Zeit damit verbringen, Ressourcen mithilfe herkömmlicher 2D-Tools wie Etwa Einem, Einem oder anderen PowerPoint. Diese 2D-Entwürfe erfordern häufig zusätzlichen Aufwand, um sie in 3D zu konvertieren. Bei dieser Übersetzung von 2D in 3D gehen einige Ideen verloren.

### <a name="complex-deployment-process"></a>Komplexer Bereitstellungsprozess

Da Mixed Reality eine neue Canvas für uns ist, umfasst es von Natur aus viele Entwurfsiterationen sowie Test- und Fehlerfehler. Für Designer, die nicht mit Tools wie Unity und Visual Studio vertraut sind, ist es nicht einfach, etwas in einem HoloLens. In der Regel müssen Sie den unten angegebenen Prozess durchgehen, um Ihre 2D/3D-Grafik auf dem Gerät zu sehen. Dies war eine große Barriere für Designer, die schnell Ideen und Szenarien durchbrechen.

![Komplexer Bereitstellungsprozess](images/holosketch-image-03-1000px.png)<br>
*Bereitstellungsprozess*

### <a name="simplified-process-with-holosketch"></a>Vereinfachter Prozess mit HoloSketch

Mit HoloSketch wollten wir diesen Prozess vereinfachen, ohne Entwicklungstools und Geräteportalpaare zu verwenden. Mit OneDrive können Benutzer problemlos 2D/3D-Objekte in HoloLens.

![Vereinfachter Prozess mit HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Vereinfachter Prozess mit HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Fördern von dreidimensionalen Entwurfskonzepten und -lösungen

Wir haben angenommen, dass dieses Tool Designern die Möglichkeit geben würde, Lösungen in einem wirklich dreidimensionalen Raum zu untersuchen und nicht in 2D hängen zu bleiben. Sie müssen nicht darüber nachdenken, einen 3D-Hintergrund für ihre Benutzeroberfläche zu erstellen, da der Hintergrund die reale Welt im Fall von HoloLens. HoloSketch bietet Designern die Möglichkeit, das 3D-Design auf dem HoloLens.

## <a name="get-started"></a>Erste Schritte

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Importieren von 2D-Bildern (JPG/PNG) in HoloSketch

* Hochladen JPG/PNG-Bilder in OneDrive Ordner "Documents/HoloSketch".
* Über das OneDrive in HoloSketch können Sie das Bild auswählen und in der Umgebung platzieren.

![Importieren von 2D-Images](images/import-2d-images-1000px.jpg)<br>
*Importieren von Bildern und 3D-Objekten über OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Importieren von 3D-Objekten in HoloSketch

Führen Sie vor dem Hochladen in OneDrive Ordner die folgenden Schritte aus, um Ihre 3D-Objekte in ein Unity-Ressourcenpaket zu packen. Mit diesem Prozess können Sie Ihre FBX-/OBJ-Dateien aus 3D-Software wie Maya, Maya 4D und Microsoft Paint 3D.

>[!IMPORTANT]
>Derzeit wird die Erstellung von Ressourcenpaketen mit Unity Version 5.4.5f1 unterstützt.

1. Laden Sie das Unity-Projekt ["AssetBunlder_Unity" herunter, und öffnen Sie es.](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity) Dieses Unity-Projekt enthält das Skript für die Generierung des Bundle-Assets.
2. Erstellen Sie ein neues GameObject.
3. Benennen Sie das GameObject basierend auf dem Inhalt.
4. Klicken Sie im Inspektorbereich auf "Add Component" (Komponente hinzufügen), und fügen Sie "Box Collider" hinzu. 

   ![Klicken Sie im Inspektorbereich auf "Add Component" (Komponente hinzufügen), und fügen Sie "Box Collider" hinzu.](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Klicken Sie im Inspektorbereich auf "Add Component" (Komponente hinzufügen), und fügen Sie "Box Collider" #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importieren Sie die 3D-FBX-Datei, indem Sie sie in den Projektbereich ziehen.
6. Ziehen Sie das -Objekt in den Hierarchiebereich **unter das neue GameObject.**

   ![Ziehen Sie das Objekt in den Hierarchiebereich unter das neue GameObject.](images/holosketch-12-assetbundles-1000px.png)

7. Passen Sie die Colliderdimension an, wenn sie nicht mit dem -Objekt übereinstimmen. Drehen Sie das -Objekt, um auf **die Z-Achse zu zeigen.**

   ![Passen Sie die Colliderdimension an, wenn sie nicht mit dem -Objekt übereinstimmen.](images/holosketch-13-assetbundles-1000px.png)

8. Ziehen Sie das -Objekt aus dem Hierarchiebereich in den Project, um es **als Prefab zu erstellen.**
9. Klicken Sie unten im Inspektorbereich auf die Dropdownliste, erstellen Sie einen neuen eindeutigen Namen, und weisen Sie diesen zu. Das folgende Beispiel zeigt das Hinzufügen und Zuweisen von "brownchair" für den AssetBundle-Namen. 

   ![Klicken Sie unten im Inspektorbereich auf die Dropdownliste, und weisen Sie einen neuen eindeutigen Namen zu.](images/holosketch-14-assetbundles-1000px.png)

10. Bereiten Sie ein Miniaturbild für das Modellobjekt vor. 
   ![Ziehen Sie ein Bild in den Projektbereich, und weisen Sie den namen zu, der für das Objekt verwendet wird.](images/holosketch-15-assetbundles-1000px.png)

11. Erstellen Sie einen Ordner mit dem Namen "Assetbundles" im Ordner "Asset" des Unity-Projekts.

12. Wählen Sie im Menü Assets die Option "AssetBundles erstellen" aus, um eine Datei zu generieren. 
   ![Wählen Sie im Menü Assets die Option "AssetBundles erstellen" aus, um eine Datei zu generieren.](images/holosketch-15a-assetbundles.png)


13. **Hochladen die generierte Datei im Ordner /Files/Documents/HoloSketch auf OneDrive.** Hochladen sie asset_unique_name datei. Sie müssen keine Manifestdateien oder AssetBundles-Dateien hochladen. <br>
![Hinzufügen von Dateien zum Ordner "Files/Documents/HoloSketch/" (Dateien/Dokumente/HoloSketch/) Sie sehen, dass das 3D-Objekt im Menü "OneDrive ](images/holosketch-onedriveupload-1000px.png)
 ![ HoloSketch" hinzugefügt wurde.](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Bearbeiten der Objekte

HoloSketch unterstützt die herkömmliche Schnittstelle, die häufig in 3D-Software verwendet wird. Sie können das Verschieben, Drehen und Skalieren der Objekte mit Gesten und einer Maus verwenden. Mit Sprache oder Tastatur können Sie schnell zwischen verschiedenen Modi wechseln.

### <a name="object-manipulation-modes"></a>Objektbearbeitungsmodi

![Bearbeiten der Objekte](images/holosketch-image-06-1000px.png)<br>
*Bearbeiten der Objekte*

### <a name="contextual-and-tool-belt-menus"></a>Kontextmenüs und Menüs für Toolband

**Verwenden des Kontextmenüs**

Tippen Sie doppelt in die Luft, um das Kontextmenü zu öffnen. 

Menüelemente:
* **Layoutoberfläche:** Dies ist ein 3D-Rastersystem, in dem Sie mehrere Objekte layouten und als Gruppe verwalten können. Doppelklicken Sie auf die Layoutoberfläche, um ihr Objekte hinzuzufügen.
* **Primitive:** Verwenden Sie Cubes, Kugeln, Zylinder und Kegel für Massenstudien.
* **OneDrive:** Öffnen Sie das OneDrive, um Objekte zu importieren.
* **Hilfe:** Zeigt den Hilfebildschirm an.

![Kontextmenü](images/holosketch-image-07.png)<br>
*Kontextmenü*

**Verwenden des Menüs "Toolband"**

Move, Rotate, Scale, Save, and Load Scene (Verschieben, Drehen, Skalieren, Speichern und Laden) sind über das Menü "Toolband" verfügbar. 

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
* Mit der Schaltfläche "Wiedergabe" im Menü "Toolband" werden die Manipulationsmoos entiert.

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