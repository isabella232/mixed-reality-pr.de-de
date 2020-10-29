---
title: Hololens Research-Modus
description: Mithilfe des Research-Modus auf hololens kann eine Anwendung auf wichtige Geräte Sensordaten Ströme (Tiefe, Umgebungs Überwachung und IR-Reflektivität) zugreifen.
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Research Mode, CV, RS4, Maschinelles sehen, Forschung, hololens, hololens 2
ms.openlocfilehash: 327ee932dce99a2559e406630611dcc3c69a0002
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684966"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="bef87-104">Hololens Research-Modus</span><span class="sxs-lookup"><span data-stu-id="bef87-104">HoloLens Research Mode</span></span>

<span data-ttu-id="bef87-105">Der Forschungs Modus wurde in den ersten hololens der Generation eingeführt, um den Zugriff auf die Schlüssel Sensoren auf dem Gerät zu erhalten, insbesondere für Forschungsanwendungen, die nicht für die Bereitstellung vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="bef87-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="bef87-106">Der Forschungs Modus für hololens 2 behält die Funktionen von hololens 1 bei und bietet Zugriff auf zusätzliche Streams:</span><span class="sxs-lookup"><span data-stu-id="bef87-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="bef87-107">**Sichtbare helle Umgebungs Überwachungskameras** : graue Kameras, die vom System für die Head-Nachverfolgung und die Zuordnungs Bildung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bef87-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="bef87-108">**Tiefe Kamera** – wird in zwei Modi betrieben:</span><span class="sxs-lookup"><span data-stu-id="bef87-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="bef87-109">Ahat, hohe Häufigkeit (45 fps), die für die Hand Verfolgung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bef87-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="bef87-110">Anders als bei der ersten Version des kurzthrow-Modus gibt ahat eine Pseudo Tiefe mit einem Phasen Umbruch über 1 Meter hinaus.</span><span class="sxs-lookup"><span data-stu-id="bef87-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="bef87-111">Lange throw-, Low-Frequency (1-5 fps)-Erkennung, die von der [räumlichen Zuordnung](../../design/spatial-mapping.md) verwendet wird</span><span class="sxs-lookup"><span data-stu-id="bef87-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="bef87-112">**Zwei Versionen des IR-Reflektivität-Streams** : werden von den hololens zum Berechnen der Tiefe verwendet.</span><span class="sxs-lookup"><span data-stu-id="bef87-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="bef87-113">Diese Bilder werden von Infrarot beleuchtet und sind von der Sichtbarkeit sichtbar.</span><span class="sxs-lookup"><span data-stu-id="bef87-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="bef87-114">Wenn Sie ein hololens 2 verwenden, haben Sie auch Zugriff auf die unten aufgeführten zusätzlichen Eingaben:</span><span class="sxs-lookup"><span data-stu-id="bef87-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="bef87-115">**Beschleunigungsmesser** – wird vom System verwendet, um die lineare Beschleunigung entlang der X-, Y-und Z-Achse und der Schweregrad zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="bef87-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="bef87-116">**Gyro** – wird vom System verwendet, um Drehungen zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="bef87-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="bef87-117">**Magnetometer** – wird vom System zum Schätzen der absoluten Ausrichtung verwendet.</span><span class="sxs-lookup"><span data-stu-id="bef87-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bef87-118">Der Research-Modus befindet sich derzeit in Public Preview.</span><span class="sxs-lookup"><span data-stu-id="bef87-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="bef87-119">![Screenshot der Recherche Modus-App](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="bef87-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="bef87-120">*Eine gemischte Realität-Erfassung einer Testanwendung, die die acht im Research-Modus verfügbaren Sensordaten Ströme anzeigt*</span><span class="sxs-lookup"><span data-stu-id="bef87-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="bef87-121">Verwendung</span><span class="sxs-lookup"><span data-stu-id="bef87-121">Usage</span></span>

