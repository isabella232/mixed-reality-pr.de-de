---
title: Ermitteln und Erwerben von Features
description: Ermitteln und Herunterladen von Mixed Reality-Features.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: fef1edd9e7257985a30739794f4b40164345254e3e76cfa740b3fe9699de79f2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203730"
---
# <a name="discovering-and-acquiring-features"></a>Ermitteln und Erwerben von Features

In den Abschnitten in diesem Artikel wird erläutert, wie Sie Featurepakete im Mixed Reality-Featuretool finden. Wenn Sie eine Referenz für einen bestimmten Abschnitt benötigen, sehen Sie sich den Screenshot unten an:

![Ermitteln von Features](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>Verfügbare Features

### <a name="category"></a>Category

Das Mixed Reality-Featuretool zeigt eine Auflistung von Featurekategorien an, um das Auffinden der gewünschten Features zu vereinfachen. Erweitern Sie eine beliebige Kategorie, um die in ihr enthaltene Sammlung verfügbarer Features anzuzeigen.

> [!NOTE]
> Wenn Sie die gewünschte Funktionalität nicht finden können, aktivieren Sie **Other Features** (Weitere Features).

![Featurekategorie](images/FeatureCategory.png)

Die Kategoriekopfzeile im Screenshot oben enthält von links nach rechts die folgenden Eigenschaften:

- Schaltfläche zum Erweitern und Reduzieren
- Kategoriename (Bsp.: Mixed Reality-Toolkit)
- Anzahl der ausgewählten Features
- Anzahl der verfügbaren Features
- Abschnittsschaltflächen

> [!NOTE]
> Die Auswahlschaltflächen sind kontextsensitiv. Basierend auf dem Status der Featureauswahl innerhalb der Kategorie wird eine oder werden beide der Schaltflächen `Select All` und `Select None` angezeigt.

### <a name="feature"></a>Funktion

![Featureeintrag](images/FeatureEntry.png)

Die Features werden in der entsprechenden Kategorie aufgelistet. Die Featureeinträge im Screenshot oben enthalten von links nach rechts:

- Auswahlkontrollkästchen
- Featurename (Bsp.: Mixed Reality Toolkit Foundation)
- Liste der verfügbaren Versionen
- Link zu den [Featurepaketdetails](viewing-package-details.md)

> [!NOTE]
> Wenn ein Feature von einem Early Access-Programm (auch als private Vorschauversion bezeichnet) bereitgestellt wird, wird ein Indikatorsymbol ![Early Access](images/EarlyAccess.png) angezeigt.

## <a name="refresh-the-feature-catalog"></a>Aktualisieren des Featurekatalogs

Zur Suche nach neuen und aktualisierten Features klicken Sie auf die Schaltfläche zum Aktualisieren ![Schaltfläche „Aktualisieren“](images/RefreshButton.png) Schaltfläche. Dadurch wird eine Verbindung mit der Katalogwebsite hergestellt, und die neuesten Informationen werden abgerufen. Nachdem der Katalog gelesen wurde, werden das Datum und die Uhrzeit des letzten Updates angezeigt.

## <a name="select-features"></a>Auswählen von Features

Sie wählen Features aus, indem Sie eine Kategorie erweitern, eine Version auswählen und auf das Kontrollkästchen klicken:

![Ausgewählte Features](images/SelectedFeatures.png)

Zum Auswählen jedes Pakets innerhalb einer Kategorie steht eine Schaltfläche `Select All` zur Verfügung. `Select None` deaktiviert die Auswahl aller ausgewählten Pakete. 

Jede Kategorie mit mindestens einem ausgewählten Feature wird aktualisiert, um die Anzahl anzuzeigen.

## <a name="acquiring-features"></a>Erwerben von Features

Nachdem Sie Ihre Features ausgewählt haben, wählen Sie **Get features** (Features abrufen) aus, um mit dem Download der ausgewählten Featurepaketdateien zu beginnen.

> [!NOTE]
> Standardmäßig werden zuvor erworbene Featurepaketdateien nicht erneut heruntergeladen. Wenn Sie dieses Verhalten ändern möchten, finden Sie weitere Informationen unter [Konfigurieren des Featuretools](configuring-feature-tool.md).

Nachdem dem Abschluss des Downloads wechselt das Mixed Reality-Featuretool zum Schritt [Importing Features](importing-features.md) (Features importieren).

## <a name="going-back-to-the-previous-step"></a>Zurückwechseln zum vorherigen Schritt

Von **Discover features** (Features ermitteln) erlaubt Ihnen das Mixed Reality-Featuretool die Navigation zurück zur Projektauswahl. Wählen Sie **Go back** (Zurück) aus, um erneut zu beginnen.

## <a name="see-also"></a>Siehe auch

- [Willkommen beim Mixed Reality-Featuretool](welcome-to-mr-feature-tool.md)
- [Konfigurieren des Featuretools](configuring-feature-tool.md)
- [Anzeigen von Details zu Featurepaketen](viewing-package-details.md)
- [Importieren ausgewählter Pakete](importing-features.md)
