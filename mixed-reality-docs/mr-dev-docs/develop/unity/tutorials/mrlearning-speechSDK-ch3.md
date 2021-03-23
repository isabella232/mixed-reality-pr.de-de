---
title: Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services
description: In diesem Kurs erfahren Sie, wie Sie Ihren Mixed Reality-Anwendungen die Sprachübersetzung von Azure Cognitive Services hinzufügen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, Spracherkennung, Windows 10, Sprachübersetzung
ms.localizationpriority: high
ms.openlocfilehash: bcc966b63f4c3e5bb9e6d6a38dc7f0312b288402
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590142"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="6f67d-104">3. Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="6f67d-104">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="6f67d-105">In diesem Tutorial fügen Sie Ihrem Projekt Sprachübersetzung hinzu, die es Ihnen ermöglicht, Ihre Sprache in drei verschiedene Sprachen zu übersetzen und zu transkribieren.</span><span class="sxs-lookup"><span data-stu-id="6f67d-105">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="6f67d-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="6f67d-106">Objectives</span></span>

* <span data-ttu-id="6f67d-107">Erlernen der Integration von Azure-Sprachübersetzung</span><span class="sxs-lookup"><span data-stu-id="6f67d-107">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="6f67d-108">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="6f67d-108">Instructions</span></span>

<span data-ttu-id="6f67d-109">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Translation Recognizer (Script)** hinzuzufügen und sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="6f67d-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="6f67d-110">Ändern Sie die **Zielsprache** in eine Sprache Ihrer Wahl, z. B. _Deutsch_</span><span class="sxs-lookup"><span data-stu-id="6f67d-110">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="6f67d-112">Die Komponente „Lunarcom Translation Recognizer (Script)“ ist kein Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="6f67d-112">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="6f67d-113">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="6f67d-113">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="6f67d-114">Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Sprachübersetzung testen, indem Sie zuerst auf die Satellitenschaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="6f67d-114">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="6f67d-115">Falls Ihr Computer über ein Mikrofon verfügt, wird Ihre Sprache dann, wenn Sie etwas sagen, in die gewählte Sprache übersetzt und im Terminalbereich transkribiert:</span><span class="sxs-lookup"><span data-stu-id="6f67d-115">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="6f67d-117">Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="6f67d-117">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6f67d-118">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="6f67d-118">Congratulations</span></span>

<span data-ttu-id="6f67d-119">Ihr Projekt kann nun die von Ihnen gesprochenen Wörter erfolgreich in verschiedene Sprachen übersetzen.</span><span class="sxs-lookup"><span data-stu-id="6f67d-119">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="6f67d-120">Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="6f67d-120">Run the application on your device to ensure the feature is working properly.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6f67d-121">Nächstes Tutorial: 4. Einrichten des Verständnisses von Absichten und natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="6f67d-121">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
