---
ms.openlocfilehash: 924190e10de100fc84795344a6cf676f318d04cec26793af96d03a3cb7cb5f78
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212274"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Das [MRTK-Konfigurationsdialogfeld](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) versucht, Tiefenpuffereinstellungen sowohl für das XR SDK als auch für ältere WSA festzulegen. Es empfiehlt sich jedoch, diese Registerkarten zu überprüfen und die Einstellungen in Unity zu überprüfen.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

So legen Sie fest, ob Ihre Unity-App einen Tiefenpuffer für Windows bereitstellt:

1. Wechseln **Sie** zu Bearbeiten  >  **Project Einstellungen**  >  **XR-Plug-In-Verwaltung,** und stellen Sie sicher, dass das Menüelement erweitert ist.
2. Klicken Sie auf das Menüelement, das der ausgewählten XR-Runtime entspricht, entweder Windows Mixed Reality oder OpenXR. Stellen Sie außerdem sicher, dass die richtige Buildplattform ausgewählt ist, da Registerkarten für Windows eigenständige und universelle Windows-Plattform verfügbar sind.
3. So aktivieren und konfigurieren Sie Folgendes:
    1. Wählen Sie für OpenXR in der Dropdownliste **Tiefenübermittlungsmodus** entweder ein Tiefenformat oder "Keine" aus.
    2. Aktivieren oder deaktivieren Sie für Windows Mixed Reality das Kontrollkästchen **Freigegebener Tiefenpuffer.** Wählen Sie dann in der Dropdownliste **Tiefenpufferformat** ein Format aus.

![Windows XR-Plug-In-Tiefeneinstellungen ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR-Tiefeneinstellungen](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Es wird im Allgemeinen empfohlen, 16-Bit-Tiefenpuffer zu verwenden, um die Leistung zu verbessern. Bei Verwendung des 16-Bit-Tiefenformats funktionieren schablonenpufferbezogene Effekte (wie einige Unity-UI-Scrollpanels) jedoch nicht, da Unity in dieser Einstellung [keinen Schablonenpuffer erstellt.](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) Wenn Sie umgekehrt das *24-Bit-Tiefenformat* auswählen, wird in der Regel ein [8-Bit-Schablonenpuffer](https://docs.unity3d.com/Manual/SL-Stencil.html) erstellt, falls dies auf der Endpunktgrafikplattform gilt.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

So legen Sie fest, ob Ihre Unity-App einen Tiefenpuffer für Windows bereitstellt:

1. Wechseln **Sie** zur Registerkarte Edit  >  **Project Einstellungen**  >  **Player**  >  **Universal Windows Platform**  >  **Einstellungen**.
2. Erweitern Sie das **Windows Mixed Reality SDK-Element.**
3. Aktivieren oder deaktivieren Sie das Kontrollkästchen **Tiefenpufferfreigabe aktivieren.** Die Aktivierung der Tiefenpufferfreigabe ist in neuen Projekten standardmäßig aktiviert, wurde in älteren Projekten jedoch möglicherweise standardmäßig deaktiviert.

![Legacy-XR-Tiefeneinstellungen](../../images/wmr-depth.png)

Ein Tiefenpuffer kann die visuelle Qualität verbessern, solange Windows die normalisierten Tiefenwerte pro Pixel in Ihrem Tiefenpuffer mithilfe der nah- und fernen Ebenen, die Sie in Unity auf der Hauptkamera festgelegt haben, genau den Entfernungen in Metern zuordnen können. Wenn Der Rendervorgang die Tiefenwerte auf typische Weise übergibt, sollten Sie hier in der Regel in Ordnung sein, obwohl durchscheinende Renderdurchläufe, die in den Tiefenpuffer schreiben, während sie an vorhandene Farbpixel übergeben werden, die Neuprojektion verwirren können.  Wenn Sie wissen, dass ihre Renderdurchläufe viele ihrer endgültigen Tiefenpixel mit ungenauen Tiefenwerten belassen, erhalten Sie wahrscheinlich eine bessere visuelle Qualität, indem Sie "Tiefenpufferfreigabe aktivieren" deaktivieren.

> [!NOTE]
> Es wird im Allgemeinen empfohlen, 16-Bit-Tiefenpuffer zu verwenden, um die Leistung zu verbessern. Bei Verwendung des 16-Bit-Tiefenformats funktionieren schablonenpufferbezogene Effekte (wie einige Unity-UI-Scrollpanels) jedoch nicht, da Unity in dieser Einstellung [keinen Schablonenpuffer erstellt.](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) Wenn Sie umgekehrt das *24-Bit-Tiefenformat* auswählen, wird in der Regel ein [8-Bit-Schablonenpuffer](https://docs.unity3d.com/Manual/SL-Stencil.html) erstellt, falls dies auf der Endpunktgrafikplattform gilt.