---
title: Einrichten Ihres Unreal-Projekts
description: Erfahren Sie, wie Sie Ihr Projekt mit der neuesten Version der Unreal-Engine und dem Mixed Reality-Featuretool einrichten.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, Mixed Reality, Entwicklung, Features, neues Projekt, Emulator, Dokumentation, Anleitungen, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, aktuell, Tools, erste Schritte, Grundlagen, Unreal, Toolkit, Hub, Installation, Windows, HoloLens, openxr, mrtk
ms.openlocfilehash: fee0e9a9deb92dffca742e19ebe27d2dd4cb53c0
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905581"
---
# <a name="setting-up-your-unreal-project"></a>Einrichten Ihres Unreal-Projekts

Es wird empfohlen, die [Unreal-Engine, Version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) oder höher, zu installieren, um die integrierte Unterstützung von HoloLens in vollem Umfang nutzen zu können.

Wechseln Sie im Epic Games-Startprogramm zur Registerkarte **Bibliothek**, klicken Sie neben **Starten** auf den Dropdownpfeil und dann auf **Optionen**. Wählen Sie unter **Target Platforms** (Zielplattformen) **HoloLens 2** aus, und klicken Sie auf **Apply** (Übernehmen).
![HoloLens 2-Installationsoption für Unreal](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importieren des Mixed Reality-Toolkits für Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) ist ein plattformübergreifendes Open Source-Entwicklungskit für Mixed Reality-Anwendungen. MRTK bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. Das Toolkit soll die Entwicklung von Anwendungen für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.

Wenn Sie noch nicht über ein Mixed Reality-Projekt verfügen, befolgen Sie die ersten drei Abschnitte der [HoloLens 2-Einstiegstutorials](tutorials/unreal-uxt-ch1.md), um ein Projekt für das MRTK vorzubereiten.

### <a name="introducing-the-mrtk-hub-for-unreal"></a>Einführung in den MRTK-Hub für Unreal

Es empfiehlt sich, den MRTK-Hub zum Abrufen von MRTK-Plug-Ins zu verwenden. Das ist eine neue Möglichkeit für Entwickler, Microsoft Mixed Reality-Plug-Ins zu entdecken und zu aktualisieren und sie ihren Unreal-Projekten hinzuzufügen. Sie können Plug-Ins anzeigen, ihre Abhängigkeiten ersehen und sie in Ihrem Projekt installieren, ohne den Unreal-Editor zu verlassen.

- Entdecken Sie neue Microsoft Mixed Reality-Plug-Ins, und installieren Sie sie und ihre Abhängigkeiten in Ihrem Unreal-Projekt.
- Halten Sie Ihre Microsoft Mixed Reality-Plug-Ins auf dem neuesten Stand.
- Entfernen Sie Microsoft Mixed Reality-Plug-Ins aus Ihrem Projekt, wenn Sie sie nicht mehr benötigen.

