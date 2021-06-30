---
title: Framework und Runtime
description: Informationen im Zusammenhang mit Framework und Runtime in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121608"
---
# <a name="framework-and-runtime"></a>Framework und Runtime

## <a name="changes-to-the-scene"></a>Änderungen an der Szene

Um das Toolkit zu verwenden, muss sich eine Instanz des MixedRealityToolkit-Skripts in Ihrer Szene enthalten.
Um eine hinzuzufügen, verwenden Sie die Menüoption Mixed Reality Toolkit -> Zu Szene hinzufügen und konfigurieren. Diese Instanz ist für das Registrieren, Aktualisieren und Ablöschen von Diensten verantwortlich. Dort wird auch Ihr Konfigurationsprofil ausgewählt.

Neben dem Hinzufügen des MRTK GameObject zur Szene bietet die Menüoption auch Folgendes:

- Fügen Sie mixedRealityPlayspace hinzu, das von vielen anderen MRTK-Komponenten verwendet wird, um über die Welt und lokale Raumtransformationen zu denken.
- Verschieben Sie die Hauptkamera als untergeordnetes Element des MixedRealityPlayspace (und fügen Sie der Hauptkamera auch einige Eingabe- und Anvischer-Skripts hinzu, die UnityUI und die damit verbundene Eingabefunktionalität unterstützen).

## <a name="mixedrealitytoolkit-object-and-runtime"></a>MixedRealityToolkit-Objekt und -Laufzeit

Das MRTK verfügt über mehrere Kerndienste. Einige stimmen miteinander ab. andere sind unabhängig.
Alle verwenden denselben Lebenszyklus – Start, Registrierung, Update und Abgrenzung – und dieser Lebenszyklus unterscheidet sich vom MonoBehaviour-Lebenszyklus von Unity. In diesem [mittleren Beitrag](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) werden einige Hintergrundinformationen und Die Beweggründe für diesen Ansatz erläutert. MRTK verfügt über ein einzelnes Objekt, das die Lebensdauer und Laufzeit seiner Dienste verwaltet.

Diese Entität stellt Sicher, dass:

- Wenn das Spiel beginnt, erfolgt die Ermittlung und Initialisierung von Diensten in einer vordefinierten Reihenfolge.
- sie bietet einen Mechanismus für Dienste, um sich selbst zu registrieren (d. h. "Ich supportiere diesen Dienst!") und damit andere Aufrufer diese Dienste abrufen können.
- sie stellt die Update()/LateUpdate()-Aufrufe bereit und leitet sie an die verschiedenen Dienste weiter (d.h. über UpdateAllServices/LateUpdateAllServices).
