---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106096991"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 und Windows-XR-Plugin](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Sicherstellen der Funktion der Eingabe durch Anvisieren mit den Augen Hinzufügen eines Eye Gaze-Datenanbieters

Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Eye Gaze Input** (Eingabe durch Anvisieren mit den Augen) grau dargestellt wird:

![Unity MRTK-Projektkonfigurator-Fenster](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> Die Funktion zur Eingabe durch Anvisieren hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#configuring-the-unity-project) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe. Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.

Wählen Sie im Hierarchiefenster das MixedRealityToolkit-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte „Eingabe“:

* Erweitern Sie die **Eingabedatenanbieter**, und klicken Sie auf die Schaltfläche **+ Datenanbieter hinzufügen**, um einen neuen Datenanbieter hinzuzufügen.

![Hinzufügen von Augendatenanbieter 1](../images/mr-learning-base/base-08-section1-step1-2.png)

Weisen Sie **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** dem Feld **Typ** des neuen Datenanbieters zu.

![Hinzufügen von Augendatenanbieter 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 und OpenXR](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Sicherstellen der Funktion der Eingabe durch Anvisieren mit den Augen Hinzufügen eines Eye Gaze-Datenanbieters

Wählen Sie im Hierarchiefenster das MixedRealityToolkit-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte „Eingabe“:

* Erweitern Sie die **Eingabedatenanbieter**, und klicken Sie auf die Schaltfläche **+ Datenanbieter hinzufügen**, um einen neuen Datenanbieter hinzuzufügen.

![Hinzufügen von Augendatenanbieter 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

Weisen Sie **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** dem Feld **Typ** des neuen Datenanbieters zu.

![Hinzufügen von Augendatenanbieter 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Sicherstellen, dass die Eingabe durch Anvisieren mit den Augen aktiviert ist

Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Eye Gaze Input** (Eingabe durch Anvisieren mit den Augen) grau dargestellt wird:

![Unity MRTK-Projektkonfigurator-Fenster](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> Die Funktion zur Eingabe durch Anvisieren hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe. Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.
