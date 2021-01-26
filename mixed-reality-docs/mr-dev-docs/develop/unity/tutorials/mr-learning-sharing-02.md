---
title: Einrichten von Photon Unity Networking
description: In diesem Kurs lernen Sie, wie Sie Photon Unity Network in einer HoloLens 2-Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Mehrbenutzerfunktionen, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, PUN
ms.localizationpriority: high
ms.openlocfilehash: 1c47da28b3ccdc706f372749f265ac0329a2327b
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699144"
---
# <a name="2-setting-up-photon-unity-networking"></a>2. Einrichten von Photon Unity Networking

In diesem Tutorial bereiten Sie sich mithilfe des Photon Unity-Netzwerks (PUN) auf das Erstellen einer gemeinsamen Benutzeroberfläche vor. Sie erfahren, wie Sie eine PUN-App erstellen, PUN-Ressourcen in Ihr Unity-Projekt importieren und Ihr Unity-Projekt mit der PUN-App verbinden.

## <a name="objectives"></a>Ziele

* Erfahren, wie eine PUN-App erstellt wird
* Erfahren, wie die PUN-Ressourcen gesucht und importiert werden
* Erfahren, wie eine Verbindung Ihres Unity-Projekts mit der PUN-App hergestellt wird

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zunächst die Anweisungen unter [Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung](mr-learning-base-02.md) – jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2) –, die die folgenden Schritte beinhalten:

