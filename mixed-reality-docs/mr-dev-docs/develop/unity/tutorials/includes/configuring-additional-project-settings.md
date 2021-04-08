---
ms.openlocfilehash: 20cfe36028c6fe95cbdc79a1ea8884ed9c3cd5bd
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088712"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 und Windows-XR-Plugin](#tab/winxr)

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:

![Unity: Project Settings... Menüpfad](../images/mr-learning-base/base-02-section5-step2-1.png)

Wählen Sie im Fenster „Projekteinstellungen“ **XR-Plug-In-Verwaltung** > **XR-Plug-In-Verwaltung installieren** aus, um die XR-Plug-In-Verwaltung zu installieren:

![Unity: XR-Einstellungen](../images/mr-learning-base/base-02-section5-step2-2.png)

Nachdem Unity die Installation der XR-Plug-In-Verwaltung abgeschlossen hat. Stellen Sie sicher, dass Sie sich in den Einstellungen für die Universelle Windows-Plattform befinden, und aktivieren Sie **XR beim Start initialisieren** sowie das Kontrollkästchen **Windows Mixed Reality**.

![Unity: XR-Einstellungen mit „Windows Mixed Reality SDK hinzufügen“](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Nachdem Unity das Importieren des Windows Mixed Reality SDK abgeschlossen hat, sollte wieder das Fenster des MRTK-Projektkonfigurators angezeigt werden. Wenn dies nicht der Fall ist, verwenden Sie das Unity-Menü, um es zu öffnen.

Verwenden Sie im Fenster des MRTK-Projektkonfigurators die Dropdownliste **Audio spatializer** (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellung zu übernehmen:

![Unity: XR-Einstellungen mit ausgewählter Option „Windows Mixed Reality SDK“](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern. Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist. Weitere Informationen zu diesem Thema finden Sie in den <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutorials zur räumlichen Audiowiedergabe</a>.

Wählen Sie im Fenster „Projekteinstellungen“ **XR-Plug-In-Verwaltung** > **Windows Mixed Reality** > **Laufzeiteinstellungen** aus, und verwenden Sie dann die Dropdownliste **Tiefenpufferformat**, um **16-Bit Tiefe auszuwählen:**

![Unity: Veröffentlichungseinstellungen mit hervorgehobenem Paketnamen](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen. Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">Leistung</a>sdokumentation des MRTK.

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:

![Unity: Veröffentlichungseinstellungen mit Paketnamen](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Der Paketname stellt den eindeutigen Bezeichner für die App dar. Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.

> [!TIP]
> Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird. Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.

# <a name="unity-2020--openxr"></a>[Unity 2020 und OpenXR](#tab/openxr)

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:

![Unity: Project Settings... Menüpfad](../images/mr-learning-base/base-02-section5-step2-1.png)

Wählen Sie im Fenster „Projekteinstellungen“ **XR-Plug-In-Verwaltung** > **XR-Plug-In-Verwaltung installieren** aus, um die XR-Plug-In-Verwaltung zu installieren:

![Unity: XR-Einstellungen mit ausgewählter Option „ XR-Plug-In-Verwaltung installieren“](../images/mr-learning-base/base-02-section5-step2-2.png)

Nachdem Unity die Installation der XR-Plug-In-Verwaltung abgeschlossen hat. Stellen Sie sicher, dass Sie sich in den Einstellungen für die Universelle Windows-Plattform befinden, und aktivieren Sie die Kontrollkästchen **XR beim Start initialisieren**, **OpenXR** und **Microsoft HoloLens-Funktionen**.

![Unity: XR-Einstellungen mit ausgewählten Optionen „OpenXR“ und „Microsoft HoloLens-Funktionen“](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

Navigieren Sie in der Menüleiste oben auf dem Bildschirms zu **Mixed Reality > OpenXR > Empfohlene Projekteinstellungen für HoloLens 2 anwenden**, um eine bessere App-Leistung zu erzielen.

![Mixed Reality-Menü mit ausgewählten Optionen „OpenXR“ und „Empfohlene Projekteinstellungen für HoloLens 2 anwenden“](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

>[!Important]
>Wenn ein rotes Warnsymbol neben den OpenXR-Plugin (Vorschau) angezeigt wird, klicken Sie auf das Symbol, und wählen Sie „Alle korrigieren“, bevor Sie fortfahren. Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.
>![OpenXR-Projektvalidierungsmenü mit allen zur Korrektur ausgewählten Problemen](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)

Nachdem Unity das Importieren der erforderlichen Dateien abgeschlossen hat, sollte wieder das Fenster des MRTK-Projektkonfigurators angezeigt werden. Wenn dies nicht der Fall ist, verwenden Sie das Unity-Menü, um es zu öffnen.

Verwenden Sie im Fenster des MRTK-Projektkonfigurators die Dropdownliste **Audio spatializer** (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellung zu übernehmen:

![MRTK-Konfigurationsfenster mit ausgewählten Standardoptionen](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern. Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist. Weitere Informationen zu diesem Thema finden Sie in den <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutorials zur räumlichen Audiowiedergabe</a>.


Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:

![Veröffentlichungseinstellungen in Unity](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Der Paketname stellt den eindeutigen Bezeichner für die App dar. Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.

> [!TIP]
> Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird. Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, aktivieren Sie das Kontrollkästchen **Virtual Reality Supported** (Virtual Reality unterstützt), klicken Sie auf das **+** -Symbol, und wählen Sie „Windows Mixed Reality“ aus, um das Windows Mixed Reality SDK hinzuzufügen:

![Unity: XR-Einstellungen, „Windows Mixed Reality SDK hinzufügen“ ausgewählt](../images/mr-learning-base/base-02-section5-step2-4.png)

Nachdem Unity das Importieren des Windows Mixed Reality SDK abgeschlossen hat, sollte wieder das Fenster des MRTK-Projektkonfigurators angezeigt werden. Geschieht dies nicht, können Sie es manuell aus dem Unity-Menü öffnen, indem Sie zu **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Konfigurieren) navigieren.

Verwenden Sie im Fenster des MRTK-Projektkonfigurators die Dropdownliste **Audio spatializer** (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellung zu übernehmen:

![MRTK-Konfigurationsfenster](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern. Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist. Weitere Informationen zu diesem Thema finden Sie in den <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutorials zur räumlichen Audiowiedergabe</a>.

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, und verwenden Sie dann die Dropdownliste **Depth Format** (Tiefenformat), um **16-Bit Tiefe** auszuwählen:

![Unity: Tiefe 16 aktivieren](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen. Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Leistung</a>sdokumentation des MRTK.

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:

![Veröffentlichungseinstellungen in Unity. Paketname konfiguriert](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Der Paketname stellt den eindeutigen Bezeichner für die App dar. Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.

> [!TIP]
> Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird. Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.