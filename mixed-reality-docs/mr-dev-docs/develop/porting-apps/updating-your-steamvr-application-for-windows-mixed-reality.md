---
title: Aktualisieren von SteamVR-Apps für Windows Mixed Reality
description: Bewährte Methoden zum Aktualisieren Ihrer SteamVR-Anwendung, um die Kompatibilität mit Windows Mixed Reality Headsets zu maximieren.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, Kompatibilität, Portierung, HoloLens 1. Generation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Migration, Windows 10, Steam, Motion-Controller,Tik
ms.openlocfilehash: ee72994691970a3701ec8462ab0f42b6d1da1820589ca68a92c9a78fe1c18a41
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196190"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>Aktualisieren von SteamVR-Apps für Windows Mixed Reality

Wir empfehlen Entwicklern, ihre "SteamVR"-Erfahrungen zu testen und zu optimieren, um sie auf Windows Mixed Reality headsets ausführen zu können. In dieser Dokumentation werden allgemeine Verbesserungen behandelt, die Sie ausführen können, damit Ihre Erfahrungen auf dem Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Anweisungen zum anfänglichen Setup

Wenn Sie ihr Spiel oder Ihre App auf dem Computer testen Windows Mixed Reality Sie zunächst unseren Leitfaden [für die ersten Schritte befolgen.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)

## <a name="controller-models"></a>Controllermodelle

1. Wenn Ihre App Controllermodelle rendert:
    * Verwenden der [Windows Mixed Reality Motion Controller-Modelle](../../design/motion-controllers.md#rendering-the-motion-controller-model)
    * Verwenden Sie IVRRenderModel::GetComponentState, um lokale Transformationen in Komponententeile (z. B. Zeigerpose) zu erhalten.
2. Erfahrungen mit einem Konzept der Übergabe sollten Hinweise von den Eingabe-APIs erhalten, um Controller zu unterscheiden [(Unity-Beispiel)](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Steuerelemente

Beachten Sie beim Entwerfen oder Anpassen des Steuerelementlayouts die folgenden reservierten Befehle:
1. Das Klicken nach unten **auf den linken und rechten analogen Thumbstick** ist für das Dashboard **"Dashboard" reserviert.**

> [!NOTE]
> Wenn Sie einen HP Reverb G2-Controller verwenden, ist das Klicken auf die rechte Menüschaltfläche für das **Dashboard "Dashboard" reserviert.**

2. Über **Windows Schaltfläche** werden Benutzer immer zur Startseite Windows Mixed Reality zurück.

Verwenden Sie nach Möglichkeit standardmäßig die fingerabdruckbasierte Teleportierung, um dem Windows Mixed Reality [des](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) Teleportierungsverhaltens zu passen.

## <a name="tooltips-and-ui"></a>QuickInfos und Benutzeroberfläche

Viele VR-Spiele nutzen QuickInfos und Überlagerungen des Bewegungscontrollers, um Benutzern ihre App oder spiele die wichtigsten Befehle beizubringen. Wenn Sie Ihre Anwendung für Windows Mixed Reality optimieren, empfehlen wir Ihnen, diesen Teil Ihrer Erfahrung zu überprüfen, um sicherzustellen, dass die QuickInfos den Windows Controllermodellen entsprechen.

Stellen Sie darüber hinaus sicher, dass Sie aktualisierte Bilder mithilfe der Windows Mixed Reality Bereitstellen von Controllern bereitstellen, wenn ihre Erfahrung punktet, an denen Sie Bilder der Controller anzeigen.

## <a name="haptics"></a>Haptik

Ab dem [Update vom Windows 10 April 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)werden ab sofort Auch-Zeichen für die Funktionen von "SteamVR" auf Windows Mixed Reality. Wenn Ihre SteamVR-App oder Ihr Game bereits Unterstützung für Dieben enthält, sollte sie jetzt (ohne zusätzliche Arbeit) mit Windows Mixed Reality [funktionieren.](../../design/motion-controllers.md)

Windows Mixed Reality Motion-Controller verwenden im Gegensatz zu den linearen Aktuatoren, die in einigen anderen Motion-Controllern von Controllers für Dies sind, einen Standard-Aktuator. Dies kann zu einer etwas anders als erwarteten Benutzererfahrung führen. Daher empfiehlt es sich, Ihr Design für Dietikate mit Windows Mixed Reality zu testen und zu optimieren. Beispielsweise sind manchmal kurze pulstische Pulse (5-10 ms) bei Bewegungscontrollern weniger Windows Mixed Reality wahrnehmbar. Um einen spürbareren Puls zu erzeugen, experimentieren Sie mit dem Senden eines längeren "Klicks" (40-70 ms), um dem Motor mehr Zeit zum Hochdrehen zu geben, bevor sie zum erneuten Ausschalten animiert werden.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Starten von SteamVR-Apps über Windows Mixed Reality Startmenü

Für VR-Erfahrungen, die über Steam verteilt werden, haben wir Windows Mixed Reality [für SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) zusammen mit den neuesten Windows [aktualisiert.](https://insider.windows.com) Die Titel von "SteamVR" werden jetzt automatisch in Windows Mixed Reality Startmenü Liste "Alle Apps" angezeigt.

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality-Logo

Um die Windows Mixed Reality für Ihren Titel anzuzeigen, wechseln Sie zum Link "Store-Seite bearbeiten" auf Ihrer App-Landing Page, wählen Sie die Registerkarte "Grundlegende Informationen" aus, und scrollen Sie nach unten zu "Virtual Reality". Deaktivieren Sie die Option "Hide Windows Mixed Reality", und veröffentlichen Sie sie dann im Store.

## <a name="bugs-and-feedback"></a>Fehler und Feedback

Ihr Feedback ist von unschätzbarem Wert, wenn es um die Verbesserung der Windows Mixed Reality Von SteamVR geht. Übermitteln Sie alle Feedbacks und Fehler über [Windows-Feedback-Hub](/windows/mixed-reality/enthusiast-guide/filing-feedback). Im Folgenden finden Sie [einige Tipps, wie Sie Ihr Feedback zu "SteamVR" so hilfreich wie möglich gestalten können.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)

Wenn Sie Fragen oder Kommentare zu teilen haben, können Sie uns auch über unser [Forum zu Erhalten.](https://steamcommunity.com/app/719950/discussions/)

## <a name="faqs-and-troubleshooting"></a>Häufig gestellte Fragen und Problembehandlung

Wenn allgemeine Probleme beim Einrichten oder Wiederverspielen Ihrer Umgebung auft sind, sehen Sie sich [die neuesten Schritte zur Problembehandlung an.](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)

## <a name="see-also"></a>Siehe auch

* [Installieren der Tools](../install-the-tools.md)
* [Headset- und Motion Controller-Treiberverlauf](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality mindestens erforderliche Richtlinien für die PC-Hardwarekompatibilität](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)