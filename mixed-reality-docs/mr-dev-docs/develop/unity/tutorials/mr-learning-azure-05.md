---
title: Integrieren von Azure Bot Service in LUIS
description: Schließen Sie diesen Kurs ab, um zu erfahren, wie Azure Bot Service und das Verstehen natürlicher Sprache innerhalb einer HoloLens 2-Anwendung implementiert werden können.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Bot Service, LUIS, natürliche Sprache, Unterhaltungs-Bot, Azure Cloud Services, Azure Custom Vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 66737f798ef87e756cf1935b12a368bbd22a3423
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590582"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="80e23-104">5. Integrieren von Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="80e23-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="80e23-105">In diesem Tutorial erfahren Sie, wie Sie **Azure Bot Service** in der **HoloLens 2**-Demoanwendung verwenden, um Language Understanding (LUIS) hinzuzufügen, damit der Bot Benutzer bei der Suche nach **nachverfolgten Objekten** unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="80e23-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="80e23-106">Dies ist ein zweiteiliges Tutorial, in dem Sie im ersten Teil den Bot mit [Bot Composer](https://docs.microsoft.com/composer/introduction) als codefreie Lösung erstellen und einen kurzen Blick auf die Azure-Funktion werfen, die den Bot mit den benötigten Daten versorgt.</span><span class="sxs-lookup"><span data-stu-id="80e23-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="80e23-107">Im zweiten Teil verwenden Sie **BotManager (Skript)** im Unity-Projekt, um den gehosteten Bot Service zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="80e23-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="80e23-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="80e23-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="80e23-109">Teil 1:</span><span class="sxs-lookup"><span data-stu-id="80e23-109">Part 1</span></span>

* <span data-ttu-id="80e23-110">Grundlagen zu Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="80e23-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="80e23-111">Erfahren Sie, wie Sie Bot Composer zum Erstellen eines Bots verwenden</span><span class="sxs-lookup"><span data-stu-id="80e23-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="80e23-112">Erfahren Sie, wie Sie eine Azure-Funktion verwenden, um Daten aus Azure Storage bereitzustellen</span><span class="sxs-lookup"><span data-stu-id="80e23-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="80e23-113">Teil 2:</span><span class="sxs-lookup"><span data-stu-id="80e23-113">Part 2</span></span>

* <span data-ttu-id="80e23-114">Erfahren Sie, wie Sie die Szene einrichten, um Azure Bot Service in diesem Projekt zu verwenden</span><span class="sxs-lookup"><span data-stu-id="80e23-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="80e23-115">Erfahren Sie, wie Sie Objekte im Gespräch mit dem Bot festlegen und suchen können</span><span class="sxs-lookup"><span data-stu-id="80e23-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="80e23-116">Grundlegendes zu Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="80e23-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="80e23-117">**Azure Bot Service** versetzt Entwickler in die Lage, intelligente Bots zu erstellen, die dank **LUIS** eine natürlichsprachige Konversation mit Benutzern führen können.</span><span class="sxs-lookup"><span data-stu-id="80e23-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="80e23-118">Ein Unterhaltungs-Bot ist eine hervorragende Möglichkeit, die Optionen zu erweitern, wie ein Benutzer mit Ihrer Anwendung interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="80e23-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="80e23-119">Ein Bot kann als Wissensdatenbank mit einem [QnA Maker fungieren](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true), um eine anspruchsvolle Unterhaltung mit der Leistung von [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) zu führen.</span><span class="sxs-lookup"><span data-stu-id="80e23-119">A Bot can act as a knowledge base with a [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

