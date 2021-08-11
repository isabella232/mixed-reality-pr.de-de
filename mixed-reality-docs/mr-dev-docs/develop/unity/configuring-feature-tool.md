---
title: Konfigurieren des Mixed Reality-Featuretools
description: Erfahren Sie, wie Sie Mixed Reality Unity-Pakete über das MR-Featuretool für die HoloLens- und VR-Entwicklung herunterladen und installieren.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: 419f26f79ca8bdd1998955a2bdf72dfabf73976c89b1abce175ef2cf60c9597b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210908"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Konfigurieren des Mixed Reality-Featuretools

Beim Verwenden des Mixed Reality-Featuretools haben Sie Zugriff auf drei verschiedene Kategorien von Einstellungen, die Sie nach Belieben anpassen können:

* [Downloadeinstellungen](#download-settings)
* [Featureeinstellungen](#feature-settings)
* [Importieren von Einstellungen](#import-settings)

## <a name="download-settings"></a>Downloadeinstellungen

![Downloadeinstellungen](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a>Vorhandene Paketdateien überschreiben

Wenn Sie diese Einstellung aktivieren, werden die Paketdateien bei jedem Abrufen heruntergeladen. 

* **Wir empfehlen, diese Option deaktiviert zu lassen, um den Verbrauch an Netzwerkbandbreite zu verringern**
* Standardmäßig werden zuvor erworbene Featurepaketdateien nicht erneut heruntergeladen.

### <a name="package-cache"></a>Paketcache

Ändern Sie diese Einstellung, um den Speicherort zu ändern, an dem heruntergeladene Featurepakete gespeichert werden.

> [!NOTE]
> Diese Einstellung ist in dieser Version **schreibgeschützt**. In zukünftigen Versionen wird diese Einstellung möglicherweise konfigurierbar.

## <a name="feature-settings"></a>Featureeinstellungen

![Featureeinstellungen](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a>Vorschauversionen anzeigen

Aktivieren Sie diese Einstellung, um Vorschauversionen zu erhalten.
* Standardmäßig werden Vorschauversionen nicht im Mixed Reality-Featuretool angezeigt 

> [!NOTE]
> Eine Vorschauversion ist dadurch gekennzeichnet, dass sie die Bezeichnung **"-preview"** in der Paketversion enthält.

### <a name="show-early-access-program-features"></a>Features des Early Access-Programms anzeigen

Aktivieren Sie diese Einstellung, um Features aus registrierten Releases von Early Access-Programmen zu erhalten.

* Standardmäßig werden Early Access-Features nicht im Mixed Reality-Featuretool angezeigt. 

> [!NOTE]
> Die Aktivierung von `Show early access program features` ohne `Show preview releases` kann dazu führen, dass Early Access-Pakete nicht in der Ermittlung angezeigt werden.

## <a name="import-settings"></a>Importieren von Einstellungen

![Importieren von Einstellungen](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a>Vorhandene Paketdateien ersetzen

Standardmäßig entfernt das Mixed Reality-Featuretool vorherige Exemplare von Paketen, die importiert werden, um die Dateigröße und unnötige Berechnungen zu verringern. 

* Deaktivieren Sie diese Einstellung, wenn Sie alle Versionen behalten möchten.

### <a name="project-relative-import-path"></a>Relativer Importpfad des Projekts

Ändern Sie diese Einstellung, um den Ordnerpfad des Projekts zu aktualisieren, in den Featurepakete beim Importieren kopiert werden. 

* Wenn der Projektordner beispielsweise **C:\GalaxyExplorer** ist, lautet der vollqualifizierte Importpfad **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Diese Einstellung ist in dieser Version **schreibgeschützt**. In zukünftigen Versionen wird diese Einstellung möglicherweise konfigurierbar.

## <a name="early-access-settings"></a>Early Access-Einstellungen

![Early Access-Einstellungen](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a>Vor dem Entfernen eines Early Access-Programms zur Bestätigung auffordern

Diese Einstellung bestimmt, ob jedes Mal, wenn ein Early Access-Programm entfernt wird, eine Benachrichtigung angezeigt wird.

### <a name="my-previews"></a>Meine Vorschauversionen

Die Liste der registrierten Early Access-Programme. Verwenden Sie die Schaltflächen `Add`, `Edit` und `Remove`, um die Sammlung der registrierten Programme zu verwalten.

## <a name="diagnostic-settings"></a>Diagnoseeinstellungen

![Diagnoseeinstellungen](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a>Protokolldatei

Zeigt den Pfad zur Datei des Diagnoseprotokolls an.

## <a name="see-also"></a>Siehe auch

- [Willkommen beim Mixed Reality-Featuretool](welcome-to-mr-feature-tool.md)