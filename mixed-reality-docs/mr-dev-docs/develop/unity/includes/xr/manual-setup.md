---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394584"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Installieren Sie das OpenXR-Plug-In mit der neuen Mixed Reality Feature Tool-Anwendung. Befolgen Sie [die Installations- und Verwendungsanweisungen,](../../welcome-to-mr-feature-tool.md) und wählen Sie **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie Mixed Reality Toolkit aus:

![Mixed Reality fenster feature tool packages with open xr plugin (Öffnen des XR-Plug-Ins hervorgehoben)](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Festlegen des Buildziels

Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](../../images/wmr-config-img-3.png)

Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:

1. Wählen **Sie Datei > Buildeinstellungen... aus.**
2. Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**
3. Legen Sie **Architektur** auf **ARM 64** fest
4. Legen Sie **Zielgerät** auf **HoloLens** fest
5. Legen Sie **Buildtyp** auf **D3D** fest
6. Legen Sie **UWP SDK** auf **Zuletzt installiert** fest

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Konfigurieren der XR-Plug-In-Verwaltung für OpenXR

So legen Sie OpenXR als Runtime in Unity fest:

1. Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen.**
2. Wählen Sie in der Liste der Einstellungen **XR-Plug-In-Verwaltung aus.**
3. Aktivieren Sie die **Kontrollkästchen XR beim Start initialisieren** und **OpenXR.**
4. Wenn Sie HoloLens 2 auswählen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform sind, und wählen **Sie Microsoft HoloLens Feature Set (Featuresatz) aus.**

![Screenshot des im Unity-Editor geöffneten Projekteinstellungspanels mit hervorgehobener XR-Plug-In-Verwaltung](../../images/openxr-img-05.png)

### <a name="optimization"></a>Optimization

Wenn Sie für HoloLens 2 entwickeln, navigieren Sie zu Mixed Reality> **OpenXR >** Empfohlene Projekteinstellungen für HoloLens 2 anwenden, um eine bessere App-Leistung zu erzielen.

![Screenshot des geöffneten Mixed Reality-Menüelements mit ausgewählter Option "OpenXR"](../../images/openxr-img-08.png)

> [!IMPORTANT]
> Wenn neben Dem OpenXR-Plug-In ein gelbes **Warnsymbol** angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alles korrigieren aus,** bevor Sie fortfahren. Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.

![Screenshot des OpenXR-Projektüberprüfungsfensters](../../images/openxr-img-06.png)

Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen.  Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Unity-Beispielprojekte für OpenXR und HoloLens 2

Sehen Sie sich das [Repository mit OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) Mixed Reality-Beispielen für Unity-Beispielprojekte an, in dem gezeigt wird, wie Sie Unity-Anwendungen für HoloLens 2- oder Mixed Reality-Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellen.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](../../images/wmr-config-img-3.png)

Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:

1.  Wählen **Sie Datei > Buildeinstellungen... aus.**
2.  Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**
3.  Legen Sie **Architektur** auf **ARM 64** fest
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Buildtyp** auf **D3D** fest
6.  Legen Sie **UWP SDK** auf **Zuletzt installiert** fest
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](../../images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll:

1. Navigieren Sie im Unity-Editor zu Bearbeiten > **Projekteinstellungen,** und wählen Sie **XR-Plug-In-Verwaltung aus.**

2. Wählen Sie **XR-Plug-In-Verwaltung installieren aus.**

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-5.png)

3. Wählen **Sie XR beim Start initialisieren und Windows Mixed Reality** 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-7.png)

4. Erweitern Sie den **Abschnitt XR-Plug-In-Verwaltung,** und wählen Sie die Registerkarte **"Einstellungen für die Windows-Plattform"** aus.
5. Wenn Sie Unity 2020 oder höher verwenden, sehen Sie die Optionen zum Überprüfen von **OpenXR** **oder Windows Mixed Reality**. 
    * Sie können eine der beiden Laufzeiten auswählen.  Wenn Sie speziell für die HoloLens 2 oder HP Reverb G2 entwickeln und sich entschließen, **OpenXR** auszuprobieren, wählen Sie das Feld OpenXR aus, und sehen Sie sich unseren Leitfaden unter Verwenden des Mixed Reality OpenXR-Plug-Ins für [Unity](../../openxr-getting-started.md) an, um sich für diese Geräte richtig einrichten zu lassen, bevor Sie zu diesem Tutorial zurückkehren.

> [!NOTE]
> Ab Unity 2020 LTS geht Microsoft von der Entwicklung mit OpenXR aus.  Bei der Migration zu diesem Pfad wird in Unity 2021.1 das Windows XR-Plug-In veraltet sein und in 2021.2 entfernt, wodurch OpenXR der einzige unterstützte Pfad ist. Weitere Informationen finden Sie unter [Verwenden des Mixed Reality OpenXR-Plug-Ins.](../../openxr-getting-started.md)

6. Wenn Sie sich für das **Windows Mixed Reality-Plug-In** entscheiden, aktivieren Sie alle Kontrollkästchen, und legen Sie **Tiefenübermittlungsmodus** auf Tiefe **16 Bit fest.**

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener Windows Mixed Reality Abschnitt](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[Legacy-XR](#tab/legacy)

Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](../../images/wmr-config-img-3.png)

Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:

1.  Wählen **Sie Datei > Buildeinstellungen... aus.**
2.  Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**
3.  Legen Sie **Architektur** auf **ARM 64** fest
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Buildtyp** auf **D3D** fest
6.  Legen Sie **UWP SDK** auf **Zuletzt installiert** fest
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](../../images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll.

> [!CAUTION]
> Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.

1. Öffnen **Sie Playereinstellungen...** aus **den Buildeinstellungen... Und** erweitern Sie die **Gruppe XR-Einstellungen.**
2. Wählen Sie **im Abschnitt XR-Einstellungen** die Option **Virtual Reality Unterstützt aus,** um die Liste Virtual Reality-Geräte hinzuzufügen.
3. Festlegen **des Tiefenformats** auf **16-Bit-Tiefe und** Aktivieren der **Tiefenpufferfreigabe**
4. Festlegen des **Stereo-Renderingmodus** auf **eine Einzelpassinstanz**
5. Wählen **Sie WSA Holographic Remoting Supported (WSA Holographic Remoting Unterstützt)** aus, wenn Sie Holographic Remoting verwenden möchten. 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener Seite "Playereinstellungen"](../../images/wmr-config-img-9.png)