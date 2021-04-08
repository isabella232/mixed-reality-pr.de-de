---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097824"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 und Windows-XR-Plugin](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Sicherstellen der Mikrofonfunktion und Hinzufügen eines Datenanbieters für Spracheingabe

Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Microphone Capability** (Mikrofonfunktion aktivieren) grau dargestellt wird:

![Aktivieren der Mikrofonfunktion](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> Die Mikrofonfunktion hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#configuring-the-unity-project) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe. Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.

Wählen Sie im Hierarchiefenster das MixedRealityToolkit-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte „Eingabe“:

* Erweitern Sie die **Eingabedatenanbieter**, und klicken Sie auf die Schaltfläche **+ Datenanbieter hinzufügen**, um einen neuen Datenanbieter hinzuzufügen.

![Datenanbieter zum Hinzufügen neuer Sprachbefehle](../images/mr-learning-base/base-09-section1-step1-2.png)

Weisen Sie **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** dem Feld **Typ** des neuen Datenanbieters zu.

![Hinzufügen neuer Einstellungen für Sprachbefehle](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 und OpenXR](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Sicherstellen der Mikrofonfunktion und Hinzufügen eines Datenanbieters für Spracheingabe

Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Microphone Capability** (Mikrofonfunktion aktivieren) grau dargestellt wird:

![Aktivieren der Mikrofonfunktion für OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> Die Mikrofonfunktion hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#configuring-the-unity-project) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe. Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.

Wählen Sie im Hierarchiefenster das MixedRealityToolkit-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte „Eingabe“:

* Erweitern Sie die **Eingabedatenanbieter**, und klicken Sie auf die Schaltfläche **+ Datenanbieter hinzufügen**, um einen neuen Datenanbieter hinzuzufügen.

![Hinzufügen neuer Sprachbefehle für OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

Weisen Sie **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** dem Feld **Typ** des neuen Datenanbieters zu.

![Hinzufügen neuer Sprachbefehle für OpenXR-Einstellungen](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Sicherstellen, dass die Mikrofonfunktion aktiviert ist

Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Microphone Capability** (Mikrofonfunktion aktivieren) grau dargestellt wird:

![Aktivieren der Mikrofonfunktion](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> Die Mikrofonfunktion hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe. Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.