> [!NOTE]
> Der MRTK-Hub für Unreal ist nur für die Unreal Engine, Version 4.26 oder höher, verfügbar. Für Unreal Engine, Version 4.25, können Sie MRTK-Plug-Ins aus dem Unreal Engine Marketplace oder GitHub abrufen, wie im Abschnitt [Erste Schritte](unreal-development-overview.md#1-getting-started) beschrieben.

#### <a name="installing-the-mrtk-hub"></a>Installieren des MRTK-Hubs

Laden Sie das Plug-In aus dem [Unreal Engine Marketplace](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-toolkit-hub)herunter, öffnen Sie Ihr Projekt, und aktivieren Sie das Plug-In dann im _Mixed Reality_-Abschnitt des Menüs _Plug-Ins_. Starten Sie den Editor auf die entsprechende Aufforderung hin neu.

![Aktivieren des MRTK Hub-Plug-Ins](images/hub-enable-plugin.png)

Sobald das Plug-In für Ihr Projekt aktiviert ist, können Sie über die Symbolleistenschaltfläche auf den Hub zugreifen.

![Öffnen des MRTK-Hub-Fensters](images/hub-toolbar.png)

#### <a name="installing-mixed-reality-plugins"></a>Installieren von Mixed Reality-Plug-Ins

Um ein Plug-In mithilfe des Hubs zu installieren, wählen Sie das Plug-In aus, das Sie Ihrem Projekt hinzufügen möchten, und klicken Sie dann auf die Schaltfläche _Installieren_. Stellen Sie zum Herunterladen des Plug-Ins sicher, dass im Feld _Probleme_ keine Konflikte gefunden werden, und klicken Sie auf _Bestätigen_. Nachdem das Plug-In heruntergeladen wurde, werden Sie aufgefordert, den Editor neu zu starten. Leider können wir den Editor nicht automatisch neu für Sie starten. denn manchmal wird die neue Editor-Instanz gestartet, bevor die Installation abgeschlossen ist.

![Installieren eines Plug-Ins mithilfe des MRTK-Hubs](images/hub-download.png)

Nach dem Schließen des Editors wird eine Eingabeaufforderung mit einer Statusleiste zum Entpacken des heruntergeladenen Plug-Ins angezeigt. Für jedes installierte Plug-In wird eine Eingabeaufforderung angezeigt. Nachdem das Entpacken abgeschlossen ist, können Sie den Editor erneut öffnen und Ihre [Mixed Reality Development Journey](unreal-quickstart.md) fortsetzen.

![MRTK-Hub beim Entpacken eines Plug-Ins über die Eingabeaufforderung](images/hub-unpack.png)

> [!IMPORTANT]
> Nachdem das Plug-In installiert ist, muss es wie jedes andere Plug-In auf Projektebene in die Quellcodeverwaltung eingecheckt werden.

#### <a name="updating-mixed-reality-plugins"></a>Aktualisieren von Mixed Reality-Plug-Ins

Zum Aktualisieren eines Plug-Ins mithilfe des Hubs wählen Sie das zu aktualisierende Plug-In in der Liste aus, und drücken Sie die Schaltfläche _Installieren_. Achten Sie zum Herunterladen des Plug-Ins darauf, dass im Feld _Probleme_ keine Konflikte gefunden werden, und klicken Sie auf _Bestätigen_. Sie werden aufgefordert, den Editor neu zu starten, um das Update abzuschließen. Plug-In-Aktualisierungen erfolgen beim Starten des Editors, sodass sie nicht auf den Abschluss des Entpackens warten müssen, bevor Sie den Editor erneut öffnen.

![Aktualisieren eines Plug-Ins über den MRTK-Hub](images/hub-update.png)

#### <a name="removing-mixed-reality-plugins"></a>Entfernen von Mixed Reality-Plug-Ins

Zum Deinstallieren eines Plug-Ins mithilfe des Hubs wählen Sie das Plug-In aus, das Sie entfernen möchten, und wählen Sie dann in der Dropdownliste die Version aus, die Sie installiert haben. Stellen Sie zum Herunterladen des Plug-Ins sicher, dass im Feld _Probleme_ keine Konflikte gefunden werden, und klicken Sie auf _Bestätigen_. Sie werden aufgefordert, den Editor neu zu starten, um die Entfernung abzuschließen.

![Entfernen eines Plug-Ins über den MRTK-Hub](images/hub-remove.png)

#### <a name="reviewing-changes-and-detecting-incompatibilities"></a>Überprüfen von Änderungen und Erkennen von Inkompatibilitäten

Sie können die genauen Änderungen, die an Ihrem Projekt vorgenommen werden, im unteren Abschnitt des Hubfensters anzeigen. Hier sehen Sie die Plug-Ins, die Ihrem Projekt hinzugefügt oder daraus entfernt werden, sowie mögliche Inkompatibilitäten, die Probleme verursachen können, wenn die Änderungen vorgenommen wurden.

> [!NOTE]
> In der Liste _Probleme_ werden Inkompatibilitäten in der Version der Unreal-Engine und den Versionen der Plug-In-Abhängigkeiten angezeigt, jedoch werden Probleme nicht automatisch behoben oder Vorschläge zu ihrer Behebung gemacht.

![Versuch, ein inkompatibles Plug-In zu installieren](images/hub-issues.png)

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unreal-Logobild](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Wenn Sie MRTK für Unreal nicht verwenden möchten, müssen Sie für alle Interaktionen und Verhaltensweisen selber Skripts erstellen.