---
title: HoloLens-Forschungsmodus
description: Mithilfe des Research-Modus auf hololens kann eine Anwendung auf wichtige Geräte Sensordaten Ströme (Tiefe, Umgebungs Überwachung und IR-Reflektivität) zugreifen.
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Research Mode, CV, RS4, Maschinelles sehen, Forschung, hololens, hololens 2
ms.openlocfilehash: 6737f9b668b73258e65f8d00e85dcd19c28ddfb5
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237131"
---
# <a name="hololens-research-mode"></a>HoloLens-Forschungsmodus

Der Forschungs Modus wurde auf hololens-Geräten (1. Gen) eingeführt, um den Zugriff auf Schlüssel Sensoren zu erhalten, insbesondere für Forschungsanwendungen, die nicht für die Bereitstellung vorgesehen sind.  Der Forschungs Modus für hololens 2 behält die Funktionen von hololens 1 bei und bietet Zugriff auf die folgenden Datenströme:

* **Sichtbare helle Umgebungs Überwachungskameras** : graue Kameras, die vom System für die Head-Nachverfolgung und die Zuordnungs Bildung verwendet werden.
* **Tiefe Kamera** – wird in zwei Modi betrieben:  
    + Ahat, hohe Häufigkeit (45 fps), die für die Hand Verfolgung verwendet wird. Anders als bei der ersten Version des kurzthrow-Modus gibt ahat eine Pseudo Tiefe mit einem Phasen Umbruch über eine Verbrauchseinheit hinaus. 
    + Lange throw-, Low-Frequency (1-5 fps)-Erkennung, die von der [räumlichen Zuordnung](../../design/spatial-mapping.md) verwendet wird

* **Zwei Versionen des IR-Reflektivität-Streams** : werden von den hololens zum Berechnen der Tiefe verwendet. Diese Bilder werden von Infrarot beleuchtet und sind von der Sichtbarkeit sichtbar.

Wenn Sie ein hololens 2 verwenden, haben Sie auch Zugriff auf die unten aufgeführten zusätzlichen Eingaben:

* **Beschleunigungsmesser** – wird vom System verwendet, um die lineare Beschleunigung entlang der X-, Y-und Z-Achse und der Schweregrad zu ermitteln.
* **Gyro** – wird vom System verwendet, um Drehungen zu bestimmen.
* **Magnetometer** – wird vom System zum Schätzen der absoluten Ausrichtung verwendet.

> [!IMPORTANT]
> Der Research-Modus befindet sich derzeit in Public Preview. 

![Screenshot der Recherche Modus-App](images/sensor-stream-viewer.jpg)<br>
*Eine gemischte Realität-Erfassung einer Testanwendung, die die acht im Research-Modus verfügbaren Sensordaten Ströme anzeigt*

## <a name="usage"></a>Verwendung

Der Forschungs Modus wurde für akademische und Industrieexperten entwickelt, die neue Ideen in den Feldern Maschinelles Sehen und Robotik kennenlernen.  Sie ist nicht für Anwendungen gedacht, die in Unternehmensumgebungen bereitgestellt werden oder über die Microsoft Store oder andere Vertriebskanäle verfügbar sind.

Außerdem bietet Microsoft keine Garantie dafür, dass der Forschungs Modus oder die entsprechende Funktionalität bei zukünftigen Hardware-oder Betriebssystemupdates unterstützt wird. Lassen Sie die Verwendung der Anwendung zum entwickeln und Testen neuer Ideen jedoch nicht zu.

## <a name="security-and-performance"></a>Sicherheit und Leistung

Wenn Sie den Research-Modus aktivieren, wird mehr Akkuleistung beansprucht als bei der Verwendung der hololens 2 unter normalen Bedingungen, selbst wenn die Anwendung, die die Forschungs Modus-Features verwendet, nicht  Wenn Sie diesen Modus aktivieren, kann die Gesamtsicherheit Ihres Geräts auch gesenkt werden, da Anwendungen möglicherweise Sensordaten missbrauchen.  Weitere Informationen zur Gerätesicherheit finden Sie in den häufig gestellten Fragen zur [hololens-Sicherheit](/hololens/hololens-faq-security).  

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
        <td>Kopf Verfolgungs Kameras</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Tiefe & IR-Kamera</td>
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

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>Aktivieren des Research-Modus (hololens First Gen und hololens 2)

Der Forschungs Modus ist eine Erweiterung des Entwicklermodus. Bevor Sie beginnen, müssen die Entwickler Funktionen des Geräts für den Zugriff auf die Einstellungen für den Research-Modus aktiviert werden: 

* Öffnen Sie das **Startmenü > Einstellungen** , und wählen Sie **Updates** aus.
* Wählen Sie **für Entwickler aus** , und aktivieren Sie **Entwicklermodus**.
* Scrollen Sie nach unten, und aktivieren Sie **Geräteportal**.

Nachdem die Entwickler Features aktiviert wurden, stellen Sie eine [Verbindung mit dem Geräte Portal](/windows/uwp/debug-test-perf/device-portal-hololens) her, um die Funktionen des Research-Modus zu aktivieren:

* Wechseln Sie im **Geräte Portal** zum **System > Research-Modus** .
* Wählen Sie **Zugriff auf Sensordaten Strom zulassen** aus.
* Starten Sie das Gerät über das **Power** -Menü Element oben auf der Seite neu.

Nachdem Sie das Gerät neu gestartet haben, können die Anwendungen, die über das **Geräte Portal** geladen werden, auf Datenströme im Forschungs Modus zugreifen.

![Registerkarte "Forschungs Modus" des hololens-Geräte Portals](images/ResearchModeDevPortal.png)<br>
*Fenster "Forschungs Modus" im hololens-Geräte Portal*

> [!IMPORTANT]
> Der Forschungs Modus für hololens 2 ist ab Build 19041,1364 verfügbar. Wenn Sie in einem früheren Build Zugriff benötigen, registrieren Sie sich für unser [Insider-Vorschau](/hololens/hololens-insider) Programm. Weitere Informationen finden Sie im [GitHub-Repository](https://github.com/microsoft/HoloLens2ForCV)für den Research-Modus.

### <a name="using-sensor-data-in-your-apps"></a>Verwenden von Sensordaten in ihren apps

Anwendungen können auf die Sensordaten Strom Daten auf die gleiche Weise zugreifen, [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) auf Foto-und Videokamera Datenströme zugreift. 

Alle APIs, die für die hololens-Entwicklung funktionieren, sind auch im Research-Modus verfügbar. Insbesondere weiß die Anwendung genau, wo sich hololens bei jeder Sensor Frame-Erfassungs Zeit in einem 6DOF-Raum befindet.

Wir haben Beispielanwendungen, die den Datenstrom Zugriff im Recherche Modus mit den systeminternen [und extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)und Aufzeichnungsdaten strömen veranschaulichen:
* [HoloLens (1. Generation)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>Support

Verwenden Sie für hololens (erste Generation) das [Problem Tracker](https://github.com/Microsoft/HololensForCV/issues) im Repository hololensforcv, um Feedback zu senden und bekannte Probleme nachzuverfolgen.

Verwenden Sie für hololens 2 das [Issue Tracker](https://github.com/microsoft/HoloLens2ForCV/issues) im Repository HoloLens2ForCV, um Feedback zu senden und bekannte Probleme nachzuverfolgen.

## <a name="see-also"></a>Weitere Informationen

* [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [Hololensforcv GitHub-Repository](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens2ForCV GitHub-Repository](https://github.com/microsoft/HoloLens2ForCV)
* [Verwenden des Windows-Geräteportals](using-the-windows-device-portal.md)