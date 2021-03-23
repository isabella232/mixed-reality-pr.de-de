---
title: Konfigurieren des Mixed Reality-Featuretools
description: Erfahren Sie, wie Sie Mixed Reality Unity-Pakete über das MR-Featuretool für die HoloLens- und VR-Entwicklung herunterladen und installieren.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "99243929"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Konfigurieren des Mixed Reality-Featuretools

Beim Verwenden des Mixed Reality-Featuretools haben Sie Zugriff auf drei verschiedene Kategorien von Einstellungen, die Sie nach Belieben anpassen können:

* [Downloadeinstellungen](#download-settings)
* [Featureeinstellungen](#feature-settings)
* [Importieren von Einstellungen](#import-settings)

![Einstellungen](images/FeatureToolSettings.png)

## <a name="download-settings"></a>Downloadeinstellungen

### <a name="overwrite-existing-package-files"></a>Vorhandene Paketdateien überschreiben

Wenn Sie diese Einstellung aktivieren, werden die Paketdateien bei jedem Abrufen heruntergeladen. 
* **Wir empfehlen, diese Option deaktiviert zu lassen, um den Verbrauch an Netzwerkbandbreite zu verringern**
* Standardmäßig werden zuvor erworbene Featurepaketdateien nicht erneut heruntergeladen.

### <a name="package-cache"></a>Paketcache

Ändern Sie diese Einstellung, um den Speicherort zu ändern, an dem heruntergeladene Featurepakete gespeichert werden.

> [!NOTE]
> Diese Einstellung ist in dieser Version **schreibgeschützt**. In zukünftigen Versionen wird diese Einstellung möglicherweise konfigurierbar.

## <a name="feature-settings"></a>Featureeinstellungen

### <a name="include-preview-releases"></a>Vorabversionen einschließen

Aktivieren Sie diese Einstellung, um Vorschauversionen zu erhalten.
* Standardmäßig werden Vorschauversionen nicht im Mixed Reality-Featuretool angezeigt 

> [!NOTE]
> Eine Vorschauversion ist dadurch gekennzeichnet, dass sie die Bezeichnung **"-preview"** in der Paketversion enthält.

## <a name="import-settings"></a>Importieren von Einstellungen

### <a name="replace-existing-package-files"></a>Vorhandene Paketdateien ersetzen

Standardmäßig entfernt das Mixed Reality-Featuretool vorherige Exemplare von Paketen, die importiert werden, um die Dateigröße und unnötige Berechnungen zu verringern. 
* Deaktivieren Sie diese Einstellung, wenn Sie alle Versionen behalten möchten.

### <a name="project-relative-import-path"></a>Relativer Importpfad des Projekts

Ändern Sie diese Einstellung, um den Ordnerpfad des Projekts zu aktualisieren, in den Featurepakete beim Importieren kopiert werden. 
* Wenn der Projektordner beispielsweise **C:\GalaxyExplorer** ist, lautet der vollqualifizierte Importpfad **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Diese Einstellung ist in dieser Version **schreibgeschützt**. In zukünftigen Versionen wird diese Einstellung möglicherweise konfigurierbar.

## <a name="see-also"></a>Siehe auch

- [Willkommen beim Mixed Reality-Featuretool](welcome-to-mr-feature-tool.md)