<span data-ttu-id="80e23-120">Weitere Informationen zu [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="80e23-120">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="80e23-121">Teil 1: Erstellen des Bots</span><span class="sxs-lookup"><span data-stu-id="80e23-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="80e23-122">Bevor Sie den Bot in der Unity-Anwendung verwenden können, müssen Sie ihn entwickeln, Daten für ihn bereitstellen und ihn in **Azure** hosten.</span><span class="sxs-lookup"><span data-stu-id="80e23-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="80e23-123">Das Ziel des Bots ist es, mitteilen zu können, wie viele *nachverfolgte Objekte* in der Datenbank gespeichert sind, ein *nachverfolgtes Objekt* anhand seines Namens zu finden und dem Benutzer einige grundlegende Informationen zu diesem Objekt mitzuteilen.</span><span class="sxs-lookup"><span data-stu-id="80e23-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="80e23-124">Ein kurzer Blick auf die Azure-Funktion für nachverfolgte Objekte</span><span class="sxs-lookup"><span data-stu-id="80e23-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="80e23-125">Sie sind im Begriff, den Bot zu erstellen. Damit der Bot aber nutzbar wird, müssen Sie ihm eine Ressource zur Verfügung stellen, aus der er Daten pullen kann.</span><span class="sxs-lookup"><span data-stu-id="80e23-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="80e23-126">Da der *Bot* in der Lage sein soll, die Anzahl der **nachverfolgten Objekte** zu zählen, bestimmte Objekte anhand ihres Namens zu finden und Details mitzuteilen, verwenden Sie eine einfache Azure-Funktion, die Zugriff auf den **Azure Table-Speicher** besitzt.</span><span class="sxs-lookup"><span data-stu-id="80e23-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="80e23-127">Laden Sie das Azure-Funktionsprojekt für nachverfolgte Objekte herunter: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip), und extrahieren Sie es auf Ihre Festplatte.</span><span class="sxs-lookup"><span data-stu-id="80e23-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="80e23-128">Diese Azure-Funktion verfügt über zwei Aktionen: **Count** (Anzahl) und **Find** (Suchen), die über grundlegende *HTTP* *GET*-Aufrufe aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="80e23-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="80e23-129">Sie können den Code in **Visual Studio** untersuchen.</span><span class="sxs-lookup"><span data-stu-id="80e23-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="80e23-130">Weitere Informationen zu [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="80e23-130">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="80e23-131">Die Funktion **Count** fragt aus **Table Storage** alle **TrackedObjects** aus der Tabelle ab. Dies ist ein sehr einfacher Vorgang.</span><span class="sxs-lookup"><span data-stu-id="80e23-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="80e23-132">Die Funktion **Find** nimmt ihrerseits einen Abfrageparameter *name* aus der *GET*-Anforderung an, fragt **Table Storage** nach einem passenden **TrackedObject** ab und gibt dann ein DTO als JSON zurück.</span><span class="sxs-lookup"><span data-stu-id="80e23-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="80e23-133">Zum Bereitstellen dieser **Azure-Funktion** direkt aus **Visual Studio** öffnen Sie den heruntergeladenen Ordner „AzureFunction_TrackedObjectsService“, und öffnen Sie die vorhandene **SLN**-Datei mit der ![Bot Framework Composer-Startumgebung](images/mr-learning-azure/tutorial5-section3-step1-1.png) in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="80e23-133">To deploy this **Azure Function** directly from **Visual Studio**, open the downloaded AzureFunction_TrackedObjectsService folder and open the present **.sln** file with visual studio ![Bot Framework Composer Home](images/mr-learning-azure/tutorial5-section3-step1-1.png)</span></span>

<span data-ttu-id="80e23-134">Nachdem die Datei in Visual Studio geladen wurde, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Tracked object service** (Dienst für nachverfolgte Objekte), und wählen Sie ![Bot Framework Composer-Startumgebung veröffentlichen](images/mr-learning-azure/tutorial5-section3-step1-2.png) aus.</span><span class="sxs-lookup"><span data-stu-id="80e23-134">Once file loaded in visual studio, Right click over **Tracked object sevice** in solution explorer and select publish ![Bot Framework Composer Home](images/mr-learning-azure/tutorial5-section3-step1-2.png)</span></span>

<span data-ttu-id="80e23-135">Das Popupfenster zum Veröffentlichen wird angezeigt und fordert Sie zur Auswahl der Zielplattform auf. Wählen Sie Azure aus, und klicken Sie auf die Schaltfläche **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="80e23-135">The publish pop up will be displayed and ask for target flatform Select azure and click on **Next** button</span></span>

![Bot Framework Composer-Startumgebung](images/mr-learning-azure/tutorial5-section3-step1-3.png)

<span data-ttu-id="80e23-137">Wählen Sie als spezifisches Ziel **Azure-Funktions-App (Windows)** aus, und klicken Sie auf die Schaltfläche **Weiter**</span><span class="sxs-lookup"><span data-stu-id="80e23-137">In specific target select **Azure Function App(Windows)** and click on **Next** button</span></span>

