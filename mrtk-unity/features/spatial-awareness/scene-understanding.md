---
title: Szenenverständnis
description: beschreibt Scene Understanding im MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Scene Understanding
ms.openlocfilehash: 67a8b99a281b6deecd621edb5600578806812d8a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449749"
---
# <a name="scene-understanding"></a>Szenenverständnis

[Scene Understanding](/windows/mixed-reality/scene-understanding) gibt eine semantische Darstellung von Szenenentitäten sowie __ihre__ geometrischen Formen auf HoloLens 2 zurück (HoloLens 1. Generation wird nicht unterstützt).

Zu den erwarteten Anwendungsfällen dieser Technologie gehören:
* Platzieren von Objekten auf der nächstgelegenen Oberfläche einer bestimmten Art (z. B. Wand und Boden)
* Erstellen eines Navigationsgitters für Spiele im Plattformstil
* Bereitstellen von benutzerfreundlichen Geometrien für physikalische Triebwerke als Quader
* Beschleunigen der Entwicklung durch Vermeiden der Notwendigkeit, ähnliche Algorithmen zu schreiben

Scene Understanding wird als __experimentelles Feature__ in MRTK 2.6 eingeführt. Es ist als räumlicher [](spatial-awareness-getting-started.md#register-observers) Beobachter namens in MRTK [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) integriert. Scene Understanding funktioniert sowohl mit der Legacy-XR-Pipeline als auch mit der XR SDK-Pipeline (openXR (ab MRTK 2.7) und dem Windows XR-Plug-In. In beiden Fällen `WindowsSceneUnderstandingObserver` wird verwendet.

> [!NOTE] 
> Die Verwendung von Scene Understanding in Remoting wird nicht unterstützt.

## <a name="observer-overview"></a>Observer-Übersicht

Wenn sie dazu aufgefordert wird, gibt [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) mit Attributen zurück, die für die Anwendung nützlich sind, um ihre Umgebung zu verstehen. Die Beobachtungshäufigkeit, der zurückgegebene Objekttyp (z. B. Wand, Boden) und andere Beobachterverhalten sind von der Konfiguration des Beobachters über das Profil abhängig. Wenn beispielsweise die Okklusionsmaske gewünscht wird, muss der Beobachter so konfiguriert werden, dass Quads generiert werden. Die beobachtete Szene kann als serialisierte Datei gespeichert werden, die später geladen werden kann, um die Szene im Editor-Wiedergabemodus neu zu erstellen.

## <a name="setup"></a>Einrichten

> [!IMPORTANT]
> Scene Understanding wird nur unter HoloLens 2 und Unity 2019.4 und höher unterstützt.

1. Stellen Sie sicher, dass die Plattform in den Buildeinstellungen auf UWP festgelegt ist.
1. Erwerben Sie das Scene Understanding-Paket über [Mixed Reality FeatureTool.](https://aka.ms/MRFeatureTool)

## <a name="using-scene-understanding"></a>Verwenden von Scene Understanding

Die schnellste Möglichkeit, mit Scene Understanding zu beginnen, besteht im Überprüfen der Beispielszene.

### <a name="scene-understanding-sample-scene"></a>Scene Understanding-Beispielszene

Verwenden Sie in Unity den Projekt-Explorer, um die Szenendatei in zu öffnen `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` und die Wiedergabe zu drücken.

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> Gilt nur für MRTK 2.6.0: Wenn Sie das Mixed Reality Feature Tool verwenden oder anderweitig über UPM importieren, importieren Sie das Beispiel Demos – SpatialAwareness, bevor Sie das Experimentell – SceneUnderstanding-Beispiel aufgrund eines Abhängigkeitsproblems importieren. Weitere Informationen [finden Sie in diesem GitHub-Problem.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)

::: moniker-end
Die Szene veranschaulicht Folgendes:

* Visualisierung beobachteter Szenenobjekte mit in der Anwendungsbenutzeroberfläche zum Konfigurieren des Beobachters
* `DemoSceneUnderstandingController`Beispielskript, das zeigt, wie Sie Beobachtereinstellungen ändern und auf relevante Ereignisse lauschen.
* Speichern von Szenendaten auf dem Gerät für die Offlineentwicklung
* Laden zuvor gespeicherter Szenendaten (BYTES-Dateien) zur Unterstützung des Entwicklungsworkflows im Editor

> [!IMPORTANT]
> Standardmäßig ist `ShouldLoadFromFile` die -Eigenschaft des Beobachters auf FALSE festgelegt. Um die Visualisierung eines serialisierten Beispielraums zu sehen, lesen Sie den abschnitt [konfigurierenden](#configuring-the-observer-service) Beobachterdienst weiter unten, und legen Sie die Eigenschaft im Editor auf TRUE fest.
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> Die Beispielszene basiert auf der Legacy-XR-Pipeline. Wenn Sie die XR SDK-Pipeline verwenden, sollten Sie die Profile entsprechend ändern. Das bereitgestellte Scene Understanding Spatial Awareness System-Profil ( `DemoSceneUnderstandingSystemProfile` ) und die Scene Understanding Observer-Profile ( und ) funktionieren für beide `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` Pipelines.
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> Die Beispielszene protokolliert eine Warnung unter bestimmten Umständen aufgrund `There is no active AsyncCoroutineRunner when an action is posted.` der Initialisierungs-/Threadausführungs reihenfolge. Wenn Sie bestätigen können, dass die Komponente an das GameObject "Demo Controller" angefügt ist und die Komponente/das GameObject in der Szene aktiviert/aktiv bleibt (Standardfall), kann die Warnung sicher ignoriert `AsyncCoroutineRunner` werden. **Wenn Sie jedoch eine neue Szene mit Scene Understanding erstellen, stellen Sie sicher, dass Sie ein leeres GameObject im Stammverzeichnis erstellen und das Skript an dieses anfügen. Andernfalls funktioniert Scene Understanding möglicherweise `AsyncCoroutineRunner` nicht ordnungsgemäß.**
::: moniker-end

#### <a name="configuring-the-observer-service"></a>Konfigurieren des Observer-Diensts

Wählen Sie das Spielobjekt "MixedRealityToolkit" aus, und überprüfen Sie den Inspektor.

![Szenenverständnis des Standorts in der Hierarchie](../images/spatial-awareness/MRTKHierarchy.png)

![MRTK-Standort im Inspektor](../images/spatial-awareness/MRTKLocation.png)

Mit diesen Optionen kann konfiguriert `WindowsSceneUnderstandingObserver` werden.

### <a name="example-script"></a>Beispielskript

Das Beispielskript _DemoSceneUnderstandingController.cs_ veranschaulicht die wichtigsten Konzepte bei der Arbeit mit dem Scene Understanding-Dienst.

* Abonnieren von Scene Understanding-Ereignissen
* Behandeln von Scene Understanding-Ereignissen
* Konfigurieren von zur `WindowsSceneUnderstandingObserver` Laufzeit

Die Umschalter im Bereich der Szene ändern das Verhalten des Szenenverständnisbeobachter, indem sie öffentliche Funktionen dieses Beispielskripts aufrufen.

Wenn Sie *Prefabs instanziieren* aktivieren, wird das Erstellen von Objekten veranschaulicht, deren Größe sich an alle [SpatialAwarenessSceneObject-Objekte](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)anpasst, die unter einem übergeordneten Objekt sauber gesammelt werden.

![Democontrolleroptionen](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Hinweise zur erstellten App

Erstellen Und bereitstellen Sie HoloLens auf die Standard weise. Nach der Ausführung sollte eine Reihe von Schaltflächen mit den Features zu spielen scheinen.

Beachten Sie, dass es einige Fehler beim Ausführen von Abfragen an den Beobachter gibt. Eine fehlkonfigurierte Abrufanforderung führt dazu, dass Ihre Ereignisnutzlast nicht die erwarteten Daten enthält. Wenn sie beispielsweise keine Quads anfordern, sind keine Okklusionsmaskentexturen vorhanden. Wie weise wird kein World Mesh angezeigt, wenn der Beobachter nicht für das Anfordern von Gitternetzen konfiguriert ist. Das `DemoSceneUnderstandingController` Skript übernimmt einige dieser Abhängigkeiten, aber nicht alle.

Auf gespeicherte Szenendateien kann über das [Geräteportal unter zugegriffen](/windows/mixed-reality/using-the-windows-device-portal) `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` werden. Diese Szenendateien können im Editor verwendet werden, indem sie im Beobachterprofil im Inspektor angegeben werden.

![Geräteportal Speicherort der Bytesdatei](../images/spatial-awareness/BytesInDevicePortal.png)

![Serialisierte Szenenbytes in Observer](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Weitere Informationen

* [Übersicht über Scene Understanding](/windows/mixed-reality/scene-understanding)
* [Übersicht über das Scene Understanding SDK](/windows/mixed-reality/scene-understanding-sdk)