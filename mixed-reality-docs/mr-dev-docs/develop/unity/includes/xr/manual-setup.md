---
ms.openlocfilehash: c5276943bab0ddc961342f879c0cf4f8986aa7b4f67b16c9c8b5415ca6fc58fd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202716"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Installieren Sie das OpenXR-Plug-In mit der neuen Anwendung Mixed Reality Feature Tool. Befolgen Sie die [Installations- und Nutzungsanweisungen,](../../welcome-to-mr-feature-tool.md) und wählen Sie das **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie **Plattformunterstützung** aus:

![Mixed Reality Fenster "Featuretoolpakete" mit hervorgehobener "xr-Plug-In öffnen"](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Festlegen des Buildziels

Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Build Einstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](../../images/wmr-config-img-3.png)

Wenn Sie HoloLens 2 als Ziel verwenden, müssen Sie zur universellen Windows Plattform wechseln:

1. Wählen Sie **Datei > Build Einstellungen... aus.**
2. Wählen Sie in der Liste Plattform die Option **Universal Windows Platform** und dann Plattform **wechseln** aus.
3. Legen Sie **Architecture** (Architektur) auf **ARM64** fest.
4. Legen Sie **Zielgerät** auf **HoloLens** fest
5. Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.
6. Festlegen der **Ziel-SDK-Version** auf **"Latest installed" (Neueste Installation)**

