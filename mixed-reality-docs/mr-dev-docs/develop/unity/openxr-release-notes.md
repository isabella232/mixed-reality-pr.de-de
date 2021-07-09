---
title: Versionshinweise für das OpenXR-Plug-In für Mixed Reality
description: Bleiben Sie über die neuesten Versionshinweise und Upgrades für das OpenXR-Plug-In für Mixed Reality auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394629"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a>Versionshinweise für das OpenXR-Plug-In für Mixed Reality

## <a name="100---current-release"></a>1.0.0 – Aktuelle Version

* Ein Fehler wurde behoben, bei dem das XRAnchorSubsystem beim Starten der App immer gestartet wurde, unabhängig davon, ob ARAnchorManager vorhanden war.
* Ein Fehler wurde behoben, bei dem der Neuprojektionsmodus nicht ordnungsgemäß funktionierte.

## <a name="100-preview2---2021-06-14"></a>1.0.0-preview.2 – 2021-06-14

* Abhängig vom OpenXR 1.2.2-Plug-In von Unity.
* Holographic Remoting-Features wurden in einzelne Featuregruppen geändert.
* Ein Fehler wurde behoben, bei dem „HoloLens 2-Projekteinstellungen anwenden“ den Farbraum des Projekts geändert hat. Dies ist seit dem OpenXR 1.2.0-Plug-In von Unity nicht mehr erforderlich.
* Ein Fehler wurde behoben, bei dem ein Eingabegerät verbunden wurde, ohne die Verbindung zu trennen, nachdem die Anwendung angehalten und wieder fortgesetzt wurde.
* Unterstützung für die Erkennung von Plug-Ins und aktuellen Nachverfolgungszuständen über ARSession wurde hinzugefügt.
* Ein Fehler wurde behoben, bei dem das ARFoundation-Prefab „AR Default Plane“ (AR-Standardebene) nicht sichtbar war.

## <a name="100-preview1---2021-06-02"></a>1.0.0-preview.1 – 2021-06-02

* Unterstützt MSFT-Erweiterungen für OpenXR-Szenenverständnis anstelle von Vorschauerweiterungen.
* Die Ebenenerkennung von HoloLens 2 erfordert keine Vorschauversionen der OpenXR-Runtimes für Mixed Reality mehr.

## <a name="095---2021-05-21"></a>0.9.5 – 2021-05-21

* Abhängig vom OpenXR-Plug-In 1.2.0 von Unity
* Angepasst an die neue Featurebenutzeroberfläche (in OpenXR-Plug-In 1.2.0) für die Konfiguration.
* Ein Fehler wurde behoben, bei dem die Registrierung des Anbieters für auffindbare Kameras nicht ordnungsgemäß aufgehoben wurde.
* Einige zusätzliche Verwendungen von [Preserve] (Beibehalten) wurden bereinigt.
* Der Name „HP Reverb G2 Controller (OpenXR)“ in der Benutzeroberfläche des Eingabesystems wurde aktualisiert.

## <a name="094---2021-05-20"></a>0.9.4 – 2021-05-20

* Abhängig vom OpenXR-Plug-In 1.2.0 von Unity.
* Neue C#-API zum Abrufen des glTF-Modells für den Motion-Controller hinzugefügt.
* Neue C#-API zum Abrufen aktivierter Ansichtskonfigurationen und zum Festlegen von Neuprojektionseinstellungen hinzugefügt.
* Neue C#-API zum Festlegen zusätzlicher Einstellungen für die Berechnung von Gittermodellen mit XRMeshSubsystem hinzugefügt.
* Neue C#-API zum Konfigurieren und Abonnieren von Gestenerkennungsereignissen hinzugefügt.
* Dialogfeld mit „Windows->XR->Editor Remoting settings“ (Editor-Remoting-Einstellungen) hinzugefügt.
* ARM-Unterstützung für HoloLens UWP-Anwendungen hinzugefügt.

## <a name="093---2021-04-29"></a>0.9.3 – 2021-04-29

* Ein Fehler wurde behoben, bei dem die Holographic Remoting-Verbindung nicht zuverlässig ist.
* Ein Fehler wurde behoben, bei dem die VR-Renderingleistung nach dem Upgrade auf das OpenXR-Plug-In 1.1.1 von Unity suboptimal ist.

## <a name="092---2021-04-21"></a>0.9.2 0 – 2021-04-21

* Die Ebenenerkennung von HoloLens 2 in Plug-In-Version 0.9.1 funktioniert mit Version 105 der OpenXR-Vorschaulaufzeit für Mixed Reality.
* Die Ebenenerkennung von HoloLens 2 in Plug-In-Version 0.9.2 funktioniert mit Version 106 der OpenXR-Vorschaulaufzeit für Mixed Reality.
* Einige nicht verwendete Rückrufe wurden aus InputProvider entfernt, um zu verhindern, dass Aufrufe wie „XRInputSubsystem.* GetTrackingOriginMode“ (die nicht von unserem Eingabesystem verwaltet werden) erfolgreich mit irreführenden Werten zurückgegeben werden.
* Die veraltete Version von XRAnchorStore wurde in eine eigene Datei ausgegliedert, um Unity-Konsolenwarnungen zu verhindern.

## <a name="091---2021-04-20"></a>0.9.1 – 2021-04-20

* Abhängig vom OpenXR-Plug-In 1.1.1 von Unity.
* Unterstützung für eine Holographic Remoting-Anwendung für die UWP-Plattform hinzugefügt.
* UnityException wurde behoben, bei der XRAnchorStore versuchte, eine Instanz der Einstellungen außerhalb des Hauptthreads abzurufen.

## <a name="090---2021-03-29"></a>0.9.0 – 2021-03-29

* Unterstützung für räumliche Abbildung über XRMeshSubsystem und ARMeshManager wurde hinzugefügt.
* Neue C#-API zum Abrufen von OpenXR-Handles zur Unterstützung anderer Unity-Pakete, die OpenXR-Erweiterungen nutzen, hinzugefügt.
* Neue C#-API für Interoperabilität mit Windows.Perception-APIs zur Unterstützung anderer Unity-Pakete, die Perception WinRT-APIs nutzen, hinzugefügt.
* Interaktionsprofile aus erforderlichen Features im Windows Mixed Reality-Featuresatz entfernt, sodass Entwickler die Motion-Controller auswählen können, mit denen sie Tests durchführen.
* Eine Validierung des Remotingfeatures des Holographic-Editors wurde hinzugefügt, um Benutzern die ordnungsgemäße Einrichtung des Editor-Remotings zu erleichtern.
* Ein Fehler wurde behoben, bei dem der Unity-Editor abstürzte, wenn der Remotingmodus des Holographic-Editors nach einem Verbindungsfehler beendet wurde.
* Ein Fehler wurde behoben, bei dem nicht vorab vervielfältigte Alphatexturen zu suboptimaler Leistung bei HoloLens 2 geführt haben.
* Ein Fehler wurde behoben, bei dem die Handverfolgung nicht ordnungsgemäß positioniert war, wenn sich der Szenenursprung auf Höhe des Bodens befand.
* Ein Fehler wurde behoben, bei dem die Hand-Mesh-Verfolgung nach dem Verlassen und Laden einer neuen Szene verschwunden ist.
* Ein Fehler wurde behoben, bei dem der Anbieter für auffindbare Kameras nicht ordnungsgemäß bereinigt wurde.
* Der Namespace der XRAnchorStore-API wurde zu „Microsoft.MixedReality.OpenXR“ überarbeitet.