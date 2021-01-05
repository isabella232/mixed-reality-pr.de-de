---
title: Referenz der Geräteportal-API
description: API-Referenz für das Windows-Geräte Portal auf hololens
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Hololens, Windows-Geräte Portal, API, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: c705ce65971042ab41befed9c6813dc797b61fc0
ms.sourcegitcommit: 084b1da9d7b435394b38d6152a2f9aee7a74aa2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/29/2020
ms.locfileid: "97804429"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="71571-104">Referenz der Geräteportal-API</span><span class="sxs-lookup"><span data-stu-id="71571-104">Device portal API reference</span></span>

<span data-ttu-id="71571-105">Alles im [Windows-Geräte Portal](using-the-windows-device-portal.md) baut auf der Rest-API auf, mit der Sie auf die Daten zugreifen und Ihr Gerät Programm gesteuert steuern können.</span><span class="sxs-lookup"><span data-stu-id="71571-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="71571-106">App-Verlagerung</span><span class="sxs-lookup"><span data-stu-id="71571-106">App deloyment</span></span>

<span data-ttu-id="71571-107">**/API/APP/packagemanager/Package (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="71571-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="71571-108">Deinstalliert eine APP</span><span class="sxs-lookup"><span data-stu-id="71571-108">Uninstalls an app</span></span>

<span data-ttu-id="71571-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-109">Parameters</span></span>
* <span data-ttu-id="71571-110">Package: der Dateiname des Pakets, das deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="71571-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="71571-111">**/API/APP/packagemanager/Package (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="71571-112">Installiert eine APP</span><span class="sxs-lookup"><span data-stu-id="71571-112">Installs an App</span></span>

<span data-ttu-id="71571-113">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-113">Parameters</span></span>
* <span data-ttu-id="71571-114">Package: der Dateiname des zu installierenden Pakets.</span><span class="sxs-lookup"><span data-stu-id="71571-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="71571-115">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="71571-115">Payload</span></span>
* <span data-ttu-id="71571-116">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="71571-116">multi-part conforming http body</span></span>

<span data-ttu-id="71571-117">**/API/APP/packagemanager/Packages (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="71571-118">Hiermit wird die Liste der installierten apps auf dem System mit Details abgerufen.</span><span class="sxs-lookup"><span data-stu-id="71571-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="71571-119">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-119">Return data</span></span>
* <span data-ttu-id="71571-120">Liste der installierten Pakete mit Details</span><span class="sxs-lookup"><span data-stu-id="71571-120">List of installed packages with details</span></span>

<span data-ttu-id="71571-121">**/API/APP/packagemanager/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="71571-122">Hiermit wird der Status der Installation in Progress-App abgerufen.</span><span class="sxs-lookup"><span data-stu-id="71571-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="71571-123">Absturzabbildsammlung</span><span class="sxs-lookup"><span data-stu-id="71571-123">Dump collection</span></span>

<span data-ttu-id="71571-124">**/API/Debug/Dump/Usermode/CrashControl (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="71571-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="71571-125">Deaktiviert die Absturz Abbild Erfassung für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="71571-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="71571-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-126">Parameters</span></span>
* <span data-ttu-id="71571-127">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="71571-127">packageFullname : package name</span></span>

<span data-ttu-id="71571-128">**/API/Debug/Dump/Usermode/CrashControl (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="71571-129">Ruft Einstellungen für die Absturz Abbild Erfassung von Sideload-apps ab</span><span class="sxs-lookup"><span data-stu-id="71571-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="71571-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-130">Parameters</span></span>
* <span data-ttu-id="71571-131">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="71571-131">packageFullname : package name</span></span>

<span data-ttu-id="71571-132">**/API/Debug/Dump/Usermode/CrashControl (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="71571-133">Aktiviert und legt Sicherungs Steuerungseinstellungen für eine per Sideload übertragene App fest.</span><span class="sxs-lookup"><span data-stu-id="71571-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="71571-134">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-134">Parameters</span></span>
* <span data-ttu-id="71571-135">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="71571-135">packageFullname : package name</span></span>

<span data-ttu-id="71571-136">**/API/Debug/Dump/Usermode/crashdump (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="71571-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="71571-137">Löscht einen Absturz Abbild für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="71571-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="71571-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-138">Parameters</span></span>
* <span data-ttu-id="71571-139">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="71571-139">packageFullname : package name</span></span>
* <span data-ttu-id="71571-140">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="71571-140">fileName : dump file name</span></span>

<span data-ttu-id="71571-141">**/API/Debug/Dump/Usermode/crashdump (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="71571-142">Ruft ein Absturz Abbild für eine per Sideload übertragene App ab.</span><span class="sxs-lookup"><span data-stu-id="71571-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="71571-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-143">Parameters</span></span>
* <span data-ttu-id="71571-144">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="71571-144">packageFullname : package name</span></span>
* <span data-ttu-id="71571-145">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="71571-145">fileName : dump file name</span></span>

<span data-ttu-id="71571-146">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-146">Return data</span></span>
* <span data-ttu-id="71571-147">Dumpdatei.</span><span class="sxs-lookup"><span data-stu-id="71571-147">Dump file.</span></span> <span data-ttu-id="71571-148">Überprüfen mit WinDbg oder Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71571-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="71571-149">**/API/Debug/Dump/Usermode/Dumps (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="71571-150">Gibt eine Liste aller Absturz Abbilder für Sideload-apps zurück.</span><span class="sxs-lookup"><span data-stu-id="71571-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="71571-151">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-151">Return data</span></span>
* <span data-ttu-id="71571-152">Liste der Absturz Abbilder pro Seite geladener apps</span><span class="sxs-lookup"><span data-stu-id="71571-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="71571-153">ETW</span><span class="sxs-lookup"><span data-stu-id="71571-153">ETW</span></span>

<span data-ttu-id="71571-154">**/API/etw/Providers (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="71571-155">Listet registrierte Anbieter auf.</span><span class="sxs-lookup"><span data-stu-id="71571-155">Enumerates registered providers</span></span>

<span data-ttu-id="71571-156">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-156">Return data</span></span>
* <span data-ttu-id="71571-157">Liste der Anbieter, Anzeige Name und GUID</span><span class="sxs-lookup"><span data-stu-id="71571-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="71571-158">**/API/etw/Session/Realtime (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="71571-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="71571-159">Erstellt eine ETW-Sitzung in Echtzeit. verwaltet über einen WebSocket.</span><span class="sxs-lookup"><span data-stu-id="71571-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="71571-160">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-160">Return data</span></span>
* <span data-ttu-id="71571-161">ETW-Ereignisse von aktivierten Anbietern</span><span class="sxs-lookup"><span data-stu-id="71571-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="71571-162">Holographic – Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="71571-162">Holographic OS</span></span>

<span data-ttu-id="71571-163">**/API/Holographic/OS/etw/customproviders (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="71571-164">Gibt eine Liste von hololens-spezifischen etw-Anbietern zurück, die nicht beim System registriert sind.</span><span class="sxs-lookup"><span data-stu-id="71571-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="71571-165">**/API/Holographic/OS/Services (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="71571-166">Gibt die Zustände aller Dienste zurück, die ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="71571-166">Returns the states of all services running.</span></span>

<span data-ttu-id="71571-167">**/API/Holographic/OS/Settings/IPD (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="71571-168">Ruft die gespeicherte IPD (interpupranäre Entfernung) in Millimeter ab.</span><span class="sxs-lookup"><span data-stu-id="71571-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="71571-169">**/API/Holographic/OS/Settings/IPD (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="71571-170">Legt die IPD fest.</span><span class="sxs-lookup"><span data-stu-id="71571-170">Sets the IPD</span></span>

<span data-ttu-id="71571-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-171">Parameters</span></span>
* <span data-ttu-id="71571-172">IPD: neuer IPD-Wert, der in Millimeter festgelegt werden soll</span><span class="sxs-lookup"><span data-stu-id="71571-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="71571-173">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="71571-174">Abrufen der HTTPS-Anforderungen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="71571-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="71571-175">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="71571-176">Legt die HTTPS-Anforderungen für das Geräte Portal fest.</span><span class="sxs-lookup"><span data-stu-id="71571-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="71571-177">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-177">Parameters</span></span>
* <span data-ttu-id="71571-178">erforderlich: Ja, Nein oder Standard</span><span class="sxs-lookup"><span data-stu-id="71571-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="71571-179">Holografische Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="71571-179">Holographic Perception</span></span>

<span data-ttu-id="71571-180">**/API/Holographic/perception/Client (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="71571-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="71571-181">Akzeptiert WebSocket-Upgrades und führt einen perception-Client aus, der Updates bei 30 fps sendet.</span><span class="sxs-lookup"><span data-stu-id="71571-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="71571-182">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-182">Parameters</span></span>
* <span data-ttu-id="71571-183">clientmode: "aktiv" erzwingt den visuellen Überwachungsmodus, wenn er nicht passiv festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="71571-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="71571-184">Holographic-Therme</span><span class="sxs-lookup"><span data-stu-id="71571-184">Holographic Thermal</span></span>

<span data-ttu-id="71571-185">**/API/Holographic/Thermal/Stage (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="71571-186">Die wärmestufe des Geräts erhalten (0 normal, 1 warm, 2 kritisch)</span><span class="sxs-lookup"><span data-stu-id="71571-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="71571-187">Zuordnungs-Manager</span><span class="sxs-lookup"><span data-stu-id="71571-187">Map Manager</span></span>

<span data-ttu-id="71571-188">**/API/Holographic/mapmanager/mapFiles (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="71571-189">Ruft die Liste der verfügbaren Zuordnungs Dateien (. MapX) ab.</span><span class="sxs-lookup"><span data-stu-id="71571-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="71571-190">**/API/Holographic/mapmanager/anchorFiles (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="71571-191">Ruft die Liste der verfügbaren Anker Dateien (. ancx) ab.</span><span class="sxs-lookup"><span data-stu-id="71571-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="71571-192">**/API/Holographic/mapmanager/srdbFiles (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="71571-193">Ruft die Liste der verfügbaren Datenbankdateien für die räumliche Wiederherstellung (. SRDB) ab.</span><span class="sxs-lookup"><span data-stu-id="71571-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="71571-194">**/API/Holographic/mapmanager/getanchors (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="71571-195">Ruft die Liste der persistenten Anker für den aktuellen Benutzer ab.</span><span class="sxs-lookup"><span data-stu-id="71571-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="71571-196">Dateien herunterladen/hochladen/löschen</span><span class="sxs-lookup"><span data-stu-id="71571-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="71571-197">**/API/Holographic/mapmanager/Download (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="71571-198">Lädt eine Karten-, Anker-oder räumliche Datenbankdatei herunter.</span><span class="sxs-lookup"><span data-stu-id="71571-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="71571-199">Die Datei muss zuvor hochgeladen oder exportiert worden sein.</span><span class="sxs-lookup"><span data-stu-id="71571-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="71571-200">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-200">Parameters</span></span>
* <span data-ttu-id="71571-201">Dateiname: Name der herunter zuladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="71571-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="71571-202">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="71571-203">**/API/Holographic/mapmanager/Upload (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="71571-204">Lädt eine Karten-, Anker-oder räumliche Datenbankdatei hoch.</span><span class="sxs-lookup"><span data-stu-id="71571-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="71571-205">Nachdem eine Datei hochgeladen wurde, kann Sie später importiert werden, damit Sie vom System verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="71571-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="71571-206">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-206">Parameters</span></span>
* <span data-ttu-id="71571-207">file: Name der hoch zuladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="71571-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="71571-208">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-208">Example:</span></span>
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

<span data-ttu-id="71571-209">**/API/Holographic/mapmanager/Delete (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="71571-210">Löscht eine Karten-, Anker-oder räumliche Datenbankdatei.</span><span class="sxs-lookup"><span data-stu-id="71571-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="71571-211">Die Datei muss zuvor hochgeladen oder exportiert worden sein.</span><span class="sxs-lookup"><span data-stu-id="71571-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="71571-212">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-212">Parameters</span></span>
* <span data-ttu-id="71571-213">Dateiname: Name der zu löschenden Datei.</span><span class="sxs-lookup"><span data-stu-id="71571-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="71571-214">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="71571-215">Exportieren</span><span class="sxs-lookup"><span data-stu-id="71571-215">Export</span></span>

<span data-ttu-id="71571-216">**/API/Holographic/mapmanager/Export (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="71571-217">Exportiert die Karte, die derzeit vom System verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="71571-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="71571-218">Nach dem Export kann es heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="71571-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="71571-219">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="71571-220">**/API/Holographic/mapmanager/exportanchors (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="71571-221">Exportiert die Karte, die derzeit vom System verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="71571-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="71571-222">Nach dem Export kann es heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="71571-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="71571-223">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="71571-224">**/API/Holographic/mapmanager/exportmapandanchors (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="71571-225">Exportiert die Karte und die Anker, die zurzeit vom System verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="71571-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="71571-226">Nachdem Sie exportiert haben, können Sie heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="71571-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="71571-227">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="71571-228">**/API/Holographic/mapmanager/exportmapandspatialmappingdb (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="71571-229">Exportiert die derzeit vom System verwendete Map-und räumliche Datenbank für die Wiederherstellung.</span><span class="sxs-lookup"><span data-stu-id="71571-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="71571-230">Nachdem Sie exportiert wurden, können Sie heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="71571-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="71571-231">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="71571-232">Importieren</span><span class="sxs-lookup"><span data-stu-id="71571-232">Import</span></span>

<span data-ttu-id="71571-233">**/API/Holographic/mapmanager/Import (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="71571-234">Gibt dem System an, welche Zuordnung verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="71571-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="71571-235">Kann für exportierte oder hochgeladene Dateien aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="71571-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="71571-236">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-236">Parameters</span></span>
* <span data-ttu-id="71571-237">Dateiname: Name der zu verwendenden Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="71571-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="71571-238">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="71571-239">**/API/Holographic/mapmanager/importanchors (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="71571-240">Gibt dem System an, welche Anker aktuell verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="71571-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="71571-241">Kann für exportierte oder hochgeladene Dateien aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="71571-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="71571-242">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-242">Parameters</span></span>
* <span data-ttu-id="71571-243">Dateiname: Name der zu verwendenden Anker.</span><span class="sxs-lookup"><span data-stu-id="71571-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="71571-244">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="71571-245">**/API/Holographic/mapmanager/importspatialmappingdb (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="71571-246">Gibt an, dass das System zurzeit verwendet werden soll, welche räumliche Datenbank verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="71571-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="71571-247">Kann für exportierte oder hochgeladene Dateien aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="71571-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="71571-248">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-248">Parameters</span></span>
* <span data-ttu-id="71571-249">Dateiname: Name der zu verwendenden DB-Daten Bank Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="71571-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="71571-250">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="71571-251">Sonstiges</span><span class="sxs-lookup"><span data-stu-id="71571-251">Other</span></span>

<span data-ttu-id="71571-252">**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="71571-253">Setzen Sie das System auf die Karte, die Anker und die räumliche Wiederherstellung zurück.</span><span class="sxs-lookup"><span data-stu-id="71571-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="71571-254">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="71571-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="71571-255">**/API/Holographic/mapmanager/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="71571-256">Ruft den Status des Systems ab, einschließlich der Zuordnungs-, Anker-und räumlichen Datenbankdateien, die zuletzt importiert wurden.</span><span class="sxs-lookup"><span data-stu-id="71571-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="71571-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="71571-257">Mixed Reality Capture</span></span>

<span data-ttu-id="71571-258">**/API/Holographic/MRC/File (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="71571-259">Hiermit wird eine gemischte Reality-Datei vom Gerät heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="71571-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="71571-260">Verwenden Sie den OP = Stream-Abfrage Parameter für das Streaming.</span><span class="sxs-lookup"><span data-stu-id="71571-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="71571-261">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-261">Parameters</span></span>
* <span data-ttu-id="71571-262">Dateiname: Name, hex64-codiert, der einzurufenden Videodatei</span><span class="sxs-lookup"><span data-stu-id="71571-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="71571-263">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="71571-263">op : stream</span></span>

<span data-ttu-id="71571-264">**/API/Holographic/MRC/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="71571-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="71571-265">Löscht eine gemischte Reality-Aufzeichnung auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="71571-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="71571-266">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-266">Parameters</span></span>
* <span data-ttu-id="71571-267">Dateiname: Name, hex64-codiert, der zu löschenden Datei</span><span class="sxs-lookup"><span data-stu-id="71571-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="71571-268">**/API/Holographic/MRC/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="71571-269">Gibt die Liste der Mixed Reality-Dateien zurück, die auf dem Gerät gespeichert sind</span><span class="sxs-lookup"><span data-stu-id="71571-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="71571-270">**/API/Holographic/MRC/Photo (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="71571-271">Nimmt ein gemischtes Reality-Foto und erstellt eine Datei auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="71571-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="71571-272">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-272">Parameters</span></span>
* <span data-ttu-id="71571-273">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="71571-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="71571-274">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="71571-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="71571-275">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="71571-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="71571-276">**/API/Holographic/MRC/Settings (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="71571-277">Ruft die Standardeinstellungen für die gemischte Realität-Erfassung ab.</span><span class="sxs-lookup"><span data-stu-id="71571-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="71571-278">**/API/Holographic/MRC/Settings (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="71571-279">Legt die Standardeinstellungen für die gemischte Reality-Erfassung fest.</span><span class="sxs-lookup"><span data-stu-id="71571-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="71571-280">Einige dieser Einstellungen werden auf das MRC-Foto und die Video Erfassung des Systems angewendet.</span><span class="sxs-lookup"><span data-stu-id="71571-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="71571-281">**/API/Holographic/MRC/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="71571-282">Ruft den Zustand der Mixed Reality-Erfassung im Windows-Geräte Portal ab.</span><span class="sxs-lookup"><span data-stu-id="71571-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="71571-283">\**_Antwort_* _</span><span class="sxs-lookup"><span data-stu-id="71571-283">\**_Response_* _</span></span>

<span data-ttu-id="71571-284">Die Antwort enthält eine JSON-Eigenschaft, die angibt, ob das Windows-Geräte Portal Videos aufzeichnet.</span><span class="sxs-lookup"><span data-stu-id="71571-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="71571-285">_ */API/Holographic/MRC/Thumbnail (Get)*\*</span><span class="sxs-lookup"><span data-stu-id="71571-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="71571-286">Ruft das Miniaturbild für die angegebene Datei ab.</span><span class="sxs-lookup"><span data-stu-id="71571-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="71571-287">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-287">Parameters</span></span>
* <span data-ttu-id="71571-288">Dateiname: Name, hex64-codiert, der Datei, für die die Miniaturansicht angefordert wird</span><span class="sxs-lookup"><span data-stu-id="71571-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="71571-289">**/API/Holographic/MRC/Video/Control/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="71571-290">Startet eine gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="71571-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="71571-291">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-291">Parameters</span></span>
* <span data-ttu-id="71571-292">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="71571-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="71571-293">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="71571-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="71571-294">MIC: Mikrofon erfassen: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="71571-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="71571-295">Loopback: App-Audioerfassung: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="71571-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="71571-296">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="71571-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="71571-297">Vstab: (nur hololens 2) Videostabilisierung aktivieren: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="71571-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="71571-298">vstabbuffer: (hololens 2), Video Stabilisierungs Puffer Latenz: 0 bis 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="71571-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="71571-299">**/API/Holographic/MRC/Video/Control/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="71571-300">Beendet die aktuelle gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="71571-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="71571-301">Streaming mit gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="71571-301">Mixed Reality Streaming</span></span>

> [!CAUTION]
> <span data-ttu-id="71571-302">Aufgrund der Loopback Isolation können Sie in einer APP auf einem Gerät keine Verbindung mit Mixed Reality Streaming herstellen.</span><span class="sxs-lookup"><span data-stu-id="71571-302">Because of loopback isolation, you can't connect to Mixed Reality Streaming from inside an app on a device.</span></span>

<span data-ttu-id="71571-303">Hololens unterstützt die Live Vorschau von Mixed Reality über einen segmentierten Download einer fragmentierten MP4-Datei.</span><span class="sxs-lookup"><span data-stu-id="71571-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="71571-304">Gemischte Reality-Streams verwenden denselben Satz von Parametern, um zu steuern, was aufgezeichnet wird:</span><span class="sxs-lookup"><span data-stu-id="71571-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="71571-305">hololens: Erfassungs holograms: true oder false</span><span class="sxs-lookup"><span data-stu-id="71571-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="71571-306">PV: Erfassen der PV-Kamera: true oder false</span><span class="sxs-lookup"><span data-stu-id="71571-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="71571-307">MIC: Mikrofon erfassen: true oder false</span><span class="sxs-lookup"><span data-stu-id="71571-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="71571-308">Loopback: App-Audioerfassung: true oder false</span><span class="sxs-lookup"><span data-stu-id="71571-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="71571-309">Wenn keines dieser Angaben angegeben ist: holograms, Foto-/Videokamera und App-Audiodaten werden aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="71571-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="71571-310">Wenn eine Angabe festgelegt ist: die nicht angegebenen Parameter werden standardmäßig auf false festgelegt.</span><span class="sxs-lookup"><span data-stu-id="71571-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="71571-311">Optionale Parameter (nur hololens 2)</span><span class="sxs-lookup"><span data-stu-id="71571-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="71571-312">Renderfromcamera: Rendering aus Perspektive der Foto-/Videokamera: true oder false (Standardwert ist true)</span><span class="sxs-lookup"><span data-stu-id="71571-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="71571-313">Vstab: Videostabilisierung aktivieren: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="71571-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="71571-314">vstabbuffer: Puffer Wartezeit für Videostabilisierung: zwischen 0 und 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="71571-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="71571-315">**/API/Holographic/Stream/live.mp4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="71571-316">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="71571-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="71571-317">**/API/Holographic/Stream/live_high.mp4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="71571-318">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="71571-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="71571-319">**/API/Holographic/Stream/live_med.mp4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="71571-320">Ein 854x480p 30 fps 2.5 MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="71571-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="71571-321">**/API/Holographic/Stream/live_low.mp4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="71571-322">Ein 428x240 p 15fps 0.6-MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="71571-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="71571-323">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="71571-323">Networking</span></span>

<span data-ttu-id="71571-324">**/API/Networking/ipconfig (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="71571-325">Ruft die aktuelle IP-Konfiguration ab.</span><span class="sxs-lookup"><span data-stu-id="71571-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="71571-326">Betriebssysteminformationen</span><span class="sxs-lookup"><span data-stu-id="71571-326">OS Information</span></span>

<span data-ttu-id="71571-327">**/API/OS/Info (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="71571-328">Ruft Betriebssysteminformationen ab.</span><span class="sxs-lookup"><span data-stu-id="71571-328">Gets operating system information</span></span>

<span data-ttu-id="71571-329">**/API/OS/MachineName (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="71571-330">Ruft den Computernamen ab.</span><span class="sxs-lookup"><span data-stu-id="71571-330">Gets the machine name</span></span>

<span data-ttu-id="71571-331">**/API/OS/MachineName (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="71571-332">Legt den Computernamen fest.</span><span class="sxs-lookup"><span data-stu-id="71571-332">Sets the machine name</span></span>

<span data-ttu-id="71571-333">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-333">Parameters</span></span>
* <span data-ttu-id="71571-334">Name: neuer Computername, hex64-codiert, festgelegt auf</span><span class="sxs-lookup"><span data-stu-id="71571-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="71571-335">Wahrnehmungs Simulations-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="71571-335">Perception Simulation Control</span></span>

<span data-ttu-id="71571-336">**/API/Holographic/Simulation/Control/Mode (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-336">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="71571-337">Simulationsmodus erhalten</span><span class="sxs-lookup"><span data-stu-id="71571-337">Get the simulation mode</span></span>

<span data-ttu-id="71571-338">**/API/Holographic/Simulation/Control/Mode (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-338">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="71571-339">Festlegen des Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="71571-339">Set the simulation mode</span></span>

<span data-ttu-id="71571-340">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-340">Parameters</span></span>
* <span data-ttu-id="71571-341">Mode: Simulationsmodus: Standard, Simulation, Remote, Legacy</span><span class="sxs-lookup"><span data-stu-id="71571-341">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="71571-342">**/API/Holographic/Simulation/Control/Stream (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="71571-342">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="71571-343">Löscht einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="71571-343">Delete a control stream.</span></span>

<span data-ttu-id="71571-344">**/API/Holographic/Simulation/Control/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="71571-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="71571-345">Öffnen Sie eine websocketverbindung für einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="71571-345">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="71571-346">**/API/Holographic/Simulation/Control/Stream (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-346">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="71571-347">Erstellen Sie einen Steuerungsdaten Strom (Priorität ist erforderlich), oder stellen Sie Daten in einem erstellten Stream bereit (streamid erforderlich).</span><span class="sxs-lookup"><span data-stu-id="71571-347">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="71571-348">Es wird erwartet, dass für die Daten der Typ "Application/Octett-Stream" festgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="71571-348">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="71571-349">**/API/Holographic/Simulation/Display/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="71571-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="71571-350">Fordern Sie einen Simulations Videostream mit dem Inhalt an, der im Simulationsmodus für die System Anzeige gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="71571-350">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="71571-351">Anfänglich wird ein einfacher Format Deskriptor Header gesendet, gefolgt von H. 264-codierten Texturen, denen jeweils ein Header vorangestellt ist, der den Augen Index und die Textur Größe angibt.</span><span class="sxs-lookup"><span data-stu-id="71571-351">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="71571-352">Wiedergabe von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="71571-352">Perception Simulation Playback</span></span>

<span data-ttu-id="71571-353">**/API/Holographic/Simulation/Playback/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="71571-353">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="71571-354">Löschen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-354">Delete a recording.</span></span>

<span data-ttu-id="71571-355">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-355">Parameters</span></span>
* <span data-ttu-id="71571-356">Aufzeichnung: Name der zu löschenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-356">recording : Name of recording to delete.</span></span>

<span data-ttu-id="71571-357">**/API/Holographic/Simulation/Playback/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-357">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="71571-358">Hochladen einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-358">Upload a recording.</span></span>

<span data-ttu-id="71571-359">**/API/Holographic/Simulation/Playback/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-359">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="71571-360">Alle Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="71571-360">Get all recordings.</span></span>

<span data-ttu-id="71571-361">**/API/Holographic/Simulation/Playback/Session (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-361">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="71571-362">Gibt den aktuellen Wiedergabe Zustand einer Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="71571-362">Get the current playback state of a recording.</span></span>

<span data-ttu-id="71571-363">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-363">Parameters</span></span>
* <span data-ttu-id="71571-364">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-364">recording : Name of recording.</span></span>

<span data-ttu-id="71571-365">**/API/Holographic/Simulation/Playback/Session/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="71571-365">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="71571-366">Entladen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-366">Unload a recording.</span></span>

<span data-ttu-id="71571-367">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-367">Parameters</span></span>
* <span data-ttu-id="71571-368">Aufzeichnung: Name der zu entladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-368">recording : Name of recording to unload.</span></span>

<span data-ttu-id="71571-369">**/API/Holographic/Simulation/Playback/Session/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-369">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="71571-370">Laden Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-370">Load a recording.</span></span>

<span data-ttu-id="71571-371">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-371">Parameters</span></span>
* <span data-ttu-id="71571-372">Aufzeichnung: Name der zu ladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-372">recording : Name of recording to load.</span></span>

<span data-ttu-id="71571-373">**/API/Holographic/Simulation/Playback/Session/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-373">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="71571-374">Alle geladenen Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="71571-374">Get all loaded recordings.</span></span>

<span data-ttu-id="71571-375">**/API/Holographic/Simulation/Playback/Session/Pause (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-375">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="71571-376">Hält eine Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="71571-376">Pause a recording.</span></span>

<span data-ttu-id="71571-377">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-377">Parameters</span></span>
* <span data-ttu-id="71571-378">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-378">recording : Name of recording.</span></span>

<span data-ttu-id="71571-379">**/API/Holographic/Simulation/Playback/Session/Play (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-379">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="71571-380">Wiedergabe einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-380">Play a recording.</span></span>

<span data-ttu-id="71571-381">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-381">Parameters</span></span>
* <span data-ttu-id="71571-382">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-382">recording : Name of recording.</span></span>

<span data-ttu-id="71571-383">**/API/Holographic/Simulation/Playback/Session/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-383">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="71571-384">Beendet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-384">Stop a recording.</span></span>

<span data-ttu-id="71571-385">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-385">Parameters</span></span>
* <span data-ttu-id="71571-386">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-386">recording : Name of recording.</span></span>

<span data-ttu-id="71571-387">**/API/Holographic/Simulation/Playback/Session/Types (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-387">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="71571-388">Datentypen in einer geladenen Aufzeichnung erhalten.</span><span class="sxs-lookup"><span data-stu-id="71571-388">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="71571-389">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-389">Parameters</span></span>
* <span data-ttu-id="71571-390">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-390">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="71571-391">Erfassung von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="71571-391">Perception Simulation Recording</span></span>

<span data-ttu-id="71571-392">**/API/Holographic/Simulation/Recording/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-392">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="71571-393">Startet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-393">Start a recording.</span></span> <span data-ttu-id="71571-394">Nur eine einzelne Aufzeichnung kann gleichzeitig aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="71571-394">Only a single recording can be active at once.</span></span> <span data-ttu-id="71571-395">Eine der Köpfe, Hände, spatialmapping oder Umgebung muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="71571-395">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="71571-396">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-396">Parameters</span></span>
* <span data-ttu-id="71571-397">Head: Legen Sie auf 1 fest, um Head-Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="71571-397">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="71571-398">Hands: wird auf 1 festgelegt, um die Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="71571-398">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="71571-399">spatialmapping: auf 1 festgelegt, um die räumliche Zuordnung aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="71571-399">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="71571-400">Umgebung: Legen Sie auf 1 fest, um Umgebungs Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="71571-400">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="71571-401">Name: der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="71571-401">name : Name of the recording.</span></span>
* <span data-ttu-id="71571-402">singlespatialmappingframe: wird auf 1 festgelegt, um nur einen einzelnen räumlichen zuordnungsframe aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="71571-402">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="71571-403">**/API/Holographic/Simulation/Recording/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-403">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="71571-404">Aufzeichnungsstatus erhalten.</span><span class="sxs-lookup"><span data-stu-id="71571-404">Get recording state.</span></span>

<span data-ttu-id="71571-405">**/API/Holographic/Simulation/Recording/Stop (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-405">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="71571-406">Hält die aktuelle Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="71571-406">Stop the current recording.</span></span> <span data-ttu-id="71571-407">Die Aufzeichnung wird als Datei zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="71571-407">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="71571-408">Leistungsdaten</span><span class="sxs-lookup"><span data-stu-id="71571-408">Performance data</span></span>

<span data-ttu-id="71571-409">**/API/ResourceManager/Processes (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-409">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="71571-410">Gibt die Liste der laufenden Prozesse mit Details zurück.</span><span class="sxs-lookup"><span data-stu-id="71571-410">Returns the list of running processes with details</span></span>

<span data-ttu-id="71571-411">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-411">Return data</span></span>
* <span data-ttu-id="71571-412">JSON mit einer Liste der Prozesse und Details für jeden Prozess</span><span class="sxs-lookup"><span data-stu-id="71571-412">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="71571-413">**/API/ResourceManager/systemperf (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-413">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="71571-414">Gibt die System Leistungsstatistik (e/a-Lese-/Schreibvorgänge, Speicher Statistiken usw.) zurück.</span><span class="sxs-lookup"><span data-stu-id="71571-414">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="71571-415">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-415">Return data</span></span>
* <span data-ttu-id="71571-416">JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a</span><span class="sxs-lookup"><span data-stu-id="71571-416">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="71571-417">Leistung</span><span class="sxs-lookup"><span data-stu-id="71571-417">Power</span></span>

<span data-ttu-id="71571-418">**/API/Power/Battery (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-418">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="71571-419">Ruft den aktuellen Akku Zustand ab.</span><span class="sxs-lookup"><span data-stu-id="71571-419">Gets the current battery state</span></span>

<span data-ttu-id="71571-420">**/API/Power/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-420">**/api/power/state (GET)**</span></span>

<span data-ttu-id="71571-421">Prüft, ob sich das System in einem niedrigen Energiezustand befindet</span><span class="sxs-lookup"><span data-stu-id="71571-421">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="71571-422">Remotesteuerung</span><span class="sxs-lookup"><span data-stu-id="71571-422">Remote Control</span></span>

<span data-ttu-id="71571-423">**/API/Control/Restart (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-423">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="71571-424">Startet das Zielgerät neu.</span><span class="sxs-lookup"><span data-stu-id="71571-424">Restarts the target device</span></span>

<span data-ttu-id="71571-425">**/API/Control/Shutdown (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-425">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="71571-426">Fährt das Zielgerät herunter.</span><span class="sxs-lookup"><span data-stu-id="71571-426">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="71571-427">Task-Manager</span><span class="sxs-lookup"><span data-stu-id="71571-427">Task Manager</span></span>

<span data-ttu-id="71571-428">**/API/Taskmanager/app (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="71571-428">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="71571-429">Beendet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="71571-429">Stops a modern app</span></span>

<span data-ttu-id="71571-430">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-430">Parameters</span></span>
* <span data-ttu-id="71571-431">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="71571-431">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="71571-432">forcestop: erzwingen, dass alle Prozesse beendet werden (= yes)</span><span class="sxs-lookup"><span data-stu-id="71571-432">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="71571-433">**/API/Taskmanager/app (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-433">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="71571-434">Startet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="71571-434">Starts a modern app</span></span>

<span data-ttu-id="71571-435">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-435">Parameters</span></span>
* <span data-ttu-id="71571-436">AppID: Praid der zu startenden APP, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="71571-436">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="71571-437">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="71571-437">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="71571-438">WiFi-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="71571-438">WiFi Management</span></span>

<span data-ttu-id="71571-439">**/API/WiFi/Interfaces (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-439">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="71571-440">Listet drahtlose Netzwerkschnittstellen auf.</span><span class="sxs-lookup"><span data-stu-id="71571-440">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="71571-441">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-441">Return data</span></span>
* <span data-ttu-id="71571-442">Liste der drahtlos Schnittstellen mit Details (GUID, Beschreibung usw.)</span><span class="sxs-lookup"><span data-stu-id="71571-442">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="71571-443">**/API/WiFi/Network (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="71571-443">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="71571-444">Löscht ein Profil, das einem Netzwerk in einer angegebenen Schnittstelle zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="71571-444">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="71571-445">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-445">Parameters</span></span>
* <span data-ttu-id="71571-446">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="71571-446">interface : network interface guid</span></span>
* <span data-ttu-id="71571-447">Profil: Profilname</span><span class="sxs-lookup"><span data-stu-id="71571-447">profile : profile name</span></span>

<span data-ttu-id="71571-448">**/API/WiFi/Networks (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-448">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="71571-449">Listet drahtlose Netzwerke auf der angegebenen Netzwerkschnittstelle auf.</span><span class="sxs-lookup"><span data-stu-id="71571-449">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="71571-450">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-450">Parameters</span></span>
* <span data-ttu-id="71571-451">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="71571-451">interface : network interface guid</span></span>

<span data-ttu-id="71571-452">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-452">Return data</span></span>
* <span data-ttu-id="71571-453">Liste der Drahtlos Netzwerke, die sich auf der Netzwerkschnittstelle befinden, mit Details</span><span class="sxs-lookup"><span data-stu-id="71571-453">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="71571-454">**/API/WiFi/Network (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-454">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="71571-455">Stellt eine Verbindung mit einem Netzwerk auf der angegebenen Schnittstelle her oder trennt es.</span><span class="sxs-lookup"><span data-stu-id="71571-455">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="71571-456">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-456">Parameters</span></span>
* <span data-ttu-id="71571-457">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="71571-457">interface : network interface guid</span></span>
* <span data-ttu-id="71571-458">SSID: SSID, hex64-codiert, um eine Verbindung herzustellen</span><span class="sxs-lookup"><span data-stu-id="71571-458">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="71571-459">OP: verbinden oder trennen</span><span class="sxs-lookup"><span data-stu-id="71571-459">op : connect or disconnect</span></span>
* <span data-ttu-id="71571-460">kreateprofile: Ja oder Nein</span><span class="sxs-lookup"><span data-stu-id="71571-460">createprofile : yes or no</span></span>
* <span data-ttu-id="71571-461">Schlüssel: gemeinsam verwendeter Schlüssel, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="71571-461">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="71571-462">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="71571-462">Windows Performance Recorder</span></span>

<span data-ttu-id="71571-463">**/API/WPR/customtrace (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-463">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="71571-464">Lädt ein WPR-Profil hoch und startet die Ablauf Verfolgung mithilfe des hochgeladenen Profils.</span><span class="sxs-lookup"><span data-stu-id="71571-464">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="71571-465">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="71571-465">Payload</span></span>
* <span data-ttu-id="71571-466">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="71571-466">multi-part conforming http body</span></span>

<span data-ttu-id="71571-467">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-467">Return data</span></span>
* <span data-ttu-id="71571-468">Gibt den WPR-Sitzungsstatus zurück.</span><span class="sxs-lookup"><span data-stu-id="71571-468">Returns the WPR session status.</span></span>

<span data-ttu-id="71571-469">**/API/WPR/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-469">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="71571-470">Ruft den Status der WPR-Sitzung ab.</span><span class="sxs-lookup"><span data-stu-id="71571-470">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="71571-471">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-471">Return data</span></span>
* <span data-ttu-id="71571-472">WPR-Sitzungs Status.</span><span class="sxs-lookup"><span data-stu-id="71571-472">WPR session status.</span></span>

<span data-ttu-id="71571-473">**/API/WPR/Trace (Get)**</span><span class="sxs-lookup"><span data-stu-id="71571-473">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="71571-474">Beendet eine WPR-Ablauf Verfolgungs Sitzung (Leistung).</span><span class="sxs-lookup"><span data-stu-id="71571-474">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="71571-475">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-475">Return data</span></span>
* <span data-ttu-id="71571-476">Gibt die ETL-Ablauf Verfolgungs Datei zurück.</span><span class="sxs-lookup"><span data-stu-id="71571-476">Returns the trace ETL file</span></span>

<span data-ttu-id="71571-477">**/API/WPR/Trace (Post)**</span><span class="sxs-lookup"><span data-stu-id="71571-477">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="71571-478">Startet eine Ablauf Verfolgungs Sitzung für WPR (Leistung).</span><span class="sxs-lookup"><span data-stu-id="71571-478">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="71571-479">Parameter</span><span class="sxs-lookup"><span data-stu-id="71571-479">Parameters</span></span>
* <span data-ttu-id="71571-480">Profil: Profilname.</span><span class="sxs-lookup"><span data-stu-id="71571-480">profile : Profile name.</span></span> <span data-ttu-id="71571-481">Verfügbare Profile werden in perfprofiles/profiles.jsgespeichert.</span><span class="sxs-lookup"><span data-stu-id="71571-481">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="71571-482">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="71571-482">Return data</span></span>
* <span data-ttu-id="71571-483">Beim Start wird der WPR-Sitzungs Status zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="71571-483">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="71571-484">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="71571-484">See also</span></span>
* [<span data-ttu-id="71571-485">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="71571-485">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="71571-486">API-Referenz für den Geräte Portal (UWP)</span><span class="sxs-lookup"><span data-stu-id="71571-486">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
