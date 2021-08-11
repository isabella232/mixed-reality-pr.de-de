---
title: Einführung in die MRTK-Tutorials
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung von Grund auf zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, Solver, Eye Tracking, Sprachbefehle
ms.localizationpriority: high
ms.openlocfilehash: e8eb878e7ab2fecf27defc5f28e045c4d4768682e95a3a42cda7f324a21617e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224786"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a>1. Einführung in die MRTK-Tutorials

Willkommen bei der Tutorialreihe zu den ersten Schritten! Im Verlauf dieser Tutorials lernen Sie das Mixed Reality Toolkit (MRTK) und einige der von ihm gebotenen Features kennen. Sie erstellen außerdem ein Mixed Reality-Erlebnis, in dem der Benutzer ein Hologramm erforschen kann, das eine Nachbildung des Curiosity-Mars-Rovers der NASA darstellt. Am Ende dieser Reihe haben Sie ein sicheres Verständnis des MRTK und der Weise, in der es Ihren Entwicklungsprozess beschleunigen kann.

Die Tutorials in dieser Reihe sind auf eine bestimmte Abfolge ausgelegt, also arbeiten Sie sie bitte in der richtigen Reihenfolge ab:

1. [Einführung](mr-learning-base-01.md) (Sie sind bereits drin)
2. [Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung](mr-learning-base-02.md)
3. [Konfigurieren der MRTK-Profile](mr-learning-base-03.md)
4. [Positionieren von Objekten in der Szene](mr-learning-base-04.md)
5. [Erstellen dynamischer Inhalte mithilfe von Solvern](mr-learning-base-05.md)
6. [Erstellen der Benutzeroberfläche](mr-learning-base-06.md)
7. [Interagieren mit 3D-Objekten](mr-learning-base-07.md)
8. [Verwenden von Eye Tracking](mr-learning-base-08.md)
9. [Verwenden von Sprachbefehlen](mr-learning-base-09.md)

## <a name="objectives"></a>Ziele

* Erfahren, wie Unity für MRTK konfiguriert wird
* Erfahren, wie Sie auf Ihrem lokalen Computer erstellen und bereitstellen
* Erfahren, wie einige der Schlüsselfunktionen des MRTK verwendet werden
* Erstellen eines umfassenden Mixed Reality-Erlebnisses

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist
* [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) (10.0.18362.0 oder höher)
* Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät

* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2020.3 LTS oder Unity 2019.4 LTS (**OpenXR erfordert 2020.3.8 oder höher, um Fehler zu verhindern**)

Achten Sie bei der Installation von Unity darauf, die folgenden Komponenten unter **Plattformen** zu aktivieren.

* **Buildunterstützung für Universelle Windows-Plattform**
* **Windows-Buildunterstützung (IL2CPP)**

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

Wenn Sie Unity ohne diese Optionen installiert haben, können Sie sie über das Menü **Module hinzufügen** in Unity Hub hinzufügen.

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> Die empfohlene MRTK-Version für diese Tutorialreihe ist MRTK 2.7.2.

> [!Important]
> Diese Tutorialreihe unterstützt Unity 2020 LTS (derzeit 2020.3.x), wenn Sie Open XR oder Windows XR-Plug-In und auch Unity 2019 LTS (derzeit 2019.4.x) verwenden, wenn Sie Legacy WSA oder das Windows XR-Plug-In verwenden. Diese Information hat Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung](mr-learning-base-02.md)