1. [Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*
2. [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform)
3. [Importieren der TextMeshPro Essential-Ressourcen](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Importieren des Mixed Reality-Toolkits](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Konfigurieren des Unity-Projekts](mr-learning-base-02.md#configuring-the-unity-project)
6. [Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und Bezeichnen der Szene mit einem passenden Namen, z. B. *MultiUserCapabilities*

Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoptionen für räumliche Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um die folgenden Aufgaben auszuführen:

1. Ändern des **MRTK-Konfigurationsprofils** in **DefaultHoloLens2ConfigurationProfile**.
1. Ändern der **Anzeigeoptionen für das Gittermodell für räumliche Wahrnehmung** in **Occlusion** (Verdeckung).

## <a name="enabling-additional-capabilities"></a>Aktivieren zusätzlicher Funktionen

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Player-Einstellungen zu öffnen, und suchen Sie dann den Abschnitt **Player** >  **Publishing Settings** (Player > Veröffentlichungseinstellungen):

![Unity: Player-Einstellungen](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

Scrollen Sie in **Publishing Settings** (Veröffentlichungseinstellungen) nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone**, **SpatialPerception** und **GazeInput**, die Sie im Schritt [Konfigurieren des Unity-Projekts](mr-learning-base-02.md#configuring-the-unity-project) weiter oben aktiviert haben, aktiviert sind.

Aktivieren Sie dann die folgenden zusätzlichen Funktionen:

* **InternetClientServer**-Funktion
* **PrivateNetworkClientServer**-Funktion

![Einstellungen für Unity-Funktionen](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a>Installieren von integrierten Unity-Paketen

Wählen Sie im Unity-Menü **Fenster** > **Package Manager** (Paket-Manager) aus, um das Fenster „Package Manager“ zu öffnen, wählen Sie **AR Foundation** aus, und klicken Sie auf die Schaltfläche **Install** (Installieren), um das Paket zu installieren:

![Unity-Paket-Manager mit ausgewählter AR Foundation](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> Sie installieren das AR Foundation-Paket, da es für das Azure Spatial Anchor SDK erforderlich ist, das Sie im nächsten Abschnitt importieren.

## <a name="importing-the-tutorial-assets"></a>Importieren der Tutorialressourcen

Fügen Sie Ihrem Unity-Projekt das AzurespatialAnchors SDK V2.7.1 hinzu. Um die Pakete hinzuzufügen, befolgen Sie dieses [Tutorial](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).


Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:
 
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:

![Unity-Fenster „Hierarchie“, „Szene“ und „Projekt“ nach dem Importieren der Tutorialressourcen](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

> [!NOTE]
> Nach dem Importieren des Pakets mit den MultiUserCapabilities-Tutorialressourcen werden im Konsolenfenster mehrere [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246)-Fehler angezeigt, die besagen, dass der Typ oder Namespace fehlt. Dies ist das erwartungsgemäße Verhalten, das im nächsten Abschnitt durch das Importieren der PUN-Ressourcen behoben wird.

## <a name="importing-the-pun-assets"></a>Importieren der PUN-Ressourcen

Wählen Sie im Unity-Menü **Window** > **Asset Store** (Fenster > Asset Store) aus, um das Asset Store-Fenster zu öffnen, suchen Sie unter „Exit Games“ **PUN 2 - FREE** aus, und klicken Sie dann auf die Schaltfläche **Download**, um das Ressourcenpaket in Ihr Unity-Konto herunterzuladen.

Wenn der Download abgeschlossen ist, klicken Sie auf die **Import**-Schaltfläche, um das Fenster Import Unity Package (Unity-Paket importieren) zu öffnen:

![Unity Asset Store mit „PUN 2 – Free“](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:

![Unity mit Fenster zum Importieren von PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

Nachdem Unity den Importvorgang abgeschlossen hat, wird das Fenster des PUN-Assistenten mit geöffnetem PUN-Setupmenü geladen. Für den Augenblick können Sie dieses Fenster ignorieren oder schließen:

![Unity mit Fenster zum Einrichten von PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a>Erstellen der PUN-Anwendung

In diesem Abschnitt erstellen Sie ein Photon-Konto, falls dies noch nicht geschehen ist, und Sie erstellen eine neue PUN-App.

Navigieren Sie zum Photon-<a href="https://dashboard.photonengine.com/account/signin" target="_blank">Dashboard</a>, und melden Sie sich an, wenn Sie bereits über ein Konto verfügen, das Sie verwenden möchten, oder klicken Sie andernfalls auf den Link **Create One** (Konto erstellen), und befolgen Sie die Anweisungen zum Registrieren eines neuen Kontos:

![Photon-Anmeldeseite](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

Nachdem Sie sich angemeldet haben, klicken Sie auf die Schaltfläche **Create a New App** (Neue App erstellen):

![Die Seite „Willkommen“ des Photon-Dashboards](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

Geben Sie auf der Seite „Create a New Application“ (Neue Anwendung erstellen) die folgenden Werte ein:

* Wählen Sie als Photon-Typ „PUN“ aus.
* Geben Sie als Namen einen passenden Namen ein, beispielsweise _MRTK-Tutorials_
* Geben Sie als Beschreibung optional eine passende Beschreibung ein
* Lassen Sie das Feld „URL“ leer

Klicken Sie dann auf die Schaltfläche **Create** (Erstellen), um die neue App zu erstellen:

![Photon-Seite „Anwendung erstellen“](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

Nachdem Photon den Erstellungsvorgang abgeschlossen hat, wird die neue PUN-App auf Ihrem Dashboard angezeigt:

![Photon-Seite „Anwendung“](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Verbinden des Unity-Projekts mit der PUN-Anwendung

In diesem Abschnitt verbinden Sie Ihr Unity-Projekt mit der PUN-App, die Sie im vorherigen Abschnitt erstellt haben.

Klicken Sie auf dem Photon-Dashboard auf das Feld **App-ID**, um die App-ID anzuzeigen, und kopieren Sie sie dann in die Zwischenablage:

![Photon-Seite „Anwendung“ mit ausgewählter App-ID](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

Wählen Sie im Unity-Menü **Window** > **Photon Unity Networking** > **PUN Wizard** (Fenster > Photon Unity-Netzwerk > PUN-Assistent) aus, um das Fenster des Pun-Assistenten zu öffnen, klicken Sie auf die Schaltfläche **Setup Project** (Projekt einrichten), um das PUN-Setupmenü zu öffnen, und konfigurieren Sie es wie folgt:

* Fügen Sie im Feld **AppId or Email** (AppID oder E-Mail) die PUN-App-ID ein, die Sie im vorherigen Schritt kopiert hatten

Klicken Sie anschließend auf die Schaltfläche **Setup Project** (Projekt einrichten), um die AppID zu übernehmen:

![Unity-Fenster zum Einrichten von PUN mit eingetragener AppID](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

Nachdem Unity den PUN-Setupvorgang abgeschlossen hat, wird im PUN-Setupmenü die Meldung **Done!** (Fertig!) angezeigt und automatisch im Projektfenster die Ressource **PhotonServerSettings** ausgewählt, sodass deren Eigenschaften im Inspektorfenster angezeigt werden:

![Unity-Fenster zum Einrichten von PUN mit angewendetem „Setup Project“](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben erfolgreich eine PUN-Anwendung erstellt und sie mit Ihrem Unity-Projekt verbunden. Der nächste Schritt besteht im Zulassen von Verbindungen mit anderen Benutzern, sodass sich mehrere Benutzer gegenseitig sehen können.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. Verbinden mehrerer Benutzer](mr-learning-sharing-03.md)