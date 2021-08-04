---
title: Erstellen einer PC-Anwendung für Holographic Remoting
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie eine Anwendung erstellen, die Mixed Reality-Remoting von Ihrem PC zu HoloLens 2 ausführt.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Holographic Remoting am PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: 19c10ad0cdad70b38663f9da0f7d2a1f1702d94d
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757232"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Erstellen einer PC-Anwendung für Holographic Remoting

In diesem Tutorial erfahren Sie, wie Sie eine PC-App erstellen, die Holographic Remoting verwendet, sodass Sie den aktuellen Stand Ihrer Arbeit an die HoloLens streamen und anzeigen können, ohne ihn zuerst erstellen zu müssen.

[Erlernen der Grundlagen von Holographic Remoting.](../../platform-capabilities-and-apis/holographic-remoting-overview.md)

## <a name="objectives"></a>Ziele

* Konfigurieren von Unity für Holographic Remoting
* Erfahren Sie, wie Sie die Anwendung mit Visual Studio erstellen und bereitstellen
* Entwickeln einer Holographic Remoting-Anwendung und Herstellen einer Verbindung mit HoloLens

## <a name="configuring-the-capabilities"></a>Konfigurieren der Funktionen

Erweitern Sie im Fenster **Projekteinstellungen** die **Veröffentlichungseinstellungen**, scrollen Sie nach unten zum Bereich „Funktionen“, und aktivieren Sie zusätzlich zu den vorhandenen Funktionen das unten angezeigte Funktionskontrollkästchen.

* Internet Client Server
* Privates Netzwerk Client Server

![Aktivieren von Funktionen](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a>Erstellen Ihrer Anwendung auf dem PC

Ihre Holographic Remoting-App kann jetzt auf Ihrem PC erstellt werden. Führen Sie die folgenden Schritte aus, und nehmen Sie diese Änderungen vor, um die Anwendung auf Ihrem PC zu erstellen.

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a>Testen einer Holographic Remoting-Remoteanwendung

Zum Herstellen einer Verbindung Ihrer PC-Anwendung mit HoloLens 2 führen Sie den folgenden Prozess aus:

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Installieren der Remoting Player-Anwendung auf HoloLens 2-Geräten

* Besuchen Sie auf dem HoloLens 2-Gerät die Store-App, und suchen Sie nach „**Remoting Player**“.
* Wählen Sie die **Remoting Player**-App aus.
* Tippen Sie auf **Installieren**, um die App herunterzuladen und zu installieren.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Verbinden der PC-App für Holographic Remoting mit dem Remoting Player

* Starten Sie den **Remoting Player** auf Ihrem HoloLens-Gerät.
* Notieren Sie sich die HoloLens-**IP-Adresse**. Sie wird vom **Remoting Player** als Hologramm angezeigt, sobald er gestartet wird.
* Öffnen Sie die PC-Anwendung für Holographic Remoting auf Ihrem PC.
* Nachdem die Anwendung gestartet wurde, geben Sie die **IP-Adresse** ein, und klicken Sie auf die Schaltfläche **Connect** (Verbinden), um eine Verbindung herzustellen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie eine Remote-App für Holographic Remoting erstellen und zu einem beliebigen Zeitpunkt eine Verbindung mit HoloLens 2 herstellen. Auf diese Weise können Sie 3D-Inhalte in Mixed Reality visualisieren. Sobald das HoloLens-Gerät eine Verbindung mit der PC-Anwendung für Holographic Remoting hergestellt hat, sollte die Mixed Reality-Lösung auf das HoloLens 2-Gerät gestreamt werden.
