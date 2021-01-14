---
ms.openlocfilehash: 0ef22142ac2efc3ef47ece2619d31dbeddcff8fe
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192662"
---
# <a name="project-settings"></a>[Projekteinstellungen](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. Überprüfen Sie die oben aufgeführten allgemeinen Schritte zum Portieren.

Überprüfen Sie die oben aufgeführten allgemeinen Schritte, um sicherzustellen, dass Ihre Entwicklungsumgebung ordnungsgemäß eingerichtet ist. Wenn Sie in Schritt #3 Visual Studio verwenden, sollten Sie die Arbeitsauslastung " **Spieleentwicklung mit Unity** " auswählen. Wenn Sie im nächsten Schritt eine neuere Version von Unity installieren, deaktivieren Sie ggf. die Auswahl der optionalen Unity-Editor-Komponente.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. Upgrade auf den neuesten öffentlichen Build von Unity mit Windows Mr-Unterstützung
1. Laden Sie den neuesten [empfohlenen öffentlichen Build von Unity](../../install-the-tools.md) mit gemischter Reality-Unterstützung herunter.
2. Speichern Sie eine Kopie des Projekts, bevor Sie loslegen.
3. Überprüfen Sie die in Unity verfügbare [Dokumentation](https://docs.unity3d.com/Manual/UpgradeGuides.html) beim Upgrade, wenn Ihr Projekt auf einer älteren Version von Unity basiert.
4. Befolgen Sie die [Anweisungen](https://docs.unity3d.com/Manual/APIUpdater.html) auf der Website von Unity, um Ihren automatischen API-Updater zu verwenden.
5. Überprüfen Sie, ob weitere Änderungen vorhanden sind, die Sie vornehmen müssen, um das Projekt ausführen zu können, und arbeiten Sie mit allen verbleibenden Fehlern und Warnungen. 

> [!Note] 
> Wenn Sie über eine Middleware verfügen, von der Sie abhängig sind, überprüfen Sie, ob Sie die neueste Version verwenden (Weitere Informationen finden Sie unten in Schritt 3).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. aktualisieren Sie Ihre Middleware auf die neuesten Versionen.

Bei jedem Unity-Update besteht eine gute Chance, dass Sie ein oder mehrere Middlewarepakete aktualisieren müssen, von denen Ihr Spiel oder Ihre Anwendung abhängig ist. Außerdem erhöht sich die Wahrscheinlichkeit, dass Sie im gesamten Rest des Portierungs Prozesses Erfolg haben, auf dem neuesten Stand der aktuellen Middleware.

### <a name="4-target-your-application-to-run-on-win32"></a>4. Ziel Ihrer Anwendung für die Verwendung mit Win32

In ihrer Unity-Anwendung:

* Navigieren Sie zu Datei-> Buildeinstellungen.
* Wählen Sie "PC, Mac, eigenständiges Linux" aus.
* Legen Sie die Zielplattform auf "Windows" fest.
* Legen Sie Architektur auf "x86" Select "Switch Platform" fest.

> [!NOTE] 
> Wenn Ihre Anwendung Abhängigkeiten von gerätespezifischen Diensten aufweist (z. b. die Abgleich von "Stream"), müssen Sie Sie in diesem Schritt deaktivieren. Sie können die entsprechenden Dienste einrichten, die von Windows später bereitstellt werden.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. Einrichten der Windows Mixed Reality-Hardware
1. Überprüfen der Schritte in der [immersiven Headset-Einrichtung](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Erfahren Sie mehr über [die Verwendung des Windows Mixed Reality-Simulators](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) und [Navigieren in Windows Mixed Reality Home](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. Ziel Ihrer Anwendung für die unter Windows Mixed Reality
1. Zunächst müssen Sie alle anderen Bibliotheks Unterstützung für ein bestimmtes VR-SDK entfernen oder bedingt kompilieren. Diese Assets ändern häufig Einstellungen und Eigenschaften für Ihr Projekt in einer Weise, die nicht mit anderen VR-sDas kompatibel ist, wie z. b. Windows Mixed Reality.
    * Wenn Ihr Projekt beispielsweise auf das steamvr-SDK verweist, müssen Sie das Projekt aktualisieren, um stattdessen die allgemeinen VR-APIs von Unity zu verwenden, die sowohl Windows Mixed Reality als auch steamvr unterstützen.
    * In Kürze werden bestimmte Schritte zum bedingten ausschließen anderer VR-sdche in Kürze ausgeführt.
2. In Ihrem Unity-Projekt [das Windows 10-SDK als Ziel](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. Richten Sie [die Kamera](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera) für jede Szene ein.

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. verwenden Sie die Stufe, um Inhalte auf der Etage zu platzieren.

Sie können in einer Vielzahl von [Erfahrungs Skalen](../../../design/coordinate-systems.md)Umgebungen mit gemischter Realität entwickeln.

Wenn Sie eine Anwendung mit **sitzender Skalierung** portieren, müssen Sie sicherstellen, dass Unity auf den Typ des **stationären** nach Verfolgungs Raums festgelegt ist:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Mit dem obigen Code wird das World-Koordinatensystem von Unity festgelegt, um den [stationären Verweis Rahmen](../../../design/coordinate-systems.md#spatial-coordinate-systems)zu verfolgen. Im Modus der stationären Nachverfolgung wird der Inhalt, der direkt vor dem Standard Speicherort der Kamera (vorwärts ist-Z) im Editor eingefügt wird, vor dem Benutzer angezeigt, wenn die APP gestartet wird. Um den sitzenden Ursprung des Benutzers wieder einzugeben, können Sie den "XR"-Befehl von Unity aufzurufen [. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) -Methode.

Wenn **Sie eine vorhandene** Oberfläche oder **Raum Skalierung** portieren, werden Sie Inhalte relativ zum Boden platzieren. Sie haben eine Begründung für den Benutzer, der die **[räumliche Phase](../../../design/coordinate-systems.md#spatial-coordinate-systems)** verwendet, die den definierten Ursprung und die optionale Raumgrenze des Benutzers darstellt, die während der ersten Durchführung eingerichtet wird. Für diese Umgebungen müssen Sie sicherstellen, dass Unity auf den Typ des **roomscale** -nach Verfolgungs Raums festgelegt ist. Obwohl es sich bei der Standardeinstellung um die Standardeinstellung handelt, sollten Sie Sie explizit festlegen und sicherstellen, dass Sie den Vorgang wiederholen.

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

Nachdem Ihre APP den Typ für die Nachverfolgung von roomscale festgelegt hat, wird der Inhalt auf der Ebene "y = 0" auf der Etage angezeigt. Der Ursprung bei (0,0) ist die spezifische Stelle auf dem Boden, an der der Benutzer während des Raum Setups Stand, wobei-Z die Vorwärtsrichtung darstellt, die während des Setups aufgetreten ist.

In Skriptcode können Sie dann die trygetgeometry-Methode aufrufen, indem Sie den Typ "unityengine. experimental. XR. Boundary" verwenden, um ein Begrenzungs Polygon abzurufen und dabei den Grenztyp "trackedarea" anzugeben. Wenn der Benutzer eine Grenze definiert hat (Sie erhalten eine Liste mit Scheitel Punkten), ist es sicher, dem Benutzer eine **Raum** Umgebung bereitzustellen, in der Sie die von Ihnen erstellte Szene durchlaufen können.

Das System gibt die Grenze automatisch aus, wenn der Benutzer es nähert. Ihre APP muss dieses Polygon nicht verwenden, um die Grenze selbst zu erzeugen.

Weitere Informationen finden Sie auf der Seite [Koordinatensysteme in Unity](../../unity/coordinate-systems-in-unity.md) .

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

Beispiel für Ergebnisse:

![Beispiel für Ergebnisse](../../porting-apps/images/largestrectangle-400px.jpg)

Der Algorithmus basiert auf einem Blog von Daniel smilkow: [größten Rechteck in einem Polygon](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. arbeiten Sie mit dem Eingabe Modell

Jedes Spiel oder jede Anwendung, das auf ein vorhandenes HMD ausgerichtet ist, verfügt über eine Reihe von Eingaben, die es verarbeitet, sowie über die Typen von Eingaben, die für die Benutzer Anforderung benötigt werden Wir haben versucht, es so einfach und unkompliziert wie möglich zu gestalten, um die in Windows Mixed Reality verfügbaren Eingaben zu nutzen.

Ausführliche Informationen zur Bereitstellung von Eingaben durch Windows Mixed Reality finden Sie im [Leitfaden für die Eingabe Portierung für Unity](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input) auf der angrenzenden Registerkarte.

### <a name="9-performance-testing-and-tuning"></a>9. Leistungstests und-Optimierung

Windows Mixed Reality steht auf einer Vielzahl von Geräten zur Verfügung, die von High-End-Gaming-PCs bis hin zu großen Markt Einführungs PCs reichen. Je nachdem, welchen Markt Sie als Ziel haben, gibt es einen signifikanten Unterschied in den verfügbaren COMPUTE-und Grafik Budgets für Ihre Anwendung. Während dieser Portierungs Übung nutzen Sie wahrscheinlich einen Premium-PC und haben bedeutende COMPUTE-und Grafik Budgets für Ihre APP zur Verfügung gestellt. Wenn Sie Ihre APP für eine größere Zielgruppe verfügbar machen möchten, sollten Sie Ihre APP auf [der repräsentativen Hardware](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)testen und erstellen, die Sie als Ziel festlegen möchten.

Sowohl [Unity](https://docs.unity3d.com/Manual/Profiler.html) als auch [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) beinhalten leistungsprofilerstellungs-und sowohl [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) -als auch [Intel](https://software.intel.com/articles/vr-content-developer-guide) -Veröffentlichungs Richtlinien zur Leistungsprofil Erstellung und-Optimierung. Es gibt eine umfassende Erörterung der Leistung, um die [Leistung für gemischte Realität zu verstehen](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md). Darüber hinaus gibt es spezifische Details für Unity unter [Empfehlungen zur Leistung für Unity](../../unity/performance-recommendations-for-unity.md).

# <a name="input-mapping"></a>[Eingabezuordnung](#tab/input)

Sie können Ihre Eingabe Logik in Windows Mixed Reality portieren. verwenden Sie dazu einen von zwei Ansätzen: die allgemeinen Eingabe. getbutton/getaxis-APIs von Unity, die sich über mehrere Plattformen erstrecken, oder den Windows-spezifischen XR. WSA. Eingabe-APIs, die umfangreichere Daten speziell für Bewegungs Controller und hololens-Hände bieten.

> [!IMPORTANT]
> Wenn Sie mit HP Reverb G2-Controllern verwenden, finden Sie in [diesem Artikel](../../unity/unity-reverb-g2-controllers.md) weitere Anweisungen zur Eingabe Zuordnung.

## <a name="unity-xr-input-apis"></a>Eingabe-APIs für Unity XR

Bei neuen Projekten wird die Verwendung der neuen XR-Eingabe-APIs von Anfang an empfohlen. 

Weitere Informationen zu den [XR-APIs](https://docs.unity3d.com/Manual/xr_input.html)finden Sie hier.

## <a name="inputgetbuttongetaxis-apis"></a>Input. getbutton/getaxis-APIs

Unity verwendet derzeit die allgemeinen Input. getbutton/Input. getaxis-APIs, um Eingaben für [das Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) und [das openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)verfügbar zu machen. Wenn Ihre apps bereits diese APIs für die Eingabe verwenden, ist dies der einfachste Weg zur Unterstützung von Bewegungs Controllern in Windows Mixed Reality: Sie müssen nur Schaltflächen und Achsen im Eingabe-Manager neu zuordnen.

Weitere Informationen finden Sie in der [Unity-Schaltflächen-/Achsen-Mapping-Tabelle](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) und [in der Übersicht über die gemeinsamen Unity-APIs](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>Windows-spezifischer XR. WSA. Eingabe-APIs

> [!CAUTION]
> , Wenn Ihr Projekt einen der XR-verwendet. WSA-APIs werden nach dem XR SDK in zukünftigen Unity-Releases eingestellt. Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden. Weitere Informationen zum [XR-Eingabe System und](https://docs.unity3d.com/Manual/xr_input.html)zu den APIs finden Sie hier.

Wenn Ihre APP bereits eine benutzerdefinierte Eingabe Logik für jede Plattform erstellt hat, können Sie die Windows-spezifischen räumlichen Eingabe-APIs im Namespace **unityengine. XR. WSA. Input** verwenden. Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, wie z. b. Die Positionsgenauigkeit oder die quellart, sodass Sie die Hände und Controller auf hololens aufteilen können.

> [!NOTE]
> Wenn Sie HP-Reverb-G2-Controller verwenden, funktionieren alle Eingabe-APIs weiterhin mit Ausnahme von **Interaction Source. supportstouchpad**, das false ohne Touchpad-Daten zurückgibt.

Weitere Informationen finden Sie in der [Übersicht über die unityengine. XR. WSA. Input-APIs](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt im Vergleich zu Zeige darstellen

Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren, wobei sich der Entwurf des Controllers in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung unterscheidet, die von den apps beim Rendern des Controllers verwendet werden sollen.

Um diese Controller besser darstellen zu können, gibt es zwei Arten von Posen, die Sie für die einzelnen Interaktions Quellen untersuchen können:

* Die Zieh Punkt Darstellung, die den Speicherort der von einem hololens erkannten **Hand, oder** die Palme mit einem Bewegungs Controller darstellt.
    * Bei immersiven Headsets eignet sich diese Pose am besten zum Rendering **der Benutzer Hand** oder **eines Objekts, das in der Hand des Benutzers gehalten** wird, z. b. ein Schwert oder eine Waffe.
    * Die Zieh **Punktposition**: der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren.
    * Die **Rechte Achse** der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).
    * Die **Forward-Achse** der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.
    * Die **aufwärts Achse** der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.
    * Sie können auf die Ziehpunkt-Pose über die Anbieter übergreifende Eingabe-API von Unity (XR) zugreifen **[. Inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Getlocalposition/Rotation**) oder über die Windows-spezifische API (**SourceState. sourcepose. trygetposition/Rotation**, Anfordern der Ziehpunkt-Pose).
* Die **Zeiger** Darstellung, die die Spitze des Controllers darstellt, der vorwärts zeigt.
    * Diese Pose eignet sich am besten für raycast, wenn Sie **auf die Benutzeroberfläche zeigen** , wenn Sie das Controller Modell selbst rendern.
    * Derzeit ist die Zeiger Pose nur über die Windows-spezifische API (**SourceState. sourcepose. trygetposition/Rotation**) verfügbar, die die Zeiger Pose anfordert.

Diese posikoordinaten werden alle in Unity-Weltkoordinaten ausgedrückt.
