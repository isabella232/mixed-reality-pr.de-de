---
title: Freigeben von Objektbewegungen für mehrere Benutzer
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Objektbewegungen mit mehreren Benutzern in einer HoloLens 2-Anwendung teilen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Mehrbenutzerfunktionen, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: c9a37dd94083b796da6d5fba2727d739112e411b494af5882ad08525e733a722
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200787"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Freigeben von Objektbewegungen für mehrere Benutzer

In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten teilen, damit alle Teilnehmer einer geteilten Benutzeroberfläche zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können.

## <a name="objectives"></a>Ziele

* Konfigurieren des Projekts zum Teilen der Bewegungen von Objekten
* Erlernen des Erstellens einer einfachen Mehrbenutzer-App zur Zusammenarbeit

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie das Tutorial-Prefab hinzufügen.

Erweitern Sie im Hierarchiefenster das Objekt **MixedRealityPlayspace**, und wählen Sie das untergeordnete Objekt **Hauptkamera** aus. Verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem **Hauptkameraobjekt** die Komponente **AR-Kamera-Manager (Skript)** hinzuzufügen:

![Unity mit teilweise konfigurierter AR-Kamera-Manager-Komponente](images/mr-learning-sharing/sharing-04-section1-step1-0.png)

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, und ziehen Sie das **TableAnchor**-Prefab auf das **SharedPlayground**-Objekt im Hierarchiefenster, um es Ihrer Szene als untergeordnetes Objekt des SharedPlayground-Objekts hinzuzufügen:

![Unity mit neu hinzugefügtem, ausgewähltem TableAnchor-Prefab](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

Vergewissern Sie sich, dass im Hierarchiefenster das Objekt **MixedRealityPlayspace** aufgeklappt und das Objekt **TableAnchor** ausgewählt ist. Ziehen Sie die Komponente **Hauptkamera** auf das Feld **Kamera** der Komponente **AR Session Origin** (AR-Sitzungsursprung) von **TableAnchor**:

![Unity mit konfigurierter Zuweisung für die AR-Sitzungsursprung-Hauptkamera](images/mr-learning-sharing/sharing-04-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Konfigurieren von PUN zum Instanziieren der Objekte

In diesem Abschnitt konfigurieren Sie das Projekt so, dass es die Benutzeroberfläche von Rover-Explorer verwendet, die in den [Tutorials mit den ersten Schritten](mr-learning-base-01.md) erstellt wurde, und definieren, wo sie instanziiert werden soll.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.

Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:

* Weisen Sie dem Feld **RoverExplorer Prefab** das Prefab **RoverExplorer_Complete_Variant** aus dem Ordner „Resources“ zu.

![Unity mit teilweise konfigurierter Photon Room-Komponente](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

Klappen Sie im Hierarchiefenster das **TableAnchor**-Objekt auf, während das untergeordnete Objekt **NetworkRoom** noch ausgewählt ist, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:

* Weisen Sie dem Feld **Rover Explorer Location** (Rover-Explorer-Position) das untergeordnete Objekt **Table** aus dem Hierarchiefenster zu.

![Unity mit konfigurierter Photon Room-Komponente](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Ausprobieren der Benutzeroberfläche mit geteilter Objektbewegung

Wenn Sie das Unity-Projekt jetzt für Ihr HoloLens-Gerät erstellen und bereitstellen und anschließend, wieder in Unity, auf die Schaltfläche „Wiedergabe“ drücken, um in den Spielmodus zu wechseln, während die App auf Ihrem HoloLens-Gerät ausgeführt wird, sehen Sie, wie sich das Objekt in Unity bewegt, wenn Sie es in HoloLens bewegen:

![Animation, die Unity mit vernetzten Objekten zeigt.](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben Ihr Projekt erfolgreich so konfiguriert, dass Objektbewegungen synchronisiert werden, damit Benutzer sehen können, wie sich die Objekte bewegen, wenn andere Benutzer sie bewegen. Im nächsten Tutorial implementieren Sie Funktionen, um die Lösung in der physischen Welt auszurichten. Dadurch wird sichergestellt, dass die Benutzer einander an ihrem tatsächlichen physischen Standort sehen, sodass die Objekte für alle Benutzer in der gleichen physischen Position und Drehung angezeigt werden.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 5. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung](mr-learning-sharing-05.md)
