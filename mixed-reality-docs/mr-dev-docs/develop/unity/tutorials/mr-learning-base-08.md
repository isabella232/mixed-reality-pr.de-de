---
title: Verwenden von Eye Tracking
description: In diesem Kurs erfahren Sie, wie Sie Eye Tracking in Ihren Mixed Reality-Apps mit dem Mixed Reality Toolkit (MRTK) verwenden.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Eye Tracking
ms.localizationpriority: high
ms.openlocfilehash: bf7bd266eb471193979c588d97d14dd37aed175e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982885"
---
# <a name="8-using-eye-tracking"></a>8. Verwenden von Eye Tracking

In diesem Tutorial erfahren Sie, wie Sie Eye Tracking für HoloLens 2 aktivieren und Objekten Eye Tracking hinzufügen, um Aktionen auszulösen, wenn der Benutzer die Objekte ansieht.

> [!NOTE]
> Wenn Sie dieses Projekt auch in HoloLens (1. Generation) bereitstellen, beachten Sie, dass Eye Tracking nur in HoloLens 2 unterstützt wird.

## <a name="objectives"></a>Ziele

* Erfahren, wie Eye Tracking für HoloLens 2 aktiviert wird
* Erfahren, wie Eye Tracking zum Auslösen von Aktionen verwendet wird

[!INCLUDE[](includes/ensuring-eye-gaze-capabality.md)]

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Aktivieren des Anvisierens mit den Augen im Blickanbieter

Wählen Sie im Hierarchiefenster das Objekt **MixedRealityToolkit** aus, wählen Sie dann im Inspektorfenster die Registerkarte „MixedRealityToolkit > **Input**“ aus, und führen Sie die folgenden Schritte aus:

* Klonen Sie das Profil **DefaultHoloLens2InputSystemProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_HoloLens2InputSystemProfile_
* Erweitern Sie den Abschnitt **Pointers** (Zeiger)
* Klonen Sie das Profil **DefaultMixedRealityPointerProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealityPointerProfile_
* Suchen Sie den Abschnitt **Gaze Settings** (Blickeinstellungen), und aktivieren Sie das Kontrollkästchen **Is Eye Tracking Enabled** (Ist Eye Tracking aktiviert)

![Unity MixedRealityToolkit-Komponente mit neu erstellten, angewendeten Profilen und aktiviertem Eye Tracking](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der MRTK-Profile](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Aktivieren von simuliertem Eye Tracking für den Unity-Editor

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte **Input** (Eingabe). Führen Sie dann Folgendes aus:

* Klappen Sie den Abschnitt **Input Data Providers** > **Input Simulation Service** (Eingabedatenanbieter > Eingabesimulationsdienst) auf
* Klonen Sie das Profil **DefaultMixedRealityInputSimulationProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealityInputSimulationProfile_
* Suchen Sie die **„Anvisieren mit den Augen“-Simulation**, und legen Sie den **Standardmodus für die „Anvisieren mit den Augen“-Simulation** auf **Vorwärts gerichtete Kameraachse** fest.

![Unity mit ausgewähltem TextMeshPro-Objekt](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Hinzufügen von Eye Tracking zu Objekten

Erweitern Sie im Hierarchie Fenster **RoverExplorer** > **Buttons**, und wählen Sie dann alle drei untergeordneten Schaltflächenobjekte aus:

![Unity mit ausgewähltem Button-Objekt](images/mr-learning-base/base-08-section4-step1-1.png)

Während die drei Button-Objekte noch ausgewählt sind, verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um allen ausgewählten Objekten die **EyeTrackingTarget**-Komponente hinzuzufügen:

![Unity mit ausgewähltem TextMeshPro-Objekt und hinzugefügten Komponenten](images/mr-learning-base/base-08-section4-step1-2.png)

Klappen Sie im Hierarchiefenster **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro** auf

Wählen Sie anschließend im Hierarchiefenster das Schaltflächenobjekt **Hints** (Hinweise) aus, und konfigurieren Sie die **EyeTrackingTarget**-Komponente wie folgt:

* Im Ereignisabschnitt **On Look At Start ()**
  * Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
  * Weisen Sie das **TextMeshPro**-Objekt von der Schaltfläche **Hints** (Hinweise) dem Feld **None (Object)** (Ohne (Objekt)) zu
  * Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TextMeshPro** > **float fontSize** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
  * Legen Sie das Argument auf **0,06** fest, um den aktuellen Schriftgrad von 0,04 um 50 % zu erhöhen
* Im Ereignisabschnitt **On Look Away ()**
  * Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
  * Weisen Sie das **TextMeshPro**-Objekt von der Schaltfläche **Hints** (Hinweise) dem Feld **None (Object)** (Ohne (Objekt)) zu
  * Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TextMeshPro** > **float fontSize** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
  * Legen Sie das Argument auf **0,04** fest, um den Schriftgrad wieder auf 0,04 zurückzusetzen

![Unity mit ausgewähltem Hints TextMeshPro-Objekt und konfigurierter EyeTrackingTarget-Komponente](images/mr-learning-base/base-08-section4-step1-3.png)

**Wiederholen** Sie diesen Schritt für die Schaltflächenobjekte **Explode** (Explodieren) und **Reset** (Zurücksetzen), um Eyetracking für die verbleibenden Schaltflächen zu konfigurieren.

Wenn Sie jetzt in den Spielmodus wechseln, dann die rechte Maustaste drücken und sie gedrückt halten, während Sie die Maus bewegen, bis der Blick auf eine der Schaltflächen trifft, sehen Sie, dass sich der Schriftgrad des Texts um 50 % vergrößert und wieder zur normalen Größe zurückkehrt, wenn Sie den Blick abwenden:

![Geteilte Ansicht des Unity-Wiedergabemodus mit Anvisier-Zugriff per Eye Tracking auf Ziel und Schaltflächenbezeichnung „Explode“](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie Eye Tracking für HoloLens 2 aktivieren und Objekten Eye Tracking hinzufügen, um Aktionen auszulösen, wenn der Benutzer die Objekte ansieht.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 9. Verwenden von Sprachbefehlen](mr-learning-base-09.md)
