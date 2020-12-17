---
title: Aktualisieren von SteamVR-Apps für Windows Mixed Reality
description: Bewährte Methoden zum Aktualisieren Ihrer steamvr-Anwendung, um die Kompatibilität mit Windows Mixed Reality-Headsets zu maximieren.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Steamvr, Kompatibilität, portieren, hololens 1. gen, Mixed Reality-Headset, Windows Mixed Reality-Headset, Migration, Windows 10, Steam, Motion Controllers, Haptik
ms.openlocfilehash: 94b6aad63156d752858c6566174ff01e6127d75d
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612904"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>Aktualisieren von SteamVR-Apps für Windows Mixed Reality

Wir empfehlen Entwicklern, ihre steamvr-Erfahrungen zu testen und zu optimieren, um Sie auf Windows Mixed Reality-Headsets auszuführen. Diese Dokumentation behandelt allgemeine Verbesserungen, die Sie vornehmen können, um Ihre Erfahrungen in Windows Mixed Reality hervorragend ausführen zu können.

## <a name="initial-setup-instructions"></a>Anweisungen für die erste Einrichtung

Um mit dem Testen Ihres Spiels oder ihrer app in Windows Mixed Reality zu beginnen, müssen Sie zunächst unseren ersten Schritten folgen [.](https://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Controller Modelle

1. Wenn Ihre APP Controller Modelle rendert:
    * Verwenden der [Windows Mixed Reality Motion Controller-Modelle](../../design/motion-controllers.md#rendering-the-motion-controller-model)
    * Verwenden Sie ivrrendermodel:: getcomponentstate, um lokale Transformationen zu Komponenten teilen (z. b. Zeiger Pose) zu erhalten.
2. Erfahrungen mit einer Art von häntigkeit sollten Hinweise von den Eingabe-APIs erhalten, um die Controller zu unterscheiden [(Unity-Beispiel)](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) .

## <a name="controls"></a>Steuerelemente

Beachten Sie beim Entwerfen oder Anpassen des Steuerelement Layouts die folgenden reservierten Befehle:
1. Das Klicken auf den **linken und rechten analogen Ministick** ist für das **Dashboard "Steam**" reserviert.

> [!NOTE]
> Wenn Sie einen HP-Reverb-G2-Controller verwenden, ist das Klicken auf die Menü Schaltfläche rechts für das **Steam-Dashboard** reserviert.

2. Mit der **Windows-Schaltfläche** werden Benutzer immer an den Windows Mixed Reality-Start zurückgegeben.

Wenn möglich, wird die fingerstick-basierte teleportierung standardmäßig auf das [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) -teleportationsverhalten abgestimmt.

## <a name="tooltips-and-ui"></a>Quick Infos und Benutzeroberfläche

Viele VR-Spiele nutzen die Quick Infos und Überlagerungen von Motion Controller, um Benutzern zu vermitteln, dass Sie Ihre APP oder Spiele am wichtigsten sind. Wenn Sie Ihre Anwendung für Windows Mixed Reality optimieren, sollten Sie diesen Teil Ihrer Benutzer Arbeit überprüfen, um sicherzustellen, dass die Quick Infos den Windows Controller-Modellen zugeordnet sind.

Außerdem sollten Sie, wenn Sie Ihre Benutzeroberflächen anzeigen, wenn Sie die Abbilder der Controller anzeigen, aktualisierte Images mithilfe der Windows Mixed Reality Motion Controller bereitstellen.

## <a name="haptics"></a>Haptik

Ab dem [Windows 10-Update vom April 2018](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)wird die Haptik jetzt für die Verwendung von steamvr in Windows Mixed Reality unterstützt. Wenn Ihre steamvr-APP oder Ihr Spiel bereits Unterstützung für die Haptik bietet, sollte Sie nun (ohne zusätzliche Arbeit) mit [Windows Mixed Reality Motion Controllers](../../design/motion-controllers.md)funktionieren.

Windows Mixed Reality Motion Controllers verwenden einen standardmäßigen Haptik-Motor, im Gegensatz zu den linearen Aktoren, die in einigen anderen steamvr-Bewegungs Controllern gefunden werden. Dies kann zu einer etwas anderen-als-erwarteten Benutzer Darstellung führen. Daher empfiehlt es sich, das Design der Haptik mit Windows Mixed Reality Motion Controller zu testen und zu optimieren. Manchmal sind kurze, willkürliche Pulse (5-10 ms) für Windows Mixed Reality Motion Controllers weniger bemerkbar. Um einen aussagekräftigeren Impuls zu erzielen, experimentieren Sie mit dem Senden eines längeren "Click"-Vorgangs (40-70 MS), um dem Motor mehr Zeit für den Einstieg zu liefern

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Starten von steamvr-Apps über das Windows Mixed Reality-Startmenü

Bei der durch die Verwendung von Steam verteilten VR-Umgebung haben wir [Windows Mixed Reality für steamvr](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) zusammen mit den neuesten [Windows-Versionen](https://insider.windows.com)aktualisiert. Steamvr-Titel werden nun automatisch im Windows Mixed Reality-Startmenü in der Liste "alle apps" angezeigt.

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality-Logo

Um die Windows Mixed Reality-Unterstützung für Ihren Titel anzuzeigen, wechseln Sie auf der Startseite der APP zum Link "Store bearbeiten", wählen Sie die Registerkarte "grundlegende Info" aus, und Scrollen Sie nach unten zu "Virtual Reality". Deaktivieren Sie die Option "gemischte Windows-Realität ausblenden", und veröffentlichen Sie Sie im Store.

## <a name="bugs-and-feedback"></a>Fehler und Feedback

Ihr Feedback ist äußerst nützlich, wenn es um die Verbesserung der Windows Mixed Reality-steamvr-Darstellung geht. Übermitteln Sie Feedback und Fehler über den [Windows-Feedback-Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Im folgenden finden [Sie einige Tipps, wie Sie Ihr steamvr-Feedback so hilfreich wie möglich machen](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Wenn Sie Fragen oder Kommentare haben, die Sie freigeben können, können Sie uns auch in unserem [Steam-Forum](https://steamcommunity.com/app/719950/discussions/)erreichen.

## <a name="faqs-and-troubleshooting"></a>FAQs und Problembehandlung

Wenn Sie allgemeine Probleme beim Einrichten oder Wiedergeben Ihrer Umgebung haben, sehen Sie sich [die neuesten Schritte zur Problem](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)Behandlung an.

## <a name="see-also"></a>Siehe auch

* [Installieren der Tools](../install-the-tools.md)
* [Verlauf des Headset-und Motion Controller-Treibers](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality-Mindestanforderungen für die PC-Hardware Kompatibilität](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
