---
title: 'Tutorials zu den ersten Schritten: 3 Konfigurieren der MRTK-Profile'
description: In diesem Kurs erfahren Sie, wie Sie die MRTK-Profile (Mixed Reality Toolkit) konfigurieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, räumliche Wahrnehmung
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300455"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Konfigurieren der MRTK-Profile

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie die MRTK-Profile angepasst und konfiguriert werden.

Bei den <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK-Profilen</a> handelt es sich um eine Struktur geschachtelter Profile, aus denen die Konfigurationsinformationen für die Initialisierung der MRTK-Systeme und -Funktionen bestehen. Das Profil der obersten Ebene, das Konfigurationsprofil, enthält für jedes der primären Kernsysteme geschachtelte Profile. Jedes geschachtelte Profil ist so konzipiert, dass das Verhalten des entsprechenden Systems konfiguriert wird.

Dieses Beispiel veranschaulicht insbesondere, wie das Gittermodell zur räumlichen Wahrnehmung durch Ändern der Einstellungen des Betrachters für räumliche Gittermodelle ausgeblendet wird. Jedoch können Sie dieselben Prinzipien befolgen, um beliebige Einstellungen oder Werte in den MRTK-Profilen anzupassen.

Wie Sie bei der Bereitstellung Ihres Projekts in Ihrer HoloLens 2 während des [vorherigen Tutorials](mr-learning-base-02.md#congratulations) gesehen haben, ist das <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a>-Gittermodell (für räumliche Wahrnehmung) eine Sammlung von Gittermodellen, die die Geometrie der Umgebung darstellen. Es ist eine hilfreiche Visualisierung für die anfängliche Anzeige, die jedoch in der Regel deaktiviert ist, um die visuelle Ablenkung und die zusätzliche Leistungseinbuße durch die Aktivierung zu vermeiden.

## <a name="objectives"></a>Ziele

* Erfahren, wie MRTK-Profile angepasst und konfiguriert werden
* Ausblenden des Gittermodells für räumliche Wahrnehmung

## <a name="changing-the-spatial-awareness-display-option"></a>Ändern der Anzeigeoptionen für räumliche Wahrnehmung

Dies sind die wichtigsten Schritte, die Sie ausführen, um das Gittermodell zur räumlichen Wahrnehmung auszublenden:

1. Klonen des Standardkonfigurationsprofils
2. Aktivieren des Systems für räumliche Wahrnehmung
3. Klonen des Standardprofils des Systems für räumliche Wahrnehmung
4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle
5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung

> [!NOTE]
> Standardmäßig können die MRTK-Profile nicht bearbeitet werden. Es handelt sich um Standardprofilvorlagen, die Sie zuerst klonen müssen, um sie bearbeiten zu können. Es gibt mehrere verschachtelte Profilebenen. Es ist daher gängige Praxis, mehrere Profile zu klonen und zu bearbeiten, wenn Einstellungen konfiguriert werden sollen.

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie MRTK-Profile und Einstellungen klonen, anpassen und konfigurieren.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 4. Positionieren von Objekten in der Szene](mr-learning-base-04.md)