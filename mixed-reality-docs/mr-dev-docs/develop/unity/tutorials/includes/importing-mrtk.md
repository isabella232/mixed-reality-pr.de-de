---
ms.openlocfilehash: 7fd590713322c296cbbb14e133b1085aa27bb0197b70d1feca1ecb59ed61a3c7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201725"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 und OpenXR](#tab/openxr)

Klicken Sie nach dem Öffnen von **MixedRealityFeatureTool** auf **Start**, um mit dem Mixed Reality-Featuretool loszulegen.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Der erste Schritt besteht im Verweisen des Mixed Reality-Featuretools auf Ihren **Projektpfad** mithilfe der Schaltfläche mit den **Auslassungspunkten**. Klicken Sie auf die Schaltfläche mit den drei Auslassungspunkten neben dem Projektpfad, und navigieren Sie im Explorer zu Ihrem Projektordner, z. B. _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Wenn Sie den Ordner Ihres Projekts gefunden haben, klicken Sie auf die Schaltfläche „Öffnen“, um zum Mixed Reality-Featuretool zurückzukehren. Klicken Sie dann auf **Discover Features** (Features ermitteln).

> [!NOTE]
> Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen. Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.

> [!Important]
> Das Mixed Reality-Featuretool führt eine Überprüfung durch, um sicherzustellen, dass die Weiterleitung an einen Unity-Projektordner erfolgt. Der Ordner muss die Ordner „Assets“, „Packages“ und „Project Settings“ enthalten.

Die Features sind nach Kategorie gruppiert, um die Suche zu erleichtern. Klicken Sie auf die Dropdownliste **Mixed Reality Toolkit**, um Pakete im Zusammenhang mit dem Mixed Reality Toolkit zu finden, und klicken Sie auf die Dropdownliste **Plattformunterstützung**, um Pakete für verschiedene unterstützende Plattformen zu finden.

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

Überprüfen Sie **die Mixed Reality Toolkit Foundation**, und klicken Sie auf die Dropdownliste daneben, um **MRTK 2.7.2** auszuwählen. Überprüfen Sie auch das **Mixed Reality OpenXR-Plug-In 1.0.0,** , und klicken Sie auf die Dropdownliste daneben, um die neueste verfügbare Version auszuwählen. Klicken Sie dann auf die Schaltfläche **Get features** (Features abrufen), um die ausgewählten Pakete herunterzuladen.

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

Klicken Sie dann auf die Schaltfläche **Validate** (Überprüfen), um das ausgewählte Paket zu überprüfen, Es wird ein Popupfenster mit der Nachricht **No validation issues were detected** (Bei der Überprüfung wurden keine Probleme erkannt) angezeigt. Klicken Sie auf **OK**, um das Popup zu schließen, und klicken Sie auf die Schaltfläche **Import** (Importieren).

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


Klicken Sie auf die Schalftläche **Approve** (Genehmigen), um dem Projekt das **Mixed Reality-Toolkit** hinzuzufügen.

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>Konfigurieren des Unity-Projekts

Nachdem Unity den Import des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, wird eine Warnmeldung angezeigt, um den Unity-Editor neu zu starten, um Back-Ends für das neue Plug-In-System zu aktivieren. Klicken Sie auf **Ja**.

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

Sobald Unity neu startet, sollte das Fenster „MRTK Project Configurator“ (MRTK-Projektkonfigurator) angezeigt werden. Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) wechseln:

