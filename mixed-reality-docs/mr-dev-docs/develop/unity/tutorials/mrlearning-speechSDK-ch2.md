---
title: Ausführen von Befehlen mithilfe der Azure-Spracherkennung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Befehle mittels Azure-Spracherkennung in Mixed-Reality-Anwendungen ausführen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, Spracherkennung, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 8d031896a1725c0121272b68578016edf38a36cf
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656620"
---
# <a name="2-execute-commands-using-azure-speech-recognition"></a><span data-ttu-id="0e394-104">2. Ausführen von Befehlen mithilfe der Azure-Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="0e394-104">2. Execute commands using Azure speech recognition</span></span>

<span data-ttu-id="0e394-105">In diesem Tutorial fügen Sie die Möglichkeit hinzu, Befehle mithilfe der Azure-Spracherkennung auszuführen, sodass Sie basierend auf dem von Ihnen definierten Wort oder Ausdruck eine Aktion auslösen können.</span><span class="sxs-lookup"><span data-stu-id="0e394-105">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="0e394-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="0e394-106">Objectives</span></span>

* <span data-ttu-id="0e394-107">Erfahren, wie die Azure-Spracherkennung zum Ausführen von Befehlen verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="0e394-107">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="0e394-108">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="0e394-108">Instructions</span></span>

<span data-ttu-id="0e394-109">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Wake Word Recognizer (Script)** hinzuzufügen und sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="0e394-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="0e394-110">Geben Sie im Feld **Wake Word** (Wort zum Aufwecken) einen passenden Ausdruck ein, z. B. _Terminal aktivieren_.</span><span class="sxs-lookup"><span data-stu-id="0e394-110">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="0e394-111">Geben Sie im Feld **Dismiss Word** (Wort zum Schließen) einen passenden Ausdruck ein, z. B. _Terminal schließen_.</span><span class="sxs-lookup"><span data-stu-id="0e394-111">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![Unity-Editor mit hervorgehobener Skriptkomponente „Lunarcom Wake Word Recognizer“](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="0e394-113">Die Komponente „Lunarcom Wake Word Recognizer (Script)“ ist kein Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="0e394-113">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="0e394-114">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="0e394-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="0e394-115">Wenn Sie jetzt in den Spielmodus wechseln, wie im vorherigen Tutorial, ist der Terminalbereich standardmäßig aktiviert. Sie können ihn jetzt jedoch deaktivieren, indem Sie das Wort zum Schließen aussprechen, **Terminal schließen**:</span><span class="sxs-lookup"><span data-stu-id="0e394-115">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![Unity-Editor im Spielmodus mit aktivierter Funktion zur Spracherkennung](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="0e394-117">Und es erneut aktivieren, indem Sie das Wort zum Aufwecken sprechen **Terminal aktivieren**:</span><span class="sxs-lookup"><span data-stu-id="0e394-117">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![Unity-Editor im Spielmodus mit aktivem Terminal](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="0e394-119">Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="0e394-119">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="0e394-120">Wenn Sie davon ausgehen müssen, dass Sie häufig keine Verbindung mit Azure herstellen können, können Sie außerdem Sprachbefehle mithilfe von MRTK implementieren. Befolgen Sie dazu die Anweisungen unter [Verwenden von Sprachbefehlen](mr-learning-base-09.md).</span><span class="sxs-lookup"><span data-stu-id="0e394-120">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="0e394-121">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="0e394-121">Congratulations</span></span>

<span data-ttu-id="0e394-122">Sie haben die von Azure unterstützten Sprachbefehle implementiert.</span><span class="sxs-lookup"><span data-stu-id="0e394-122">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="0e394-123">Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0e394-123">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="0e394-124">Im nächsten Tutorial erfahren Sie, wie Sprache mithilfe von Azure-Sprachübersetzung übersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="0e394-124">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e394-125">Nächstes Tutorial: 3. Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="0e394-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
