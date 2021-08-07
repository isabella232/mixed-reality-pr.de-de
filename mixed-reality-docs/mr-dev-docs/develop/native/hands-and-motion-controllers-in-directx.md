---
title: Hände und Motion-Controller in DirectX
description: Erste Schritte mit dem Entwicklerhandbuch für die Verwendung von Handtracking- und Motion-Controllern in nativen DirectX-Apps.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: Hände, Motion-Controller, DirectX, Eingabe, Hologramme, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 13988df80052ef85662dcf9834406baa91d48f7c0b70242d1c904548c2707105
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210956"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Hände und Motion-Controller in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren nativen WinRT-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API empfohlen.](openxr-getting-started.md)**

In Windows Mixed Reality wird die [](../../design/motion-controllers.md) Eingabe von Hand- und Bewegungscontrollern über die APIs für räumliche Eingaben verarbeitet, die sich im [Windows. Benutzeroberfläche. Input.Spatial-Namespace.](/uwp/api/windows.ui.input.spatial) Auf diese Weise können Sie gängige Aktionen wie **Select** problemlos auf die gleiche Weise über Hände und Motion Controller verarbeiten.

## <a name="getting-started"></a>Erste Schritte

Um auf räumliche Eingaben in Windows Mixed Reality, beginnen Sie mit der SpatialInteractionManager-Schnittstelle.  Sie können auf diese Schnittstelle zugreifen, indem  [Sie SpatialInteractionManager::GetForCurrentView](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)aufrufen, in der Regel einige Zeit während des App-Starts.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Die Aufgabe von SpatialInteractionManager besteht im Bereitstellen des Zugriffs auf [SpatialInteractionSources,](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)die eine Eingabequelle darstellen.  Im System sind drei Arten von SpatialInteractionSources verfügbar.
* **Hand** stellt die erkannte Hand eines Benutzers dar. Handquellen bieten verschiedene Features, die auf dem Gerät basieren, von einfachen Gesten auf HoloLens bis hin zur vollständig artikulierten Handverfolgung auf HoloLens 2. 
* **Controller** stellt einen gekoppelten Bewegungscontroller dar. Motion-Controller können verschiedene Funktionen bieten, z. B. Trigger auswählen, Menüschaltflächen, Schaltflächen zum Erfassen, Touchpads und Sticks.
* **Die Stimme** stellt die vom Spracherkennungssystem erkannten Schlüsselwörter des Benutzers dar. Diese Quelle fügt z. B. ein Select-Drücken und -Release ein, wenn der Benutzer "Auswählen" sagt.

Daten pro Frame für eine Quelle werden durch die  [SpatialInteractionSourceState-Schnittstelle](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) dargestellt. Es gibt zwei verschiedene Möglichkeiten, auf diese Daten zu zugreifen, je nachdem, ob Sie ein ereignisgesteuertes oder abrufbasiertes Modell in Ihrer Anwendung verwenden möchten.

