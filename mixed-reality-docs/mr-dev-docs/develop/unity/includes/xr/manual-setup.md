---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603716"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Installieren Sie das OpenXR-Plug-In mit der neuen Mixed Reality Feature Tool-Anwendung. Befolgen Sie [die Installations- und Nutzungsanweisungen,](../../welcome-to-mr-feature-tool.md) und wählen Sie **Mixed Reality OpenXR-Plug-In-Paket** in der **Kategorie Plattformunterstützung** aus:

![Mixed Reality fenster feature tool packages with open xr plugin (Öffnen des XR-Plug-Ins hervorgehoben)](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Festlegen des Buildziels

Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener eigenständiger Mac &-Plattform](../../images/wmr-config-img-3.png)

Wenn Sie auf HoloLens 2 möchten, müssen Sie zur Universellen Windows-Plattform wechseln:

1. Wählen **Sie Datei > Build Einstellungen...**
2. Wählen **Sie Windows Plattform** in der Liste Plattform aus, und wählen Sie Plattform wechseln **aus.**
3. Legen Sie **Architecture** (Architektur) auf **ARM64** fest.
4. Legen Sie **Zielgerät** auf **HoloLens** fest
5. Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.
6. Festlegen **der Ziel-SDK-Version** **auf Neueste installiert**

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener Windows Plattform](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Konfigurieren der XR-Plug-In-Verwaltung für OpenXR

So legen Sie OpenXR als Runtime in Unity fest:

1. Navigieren Sie im Unity-Editor zu **Bearbeiten > Project Einstellungen**
2. Wählen Sie in Einstellungen Liste der Anwendungen **XR-Plug-In-Verwaltung** aus (sollte bereits installiert sein, wenn Sie das openXR Mixed Reality-Plug-In mit MRFT installiert haben).
3. Aktivieren Sie das **Kontrollkästchen XR beim Start initialisieren.**
4. Wenn Sie Desktop VR als Ziel verwenden, bleiben Sie auf der Registerkarte Eigenständiger PC (Monitor) und aktivieren sie die Kontrollkästchen **OpenXR** **und Windows Mixed Reality Featuresatz.**
5. Wenn Sie HoloLens 2 auswählen, wechseln Sie zur Registerkarte Universelle Windows-Plattform (das Windows-Logo), und wählen Sie die Felder **OpenXR** und Microsoft HoloLens **Featuresatz** aus.

![Screenshot des im Unity-Editor geöffneten Projekteinstellungspanels mit hervorgehobener XR-Plug-In-Verwaltung](../../images/openxr-img-05.png)

> [!IMPORTANT]
> Wenn neben Dem OpenXR-Plug-In ein gelbes **Warnsymbol** angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alle korrigieren aus,** bevor Sie fortfahren. Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.

![Screenshot des OpenXR-Projektüberprüfungsfensters](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

Wenn Sie für die Entwicklung HoloLens 2,  wählen Sie das Menüelement Mixed Reality > Project > Empfohlene Projekteinstellungen für HoloLens 2 anwenden aus, um eine bessere App-Leistung zu erzielen.

![Screenshot des geöffneten Mixed Reality-Menüelements mit ausgewählter Option "OpenXR"](../../images/openxr-img-08.png)

Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen.  Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Unity-Beispielprojekte für OpenXR und HoloLens 2

Sehen Sie sich das [OpenXR Mixed Reality-Beispielre](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) repo für Unity-Beispielprojekte an, in dem gezeigt wird, wie Sie Unity-Anwendungen für HoloLens 2- oder Mixed Reality-Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellen.

Wenn Sie selbst mit einem leeren Projekt beginnen möchten, fahren Sie mit dem Artikel Einrichten der [Kamera](../../camera-in-unity.md) fort.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

> [!CAUTION]
> Das Windows XR-Plug-In ist in Unity 2021.1 veraltet und wird in Unity 2021.2 entfernt.  Für die Unity 2020-Entwicklung empfiehlt Microsoft stattdessen das OpenXR-Plug-In.

Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener eigenständiger Mac &-Plattform](../../images/wmr-config-img-3.png)

Wenn Sie auf HoloLens 2 möchten, müssen Sie zur Universellen Windows-Plattform wechseln:

1.  Wählen **Sie Datei > Build Einstellungen...**
2.  Wählen **Sie Windows Plattform** in der Liste Plattform aus, und wählen Sie Plattform wechseln **aus.**
3.  Legen Sie **Architecture** (Architektur) auf **ARM64** fest.
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.
6.  Festlegen **der Ziel-SDK-Version** **auf Neueste installiert**
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener Windows Plattform](../../images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll:

1. Navigieren Sie im Unity-Editor zu **Edit > Project settings (Einstellungen bearbeiten),** und wählen Sie **XR Plugin Management (XR-Plug-In-Verwaltung) aus.**

2. Wählen Sie **XR-Plug-In-Verwaltung installieren aus,** wenn es angezeigt wird.

![Screenshot: Project Einstellungen geöffneten Fensters im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-5.png)

3. Wählen **Sie XR beim Start initialisieren und Windows Mixed Reality** 

![Screenshot: Project Fenster "Einstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-7.png)

4. Wählen Sie den **Abschnitt XR Plug-in Management Windows Mixed Reality** aus, aktivieren Sie alle Kontrollkästchen, und legen Sie Tiefenpufferformat auf  >   **Tiefenpuffer 16 Bit fest.** 

![Screenshot: Project Fenster "Einstellungen" im Unity-Editor mit hervorgehobener Windows Mixed Reality](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[Legacy-XR](#tab/legacy)

> [!CAUTION]
> Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.

Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener eigenständiger Mac &-Plattform](../../images/wmr-config-img-3.png)

Wenn Sie auf HoloLens 2 möchten, müssen Sie zur Universellen Windows-Plattform wechseln:

1.  Wählen **Sie Datei > Build Einstellungen...**
2.  Wählen **Sie Windows Plattform** in der Liste Plattform aus, und wählen Sie Plattform wechseln **aus.**
3.  Legen Sie **Architecture** (Architektur) auf **ARM64** fest.
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.
6.  Festlegen **der Ziel-SDK-Version** **auf Neueste installiert**
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener Windows Plattform](../../images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll.

1. Öffnen **Sie player Einstellungen...** im **Build Einstellungen... Und** erweitern Sie die **XR Einstellungen Gruppe.**
2. Wählen Sie **im Abschnitt XR Einstellungen** Virtual Reality Supported **(Virtual Reality** unterstützt) aus, um die Liste Virtual Reality-Geräte hinzuzufügen.
3. Legen **Sie tiefenformat auf** **16-Bit-Tiefe fest,** und aktivieren Sie **Tiefenpufferfreigabe aktivieren.**
4. Legen Sie **Stereo Rendering Mode** (Stereorenderingmodus) auf **Single Pass Instanced** (Einzeldurchlauf instanziiert) fest.
5. Wählen **Sie WSA Holographic Remoting Supported (WSA Holographic Remoting unterstützt)** aus, wenn Sie remoting im holografischen Wiedergabemodus verwenden möchten.

![Screenshot: Project Fenster "Einstellungen" im Unity-Editor mit hervorgehobenen Abschnitt "Playereinstellungen"](../../images/wmr-config-img-9.png)
