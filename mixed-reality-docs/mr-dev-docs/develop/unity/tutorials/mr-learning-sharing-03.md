---
title: Verbinden mehrerer Benutzer
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie mehrere Benutzer in einer HoloLens 2-Mixed Reality-Anwendung verbinden.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Mehrbenutzerfunktionen, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: ba8a29844489a9153f970f6e39ff2022701c845711ffd9abc232d8da8eeb2e32
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200736"
---
# <a name="3-connecting-multiple-users"></a>3. Verbinden mehrerer Benutzer

In diesem Tutorial lernen Sie, wie Sie mehrere Benutzer im Rahmen einer freigegebenen Live-Benutzererfahrung verbinden. Am Ende des Tutorials können Sie die App auf mehreren Geräten ausführen, und jedem Benutzer wird der bewegte Avatar anderer Benutzer in Echtzeit angezeigt.

## <a name="objectives"></a>Ziele

* Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, klicken Sie auf die folgenden Prefabs, und ziehen Sie sie dann in das Hierarchiefenster, um sie Ihrer Szene hinzuzufügen:

* **NetworkLobby**-Prefab
* **SharedPlayground**-Prefab

![Unity mit neu hinzugefügten, ausgewählten NetworkLobby- und SharedPlayground-Prefabs](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, klicken Sie auf das folgende Prefab, und ziehen Sie es in das Hierarchiefenster, um es Ihrer Szene hinzuzufügen:

* **DebugWindow**-Prefab

![Unity mit neu hinzugefügtem, ausgewähltem DebugWindow-Prefab](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Konfigurieren von PUN zum Instanziieren des Benutzerprefabs

In diesem Abschnitt konfigurieren Sie das Projekt für die Verwendung des PhotonUser-Prefabs.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.

Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:

* Weisen Sie das **PhotonUser**-Prefab aus dem Ordner „Resources“ dem **Photon User Prefab**-Feld zu

![Unity mit teilweise konfigurierter Photon Room-Komponente](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Ausprobieren der Benutzeroberfläche mit mehreren Benutzern

Wenn Sie das Unity-Projekt jetzt für Ihr HoloLens-Gerät erstellen und bereitstellen und zurück in Unity in den Spielmodus wechseln, während die App auf Ihrem HoloLens-Gerät ausgeführt wird, sehen Sie, wie sich der HoloLens-Benutzeravatar bewegt, wenn Sie Ihren Kopf (HoloLens) bewegen:

![Animation, die Unity mit vernetzten Benutzern zeigt.](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> Die App muss eine Verbindung mit Photon herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben Ihr Projekt erfolgreich so konfiguriert, dass es mehreren Benutzern ermöglicht, Verbindungen mit der gleichen Benutzeroberfläche herzustellen und die Bewegungen der anderen Teilnehmer zu sehen. Im nächsten Tutorial implementieren Sie die Funktionalität zum Teilen der Bewegungen von Objekten unter mehreren Geräten.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 4. Freigeben von Objektbewegungen für mehrere Benutzer](mr-learning-sharing-04.md)