<span data-ttu-id="bef87-122">Der Forschungs Modus wurde für akademische und Industrieexperten entwickelt, die neue Ideen in den Feldern Maschinelles Sehen und Robotik kennenlernen.</span><span class="sxs-lookup"><span data-stu-id="bef87-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="bef87-123">Sie ist nicht für Anwendungen gedacht, die in Unternehmensumgebungen bereitgestellt werden oder über die Microsoft Store oder andere Vertriebskanäle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="bef87-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="bef87-124">Außerdem bietet Microsoft keine Garantie dafür, dass der Forschungs Modus oder die entsprechende Funktionalität bei zukünftigen Hardware-oder Betriebssystemupdates unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="bef87-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="bef87-125">Dies sollte jedoch nicht daran hindern, ihn zum entwickeln und Testen neuer Ideen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bef87-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="bef87-126">Sicherheit und Leistung</span><span class="sxs-lookup"><span data-stu-id="bef87-126">Security and performance</span></span>

<span data-ttu-id="bef87-127">Beachten Sie, dass die Aktivierung des Research-Modus mehr Akkuleistung als die Verwendung der hololens 2 unter normalen Bedingungen beansprucht.</span><span class="sxs-lookup"><span data-stu-id="bef87-127">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="bef87-128">Dies gilt auch dann, wenn die Anwendung, die die Research Mode-Features verwendet, nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bef87-128">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="bef87-129">Wenn Sie diesen Modus aktivieren, kann die Gesamtsicherheit Ihres Geräts auch gesenkt werden, da Anwendungen möglicherweise Sensordaten missbrauchen.</span><span class="sxs-lookup"><span data-stu-id="bef87-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="bef87-130">Weitere Informationen zur Gerätesicherheit finden Sie in den häufig gestellten Fragen zur [hololens-Sicherheit](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="bef87-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="bef87-131">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="bef87-131">Device support</span></span>
<table><span data-ttu-id="bef87-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="bef87-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="bef87-133"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="bef87-133"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="bef87-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="bef87-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="bef87-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="bef87-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bef87-136">Kopf Verfolgungs Kameras</span><span class="sxs-lookup"><span data-stu-id="bef87-136">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="bef87-137">✔️</span><span class="sxs-lookup"><span data-stu-id="bef87-137">✔️</span></span></td>
        <td><span data-ttu-id="bef87-138">✔️</span><span class="sxs-lookup"><span data-stu-id="bef87-138">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bef87-139">Tiefe & IR-Kamera</span><span class="sxs-lookup"><span data-stu-id="bef87-139">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="bef87-140">✔️</span><span class="sxs-lookup"><span data-stu-id="bef87-140">✔️</span></span></td>
        <td><span data-ttu-id="bef87-141">✔️</span><span class="sxs-lookup"><span data-stu-id="bef87-141">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bef87-142">Beschleunigungsmesser</span><span class="sxs-lookup"><span data-stu-id="bef87-142">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="bef87-143">✔️</span><span class="sxs-lookup"><span data-stu-id="bef87-143">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bef87-144">Gyroskop</span><span class="sxs-lookup"><span data-stu-id="bef87-144">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="bef87-145">✔️</span><span class="sxs-lookup"><span data-stu-id="bef87-145">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bef87-146">Magnetometer</span><span class="sxs-lookup"><span data-stu-id="bef87-146">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="bef87-147">✔️</span><span class="sxs-lookup"><span data-stu-id="bef87-147">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="bef87-148">Aktivieren des Research-Modus (hololens 1. gen und hololens 2)</span><span class="sxs-lookup"><span data-stu-id="bef87-148">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="bef87-149">Der Forschungs Modus ist eine Erweiterung des Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="bef87-149">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="bef87-150">Bevor Sie beginnen, müssen die Entwickler Funktionen des Geräts für den Zugriff auf die Einstellungen für den Research-Modus aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="bef87-150">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="bef87-151">Öffnen Sie das **Startmenü > Einstellungen** , und wählen Sie **Updates** aus.</span><span class="sxs-lookup"><span data-stu-id="bef87-151">Open **Start Menu > Settings** and select **Updates** .</span></span>
* <span data-ttu-id="bef87-152">Wählen Sie **für Entwickler aus** , und aktivieren Sie **Entwicklermodus** .</span><span class="sxs-lookup"><span data-stu-id="bef87-152">Select **For Developers** and enable **Developer Mode** .</span></span>
* <span data-ttu-id="bef87-153">Scrollen Sie nach unten, und aktivieren Sie **Geräteportal** .</span><span class="sxs-lookup"><span data-stu-id="bef87-153">Scroll down and enable **Device Portal** .</span></span>

<span data-ttu-id="bef87-154">Nachdem die Entwickler Features aktiviert wurden, stellen Sie eine [Verbindung mit dem Geräte Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) her, um die Funktionen des Research-Modus zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="bef87-154">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="bef87-155">Wechseln Sie im **Geräte Portal** zum **System > Research-Modus** .</span><span class="sxs-lookup"><span data-stu-id="bef87-155">Go to **System > Research Mode** in the **Device Portal** .</span></span>
* <span data-ttu-id="bef87-156">Wählen Sie **Zugriff auf Sensordaten Strom zulassen** aus.</span><span class="sxs-lookup"><span data-stu-id="bef87-156">Select **Allow access to sensor stream** .</span></span>
* <span data-ttu-id="bef87-157">Starten Sie das Gerät über das **Power** -Menü Element oben auf der Seite neu.</span><span class="sxs-lookup"><span data-stu-id="bef87-157">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="bef87-158">Nachdem Sie das Gerät neu gestartet haben, können die Anwendungen, die über das **Geräte Portal** geladen werden, auf Datenströme im Forschungs Modus zugreifen.</span><span class="sxs-lookup"><span data-stu-id="bef87-158">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="bef87-159">![Registerkarte "Forschungs Modus" des hololens-Geräte Portals](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="bef87-159">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="bef87-160">*Fenster "Forschungs Modus" im hololens-Geräte Portal*</span><span class="sxs-lookup"><span data-stu-id="bef87-160">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bef87-161">Der Forschungs Modus für hololens 2 ist ab Build 19041,1356 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bef87-161">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="bef87-162">Wenn Sie in einem früheren Build Zugriff benötigen, registrieren Sie sich für unser [Insider-Vorschau](https://docs.microsoft.com/hololens/hololens-insider) Programm.</span><span class="sxs-lookup"><span data-stu-id="bef87-162">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="bef87-163">Verwenden von Sensordaten in ihren apps</span><span class="sxs-lookup"><span data-stu-id="bef87-163">Using sensor data in your apps</span></span>

<span data-ttu-id="bef87-164">Anwendungen können auf die Sensordaten Strom Daten auf die gleiche Weise zugreifen wie auf Foto-und Videokamera-Streams über [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="bef87-164">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="bef87-165">Alle APIs, die für die hololens-Entwicklung funktionieren, sind auch im Research-Modus verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bef87-165">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="bef87-166">Insbesondere weiß die Anwendung genau, wo sich hololens bei jeder Sensor Frame-Erfassungs Zeit in einem 6DOF-Raum befindet.</span><span class="sxs-lookup"><span data-stu-id="bef87-166">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="bef87-167">Sie finden Beispielanwendungen für den Zugriff auf die verschiedenen Stream-Datenströme, mithilfe der systeminternen Funktionen [und der extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)und durch Aufzeichnen von Streams in den entsprechenden Repos für Forschungs Modi:</span><span class="sxs-lookup"><span data-stu-id="bef87-167">You can find sample applications on accessing the various Research Mode streams, using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams in the respective Research Mode repos:</span></span>
* [<span data-ttu-id="bef87-168">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="bef87-168">HoloLens (1st gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="bef87-169">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bef87-169">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="bef87-170">Support</span><span class="sxs-lookup"><span data-stu-id="bef87-170">Support</span></span>

<span data-ttu-id="bef87-171">Verwenden Sie für hololens (1. Gen) das [Problem Tracker](https://github.com/Microsoft/HololensForCV/issues) im Repository hololensforcv, um Feedback zu senden und bekannte Probleme nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="bef87-171">For HoloLens (1st gen), please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="bef87-172">Verwenden Sie für hololens 2 das [Issue Tracker](https://github.com/microsoft/HoloLens2ForCV/issues) im Repository HoloLens2ForCV, um Feedback zu senden und bekannte Probleme nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="bef87-172">For HoloLens 2, please use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="bef87-173">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bef87-173">See also</span></span>

* [<span data-ttu-id="bef87-174">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="bef87-174">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="bef87-175">Hololensforcv GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="bef87-175">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="bef87-176">HoloLens2ForCV GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="bef87-176">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="bef87-177">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="bef87-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
