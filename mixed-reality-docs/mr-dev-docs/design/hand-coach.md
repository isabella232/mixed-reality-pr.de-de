---
title: Hand Coach
description: Hier erfahren Sie, wie 3D-Hände mit hand-Hand ausgelöst werden, wenn das System die Hände des Benutzers nicht erkennt, um ihnen zu helfen.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, Design, Handfasching, immersives Headset, MRTK, Hände, Helfende Hände, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0fe0d87e26d06838c0d1b7935573d9bd8ce258ee
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600429"
---
# <a name="hand-coach"></a>Hand Coach

![Beispiel: Handschn.](images/HandCoach/MRTK_handCoach.jpg)<br>

Handauslöser löst 3D-modellierte Hände aus, wenn das System die Hände des Benutzers nicht erkennt. Dieses Feature ist eine "Unterrichtskomponente", die den Benutzer bei der Anleitung unterstützt, wenn die Geste nicht vermittelt wurde. Wenn Benutzer die angegebene Geste für einen Bestimmten nicht durchgeführt haben, werden die Hände mit einer Verzögerung in die Schleife schleife. Das Hand-Brillen-Paar kann verwendet werden, um das Drücken einer Schaltfläche oder das Aufnehmen eines Hologramms zu darstellen.  

## <a name="hand-coach-provided"></a>Handhand-2016

Das aktuelle Interaktionsmodell stellt eine Vielzahl von Gestensteuerelementen dar, z. B. Scrollen, Fernauswahl und Tippen in der Nähe. Im Folgenden finden Sie eine vollständige Liste der vorhandenen Handgesten, die im<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK bereitgestellt werden:</a>

:::row:::
    :::column:::
       ![Beispiel für Near Select](images/HandCoach/NearSelect.gif)<br>
       **Beispiel für Near Select – Used zeigt, wie Schaltflächen ausgewählt oder interaktionsfähige Objekte geschlossen werden.**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für Tippen in die Luft](images/HandCoach/AirTap.gif)<br>
        **Beispiel für Tippen in die Luft– Wird verwendet, um zu zeigen, wie weit entfernte Objekte ausgewählt werden.**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für "Verschieben"](images/HandCoach/Move.gif)<br>
       **Beispiel für das Verschieben eines Objekts im Raum: Wird verwendet, um zu zeigen, wie ein Hologramm in den Raum bewegt wird**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für "Rotieren"](images/HandCoach/Rotate.gif)<br>
       **Beispiel für Rotate-Used, wie Hologramme oder Objekte gedreht werden**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Beispiel für Skalierung](images/HandCoach/Scale.gif)<br>
       **Beispiel für Skalierung: Wird verwendet, um zu zeigen, wie Hologramme so bearbeitet werden, dass sie größer oder kleiner sind**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für "Palm Up"](images/HandCoach/PalmUp.gif)<br>
        **Beispiel für "Palm up" – Empfohlene Verwendung zum Anzeigen von Handmenüs**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für HandFlip](images/HandCoach/HandFlip.gif)<br>
       **Exmaple of Hand Flip – Another way to bring up Hand Menus**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für Scrollen](images/HandCoach/Scoll.gif)<br>
       **Beispiel für "Scrollen": Wird zum Scrollen einer Liste oder eines langen Dokuments verwendet**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Entwurfskonzepte

Für Hololens2 haben wir Handinteraktionen basierend auf instinktiven und natürlichen Handgesten entworfen. Wir sind der Meinung, dass diese für die meisten Benutzer intuitiv sind, sodass wir keine dedizierten Lernmomente für Gesten erstellt haben. Stattdessen haben wir die Handarbeit erstellt, um Benutzern zu helfen, mehr über diese Gesten zu erfahren, wenn sie hängen bleiben oder mit Hologramminteraktionen nicht vertraut sind. Ohne einen Lernmoment haben wir uns davon aus gefühlt, dass es die beste Option wäre, Benutzern zu zeigen, wie sie eine Aktion ausführen, indem sie demonstriert wird. Wir haben festgestellt, dass Benutzer die Geste herausfinden konnten, aber ein wenig Anleitungen benötigten. Wenn wir feststellen, dass ein Benutzer für einen bestimmten Zeitraum nicht mit einem Objekt interagiert, wird ein Hand-2016 ausgelöst, das die richtige Hand- und Fingerplatzierung zeigt. 

### <a name="intuitive"></a>Intuitiv

Beim Animieren der Hände sollte dies offensichtlich sein und keine Verwirrung verursachen. Die Handanimation ist eine Darstellung der Geste, die Sie dem Benutzer zum Verstehen auffordern möchten. 

Wenn ein Benutzer z. B. eine Schaltfläche drücken soll, wird eine Hand zum Drücken einer Schaltfläche ausgelöst.

