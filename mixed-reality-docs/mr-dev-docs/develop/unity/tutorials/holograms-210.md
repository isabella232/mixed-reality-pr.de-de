---
title: 'HoloLens (1. Generation) Eingabe 210: Anvisieren'
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio und HoloLens, um die Details der Konzepte des Anvierens zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gaze, HoloLens, Mixed Reality Academy, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Windows 10
ms.openlocfilehash: e0d761c6292502f381618f8efa1bed9d26f0e6fbac8dbdafa8085e0bb41676ce
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220974"
---
# <a name="hololens-1st-gen-input-210-gaze"></a>HoloLens (1. Generation) Eingabe 210: Anvits

>[!IMPORTANT]
>Die Mixed Reality Academy-Tutorials wurden mit HoloLens (1. Generation), Unity 2017 und Mixed Reality immersive Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen. Diese Tutorials werden **_nicht mit_** den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 und sind möglicherweise nicht mit neueren Versionen von Unity kompatibel.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.

[Anvisiert](../../../design/gaze-and-commit.md) ist die erste Form der Eingabe und zeigt die Absicht und das Bewusstsein des Benutzers an. MR Input 210 (auch als Project Explorer bezeichnet) ist ein tiefer Einblick in konzeptebezogene Konzepte für Windows Mixed Reality. Wir werden unseren Cursorn und Hologrammen kontextbezogenes Bewusstsein hinzufügen und dabei das, was Ihre App über das Anvisieren des Benutzers weiß, voll ausnutzen.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Wir verfügen hier über einen nutzerfreundlichen Astronauten, der Ihnen hilft, Konzepte zum Anvieren zu erlernen. In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md)hatten wir einen einfachen Cursor, der ihrem Anving gerade folgt. Heute bewegen wir einen Schritt über den einfachen Cursor hinaus:

* Wir machen den Cursor und unsere Hologramme anviert: Beides ändert sich je nach Dem, wo der Benutzer sucht oder wo der Benutzer *nicht* sucht. Dies macht sie kontextbewusst.
* Wir fügen dem Cursor und hologramm Feedback hinzu, um dem Benutzer mehr Kontext zu geben, was als Ziel verwendet wird. Dieses Feedback kann audio und visual sein.
* Wir zeigen Ihnen Zielgruppenadressierungstechniken, mit deren Hilfe Benutzer kleinere Ziele erreichen können.
* Wir zeigen Ihnen, wie Sie die Aufmerksamkeit des Benutzers auf Ihre Hologramme mit einem Richtungsindikator lenken.
* Wir vermitteln Ihnen Techniken, um Ihre Hologramme mit dem Benutzer zu nehmen, während er sich in Ihrer Welt bewegt.

