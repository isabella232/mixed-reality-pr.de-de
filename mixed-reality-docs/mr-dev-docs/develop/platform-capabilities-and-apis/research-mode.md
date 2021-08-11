---
title: HoloLens-Forschungsmodus
description: Mithilfe des Forschungsmodus auf HoloLens kann eine Anwendung auf wichtige Gerätesensorstreams (Tiefe, Umgebungsnachverfolgung und IR-Reflektorivität) zugreifen.
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Research Mode, cv, rs4, computer vision, research, HoloLens, HoloLens 2
ms.openlocfilehash: 57306307e4fd23870ae4cbcdb88773cfc858515f4d7ff0e27e26930bace54d65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193684"
---
# <a name="hololens-research-mode"></a>HoloLens-Forschungsmodus

Der Forschungsmodus wurde auf HoloLens -Geräten (1. Generation) eingeführt, um Zugriff auf wichtige Sensoren zu ermöglichen, insbesondere für Forschungsanwendungen, die nicht für die Bereitstellung vorgesehen sind.  Der Forschungsmodus für HoloLens 2 behält die Funktionen von HoloLens 1 bei, fügt aber Zugriff auf die folgenden Streams hinzu:

* **Überwachungskameras für sichtbare Lichtumgebungen:** Graustufenkameras, die vom System für die Kopfverfolgung und kartenbasierte Gebäudebau verwendet werden.
* **Tiefenkamera:** Wird in zwei Modi betrieben:  
    + AHAT, high-frequency (45 FPS) Near-Depth-Sensor, der für die Handverfolgung verwendet wird. Anders als bei der ersten Version des Kurzausbruchmodus bietet AHAT Pseudotiefe mit Phasenumbruch über 1 Meter. 
    + Von der räumlichen Zuordnung verwendete Tiefenmessung mit langer Würfe und niedriger Frequenz (1-5 [FPS)](../../design/spatial-mapping.md)

* **Zwei Versionen des IR-Reflektoritätsstreams:** Wird von der HoloLens zum Berechnen der Tiefe verwendet. Diese Bilder werden durch Einendung und unbeeinflusst von umgebungs sichtbarem Licht geerbt.

Wenn Sie ein -HoloLens 2, haben Sie auch Zugriff auf die folgenden zusätzlichen Eingaben:

* **Beschleunigungsmesser:** Wird vom System verwendet, um die lineare Beschleunigung entlang der X-, Y- und Z-Achse und schwerkraft zu bestimmen.
* **Gyro** : Wird vom System verwendet, um Drehungen zu bestimmen.
* **Magnetometer:** Wird vom System verwendet, um die absolute Ausrichtung zu schätzen.

> [!IMPORTANT]
> Der Forschungsmodus befindet sich derzeit in Public Preview. 

![Screenshot der App "Forschungsmodus"](images/sensor-stream-viewer.jpg)<br>
*Eine Mixed Reality-Erfassung einer Testanwendung, die die acht im Forschungsmodus verfügbaren Sensorstreams anzeigt*

## <a name="usage"></a>Verbrauch

Der Forschungsmodus ist für Wissenschaftler und Industrieexperten konzipiert, die neue Ideen in den Bereichen maschinelles Sehen Und-Roboter erkunden.  Sie ist nicht für Anwendungen vorgesehen, die in Unternehmensumgebungen bereitgestellt oder über die Microsoft Store oder andere Verteilungskanäle verfügbar sind.

Darüber hinaus bietet Microsoft keine Zusicherungen, dass der Forschungsmodus oder entsprechende Funktionen in zukünftigen Hardware- oder Betriebssystemupdates unterstützt werden. Lassen Sie sich jedoch nicht davon abzuhalten, sie zum Entwickeln und Testen neuer Ideen zu verwenden!

## <a name="security-and-performance"></a>Sicherheit und Leistung