![Beispiel: Handschnippen in der Nähe von Tap](images/HandCoach/NearSelect_unity.gif)<br>
*HandGewinde zeigt das Tippen auf ein Gem in der Nähe*  

### <a name="hand-scale"></a>Handskalieren

Wir haben verschiedene Handgrößen mit den Benutzeroberflächenmenüs getestet und dabei den Eindruck bekommen, dass die Größe der Hände ein berohendes Gefühl war, wenn die Hände groß sind. Wenn sie zu klein waren, war es schwierig, die Geste zu erkennen und zu verstehen. 

**Sprachüber und Hände**

Erwarten Sie nicht, dass Benutzer über Voice over auf eine Reihe von Anweisungen lauschen und unterschiedliche Anweisungen über Handarbeit ansehen können. Sequenzieren Sie Ihre Anweisungen, um Benutzern zu helfen, sich zu konzentrieren und um ihre Aufmerksamkeit zu konkurrieren, um die sensorische Überlastung zu reduzieren.


## <a name="can-i-create-my-own"></a>Kann ich meine eigenen erstellen?

Ja! Wir empfehlen Ihnen, Ihre eigene einzigartige Geste für Ihr Spiel zu erstellen und einen Beitrag zur Community zu leisten!
Wir haben eine Maya-Datei mit einer manipulierten Hand bereitgestellt, die für Ihre App verwendet werden kann. Diese kann hier heruntergeladen <a href="files/HandCoach_MRTK.zip">werden: Download</a> HandCoach_MRTK.zip

