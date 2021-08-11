---
title: Spracheingabe/-ausgabe
description: Konfigurieren der Spracheingabe im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Speech,
ms.openlocfilehash: 00de7854bcb68703fbfd5566b7d502f08ac34efc1ac9434a2c86274f07b6342d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228412"
---
# <a name="speech"></a>Spracheingabe/-ausgabe

![Nähemenü](../images/input/MRTK_Input_Speech.png)

Spracheingabeanbieter, z. *B. Windows Speech Input,* erstellen keine Controller, sondern ermöglichen Es Ihnen, Schlüsselwörter zu definieren, die Spracheingabeereignisse auslösen, wenn sie erkannt werden. Im **Sprachbefehlsprofil** im *Eingabesystemprofil* konfigurieren Sie die zu erkennenden Schlüsselwörter. Für jeden Befehl haben Sie auch die folgenden Möglichkeiten:

- Wählen Sie eine **Eingabeaktion** aus, der sie zugeordnet werden soll. Auf diese Weise können Sie z. B. das Schlüsselwort *Auswählen* verwenden, um den gleichen Effekt wie ein linker Mausklick zu haben, indem Sie beide derselben Aktion zuordnen.
- Geben Sie einen **Schlüsselcode** an, der das gleiche Sprachereignis erzeugt, wenn er gedrückt wird.
- Fügen Sie einen **Lokalisierungsschlüssel** hinzu, der in UWP-Apps verwendet wird, um das lokalisierte Schlüsselwort aus den App-Ressourcen abzurufen.

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands profile">

## <a name="handling-speech-input"></a>Behandeln von Spracheingaben

Das [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) Skript kann einem GameObject hinzugefügt werden, um Sprachbefehle mit [**UnityEvents**](https://docs.unity3d.com/Manual/UnityEvents.html)zu verarbeiten. Die Liste der definierten Schlüsselwörter aus dem **Speech Commands Profile** wird automatisch angezeigt.

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input handler">

Weisen Sie optional **SpeechConfirmationTooltip.prefab** zu, um die QuickInfo-Bezeichnung für animierte Bestätigungen bei der Erkennung anzuzeigen.

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Sppech input handler 2">

Alternativ können Entwickler die [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) -Schnittstelle in einer benutzerdefinierten Skriptkomponente implementieren, um [Spracheingabeereignisse](input-events.md#input-event-interface-example)zu verarbeiten.

## <a name="example-scene"></a>Beispielszene

Die **SpeechInputExample-Szene** in `MRTK/Examples/Demos/Input/Scenes/Speech` zeigt die Verwendung von Sprache. Sie können auch direkt in Ihrem eigenen Skript auf Sprachbefehlsereignisse lauschen, indem Sie implementieren [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (siehe Tabelle der [Ereignishandler](input-events.md)).

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
