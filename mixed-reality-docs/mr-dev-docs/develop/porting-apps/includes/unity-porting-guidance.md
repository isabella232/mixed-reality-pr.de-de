---
ms.openlocfilehash: e7f298b9d587df2243601670e187c109bb674a278deb67862b517568ca5198d7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213513"
---
# <a name="project-settings"></a>[Projekteinstellungen](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. Sehen Sie sich die oben aufgeführten allgemeinen Portierungsschritte an.

Überprüfen Sie die oben aufgeführten allgemeinen Schritte, um sicherzustellen, dass Ihre Entwicklungsumgebung ordnungsgemäß eingerichtet ist. Wenn Sie #3 Verwenden von Visual Studio sie die Workload Game **Development with Unity (Spieleentwicklung mit Unity)** aus. Sie können die Komponente "Unity-Editor optional" deaktivieren, da Sie im nächsten Schritt eine neuere Version von Unity installieren.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. Upgrade auf den neuesten öffentlichen Build von Unity mit Windows MR-Unterstützung
1. Laden Sie den neuesten [empfohlenen öffentlichen Build von Unity mit](../../install-the-tools.md) Mixed Reality-Unterstützung herunter.
2. Speichern Sie eine Kopie Ihres Projekts, bevor Sie beginnen.
3. Sehen Sie sich [die von](https://docs.unity3d.com/Manual/UpgradeGuides.html) Unity verfügbare Dokumentation zum Upgrade an, wenn Ihr Projekt auf einer älteren Version von Unity basiert.
4. Befolgen Sie [die Anweisungen](https://docs.unity3d.com/Manual/APIUpdater.html) auf der Unity-Website für die Verwendung des automatischen API-Updates.
5. Überprüfen Sie, ob zusätzliche Änderungen vorgenommen werden müssen, damit Ihr Projekt ausgeführt wird, und beheben Sie alle verbleibenden Fehler und Warnungen. 

> [!Note] 
> Wenn Sie über Middleware verfügen, von der Sie abhängig sind, überprüfen Sie, ob Sie das neueste Release verwenden (weitere Details finden Sie weiter unten in Schritt 3).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. Aktualisieren Ihrer Middleware auf die neuesten Versionen

Bei jedem Unity-Update besteht die Wahrscheinlichkeit, dass Sie mindestens ein Middlewarepaket aktualisieren müssen, von dem Ihr Spiel oder Ihre Anwendung abhängt. Darüber hinaus erhöht sich die Wahrscheinlichkeit, dass der Portierungsprozess während des restlichen Portierungsprozesses erfolgreich ist, wenn Sie mit der neuesten Middleware auf dem neuesten Stand sind.

### <a name="4-target-your-application-to-run-on-win32"></a>4. Ziel ihrer Anwendung für die Ausführung unter Win32

In Ihrer Unity-Anwendung:

* Navigieren Sie zu Datei -> Build Einstellungen
* Wählen Sie "PC, Mac, Linux Standalone" aus.
* Festlegen der Zielplattform auf "Windows"
* Legen Sie die Architektur auf "x86" fest. Wählen Sie "Plattform wechseln" aus.

> [!NOTE] 
> Wenn Ihre Anwendung Abhängigkeiten von gerätespezifischen Diensten aufweist, z. B. match making from Steam, müssen Sie diese in diesem Schritt deaktivieren. Sie können die entsprechenden Dienste, die später von Windows werden, mit anderen diensten.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. Einrichten ihrer Windows Mixed Reality Hardware
1. Lesen Sie die Schritte unter [Einrichten des immersiven Headsets.](/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Erfahren Sie [mehr über das Verwenden Windows Mixed Reality Simulators](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) und navigieren im Windows Mixed Reality [Start.](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. Ziel ihrer Anwendung für die Ausführung auf Windows Mixed Reality
1. Zunächst müssen Sie jede andere Bibliotheksunterstützung, die für ein bestimmtes VR SDK spezifisch ist, entfernen oder bedingt kompilieren. Diese Ressourcen ändern Einstellungen und Eigenschaften in Ihrem Projekt häufig auf eine Weise, die mit anderen VR SDKs nicht kompatibel ist, z. B. Windows Mixed Reality.
    * Wenn Ihr Projekt beispielsweise auf das SteamVR SDK verweist, müssen Sie Ihr Projekt aktualisieren, um stattdessen die gängigen VR-APIs von Unity zu verwenden, die sowohl Windows Mixed Reality als auchVrvr unterstützen.
    * Bestimmte Schritte zum bedingten Ausschließen anderer VR SDKs sind in Kürze verfügbar.
2. Verwenden Sie in Ihrem [Unity-Projekt das Windows 10 SDK.](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. Richten Sie für jede Szene [die Kamera ein.](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. Verwenden der Stufe zum Platzieren von Inhalten auf dem Boden

Sie können eine Mixed Reality für eine Vielzahl von [Benutzererfahrungsskalieren erstellen.](../../../design/coordinate-systems.md)

Wenn Sie eine besenskalierte Beschriftung **portieren,** müssen Sie sicherstellen, dass Unity auf den Typ des **ortsfestgelegten** Nachverfolgungsraums festgelegt ist:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Mit diesem obigen Code wird das Weltkoordinatensystem von Unity so definiert, dass der [fest stehende Bezugsrahmen nachverfolgt wird.](../../../design/coordinate-systems.md#spatial-coordinate-systems) Im Nachverfolgungsmodus "Stationär" werden Inhalte, die im Editor direkt vor der Standardposition der Kamera platziert werden (vorwärts ist -Z), vor dem Benutzer angezeigt, wenn die App gestartet wird. Sie können unitys XR aufrufen, um den Ursprung des Benutzers zu einem neueren [Tag zu erhalten. InputTracking.Recenter-Methode.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

Wenn Sie eine Begeh- oder Raumerfahrung portieren, platzieren Sie Inhalte relativ zum Boden.   Sie können den Grund für **[](../../../design/coordinate-systems.md#spatial-coordinate-systems)** den Boden des Benutzers mithilfe der räumlichen Stufe festlegen, die den vom Benutzer definierten Ursprung auf Bodenebene und die optionale Raumgrenze darstellt, die während der ersten Ausführung eingerichtet wurde. Für diese Erfahrungen müssen Sie sicherstellen, dass Unity auf den **Raumtyp RoomScale tracking** festgelegt ist. Obwohl RoomScale die Standardeinstellung ist, sollten Sie sie explizit festlegen und sicherstellen, dass Sie "true" erhalten, um Situationen zu fangen, in denen der Benutzer seinen Computer aus dem Raum entfernt hat, in dem er kalibriert hat:

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

Nachdem Ihre App den Raumtyp RoomScale-Nachverfolgung erfolgreich gesetzt hat, werden Inhalte auf der Ebene y=0 im Boden angezeigt. Der Ursprung bei (0, 0, 0) ist der spezifische Ort im Boden, an dem der Benutzer während der Einrichtung des Raums mit -Z die Vorwärtsrichtung darstellt, die er während des Setups hatte.

Im Skriptcode können Sie dann die TryGetGeometry-Methode für Den UnityEngine.Experimental.XR.Boundary-Typ aufrufen, um ein Begrenzungspolygon zu erhalten, und dabei den Begrenzungstyp TrackedArea angeben. Wenn der Benutzer eine Grenze definiert hat (Sie erhalten eine Liste von  Scheitellinien), ist es sicher, dem Benutzer eine Raumerfahrung zu bieten, in der er die von Ihnen erstellten Szenen durchläuft.

Das System rendert die Grenze automatisch, wenn sich der Benutzer ihr nähert. Ihre App muss dieses Polygon nicht verwenden, um die Grenze selbst zu rendern.

Weitere Informationen finden Sie auf der Seite [Koordinatensysteme in Unity.](../../unity/coordinate-systems-in-unity.md)

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

Beispiel für Ergebnisse:

![Beispiel für Ergebnisse](../../porting-apps/images/largestrectangle-400px.jpg)

Der Algorithmus basiert auf einem Blog von Daniel Smilmilmil: [Größtes Rechteck in einem Polygon](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. Arbeiten Sie Ihr Eingabemodell durch.

Jedes Spiel oder jede Anwendung, die auf ein vorhandenes HMD abzielen, hat eine Reihe von Eingaben, die es verarbeitet, Eingabetypen, die es für die Erfahrung benötigt, und bestimmte APIs, die zum Erhalten dieser Eingaben aufruft. Wir haben in den Versuch investiert, es so einfach und einfach wie möglich zu gestalten, um die in der Lösung verfügbaren Eingaben Windows Mixed Reality.

Lesen Sie den [Eingabeportierungsleitfaden](../porting-guides.md?tabs=input) für Unity auf der angrenzenden Registerkarte, um zu erfahren, wie Windows Mixed Reality Eingaben verfügbar macht und wie dies den heutigen Anforderungen Ihrer Anwendung zu entnehmen ist.

### <a name="9-performance-testing-and-tuning"></a>9. Leistungstests und -optimierung

Windows Mixed Reality werden auf einer breiten Palette von Geräten verfügbar sein, von High-End-Gaming-PCs bis hin zu gängigen Markt-PCs. Je nachdem, auf welchen Markt Sie abzielen, gibt es einen erheblichen Unterschied in den verfügbaren Compute- und Grafikbudgets für Ihre Anwendung. Während dieser Portierungsübung nutzen Sie wahrscheinlich einen Premium-PC und haben erhebliche Compute- und Grafikbudgets für Ihre App zur Verfügung gestellt. Wenn Sie Ihre App einer größeren Zielgruppe zur Verfügung stellen möchten, sollten Sie Ihre App auf der repräsentativen Hardware testen und profilieren, die [Sie als Ziel verwenden möchten.](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)

[Sowohl Unity](https://docs.unity3d.com/Manual/Profiler.html) als [auch Visual Studio](/visualstudio/profiling/index) enthalten Leistungsprofiler sowie [Microsoft-](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) und Intel-Veröffentlichungsrichtlinien zur Leistungsprofilerstellung und -optimierung. [](https://software.intel.com/articles/vr-content-developer-guide) Eine ausführliche Erörterung der Leistung finden Sie unter Grundlegendes zur [Leistung für Mixed Reality.](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) Darüber hinaus finden Sie unter Performance Empfehlungen for Unity (Leistungs-Empfehlungen [für Unity) spezifische Details zu Unity.](../../unity/performance-recommendations-for-unity.md)

# <a name="input-mapping"></a>[Eingabezuordnung](#tab/input)

Sie können Ihre Eingabelogik portieren, um Windows Mixed Reality zu verwenden, indem Sie einen von zwei Ansätzen verwenden: die allgemeinen Input.GetButton/GetAxis-APIs von Unity, die sich über mehrere Plattformen erstrecken, oder die Windows-spezifische XR. WSA. Eingabe-APIs, die umfangreiche Daten speziell für Motion Controller und HoloLens bieten.

> [!IMPORTANT]
> Wenn Sie HP Reverb G2-Controller verwenden, finden Sie in diesem Artikel [weitere](../../unity/unity-reverb-g2-controllers.md) Anweisungen zur Eingabezuordnung.

## <a name="unity-xr-input-apis"></a>Unity XR-Eingabe-APIs

Für neue Projekte wird empfohlen, die neuen XR-Eingabe-APIs von Anfang an zu verwenden. 

Weitere Informationen zu den [XR-APIs finden Sie hier.](https://docs.unity3d.com/Manual/xr_input.html)

## <a name="inputgetbuttongetaxis-apis"></a>Input.GetButton/GetAxis-APIs

Unity verwendet derzeit seine allgemeinen Input.GetButton/Input.GetAxis-APIs, um Eingaben für das [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) und das [OpenVR SDK verfügbar zu machen.](https://docs.unity3d.com/Manual/OpenVRControllers.html) Wenn Ihre Apps diese APIs bereits für die Eingabe verwenden, ist dies der einfachste Weg zur Unterstützung von Motion Controllern in Windows Mixed Reality: Sie müssen nur Schaltflächen und Achsen im Eingabe-Manager neu zuzuordnungen.

Weitere Informationen finden Sie in der [Unity-Schaltflächen-/Achsenzuordnungstabelle](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) und in der Übersicht [über die allgemeinen Unity-APIs.](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)

## <a name="windows-specific-xrwsainput-apis"></a>Windows XR-spezifische xr. WSA. Eingabe-APIs

> [!CAUTION]
> Wenn Ihr Projekt eine der XR-Daten verwendet. WSA-APIs werden in zukünftigen Unity-Releases zugunsten des XR SDK aus der Veröffentlichungsphase entfernt. Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden. Weitere Informationen zum XR-Eingabesystem und zu [den APIs finden Sie hier.](https://docs.unity3d.com/Manual/xr_input.html)

Wenn Ihre App bereits benutzerdefinierte Eingabelogik für jede Plattform erstellt, können Sie die Windows-spezifischen APIs für räumliche Eingaben unter dem **UnityEngine.XR.WSA.Input-Namespace** verwenden. Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, z. B. die Position oder die Quellart, damit Sie Hände und Controller bei der HoloLens.

> [!NOTE]
> Wenn Sie HP Reverb G2-Controller verwenden, funktionieren alle Eingabe-APIs weiterhin, mit Ausnahme von **InteractionSource.supportsTouchpad,** das false ohne Touchpaddaten zurück gibt.

Weitere Informationen finden Sie in der [Übersicht über die UnityEngine.XR.WSA.Input-APIs.](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)

## <a name="grip-pose-vs-pointing-pose"></a>Greifpose im Vergleich zu zeigenden Posen

Windows Mixed Reality unterstützt Bewegungscontroller in einer Vielzahl von Formfaktoren, bei denen sich das Design jedes Controllers in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen "Vorwärtsrichtung", die Apps zum Zeigen beim Rendern des Controllers verwenden sollten, unterscheiden.

Um diese Controller besser darstellen zu können, gibt es zwei Arten von Posen, die Sie für jede Interaktionsquelle untersuchen können:

* Der **Greifhaltung,** die die Position der Handfläche darstellt, die von einer Hand erkannt HoloLens oder der Handfläche, die einen Bewegungscontroller hält.
    * Bei immersiven Headsets wird diese  Pose am besten verwendet, um die Hand des Benutzers oder ein **Objekt in** der Hand des Benutzers zu rendern, z. B. eine Brille oder eine Brille.
    * Die **Greifposition:** Der Handflächenschwerpunkt, wenn der Controller natürlich hält, nach links oder rechts angepasst, um die Position innerhalb des Greifs zu zentriert.
    * Die **rechte** Achse der Greifausrichtung: Wenn Sie Ihre Hand vollständig öffnen, um eine flache 5-Finger-Pose zu bilden, den Strahl, der normal zu Ihrer Handfläche ist (vorwärts von der linken Handfläche, rückwärts von der rechten Handfläche).
    * Die **Vorwärtsachse** der Greifausrichtung: Wenn Sie die Hand teilweise schließen (als ob Sie den Controller halten), wird der Strahl, der "vorwärts" durch die Achse zeigt, die von Ihren Fingern ohne Daumen gebildet wird.
    * Die **Nach-oben-Achse** der Greifausrichtung: Die up-Achse, die durch die Definitionen "Right" und "Forward" impliziert wird.
    * Sie können über die anbieterübergreifende Eingabe-API **(XR) von Unity auf die Greifpose [zugreifen. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) oder über die Windows-spezifische API (**sourceState.sourcePose.TryGetPosition/Rotation**, anfordern der Greifposition).
* Der **Zeiger stellt die Spitze** des Controllers darstellt, der nach vorn zeigen soll.
    * Diese Darstellung wird am besten für Raycast verwendet, wenn Sie auf die **Benutzeroberfläche zeigen,** wenn Sie das Controllermodell selbst rendern.
    * Derzeit ist die Zeigerposition nur über die Windows-spezifische API verfügbar (**sourceState.sourcePose.TryGetPosition/Rotation**, anfordern der Zeigerposition).

Diese Posenkoordinaten werden alle in Unity-Weltkoordinaten ausgedrückt.