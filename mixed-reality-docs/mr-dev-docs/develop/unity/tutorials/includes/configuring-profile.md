---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097895"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 und Windows-XR-Plugin](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a>1. Klonen des Standardkonfigurationsprofils

> [!NOTE]
> Das Konfigurationsprofil ist das Profil der obersten Ebene. Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und überprüfen Sie dann im Inspektorfenster, ob das Konfigurationsprofil **MixedRealityToolkit** auf **DefaultXRSDKConfigurationProfile** festgelegt ist:

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultHoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![„Copy & Paste“-Schaltfläche der MixedRealityToolkit-Komponente von Unity](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

Geben Sie im Fenster „Profil klonen“ einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_XRSDKConfigurationProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultXRSDKConfigurationProfile** zu erstellen:

![Popupfenster „Konfigurationsprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem HoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.

> [!TIP]
> Denken Sie daran, Ihre Arbeit während der Tutorials zu speichern.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Aktivieren des Systems für räumliche Wahrnehmung

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt, dann im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung aktivieren):

![MixedRealityToolkit-Komponente von Unity mit aktiviertem Spatial Awareness-System](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> Für zukünftige Projekte empfiehlt es sich, wenn Ihre App nicht auf die Umgebung reagieren oder mit dieser interagieren muss, „Spatial Awareness“ (räumliche Wahrnehmung) deaktiviert zu lassen, um die Leistungskosten zu senken.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung

Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![MixedRealityToolkit-Komponente von Unity mit ausgewählter Registerkarte „Spatial Awareness“ (räumliche Wahrnehmung)](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

Geben Sie im Fenster „Profil klonen“ einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultXRSDKSpatialAwarenessSystemProfile** zu erstellen:

![Popupfenster „Spatial Awareness-Systemprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle

Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von XR SDK Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:

![MixedRealityToolkit-Komponente von Unity mit erweitertem Abschnitt „Windows Mixed Reality Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie von **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:

![Popupfenster „Raum-Mesh-Betrachterprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung

Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:

![MixedRealityToolkit-Komponente von Unity mit auf „Occlusion“ festgelegter Anzeigeoption „Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert. Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.

Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können. Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen. Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten. Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [MRTK-Leitfaden zur Profilkonfiguration](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) im [MRTK-Dokumentationsportal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).

# <a name="unity-2020--openxr"></a>[Unity 2020 und OpenXR](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a>1. Klonen des Standardkonfigurationsprofils

> [!NOTE]
> Das Konfigurationsprofil ist das Profil der obersten Ebene. Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und überprüfen Sie dann im Inspektorfenster, ob das Konfigurationsprofil **MixedRealityToolkit** auf **DefaultOpenXRConfigurationProfile** festgelegt ist:

![Unity: MixedRealityToolkit-Komponente mit ausgewähltem OpenXR-Standardprofil](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![Unity: Schaltfläche zum Kopieren und Anpassen für das OpenXR-Profil der MixedRealityToolkit-Komponente](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

Geben Sie im Fenster „Profil klonen“ einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_OpenXRConfigurationProfile_, und klicken Sie dann auf die Schaltfläche **Klonen**, um eine bearbeitbare Kopie des **DefaultOpenXRConfigurationProfile** zu erstellen:

![Unity: Popupfenster „Konfigurationsprofil klonen“ des MixedRealityToolkit für das OpenXR-Profil](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:

![Unity: MixedRealityToolkit-Komponente mit neu erstelltem benutzerdefinierten OpenXR angewendet](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.

> [!TIP]
> Denken Sie daran, Ihre Arbeit während der Tutorials zu speichern.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Aktivieren des Systems für räumliche Wahrnehmung

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt, dann im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung aktivieren):

![MixedRealityToolkit-Komponente von Unity mit aktiviertem Spatial Awareness-System](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> Für zukünftige Projekte empfiehlt es sich, wenn Ihre App nicht auf die Umgebung reagieren oder mit dieser interagieren muss, „Spatial Awareness“ (räumliche Wahrnehmung) deaktiviert zu lassen, um die Leistungskosten zu senken.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung

Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![MixedRealityToolkit-Komponente von Unity mit ausgewählter Registerkarte „Spatial Awareness“ (räumliche Wahrnehmung)](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

Geben Sie im Fenster „Profil klonen“ einen passenden **Profilnamen** ein, beispielsweise „GettingStarted_OpenXRSpatialAwarenessSystemProfile“, und klicken Sie dann auf die Schaltfläche **Klonen**, um eine bearbeitbare Kopie des **DefaultXRSDKSpatialAwarenessSystemProfile** zu erstellen:

![Popupfenster „Spatial Awareness-Systemprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle

Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von XR SDK Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:

![MixedRealityToolkit-Komponente von Unity mit erweitertem Abschnitt „Windows Mixed Reality Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie von **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:

![Popupfenster „Raum-Mesh-Betrachterprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung

Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:

![MixedRealityToolkit-Komponente von Unity mit auf „Occlusion“ festgelegter Anzeigeoption „Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert. Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.

Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können. Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen. Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten. Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [MRTK-Leitfaden zur Profilkonfiguration](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) im [MRTK-Dokumentationsportal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).


# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a>1. Klonen des Standardkonfigurationsprofils

> [!NOTE]
> Das Konfigurationsprofil ist das Profil der obersten Ebene. Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und ändern Sie dann im Inspektorfenster das Konfigurationsprofil des **Mixed Reality-Toolkits** in **DefaultHoloLens2ConfigurationProfile**:

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultHoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-1.png)

Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![„Copy & Paste“-Schaltfläche der MixedRealityToolkit-Komponente von Unity](../images/mr-learning-base/base-03-section1-step1-2.png)

Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_HoloLens2ConfigurationProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultHololens2ConfigurationProfile** zu erstellen:

![Popupfenster „Konfigurationsprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step1-3.png)

Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem HoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-4.png)

Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.

> [!TIP]
> Denken Sie daran, Ihre Arbeit während der Tutorials zu speichern.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Aktivieren des Systems für räumliche Wahrnehmung

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt, dann im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung aktivieren):

![MixedRealityToolkit-Komponente von Unity mit aktiviertem Spatial Awareness-System](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> Für zukünftige Projekte empfiehlt es sich, wenn Ihre App nicht auf die Umgebung reagieren oder mit dieser interagieren muss, „Spatial Awareness“ (räumliche Wahrnehmung) deaktiviert zu lassen, um die Leistungskosten zu senken.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung

Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![MixedRealityToolkit-Komponente von Unity mit ausgewählter Registerkarte „Spatial Awareness“ (räumliche Wahrnehmung)](../images/mr-learning-base/base-03-section1-step3-1.png)

Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultMixedRealitySpatialAwarenessSystemProfile** zu erstellen:

![Popupfenster „Spatial Awareness-Systemprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step3-2.png)

Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle

Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:

![MixedRealityToolkit-Komponente von Unity mit erweitertem Abschnitt „Windows Mixed Reality Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step4-1.png)

Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie von **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:

![Popupfenster „Raum-Mesh-Betrachterprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step4-2.png)

Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung

Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:

![MixedRealityToolkit-Komponente von Unity mit auf „Occlusion“ festgelegter Anzeigeoption „Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert. Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.

Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können. Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen. Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten. Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [MRTK-Leitfaden zur Profilkonfiguration](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) im [MRTK-Dokumentationsportal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).