![Öffnen des Fensters „MRTK Project Configurator“](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

Klicken Sie auf **Unity OpenXR-Plug-In**, um die XR-Plug-In-Verwaltung zu aktivieren und ihrem Projekt die erforderlichen Pakete hinzuzufügen.

![Hinzufügen des Unity OpenXR-Plug-Ins (Add Unity OpenXR Plugin) ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

Dadurch werden die erforderlichen Unity-Pakete für die XR-Plug-In-Verwaltung importiert. Sobald Sie fertig sind, klicken Sie im MRTK-Projektkonfigurator auf **Show XR Plug-In Management Settings** (XR-Plug-In-Verwaltungseinstellungen anzeigen).

![Anzeigen der XR-Plug-In-Verwaltungseinstellungen (Show XR Plug-In Management Settings) ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

Dadurch wird das Fenster **Project Settings** (Projekteinstellungen) geöffnet. Stellen Sie im Fenster mit den Projekteinstellungen unter **XR Plug-In Management** (XR-Plug-In-Verwaltung) sicher, dass Sie sich in den Einstellungen der universellen Windows Plattform befinden (Registerkarte mit dem Windows-Logo). Stellen Sie außerdem sicher, dass **Initialize XR on Startup** (XR beim Start initialisieren) aktiviert ist, klicken Sie dann auf die Kontrollkästchen **OpenXR** und **Microsoft HoloLens feature set** (Microsoft HoloLens-Featuresatz), um sie zu aktivieren.

![Aktivieren von Open XR (Enable Open XR)](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

Sobald Sie das Kontrollkästchen „OpenXR“ aktiviert haben, wird im „MRTK Project Configurator“-Fenster die aktualisierte Meldung mit der Schaltfläche **Apply Settings** (Einstellungen anwenden) angezeigt. Klicken Sie auf die Schaltfläche **Apply Settings** (Einstellungen anwenden). 

![Fenster 1 mit Projekteinstellungen](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

Wenn Sie auf „Apply Settings“ (Einstellungen anwenden) klicken, wird diese Fehlermeldung möglicherweise in der Konsole angezeigt. Sie können fortfahren, wenn dies der einzige Fehler oder gar kein Fehler vorhanden ist.

![OpenXR-Remoting-Fehlermeldung](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

Klicken Sie zum Überprüfen der OpenXR-Konfiguration unter **XR Plug-in Management** (XR-Plug-In-Verwaltung) auf **OpenXR**, und überprüfen Sie die folgenden Elemente:
* Tiefenübermittlungsmodus: **Tiefe 16 Bit**
* Interaktionsprofile: **Microsoft-Handinteraktionsprofil**

![Fenster 2 mit Projekteinstellungen](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen. Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der Leistungsdokumentation zum MRTK.


Klicken Sie im Fenster **MRTK Project Configurator** auf **Weiter**, und klicken Sie dann auf die Schaltfläche **Anwenden**, um die Einstellungen anzuwenden. (Wenn Sie das Fenster geschlossen hatten, können Sie es manuell öffnen, indem Sie zu **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) wechseln.)

![Fenster 3 mit Projekteinstellungen](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Fenster 4 mit Projekteinstellungen](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

Nachdem Sie auf „Anwenden“ geklickt haben, versucht Unity einen Neustart, damit das Eingabesystem wirksam wird. Klicken Sie auf **Anwenden**, um den Unity-Editor neu zu starten.

### <a name="configure-additional-project-settings"></a>Konfigurieren zusätzlicher Projekteinstellungen

Wählen Sie im Unity-Menü **Bearbeiten** > **Projekteinstellungen...** aus, um das Fenster Projekteinstellungen zu öffnen.

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:

![Veröffentlichungseinstellungen in Unity. Paketname konfiguriert](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Der Paketname stellt den eindeutigen Bezeichner für die App dar. Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.

> [!TIP]
> Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird. Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 und Windows-XR-Plugin](#tab/winxr)

Klicken Sie nach dem Öffnen von **MixedRealityFeatureTool** auf **Start**, um mit dem Mixed Reality-Featuretool loszulegen.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Der erste Schritt besteht im Verweisen des Mixed Reality-Featuretools auf Ihren **Projektpfad** mithilfe der Schaltfläche mit den **Auslassungspunkten**. Klicken Sie auf die Schaltfläche mit den drei Auslassungspunkten neben dem Projektpfad, und navigieren Sie im Explorer zu Ihrem Projektordner, z. B. _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


Wenn Sie den Ordner Ihres Projekts gefunden haben, klicken Sie auf die Schaltfläche „Öffnen“, um zum Mixed Reality-Featuretool zurückzukehren. Klicken Sie dann auf **Discover Features** (Features ermitteln).

> [!NOTE]
> Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen. Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.

> [!Important]
> Das Mixed Reality-Featuretool führt eine Überprüfung durch, um sicherzustellen, dass die Weiterleitung an einen Unity-Projektordner erfolgt. Der Ordner muss die Ordner „Assets“, „Packages“ und „Project Settings“ enthalten.

Die Features sind nach Kategorie gruppiert, damit sie leichter zu finden sind. Klicken Sie auf das Dropdownmenü **Mixed Reality-Toolkit**, um Pakete im Zusammenhang mit dem Mixed Reality-Toolkit zu finden.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Aktivieren Sie das Kontrollkästchen **Mixed Reality Toolkit Foundation**, und klicken Sie auf die Dropdownliste daneben, um **MRTK 2.7.0** auszuwählen. Klicken Sie dann auf die Schaltfläche **Get Features** (Features abrufen), um die ausgewählten Pakete herunterzuladen.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Klicken Sie dann auf die Schaltfläche **Validate** (Überprüfen), um das ausgewählte Paket zu überprüfen, Es wird ein Popupfenster mit der Nachricht **No validation issues were detected** (Bei der Überprüfung wurden keine Probleme erkannt) angezeigt. Klicken Sie auf **OK**, um das Popup zu schließen, und klicken Sie auf die Schaltfläche **Import** (Importieren).

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


Klicken Sie auf die Schalftläche **Approve** (Genehmigen), um dem Projekt das **Mixed Reality-Toolkit** hinzuzufügen.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Konfigurieren des Unity-Projekts

Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des MRTK-Projektkonfigurators angezeigt werden. Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) wechseln:

![Öffnen des MRTK-Konfiguratortools](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

Klicken Sie auf **Built-in Unity Plugin (non-OpenXR)** (Integriertes Unity-Plug-In (nicht OpenXR)), um die XR-Plug-In-Verwaltung zu aktivieren und ihrem Projekt die erforderlichen Pakete hinzuzufügen.

![ MRTK-Konfiguratortool](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> Der obige Screenshot stammt aus Unity 2020. Wenn Sie Unity 2019 verwenden, wählen Sie **XR SDK/XR Management** aus.

Dadurch werden die erforderlichen Unity-Pakete für die XR-Plug-In-Verwaltung importiert. Sobald Sie fertig sind, klicken Sie im MRTK-Projektkonfigurator auf **Show Settings** (Einstellungen anzeigen).

![Fenster mit Player-Einstellungen](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

Hierdurch wird das Fenster **Project Settings** (Projekteinstellungen) geöffnet. Stellen Sie im Fenster „Project Settings“ unter **XR Plug-In Management** sicher, dass Sie sich in den Einstellungen der universellen Windows-Plattform befinden. Stellen Sie außerdem sicher, dass **Initialize XR on Startup** (XR beim Start initialisieren) aktiviert ist, und aktivieren Sie das Kontrollkästchen **Windows Mixed Reality**.

![Fenster mit Player-Einstellungen, „Mixed Reality-xrsdk“ aktivieren](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Nachdem Unity das Importieren des Windows Mixed Reality SDK abgeschlossen hat, sollte wieder das Fenster des MRTK-Projektkonfigurators angezeigt werden. Wenn dies nicht der Fall ist, verwenden Sie das Unity-Menü, um es zu öffnen.

Klicken Sie im Fenster des MRTK-Projektkonfigurators auf **Weiter**, und verwenden Sie dann die Dropdownliste „Audio spatializer“ (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellung zu übernehmen:

![MRTK-Projektkonfigurator-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:

> * Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) der [Leistung](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)sdokumentation von MRTK.
> * Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung. Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.

> [!TIP]
> Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern. Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist. Weitere Informationen zu diesem Thema finden Sie in den <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutorials zur räumlichen Audiowiedergabe</a>.

Klicken Sie auf **Weiter** und dann im Fenster des MRTK-Projektkonfigurators auf **Fertig**, um die Unity-Projektkonfiguration für XRSDK fertig zu stellen.

### <a name="configure-additional-project-settings"></a>Konfigurieren zusätzlicher Projekteinstellungen

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:

Wählen Sie im Fenster „Projekteinstellungen“ **XR-Plug-In-Verwaltung** > **Windows Mixed Reality** > **Laufzeiteinstellungen** aus, und verwenden Sie dann die Dropdownliste **Tiefenpufferformat**, um **16-Bit Tiefe** auszuwählen:

![Unity: Tiefe 16 aktivieren](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen. Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der Leistungsdokumentation zum MRTK.

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:

![Veröffentlichungseinstellungen in Unity. Paketname konfiguriert](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Der Paketname stellt den eindeutigen Bezeichner für die App dar. Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.

> [!TIP]
> Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird. Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

Klicken Sie nach dem Öffnen von **MixedRealityFeatureTool** auf **Start**, um mit dem Mixed Reality-Featuretool loszulegen.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Der erste Schritt besteht im Verweisen des Mixed Reality-Featuretools auf Ihren **Projektpfad** mithilfe der Schaltfläche mit den **Auslassungspunkten**. Klicken Sie auf die Schaltfläche mit den drei Auslassungspunkten neben dem Projektpfad, und navigieren Sie im Explorer zu Ihrem Projektordner, z. B. _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Wenn Sie den Ordner Ihres Projekts gefunden haben, klicken Sie auf die Schaltfläche „Öffnen“, um zum Mixed Reality-Featuretool zurückzukehren. Klicken Sie dann auf **Discover Features** (Features ermitteln).

> [!NOTE]
> Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen. Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.

> [!Important]
> Das Mixed Reality-Featuretool führt eine Überprüfung durch, um sicherzustellen, dass die Weiterleitung an einen Unity-Projektordner erfolgt. Der Ordner muss die Ordner „Assets“, „Packages“ und „Project Settings“ enthalten.

Die Features sind nach Kategorie gruppiert, damit sie leichter zu finden sind. Klicken Sie auf das Dropdownmenü **Mixed Reality-Toolkit**, um Pakete im Zusammenhang mit dem Mixed Reality-Toolkit zu finden.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Aktivieren Sie das Kontrollkästchen **Mixed Reality Toolkit Foundation**, und klicken Sie auf die Dropdownliste daneben, um **MRTK 2.7.0** auszuwählen. Klicken Sie dann auf die Schaltfläche **Get Features** (Features abrufen), um die ausgewählten Pakete herunterzuladen.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Klicken Sie dann auf die Schaltfläche **Validate** (Überprüfen), um das ausgewählte Paket zu überprüfen, Es wird ein Popupfenster mit der Nachricht **No validation issues were detected** (Bei der Überprüfung wurden keine Probleme erkannt) angezeigt. Klicken Sie auf **OK**, um das Popup zu schließen, und klicken Sie auf die Schaltfläche **Import** (Importieren).

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

Klicken Sie auf die Schalftläche **Approve** (Genehmigen), um dem Projekt das **Mixed Reality-Toolkit** hinzuzufügen.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Konfigurieren des Unity-Projekts

Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des MRTK-Projektkonfigurators angezeigt werden. Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) wechseln:

![Unity: Menüpfad für „Configure Unity Project“](../images/mr-learning-base/base-02-section5-step1-1.png)

Klicken Sie auf **Legacy XR**, um Legacy-XR zu aktivieren und ihrem Projekt die erforderlichen Pakete hinzuzufügen.

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

Klicken Sie auf die Schaltfläche „Weiter“, um XR-Pipelineeinstellungen für Legacy-XR zu aktivieren.

![Unity MRTK-Konfigurationsfenster](../images/mr-learning-base/base-02-section5-step1-3.PNG)

Stellen Sie im Fenster des MRTK-Projektkonfigurators sicher, dass alle Optionen aktiviert sind, und verwenden Sie außerdem die Dropdownliste **Audio spatializer** (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellung zu übernehmen:

![MRTK-Konfigurationsfenster](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:

> * Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) der [Leistung](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)sdokumentation von MRTK.
> * Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung. Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.

> [!TIP]
> Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern. Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist. Weitere Informationen zu diesem Thema finden Sie in den <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutorials zur räumlichen Audiowiedergabe</a>.

Klicken Sie auf **Weiter** und dann im Fenster des MRTK-Projektkonfigurators auf die Schaltfläche **Fertig**, um die Unity-Projektkonfiguration für Legacy-XR fertig zu stellen.

### <a name="configure-additional-project-settings"></a>Konfigurieren zusätzlicher Projekteinstellungen

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, und verwenden Sie dann die Dropdownliste **Depth Format** (Tiefenformat), um **16-Bit Tiefe** auszuwählen:

![Unity: Tiefe 16 aktivieren](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen. Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der Leistungsdokumentation zum MRTK.

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:

![Veröffentlichungseinstellungen in Unity. Paketname konfiguriert](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Der Paketname stellt den eindeutigen Bezeichner für die App dar. Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.

> [!TIP]
> Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird. Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.
