---
title: Framework und Runtime
description: Informationen im Zusammenhang mit Framework und Runtime in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: f2391ab0c67880c8902092be6fcecefcf30f008c7f31ea76879d399e35e1491b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212671"
---
# <a name="framework-and-runtime"></a>Framework und Runtime

## <a name="changes-to-the-scene"></a>Änderungen an der Szene

Um das Toolkit verwenden zu können, muss sich eine Instanz des MixedRealityToolkit-Skripts in Ihrer Szene finden.
Um eine hinzuzufügen, verwenden Sie die Menüoption Mixed Reality Toolkit -> Zu Szene hinzufügen und konfigurieren. Diese Instanz ist für die Registrierung, Aktualisierung und Dasinierung von Diensten verantwortlich. Hier wird auch Ihr Konfigurationsprofil ausgewählt.

Neben dem Hinzufügen des MRTK GameObject zur Szene wird die Menüoption auch:

- Fügen Sie den MixedRealityPlayspace hinzu, der von vielen anderen MRTK-Komponenten verwendet wird, um weltumwandlungen und lokale Raumtransformationen zu verinnerlichen.
- Verschieben Sie die Hauptkamera als untergeordnetes Objekt des MixedRealityPlayspace (und fügen Sie der Hauptkamera eingabe- und anvisierte Skripts hinzu, die UnityUI unterstützen und die eingabebezogene Eingabefunktionalität anvisierten).

## <a name="mixedrealitytoolkit-object-and-runtime"></a>MixedRealityToolkit-Objekt und -Runtime

Das MRTK verfügt über mehrere Kerndienste. Einige koordinen miteinander; andere sind unabhängig.
Alle haben denselben Lebenszyklus – Start, Registrierung, Update und Abbruch – und dieser Lebenszyklus hebt sich vom MonoBehaviour-Lebenszyklus von Unity ab. In [diesem mittleren Beitrag](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) werden einige Hintergrundinformationen und Beweggründe für diesen Ansatz erläutert. MRTK verfügt über ein einzelnes Objekt, das die Lebensdauer und Laufzeit seiner Dienste verwaltet.

Diese Entität stellt Sicher, dass:

- Wenn das Spiel gestartet wird, erfolgt die Ermittlung und Initialisierung von Diensten in einer vordefinierten Reihenfolge.
- Sie bietet einen Mechanismus, mit dem dienste sich selbst registrieren können (d. h. "I support this service!") und für andere Aufrufer, um diese Dienste zu nutzen.
- Er stellt die Update()/LateUpdate()-Aufrufe zur Verfügung und weiter an die verschiedenen Dienste (d.h. über UpdateAllServices/LateUpdateAllServices).