>[!IMPORTANT]
>Die in die einzelnen Kapitel unten eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet. Obwohl die Schritt-für-Schritt-Anweisungen genau und aktuell sind, werden möglicherweise Skripts und Visuals in den entsprechenden Videos angezeigt, die veraltet sind. Die Videos bleiben für die Nachwelt enthalten, und da die behandelten Konzepte weiterhin gelten.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR-Eingabe 210: Anvisieren</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Vorbereitung

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10 PC, der mit den richtigen [installierten Tools konfiguriert ist.](../../../develop/install-the-tools.md)
* Einige grundlegende C#-Programmierfunktionen.
* Sie sollten die [MR-Grundlagen 101 abgeschlossen haben.](../../../develop/unity/tutorials/holograms-101.md)
* Ein HoloLens, [das für die Entwicklung konfiguriert ist.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Projektdateien

* Laden Sie [die für](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) das Projekt erforderlichen Dateien herunter. Erfordert Unity 2017.2 oder höher.
* Archivieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht erreichbaren Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem Herunterladen durchschauen möchten, ist er [auf GitHub.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)

### <a name="errata-and-notes"></a>Errata und Hinweise

* In Visual Studio muss "Nur eigenen Code" unter Extras->Optionen->Debuggen deaktiviert (deaktiviert) werden, um Breakpoints im Code zu finden.

## <a name="chapter-1---unity-setup"></a>Kapitel 1: Unity-Setup

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Ziele

* Optimieren von Unity für die HoloLens-Entwicklung
* Importieren von Assets und Einrichten der Szene
* Zeigen Sie den Astronauten in der HoloLens.

### <a name="instructions"></a>Anweisungen

1. Starten Sie Unity.
2. Wählen Sie auf **Neues Projekt** aus.
3. Nennen Sie das **Projekt ModelExplorer**.
4. Geben Sie location als ordner **gaze** ein, den Sie zuvor nicht archiviert haben.
5. Stellen Sie sicher, dass das Projekt auf **3D** festgelegt ist.
6. Klicken Sie **auf Project**.

### <a name="unity-settings-for-hololens"></a>Unity-Einstellungen für HoloLens

Wir müssen Unity wissen lassen, dass die App, die wir exportieren möchten, eine [immersive](../../../design/app-views.md) Ansicht anstelle einer 2D-Ansicht erstellen sollte. Dazu fügen wir HoloLens als Virtual Reality-Gerät hinzu.

1. Wechseln Sie **zu Bearbeiten > Project Einstellungen > Player**.
2. Wählen Sie **im Inspektorbereich** Einstellungen Player-Windows Store **aus.**
3. Erweitern Sie die Gruppe **XR-Einstellungen**.
4. Aktivieren Sie im Abschnitt **Rendering** das Kontrollkästchen **Virtuelle Realität unterstützt**, um eine neue Liste mit **Virtual Reality-SDKs** hinzuzufügen.
5. Überprüfen Sie, ob in der Liste **Windows Mixed Reality** angezeigt wird. Wenn nicht, wählen Sie die Schaltfläche unten in der Liste aus, **+** und wählen Sie Windows **Holographic aus.**

Als Nächstes müssen wir unser Skript-Back-End auf .NET festlegen.

1. Wechseln Sie **zu > Project Einstellungen > Player bearbeiten** (dies ist möglicherweise noch im vorherigen Schritt der Fall).
2. Wählen Sie **im Inspektorbereich** Einstellungen Player-Windows Store **aus.**
3. Stellen Sie **im Abschnitt Einstellungen** Konfiguration sicher, dass **Skripterstellungs-Back-End** auf **.NET festgelegt ist.**

Schließlich aktualisieren wir unsere Qualitätseinstellungen, um eine schnelle Leistung auf dem HoloLens.

1. Wechseln Sie **zu Edit > Project Einstellungen > Quality (Bearbeiten > Project Einstellungen > Quality).**
2. Klicken Sie auf den nach unten zeigenden Pfeil in der **Zeile Standard** unter dem Windows Store Symbol.
3. Wählen **Sie sehr niedrig** für Windows Store Apps **aus.**

### <a name="import-project-assets"></a>Importieren von Projektressourcen

1. Klicken Sie mit **der rechten Maustaste** auf den Ordner Assets im **Project** Bereich.
2. Klicken Sie **auf Paket importieren > Benutzerdefiniertes Paket**.
3. Navigieren Sie zu den heruntergeladenen Projektdateien, und klicken Sie auf **ModelExplorer.unitypackage**.
4. Klicken Sie auf **Öffnen**.
5. Nachdem das Paket geladen wurde, klicken Sie auf **die Schaltfläche Importieren.**

### <a name="setup-the-scene"></a>Einrichten der Szene

1. Löschen Sie in der Hierarchie die **Hauptkamera**.
2. Öffnen Sie **im Ordner HoloToolkit** den **Ordner Input** und dann den **Ordner Prefabs.**
3. Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.
4. Klicken Sie mit der rechten Maustaste **auf das Richtungslicht** in der Hierarchie, und wählen Sie **Löschen aus.**
5. In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:
    * **Dabei kann es sich um einen**
    * **Lichter**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Starten **Sie play mode ▶,** um den Astronauten zu sehen.
7. Klicken **Sie erneut auf Wiedergabemodus▶** um zu **Beenden.**
8. Suchen Sie **Hologramme** Ordner nach dem **Fitbox-Objekt,** und ziehen Sie es in das Stammverzeichnis der **Hierarchie**.
9. Wählen Sie **im Bereich Hierarchie die** Option **Fitbox** aus.
10. Ziehen Sie **die Sammlung "Sollman"** aus **der Hierarchie** auf die **Hologram Collection-Eigenschaft** des Fitbox-Fensters **im Inspektorbereich.**

### <a name="save-the-project"></a>Speichern des Projekts

1. Speichern Sie die neue Szene: **Datei > Speichern der Szene unter**.
2. Klicken Sie **auf Neuer Ordner,** und nennen Sie den Ordner **Scenes**.
3. Nennen Sie die Datei **ModelExplorer,** und speichern Sie sie im **Ordner Scenes.**

### <a name="build-the-project"></a>Erstellen des Projekts

1. Wählen Sie in Unity **Datei > Build Einstellungen.**
2. Klicken **Sie auf Open Scenes hinzufügen,** um die Szene hinzuzufügen.
3. Wählen **Sie universelle Windows Plattform** in der **Liste Plattform aus,** und klicken Sie **auf Plattform wechseln.**
4. Wenn Sie speziell für die Entwicklung HoloLens, legen Sie **Zielgerät** auf **HoloLens.** Andernfalls belasse es auf **Beliebiges Gerät.**
5. Stellen **Sie sicher,** dass build type (Buildtyp) auf **D3D** und **SDK** auf **Latest installed** (SDK 16299 oder neuer) festgelegt ist.
6. Klicken Sie auf **Erstellen**.
7. Erstellen Sie **einen neuen Ordner** mit dem Namen "App".
8. Klicken Sie mit nur einem Klick **auf den Ordner App.**
9. Klicken Sie **auf Ordner auswählen.**

Wenn Unity fertig ist, wird ein Datei-Explorer-Fenster angezeigt.

1. Öffnen Sie den **Ordner App.**
2. Öffnen Sie **modelExplorer Visual Studio Solution**.

Bei der Bereitstellung in HoloLens:

1. Ändern Sie das Ziel über Visual Studio symbolleiste von Debuggen in **Release** und von ARM in **x86.**
2. Klicken Sie auf den Dropdownpfeil neben der Schaltfläche Lokaler Computer, und wählen Sie **Remotecomputer aus.**
3. Geben **Sie ihre HoloLens-IP-Adresse ein,** und legen Sie den Authentifizierungsmodus auf **Universell (unverschlüsselte Protokoll) fest.** Klicken Sie auf **Auswählen**. Wenn Sie Die IP-Adresse Ihres Geräts nicht kennen, finden Sie weitere Informationen unter Einstellungen > Network & Internet > Advanced Options ( Erweiterte **Optionen).**
4. Klicken Sie in der oberen Menüleiste **auf Debuggen -> Ohne Debuggen** starten, oder drücken Sie **STRG+F5.** Wenn Dies die erste Bereitstellung auf Ihrem Gerät ist, müssen Sie es mit [einem Visual Studio.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)
5. Wenn die App bereitgestellt wurde, verknappen Sie **die Fitbox** mit einer **Auswahlgeste.**

Bei der Bereitstellung auf einem immersiven Headset:

1. Ändern Sie über die obere Symbolleiste in Visual Studio Ziel von Debuggen in **Release** und von ARM in **x64.**
2. Stellen Sie sicher, dass das Bereitstellungsziel auf Lokaler **Computer festgelegt ist.**
3. Klicken Sie in der oberen Menüleiste **auf Debuggen -> Ohne Debuggen** starten, oder drücken Sie **STRG+F5.**
4. Wenn die App bereitgestellt wurde, verdringen Sie **die Fitbox,** indem Sie den Trigger auf einen Motion-Controller ziehen.

## <a name="chapter-2---cursor-and-target-feedback"></a>Kapitel 2: Cursor- und Zielfeedback

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Ziele

* Visuelles Cursordesign und -verhalten.
* Anving-basiertes Cursorfeedback.
* Feedback zu hologrammbasiertem Anvieren.

Wir werden unsere Arbeit auf einigen Cursorentwurfsprinzipien beruhen, nämlich:

* Der Cursor ist immer vorhanden.
* Lassen Sie den Cursor nicht zu klein oder groß.
* Vermeiden Sie das Verhindern von Inhalten.

### <a name="instructions"></a>Anweisungen

1. Suchen Sie **im Ordner HoloToolkit\Input\Prefabs** nach dem **InputManager-Objekt.**
2. Drag and drop the **InputManager** onto the **Hierarchy**.
3. Suchen Sie **im Ordner HoloToolkit\Input\Prefabs** nach dem **Objekt Cursor.**
4. Drag and drop the **Cursor** onto the **Hierarchy**.
5. Wählen Sie das **InputManager-Objekt** in der **Hierarchie aus.**
6. Ziehen Sie **das Cursor-Objekt** aus der **Hierarchie** in das **Cursorfeld** **von SimpleSinglePointerSelector** von InputManager am unteren Rand des **Inspectors.**

![Einfache Einrichtung der Einfachzeigerauswahl](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

1. Erstellen Sie die App unter **Datei > Build Einstellungen**.
2. Öffnen Sie den **Ordner App**.
3. Öffnen Sie **modelExplorer Visual Studio Solution**.
4. Klicken **Sie auf Debuggen -> Ohne Debuggen starten,** oder drücken Sie **STRG+F5.**
5. Beobachten Sie, wie der Cursor gezeichnet wird und wie er die Darstellung ändert, wenn er ein Hologramm berührt.

### <a name="instructions"></a>Anweisungen

1. Erweitern Sie **im Bereich** Hierarchie die **GEO_G** ->  -> **Back_Center** Objekt.
2. Doppelklicken Sie auf **Interactible.cs,** um sie in der Visual Studio.
3. Auskommentierung der Zeilen in den **IFocusable.OnFocusEnter()-** und **IFocusable.OnFocusExit()-Rückrufen** in **Interactible.cs.** Diese werden vom InputManager des Mixed Reality Toolkits aufgerufen, wenn der Fokus (entweder durch Anvieren oder durch Zeigen des Controllers) in den Collider des jeweiligen GameObject eintritt und beendet wird.

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>Wir verwenden `EnableKeyword` und `DisableKeyword` höher. Um diese in Ihrer eigenen App mit dem Standard-Shader des Toolkits zu verwenden, müssen Sie die Unity-Richtlinien für den Zugriff auf Materialien über das [Skript befolgen.](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html) In diesem Fall haben wir [](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) bereits die drei Varianten hervorgehobener Materialien in den Ordner Ressourcen aufgenommen (suchen Sie nach den drei Materialien mit Hervorhebung im Namen).

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

1. Erstellen Sie wie zuvor das Projekt, und stellen Sie es im HoloLens.
2. Beobachten Sie, was geschieht, wenn das Anvitätsbild auf ein Objekt ausgerichtet ist und nicht.

## <a name="chapter-3---targeting-techniques"></a>Kapitel 3: Zieltechniken

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Ziele

* Vereinfachen Sie das Ziel von Hologrammen.
* Stabilität natürlicher Kopfbewegungen.

### <a name="instructions"></a>Anweisungen

1. Wählen Sie **im Bereich** Hierarchie das **InputManager-Objekt** aus.
2. Suchen Sie **im Inspektorbereich** nach dem **Skript Anvisierer.** Klicken Sie darauf, um Visual Studio öffnen, wenn Sie einen Blick darauf werfen möchten.
    * Dieses Skript durch iteriert Stichproben von Raycast-Daten und hilft, das Anvieren des Benutzers für die Zielgenauigkeit zu stabilisiert.
3. Im **Inspektor** können Sie den Wert **gespeicherte Stabilitätsbeispiele** bearbeiten. Dieser Wert stellt die Anzahl der Stichproben dar, die der Schützer durch iteriert, um den stabilen Wert zu berechnen.

## <a name="chapter-4---directional-indicator"></a>Kapitel 4: Richtungsindikator

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Ziele

* Fügen Sie dem Cursor einen Richtungsindikator hinzu, um Hologramme zu finden.

### <a name="instructions"></a>Anweisungen

Wir verwenden die Datei **DirectionIndicator.cs,** die:

1. Zeigt den Richtungsindikator an, wenn sich der Benutzer nicht an den Hologrammen befindet.
2. Blenden Sie den Richtungsindikator aus, wenn sich der Benutzer an den Hologrammen befindet.
3. Aktualisieren Sie den Richtungsindikator so, dass er auf die Hologramme zeigt.

Fangen wir also an.

1. Klicken Sie im Bereich  Hierarchie auf das **Objekt "Sollman",** und klicken Sie auf **den Pfeil,** um es zu erweitern.
2. Wählen Sie **im Bereich** Hierarchie das **DirectionalIndicator-Objekt** **unterGraphMan aus.**
3. Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
4. Geben Sie im Menü in das Suchfeld **Richtungsindikator ein.** Wählen Sie das Suchergebnis aus.
5. In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.
6. In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.
7. Erstellen Sie die App, und stellen Sie sie bereit.
8. Sehen Sie sich an, wie das direktionale Indikatorobjekt Ihnen hilft, den Astronauten zu finden.

## <a name="chapter-5---billboarding"></a>Kapitel 5: Beschilderung

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Ziele

* Verwenden Sie die -Brille, damit Hologramme immer ihnen gegenüber stehen.

Wir verwenden die Datei **"Sollen.cs",** um ein GameObject so zu halten, dass es dem Benutzer jederzeit angezeigt wird.

1. Wählen Sie **im Bereich** Hierarchie das **Objekt "Steuerungsman"** aus.
2. Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
3. Geben Sie im Menü in das Suchfeld **Dann ein.** Wählen Sie das Suchergebnis aus.
4. Legen Sie **im Inspektor** die **Pivotachse auf** **Y fest.**
5. Testen Erstellen Sie die App wie zuvor, und stellen Sie sie bereit.
6. Sehen Sie sich an, wie das Objekt "Faces" ihnen gegenübersteht, unabhängig davon, wie Sie den Blickpunkt ändern.
7. Löschen Sie das Skript vorerst aus **der Liste DerMan.**

## <a name="chapter-6---tag-along"></a>Kapitel 6 – Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Ziele

* Verwenden Sie Tag-Along, damit unsere Hologramme uns im Raum folgen.

Während wir an diesem Problem arbeiten, werden wir von den folgenden Entwurfseinschränkungen geleitet:

* Der Inhalt sollte immer einen Blick entfernt sein.
* Der Inhalt sollte nicht im Weg stehen.
* Kopfsperren sind unlösbare Inhalte.

Die hier verwendete Lösung besteht darin, einen "Tag-Along"-Ansatz zu verwenden.

Ein Tag-Along-Objekt verlässt nie vollständig die Ansicht des Benutzers. Sie können sich ein Tag-Along als ein Objekt vorstellen, das mithilfe von Bändern an den Kopf des Benutzers angefügt wird. Während sich der Benutzer bewegt, bleibt der Inhalt auf einen blickbaren Blick, indem er zum Rand der Ansicht gleitet, ohne vollständig zu verlassen. Wenn der Benutzer auf das Tag-Along-Objekt anviert, wird es ausführlicher angezeigt.

Wir verwenden die Datei **SimpleTagalong.cs,** die Folgendes vorsieht:

1. Bestimmen Sie, ob sich das Tag-Along-Objekt innerhalb der Kameragrenzen befindet.
2. Wenn sie sich nicht innerhalb des Ansichts-Frustums befinden, positionieren Sie die Tag-Along teilweise innerhalb des Ansichts-Frustums.
3. Andernfalls positionieren Sie den Tag-Along auf einen Standardabstand zum Benutzer.

Dazu müssen wir zuerst das Skript **Interactible.cs** ändern, um die **TagalongAction** aufzurufen.

1. Bearbeiten Sie **Interactible.cs,** indem Sie Codierungsübung 6.a abschließen (Auskommentierung der Zeilen 84 bis 87 aufheben).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

Das **Skript InteractibleAction.cs,** gekoppelt mit **Interactible.cs,** führt benutzerdefinierte Aktionen aus, wenn Sie auf Hologramme tippen. In diesem Fall verwenden wir eine speziell für das Tag-Along.

* Klicken Sie im Ordner **Skripts** auf das Medienobjekt **TagalongAction.cs,** um es in Visual Studio zu öffnen.
* Schließen Sie die Codierungsübung ab, oder ändern Sie sie in Folgendes:
  * Geben Sie oben in der **Hierarchie** in der Suchleiste **ChestButton_Center** ein, und wählen Sie das Ergebnis aus.
  * Klicken Sie im Bereich **Inspector (Inspektor)** auf die Schaltfläche **Add Component (Komponente hinzufügen).**
  * Geben Sie im Menü in das Suchfeld **Tagalong Action** ein. Wählen Sie das Suchergebnis aus.
  * Suchen Sie **in Hologramme** Ordner nach dem **Tagalong-Medienobjekt.**
  * Wählen Sie das **ChestButton_Center** -Objekt in der **Hierarchie** aus. Ziehen Sie das **TagAlong-Objekt** aus dem **bereich Project** in den **Inspector** in die Object **To Tagalong-Eigenschaft.**
  * Ziehen Sie das **Tagalong Action-Objekt** aus dem **Inspector** in das Feld **Interactible Action** des **Interactible-Skripts.**
* Doppelklicken Sie auf das **Skript TagalongAction,** um es in Visual Studio zu öffnen.

![Interaktive Einrichtung](images/holograms210-interactible.png)

Fügen Sie Folgendes hinzu:

* Fügen Sie der PerformAction-Funktion im TagalongAction-Skript Funktionalität hinzu (geerbt von InteractibleAction).
* Fügen Sie dem anvappbaren Objekt Einfügezeichen hinzu, und legen Sie die Pivotachse auf XY fest.
* Fügen Sie dann einfache Tag-Along zum -Objekt hinzu.

Dies ist unsere Lösung aus **"TagalongAction.cs":**

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* Testen Erstellen Sie die App, und stellen Sie sie bereit.
* Sehen Sie sich an, wie der Inhalt dem Mittelpunkt des Anverweisepunkts folgt, aber nicht kontinuierlich und ohne Blockieren.