![Beispiel für animierte Hände in Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Beispiel für animiertes Hand-Poking eines Felds in Maya*


**Empfohlenes Erstellungstool**

Unter den 3D-Frauen entscheiden sich viele für die Verwendung der Maya von Autodesk, die [HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) verwenden kann, um die Art und Weise zu transformieren, wie Ressourcen erstellt werden. Die bereitgestellte Hands-Datei ist eine Maya-Binärdatei, daher wird empfohlen, Maya zum Animieren und Exportieren der Hände zu verwenden. Wenn Sie lieber ein anderes 3D-Programm verwenden möchten, finden Sie hier eine <b>. FBX:</b> <a href="files/HandCoachMRTK_FBX.zip"> Laden Sie HandCoachMRTK_FBX.zip </a> herunter, um Ihr eigenes Controllersetup zu erstellen. 

Wenn Sie die heruntergeladene Maya-Handdatei verwenden, wird empfohlen, die Hände in Unity auf 0,6 herunterskalieren.

![Beispiel: Hand-1-5-5-1-1-4-](images/HandCoach/MayaExample.png)<br>
*Verfälschte Hände*

### <a name="technical-specs"></a>Technische Spezifikationen

*   Die zweihändige Datei ist im Maya Ascii-Format verfügbar.
*    Die rechte und linke Hand ist im Maya-Binärformat verfügbar.
*   Legen Sie Ihre Maya-Datei auf 24 FPS fest.
*   In der Datei gibt es eine linke und rechte Hand, die für zwei händige oder einhändige Gesten verwendet werden kann. Die rechte Seite ist standardmäßig nur sichtbar.
*   Es wird empfohlen, einen Puffer von ca. 10 Frames am Anfang und Ende für Einblendungen zu belassen.
*   Wenn Sie ein Objekt mit einem angegebenen Ziel animieren, wird die bewährte Methode zum Animieren in ein Standardfeld oder NULL verwendet.
*   Wenn die Hand ein physisches Objekt animiert, z. B. ein Feld, ist es eine bewährte Methode, die Übersetzung in Maya nicht zu animieren, sondern darauf zu warten, sie in Unity oder im Code zu animieren.
*   Die sichtbare Animation sollte 1,5 Sekunden beträgt, damit aussagekräftige Informationen übermittelt werden können.
*   Wenn Sie mit Ihrer Animation zufrieden sind:
    *   Auswählen aller Fugen und Backen von Keyframes
    *   Löschen der Controller, Auswählen der Fugen und Gitter und Exportieren als FBX
    *  Wenn mehrere Animationen enthalten sind, können Sie den integrierten Game Exporter von Maya verwenden: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Exportieren aus Maya

Nachdem Sie mit Ihrer Animation zufrieden sind
* Alle Fugen auswählen: Wählen Sie > Hierarchie aus.

     ![Beispiel: Hierarchie im Menü](images/HandCoach/Hierarchy.png)<br>
* Baking ihrer Animation: Wechseln Sie zu Animation > Key > Bake Animation

     ![Beispiel: Speicherort des Bake-Animationsmenüs](images/HandCoach/BakeAnimation.png)<br>
* Löschen Sie das Controllergerät: Outliner > MainR_Grp oder MainL_Grp

     ![Beispiel: Position des Controllermenüs](images/HandCoach/ControllerRig.png)<br>

* Als FBX exportieren: Wählen Sie JNT + Mesh: File > Export Selection (Optionsfeld) > Export Selection (Auswahl exportieren) aus.

     ![Beispiel: Exportieren des Menüspeicherorts für die Auswahl](images/HandCoach/OptionBox.png)<br>

     ![Beispiel: Menüposition](images/HandCoach/SelectionExport.png)<br>

     ![Beispiel: Speicherort des Menüs "Optionen exportieren"](images/HandCoach/FBXSelection.png)<br>


 Wenn Sie als FBX exportieren und in Unity importieren, skalieren Sie die Hände auf 0,6 herunter. Wir haben festgestellt, dass dies ein perfektes Gleichgewicht für die Anzeige der Hände war. 

![Beispiel: Unity-Einstellungen](images/HandCoach/HandHintScale.png)<br>
*Unity-Einstellungen für HandCoach_R prefab in MRTK*


## <a name="implementing-hands-into-your-unity-project"></a>Implementieren von Händen in Ihr Unity-Projekt

### <a name="best-practices"></a>Bewährte Methoden

* Es wird empfohlen, die Hände in Unity auf 0,6 herunterskalieren.
* Die Hände sollten zweimal abgespielt werden, und wenn sie nicht abgeschlossen sind, wird kontinuierlich eine Schleife durchgeführt, bis die Geste abgeschlossen ist. Die Hände sollten zweimal in einer Schleife sein, um sicherzustellen, dass der Benutzer Zeit hatte, sich zu registrieren und die Geste zu sehen. Die Hände sollten zwischen Schleifen ein- und ausblenden. 
 *  Wenn die Hände des Benutzers von HL2-Kameras angezeigt werden, benutzer jedoch nicht die für sie benötigte Interaktion tun, werden die Hände nach 10 Sekunden angezeigt.
*   Wenn die Hände des Benutzers für HL2-Kameras NICHT sichtbar sind, werden die Hände nach 5 Sekunden angezeigt.  
*   Wenn die Hände des Benutzers von HL2-Kameras in der Mitte der Animation sichtbar nachverfolgt werden, wird die Animation abgeschlossen und ausgeblendet.
*   Wenn Sie Voice over verwenden, empfehlen wir, dass dies der Geste der Hand entspricht.
*   Wenn Sie die Hände mindestens einmal gelernt haben, wiederholen Sie die Geste nur, wenn erkannt wird, dass der Benutzer hängen bleibt.
*   Wenn bestimmte Finger-/Handpositionen wichtig sind, stellen Sie sicher, dass Benutzer diese Nuancen in der Animation deutlich erkennen können. Versuchen Sie, die Hände zu verfingen, damit die wichtigsten Teile deutlich sichtbar sind. 
* Wenn Sie eine Verzerrung an den Händen bemerken, müssen Sie zu Den Qualitätseinstellungen von Unity wechseln, um die Anzahl der Brüche zu erhöhen. 
 Wechseln Sie zur Unity-Seite Edit > Project Settings > Quality > Other > Blend Weights (Bearbeiten >-Projekteinstellungen > Andere > Mischungsgewichtungen). Stellen Sie sicher, dass "4 1000" ausgewählt sind, um Smooth Joints (Smooth Joints) zu sehen.

   ![Beispiel: Fenster "Projekteinstellungen"](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>Was Sie vermeiden sollten

* Skalieren der Hände zu groß
* Platzieren der Hände zu nah am Benutzer
* Die Hände sollten nur einmal gelernt werden. Over teaching can cause confusion and messiness
* Laden Sie das neueste MRTK hier herunter, um es in Unity zu installieren: https://github.com/microsoft/MixedRealityToolkit-Unity
  * Material: Teaching_Hand2
  * Skripts: Weitere Informationen finden Sie in den MRTK-Richtlinien für <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> MRTK-Handbücher. </a>
  * Projektspezifische Einstellung
    * Szene auf UWP festgelegt: Anweisungen finden Sie unter [Konfigurieren des Unity-Projekts](../develop/unity/Configure-Unity-Project.md) für Windows Mixed Reality

## <a name="see-also"></a>Siehe auch

* [Interaktionsprinzipien](interaction-fundamentals.md)
* [Erstellungsprozess für Ressourcen](asset-creation-process.md)
* [Gesten](./interaction-fundamentals.md)
* [Installieren der Tools](../develop/install-the-tools.md)
* [Konfigurieren des Unity-Projekts](../develop/unity/Configure-Unity-Project.md)
* [Unity-Entwicklung – Übersicht](../develop/unity/unity-development-overview.md)
* [MRTK 101](/windows/mixed-reality/mrtk-unity/)