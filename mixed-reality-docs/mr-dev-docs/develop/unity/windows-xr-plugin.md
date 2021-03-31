---
title: Verwenden des Windows XR-Plug-ins
description: Erfahren Sie, wie Sie Ihre Unity-Projekte mit und ohne mrtk mithilfe von Windows-XR-Unterstützung einrichten.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung, Legacy, mrtk, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938107"
---
# <a name="using-windows-xr-plugin"></a>Verwenden des Windows-

Für Entwickler, die auf Unity 2020 abzielen, ermöglicht das Windows-XR-Plug-in den Zugriff auf gemischte Reality-Features auf hololens 2-und Windows Mixed Reality-  Dieses Plug-in wird auch in Unity 2019 unterstützt, obwohl bei Verwendung dieses Plug-Ins für diese Version einige bekannte Inkompatibilitäten mit räumlichen Azure-Anker vorhanden sind.

Obwohl Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (mrtk)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) erstellt haben, das die WMR-Umgebung automatisch einrichten wird, möchten viele Entwickler ihre Erfahrungen von Grund auf neu erstellen.  In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt für die Entwicklung mit gemischter Realität ordnungsgemäß einrichten, unabhängig davon, ob Sie mrtk verwenden oder nicht.  Die Einstellungen, die Sie ändern müssen, werden in zwei Kategorien unterteilt: Einstellungen pro Projekt und Einstellungen pro Szene.

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit mrtk

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

> [!div class="nextstepaction"]
> [Testen Sie unsere mrtk-Tutorials](tutorials/mr-learning-base-01.md)

Weitere Featuredetails finden Sie in [der Dokumentation zu mrtk](/windows/mixed-reality/mrtk-unity) .

## <a name="manual-setup-without-mrtk"></a>Manuelles Setup ohne mrtk

Wenn Sie auf Desktop VR abzielen, empfiehlt es sich, die eigenständige PC-Plattform zu verwenden, die für ein neues Unity-Projekt standardmäßig ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit PC, Mac & eigenständige Plattform hervorgehoben](images/wmr-config-img-3.png)

Wenn Sie hololens 2 als Ziel verwenden, müssen Sie zum universelle Windows-Plattform wechseln:

1.  **Datei > Buildeinstellungen auswählen...**
2.  Wählen Sie in der Platt Form Liste **universelle Windows-Plattform** aus, und wählen Sie **Plattform wechseln**
3.  **Architektur** auf **Arm 64** festlegen
4.  **Zielgerät** auf **hololens** festlegen
5.  **Buildtyp** auf **D3D** festlegen
6.  **UWP SDK** auf **Letztes installiert** festlegen
7.  **Buildkonfiguration** auf **Release** festlegen, da beim Debuggen bekannte Leistungsprobleme auftreten

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor öffnen mit hervorgehobener universelle Windows-Plattform](images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass Sie beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellen können:

1. Navigieren Sie im Unity-Editor zu **Edit > Project Settings** , und wählen Sie die **Verwaltung von XR Plugin** aus.

2. Select 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-5.png)

3. Wählen Sie " **XR beim Start** und **Windows Mixed Reality** initialisieren" aus.

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-7.png)

4. Erweitern Sie den Abschnitt **XR-Plug-in-Verwaltung** , und wählen Sie die Registerkarte **universelle Windows-Plattform**
5. Wenn Sie Unity 2020 oder höher verwenden, sehen Sie die Optionen zum Überprüfen von **openxr** oder **Windows Mixed Reality**. 
    * Sie können beide Laufzeitoptionen auswählen.  Wenn Sie speziell für die hololens 2 oder den HP-Reverb-G2 entwickeln und das **openxr** testen möchten, wählen Sie das Feld openxr aus, und lesen Sie unser Handbuch zum [Verwenden des gemischten Reality openxr-Plug-Ins für Unity](openxr-getting-started.md) , um sich vor der Rückkehr zu diesem Tutorial ordnungsgemäß für diese Geräte einzurichten.

> [!NOTE]
> Ab Unity 2020 LTS geht Microsoft mit der Entwicklung mit openxr um.  Wenn wir zu diesem Pfad migrieren, wird das Windows-XR-Plug-in in Unity 2021,1 als veraltet markiert und 2021,2 entfernt, sodass openxr der einzige unterstützte Pfad ist. Weitere Informationen finden Sie unter [Verwenden des gemischten Reality openxr-Plug](openxr-getting-started.md)-ins.

6. Wenn Sie das **Windows Mixed Reality** -Plug-in auswählen, aktivieren Sie alle Kontrollkästchen, und legen Sie den tiefen Übermittlungs **Modus** auf **Tiefe 16 Bit** fest.

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet mit hervorgehobenem Windows Mixed Reality-Abschnitt](images/wmr-config-img-8.png)
