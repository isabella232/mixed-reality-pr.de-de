---
title: Entwerfen eigener immersiver Umgebungen
description: Erfahren Sie, wie Sie Windows Mixed Reality eigene Heimumgebungen erstellen.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Home, Benutzerdefinierte Umgebungen, Orte, Haus, Skyloft, Benutzer, Erstellen, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: c0f006d3e05cb0892a0a9b2014a4d46a0668f628cf369e38c63c83756148d778
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198600"
---
# <a name="design-your-own-immersive-environments"></a>Entwerfen eigener immersiver Umgebungen

>[!NOTE]
>Dies ist ein experimentelles Feature. Probieren Sie es aus, und haben Sie Spaß daran, aber sind Sie nicht überraschend, wenn nicht alles wie erwartet funktioniert. Wir bewerten die Funktionsfähigkeit und das Interesse an der Verwendung. Informieren Sie uns daher in den Entwicklerforen über Ihre Erfahrung (und alle gefundenen [Fehler).](https://forums.hololens.com/categories/custom-home-environments)

Ab dem [Update vom Windows 10 April 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)haben wir ein experimentelles Feature aktiviert, mit dem Sie der Places-Auswahl (auf der Startmenü) benutzerdefinierte Umgebungen hinzufügen können, die als Windows Mixed Reality home verwendet werden [können.](../discover/navigating-the-windows-mixed-reality-home.md) Windows Mixed Reality über zwei Standardumgebungen verfügt, Haus an den Klippen und Skyloft, können Sie als Ihr Haus auswählen. Durch das Erstellen benutzerdefinierter Umgebungen können Sie die Liste mit Ihren eigenen Erstellungen erweitern. Wir stellen dieses Feature in einem frühen Zustand zur Verfügung, um das Interesse von Erstellern und Entwicklern zu bewerten. Sehen Sie sich an, welche Arten von Welten Sie erstellen, und verstehen Sie, wie Sie mit verschiedenen Erstellungstools arbeiten.

Wenn Sie eine benutzerdefinierte Umgebung verwenden, werden Sie feststellen, dass das Teleportieren, die Interaktion mit Apps und das Platzieren von Hologrammen genauso funktioniert wie in Haus an den Klippen und Skyloft. Sie können das Web in einer Brillenlandschaft durchsuchen oder eine begnötige Stadt mit Hologrammen füllen – die Möglichkeiten sind endlos!

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Benutzerdefinierte Heimumgebungen</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>Ausprobieren einer Beispielumgebung

Wir haben eine Beispielumgebung erstellt, die einige der kreativsten Möglichkeiten benutzerdefinierter Heimumgebungen veranschaulicht. Führen Sie die folgenden Schritte aus, um es auszuprobieren:
1. [Laden Sie unsere Beispielumgebung für Island Island herunter](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (Linkpunkte zu selbst extrahierenden ausführbaren Dateien).

    ![Island-Beispielumgebung](images/FantasyLand.jpg)<br>
    *Island-Beispielumgebung*<br>

2. Führen Sie **Fantasy_Island.exe** heruntergeladene Datei aus.

    > [!NOTE]
    > Wenn Sie versuchen, eine .exe aus dem Web heruntergeladene Datei (wie diese) ausführen zu können, wird möglicherweise ein Popupfenster "Windows geschützten PC" angezeigt. Wählen Sie Fantasy_Island.exe aus, und klicken Sie dann auf **Weitere** Informationen und dann auf Trotzdem ausführen, um die Fantasy_Island.exe **aus diesem Popupmenü aus.** Diese Sicherheitseinstellung soll Sie vor dem Herunterladen von Dateien schützen, denen Sie möglicherweise nicht vertrauen möchten. Wählen Sie diese Option daher nur aus, wenn Sie der Quelle der Datei vertrauen.

3. Öffnen **Sie den Datei-Explorer,** und navigieren Sie zum Ordner environments, indem Sie den folgenden Dateispeicherort in die Adressleiste eingeben: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` .
4. Kopieren Sie die Beispielumgebung, die Sie heruntergeladen haben, in diesen Ordner.
5. Starten **Mixed Reality-Portal,** um die Liste der Umgebungen in der Auswahl "Orte" zu aktualisieren.
6. Setzen Sie Ihr Headset an. Sobald Sie zu Hause sind, öffnen Sie die Startmenü **über** die Schaltfläche Windows Controller.
7. Wählen Sie **das Symbol Orte** oberhalb der Liste der angeheftet Apps aus, um eine Startumgebung auszuwählen.
8. Die Von Ihnen heruntergeladene Umgebung "Island Island" finden Sie in der Liste der Orte. Wählen **Sie Island aus,** um Ihre neue benutzerdefinierte Heimumgebung zu erstellen.

## <a name="creating-your-own-custom-environment"></a>Erstellen einer eigenen benutzerdefinierten Umgebung

Zusätzlich zur Verwendung unserer Beispielumgebungen können Sie Ihre eigenen benutzerdefinierten Umgebungen mit Ihrer bevorzugten 3D-Bearbeitungssoftware exportieren. 

### <a name="modeling-guidelines"></a>Modellierungsrichtlinien

Beachten Sie beim Modellieren Ihrer Umgebung die folgenden Empfehlungen, damit Benutzer in einer weltlich großen Welt in der richtigen Ausrichtung bleiben:

1. Benutzer werden bei 0,0,0 gesprungen, also zentriert ihr Spawn-Standort um den Ursprung.
2. Arbeitseinheiten sollten auf Meter festgelegt werden, damit Ressourcen weltweit verfasst werden können.
3. Die Up-Achse sollte auf "Y" festgelegt werden.
4. Das Asset sollte "vorwärts" zur positiven Z-Achse stehen.
5. Sie müssen nicht alle Ihre Gitternetze kombinieren, aber es wird empfohlen, wenn Sie ressourcenbeschränkte Geräte als Ziel verwenden.

### <a name="exporting-your-environment"></a>Exportieren Ihrer Umgebung

Windows Mixed Reality basiert auf binärem glTF (.glb) als Übermittlungsformat für Ressourcen für Umgebungen. glTF ist ein lizenzgebührenfreier offener Standard für die Übermittlung von 3D-Ressourcen, der von der Gruppe "Igenronos" verwaltet wird. Die Unterstützung von Microsoft für das Format für Windows Apps und Erfahrungen wird zunehmen, wenn glTF sich als Branchenstandard für interoperable 3D-Inhalte weiterentwickelt.

Der erste Schritt beim Exportieren von Ressourcen, die als benutzerdefinierte Heimumgebungen verwendet werden sollen, ist das Generieren eines glTF 2.0-Modells. Die glTF-Arbeitsgruppe verwaltet eine Liste der unterstützten Exporte und [Konverter,](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) um ein glTF 2.0-Modell zu erstellen. Verwenden Sie zum Einstieg eines der auf dieser Seite aufgeführten Programme, um ein glTF 2.0-Modell zu erstellen und zu exportieren, oder konvertieren Sie ein vorhandenes Modell mit einem der unterstützten Konverter.

<!-- Additionally, check out [this helpful article, which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.  -->

### <a name="environment-limits"></a>Umgebungsgrenzwerte

Alle Umgebungen müssen < 256 MB groß sein. Umgebungen, die größer als 256 MB sind, können nicht geladen werden und auf eine leere Welt mit nur der Standard-Skybox um den Benutzer zurückfallen. Beachten Sie diese Dateigrößenbeschränkung beim Erstellen Ihrer Modelle. Wenn Sie ihre Umgebung mit dem WindowsMRAssetConverter wie unten beschrieben optimieren möchten, sollten Sie außerdem darauf vertrauen, dass sich die Texturgröße erhöht, wenn der Optimierer Texturen erstellt, die eine größere Dateigröße aufweisen, aber schneller laden. 

### <a name="optimizing-your-environment"></a>Optimieren Ihrer Umgebung

Windows Mixed Reality unterstützt viele optionale Optimierungen, die die Ladezeiten Ihrer Umgebung erheblich reduzieren können. Achten Sie besonders auf Umgebungen mit vielen Texturen, da sie beim Laden manchmal ein Time out sind. Im Allgemeinen wird dieser Schritt für alle Ressourcen empfohlen. Kleinere Umgebungen mit wenigen oder wenig auflösungsbasierten Texturen erfordern dies jedoch nicht immer. 

Um diesen Prozess zu vereinfachen, haben wir den Windows Mixed Reality [Asset Converter (verfügbar](https://github.com/Microsoft/glTF-Toolkit/releases) auf GitHub) für Ihre Optimierungen erstellt. Dieses Tool verwendet eine Reihe von Hilfsprogrammen, die im Microsoft glTF-Toolkit verfügbar sind, um alle standardmäßigen 2.0 glTF- oder GLB-Dateien zu optimieren, indem eine zusätzliche Texturkomprimierung, Komprimierung und Auflösungsskalierung erfolgen. 

Der Konverter unterstützt derzeit mehrere Flags, um das genaue Verhalten der Optimierungen zu optimieren. Es wird empfohlen, die Ausführung mit den folgenden Flags für optimale Ergebnisse zu erzielen:

Flag|Empfohlene Werte|Beschreibung
---|---|---
-max-texture-size|1024 oder 2048| Optimieren Sie den Wert, um die Qualität der Texturen zu verbessern. Der Standardwert ist 512 x 512. Ein größerer Wert wirkt sich erheblich auf die Dateigröße der Umgebung aus. Beachten Sie daher den Grenzwert von 256 MB.
-min-version|1803|Benutzerdefinierte Umgebungen werden nur in Versionen von Windows >= 1803 unterstützt. Dieses Flag entfernt Texturen für ältere Versionen und reduziert die Dateigröße des endgültigen Assets.

Beispiel:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>Testen Ihrer Umgebung

Sobald Sie ihre final.glb-Umgebung haben, können Sie sie im Headset testen. Beginnen Sie bei Schritt 2 im Abschnitt ["Ausprobieren einer Beispielumgebung",](#trying-a-sample-environment) um Ihre benutzerdefinierte Umgebung als Mixed Reality Startumgebung. 

## <a name="sending-feedback"></a>Senden von Feedback

Während wir dieses experimentelle Feature auswerten, sind wir daran interessiert, zu erfahren, wie Sie benutzerdefinierte Umgebungen verwenden, welche Fehler Sie möglicherweise finden und wie Ihnen das Feature gefällt. Geben Sie Feedback zum Erstellen und Verwenden benutzerdefinierter Heimumgebungen in den [Entwicklerforen.](https://forums.hololens.com/categories/custom-home-environments)

## <a name="troubleshooting-and-tips"></a>Problembehandlung und Tipps

### <a name="how-do-i-change-the-name-of-the-environment"></a>Gewusst wie sie den Namen der Umgebung ändern?

Der Dateiname im Ordner environments wird in der Places-Auswahl verwendet. Um den Namen Ihrer Umgebung zu ändern, benennen Sie den Namen der Umgebungsdatei um, und starten Sie dann Mixed Reality-Portal.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Gewusst wie aus meiner Places-Auswahl benutzerdefinierte Umgebungen entfernen?

Um eine benutzerdefinierte Umgebung zu entfernen, öffnen Sie den Ordner environments auf Ihrem PC ( `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` ), und löschen Sie die Umgebung. Nachdem Sie Mixed Reality-Portal neu gestartet haben, wird diese Umgebung nicht mehr in der Auswahl "Orte" angezeigt. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>Gewusst wie standardmäßig auf meine bevorzugte benutzerdefinierte Umgebung festgelegt?

Die Standardumgebung kann derzeit nicht geändert werden. Jedes Mal, wenn Mixed Reality-Portal neu gestartet wird, werden Sie zur Haus an den Klippen zurückgegeben. 

### <a name="i-spawn-into-a-blank-space"></a>Ich spawne in einen leeren Bereich

Windows Mixed Reality [unterstützt keine Umgebungen, die 256 MB überschreiten.](#environment-limits) Wenn eine Umgebung diesen Grenzwert überschreitet, landen Sie in der leeren Skybox ohne Modell.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Das Laden meiner Umgebung dauert sehr lange.

Sie können Ihrer Umgebung optionale Optimierungen hinzufügen, um das Laden zu beschleunigen. Weitere Informationen finden Sie unter ["Optimieren Ihrer Umgebung".](#optimizing-your-environment)

### <a name="the-scale-of-my-environment-is-incorrect"></a>Die Skalierung meiner Umgebung ist falsch.

Windows Mixed Reality übersetzt glTF-Einheiten beim Laden von Umgebungen in eine Verbrauchseinheit. Wenn Ihre Umgebung eine unerwartete Skala hochlädt, überprüfen Sie den Exporter, um sicherzustellen, dass Sie eine Skalierung von 1 Metern erstellen. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>Der Spawn-Speicherort in meiner Umgebung ist falsch.

Der Standardspeicherort für das Spawn befindet sich in der Umgebung bei 0,0,0. Es ist derzeit nicht möglich, diesen Speicherort anzupassen. Daher müssen Sie den Spawnpunkt ändern, indem Sie Ihre Umgebung mit dem Ursprung exportieren, der am gewünschten Spawnpunkt positioniert ist.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>Die Audiodaten klingen in der Umgebung nicht richtig.

Wenn Sie Ihre benutzerdefinierte Umgebung erstellen, wird eine Akustikrenderingsimulation verwendet, die nicht mit dem von Ihnen erstellten physischen Raum übereinstimmt. Der Sound kann aus der falschen Richtung stammen und muffig klingen. 

## <a name="see-also"></a>Siehe auch
* [Windows Mixed Reality Asset Converter (auf GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)