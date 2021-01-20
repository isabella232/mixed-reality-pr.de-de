---
title: Aktivieren des Platzierens von 3D-Modellen auf der Startseite
description: Erfahren Sie, wie Sie 3D-Modelle von Ihrer Website oder Anwendung in Windows Mixed Reality Home platzieren.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, Modell, Ort in Zuhause, Ort, Welt, Modellierung, gemischte Realität Home, Web, APP, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 58da61add35546331ff8199fa20885f9869a9f43
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583808"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Aktivieren der Platzierung von 3D-Modellen in der Mixed Reality Startumgebung

> [!NOTE]
> Diese Funktion wurde als Teil des [Windows 10-Updates vom April 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)hinzugefügt. Ältere Versionen von Windows sind mit diesem Feature nicht kompatibel.

Der [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) -Startpunkt ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen. In einigen Szenarios ermöglichen 2D-Apps (wie die holograms-APP) die Platzierung von 3D-Modellen direkt in der Mixed Reality-Startseite als Dekorationen oder für eine weitere Prüfung in vollständigem 3D. Das *Add Model-Protokoll* ermöglicht es Ihnen, ein 3D-Modell von Ihrer Website oder Anwendung direkt an die Windows Mixed Reality-Startseite zu senden, wo Sie wie [3D-App-Launcher](3d-app-launcher-design-guidance.md), 2D-apps und holograms beibehalten wird. 

Wenn Sie z. b. eine Anwendung entwickeln, die einen Katalog mit 3D-Möbeln zum Entwerfen eines leer Zeichens verwendet, verwenden Sie das *Add Model-Protokoll* , um es Benutzern zu ermöglichen, diese 3D-möbelmodelle aus dem Katalog zu platzieren. Nachdem die Benutzer in der Welt platziert wurden, können Sie diese 3D-Modelle wie andere holograms in der Startseite verschieben, ändern und ihre Größe ändern. Dieser Artikel bietet eine Übersicht über die Implementierung des *Add Model-Protokolls* , mit dem Benutzer ihre Welt mit 3D-Objekten aus Ihrer APP oder dem Web ergänzen können.

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Modell Protokoll hinzufügen</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>Grundlagen

Es gibt zwei Schritte, um die Platzierung von 3D-Modellen in der Windows Mixed Reality-Startseite zu aktivieren:
1. [Stellen Sie sicher, dass Ihr 3D-Modell mit dem Windows Mixed Reality-Home kompatibel ist](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implementieren *Sie das Add Model-Protokoll* in Ihrer Anwendung oder Webseite (in diesem Artikel).

## <a name="implementing-the-add-model-protocol"></a>Implementieren des *Add Model-Protokolls*

Sobald Sie über ein [kompatibles 3D-Modell](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)verfügen, können Sie das *Add Model-Protokoll* implementieren, indem Sie den folgenden URI auf einer beliebigen Webseite oder Anwendung aktivieren:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Wenn der URI auf eine Remote Ressource verweist, wird er automatisch heruntergeladen und in die Startseite eingefügt. Lokale Ressourcen werden in den App-Datenordner der Mixed Reality-Startseite kopiert, bevor Sie in der Startseite abgelegt werden. Es empfiehlt sich, die Benutzer Funktionalität für Szenarien zu berücksichtigen, in denen der Benutzer möglicherweise eine ältere Version von Windows ausführen kann, die dieses Feature nicht unterstützt, indem Sie die Schaltfläche ausblenden oder nach Möglichkeit deaktivieren. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Aufrufen des *Add Model-Protokolls* aus einer universelle Windows-Plattform-App:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Aufrufen des *Add Model-Protokolls* von einer Webseite:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Überlegungen zu immersiven (VR) Headsets

* Bei immersiven (VR)-Headsets muss das Mixed Reality-Portal vor dem Aufrufen des *Add Model-Protokolls* nicht ausgeführt werden. In diesem Fall startet das *Modell zum Hinzufügen von Modellen* das Mixed Reality-Portal und platziert das Objekt direkt an der Stelle, an der das Headset sucht, sobald Sie in der Mixed Reality-Startseite eintreffen. 
* Wenn Sie das *Add Model-Protokoll* vom Desktop aus aufrufen, während das gemischte Reality-Portal bereits ausgeführt wird, stellen Sie sicher, dass das Headset "Awake" ist. Andernfalls ist die Platzierung nicht erfolgreich. 

## <a name="see-also"></a>Weitere Informationen

* [Erstellen von 3D-Modellen für die Verwendung in der Windows Mixed Reality-Startseite](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)