Die Aktivierung des Forschungsmodus verbraucht mehr Akkuleistung als die Verwendung des HoloLens 2 unter normalen Bedingungen, auch wenn die Anwendung, die die Features des Forschungsmodus verwendet, nicht ausgeführt wird.  Die Aktivierung dieses Modus kann auch die Gesamtsicherheit Ihres Geräts senken, da Anwendungen sensorische Daten missbrauchen können.  Weitere Informationen zur Gerätesicherheit finden Sie in den häufig gestellten Fragen [HoloLens Sicherheit.](/hololens/hololens-faq-security)  

## <a name="device-support"></a>Geräteunterstützung
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>Kopfverfolgungskameras</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Tiefen& IR-Kamera</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Beschleunigungsmesser</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Gyroskop</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Magnetometer</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>Aktivieren des Forschungsmodus (HoloLens ersten Generation und HoloLens 2)

Der Forschungsmodus ist eine Erweiterung des Entwicklermodus. Bevor Sie beginnen, müssen die Entwicklerfeatures des Geräts aktiviert werden, um auf die Einstellungen des Forschungsmodus zugreifen zu können: 

* Öffnen Sie **start menu > Einstellungen,** und wählen Sie **Updates aus.**
* Wählen Sie **Für Entwickler aus,** und aktivieren Sie **den Entwicklermodus**.
* Scrollen Sie nach unten, und aktivieren Sie **Geräteportal**.

Nachdem die Entwicklerfeatures aktiviert wurden, stellen [Sie eine Verbindung mit dem Geräteportal herstellen,](/windows/uwp/debug-test-perf/device-portal-hololens) um die Features des Forschungsmodus zu aktivieren:

* Wechseln Sie **im > zu** System > **Research Geräteportal**.
* Wählen Sie **Zugriff auf Sensorstream zulassen aus.**
* Starten Sie das Gerät über das **Menüelement** Energie am oberen Seitenanfang neu.

Nachdem Sie das Gerät neu gestartet haben, können die anwendungen, die über die Geräteportal, **auf** Streams im Forschungsmodus zugreifen.

![Registerkarte "Forschungsmodus" HoloLens Geräteportal](images/ResearchModeDevPortal.png)<br>
*Fenster "Forschungsmodus" im HoloLens Geräteportal*

> [!IMPORTANT]
> Der Forschungsmodus für HoloLens 2 ist ab Build 19041.1364 verfügbar. Wenn Sie Zugriff in einem früheren Build benötigen, registrieren Sie sich für unser [Insider Preview-Programm.](/hololens/hololens-insider) Weitere Informationen finden Sie im [Repository research mode GitHub .](https://github.com/microsoft/HoloLens2ForCV)

### <a name="using-sensor-data-in-your-apps"></a>Verwenden von Sensordaten in Ihren Apps

Anwendungen können auf die Sensordatenstromdaten [](/windows/win32/medfound/microsoft-media-foundation-sdk) auf die gleiche Weise wie Media Foundation auf Foto- und Videokamerastreams zugreifen. 

Alle APIs, die für die entwicklung HoloLens funktionieren, sind auch im Forschungsmodus verfügbar. Insbesondere weiß die Anwendung genau, wo sich HoloLens bei jeder Sensorframeerfassung im 6DoF-Raum befindet.

Wir haben Beispielanwendungen, die den Datenstromzugriff im Forschungsmodus unter Verwendung der systeminternen [Und-Extrinsik sowie aufzeichnungsstreams](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)zeigen:
* [HoloLens (1. Generation)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>Support

Für HoloLens (erste Generation) verwenden [](https://github.com/Microsoft/HololensForCV/issues) Sie die Problemverfolgung im HoloLensForCV-Repository, um Feedback zu senden und bekannte Probleme zu verfolgen.

Verwenden HoloLens 2 Problemverfolgung [im](https://github.com/microsoft/HoloLens2ForCV/issues) HoloLens2ForCV-Repository, um Feedback zu senden und bekannte Probleme zu verfolgen.

## <a name="see-also"></a>Siehe auch

* [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [HoloLensForCV-GitHub Repository](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens2ForCV-GitHub Repository](https://github.com/microsoft/HoloLens2ForCV)
* [Verwenden des Windows-Geräteportals](using-the-windows-device-portal.md)