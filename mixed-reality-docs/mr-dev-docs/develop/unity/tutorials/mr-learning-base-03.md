---
title: 'Tutorials zu den ersten Schritten: 3 Konfigurieren der MRTK-Profile'
description: In diesem Kurs erfahren Sie, wie Sie die MRTK-Profile (Mixed Reality Toolkit) konfigurieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, räumliche Wahrnehmung
ms.localizationpriority: high
ms.openlocfilehash: dc30997bbb43b29bf2495aa98be392af6885f6b8
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112907006"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Konfigurieren der MRTK-Profile

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie die MRTK-Profile angepasst und konfiguriert werden.

Bei den <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK-Profilen</a> handelt es sich um eine Struktur geschachtelter Profile, aus denen die Konfigurationsinformationen für die Initialisierung der MRTK-Systeme und -Funktionen bestehen. Das Profil der obersten Ebene, das Konfigurationsprofil, enthält für jedes der primären Kernsysteme geschachtelte Profile. Jedes geschachtelte Profil ist so konzipiert, dass das Verhalten des entsprechenden Systems konfiguriert wird.

Dieses Beispiel veranschaulicht insbesondere, wie das Gittermodell zur räumlichen Wahrnehmung durch Ändern der Einstellungen des Betrachters für räumliche Gittermodelle ausgeblendet wird. Jedoch können Sie dieselben Prinzipien befolgen, um beliebige Einstellungen oder Werte in den MRTK-Profilen anzupassen.

Wie Sie bei der Bereitstellung Ihres Projekts in Ihrer HoloLens 2 während des [vorherigen Tutorials](mr-learning-base-02.md#congratulations) gesehen haben, ist das <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a>-Gittermodell (für räumliche Wahrnehmung) eine Sammlung von Gittermodellen, die die Geometrie der Umgebung darstellen. Es ist eine hilfreiche Visualisierung für die anfängliche Anzeige, die jedoch in der Regel deaktiviert ist, um die visuelle Ablenkung und die zusätzliche Leistungseinbuße durch die Aktivierung zu vermeiden.

## <a name="objectives"></a>Ziele

* Erfahren, wie MRTK-Profile angepasst und konfiguriert werden
* Ausblenden des Gittermodells für räumliche Wahrnehmung

## <a name="changing-the-spatial-awareness-display-option"></a>Ändern der Anzeigeoptionen für räumliche Wahrnehmung

Dies sind die wichtigsten Schritte, die Sie ausführen, um das Gittermodell zur räumlichen Wahrnehmung auszublenden:

1. Klonen des Standardkonfigurationsprofils
2. Aktivieren des Systems für räumliche Wahrnehmung
3. Klonen des Standardprofils des Systems für räumliche Wahrnehmung
4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle
5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung

> [!NOTE]
> Standardmäßig können die MRTK-Profile nicht bearbeitet werden. Es handelt sich um Standardprofilvorlagen, die Sie zuerst klonen müssen, um sie bearbeiten zu können. Es gibt mehrere verschachtelte Profilebenen. Es ist daher gängige Praxis, mehrere Profile zu klonen und zu bearbeiten, wenn Einstellungen konfiguriert werden sollen.

### <a name="1-clone-the-default-configuration-profile"></a>1. Klonen des Standardkonfigurationsprofils

> [!NOTE]
> Das Konfigurationsprofil ist das Profil der obersten Ebene. Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und ändern Sie dann im Inspektorfenster das Konfigurationsprofil des **Mixed Reality-Toolkits** in **DefaultHoloLens2ConfigurationProfile**:

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultHoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-1.png)

Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![„Copy & Paste“-Schaltfläche der MixedRealityToolkit-Komponente von Unity](images/mr-learning-base/base-03-section1-step1-2.png)

Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_HoloLens2ConfigurationProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultHololens2ConfigurationProfile** zu erstellen:

![Popupfenster „Konfigurationsprofil klonen“ des MixedRealityToolkit von Unity](images/mr-learning-base/base-03-section1-step1-3.png)

Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem HoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-4.png)

Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.

> [!TIP]
> Denken Sie daran, Ihre Arbeit während der Tutorials zu speichern.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Aktivieren des Systems für räumliche Wahrnehmung

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt, dann im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung aktivieren):

![MixedRealityToolkit-Komponente von Unity mit aktiviertem Spatial Awareness-System](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> Für zukünftige Projekte empfiehlt es sich, wenn Ihre App nicht auf die Umgebung reagieren oder mit dieser interagieren muss, „Spatial Awareness“ (räumliche Wahrnehmung) deaktiviert zu lassen, um die Leistungskosten zu senken.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung

Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![MixedRealityToolkit-Komponente von Unity mit ausgewählter Registerkarte „Spatial Awareness“ (räumliche Wahrnehmung)](images/mr-learning-base/base-03-section1-step3-1.png)

Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultMixedRealitySpatialAwarenessSystemProfile** zu erstellen:

![Popupfenster „Spatial Awareness-Systemprofil klonen“ des MixedRealityToolkit von Unity](images/mr-learning-base/base-03-section1-step3-2.png)

Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessSystemProfile](images/mr-learning-base/base-03-section1-step3-3.png)

[!INCLUDE[](includes/configuring-profile.md)]

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung

Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:

![MixedRealityToolkit-Komponente von Unity mit auf „Occlusion“ festgelegter Anzeigeoption „Raum-Mesh-Betrachter“](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert. Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.

Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können. Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen. Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten. Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [MRTK-Leitfaden zur Profilkonfiguration](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) im [MRTK-Dokumentationsportal](/windows/mixed-reality/mrtk-unity).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie MRTK-Profile und Einstellungen klonen, anpassen und konfigurieren.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 4. Positionieren von Objekten in der Szene](mr-learning-base-04.md)