### <a name="event-driven-input"></a>Ereignisgesteuerte Eingabe
SpatialInteractionManager stellt eine Reihe von Ereignissen zur Verfügung, auf die Ihre App lauschen kann.  Einige Beispiele sind   [SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased und [SourceUpdated](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Der folgende Code gliedert beispielsweise einen Ereignishandler namens MyApp::OnSourcePressed mit dem SourcePressed-Ereignis ein.  Dies ermöglicht Ihrer App das Erkennen von Pressen an jeder Art von Interaktionsquelle.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Dieses gedrückte Ereignis wird asynchron an Ihre App gesendet, zusammen mit dem entsprechenden SpatialInteractionSourceState zum Zeitpunkt des Drückens. Ihre App oder Spiel-Engine möchte möglicherweise sofort mit der Verarbeitung beginnen oder die Ereignisdaten in der Eingabeverarbeitungsroutine in die Warteschlange stellen. Hier ist eine Ereignishandlerfunktion für das SourcePressed-Ereignis, die überprüft, ob die Schaltfläche "Auswählen" gedrückt wurde.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

Mit dem obigen Code wird nur überprüft, ob die Select-Taste gedrückt wird. Dies entspricht der primären Aktion auf dem Gerät. Beispiele hierfür sind das Verwenden eines AirTap-HoloLens oder das Pullen des Triggers auf einem Motion-Controller.  "Select"-Pressen stellen die Absicht des Benutzers dar, das Hologramm zu aktivieren, auf das er abzielen soll.  Das SourcePressed-Ereignis wird für eine Reihe verschiedener Schaltflächen und Gesten angezeigt, und Sie können andere Eigenschaften in SpatialInteractionSource überprüfen, um diese Fälle zu testen.

### <a name="polling-based-input"></a>Abrufbasierte Eingabe
Sie können spatialInteractionManager auch verwenden, um den aktuellen Zustand der Eingabe für jeden Frame abzurufen.  Rufen Sie hierzu [getDetectedSourcesAtTimestamp für jeden](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) Frame auf.  Diese Funktion gibt ein Array zurück, das [einen SpatialInteractionSourceState für](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) jede aktive [SpatialInteractionSource enthält.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource) Dies bedeutet einen für jeden aktiven Bewegungscontroller, einen für jede nachverfolgte Hand und einen für die Spracherkennung, wenn kürzlich ein Select-Befehl ausgesprochen wurde. Anschließend können Sie die Eigenschaften auf jedem SpatialInteractionSourceState überprüfen, um Eingaben in Ihre Anwendung zu führen. 

Hier ist ein Beispiel dafür, wie Sie mithilfe der Abrufmethode nach der Select-Aktion suchen. Die *Vorhersagevariable* stellt ein [HolographicFramePrediction-Objekt](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) dar, das aus dem [HolographicFrame -Objekt erhalten werden kann.](/uwp/api/windows.graphics.holographic.holographicframe)

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

Jede SpatialInteractionSource verfügt über eine ID, mit der Sie neue Quellen identifizieren und vorhandene Quellen von Frame zu Frame korrelieren können.  Die Hände erhalten bei jedem Verlassen eine neue ID und geben den FOV ein. Controller-IDs bleiben jedoch für die Dauer der Sitzung statisch.  Sie können die Ereignisse auf SpatialInteractionManager wie [SourceDetected](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) und [SourceLost](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)verwenden, um zu reagieren, wenn Die Hände die Ansicht des Geräts eingeben oder verlassen, oder wenn Motion-Controller ein-/ausgeschaltet oder paariert/entkoppelt sind.

### <a name="predicted-vs-historical-poses"></a>Vorhergesagte und historische Posen
GetDetectedSourcesAtTimestamp verfügt über einen timestamp-Parameter. Auf diese Weise können Sie zustandsbezogene daten anfordern und darstellen, die entweder vorhergesagt oder verlaufsbezogene Daten darstellen, damit Sie räumliche Interaktionen mit anderen Eingabequellen korrelieren können. Wenn Sie beispielsweise die Position der Hand im aktuellen Frame rendern, können Sie den vorhergesagten Zeitstempel übergeben, der vom [HolographicFrame bereitgestellt wird.](/uwp/api/windows.graphics.holographic.holographicframe) Dadurch kann das System die Handposition vorwärts vorhersagen, um eng an der gerenderten Frameausgabe ausgerichtet zu sein, wodurch die wahrgenommene Latenz minimiert wird.

Eine solche vorhergesagte Pose erzeugt jedoch keinen idealen Zeigerstrahl für die Ausrichtung mit einer Interaktionsquelle. Wenn beispielsweise eine Motion Controller-Taste gedrückt wird, kann es bis zu 20 ms dauern, bis dieses Ereignis über Bluetooth Betriebssystem übertragen wird. Wenn ein Benutzer eine Handgeste verwendet hat, kann auch einige Zeit verpasst werden, bevor das System die Geste erkennt und Ihre App diese dann abfing. Wenn Ihre App eine Zustandsänderung abruft, sind die Kopf- und Hand-Posen, die verwendet wurden, um diese Interaktion als Ziel zu verwenden, tatsächlich in der Vergangenheit passiert. Wenn Sie das Ziel verwenden, indem Sie den Zeitstempel Ihres aktuellen HolographicFrames an GetDetectedSourcesAtTimestamp übergeben, wird die Pose stattdessen an den Zielstrahl zum Zeitpunkt der Anzeige des Frames vorhergesagt, was in der Zukunft mehr als 20 ms sein kann. Diese zukünftige Darstellung  ist gut für das Rendern  der Interaktionsquelle, aber wir lösen unser Zeitproblem für die Ausrichtung auf die Interaktion, da die Zielgruppenadressierung des Benutzers in der Vergangenheit aufgetreten ist.

Glücklicherweise stellen die [Ereignisse SourcePressed,](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)[SourceReleased und [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) [SourceUpdated)](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) den Verlaufszustand für jedes Eingabeereignis zur Verfügung.  Dies schließt direkt den verlaufsbezogene Kopf und hand-Posen ein, die über [TryGetPointerPose verfügbar](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)sind, sowie einen verlaufsbezogene Zeitstempel, den Sie an andere APIs übergeben können, um mit diesem Ereignis zu korrelieren. [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp)

Dies führt zu den folgenden bewährten Methoden beim Rendern und Anadressieren mit Händen und Controllern in jedem Frame:
* Für **das Rendern der** einzelnen  Frames durch  Hand/Controller sollte Ihre App die vorhergesagte Pose jeder Interaktionsquelle zur Photonenzeit des aktuellen Frames absehen.  Sie können alle Interaktionsquellen durch Aufrufen [von GetDetectedSourcesAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) für jeden Frame abrufen und dabei den vorhergesagten Zeitstempel übergeben, der von [HolographicFrame::CurrentPrediction bereitgestellt wird.](/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)
* Für **Hand/Controller,** die auf eine Veröffentlichung oder eine Veröffentlichung abzielen, sollte  Ihre App gedrückte/freigegebene Ereignisse **verarbeiten,** raycasting basierend auf dem verlaufsbasierten Kopf oder der Handpose für dieses Ereignis. Sie erhalten diesen Zielstrahl, indem Sie das [SourcePressed-](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) oder [SourceReleased-Ereignis](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) behandeln, die [State-Eigenschaft](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) aus den Ereignisargumenten abrufen und dann die [TryGetPointerPose-Methode](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) aufrufen.

## <a name="cross-device-input-properties"></a>Geräteübergreifende Eingabeeigenschaften
Die SpatialInteractionSource-API unterstützt Controller und Handverfolgungssysteme mit einer Vielzahl von Funktionen. Eine Reihe dieser Funktionen ist für Gerätetypen üblich. Beispielsweise stellen Handtracking- und Motion-Controller sowohl eine Select-Aktion als auch eine 3D-Position zur Verfügung. Nach Möglichkeit ordnet die API diese allgemeinen Funktionen denselben Eigenschaften in SpatialInteractionSource zu.  Dadurch können Anwendungen eine Vielzahl von Eingabetypen einfacher unterstützen. In der folgenden Tabelle werden die unterstützten Eigenschaften und deren Vergleich zwischen Eingabetypen beschrieben.

| Eigenschaft | Beschreibung | HoloLens(1. Generation) Gesten | Motion-Controller | Artikulierte Hände|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**Handgabe**](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Rechte oder linke Hand/Controller. | Nicht unterstützt | Unterstützt | Unterstützt |
| [SpatialInteractionSourceState::**IsSelectPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Aktueller Status der primären Schaltfläche. | Tippen in die Luft | Trigger | Gelockerter Tippen in die Luft (upright pinch) |
| [SpatialInteractionSourceState::**IsGrasped**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Aktueller Zustand der Greifschaltfläche. | Nicht unterstützt | Schaltfläche "Greifen" | Pinch oder Closed Hand |
| [SpatialInteractionSourceState::**IsMenuPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Aktueller Status der Menüschaltfläche.    | Nicht unterstützt | Menüschaltfläche | Nicht unterstützt |
| [SpatialInteractionSourceLocation::**Position**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | XYZ-Position der Hand- oder Greifposition auf dem Controller. | Handfläche | Position der Greifposition | Handfläche |
| [SpatialInteractionSourceLocation::**Orientation**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Quaternion, die die Ausrichtung der Hand- oder Greifpose auf dem Controller darstellt. | Nicht unterstützt | Ausrichtung der Greifpose | Handflächenausrichtung |
| [SpatialPointerInteractionSourcePose::**Position**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Ursprung des zeigenden Strahls. | Nicht unterstützt | Unterstützt | Unterstützt |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Richtung des zeigenden Strahls. | Nicht unterstützt | Unterstützt | Unterstützt |

Einige der oben genannten Eigenschaften sind nicht auf allen Geräten verfügbar, und die API bietet eine Möglichkeit, dies zu testen. Beispielsweise können Sie die [SpatialInteractionSource::IsGraspSupported-Eigenschaft](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) überprüfen, um zu bestimmen, ob die Quelle eine Greifaktion bietet.

### <a name="grip-pose-vs-pointing-pose"></a>Greifpose im Vergleich zu zeigenden Posen

Windows Mixed Reality unterstützt Bewegungscontroller in verschiedenen Formfaktoren.  Außerdem werden artikulierte Handverfolgungssysteme unterstützt.  Alle diese Systeme haben unterschiedliche Beziehungen zwischen der Handposition und der natürlichen "Vorwärtsrichtung", die Apps zum Zeigen oder Rendern von Objekten in der Hand des Benutzers verwenden sollten.  Um all dies zu unterstützen, werden zwei Arten von 3D-Posen für Handtracking und Motion-Controller bereitgestellt.  Die erste ist Greifposition, die die Handposition des Benutzers darstellt.  Die zweite ist die Zeigerpose, die einen zeigenden Strahl darstellt, der von der Hand oder dem Controller des Benutzers stammt. Wenn Sie also die  Hand des Benutzers oder ein **Objekt rendern** möchten, das sich in der Hand des Benutzers (z. B. ein Greif oder eine Greifschlange) halten soll, verwenden Sie die Greifpose. Wenn Sie einen Raycast über den Controller oder die Hand verwenden möchten, z. B. wenn der Benutzer auf die Benutzeroberfläche zeigt, verwenden Sie die zeigende Pose.

Sie können auf die **Greifpose** über [SpatialInteractionSourceState::P roperties::TryGetLocation(...) zugreifen.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_) Sie ist wie folgt definiert:
* Die **Greifposition:** Der Handflächenschwerpunkt, wenn der Controller natürlich hält, nach links oder rechts angepasst, um die Position innerhalb des Greifs zu zentriert.
* Die **rechte** Achse der Greifausrichtung: Wenn Sie Ihre Hand vollständig öffnen, um eine flache 5-Finger-Pose zu bilden, den Strahl, der normal zu Ihrer Handfläche ist (vorwärts von der linken Handfläche, rückwärts von der rechten Handfläche).
* Die **Vorwärtsachse** der Greifausrichtung: Wenn Sie die Hand teilweise schließen (als ob Sie den Controller halten), wird der Strahl, der "vorwärts" durch die Achse zeigt, die von Ihren Fingern ohne Daumen gebildet wird.
* Die **Nach-oben-Achse** der Greifausrichtung: Die up-Achse, die durch die Definitionen "Right" und "Forward" impliziert wird.

Sie können  auf die Zeigerpose über [SpatialInteractionSourceState::P roperties::TryGetLocation(...)::SourcePointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) oder [SpatialInteractionSourceState::TryGetPointerPose(...)::TryGetInteractionSourcePose zugreifen.](/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)

## <a name="controller-specific-input-properties"></a>Controllerspezifische Eingabeeigenschaften
Für Controller verfügt SpatialInteractionSource über eine Controller-Eigenschaft mit zusätzlichen Funktionen.
* **HasThumbstick:** True gibt an, dass der Controller über einen Thumbstick verfügt. Überprüfen Sie [die ControllerProperties-Eigenschaft](/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) von SpatialInteractionSourceState, um die Werte für thumbstick x und y (ThumbstickX und ThumbstickY) sowie den gedrückten Zustand (IsThumbstickPressed) zu erhalten.
* **HasTouchpad:** True gibt an, dass der Controller über ein Touchpad verfügt. Überprüfen Sie die ControllerProperties-Eigenschaft von SpatialInteractionSourceState, um die x- und y-Werte des Touchpads (TouchpadX und TouchpadY) zu erhalten und zu überprüfen, ob der Benutzer das Pad berührt (IsTouchpadTouched) und ob er das Touchpad nach unten drückt (IsTouchpadPressed).
* **SimpleHapticsController:** Mit der SimpleHapticsController-API für den Controller können Sie die Funktionen des Controllers untersuchen und das feedback-Steuerelement steuern.

Der Bereich für Touchpad und Fingerabdruck ist -1 bis 1 für beide Achsen (von unten nach oben und von links nach rechts). Der Bereich für den analogen Trigger, auf den mithilfe der SpatialInteractionSourceState::SelectPressedValue-Eigenschaft zugegriffen wird, hat einen Bereich von 0 bis 1. Der Wert 1 korreliert damit, dass IsSelectPressed gleich TRUE ist. Jeder andere Wert korreliert damit, dass IsSelectPressed gleich FALSE ist.

## <a name="articulated-hand-tracking"></a>Artikulierte Handverfolgung
Die Windows Mixed Reality-API bietet vollständige Unterstützung für die artikulierte Handverfolgung, z. B. HoloLens 2. Die artikulierte Handverfolgung kann verwendet werden, um direkte Manipulations- und Point-and-Commit-Eingabemodelle in Ihren Anwendungen zu implementieren. Sie kann auch verwendet werden, um vollständig benutzerdefinierte Interaktionen zu erstellen.

### <a name="hand-skeleton"></a>Handgerüst
Die artikulierte Handverfolgung bietet ein 25-gerüstiertes Gerüst, das viele verschiedene Arten von Interaktionen ermöglicht.  Das Gerüst stellt fünf Fugen für index/middle/ring/little fingers, vier Fugen für den Daumen und ein Handgelenk zur Hand.  Das Handgelenk ist die Basis der Hierarchie. Die folgende Abbildung veranschaulicht das Layout des Gerüsts.

![Handgerüst](images/hand-skeleton.png)

In den meisten Fällen wird jedes Fugen basierend auf der Ungnung benannt, die es darstellt.  Da es an jedem Gemeinsamen zwei Gelenke gibt, verwenden wir eine Konvention zum Benennen jedes Fugens basierend auf dem untergeordneten Tier an diesem Ort.  Die untergeordnete 100-00-000-30-000-30-000-30-00  Beispielsweise enthält das "Index Proximal"-Joint die Anfangsposition des Indexproximals und die Ausrichtung dieser Kapselung.  Er enthält nicht die Endposition des 500-00-00-00-00-00-00-0  Wenn Sie dies benötigen, erhalten Sie es vom nächsten Gemeinsamen in der Hierarchie, dem "Index Intermediate"-Joint.

Zusätzlich zu den 25 hierarchischen Fugen stellt das System ein Handflächen-Fugen zur Hand.  Die Handfläche wird in der Regel nicht als Teil der Skeletalstruktur betrachtet. Sie wird nur als bequeme Möglichkeit bereitgestellt, um die Allgemeine Position und Ausrichtung der Hand zu erhalten.

Für jedes Gemeinsame werden die folgenden Informationen bereitgestellt:

| Name | Beschreibung |
|--- |--- |
|Position | 3D-Position des Fugens, verfügbar in jedem angeforderten Koordinatensystem. |
|Orientation | 3D-Ausrichtung des Ungns, verfügbar in jedem angeforderten Koordinatensystem. |
|Radius | Abstand zur Oberfläche der Skin an der Position des Fugens. Nützlich für die Optimierung direkter Interaktionen oder Visualisierungen, die auf der Fingerbreite basieren. |
|Genauigkeit | Gibt einen Hinweis darauf an, wie sicher das System über die Informationen dieses Joints ist. |

Sie können auf die Handgerüstdaten über eine Funktion in [SpatialInteractionSourceState zugreifen.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)  Die Funktion heißt [TryGetHandPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)und gibt ein Objekt mit dem Namen [HandPose zurück.](/uwp/api/windows.perception.people.handpose)  Wenn die Quelle keine artikulierten Hände unterstützt, gibt diese Funktion NULL zurück.  Sobald Sie über ein HandPose verfügen, können Sie aktuelle gemeinsame Daten erhalten, indem Sie [TryGetJoint](/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)mit dem Namen des für Sie interessierenden Joints aufrufen.  Die Daten werden als [JointPose-Struktur](/uwp/api/windows.perception.people.jointpose) zurückgegeben.  Der folgende Code ruft die Position der Zeigefingerspitze ab. Die Variable *currentState stellt* eine Instanz von [SpatialInteractionSourceState dar.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>Handgitternetz

Die artikulierte Handverfolgungs-API ermöglicht ein vollständig verformbares Dreieckshandgitter.  Dieses Gittermodell kann sich zusammen mit dem Handgerüst in Echtzeit verformn und ist nützlich für visualisierungs- und erweiterte physikalische Techniken.  Für den Zugriff auf das Handgittermodell müssen Sie zunächst ein [HandMeshObserver-Objekt](/uwp/api/windows.perception.people.handmeshobserver) erstellen, indem Sie [TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) für [SpatialInteractionSource aufrufen.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)  Dies muss nur einmal pro Quelle erfolgen, in der Regel beim ersten Sehen.  Das bedeutet, dass Sie diese Funktion aufrufen, um ein HandMeshObserver-Objekt zu erstellen, wenn eine Hand in den FOV eintritt.  Dies ist eine asynchrone Funktion, daher müssen Sie hier mit ein wenig Parallelität umgehen.  Sobald verfügbar, können Sie das HandMeshObserver-Objekt nach dem Dreiecksindexpuffer fragen, indem Sie [GetTringleIndices aufrufen.](/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)  Indizes ändern frame over frame nicht, sodass Sie diese einmal erhalten und für die Lebensdauer der Quelle zwischenspeichern können.  Indizes werden in der Wickelrichtung im Uhrzeigersinn bereitgestellt.

Der folgende Code löst einen getrennten std::thread aus, um den Gitternetzbeobachter zu erstellen, und extrahiert den Indexpuffer, sobald der Gitternetzbeobachter verfügbar ist.  Sie beginnt mit einer Variablen namens *currentState,* bei der es sich um eine Instanz von [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) handelt, die eine nachverfolgte Hand darstellt.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
Das Starten eines getrennten Threads ist nur eine Option für die Verarbeitung asynchroner Aufrufe.  Alternativ können Sie die neue Funktionalität verwenden, [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) C++/WinRT unterstützt wird.

Sobald Sie über ein HandMeshObserver-Objekt verfügen, sollten Sie es für die Dauer halten, in der die entsprechende SpatialInteractionSource aktiv ist.  Anschließend können Sie jeden Frame nach dem neuesten Scheitelpunktpuffer fragen, der die Hand darstellt, indem Sie [GetVertexStateForPose](/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) aufrufen und eine [HandPose-Instanz](/uwp/api/windows.perception.people.handpose) übergeben, die die Pose darstellt, für die Sie Scheitelpunkte wünschen.  Jeder Scheitelpunkt im Puffer hat eine Position und eine Normale.  Hier ist ein Beispiel dafür, wie Sie den aktuellen Satz von Scheiteltices für ein Handgitternetz erhalten.  Wie zuvor stellt die *CurrentState-Variable* eine Instanz von [SpatialInteractionSourceState dar.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

Im Gegensatz zu Gerüsten lässt die Handgittermodell-API nicht zu, dass Sie ein Koordinatensystem für die Scheitelungen angeben.  Stattdessen gibt [HandMeshVertexState](/uwp/api/windows.perception.people.handmeshvertexstate) das Koordinatensystem an, in dem die Scheitelungen bereitgestellt werden.  Sie können dann eine Gitternetztransformation abrufen, indem [Sie TryGetTransformTo](/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) aufrufen und das gewünschte Koordinatensystem angeben.  Sie müssen diese Meshtransformation immer dann verwenden, wenn Sie mit den Scheitelpunkten arbeiten.  Dieser Ansatz reduziert den CPU-Mehraufwand, insbesondere, wenn Sie das Gitternetz nur für Renderingzwecke verwenden.

## <a name="gaze-and-commit-composite-gestures"></a>Kombinierte Gesten anv und Commits
Für Anwendungen, die das Eingabemodell "Anvieren und Committen" verwenden, insbesondere für HoloLens (erste Generation), stellt die API für räumliche Eingaben eine optionale [SpatialGestureRecognizer-Klasse](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) bereit, mit der zusammengesetzte Gesten aktiviert werden können, die auf dem Select-Ereignis aufbauen.  Durch das Weiterleiten von Interaktionen vom SpatialInteractionManager an spatialGestureRecognizer eines Hologramms können Apps Tap-, Hold-, Manipulations- und Navigationsereignisse gleichmäßig über Hände-, Sprach- und räumliche Eingabegeräte hinweg erkennen, ohne dass Pressen und Releases manuell behandelt werden müssen.

SpatialGestureRecognizer führt nur die minimale Mehrdeutigkeit zwischen den angeforderten Gesten aus. Wenn Sie z. B. nur Tippen anfordern, kann der Benutzer den Finger gedrückt halten, solange er möchte, und es wird weiterhin ein Tippen ausgeführt. Wenn Sie sowohl Tippen als auch Halten anfordern, wird die Geste nach etwa einer Sekunde nach dem Halten des Fingers zu einer Hold-Geste heraufgestuft, und ein Tippen tritt nicht mehr auf.

Um SpatialGestureRecognizer zu verwenden, behandeln Sie das [InteractionDetected-Ereignis](/uwp/api/Windows.UI.Input.Spatial.SpatialInteractionManager) von SpatialInteractionManager, und greifen Sie das dort verfügbar gemachte SpatialPointerPose-Objekt. Verwenden Sie den Anviert-Strahl des Benutzers aus dieser Pose, um sich mit den Hologrammen und Oberflächengittern in der Umgebung des Benutzers zu überschneiden, um zu bestimmen, mit welchem Benutzer die Interaktion erfolgen soll. Leiten Sie dann die SpatialInteraction in den Ereignisargumenten mithilfe der [CaptureInteraction-Methode](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) an spatialGestureRecognizer des Ziel hologramms weiter. Dies beginnt mit der Interpretation dieser Interaktion gemäß den [SpatialGestureSettings,](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureSettings) die bei der Erstellung für diese Erkennung festgelegt wurden – oder nach [TrySetGestureSettings.](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer)

Bei HoloLens (erste Generation) sollten Interaktionen und Gesten ihre Zielgruppenadressierung vom Anvisieren mit dem Kopf des Benutzers ableiten, anstatt an der Position der Hand zu rendern oder zu interagieren. Sobald eine Interaktion gestartet wurde, können relative Bewegungen der Hand verwendet werden, um die Geste zu steuern, wie bei der Bearbeitungs- oder Navigationsgeste.

## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Eingabemodell für direkte Bearbeitung](../../design/direct-manipulation.md)
* [Point-and-Commit-Eingabemodell](../../design/point-and-commit.md)
* [Eingabemodell "Anvieren und Committen"](../../design/gaze-and-commit.md)
* [Motion-Controller](../../design/motion-controllers.md)