![Bot Framework Composer-Startumgebung](images/mr-learning-azure/tutorial5-section3-step1-4.png)

<span data-ttu-id="80e23-139">Wenn Sie nicht bei Azure angemeldet sind, melden Sie sich über Visual Studio an. Das Fenster sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="80e23-139">If you are not logged in to azure please login through visual studio and the window look like</span></span>

![Bot Framework Composer-Startumgebung](images/mr-learning-azure/tutorial5-section3-step1-5.png)

<span data-ttu-id="80e23-141">Klicken Sie auf die Plus-Schaltfläche, um eine neue Funktions-App in Ihrem Azure-Konto zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="80e23-141">Click on pulse button to create new Function App in azure account</span></span>

![Bot Framework Composer-Startumgebung](images/mr-learning-azure/tutorial5-section3-step1-6.png)

* <span data-ttu-id="80e23-143">Geben Sie für **Name** einen passenden Namen für den Dienst ein, z. B. *TrackedObjectsService*</span><span class="sxs-lookup"><span data-stu-id="80e23-143">For **Name**, enter a suitable name for the service, for example, *TrackedObjectsService*</span></span>
* <span data-ttu-id="80e23-144">Wählen Sie als **Plan Type** (Plantyp) „Consumption“ (Verbrauch) aus</span><span class="sxs-lookup"><span data-stu-id="80e23-144">For **Plan Type**, choose consumption</span></span>
* <span data-ttu-id="80e23-145">Wählen Sie unter **Location** (Speicherort) einen Speicherort in der Nähe des physischen Standorts Ihres App-Benutzers aus, beispielsweise *(USA) USA, Westen*</span><span class="sxs-lookup"><span data-stu-id="80e23-145">For **Location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="80e23-146">Wählen Sie als **Resource Group** (Ressourcengruppe) und **Storage** (Speicher) die entsprechende Azure-Gruppe und das Speicherkonto aus, die in den vorhergehenden Kapiteln erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="80e23-146">For **Resource Group** and **Storage**, choose respective azure group and storage account have been created in pervious chapters.</span></span>

<span data-ttu-id="80e23-147">Nachdem die Funktions-App erstellt wurde, klicken Sie auf die Schaltfläche **Finish** (Fertigstellen)</span><span class="sxs-lookup"><span data-stu-id="80e23-147">Once Function App created click on **Finish** button</span></span> 

![Bot Framework Composer-Startumgebung](images/mr-learning-azure/tutorial5-section3-step1-7.png)

<span data-ttu-id="80e23-149">Nach dem Abschluss des Vorgangs wird ein Veröffentlichen-Popup geöffnet. Klicken Sie auf die Schaltfläche **Publish** (Veröffentlichen), um die Funktion zu veröffentlichen, und warten Sie auf die Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="80e23-149">A publish pop up will be opened after the finish process, click on **Publish** button to publish the function and wait for publish</span></span>

![Bot Framework Composer-Startumgebung](images/mr-learning-azure/tutorial5-section3-step1-8.png)

<span data-ttu-id="80e23-151">Klicken Sie nach dem Abschluss der Veröffentlichung im Abschnitt „Actions“ (Akionen) auf **Manage in Azure portal** (Im Azure-Portal verwalten). Hierdurch gelangen Sie zu spezifischen Funktionen im Azure-Portal. Klicken Sie dort im Abschnitt *Settings* (Einstellungen) auf **Configuration** (Konfiguration).</span><span class="sxs-lookup"><span data-stu-id="80e23-151">Once completion of publish click on **Manage in Azure portal** under Actions section it is take you to specific function in azure portal and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="80e23-152">Dort müssen Sie unter **Anwendungseinstellungen** die *Verbindungszeichenfolge* für den **Azure Storage**-Speicher angeben, in dem die **nachverfolgten Objekte** gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="80e23-152">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="80e23-153">Klicken Sie auf **Neue Anwendungseinstellung**, und verwenden Sie den folgenden Namen: **AzureStorageConnectionString**. Geben Sie als Wert die richtige *Verbindungszeichenfolge* an.</span><span class="sxs-lookup"><span data-stu-id="80e23-153">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="80e23-154">Klicken Sie anschließend auf **Speichern**. Die **Azure-Funktion** ist nun bereit, den *Bot* mit Daten zu versorgen, den Sie im nächsten Schritt erstellen.</span><span class="sxs-lookup"><span data-stu-id="80e23-154">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

