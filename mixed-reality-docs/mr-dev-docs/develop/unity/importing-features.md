---
title: Importieren von Features
description: Erfahren Sie, wie Sie Features aus dem MR-Featuretool für die HoloLens- und VR-Entwicklung importieren.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230815"
---
# <a name="importing-features"></a>Importieren von Features

Nachdem Ihre Features heruntergeladen wurden, können sie überprüft und in das Unity-Projekt importiert werden. In diesem Schritt sollte Ihr Anwendungsfenster wie in der folgenden Abbildung aussehen:

![Importieren von Features](images/FeatureToolImport.png)

## <a name="features-list"></a>Features list

Die Liste **Features** enthält die Sammlung von Paketen, die während der Ermittlung ausgewählt wurden. Die einzelnen Features können vor dem Importieren ausgewählt oder abgewählt werden. Paketdetails können über den unten abgebildeten Link **Details** angezeigt werden

![Features list](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>Liste der erforderlichen Abhängigkeiten

Die Liste **Required dependencies** (Erforderliche Abhängigkeiten) enthält die Pakete, die für die Funktion eines oder mehrerer der ausgewählten Features erforderlich sind. Diese Liste enthält auch Abhängigkeiten von Abhängigkeiten. Jede Abhängigkeit kann vor dem Importieren ausgewählt oder abgewählt werden. Paketdetails können über den unten abgebildeten Link **Details** angezeigt werden

![Liste „Dependencies“ (Abhängigkeiten)](images/RequiredDependencyList.png)

> [!NOTE]
> Das Aufheben der Auswahl erforderlicher Abhängigkeiten führt beim Laden des Projekts in Unity zu mindestens einem Fehler wegen fehlender Abhängigkeiten. Die betroffenen Features sind dann im Projekt nicht nutzbar.

## <a name="validating-selections"></a>Überprüfen der Auswahl

Wir empfehlen dringend, die Featureauswahl vor dem Importieren zu überprüfen. In diesem Schritt kommen alle Probleme ans Licht, die eine erfolgreiche Projektentwicklung wahrscheinlich verhindern.

![Probleme bei der Überprüfung](images/ValidationIssues.png)

Das Mixed Reality-Featuretool bietet zwei automatische Fehlerbehebungen (in den folgenden Abschnitten beschrieben) und die Option zum Abbrechen und manuellen Beheben von Fehlern.

### <a name="enable-dependencies"></a>Aktivieren von Abhängigkeiten

Mit der Schaltfläche **Enable dependencies** (Abhängigkeiten aktivieren) werden die fehlenden Abhängigkeiten automatisch wieder ausgewählt. Dies gilt für Abhängigkeiten, die explizit ausgewählt wurden (werden in der Liste **Features** angezeigt) und solchen, die auf der Grundlage der Abhängigkeiten der ausgewählten Features implizit ausgewählt wurden.

### <a name="disable-features"></a>Deaktivieren von Features

Wenn Sie **Features deaktivieren** auswählen, werden alle Features, die von mindestens einer der Abhängigkeiten abhängen, deren Auswahl aufgehoben wurde, automatisch deaktiviert. Dies gilt für implizit ausgewählte Abhängigkeitspakete und explizit ausgewählte Features.

## <a name="importing"></a>Importieren

Wählen Sie **importieren** aus, um die ausgewählten Features hinzuzufügen und die [endgültige Genehmigung](reviewing-changes.md) zu erteilen, bevor Sie das Zielprojekt aktualisieren.

> [!IMPORTANT]
> Wenn beim importieren ein Überprüfungsfehler verbleibt, wird eine Warnmeldung angezeigt. In diesem Fall wird empfohlen, dass Sie „No“ (Nein) auswählen, auf **Validate** (Überprüfen) klicken und alle angezeigten Fehler beheben.
>
> ![Mit Überprüfungsproblemen fortfahren](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>Zurück zum vorherigen Schritt

Von **Import features** (Features importieren) erlaubt Ihnen das Mixed Reality-Featuretool die Navigation zurück zur [Ermittlung](discovering-features.md). Wählen Sie **Go back** (Zurück) aus, um weitere Featurepakete herunterzuladen.

## <a name="see-also"></a>Siehe auch

- [Willkommen beim Mixed Reality-Featuretool](welcome-to-mr-feature-tool.md)
- [Ermittlung und Erwerb](discovering-features.md)
- [Anzeigen von Details zu Featurepaketen](viewing-package-details.md)
- [Überprüfen und Genehmigen von Projektänderungen](reviewing-changes.md)