---
ms.openlocfilehash: 3306a9925c55c24c4d72ecb58d7c744dd64b283e
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636300"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Das [Konfigurations Dialogfeld von mrtk](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) versucht, die tiefen Puffer Einstellungen für das XR SDK und das Legacy-WSA festzulegen, aber es ist gut, diese Registerkarten zu überprüfen und die Einstellungen in Unity zu überprüfen.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

So legen Sie fest, ob Ihre Unity-APP einen tiefen Puffer für Windows bereitstellt:

1. Wechseln Sie zu **Edit**  >  **Project Settings**  >  **XR Plug-in Management** , und stellen Sie sicher, dass das Menü Element erweitert ist.
2. Klicken Sie auf das Menü Element, das der von Ihnen ausgewählten XR-Laufzeit entspricht, entweder Windows Mixed Reality oder openxr. Stellen Sie außerdem sicher, dass die richtige Buildplattform ausgewählt ist, da Registerkarten für eigenständige Windows-und universelle Windows-Plattform verfügbar sind.
3. So aktivieren und konfigurieren Sie Folgendes:
    1. Wählen Sie für openxr in der Dropdown Liste für den tiefen Übermittlungs **Modus** entweder ein tiefen Format oder "keine" aus.
    2. Aktivieren oder deaktivieren Sie für Windows Mixed Reality das Kontrollkästchen frei **gegebenen tiefen Puffer** . Wählen Sie dann ein Format aus der Dropdown Liste **Tiefe Puffer Format** aus.

![Einstellungen für die Windows-XR-Plug-in-Tiefe ](../../images/xrsdk-winxr-depth.png)
 ![ openxr](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Im Allgemeinen wird empfohlen, 16-Bit-Tiefen Puffer für eine verbesserte Leistung zu verwenden. Wenn Sie jedoch ein 16-Bit-Tiefen Format verwenden, sind die Auswirkungen der Schablone (z. b. einige Unity-UI-Schiebe Bereiche) nicht funktionsfähig, da Unity in dieser Einstellung [keinen Schablonen Puffer erstellt](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) . Durch die Auswahl des *24-Bit-Tiefen Formats* umgekehrt wird in der Regel ein [8-Bit-Schablonen Puffer](https://docs.unity3d.com/Manual/SL-Stencil.html) erstellt, wenn er auf der Endpunkt Grafik Plattform anwendbar ist.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

So legen Sie fest, ob Ihre Unity-APP einen tiefen Puffer für Windows bereitstellt:

1. Wechseln Sie zu **Edit**  >  **Project Settings**  >  **Player**  >  **universelle Windows-Plattform Tab**  >  **XR Settings**.
2. Erweitern Sie das **Windows Mixed Reality SDK** -Element.
3. Aktivieren oder deaktivieren Sie das Kontrollkästchen **Tiefe Puffer Freigabe aktivieren** . Die Aktivierung der tiefen Puffer Freigabe ist in neuen Projekten standardmäßig aktiviert, wurde in älteren Projekten jedoch möglicherweise standardmäßig deaktiviert.

![Einstellungen der Legacy-XR-Tiefe](../../images/wmr-depth.png)

Ein tiefen Puffer kann die visuelle Qualität verbessern, solange Windows die normalisierten pro-Pixel-tiefen Werte in ihrem tiefen Puffer mithilfe der Near-und Far-Ebenen, die Sie in Unity auf der Hauptkamera festgelegt haben, genauer zuordnen lässt. Wenn Ihr renderingwert auf typische Weise handle-Werte übergibt, sollten Sie in der Regel in Ordnung sein, obwohl die übergreifende Renderingvorgänge, die in den tiefen Puffer schreiben, während Sie bis zu vorhandenen Farbpixeln zeigen, die neuprojektion verwirren können.  Wenn Sie wissen, dass Ihre Renderingdurchläufen viele der abschließenden tiefen Pixel mit ungenauen tiefen Werten belassen, erhalten Sie wahrscheinlich eine bessere visuelle Qualität, indem Sie die Option "Tiefe Puffer Freigabe aktivieren" deaktivieren.

> [!NOTE]
> Im Allgemeinen wird empfohlen, 16-Bit-Tiefen Puffer für eine verbesserte Leistung zu verwenden. Wenn Sie jedoch ein 16-Bit-Tiefen Format verwenden, sind die Auswirkungen der Schablone (z. b. einige Unity-UI-Schiebe Bereiche) nicht funktionsfähig, da Unity in dieser Einstellung [keinen Schablonen Puffer erstellt](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) . Durch die Auswahl des *24-Bit-Tiefen Formats* umgekehrt wird in der Regel ein [8-Bit-Schablonen Puffer](https://docs.unity3d.com/Manual/SL-Stencil.html) erstellt, wenn er auf der Endpunkt Grafik Plattform anwendbar ist.