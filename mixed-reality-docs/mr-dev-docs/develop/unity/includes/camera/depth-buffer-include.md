---
ms.openlocfilehash: 481a063cac3cb4d7e5ef7521ad19af43cb68e2cf
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110630588"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Im [MrTK-Konfigurationsdialogfeld](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) wird versucht, Tiefenpuffereinstellungen sowohl für das XR SDK als auch für das Legacy-WSA festlegen. Es ist jedoch gut, diese Registerkarten zu überprüfen und die Einstellungen in Unity zu überprüfen.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

So legen Sie fest, ob Ihre Unity-App einen Tiefenpuffer für Windows bereitstellen wird:

1. Wechseln Sie **zu Edit**  >  **Project Settings**  >  **XR Plug-in Management (XR-Plug-In-Verwaltung** bearbeiten), und stellen Sie sicher, dass das Menüelement erweitert ist.
2. Klicken Sie auf das Menüelement, das der ausgewählten XR-Runtime entspricht, entweder Windows Mixed Reality OpenXR. Stellen Sie außerdem sicher, dass die richtige Buildplattform ausgewählt ist, da Registerkarten sowohl für windows standalone als auch Universelle Windows-Plattform verfügbar sind.
3. So aktivieren und konfigurieren Sie
    1. Wählen Sie für OpenXR in der Dropdownliste Tiefenübermittlungsmodus entweder ein Tiefenformat oder **"Keine"** aus.
    2. Aktivieren Windows Mixed Reality aktivieren oder deaktivieren Sie das Kontrollkästchen **Freigegebener Tiefenpuffer.** Wählen Sie dann in der Dropdownliste **Tiefenpufferformat ein Format** aus.

![OpenXR-Tiefeneinstellungen des Windows ](../../images/xrsdk-winxr-depth.png)
 ![ XR-Plug-Ins](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Es wird im Allgemeinen empfohlen, 16-Bit-Tiefenpuffer zu verwenden, um die Leistung zu verbessern. Wenn Sie jedoch das 16-Bit-Tiefenformat verwenden, funktionieren die erforderlichen Effekte des Schablonenpuffers (wie einige Unity-Scrollpanels auf der Benutzeroberfläche) nicht, da [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in dieser Einstellung keinen Schablonenpuffer erstellt. Wenn Sie *umgekehrt das 24-Bit-Tiefenformat* auswählen, wird in der Regel ein [8-Bit-Schablonenpuffer](https://docs.unity3d.com/Manual/SL-Stencil.html) erstellt, falls dies auf der Endpunktgrafikplattform gilt.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

So legen Sie fest, ob Ihre Unity-App einen Tiefenpuffer für Windows bereitstellen wird:

1. Wechseln Sie **zu**  >  **Projekteinstellungen**  >  **bearbeiten Player Universelle Windows-Plattform**  >  **Registerkarte**  >  **XR-Einstellungen**.
2. Erweitern Sie **Windows Mixed Reality SDK-Element.**
3. Aktivieren oder deaktivieren Sie das **Kontrollkästchen Tiefenpufferfreigabe** aktivieren. Tiefenpufferfreigabe aktivieren ist in neuen Projekten standardmäßig aktiviert, wurde in älteren Projekten jedoch möglicherweise standardmäßig deaktiviert.

![Ältere XR-Tiefeneinstellungen](../../images/wmr-depth.png)

Ein Tiefenpuffer kann die visuelle Qualität verbessern, solange Windows die normalisierten Tiefenwerte pro Pixel in Ihrem Tiefenpuffer mithilfe der nah- und fernen Ebenen, die Sie in Unity auf der Hauptkamera festgelegt haben, genau den Entfernungen in Metern zuordnen kann. Wenn ihr Renderhandl-Tiefenwerte auf typische Weise übergibt, sollten Sie in der Regel in Ordnung sein, obwohl durchsichtige Renderüberläufe, die schreibe an den Tiefenpuffer übergibt, während sie bis zu vorhandenen Farbpixeln angezeigt werden, die Neuprojektion verwirren können.  Wenn Sie wissen, dass Ihre Renderüberläufe viele Ihrer letzten Tiefenpixel mit ungenauen Tiefenwerten verlassen, erhalten Sie wahrscheinlich eine bessere visuelle Qualität, indem Sie die Option "Tiefenpufferfreigabe aktivieren" deaktivieren.

> [!NOTE]
> Es wird im Allgemeinen empfohlen, 16-Bit-Tiefenpuffer zu verwenden, um die Leistung zu verbessern. Wenn Sie jedoch das 16-Bit-Tiefenformat verwenden, funktionieren die erforderlichen Effekte des Schablonenpuffers (wie einige Unity-Scrollpanels auf der Benutzeroberfläche) nicht, da [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in dieser Einstellung keinen Schablonenpuffer erstellt. Wenn Sie *umgekehrt das 24-Bit-Tiefenformat* auswählen, wird in der Regel ein [8-Bit-Schablonenpuffer](https://docs.unity3d.com/Manual/SL-Stencil.html) erstellt, falls dies auf der Endpunktgrafikplattform gilt.