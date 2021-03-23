---
title: Azure-Raumanker in Unreal
description: Erfahren Sie, wie vorhandene Azure Spatial Anchors in Unreal-Mixed Reality-Anwendungen erstellt, verwaltet und lokalisiert werden.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, Azure, Azure-Entwicklung, Raumanker, Mixed Reality, Entwicklung, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 01d7217f038519d68eabfbf4f273c7ff8cbe7193
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "100496193"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="80ddf-104">Azure-Raumanker in Unreal</span><span class="sxs-lookup"><span data-stu-id="80ddf-104">Azure Spatial Anchors in Unreal</span></span>

<span data-ttu-id="80ddf-105">Azure-Raumanker (Azure Spatial Anchors) sind ein Microsoft Mixed Reality-Dienst, mit dem Augmented Reality-Geräte Ankerpunkte in der physischen Welt ermitteln, teilen und speichern können.</span><span class="sxs-lookup"><span data-stu-id="80ddf-105">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="80ddf-106">Die folgende Dokumentation enthält Anleitungen zum Integrieren des Azure Spatial Anchors-Diensts in ein Unreal-Projekt.</span><span class="sxs-lookup"><span data-stu-id="80ddf-106">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="80ddf-107">Weitere Informationen finden Sie unter [-Dienst](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="80ddf-107">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="80ddf-108">Unreal Engine 4.26 verfügt jetzt über Plug-Ins für die Unterstützung von ARKit und ARCore, falls Sie mit den Zielplattformen iOS oder Android arbeiten.</span><span class="sxs-lookup"><span data-stu-id="80ddf-108">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80ddf-109">Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="80ddf-110">Wenn Sie Ihre Anker lokal auf einem Gerät speichern möchten, verfügen wir über das Dokument [Lokale Raumanker](unreal-spatial-anchors.md), in dem Sie durch den Prozess geführt werden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="80ddf-111">Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.</span><span class="sxs-lookup"><span data-stu-id="80ddf-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="80ddf-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="80ddf-112">Prerequisites</span></span>

<span data-ttu-id="80ddf-113">Um diese Anleitung durchzuführen, stellen Sie sicher, dass Folgendes erfüllt ist:</span><span class="sxs-lookup"><span data-stu-id="80ddf-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="80ddf-114">[Unreal, Version 4.25](https://www.unrealengine.com/get-now) oder höher, ist installiert.</span><span class="sxs-lookup"><span data-stu-id="80ddf-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="80ddf-115">Eine [HoloLens 2-Projekt](tutorials/unreal-uxt-ch1.md)einrichtung in Unreal ist vorhanden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-115">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="80ddf-116">Sie haben die [Azure-Raumanker: Übersicht](/azure/spatial-anchors/overview) gelesen.</span><span class="sxs-lookup"><span data-stu-id="80ddf-116">Read through the [Azure Spatial Anchors overview](/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="80ddf-117">Grundkenntnisse in C++ und Unreal</span><span class="sxs-lookup"><span data-stu-id="80ddf-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="80ddf-118">Abrufen von Azure-Raumanker-Kontoinformationen</span><span class="sxs-lookup"><span data-stu-id="80ddf-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="80ddf-119">Bevor Sie Azure-Raumanker in Ihrem Projekt verwenden können, müssen Sie Folgendes erledigen:</span><span class="sxs-lookup"><span data-stu-id="80ddf-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="80ddf-120">[Erstellen Sie eine Raumankerressource](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource), und kopieren Sie die unten aufgeführten Kontofelder.</span><span class="sxs-lookup"><span data-stu-id="80ddf-120">[Create a spatial anchors resource](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="80ddf-121">Diese Werte werden verwendet, um Benutzer mit dem Konto Ihrer Anwendung zu authentifizieren:</span><span class="sxs-lookup"><span data-stu-id="80ddf-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="80ddf-122">**Konto-ID**</span><span class="sxs-lookup"><span data-stu-id="80ddf-122">**Account ID**</span></span>
    * <span data-ttu-id="80ddf-123">**Kontoschlüssel**</span><span class="sxs-lookup"><span data-stu-id="80ddf-123">**Account Key**</span></span>

<span data-ttu-id="80ddf-124">Weitere Informationen finden Sie unter [Azure-Raumanker: Authentifizierung](/azure/spatial-anchors/concepts/authentication?tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="80ddf-124">Check out the [Azure Spatial Anchors authentication](/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="80ddf-125">Azure-Raumanker in Unreal 4.25 unterstützen keine Azure AD-Authentifizierungstoken, aber Unterstützung für diese Funktionalität wird in einer späteren Version verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="80ddf-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="enabling-internet-access"></a><span data-ttu-id="80ddf-126">Aktivieren des Internetzugriffs</span><span class="sxs-lookup"><span data-stu-id="80ddf-126">Enabling Internet access</span></span>

<span data-ttu-id="80ddf-127">Öffnen Sie **Projekteinstellungen > HoloLens**, und aktivieren Sie die Funktion **Internetclient**:</span><span class="sxs-lookup"><span data-stu-id="80ddf-127">Open **Project Settings > HoloLens** and enable the **Internet Client** capability:</span></span>

![HoloLens-Projekteinstellungen mit hervorgehobenen Funktionen](images/asa-enable-wifi-connection.jpg)

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="80ddf-129">Hinzufügen von Azure-Raumanker-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="80ddf-129">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="80ddf-130">Aktivieren Sie die Azure-Raumanker-Plug-Ins im Unreal-Editor wie folgt:</span><span class="sxs-lookup"><span data-stu-id="80ddf-130">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="80ddf-131">Klicken Sie auf **Bearbeiten > Plug-Ins**, und suchen Sie nach **AzureSpatialAnchors** sowie **AzureSpatialAnchorsForWMR**.</span><span class="sxs-lookup"><span data-stu-id="80ddf-131">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="80ddf-132">Aktivieren Sie das Kontrollkästchen **Aktiviert** für beide Plug-Ins, um den Zugriff auf die Azure-Raumanker-Blaupausenbibliotheken in Ihrer Anwendung zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="80ddf-132">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Screenshot des Raumanker-Plug-Ins im Unreal-Editor](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="80ddf-134">Starten Sie anschließend den Unreal-Editor neu, damit die Plug-In-Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-134">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="80ddf-135">Das Projekt ist jetzt für die Verwendung von Azure-Raumankern bereit.</span><span class="sxs-lookup"><span data-stu-id="80ddf-135">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="80ddf-136">Starten einer Raumankersitzung</span><span class="sxs-lookup"><span data-stu-id="80ddf-136">Starting a Spatial Anchors session</span></span>

<span data-ttu-id="80ddf-137">Eine Azure-Raumankersitzung ermöglicht Clientanwendungen die Kommunikation mit dem Azure Spatial Anchors-Dienst.</span><span class="sxs-lookup"><span data-stu-id="80ddf-137">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="80ddf-138">Sie müssen eine Azure Spatial Anchors-Sitzung erstellen und starten, um Azure-Raumanker zu erstellen, zu speichern und zu teilen:</span><span class="sxs-lookup"><span data-stu-id="80ddf-138">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="80ddf-139">Öffnen Sie die Blaupause für den „Pawn“ (Bauer), den Sie in der Anwendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-139">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="80ddf-140">Fügen Sie zwei Zeichenfolgenvariablen für die **Konto-ID** und den **Kontoschlüssel** hinzu, und weisen Sie dann die entsprechenden Werte aus Ihrem Azure Spatial Anchors-Konto zu, um die Sitzung zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="80ddf-140">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Screenshot des Bereichs „Details“ mit hervorgehobener Konto-ID, Schlüssel und Variablentyp für Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="80ddf-142">Starten Sie eine Azure Spatial Anchors-Sitzung wie folgt:</span><span class="sxs-lookup"><span data-stu-id="80ddf-142">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="80ddf-143">Überprüfen Sie, ob eine **AR-Sitzung** in der HoloLens-Anwendung ausgeführt wird, da die Azure Spatial Anchors-Sitzung erst gestartet werden kann, wenn eine AR-Sitzung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="80ddf-143">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="80ddf-144">Wenn Sie keine eingerichtet haben, [erstellen Sie eine AR-Sitzungsressource](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="80ddf-144">If you don't have one setup, [create an AR Session asset](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="80ddf-145">Fügen Sie das benutzerdefinierte Ereignis **-Sitzung starten** hinzu, und konfigurieren Sie es, wie im folgenden Screenshot gezeigt.</span><span class="sxs-lookup"><span data-stu-id="80ddf-145">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="80ddf-146">Beim Erstellen einer Sitzung wird die Sitzung nicht standardmäßig gestartet, sodass Sie die Sitzung für die Authentifizierung beim Azure Spatial Anchors-Dienst konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="80ddf-146">Creating a session doesn't start the session by default, which allows you to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Blaupause für das benutzerdefinierte Ereignis zum Starten der Azure Spatial Anchors-Sitzung](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="80ddf-148">Konfigurieren Sie die Azure Spatial Anchors-Sitzung so, dass sie die **Konto-ID** und den **Kontoschlüssel** angibt.</span><span class="sxs-lookup"><span data-stu-id="80ddf-148">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![Blaupause der Konfigurationssitzungsfunktion mit hinzugefügter Konto-ID und Schlüssel](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="80ddf-150">Starten Sie die Azure Spatial Anchors-Sitzung, was es der Anwendung ermöglicht, lokale Azure-Raumanker zu erstellen und aufzufinden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-150">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Blaupause der Startfunktion für die Azure Spatial Anchors-Sitzung](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="80ddf-152">Es hat sich bewährt, die Azure-Raumankerressourcen in Ihrer Ereignisdiagramm-Blaupause zu bereinigen, wenn Sie den Dienst nicht mehr verwenden:</span><span class="sxs-lookup"><span data-stu-id="80ddf-152">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="80ddf-153">Beenden Sie die Azure Spatial Anchors-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="80ddf-153">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="80ddf-154">Die Sitzung wird nicht mehr ausgeführt, aber die zugehörigen Ressourcen sind weiterhin im Azure-Raumanker-Plug-In vorhanden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-154">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Blaupause für das benutzerdefinierte Ereignis zum Beenden der Azure Spatial Anchors-Sitzung und der Funktion zum Beenden der Sitzung](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="80ddf-156">Zerstören Sie die Azure Spatial Anchors-Sitzung, um alle Azure Spatial Anchors-Sitzungsressourcen zu bereinigen, die im Azure-Raumanker-Plug-In noch bekannt sind.</span><span class="sxs-lookup"><span data-stu-id="80ddf-156">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![Blaupause der Funktion zum Zerstören der Sitzung](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="80ddf-158">Ihre Ereignisdiagramm-Blaupause sollte wie im folgenden Screenshot aussehen:</span><span class="sxs-lookup"><span data-stu-id="80ddf-158">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Blaupause des vollständigen Ereignisdiagramms der Einrichtung der Azure Spatial Anchors-Sitzung](images/asa-unreal/unreal-spatial-anchors-img-08.png)

## <a name="creating-an-anchor"></a><span data-ttu-id="80ddf-160">Erstellen eines Ankers</span><span class="sxs-lookup"><span data-stu-id="80ddf-160">Creating an anchor</span></span>

<span data-ttu-id="80ddf-161">Ein Azure-Raumanker stellt eine physische Weltpose im Augmented Reality-Anwendungsraum dar, die Augmented Reality-Inhalte an physische Orte bindet.</span><span class="sxs-lookup"><span data-stu-id="80ddf-161">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to physical locations.</span></span> <span data-ttu-id="80ddf-162">Azure-Raumanker können auch von verschiedenen Benutzern gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-162">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="80ddf-163">Dieses Teilen ermöglicht es, dass Augmented Reality-Inhalte, die auf verschiedenen Geräten gezeichnet werden, am selben Ort in der physischen Welt positioniert werden können.</span><span class="sxs-lookup"><span data-stu-id="80ddf-163">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="80ddf-164">So erstellen Sie einen neuen Azure-Raumanker</span><span class="sxs-lookup"><span data-stu-id="80ddf-164">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="80ddf-165">Überprüfen Sie, ob eine Azure Spatial Anchors-Sitzung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="80ddf-165">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="80ddf-166">Die Anwendung kann einen Azure-Raumanker nur erstellen oder speichern, wenn eine Azure Spatial Anchors-Sitzung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="80ddf-166">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Blaupause für das Erstellen eines benutzerdefinierten Azure Spatial Anchors-Ereignisses](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="80ddf-168">Erstellen Sie eine Unreal- **[Szenenkomponente](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** , oder rufen Sie eine ab, deren Ort gespeichert werden sollte.</span><span class="sxs-lookup"><span data-stu-id="80ddf-168">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="80ddf-169">Im folgenden Bild wird die Komponente **Szenenkomponente, die einen Anker benötigt** als Variable verwendet.</span><span class="sxs-lookup"><span data-stu-id="80ddf-169">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="80ddf-170">Eine Unreal-Szenenkomponente ist erforderlich, um eine Anwendungswelttransformation für ein [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) und einen Azure-Raumanker einzurichten.</span><span class="sxs-lookup"><span data-stu-id="80ddf-170">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![Blaupause für das Erstellen eines benutzerdefinierten Azure Spatial Anchors-Ereignisses mit Szenenkomponente](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="80ddf-172">So erstellen und speichern Sie einen Azure-Raumanker für eine Unreal-Szenenkomponente</span><span class="sxs-lookup"><span data-stu-id="80ddf-172">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="80ddf-173">Rufen Sie die [Pin-Komponente](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) für die Unreal-Szenenkomponente auf, und geben Sie die **Welttransformation** der Szenenkomponente als die Welttransformation an, die für den AR Pin verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="80ddf-173">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="80ddf-174">Unreal verfolgt AR-Punkte im Anwendungsraum mithilfe von AR Pins, die zum Erstellen eines Azure-Raumankers verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-174">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="80ddf-175">In Unreal entspricht ein AR Pin analog einem SpatialAnchor (Raumanker) auf HoloLens.</span><span class="sxs-lookup"><span data-stu-id="80ddf-175">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![Blaupause der mit der Pin-Komponentenfunktion verbundenen Szenenkomponente](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="80ddf-177">Rufen Sie mithilfe des neu erstellten AR Pins **Cloudanker erstellen** auf.</span><span class="sxs-lookup"><span data-stu-id="80ddf-177">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="80ddf-178">„Cloudanker erstellen“ erstellt lokal einen Azure-Raumanker, aber nicht im Azure-Raumankerdienst.</span><span class="sxs-lookup"><span data-stu-id="80ddf-178">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="80ddf-179">Parameter für den Azure-Raumanker, z. B. ein Ablaufdatum, können festgelegt werden, bevor der Azure-Raumanker mit dem Dienst erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="80ddf-179">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![Blaupause der Pin-Komponentenfunktion, die mit der Funktion zum Erstellen eines Cloudankers verbunden ist, die ARPin zurückgibt](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="80ddf-181">Legen Sie den Ablauf des Azure-Raumankers fest.</span><span class="sxs-lookup"><span data-stu-id="80ddf-181">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="80ddf-182">Der Parameter „Lifetime“ (Lebensdauer) dieser Funktion ermöglicht es dem Entwickler, in Sekunden anzugeben, wie lange der Anker vom Dienst erhalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="80ddf-182">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="80ddf-183">Eine Ablaufzeit von einer Woche würde beispielsweise einen Wert von 60 Sekunden × 60 Minuten x 24 Stunden x 7 Tage = 604.800 Sekunden erfordern.</span><span class="sxs-lookup"><span data-stu-id="80ddf-183">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![Blaupause des Cloudankers, der mit der Funktion zum Festlegen des Ablaufs verbunden ist, mit auf 604.800 Sekunden festgelegter Lebensdauer](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="80ddf-185">Nachdem Sie Ankerparameter festgelegt haben, deklarieren Sie den Anker als zum Speichern bereit.</span><span class="sxs-lookup"><span data-stu-id="80ddf-185">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="80ddf-186">Im folgenden Beispiel wird der neu erstellte Azure-Raumanker zu einem Satz von Azure-Raumankern hinzugefügt, die gespeichert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="80ddf-186">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="80ddf-187">Dieser Satz wird als Variable für die Pawn-Blaupause deklariert.</span><span class="sxs-lookup"><span data-stu-id="80ddf-187">This set is declared as a variable for the Pawn blueprint.</span></span>

![Blaupause des zum Speichern in der Satzvariablen bereiten Ankers](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="80ddf-189">Speichern eines Ankers</span><span class="sxs-lookup"><span data-stu-id="80ddf-189">Saving an Anchor</span></span>

<span data-ttu-id="80ddf-190">Nachdem Sie den Azure-Raumanker mit Ihren Parametern konfiguriert haben, rufen Sie **Cloudanker speichern** auf.</span><span class="sxs-lookup"><span data-stu-id="80ddf-190">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="80ddf-191">„Cloudanker speichern“ deklariert den Anker im Azure Spatial Anchors-Dienst.</span><span class="sxs-lookup"><span data-stu-id="80ddf-191">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="80ddf-192">Wenn der Aufruf von „Cloudanker speichern“ erfolgreich ist, steht der Azure-Raumanker anderen Benutzern des Azure Spatial Anchors-Diensts zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="80ddf-192">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![Blaupause des Aufrufs der Funktion zum Speichern eines Cloudankers](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="80ddf-194">„Cloudanker speichern“ ist eine asynchrone Funktion und kann nur für ein Spielthreadereignis wie **EventTick** aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-194">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="80ddf-195">„Cloudanker speichern“ wird in benutzerdefinierten Blaupausenfunktionen möglicherweise nicht als verfügbare Blaupausenfunktion angezeigt.</span><span class="sxs-lookup"><span data-stu-id="80ddf-195">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="80ddf-196">Es sollte jedoch im Blaupausen-Editor für das Pawn-Ereignisdiagramm verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="80ddf-196">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="80ddf-197">Im folgenden Beispiel wird der Azure-Raumanker während eines Eingabeereignisrückrufs in einem Satz gespeichert.</span><span class="sxs-lookup"><span data-stu-id="80ddf-197">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="80ddf-198">Der Anker wird dann im EventTick gespeichert.</span><span class="sxs-lookup"><span data-stu-id="80ddf-198">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="80ddf-199">Es kann mehrere Versuche benötigen, um einen Azure-Raumanker zu speichern, je nach der Menge von Raumdaten, die Ihre Azure Spatial Anchors-Sitzung erstellt hat.</span><span class="sxs-lookup"><span data-stu-id="80ddf-199">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="80ddf-200">Aus diesem Grund empfiehlt es sich, zu überprüfen, ob der Speichernaufruf erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="80ddf-200">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="80ddf-201">Wenn der Anker nicht gespeichert wird, fügen Sie ihn erneut dem Satz von Ankern hinzu, die noch gespeichert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="80ddf-201">If the anchor doesn't save, readd it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="80ddf-202">Zukünftige EventTicks versuchen weiterhin, den Anker zu speichern, bis er erfolgreich gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="80ddf-202">Future EventTicks will keep trying to save the anchor until it's successfully stored.</span></span>

![Blaupause von nicht gespeicherten Ankern, die in der Satzvariablen erneut gespeichert werden](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="80ddf-204">Nachdem der Anker gespeichert wurde, fungiert die Transformation des AR Pins als Verweistransformation, um Inhalt in Ihrer App abzulegen.</span><span class="sxs-lookup"><span data-stu-id="80ddf-204">Once the anchor saves, the AR Pins' transform acts as a reference transform for placing content in your app.</span></span> <span data-ttu-id="80ddf-205">Andere Benutzer können diesen Anker erkennen und AR-Inhalt für verschiedene Geräte in der physischen Welt ausrichten.</span><span class="sxs-lookup"><span data-stu-id="80ddf-205">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="80ddf-206">Löschen eines Ankers</span><span class="sxs-lookup"><span data-stu-id="80ddf-206">Deleting an Anchor</span></span>

<span data-ttu-id="80ddf-207">Sie können Anker aus dem Azure Spatial Anchors-Dienst löschen, indem Sie **Cloudanker löschen** aufrufen.</span><span class="sxs-lookup"><span data-stu-id="80ddf-207">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![Blaupause des Aufrufs der Funktion zum Löschen eines Cloudankers](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="80ddf-209">„Cloudanker löschen“ ist eine latente Funktion und kann nur für ein Spielthreadereignis wie „EventTick“ aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-209">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="80ddf-210">„Cloudanker löschen“ wird in benutzerdefinierten Blaupausenfunktionen möglicherweise nicht als verfügbare Blaupausenfunktion angezeigt.</span><span class="sxs-lookup"><span data-stu-id="80ddf-210">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="80ddf-211">Es sollte jedoch im Blaupausen-Editor für das Pawn-Ereignisdiagramm verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="80ddf-211">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="80ddf-212">Im folgenden Beispiel ist der Anker für das Löschen in einem benutzerdefinierten Eingabeereignis gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="80ddf-212">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="80ddf-213">Der Löschvorgang wird dann bei EventTick versucht.</span><span class="sxs-lookup"><span data-stu-id="80ddf-213">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="80ddf-214">Wenn das Löschen des Ankers fehlschlägt, fügen Sie den Azure-Raumanker dem Satz von Ankern hinzu, die zum Löschen gekennzeichnet sind, und versuchen Sie es noch mal mit späteren EventTicks.</span><span class="sxs-lookup"><span data-stu-id="80ddf-214">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="80ddf-215">Ihre Ereignisdiagramm-Blaupause sollte jetzt wie im folgenden Screenshot aussehen:</span><span class="sxs-lookup"><span data-stu-id="80ddf-215">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![Blaupause des vollständigen Ereignisdiagramms für die Behandlung von Cloudankern](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="80ddf-217">Auffinden bereits vorhandener Anker</span><span class="sxs-lookup"><span data-stu-id="80ddf-217">Locating pre-existing anchors</span></span>

<span data-ttu-id="80ddf-218">Vorhandene Anker können von Peers mithilfe des Azure Spatial Anchors-Diensts erstellt werden:</span><span class="sxs-lookup"><span data-stu-id="80ddf-218">Existing anchors can be created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="80ddf-219">Rufen Sie einen Azure-Raumankerbezeichner für den Anker ab, den Sie erkennen möchten.</span><span class="sxs-lookup"><span data-stu-id="80ddf-219">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="80ddf-220">Ein Ankerbezeichner kann für einen Anker abgerufen werden, der von demselben Gerät in einer früheren Azure Spatial Anchors-Sitzung erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="80ddf-220">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="80ddf-221">Er kann außerdem von Peergeräten erstellt und geteilt werden, die mit dem Azure Spatial Anchors-Dienst interagieren.</span><span class="sxs-lookup"><span data-stu-id="80ddf-221">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Blaupause für das benutzerdefinierte Ereignis zum Speichern des Azure Spatial Anchors-Bezeichners mit Funktion zum Abrufen des Azure-Cloudbezeichners](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="80ddf-223">Fügen Sie Ihrer Pawn-Blaupause eine **AzureSpatialAnchorsEvent**-Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="80ddf-223">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="80ddf-224">Mit dieser Komponente können Sie verschiedene Azure-Raumankerereignisse abonnieren, z. B. Ereignisse, die aufgerufen werden, wenn Azure-Raumanker aufgefunden werden.</span><span class="sxs-lookup"><span data-stu-id="80ddf-224">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![Screenshot der im Blaupausen-Editor geöffneten „BP_Pawn“ mit geöffneten Bereichen „Komponenten“ und „Detail“.](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="80ddf-226">Abonnieren Sie den **Delegaten für gefundene ASAAnchor** für die **AzureSpatialAnchorsEvent**-Komponente.</span><span class="sxs-lookup"><span data-stu-id="80ddf-226">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="80ddf-227">Der Delegat teilt der Anwendung mit, wenn neue Anker gefunden wurden, die dem Azure Spatial Anchors-Konto zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="80ddf-227">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="80ddf-228">Mit dem Ereignisrückruf werden für Azure-Raumanker, die von Peers mit der Azure Spatial Anchors-Sitzung erstellt wurden, standardmäßig keine AR Pins erstellt.</span><span class="sxs-lookup"><span data-stu-id="80ddf-228">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="80ddf-229">Um einen AR Pin für den erkannten Azure-Raumanker zu erstellen, können Entwickler **ARPin um Azure Cloud-Raumanker erstellen** aufrufen.</span><span class="sxs-lookup"><span data-stu-id="80ddf-229">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![Blaupause des „Begin Play“-Ereignisses, das mit dem Delegaten für gefundene ASAAnchor verbunden ist](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="80ddf-231">Zum Auffinden von Azure-Raumankern, die von Peers mithilfe des Azure Spatial Anchors-Diensts erstellt wurden, muss die Anwendung einen **Azure Spatial Anchors-Watcher** erstellen:</span><span class="sxs-lookup"><span data-stu-id="80ddf-231">To locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="80ddf-232">Überprüfen Sie, ob eine Azure Spatial Anchors-Sitzung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="80ddf-232">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="80ddf-233">Erstellen Sie ein **AzureSpatialAnchorsLocateCriteria**.</span><span class="sxs-lookup"><span data-stu-id="80ddf-233">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="80ddf-234">Sie können verschiedene Standortparameter angeben, z. B. die Entfernung vom Benutzer oder die Entfernung von einem anderen Anker.</span><span class="sxs-lookup"><span data-stu-id="80ddf-234">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="80ddf-235">Deklarieren Sie den Azure Spatial Anchors-Bezeichner, nach dem Sie in **AzureSpatialAnchorsLocateCritieria** suchen.</span><span class="sxs-lookup"><span data-stu-id="80ddf-235">Declare the Azure Spatial Anchor identifier you're looking for in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="80ddf-236">Rufen Sie **Watcher erstellen** auf.</span><span class="sxs-lookup"><span data-stu-id="80ddf-236">Call **Create Watcher**.</span></span>

![Blaupause für das benutzerdefinierte Ereignis zum Starten des Azure Spatial Anchors-Watchers](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="80ddf-238">Die Anwendung beginnt nun, nach Azure-Raumankern zu suchen, die dem Azure Spatial Anchors-Dienst bekannt sind, was bedeutet, dass Benutzer von Peers erstellte Azure-Raumanker auffinden können.</span><span class="sxs-lookup"><span data-stu-id="80ddf-238">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="80ddf-239">Nachdem Sie den Azure-Raumanker gefunden haben, rufen Sie **Watcher beenden** auf, um den Azure-Raumanker-Watcher zu beenden und Watcherressourcen zu bereinigen.</span><span class="sxs-lookup"><span data-stu-id="80ddf-239">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![Blaupause des Aufrufs der Funktion zum Beenden des Watchers](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="80ddf-241">Ihre endgültige Ereignisdiagramm-Blaupause sollte jetzt wie im folgenden Screenshot aussehen:</span><span class="sxs-lookup"><span data-stu-id="80ddf-241">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![Blaupause des vollständigen Ereignisdiagramms für die Behandlung von Ankerdelegatenereignissen](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="80ddf-243">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="80ddf-243">Next Development Checkpoint</span></span>

<span data-ttu-id="80ddf-244">Wenn Sie der Unreal-Entwicklungs-Journey folgen, die wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="80ddf-244">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="80ddf-245">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="80ddf-245">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="80ddf-246">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="80ddf-246">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="80ddf-247">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="80ddf-247">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="80ddf-248">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="80ddf-248">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="80ddf-249">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="80ddf-249">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="80ddf-250">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="80ddf-250">Next steps</span></span>
* [<span data-ttu-id="80ddf-251">Lokale Raumanker</span><span class="sxs-lookup"><span data-stu-id="80ddf-251">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="80ddf-252">Raumanker-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="80ddf-252">Spatial Anchors documentation</span></span>](/azure/spatial-anchors/)
* [<span data-ttu-id="80ddf-253">Raumankerfunktionen</span><span class="sxs-lookup"><span data-stu-id="80ddf-253">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="80ddf-254">Richtlinien für eine effektive Ankererfahrung</span><span class="sxs-lookup"><span data-stu-id="80ddf-254">Effective anchor experience guidelines</span></span>](/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)