---
title: Referenz der Geräteportal-API
description: API-Referenz für das Windows-Geräte Portal auf hololens
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Hololens, Windows-Geräte Portal, API
ms.openlocfilehash: 6b8f99fbc6f1965639ceef218f5c516d2e6ba467
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683771"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="326c5-104">Referenz der Geräteportal-API</span><span class="sxs-lookup"><span data-stu-id="326c5-104">Device portal API reference</span></span>

<span data-ttu-id="326c5-105">Alles im [Windows-Geräte Portal](using-the-windows-device-portal.md) baut auf der Rest-API auf, mit der Sie auf die Daten zugreifen und Ihr Gerät Programm gesteuert steuern können.</span><span class="sxs-lookup"><span data-stu-id="326c5-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="326c5-106">App-Verlagerung</span><span class="sxs-lookup"><span data-stu-id="326c5-106">App deloyment</span></span>

<span data-ttu-id="326c5-107">**/API/APP/packagemanager/Package (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="326c5-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="326c5-108">Deinstalliert eine APP</span><span class="sxs-lookup"><span data-stu-id="326c5-108">Uninstalls an app</span></span>

<span data-ttu-id="326c5-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-109">Parameters</span></span>
* <span data-ttu-id="326c5-110">Package: der Dateiname des Pakets, das deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="326c5-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="326c5-111">**/API/APP/packagemanager/Package (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="326c5-112">Installiert eine APP</span><span class="sxs-lookup"><span data-stu-id="326c5-112">Installs an App</span></span>

<span data-ttu-id="326c5-113">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-113">Parameters</span></span>
* <span data-ttu-id="326c5-114">Package: der Dateiname des zu installierenden Pakets.</span><span class="sxs-lookup"><span data-stu-id="326c5-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="326c5-115">Payload</span><span class="sxs-lookup"><span data-stu-id="326c5-115">Payload</span></span>
* <span data-ttu-id="326c5-116">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="326c5-116">multi-part conforming http body</span></span>

<span data-ttu-id="326c5-117">**/API/APP/packagemanager/Packages (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="326c5-118">Hiermit wird die Liste der installierten apps auf dem System mit Details abgerufen.</span><span class="sxs-lookup"><span data-stu-id="326c5-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="326c5-119">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-119">Return data</span></span>
* <span data-ttu-id="326c5-120">Liste der installierten Pakete mit Details</span><span class="sxs-lookup"><span data-stu-id="326c5-120">List of installed packages with details</span></span>

<span data-ttu-id="326c5-121">**/API/APP/packagemanager/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="326c5-122">Hiermit wird der Status der Installation in Progress-App abgerufen.</span><span class="sxs-lookup"><span data-stu-id="326c5-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="326c5-123">Absturzabbildsammlung</span><span class="sxs-lookup"><span data-stu-id="326c5-123">Dump collection</span></span>

<span data-ttu-id="326c5-124">**/API/Debug/Dump/Usermode/CrashControl (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="326c5-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="326c5-125">Deaktiviert die Absturz Abbild Erfassung für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="326c5-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="326c5-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-126">Parameters</span></span>
* <span data-ttu-id="326c5-127">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="326c5-127">packageFullname : package name</span></span>

<span data-ttu-id="326c5-128">**/API/Debug/Dump/Usermode/CrashControl (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="326c5-129">Ruft Einstellungen für die Absturz Abbild Erfassung von Sideload-apps ab</span><span class="sxs-lookup"><span data-stu-id="326c5-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="326c5-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-130">Parameters</span></span>
* <span data-ttu-id="326c5-131">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="326c5-131">packageFullname : package name</span></span>

<span data-ttu-id="326c5-132">**/API/Debug/Dump/Usermode/CrashControl (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="326c5-133">Aktiviert und legt Sicherungs Steuerungseinstellungen für eine per Sideload übertragene App fest.</span><span class="sxs-lookup"><span data-stu-id="326c5-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="326c5-134">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-134">Parameters</span></span>
* <span data-ttu-id="326c5-135">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="326c5-135">packageFullname : package name</span></span>

<span data-ttu-id="326c5-136">**/API/Debug/Dump/Usermode/crashdump (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="326c5-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="326c5-137">Löscht einen Absturz Abbild für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="326c5-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="326c5-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-138">Parameters</span></span>
* <span data-ttu-id="326c5-139">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="326c5-139">packageFullname : package name</span></span>
* <span data-ttu-id="326c5-140">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="326c5-140">fileName : dump file name</span></span>

<span data-ttu-id="326c5-141">**/API/Debug/Dump/Usermode/crashdump (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="326c5-142">Ruft ein Absturz Abbild für eine per Sideload übertragene App ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="326c5-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-143">Parameters</span></span>
* <span data-ttu-id="326c5-144">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="326c5-144">packageFullname : package name</span></span>
* <span data-ttu-id="326c5-145">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="326c5-145">fileName : dump file name</span></span>

<span data-ttu-id="326c5-146">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-146">Return data</span></span>
* <span data-ttu-id="326c5-147">Dumpdatei.</span><span class="sxs-lookup"><span data-stu-id="326c5-147">Dump file.</span></span> <span data-ttu-id="326c5-148">Überprüfen mit WinDbg oder Visual Studio</span><span class="sxs-lookup"><span data-stu-id="326c5-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="326c5-149">**/API/Debug/Dump/Usermode/Dumps (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="326c5-150">Gibt eine Liste aller Absturz Abbilder für Sideload-apps zurück.</span><span class="sxs-lookup"><span data-stu-id="326c5-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="326c5-151">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-151">Return data</span></span>
* <span data-ttu-id="326c5-152">Liste der Absturz Abbilder pro Seite geladener apps</span><span class="sxs-lookup"><span data-stu-id="326c5-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="326c5-153">ETW</span><span class="sxs-lookup"><span data-stu-id="326c5-153">ETW</span></span>

<span data-ttu-id="326c5-154">**/API/etw/Providers (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="326c5-155">Listet registrierte Anbieter auf.</span><span class="sxs-lookup"><span data-stu-id="326c5-155">Enumerates registered providers</span></span>

<span data-ttu-id="326c5-156">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-156">Return data</span></span>
* <span data-ttu-id="326c5-157">Liste der Anbieter, Anzeige Name und GUID</span><span class="sxs-lookup"><span data-stu-id="326c5-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="326c5-158">**/API/etw/Session/Realtime (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="326c5-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="326c5-159">Erstellt eine ETW-Sitzung in Echtzeit. verwaltet über einen WebSocket.</span><span class="sxs-lookup"><span data-stu-id="326c5-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="326c5-160">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-160">Return data</span></span>
* <span data-ttu-id="326c5-161">ETW-Ereignisse von aktivierten Anbietern</span><span class="sxs-lookup"><span data-stu-id="326c5-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="326c5-162">Holographic – Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="326c5-162">Holographic OS</span></span>

<span data-ttu-id="326c5-163">**/API/Holographic/OS/etw/customproviders (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="326c5-164">Gibt eine Liste von hololens-spezifischen etw-Anbietern zurück, die nicht beim System registriert sind.</span><span class="sxs-lookup"><span data-stu-id="326c5-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="326c5-165">**/API/Holographic/OS/Services (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="326c5-166">Gibt die Zustände aller Dienste zurück, die ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-166">Returns the states of all services running.</span></span>

<span data-ttu-id="326c5-167">**/API/Holographic/OS/Settings/IPD (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="326c5-168">Ruft die gespeicherte IPD (interpupranäre Entfernung) in Millimeter ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="326c5-169">**/API/Holographic/OS/Settings/IPD (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="326c5-170">Legt die IPD fest.</span><span class="sxs-lookup"><span data-stu-id="326c5-170">Sets the IPD</span></span>

<span data-ttu-id="326c5-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-171">Parameters</span></span>
* <span data-ttu-id="326c5-172">IPD: neuer IPD-Wert, der in Millimeter festgelegt werden soll</span><span class="sxs-lookup"><span data-stu-id="326c5-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="326c5-173">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="326c5-174">Abrufen der HTTPS-Anforderungen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="326c5-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="326c5-175">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="326c5-176">Legt die HTTPS-Anforderungen für das Geräte Portal fest.</span><span class="sxs-lookup"><span data-stu-id="326c5-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="326c5-177">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-177">Parameters</span></span>
* <span data-ttu-id="326c5-178">erforderlich: Ja, Nein oder Standard</span><span class="sxs-lookup"><span data-stu-id="326c5-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="326c5-179">Holografische Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="326c5-179">Holographic Perception</span></span>

<span data-ttu-id="326c5-180">**/API/Holographic/perception/Client (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="326c5-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="326c5-181">Akzeptiert WebSocket-Upgrades und führt einen perception-Client aus, der Updates bei 30 fps sendet.</span><span class="sxs-lookup"><span data-stu-id="326c5-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="326c5-182">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-182">Parameters</span></span>
* <span data-ttu-id="326c5-183">clientmode: "aktiv" erzwingt den visuellen Überwachungsmodus, wenn er nicht passiv festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="326c5-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="326c5-184">Holographic-Therme</span><span class="sxs-lookup"><span data-stu-id="326c5-184">Holographic Thermal</span></span>

<span data-ttu-id="326c5-185">**/API/Holographic/Thermal/Stage (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="326c5-186">Die wärmestufe des Geräts erhalten (0 normal, 1 warm, 2 kritisch)</span><span class="sxs-lookup"><span data-stu-id="326c5-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="326c5-187">Karten-Manager</span><span class="sxs-lookup"><span data-stu-id="326c5-187">Map Manager</span></span>

<span data-ttu-id="326c5-188">**/API/Holographic/mapmanager/mapFiles (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="326c5-189">Ruft die Liste der verfügbaren Zuordnungs Dateien (. MapX) ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="326c5-190">**/API/Holographic/mapmanager/anchorFiles (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="326c5-191">Ruft die Liste der verfügbaren Anker Dateien (. ancx) ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="326c5-192">**/API/Holographic/mapmanager/srdbFiles (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="326c5-193">Ruft die Liste der verfügbaren Datenbankdateien für die räumliche Wiederherstellung (. SRDB) ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="326c5-194">**/API/Holographic/mapmanager/getanchors (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="326c5-195">Ruft die Liste der persistenten Anker für den aktuellen Benutzer ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="326c5-196">Dateien herunterladen/hochladen/löschen</span><span class="sxs-lookup"><span data-stu-id="326c5-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="326c5-197">**/API/Holographic/mapmanager/Download (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="326c5-198">Lädt eine Karten-, Anker-oder räumliche Datenbankdatei herunter.</span><span class="sxs-lookup"><span data-stu-id="326c5-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="326c5-199">Die Datei muss zuvor hochgeladen oder exportiert worden sein.</span><span class="sxs-lookup"><span data-stu-id="326c5-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="326c5-200">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-200">Parameters</span></span>
* <span data-ttu-id="326c5-201">Dateiname: Name der herunter zuladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="326c5-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="326c5-202">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="326c5-203">**/API/Holographic/mapmanager/Upload (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="326c5-204">Lädt eine Karten-, Anker-oder räumliche Datenbankdatei hoch.</span><span class="sxs-lookup"><span data-stu-id="326c5-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="326c5-205">Nachdem eine Datei hochgeladen wurde, kann Sie später importiert werden, damit Sie vom System verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="326c5-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="326c5-206">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-206">Parameters</span></span>
* <span data-ttu-id="326c5-207">file: Name der hoch zuladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="326c5-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="326c5-208">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="326c5-209">**/API/Holographic/mapmanager/Delete (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="326c5-210">Löscht eine Karten-, Anker-oder räumliche Datenbankdatei.</span><span class="sxs-lookup"><span data-stu-id="326c5-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="326c5-211">Die Datei muss zuvor hochgeladen oder exportiert worden sein.</span><span class="sxs-lookup"><span data-stu-id="326c5-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="326c5-212">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-212">Parameters</span></span>
* <span data-ttu-id="326c5-213">Dateiname: Name der zu löschenden Datei.</span><span class="sxs-lookup"><span data-stu-id="326c5-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="326c5-214">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="326c5-215">Exportieren</span><span class="sxs-lookup"><span data-stu-id="326c5-215">Export</span></span>

<span data-ttu-id="326c5-216">**/API/Holographic/mapmanager/Export (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="326c5-217">Exportiert die Karte, die derzeit vom System verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="326c5-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="326c5-218">Nach dem Export kann es heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="326c5-219">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="326c5-220">**/API/Holographic/mapmanager/exportanchors (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="326c5-221">Exportiert die Karte, die derzeit vom System verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="326c5-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="326c5-222">Nach dem Export kann es heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="326c5-223">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="326c5-224">**/API/Holographic/mapmanager/exportmapandanchors (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="326c5-225">Exportiert die Karte und die Anker, die zurzeit vom System verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="326c5-226">Nachdem Sie exportiert haben, können Sie heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="326c5-227">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="326c5-228">**/API/Holographic/mapmanager/exportmapandspatialmappingdb (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="326c5-229">Exportiert die derzeit vom System verwendete Map-und räumliche Datenbank für die Wiederherstellung.</span><span class="sxs-lookup"><span data-stu-id="326c5-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="326c5-230">Nachdem Sie exportiert wurden, können Sie heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="326c5-231">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="326c5-232">importieren</span><span class="sxs-lookup"><span data-stu-id="326c5-232">Import</span></span>

<span data-ttu-id="326c5-233">**/API/Holographic/mapmanager/Import (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="326c5-234">Gibt dem System an, welche Zuordnung verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="326c5-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="326c5-235">Kann für exportierte oder hochgeladene Dateien aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="326c5-236">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-236">Parameters</span></span>
* <span data-ttu-id="326c5-237">Dateiname: Name der zu verwendenden Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="326c5-238">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="326c5-239">**/API/Holographic/mapmanager/importanchors (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="326c5-240">Gibt dem System an, welche Anker aktuell verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="326c5-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="326c5-241">Kann für exportierte oder hochgeladene Dateien aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="326c5-242">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-242">Parameters</span></span>
* <span data-ttu-id="326c5-243">Dateiname: Name der zu verwendenden Anker.</span><span class="sxs-lookup"><span data-stu-id="326c5-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="326c5-244">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="326c5-245">**/API/Holographic/mapmanager/importspatialmappingdb (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="326c5-246">Gibt an, dass das System zurzeit verwendet werden soll, welche räumliche Datenbank verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="326c5-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="326c5-247">Kann für exportierte oder hochgeladene Dateien aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="326c5-248">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-248">Parameters</span></span>
* <span data-ttu-id="326c5-249">Dateiname: Name der zu verwendenden DB-Daten Bank Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="326c5-250">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="326c5-251">Andere</span><span class="sxs-lookup"><span data-stu-id="326c5-251">Other</span></span>

<span data-ttu-id="326c5-252">**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="326c5-253">Setzen Sie das System auf die Karte, die Anker und die räumliche Wiederherstellung zurück.</span><span class="sxs-lookup"><span data-stu-id="326c5-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="326c5-254">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="326c5-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="326c5-255">**/API/Holographic/mapmanager/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="326c5-256">Ruft den Status des Systems ab, einschließlich der Zuordnungs-, Anker-und räumlichen Datenbankdateien, die zuletzt importiert wurden.</span><span class="sxs-lookup"><span data-stu-id="326c5-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="326c5-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="326c5-257">Mixed Reality Capture</span></span>

<span data-ttu-id="326c5-258">**/API/Holographic/MRC/File (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="326c5-259">Hiermit wird eine gemischte Reality-Datei vom Gerät heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="326c5-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="326c5-260">Verwenden Sie den OP = Stream-Abfrage Parameter für das Streaming.</span><span class="sxs-lookup"><span data-stu-id="326c5-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="326c5-261">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-261">Parameters</span></span>
* <span data-ttu-id="326c5-262">Dateiname: Name, hex64-codiert, der einzurufenden Videodatei</span><span class="sxs-lookup"><span data-stu-id="326c5-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="326c5-263">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="326c5-263">op : stream</span></span>

<span data-ttu-id="326c5-264">**/API/Holographic/MRC/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="326c5-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="326c5-265">Löscht eine gemischte Reality-Aufzeichnung auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="326c5-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="326c5-266">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-266">Parameters</span></span>
* <span data-ttu-id="326c5-267">Dateiname: Name, hex64-codiert, der zu löschenden Datei</span><span class="sxs-lookup"><span data-stu-id="326c5-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="326c5-268">**/API/Holographic/MRC/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="326c5-269">Gibt die Liste der Mixed Reality-Dateien zurück, die auf dem Gerät gespeichert sind</span><span class="sxs-lookup"><span data-stu-id="326c5-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="326c5-270">**/API/Holographic/MRC/Photo (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="326c5-271">Nimmt ein gemischtes Reality-Foto und erstellt eine Datei auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="326c5-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="326c5-272">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-272">Parameters</span></span>
* <span data-ttu-id="326c5-273">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="326c5-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="326c5-274">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="326c5-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="326c5-275">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="326c5-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="326c5-276">**/API/Holographic/MRC/Settings (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="326c5-277">Ruft die Standardeinstellungen für die gemischte Realität-Erfassung ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="326c5-278">**/API/Holographic/MRC/Settings (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="326c5-279">Legt die Standardeinstellungen für die gemischte Reality-Erfassung fest.</span><span class="sxs-lookup"><span data-stu-id="326c5-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="326c5-280">Einige dieser Einstellungen werden auf das MRC-Foto und die Video Erfassung des Systems angewendet.</span><span class="sxs-lookup"><span data-stu-id="326c5-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="326c5-281">**/API/Holographic/MRC/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="326c5-282">Ruft den Zustand der Mixed Reality-Erfassung im Windows-Geräte Portal ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="326c5-283">***Antwort***</span><span class="sxs-lookup"><span data-stu-id="326c5-283">***Response***</span></span>

<span data-ttu-id="326c5-284">Die Antwort enthält eine JSON-Eigenschaft, die angibt, ob das Windows-Geräte Portal Videos aufzeichnet.</span><span class="sxs-lookup"><span data-stu-id="326c5-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="326c5-285">**/API/Holographic/MRC/Thumbnail (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-285">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="326c5-286">Ruft das Miniaturbild für die angegebene Datei ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="326c5-287">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-287">Parameters</span></span>
* <span data-ttu-id="326c5-288">Dateiname: Name, hex64-codiert, der Datei, für die die Miniaturansicht angefordert wird</span><span class="sxs-lookup"><span data-stu-id="326c5-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="326c5-289">**/API/Holographic/MRC/Video/Control/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="326c5-290">Startet eine gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="326c5-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="326c5-291">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-291">Parameters</span></span>
* <span data-ttu-id="326c5-292">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="326c5-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="326c5-293">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="326c5-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="326c5-294">MIC: Mikrofon erfassen: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="326c5-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="326c5-295">Loopback: App-Audioerfassung: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="326c5-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="326c5-296">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="326c5-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="326c5-297">Vstab: (nur hololens 2) Videostabilisierung aktivieren: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="326c5-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="326c5-298">vstabbuffer: (hololens 2), Video Stabilisierungs Puffer Latenz: 0 bis 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="326c5-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="326c5-299">**/API/Holographic/MRC/Video/Control/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="326c5-300">Beendet die aktuelle gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="326c5-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="326c5-301">Streaming mit gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="326c5-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="326c5-302">Hololens unterstützt die Live Vorschau von Mixed Reality über einen segmentierten Download einer fragmentierten MP4-Datei.</span><span class="sxs-lookup"><span data-stu-id="326c5-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="326c5-303">Gemischte Reality-Streams verwenden denselben Satz von Parametern, um zu steuern, was aufgezeichnet wird:</span><span class="sxs-lookup"><span data-stu-id="326c5-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="326c5-304">hololens: Erfassungs holograms: true oder false</span><span class="sxs-lookup"><span data-stu-id="326c5-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="326c5-305">PV: Erfassen der PV-Kamera: true oder false</span><span class="sxs-lookup"><span data-stu-id="326c5-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="326c5-306">MIC: Mikrofon erfassen: true oder false</span><span class="sxs-lookup"><span data-stu-id="326c5-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="326c5-307">Loopback: App-Audioerfassung: true oder false</span><span class="sxs-lookup"><span data-stu-id="326c5-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="326c5-308">Wenn keines dieser Angaben angegeben ist: holograms, Foto-/Videokamera und App-Audiodaten werden aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="326c5-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="326c5-309">Wenn eine Angabe festgelegt ist: die nicht angegebenen Parameter werden standardmäßig auf false festgelegt.</span><span class="sxs-lookup"><span data-stu-id="326c5-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="326c5-310">Optionale Parameter (nur hololens 2)</span><span class="sxs-lookup"><span data-stu-id="326c5-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="326c5-311">Renderfromcamera: Rendering aus Perspektive der Foto-/Videokamera: true oder false (Standardwert ist true)</span><span class="sxs-lookup"><span data-stu-id="326c5-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="326c5-312">Vstab: Videostabilisierung aktivieren: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="326c5-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="326c5-313">vstabbuffer: Puffer Wartezeit für Videostabilisierung: zwischen 0 und 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="326c5-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="326c5-314">**/API/Holographic/Stream/live.mp4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="326c5-315">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="326c5-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="326c5-316">**/API/Holographic/Stream/live_high.mp4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="326c5-317">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="326c5-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="326c5-318">**/API/Holographic/Stream/live_med.mp4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="326c5-319">Ein 854x480p 30 fps 2.5 MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="326c5-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="326c5-320">**/API/Holographic/Stream/live_low.mp4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="326c5-321">Ein 428x240 p 15fps 0.6-MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="326c5-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="326c5-322">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="326c5-322">Networking</span></span>

<span data-ttu-id="326c5-323">**/API/Networking/ipconfig (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="326c5-324">Ruft die aktuelle IP-Konfiguration ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="326c5-325">Betriebssysteminformationen</span><span class="sxs-lookup"><span data-stu-id="326c5-325">OS Information</span></span>

<span data-ttu-id="326c5-326">**/API/OS/Info (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="326c5-327">Ruft Betriebssysteminformationen ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-327">Gets operating system information</span></span>

<span data-ttu-id="326c5-328">**/API/OS/MachineName (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="326c5-329">Ruft den Computernamen ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-329">Gets the machine name</span></span>

<span data-ttu-id="326c5-330">**/API/OS/MachineName (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="326c5-331">Legt den Computernamen fest.</span><span class="sxs-lookup"><span data-stu-id="326c5-331">Sets the machine name</span></span>

<span data-ttu-id="326c5-332">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-332">Parameters</span></span>
* <span data-ttu-id="326c5-333">Name: neuer Computername, hex64-codiert, festgelegt auf</span><span class="sxs-lookup"><span data-stu-id="326c5-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="326c5-334">Wahrnehmungs Simulations-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="326c5-334">Perception Simulation Control</span></span>

<span data-ttu-id="326c5-335">**/API/Holographic/Simulation/Control/Mode (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="326c5-336">Simulationsmodus erhalten</span><span class="sxs-lookup"><span data-stu-id="326c5-336">Get the simulation mode</span></span>

<span data-ttu-id="326c5-337">**/API/Holographic/Simulation/Control/Mode (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="326c5-338">Festlegen des Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="326c5-338">Set the simulation mode</span></span>

<span data-ttu-id="326c5-339">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-339">Parameters</span></span>
* <span data-ttu-id="326c5-340">Mode: Simulationsmodus: Standard, Simulation, Remote, Legacy</span><span class="sxs-lookup"><span data-stu-id="326c5-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="326c5-341">**/API/Holographic/Simulation/Control/Stream (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="326c5-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="326c5-342">Löscht einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="326c5-342">Delete a control stream.</span></span>

<span data-ttu-id="326c5-343">**/API/Holographic/Simulation/Control/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="326c5-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="326c5-344">Öffnen Sie eine websocketverbindung für einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="326c5-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="326c5-345">**/API/Holographic/Simulation/Control/Stream (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="326c5-346">Erstellen Sie einen Steuerungsdaten Strom (Priorität ist erforderlich), oder stellen Sie Daten in einem erstellten Stream bereit (streamid erforderlich).</span><span class="sxs-lookup"><span data-stu-id="326c5-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="326c5-347">Es wird erwartet, dass für die Daten der Typ "Application/Octett-Stream" festgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="326c5-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="326c5-348">**/API/Holographic/Simulation/Display/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="326c5-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="326c5-349">Fordern Sie einen Simulations Videostream mit dem Inhalt an, der im Simulationsmodus für die System Anzeige gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="326c5-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="326c5-350">Anfänglich wird ein einfacher Format Deskriptor Header gesendet, gefolgt von H. 264-codierten Texturen, denen jeweils ein Header vorangestellt ist, der den Augen Index und die Textur Größe angibt.</span><span class="sxs-lookup"><span data-stu-id="326c5-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="326c5-351">Wiedergabe von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="326c5-351">Perception Simulation Playback</span></span>

<span data-ttu-id="326c5-352">**/API/Holographic/Simulation/Playback/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="326c5-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="326c5-353">Löschen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-353">Delete a recording.</span></span>

<span data-ttu-id="326c5-354">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-354">Parameters</span></span>
* <span data-ttu-id="326c5-355">Aufzeichnung: Name der zu löschenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="326c5-356">**/API/Holographic/Simulation/Playback/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="326c5-357">Hochladen einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-357">Upload a recording.</span></span>

<span data-ttu-id="326c5-358">**/API/Holographic/Simulation/Playback/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="326c5-359">Alle Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="326c5-359">Get all recordings.</span></span>

<span data-ttu-id="326c5-360">**/API/Holographic/Simulation/Playback/Session (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="326c5-361">Gibt den aktuellen Wiedergabe Zustand einer Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="326c5-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="326c5-362">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-362">Parameters</span></span>
* <span data-ttu-id="326c5-363">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-363">recording : Name of recording.</span></span>

<span data-ttu-id="326c5-364">**/API/Holographic/Simulation/Playback/Session/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="326c5-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="326c5-365">Entladen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-365">Unload a recording.</span></span>

<span data-ttu-id="326c5-366">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-366">Parameters</span></span>
* <span data-ttu-id="326c5-367">Aufzeichnung: Name der zu entladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="326c5-368">**/API/Holographic/Simulation/Playback/Session/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="326c5-369">Laden Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-369">Load a recording.</span></span>

<span data-ttu-id="326c5-370">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-370">Parameters</span></span>
* <span data-ttu-id="326c5-371">Aufzeichnung: Name der zu ladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="326c5-372">**/API/Holographic/Simulation/Playback/Session/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="326c5-373">Alle geladenen Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="326c5-373">Get all loaded recordings.</span></span>

<span data-ttu-id="326c5-374">**/API/Holographic/Simulation/Playback/Session/Pause (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="326c5-375">Hält eine Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="326c5-375">Pause a recording.</span></span>

<span data-ttu-id="326c5-376">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-376">Parameters</span></span>
* <span data-ttu-id="326c5-377">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-377">recording : Name of recording.</span></span>

<span data-ttu-id="326c5-378">**/API/Holographic/Simulation/Playback/Session/Play (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="326c5-379">Wiedergabe einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-379">Play a recording.</span></span>

<span data-ttu-id="326c5-380">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-380">Parameters</span></span>
* <span data-ttu-id="326c5-381">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-381">recording : Name of recording.</span></span>

<span data-ttu-id="326c5-382">**/API/Holographic/Simulation/Playback/Session/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="326c5-383">Beendet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-383">Stop a recording.</span></span>

<span data-ttu-id="326c5-384">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-384">Parameters</span></span>
* <span data-ttu-id="326c5-385">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-385">recording : Name of recording.</span></span>

<span data-ttu-id="326c5-386">**/API/Holographic/Simulation/Playback/Session/Types (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="326c5-387">Datentypen in einer geladenen Aufzeichnung erhalten.</span><span class="sxs-lookup"><span data-stu-id="326c5-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="326c5-388">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-388">Parameters</span></span>
* <span data-ttu-id="326c5-389">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="326c5-390">Erfassung von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="326c5-390">Perception Simulation Recording</span></span>

<span data-ttu-id="326c5-391">**/API/Holographic/Simulation/Recording/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="326c5-392">Startet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-392">Start a recording.</span></span> <span data-ttu-id="326c5-393">Nur eine einzelne Aufzeichnung kann gleichzeitig aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="326c5-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="326c5-394">Eine der Köpfe, Hände, spatialmapping oder Umgebung muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="326c5-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="326c5-395">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-395">Parameters</span></span>
* <span data-ttu-id="326c5-396">Head: Legen Sie auf 1 fest, um Head-Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="326c5-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="326c5-397">Hands: wird auf 1 festgelegt, um die Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="326c5-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="326c5-398">spatialmapping: auf 1 festgelegt, um die räumliche Zuordnung aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="326c5-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="326c5-399">Umgebung: Legen Sie auf 1 fest, um Umgebungs Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="326c5-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="326c5-400">Name: der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="326c5-400">name : Name of the recording.</span></span>
* <span data-ttu-id="326c5-401">singlespatialmappingframe: wird auf 1 festgelegt, um nur einen einzelnen räumlichen zuordnungsframe aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="326c5-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="326c5-402">**/API/Holographic/Simulation/Recording/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="326c5-403">Aufzeichnungsstatus erhalten.</span><span class="sxs-lookup"><span data-stu-id="326c5-403">Get recording state.</span></span>

<span data-ttu-id="326c5-404">**/API/Holographic/Simulation/Recording/Stop (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="326c5-405">Hält die aktuelle Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="326c5-405">Stop the current recording.</span></span> <span data-ttu-id="326c5-406">Die Aufzeichnung wird als Datei zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="326c5-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="326c5-407">Leistungsdaten</span><span class="sxs-lookup"><span data-stu-id="326c5-407">Performance data</span></span>

<span data-ttu-id="326c5-408">**/API/ResourceManager/Processes (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="326c5-409">Gibt die Liste der laufenden Prozesse mit Details zurück.</span><span class="sxs-lookup"><span data-stu-id="326c5-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="326c5-410">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-410">Return data</span></span>
* <span data-ttu-id="326c5-411">JSON mit einer Liste der Prozesse und Details für jeden Prozess</span><span class="sxs-lookup"><span data-stu-id="326c5-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="326c5-412">**/API/ResourceManager/systemperf (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="326c5-413">Gibt die System Leistungsstatistik (e/a-Lese-/Schreibvorgänge, Speicher Statistiken usw.) zurück.</span><span class="sxs-lookup"><span data-stu-id="326c5-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="326c5-414">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-414">Return data</span></span>
* <span data-ttu-id="326c5-415">JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a</span><span class="sxs-lookup"><span data-stu-id="326c5-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="326c5-416">Power</span><span class="sxs-lookup"><span data-stu-id="326c5-416">Power</span></span>

<span data-ttu-id="326c5-417">**/API/Power/Battery (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="326c5-418">Ruft den aktuellen Akku Zustand ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-418">Gets the current battery state</span></span>

<span data-ttu-id="326c5-419">**/API/Power/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="326c5-420">Prüft, ob sich das System in einem niedrigen Energiezustand befindet</span><span class="sxs-lookup"><span data-stu-id="326c5-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="326c5-421">Remotesteuerung</span><span class="sxs-lookup"><span data-stu-id="326c5-421">Remote Control</span></span>

<span data-ttu-id="326c5-422">**/API/Control/Restart (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="326c5-423">Startet das Zielgerät neu.</span><span class="sxs-lookup"><span data-stu-id="326c5-423">Restarts the target device</span></span>

<span data-ttu-id="326c5-424">**/API/Control/Shutdown (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="326c5-425">Fährt das Zielgerät herunter.</span><span class="sxs-lookup"><span data-stu-id="326c5-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="326c5-426">Task-Manager</span><span class="sxs-lookup"><span data-stu-id="326c5-426">Task Manager</span></span>

<span data-ttu-id="326c5-427">**/API/Taskmanager/app (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="326c5-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="326c5-428">Beendet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="326c5-428">Stops a modern app</span></span>

<span data-ttu-id="326c5-429">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-429">Parameters</span></span>
* <span data-ttu-id="326c5-430">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="326c5-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="326c5-431">forcestop: erzwingen, dass alle Prozesse beendet werden (= yes)</span><span class="sxs-lookup"><span data-stu-id="326c5-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="326c5-432">**/API/Taskmanager/app (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="326c5-433">Startet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="326c5-433">Starts a modern app</span></span>

<span data-ttu-id="326c5-434">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-434">Parameters</span></span>
* <span data-ttu-id="326c5-435">AppID: Praid der zu startenden APP, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="326c5-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="326c5-436">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="326c5-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="326c5-437">WiFi-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="326c5-437">WiFi Management</span></span>

<span data-ttu-id="326c5-438">**/API/WiFi/Interfaces (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="326c5-439">Listet drahtlose Netzwerkschnittstellen auf.</span><span class="sxs-lookup"><span data-stu-id="326c5-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="326c5-440">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-440">Return data</span></span>
* <span data-ttu-id="326c5-441">Liste der drahtlos Schnittstellen mit Details (GUID, Beschreibung usw.)</span><span class="sxs-lookup"><span data-stu-id="326c5-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="326c5-442">**/API/WiFi/Network (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="326c5-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="326c5-443">Löscht ein Profil, das einem Netzwerk in einer angegebenen Schnittstelle zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="326c5-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="326c5-444">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-444">Parameters</span></span>
* <span data-ttu-id="326c5-445">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="326c5-445">interface : network interface guid</span></span>
* <span data-ttu-id="326c5-446">Profil: Profilname</span><span class="sxs-lookup"><span data-stu-id="326c5-446">profile : profile name</span></span>

<span data-ttu-id="326c5-447">**/API/WiFi/Networks (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="326c5-448">Listet drahtlose Netzwerke auf der angegebenen Netzwerkschnittstelle auf.</span><span class="sxs-lookup"><span data-stu-id="326c5-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="326c5-449">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-449">Parameters</span></span>
* <span data-ttu-id="326c5-450">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="326c5-450">interface : network interface guid</span></span>

<span data-ttu-id="326c5-451">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-451">Return data</span></span>
* <span data-ttu-id="326c5-452">Liste der Drahtlos Netzwerke, die sich auf der Netzwerkschnittstelle befinden, mit Details</span><span class="sxs-lookup"><span data-stu-id="326c5-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="326c5-453">**/API/WiFi/Network (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="326c5-454">Stellt eine Verbindung mit einem Netzwerk auf der angegebenen Schnittstelle her oder trennt es.</span><span class="sxs-lookup"><span data-stu-id="326c5-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="326c5-455">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-455">Parameters</span></span>
* <span data-ttu-id="326c5-456">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="326c5-456">interface : network interface guid</span></span>
* <span data-ttu-id="326c5-457">SSID: SSID, hex64-codiert, um eine Verbindung herzustellen</span><span class="sxs-lookup"><span data-stu-id="326c5-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="326c5-458">OP: verbinden oder trennen</span><span class="sxs-lookup"><span data-stu-id="326c5-458">op : connect or disconnect</span></span>
* <span data-ttu-id="326c5-459">kreateprofile: Ja oder Nein</span><span class="sxs-lookup"><span data-stu-id="326c5-459">createprofile : yes or no</span></span>
* <span data-ttu-id="326c5-460">Schlüssel: gemeinsam verwendeter Schlüssel, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="326c5-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="326c5-461">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="326c5-461">Windows Performance Recorder</span></span>

<span data-ttu-id="326c5-462">**/API/WPR/customtrace (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="326c5-463">Lädt ein WPR-Profil hoch und startet die Ablauf Verfolgung mithilfe des hochgeladenen Profils.</span><span class="sxs-lookup"><span data-stu-id="326c5-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="326c5-464">Payload</span><span class="sxs-lookup"><span data-stu-id="326c5-464">Payload</span></span>
* <span data-ttu-id="326c5-465">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="326c5-465">multi-part conforming http body</span></span>

<span data-ttu-id="326c5-466">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-466">Return data</span></span>
* <span data-ttu-id="326c5-467">Gibt den WPR-Sitzungsstatus zurück.</span><span class="sxs-lookup"><span data-stu-id="326c5-467">Returns the WPR session status.</span></span>

<span data-ttu-id="326c5-468">**/API/WPR/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="326c5-469">Ruft den Status der WPR-Sitzung ab.</span><span class="sxs-lookup"><span data-stu-id="326c5-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="326c5-470">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-470">Return data</span></span>
* <span data-ttu-id="326c5-471">WPR-Sitzungs Status.</span><span class="sxs-lookup"><span data-stu-id="326c5-471">WPR session status.</span></span>

<span data-ttu-id="326c5-472">**/API/WPR/Trace (Get)**</span><span class="sxs-lookup"><span data-stu-id="326c5-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="326c5-473">Beendet eine WPR-Ablauf Verfolgungs Sitzung (Leistung).</span><span class="sxs-lookup"><span data-stu-id="326c5-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="326c5-474">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-474">Return data</span></span>
* <span data-ttu-id="326c5-475">Gibt die ETL-Ablauf Verfolgungs Datei zurück.</span><span class="sxs-lookup"><span data-stu-id="326c5-475">Returns the trace ETL file</span></span>

<span data-ttu-id="326c5-476">**/API/WPR/Trace (Post)**</span><span class="sxs-lookup"><span data-stu-id="326c5-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="326c5-477">Startet eine Ablauf Verfolgungs Sitzung für WPR (Leistung).</span><span class="sxs-lookup"><span data-stu-id="326c5-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="326c5-478">Parameter</span><span class="sxs-lookup"><span data-stu-id="326c5-478">Parameters</span></span>
* <span data-ttu-id="326c5-479">Profil: Profilname.</span><span class="sxs-lookup"><span data-stu-id="326c5-479">profile : Profile name.</span></span> <span data-ttu-id="326c5-480">Verfügbare Profile werden in perfprofiles/profiles.jsgespeichert.</span><span class="sxs-lookup"><span data-stu-id="326c5-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="326c5-481">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="326c5-481">Return data</span></span>
* <span data-ttu-id="326c5-482">Beim Start wird der WPR-Sitzungs Status zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="326c5-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="326c5-483">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="326c5-483">See also</span></span>
* [<span data-ttu-id="326c5-484">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="326c5-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="326c5-485">API-Referenz für den Geräte Portal (UWP)</span><span class="sxs-lookup"><span data-stu-id="326c5-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
