---
title: Upgrade von Projekten in Unreal
description: Bleiben Sie mit Schritten zu Versionsupgrades, Änderungen an APIs und veralteten Features für Ihre Unreal-Projekte auf dem Laufenden.
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Dokumentation, Leitfäden, Features, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Portieren, Upgrade
ms.openlocfilehash: 27fb726bc0ca9c51b4e7b68ad28b76f89312262e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010050"
---
# <a name="upgrading-projects-in-unreal"></a>Upgrade von Projekten in Unreal

Bei Updates auf eine neue Unreal-Version werden veraltete Funktionen beim Kompilieren von Blaupausen oder beim Verpacken des Projekts in Form von Warnungen angezeigt.  Funktionen werden als veraltet deklariert, wenn eine neue Funktion hinzugefügt wurde, die an ihrer Stelle verwendet werden soll. 

## <a name="426-upgrades"></a>Upgrades in 4.26
 
In Version 4.26 wurden alle AR- und VR-Plattformen umgestaltet, um allgemeine Schnittstellen hinzuzufügen und den Anwendungscode plattformneutral zu halten, weshalb eventuell mehr Warnungen als gewöhnlich angezeigt werden.  Es wird empfohlen, auf die neuen APIs zu aktualisieren, damit das Projekt leichter auf andere Plattformen portiert werden kann.

Aus Warnmeldungen ist zu ersehen, welche Funktion als veraltet deklariert wurde und welche Funktion stattdessen verwendet werden soll.  Alle veralteten Funktionen funktionieren in dieser Version weiterhin, tun dies in zukünftigen Versionen aber möglicherweise nicht mehr.  Ferner werden als veraltet deklarierte Versionen bei der Suche nach Funktionen in einer Blaupause nicht mehr aufgelistet.

![Blaupause der Funktion „Create Named ARPin“](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>Veraltete Funktionen aus 4.25

| Veraltete Funktionen | Neue Funktion |
| --- | --- |
| CreateNamedARPin | ![Blaupause der Funktion „Pin Component“](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![Blaupause der Funktion „Load ARPins from Local Store“](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![Blaupause der Funktion „Save ARPin to Local Store“](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![Blaupause der Funktion „Remove ARPin from Local Store“](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![Blaupause der Funktion „Set Enabled XRCamera“](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![Blaupause der Funktion „Resize XRCamera“](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![Blaupause der Funktion „Toggle ARCapture“ zum Starten der Erfassung des Kamerabilds](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![Blaupause der Funktion „Toggle ARCapture“ zum Beenden der Erfassung des Kamerabilds](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![Blaupause der Funktion „Toggle ARCapture“ zum Starten der Erfassung von QR-Codes](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![Blaupause der Funktion „Toggle ARCapture“ zum Beenden der Erfassung von QR-Codes](images/unreal-porting-img-11.png) |
| Die räumliche Abbildung startete in Version 4.25 bisher automatisch, muss in Version 4.26 jedoch eingeschaltet werden. | ![Blaupause der Funktion „Toggle ARCapture“ zum Aktivieren der räumlichen Abbildung](images/unreal-porting-img-12.png) |
| ShowKeyboard | Wurde in 4.26 entfernt, da die Tastatur automatisch angezeigt wird, wenn der Fokus auf einem Textwidget liegt. |
| HideKeyboard | Wurde in 4.26 entfernt, da die Tastatur automatisch ausgeblendet wird, wenn ein Textwidget den Fokus verliert. |
| SupportsHandTracking | ![Blaupause der Eigenschaft „Supports Hand Tracking“](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![Blaupause der Eigenschaft „IsDisplayOpaque“](images/unreal-porting-img-14.png) |
| GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus | ![Blaupause der Funktion „Get Motion Controller Data“](images/unreal-porting-img-15.png) |
| GetVersionString | ![Blaupause der Funktion“Get Version String“](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![Blaupause der Eigenschaft „IsTrackingAvailable“](images/unreal-porting-img-17.png) |
| IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed | Verwenden Sie das Eingabeaktionssystem von Unreal. |
| SetFocusPointForFrame | In 4.26 entfernt.  Bisher für die Neuprojektion beim Remoting verwendet, das jetzt tiefenbasierte Neuprojektion unterstützt. |

## <a name="426-changes"></a>Änderungen in 4.26

Die maßgebliche Änderung besteht darin, dass **In VR starten** aus **Bearbeiten > Projekteinstellungen > Projekt > Beschreibung > Einstellungen** beim Starten des Windows Mixed Reality-Plug-Ins obligatorisch ist. Ohne diesen Parameter werden Ihre Hologramme nicht auf dem Gerät angezeigt.
