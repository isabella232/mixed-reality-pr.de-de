---
title: Verwenden von webvr mit gemischter Windows-Realität
description: Erfahren Sie mehr über die Grundlagen von webvr, wie Sie diese mit Microsoft Edge auf Windows Mixed Reality-Headsets verwenden und häufige Probleme bei der Problembehandlung.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, webvr, Edge, Microsoft Edge, Webbrowser
ms.openlocfilehash: 89d9e51bf4adb63e7836968a0112849f7ac403d0
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581755"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Verwenden von webvr mit gemischter Windows-Realität

>[!IMPORTANT]
>Die meisten modernen Webbrowser haben die Unterstützung von webvr zugunsten von webxr, dem neuen Standard zum Erstellen von immersiven Webumgebungen für VR-Headsets, als veraltet markiert. Installieren Sie [den neuen Microsoft Edge](using-microsoft-edge.md) für webxr-Support.

## <a name="what-is-webvr"></a>Was ist WebVR?

[Webvr](https://webvr.info) ist eine offene Spezifikation, mit der Sie VR direkt in einem Browser erleben können. Wenn eine Website die webvr-Unterstützung implementiert und 3D-Inhalte bereitstellt, können Sie mit der Zustimmung des Benutzers immersive Inhalte im Headset anzeigen.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Worin besteht der Unterschied zwischen webvr und dem Durchsuchen des Internets in VR?

Webvr ist eine Technologie, die es einem Website Autor ermöglicht, eine VR-Funktionalität zu einer Seite hinzuzufügen. Die webvr-API wird von einer Seite verwendet, um 3D-Inhalt (z. b. ein Video mit 360-Grad oder ein 3D-Modell oder ein 3D-Spiel) für das gesamte Headset anzuzeigen. **Beispiel:** Anzeigen eines 360-Videos auf [CNN.com/VR](http://cnn.com/vr). Wenn eine Seite webvr unterstützt, wird eine Schaltfläche oder ein anderes UI-Element hinzugefügt, das Sie für die Eingabe von VR auswählen können.

Das Durchsuchen des Internets in VR bedeutet, dass Sie den Edge-Browser verwenden, während Sie Ihr Headset verwenden, als 2D-App-Slate innerhalb von cliffhouse.

## <a name="do-all-websites-support-webvr"></a>Unterstützen alle Websites webvr

Nein. Website Autoren müssen sich für die Verwendung von webvr entscheiden, und Sie können optimierte Websites für bestimmte Browser, Headsets und Controller erstellen. Einige webvr-Inhalte sind nur für Mobile VR-Geräte optimiert. Beachten Sie auch, dass Websites den webvr-Inhalt explizit erstellen und bereitstellen müssen. Die Anzahl von Standorten, an denen einige webvr-kompatible Inhalte vorhanden sind, wächst jeden Tag.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>Kann ich "Vive/Oculus" usw. verwenden, um webvr-Inhalte in Microsoft Edge anzuzeigen

Nein. Ein Windows Mixed Reality-Headset ist erforderlich, um webvr in Edge zu verwenden. Sie können jedoch in einem anderen Browser auf webvr-Inhalte zugreifen. eine komplette Liste der kompatiblen Geräte und Browser finden Sie unter: [webvr. Rocks](http://webvr.rocks/).

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>Wo finde ich die webvr-Entwicklerdokumentation?

Die Entwicklerdokumentation finden Sie hier: [webvr-Entwicklerdokumentation](/microsoft-edge/webvr/).

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>Ich habe eine Website mit webvr gefunden, die in Windows Mixed Reality nicht funktioniert. Was soll ich tun

Sie können fehlerhafte Websites direkt an das Microsoft Edge-Browser Team in der [Problem](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)Verfolgung oder per Twitter über [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)Berichten.

Fehler können auch mithilfe der Windows-Feedback-Hub-App Unterkategorie protokolliert werden:

Probleme mit der Microsoft Edge->-Website

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>Was ist eine gute Seite, um zu testen, ob webvr funktioniert

Siehe [webvr.info Samples](http://webvr.info/samples/XX-vr-controllers.html).

## <a name="how-do-i-set-up-webvr"></a>Gewusst wie webvr einrichten

Um webvr-Inhalte auf einem Windows Mixed Reality-Headset (mit Hardware oder Simulation) zu erleben, müssen Sie folgende Schritte ausführen:

1. Stellen Sie sicher, dass Ihr Headset angeschlossen ist.
2. Starten Sie Microsoft Edge entweder auf dem Desktop oder in gemischter Realität.
3. Navigieren Sie zu einer webvr-aktivierten Seite.
4. Wählen Sie auf der Seite die Schaltfläche Enter VR eingeben aus (der Speicherort und die visuelle Darstellung dieser Schaltfläche können je nach Website variieren). Dies könnte etwa wie folgt aussehen: \
   ![VR-Brillen Bild](images/75px-enter-vr.png)
5. Wenn Sie zum ersten Mal versuchen, VR in eine bestimmte Domäne einzugeben, fordert der Browser die Zustimmung zur Verwendung der immersiven Ansicht an, und wählen Sie ja: ![Benutzeroberfläche für Zustimmung, die beim ersten Versuch angezeigt wird, VR in eine bestimmte Domäne einzugeben](images/1053px-Webvr-consent-ui.png)
6. Ihr Headset sollte mit dem Anzeigen der webvr-Inhalte beginnen.

## <a name="see-also"></a>Weitere Informationen

* [Problembehandlung > webvr](webvr-questions.md)
* [Vorgehensweise beim Einstieg in Ihre erste webvr-Benutzer Darstellung](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Verwenden von spielen und apps in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Ihre gemischte Reality-Startseite](your-mixed-reality-home.md)
* [Überwachungs System](tracking-system.md)
* [Motion-Controller](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Einreichen von Feedback](filing-feedback.md)