---
title: Beobachter für Szenenverständnis
description: beschreibt Scene Understanding in MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Scene Understanding
ms.openlocfilehash: bf6ceaf98f239e725de3e084bd1ca96a63abc6c28f2434e8ae84ba3f70ee025b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214362"
---
# <a name="scene-understanding-observer"></a>Beobachter für Szenenverständnis

[Scene Understanding](/windows/mixed-reality/scene-understanding) gibt eine semantische Darstellung von Szenenentitäten sowie deren geometrische Formen auf __HoloLens 2__ zurück (HoloLens 1. Generation wird nicht unterstützt).

Einige erwartete Anwendungsfälle dieser Technologie sind:
* Platzieren von Objekten auf der nächsten Oberfläche einer bestimmten Art (z. B. Wand und Boden)
* Erstellen eines Navigationsgitters für Spiele im Plattformstil
* Bereitstellen einer physikalischen Engine-freundlichen Geometrie als Quader
* Beschleunigen sie die Entwicklung, indem Sie vermeiden, ähnliche Algorithmen zu schreiben.

Scene Understanding wird als __experimentelles__ Feature in MRTK 2.6 eingeführt. Sie ist als [räumlicher Beobachter](spatial-awareness-getting-started.md#register-observers) namens in MRTK [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) integriert. Scene Understanding funktioniert sowohl mit der Legacy-XR-Pipeline als auch mit der XR SDK-Pipeline (beide OpenXR (ab MRTK 2.7) und Windows XR-Plug-In). In beiden Fällen `WindowsSceneUnderstandingObserver` wird verwendet.

> [!NOTE] 
> Die Verwendung von Scene Understanding in Remoting wird nicht unterstützt.

## <a name="observer-overview"></a>Übersicht über Beobachter

Wenn sie gefragt [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) wird, gibt [spatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) mit Attributen zurück, die für die Anwendung nützlich sind, um ihre Umgebung zu verstehen. Die Beobachtungshäufigkeit, der zurückgegebene Objekttyp (z. B. Wand, Boden) und andere Beobachterverhalten hängen von der Konfiguration des Beobachters über das Profil ab. Wenn z. B. die Verdeckungsmaske gewünscht ist, muss der Beobachter so konfiguriert werden, dass quads generiert wird. Die beobachtete Szene kann als serialisierte Datei gespeichert werden, die später geladen werden kann, um die Szene im Editor-Wiedergabemodus neu zu erstellen.

## <a name="setup"></a>Setup

> [!IMPORTANT]
> Scene Understanding wird nur für HoloLens 2 und Unity 2019.4 und höher unterstützt.

1. Stellen Sie sicher, dass die Plattform in den Buildeinstellungen auf UWP festgelegt ist.
1. Beziehen Sie das Scene Understanding-Paket über [Mixed Reality Featuretool.](https://aka.ms/MRFeatureTool)

## <a name="using-scene-understanding"></a>Verwenden von Scene Understanding

Die schnellste Möglichkeit, mit Scene Understanding zu beginnen, besteht darin, die Beispielszene zu untersuchen.

### <a name="scene-understanding-sample-scene"></a>Scene Understanding-Beispielszene

Verwenden Sie in Unity den Project-Explorer, um die Szenendatei in zu öffnen und die Wiedergabe zu `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` drücken.

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> Gilt nur für MRTK 2.6.0: Wenn Sie das Mixed Reality Feature Tool verwenden oder anderweitig über UPM importieren, importieren Sie das Beispiel Demos – SpatialAwareness, bevor Sie das Beispiel Experimental - SceneUnderstanding aufgrund eines Abhängigkeitsproblems importieren. Weitere Informationen finden Sie [in diesem GitHub Problem.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)

::: moniker-end
Die Szene veranschaulicht Folgendes:

* Visualisierung beobachteter Szenenobjekte mit in der Anwendungsbenutzeroberfläche zum Konfigurieren des Beobachters
* `DemoSceneUnderstandingController`Beispielskript, das zeigt, wie Sie Beobachtereinstellungen ändern und auf relevante Ereignisse lauschen
* Speichern von Szenendaten auf dem Gerät für die Offlineentwicklung
* Laden zuvor gespeicherter Szenendaten (BYTES-Dateien) zur Unterstützung des Entwicklungsworkflows im Editor

> [!IMPORTANT]
> Standardmäßig ist die `ShouldLoadFromFile` -Eigenschaft des Beobachters auf FALSE festgelegt. Um die Visualisierung eines serialisierten Beispielraums anzuzeigen, lesen Sie den Abschnitt Konfigurieren des [Beobachterdiensts](#configuring-the-observer-service) weiter unten, und legen Sie die -Eigenschaft im Editor auf TRUE fest.
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> Die Beispielszene basiert auf der Legacy-XR-Pipeline. Wenn Sie die XR SDK-Pipeline verwenden, sollten Sie die Profile entsprechend ändern. Das bereitgestellte Scene Understanding Spatial Awareness System-Profil ( `DemoSceneUnderstandingSystemProfile` ) und die Scene Understanding Observer-Profile ( und ) funktionieren für beide `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` Pipelines.
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> Die Beispielszene protokolliert `There is no active AsyncCoroutineRunner when an action is posted.` unter bestimmten Umständen eine Warnung aufgrund der Initialisierungs-/Threadausführungsreihenfolge. Wenn Sie bestätigen können, dass die `AsyncCoroutineRunner` Komponente an das GameObject "Demo Controller" angefügt ist und die Komponente/das GameObject in der Szene aktiviert/aktiv bleibt (Standardfall), kann die Warnung problemlos ignoriert werden. **Stellen Sie jedoch beim Erstellen einer neuen Szene mit Scene Understanding sicher, dass Sie ein leeres GameObject im Stammverzeichnis erstellen und das Skript an `AsyncCoroutineRunner` diese anfügen. Andernfalls funktioniert Scene Understanding möglicherweise nicht ordnungsgemäß.**
::: moniker-end

#### <a name="configuring-the-observer-service"></a>Konfigurieren des Beobachterdiensts

Wählen Sie das Spielobjekt "MixedRealityToolkit" aus, und überprüfen Sie den Inspektor.

![Szenenverständnis der Position in der Hierarchie](../images/spatial-awareness/MRTKHierarchy.png)

![MRTK-Standort im Inspektor](../images/spatial-awareness/MRTKLocation.png)

Mit diesen Optionen kann konfiguriert `WindowsSceneUnderstandingObserver` werden.

### <a name="example-script"></a>Beispielskript

Das Beispielskript _DemoSceneUnderstandingController.cs_ veranschaulicht die wichtigsten Konzepte bei der Arbeit mit dem Scene Understanding-Dienst.

* Abonnieren von Scene Understanding-Ereignissen
* Behandeln von Scene Understanding-Ereignissen
* Konfigurieren von `WindowsSceneUnderstandingObserver` zur Laufzeit

Die Umschalten im Bereich in der Szene ändern das Verhalten des Beobachters zum Verstehen der Szene, indem öffentliche Funktionen dieses Beispielskripts aufgerufen werden.

Wenn *Sie Prefabs instanziieren* aktivieren, wird veranschaulicht, wie Objekte erstellt werden, deren Größe sich an alle [SpatialAwarenessSceneObject-Objekte](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)anpasst, die unter einem übergeordneten Objekt gesammelt werden.

![Democontrolleroptionen](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Hinweise zur erstellten App

Erstellen und Bereitstellen in HoloLens auf standardweise Weise. Nach der Ausführung sollte eine Reihe von Schaltflächen mit den Features wiedergegeben werden.

Beachten Sie, dass es einige Fehler beim Erstellen von Abfragen an den Beobachter gibt. Eine fehlkonfigurierte Abrufanforderung führt dazu, dass Ihre Ereignisnutzlast nicht die erwarteten Daten enthält. Wenn z. B. keine Quader angefordert werden, sind keine Textur der Verdeckungsmaske vorhanden. Wie weise wird kein Weltgitternetz angezeigt, wenn der Beobachter nicht für das Anfordern von Gitternetzen konfiguriert ist. Das `DemoSceneUnderstandingController` Skript übernimmt einige dieser Abhängigkeiten, aber nicht alle.

Auf gespeicherte Szenendateien kann über das [Geräteportal](/windows/mixed-reality/using-the-windows-device-portal) unter zugegriffen `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` werden. Diese Szenendateien können im Editor verwendet werden, indem sie im Beobachterprofil des Inspektors angegeben werden.

![Geräteportal Speicherort der Bytedatei](../images/spatial-awareness/BytesInDevicePortal.png)

![Serialisierte Szenenbytes im Beobachter](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Weitere Informationen

* [Übersicht über Scene Understanding](/windows/mixed-reality/scene-understanding)
* [Übersicht über das Scene Understanding SDK](/windows/mixed-reality/scene-understanding-sdk)