![Screenshot des Fensters "Build Einstellungen" im Unity-Editor mit hervorgehobener "Universal Windows Platform"](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Konfigurieren der XR-Plug-In-Verwaltung für OpenXR

So legen Sie OpenXR als Runtime in Unity fest:

1. Navigieren Sie im Unity-Editor zu **Bearbeiten > Project Einstellungen**
2. Wählen Sie in der Liste der Einstellungen die Option **XR-Plug-In-Verwaltung** aus (sollte bereits installiert sein, wenn Sie das Mixed Reality OpenXR-Plug-In mit MRFT installiert haben).
3. Aktivieren Sie das Kontrollkästchen **XR beim Start initialisieren.**
4. Wenn Sie desktop-VR als Ziel verwenden, bleiben Sie auf der Registerkarte PC Standalone (Monitor) und aktivieren Sie die Kontrollkästchen **OpenXR** und **Windows Mixed Reality Featuresets.**
5. Wenn Sie HoloLens 2 als Ziel verwenden, wechseln Sie zur Registerkarte Universelle Windows Plattform (das Windows-Logo), und wählen Sie die Felder **OpenXR** und **Microsoft HoloLens Featuresatz** aus.

![Screenshot des im Unity-Editor geöffneten Bereichs "Projekteinstellungen" mit hervorgehobener XR-Plug-In-Verwaltung](../../images/openxr-img-05.png)

> [!IMPORTANT]
> Wenn neben **OpenXR-Plug-In** ein gelbes Warnsymbol angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alle korrigieren** aus, bevor Sie fortfahren. Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.

![Screenshot des Fensters "OpenXR-Projektvalidierung"](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

Wenn Sie für HoloLens 2 entwickeln, wählen Sie die **Mixed Reality > Project > Empfohlene Projekteinstellungen für HoloLens 2** Menüelement anwenden aus, um eine bessere App-Leistung zu erzielen.

![Screenshot: Geöffnetes Mixed Reality-Menüelement mit ausgewählter Option "OpenXR"](../../images/openxr-img-08.png)

Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen!  Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Unity-Beispielprojekte für OpenXR und HoloLens 2

Sehen Sie sich das Repository mit [OpenXR-Mixed Reality-Beispielen](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) für Unity-Beispielprojekte an, die zeigen, wie Unity-Anwendungen für HoloLens 2 oder Mixed Reality Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellt werden.

Wenn Sie bereit sind, selbst mit einem leeren Projekt zu beginnen, fahren Sie mit dem Artikel [Kameraeinrichtung](../../camera-in-unity.md) fort.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

> [!CAUTION]
> Das Windows XR-Plug-In ist in Unity 2021.1 veraltet und wird in Unity 2021.2 entfernt.  Für die Unity 2020-Entwicklung empfiehlt Microsoft stattdessen das OpenXR-Plug-In.

Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Build Einstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](../../images/wmr-config-img-3.png)

Wenn Sie HoloLens 2 als Ziel verwenden, müssen Sie zur universellen Windows Plattform wechseln:

1.  Wählen Sie **Datei > Build Einstellungen... aus.**
2.  Wählen Sie in der Liste Plattform die Option **Universal Windows Platform** und dann Plattform **wechseln** aus.
3.  Legen Sie **Architecture** (Architektur) auf **ARM64** fest.
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.
6.  Festlegen der **Ziel-SDK-Version** auf **"Latest installed" (Neueste Installation)**
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot des Fensters "Build Einstellungen" im Unity-Editor mit hervorgehobener "Universal Windows Platform"](../../images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll:

1. Navigieren Sie im Unity-Editor zu **> Project Einstellungen bearbeiten,** und wählen Sie **XR-Plug-In-Verwaltung** aus.

2. Wählen Sie **XR-Plug-In-Verwaltung installieren** aus, wenn es angezeigt wird.

![Screenshot: geöffnetes fenster "Project Einstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-5.png)

3. Wählen Sie **XR beim Start initialisieren** und **Windows Mixed Reality**

![Screenshot des fensters "Project"-Einstellungen, das im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung geöffnet ist](../../images/wmr-config-img-7.png)

4. Wählen Sie den Abschnitt **XR-Plug-In-Verwaltung**  >  **Windows Mixed Reality** aus, aktivieren Sie alle Kontrollkästchen, und legen Sie **Tiefenpufferformat** auf **Tiefenpuffer 16 Bit** fest.

![Screenshot: Fenster "Einstellungen" Project im Unity-Editor geöffnet, wobei Windows Mixed Reality Abschnitt hervorgehoben ist](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[Legacy-XR](#tab/legacy)

> [!CAUTION]
> Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.

Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Build Einstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](../../images/wmr-config-img-3.png)

Wenn Sie HoloLens 2 als Ziel verwenden, müssen Sie zur universellen Windows Plattform wechseln:

1.  Wählen Sie **Datei > Build Einstellungen... aus.**
2.  Wählen Sie in der Liste Plattform die Option **Universal Windows Platform** und dann Plattform **wechseln** aus.
3.  Legen Sie **Architecture** (Architektur) auf **ARM64** fest.
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.
6.  Festlegen der **Ziel-SDK-Version** auf **"Latest installed" (Neueste Installation)**
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot des Fensters "Build Einstellungen" im Unity-Editor mit hervorgehobener "Universal Windows Platform"](../../images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll.

1. Öffnen Sie **Player Einstellungen...** aus der **Build Einstellungen... Fenster** und Erweitern der **Gruppe "XR Einstellungen"**
2. Wählen Sie im Abschnitt **XR Einstellungen** virtual **reality supported (Virtual Reality unterstützt)** aus, um die Liste Virtual Reality-Geräte hinzuzufügen.
3. Legen Sie **das Tiefenformat** auf **16-Bit-Tiefe** fest, und aktivieren **Sie Die Tiefenpufferfreigabe aktivieren.**
4. Legen Sie **Stereo Rendering Mode** (Stereorenderingmodus) auf **Single Pass Instanced** (Einzeldurchlauf instanziiert) fest.
5. Wählen Sie **WSA Holographic Remoting Supported (WSA Holographic Remoting unterstützt)** aus, wenn Sie Remoting im holografischen Wiedergabemodus verwenden möchten.

![Screenshot des fensters "Project"-Einstellungen, das im Unity-Editor geöffnet ist, wobei der Abschnitt "Playereinstellungen" hervorgehoben ist](../../images/wmr-config-img-9.png)
