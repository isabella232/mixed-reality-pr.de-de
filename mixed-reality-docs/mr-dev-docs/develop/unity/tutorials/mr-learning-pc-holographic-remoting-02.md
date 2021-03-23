---
title: Erstellen einer PC-Anwendung für Holographic Remoting
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie eine Anwendung erstellen, die Mixed Reality-Remoting von Ihrem PC zu HoloLens 2 ausführt.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Holographic Remoting am PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: 916a9396c0b29637d5619bac203718e05112b598
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590302"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Erstellen einer PC-Anwendung für Holographic Remoting

In diesem Tutorial erfahren Sie, wie Sie eine PC-App für Holographic Remoting erstellen und zu einem beliebigen Zeitpunkt eine Verbindung mit HoloLens 2 herstellen. Auf diese Weise können Sie 3D-Inhalte in Mixed Reality visualisieren.

## <a name="objectives"></a>Ziele

* Konfigurieren von Unity für Holographic Remoting
* Erfahren Sie, wie Sie die Anwendung mit Visual Studio erstellen und bereitstellen
* Entwickeln von Holographic Remoting-Anwendungen und Herstellen einer Verbindung mit HoloLens

## <a name="configuring-your-scene-for-holographic-remoting"></a>Konfigurieren Ihrer Szene für Holographic Remoting

In diesem Abschnitt konfigurieren Sie das Projekt so, dass Sie Ihre Mixed Reality-Lösung in Echtzeit über eine WLAN-Verbindung von Ihrem PC aus auf das HoloLens 2-Gerät streamen können.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs**, klicken Sie auf das Prefab **HolographicRemoting**, und ziehen Sie es in ihre Szene.

![Unity mit neu hinzugefügtem, noch ausgewähltem HolographicRemoting-Prefab](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>Erstellen Ihrer Anwendung auf dem PC

Ihre Holographic Remoting-App kann jetzt auf Ihrem PC erstellt werden. Führen Sie die folgenden Schritte aus, und nehmen Sie diese Änderungen vor, um die Anwendung auf Ihrem PC zu erstellen.

### <a name="1-set-the-player-settings"></a>1. Festlegen der Playereinstellungen

Wählen Sie im Unity-Menü „Edit > Project Settings“ (Bearbeiten > Projekteinstellungen) aus, um das Fenster „Player Settings“ (Playereinstellungen) zu öffnen.

Erweitern Sie im Fenster „Projekteinstellungen“ die **Veröffentlichungseinstellungen**, scrollen Sie nach unten zum Bereich **Funktionen**, und aktivieren Sie zusätzlich zu den vorhandenen Funktionen das unten angezeigte Funktionskontrollkästchen.

* Internet Client Server
* Privates Netzwerk Client Server

Aktivieren Sie im Abschnitt **XR Settings** (XR-Einstellungen) das Kontrollkästchen **WSA Holographic Remoting Supported** (WSA Holographic Remoting unterstützt), und aktivieren Sie Holographic Remoting.

![Unity-Fenster XR-Einstellungen mit aktiviertem „WSA Holographic Remoting Supported“](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Erstellen des Unity-Projekts

Wählen Sie im Unity-Menü „File > Build Settings“ (Datei > Buildeinstellungen) aus, um das Fenster „Build Settings“ (Buildeinstellungen) zu öffnen.

Klicken Sie im Fenster „Build Settings“ (Buildeinstellungen) auf die Schaltfläche ***Add Open Scenes** _ (Geöffnete Szenen hinzufügen), um den Szenen die aktuelle Szene hinzuzufügen. Klicken Sie in der Liste „Build“ auf die Schaltfläche _ *_Build_**, um das Fenster „Build Universal Windows Platform“ (Universelle Windows-Plattform erstellen) zu öffnen:

![Unity-Fenster „Build Settings“ mit hinzugefügter Szene](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

Wählen Sie im Fenster „Build Universal Windows Platform“ einen passenden Speicherort zum Speichern Ihres Builds aus, z. B. „Documents\MixedRealityLearning“. Erstellen Sie einen neuen Ordner, und geben Sie ihm einen geeigneten Namen, z. B. „PCHolographicRemoting“. Klicken Sie dann auf die Schaltfläche ***Select Folder*** (Ordner auswählen), um den Buildprozess zu starten:

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Warten Sie, bis Unity den Buildvorgang abgeschlossen hat.

![Unity: Buildvorgang wird ausgeführt](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Erstellen und Bereitstellen der Anwendung

Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben. Navigieren Sie im Ordner, und doppelklicken Sie auf die SLN-Datei, um sie in Visual Studio zu öffnen:

![Windows-Explorer mit neu erstellter, ausgewählter Visual Studio-Projektmappe](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation „Installieren der Tools“ angegeben) installiert sind.

Konfigurieren Sie Visual Studio für den PC, indem Sie die Releasekonfiguration, die x64-Architektur und einen lokalen Computer als Ziel auswählen:

![Visual Studio, konfiguriert für den lokalen Computer](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Klicken Sie auf die Schaltfläche ***Lokaler Computer***. Die Anwendung wird auf Ihrem PC erstellt und bereitgestellt. Die Anwendung wird standardmäßig auf Ihrem PC installiert.

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