<span data-ttu-id="80e23-155">Um die URL von „Count“ und „Find“ abzurufen, wählen Sie **Functions** (Funktionen) im Abschnitt *Functions* (Funktionen) aus.</span><span class="sxs-lookup"><span data-stu-id="80e23-155">To get URL of count and Find , select **Functions** which is under the *Functions* section.</span></span> <span data-ttu-id="80e23-156">Hier finden Sie sowohl die Count- als auch die Find-Funktion. Wählen Sie die Count-Funktion aus. Oben finden Sie die Schaltfläche *Get Function Url* (Funktions-URL abrufen).</span><span class="sxs-lookup"><span data-stu-id="80e23-156">here you can find both Count and Find function, select Count function on top side you can find the *Get Function Url* button.</span></span> <span data-ttu-id="80e23-157">Mit der gleichen Vorgehensweise können Sie die Funktions-URL von „Find“ abrufen.</span><span class="sxs-lookup"><span data-stu-id="80e23-157">Follow the same procedure to get Find function Url.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="80e23-158">Erstellen eines Unterhaltungs-Bots</span><span class="sxs-lookup"><span data-stu-id="80e23-158">Creating a conversation Bot</span></span>

<span data-ttu-id="80e23-159">Es gibt mehrere Möglichkeiten, einen auf Bot Framework basierenden Unterhaltungs-Bot zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="80e23-159">There are several ways to develop a Bot Framework based conversational bot.</span></span> <span data-ttu-id="80e23-160">In dieser Lektion verwenden Sie die Desktopanwendung [Bot Framework Composer](https://docs.microsoft.com/composer/), bei der es sich um einen visuellen Designer handelt, der optimal für schnelle Entwicklung geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="80e23-160">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="80e23-161">Sie können die neuesten Releases aus dem [GitHub-Repository](https://github.com/microsoft/BotFramework-Composer/releases) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="80e23-161">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="80e23-162">Die Anwendung ist für Windows, Mac und Linux verfügbar.</span><span class="sxs-lookup"><span data-stu-id="80e23-162">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="80e23-163">Nachdem **Bot Framework Composer** installiert wurde, starten Sie die Anwendung. Die folgende Benutzeroberfläche sollte angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="80e23-163">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Bot Framework Composer-Startumgebung](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="80e23-165">Wir haben ein Bot Composer-Projekt vorbereitet, das die erforderlichen Dialoge und Trigger für dieses Tutorial bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="80e23-165">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="80e23-166">Laden Sie das Bot Framework Composer-Projekt herunter: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip), und extrahieren Sie es auf Ihre Festplatte.</span><span class="sxs-lookup"><span data-stu-id="80e23-166">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="80e23-167">Klicken Sie in der oberen Leiste auf **Öffnen**, und wählen Sie das heruntergeladene Bot Framework-Projekt aus, das **TrackedObjectsBot** heißt.</span><span class="sxs-lookup"><span data-stu-id="80e23-167">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="80e23-168">Nachdem das Projekt vollständig geladen wurde, sollte das Projekt als bereit angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="80e23-168">After the project is fully loaded, you should see the project ready.</span></span>

![Bot Framework Composer mit geöffnetem Projekt „TrackedObjectsBot“](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="80e23-170">Wir konzentrieren uns auf die linke Seite, auf der Sie den **Dialogbereich** sehen können.</span><span class="sxs-lookup"><span data-stu-id="80e23-170">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="80e23-171">Hier befindet sich ein Dialog mit dem Namen **TrackedObjectsBot** unter dem mehrere **Trigger** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="80e23-171">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="80e23-172">Weitere Informationen zum [Bot Framework-Konzept](https://docs.microsoft.com/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="80e23-172">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="80e23-173">Diese Trigger führen folgende Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="80e23-173">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="80e23-174">Greeting (Begrüßung)</span><span class="sxs-lookup"><span data-stu-id="80e23-174">Greeting</span></span>

<span data-ttu-id="80e23-175">Dies ist der Einstiegspunkt des Chat *Bots*, wenn ein *Benutzer* eine Unterhaltung einleitet.</span><span class="sxs-lookup"><span data-stu-id="80e23-175">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![Auslöser des Begrüßungsdialogs für das TrackedObjectsBot-Projekt](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="80e23-177">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="80e23-177">AskingForCount</span></span>

<span data-ttu-id="80e23-178">Dieser Dialog wird ausgelöst, wenn der *Benutzer* darum bittet, alle **nachverfolgten Objekte** zu zählen.</span><span class="sxs-lookup"><span data-stu-id="80e23-178">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="80e23-179">Dies sind die Auslöserbegriffe:</span><span class="sxs-lookup"><span data-stu-id="80e23-179">These are the trigger phrases:</span></span>

>* <span data-ttu-id="80e23-180">count me all (alle zählen)</span><span class="sxs-lookup"><span data-stu-id="80e23-180">count me all</span></span>
>* <span data-ttu-id="80e23-181">how many are stored (wie viele sind gespeichert?)</span><span class="sxs-lookup"><span data-stu-id="80e23-181">how many are stored</span></span>

![Auslöser des AskForCount-Dialogs für das TrackedObjectsBot-Projekt](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="80e23-183">Dank [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) muss der *Benutzer* die Begriffe nicht genau so verwenden. Der *Benutzer* kann eine natürlichsprachige Unterhaltung führen.</span><span class="sxs-lookup"><span data-stu-id="80e23-183">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="80e23-184">In diesem Dialog kommuniziert der *Bot* auch mit der Azure-Funktion **Count**. Weitere Informationen dazu später.</span><span class="sxs-lookup"><span data-stu-id="80e23-184">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="80e23-185">Unknown Intent (unbekannte Absicht)</span><span class="sxs-lookup"><span data-stu-id="80e23-185">Unknown Intent</span></span>

<span data-ttu-id="80e23-186">Dieser Dialog wird ausgelöst, wenn die Eingabe des *Benutzer* keine andere Triggerbedingung erfüllt und der Benutzer aufgefordert wird, seine Frage erneut zu stellen.</span><span class="sxs-lookup"><span data-stu-id="80e23-186">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![Auslöser des Unknown Intent-Dialogs (Unbekannte Absicht) für das TrackedObjectsBot-Projekt](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="80e23-188">FindEntity</span><span class="sxs-lookup"><span data-stu-id="80e23-188">FindEntity</span></span>

<span data-ttu-id="80e23-189">Der letzte Dialog ist komplexer mit Verzweigungen und Speichern der Daten im Arbeitsspeicher des *Bots*.</span><span class="sxs-lookup"><span data-stu-id="80e23-189">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="80e23-190">Der Benutzer wird nach dem *Namen* des **nachverfolgten Objekts** gefragt, zu dem er weitere Informationen erhalten möchte, und es wird eine Abfrage der Azure-Funktion **Find** ausgeführt. Die Antwort wird verwendet, um die Unterhaltung fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="80e23-190">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![Auslöser des FindEntity-Dialogs für das TrackedObjectsBot-Projekt](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="80e23-192">Wenn das **nachverfolgte Objekt** nicht gefunden wird, wird der Benutzer darüber informiert, und die Unterhaltung wird beendet.</span><span class="sxs-lookup"><span data-stu-id="80e23-192">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="80e23-193">Wenn das fragliche **nachverfolgte Objekt** gefunden wird, überprüft der Bot, welche Eigenschaften verfügbar sind, und meldet diese.</span><span class="sxs-lookup"><span data-stu-id="80e23-193">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="80e23-194">Anpassen des Bots</span><span class="sxs-lookup"><span data-stu-id="80e23-194">Adapting the Bot</span></span>

<span data-ttu-id="80e23-195">Die Trigger **AskingForCount** und **FindEntity** müssen mit dem Back-End kommunizieren, d. h. Sie müssen die richtige URL der **Azure-Funktion** hinzufügen, die Sie zuvor bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="80e23-195">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="80e23-196">Klicken Sie im Dialogbereich auf **AskingForCount**, und suchen Sie die Aktion *HTTP-Anforderung senden*. Dort sehen Sie das Feld **URL**, das Sie in die richtige URL für den Endpunkt der Funktion **Count** ändern müssen.</span><span class="sxs-lookup"><span data-stu-id="80e23-196">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![Endpunktkonfiguration für den Trigger des AskingForCount-Dialogs des TrackedObjectsBot-Projekts](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="80e23-198">Suchen Sie schließlich nach dem Trigger **FindEntity** und der Aktion *HTTP-Anforderung senden*, und ändern Sie im Feld **URL** die URL in den Endpunkt der **Find**-Funktion.</span><span class="sxs-lookup"><span data-stu-id="80e23-198">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![Endpunktkonfiguration für den Trigger des FindEntity-Dialogs des TrackedObjectsBot-Projekts](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="80e23-200">Nachdem alles festgelegt wurde, kann der Bot nun bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="80e23-200">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="80e23-201">Da Sie Bot Framework Composer installiert haben, können Sie den Bot direkt von dort aus veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="80e23-201">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="80e23-202">Weitere Informationen zum [Veröffentlichen eines Bots aus Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="80e23-202">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="80e23-203">Sie können mit dem Bot experimentieren, indem Sie weitere Triggerbegriffe, neue Antworten oder Unterhaltungsverzweigungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="80e23-203">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="80e23-204">Teil 2: Integrieren der einzelnen Komponenten in Unity</span><span class="sxs-lookup"><span data-stu-id="80e23-204">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="80e23-205">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="80e23-205">Preparing the scene</span></span>

<span data-ttu-id="80e23-206">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="80e23-206">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Unity-Projektfenster mit ausgewähltem ChatBotManager-Prefab](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="80e23-208">Verschieben Sie von dort das Prefab **ChatBotManager** in die Szenenhierarchie.</span><span class="sxs-lookup"><span data-stu-id="80e23-208">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="80e23-209">Nachdem Sie ChatBotManager der Szene hinzugefügt haben, klicken Sie auf die Komponente **Chat Bot Manager**.</span><span class="sxs-lookup"><span data-stu-id="80e23-209">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="80e23-210">Im Inspektor sehen Sie, dass es ein leeres Feld **Geheimer Schlüssel für Direktverbindung** gibt, das Sie ausfüllen müssen.</span><span class="sxs-lookup"><span data-stu-id="80e23-210">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="80e23-211">Sie können den *geheimen Schlüssel* aus dem Azure-Portal abrufen, indem Sie nach der Ressource vom Typ **Bot Channels Registration** suchen, die Sie im ersten Teil dieses Tutorials erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="80e23-211">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![Unity mit noch ausgewähltem, neu hinzugefügtem ChatBotManager-Prefab](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="80e23-213">Nun verbinden Sie das **ChatBotManager**-Objekt mit der **ChatBotController**-Komponente, die an das **ChatBotPanel**-Objekt angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="80e23-213">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="80e23-214">Wählen Sie in der Hierarchie das **ChatBotPanel**-Objekt aus. Es wird ein leeres Feld **Chat Bot Manager** angezeigt. Ziehen Sie das **ChatBotManager**-Objekt aus der Hierarchie in das leere Feld **Chat Bot Manager**.</span><span class="sxs-lookup"><span data-stu-id="80e23-214">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![Unity mit konfiguriertem ChatBotPanel](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="80e23-216">Nun benötigen Sie eine Möglichkeit, **ChatBotPanel** zu öffnen, damit der Benutzer damit interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="80e23-216">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="80e23-217">Im Fenster „Szene“ haben Sie möglicherweise bemerkt, dass es eine Seitenschaltfläche *Chat Bot* für das **MainMenu**-Objekt gibt. Diese werden Sie zur Lösung dieses Problems verwenden.</span><span class="sxs-lookup"><span data-stu-id="80e23-217">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="80e23-218">Suchen Sie in der Hierarchie nach **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot**, und suchen Sie im Inspektor nach dem *ButtonConfigHelper*-Skript.</span><span class="sxs-lookup"><span data-stu-id="80e23-218">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="80e23-219">Dort wird ein leerer Slot für den **OnClick ()** -Ereignisrückruf angezeigt.</span><span class="sxs-lookup"><span data-stu-id="80e23-219">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="80e23-220">Ziehen Sie **ChatBotPanel** mithilfe von Drag & Drop in den Ereignisslot, navigieren Sie in der Dropdownliste zu *GameObject*, und wählen Sie dann im Untermenü *SetActive (bool)* aus, und aktivieren Sie das Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="80e23-220">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![Unity mit konfiguriertem ButtonChatBot](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="80e23-222">Der Chat Bot kann nun über das Hauptmenü gestartet werden. Damit ist die Szene einsatzbereit.</span><span class="sxs-lookup"><span data-stu-id="80e23-222">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="80e23-223">Testen des Bots</span><span class="sxs-lookup"><span data-stu-id="80e23-223">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="80e23-224">Frage zur Anzahl der nachverfolgten Objekte</span><span class="sxs-lookup"><span data-stu-id="80e23-224">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="80e23-225">Zuerst testen Sie den Bot, indem Sie fragen, wie viele **nachverfolgte Objekte** in der Datenbank gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="80e23-225">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="80e23-226">Dieses Mal müssen Sie die Anwendung aus HoloLens 2 ausführen, da Dienste wie *Text-zu-Sprache* möglicherweise nicht auf Ihrem System verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="80e23-226">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="80e23-227">Führen Sie die Anwendung auf HoloLens 2 aus, und klicken Sie neben dem Hauptmenü auf die Schaltfläche *Chat Bot*.</span><span class="sxs-lookup"><span data-stu-id="80e23-227">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="80e23-228">Der Bot begrüßt Sie. Fragen Sie nun **how many objects do we have?** (wie viele Objekte sind vorhanden?)</span><span class="sxs-lookup"><span data-stu-id="80e23-228">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="80e23-229">Der Bot sollten Ihnen die Anzahl mitteilen und die Unterhaltung beenden.</span><span class="sxs-lookup"><span data-stu-id="80e23-229">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="80e23-230">Frage zu einem nachverfolgten Objekt</span><span class="sxs-lookup"><span data-stu-id="80e23-230">Asking about a tracked object</span></span>

<span data-ttu-id="80e23-231">Führen Sie die Anwendung nun erneut aus, und fordern Sie den Bot dieses Mal wie folgt auf: **find me a tracked object** (nachverfolgtes Objekt suchen). Der Bot fragt Sie nach dem Namen. Darauf sollten Sie mit „car“ (Auto) oder dem Namen eines anderen *nachverfolgten Objekts* antworten, von dem Sie wissen, dass es in der Datenbank vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="80e23-231">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="80e23-232">Der Bot teilt Ihnen Details wie eine Beschreibung mit und informiert sie, ob ein räumlicher Anker zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="80e23-232">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="80e23-233">Testen Sie den Bot weiter, indem Sie nach einem **nachverfolgten Objekt** fragen, das nicht vorhanden ist. Beachten Sie, was der Bot antwortet.</span><span class="sxs-lookup"><span data-stu-id="80e23-233">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="80e23-234">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="80e23-234">Congratulations</span></span>

<span data-ttu-id="80e23-235">In diesem Tutorial haben Sie gelernt, wie Azure Bot Framework verwendet werden kann, um über eine Unterhaltung in natürlicher Sprache mit der Anwendung zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="80e23-235">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="80e23-236">Sie haben gelernt, wie Sie Ihren eigenen Bot entwickeln und welche Komponenten für seine Ausführung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="80e23-236">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="80e23-237">Schlussbemerkung</span><span class="sxs-lookup"><span data-stu-id="80e23-237">Conclusion</span></span>

<span data-ttu-id="80e23-238">Im Rahmen dieser Tutorialreihe haben Sie erfahren, wie **Azure Cloud Services** neue und interessante Features für Ihre Anwendung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="80e23-238">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="80e23-239">Sie können jetzt mit **Azure Storage** Daten und Bilder in der Cloud speichern, mit **Azure Custom Vision** Bilder zuordnen und ein Modell trainieren, mit **Azure Spatial Anchors** Objekte in einen lokalen Kontext bringen und mit **Azure Bot Framework powered by LUIS** einen Unterhaltungs-Bot für ein neues und natürliches Interaktionsmuster implementieren.</span><span class="sxs-lookup"><span data-stu-id="80e23-239">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
