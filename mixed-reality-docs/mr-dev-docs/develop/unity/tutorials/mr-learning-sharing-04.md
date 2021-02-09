---
title: Freigeben von Objektbewegungen für mehrere Benutzer
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Objektbewegungen mit mehreren Benutzern in einer HoloLens 2-Anwendung teilen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Mehrbenutzerfunktionen, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: d4dc943c8ca57331b4916e40db67df3cd3d6d2e6
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590062"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="89de7-104">4. Freigeben von Objektbewegungen für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="89de7-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="89de7-105">In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten teilen, damit alle Teilnehmer einer geteilten Benutzeroberfläche zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="89de7-105">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each other's interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="89de7-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="89de7-106">Objectives</span></span>

* <span data-ttu-id="89de7-107">Konfigurieren des Projekts zum Teilen der Bewegungen von Objekten</span><span class="sxs-lookup"><span data-stu-id="89de7-107">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="89de7-108">Erlernen des Erstellens einer einfachen Mehrbenutzer-App zur Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="89de7-108">Learn how to build a basic multi-user collaborative app</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="89de7-109">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="89de7-109">Preparing the scene</span></span>

<span data-ttu-id="89de7-110">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie das Tutorial-Prefab hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="89de7-110">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="89de7-111">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, und ziehen Sie das **TableAnchor**-Prefab auf das **SharedPlayground**-Objekt im Hierarchiefenster, um es Ihrer Szene als untergeordnetes Objekt des SharedPlayground-Objekts hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="89de7-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab onto the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![Unity mit neu hinzugefügtem, ausgewähltem TableAnchor-Prefab](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="89de7-113">Konfigurieren von PUN zum Instanziieren der Objekte</span><span class="sxs-lookup"><span data-stu-id="89de7-113">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="89de7-114">In diesem Abschnitt konfigurieren Sie das Projekt so, dass es die Benutzeroberfläche von Rover-Explorer verwendet, die in den [Tutorials mit den ersten Schritten](mr-learning-base-01.md) erstellt wurde, und definieren, wo sie instanziiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="89de7-114">In this section, you will configure the project to use the Rover Explorer experience created during the [Getting started tutorials](mr-learning-base-01.md) and define where it will be instantiated.</span></span>

<span data-ttu-id="89de7-115">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.</span><span class="sxs-lookup"><span data-stu-id="89de7-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="89de7-116">Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="89de7-116">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="89de7-117">Weisen Sie dem Feld **RoverExplorer Prefab** das Prefab **RoverExplorer_Complete_Variant** aus dem Ordner „Resources“ zu.</span><span class="sxs-lookup"><span data-stu-id="89de7-117">To the **Rover Explorer Prefab** field, assign the **RoverExplorer_Complete_Variant** prefab from the Resources folder</span></span>

![Unity mit teilweise konfigurierter Photon Room-Komponente](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

<span data-ttu-id="89de7-119">Klappen Sie im Hierarchiefenster das **TableAnchor**-Objekt auf, während das untergeordnete Objekt **NetworkRoom** noch ausgewählt ist, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="89de7-119">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="89de7-120">Weisen Sie dem Feld **Rover Explorer Location** (Rover-Explorer-Position) das untergeordnete Objekt **Table** aus dem Hierarchiefenster zu.</span><span class="sxs-lookup"><span data-stu-id="89de7-120">To the **Rover Explorer Location** field, assign the TableAnchor > **Table** child object from the Hierarchy window</span></span>

![Unity mit konfigurierter Photon Room-Komponente](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="89de7-122">Ausprobieren der Benutzeroberfläche mit geteilter Objektbewegung</span><span class="sxs-lookup"><span data-stu-id="89de7-122">Trying the experience with shared object movement</span></span>

<span data-ttu-id="89de7-123">Wenn Sie das Unity-Projekt jetzt für Ihr HoloLens-Gerät erstellen und bereitstellen und anschließend, wieder in Unity, auf die Schaltfläche „Wiedergabe“ drücken, um in den Spielmodus zu wechseln, während die App auf Ihrem HoloLens-Gerät ausgeführt wird, sehen Sie, wie sich das Objekt in Unity bewegt, wenn Sie es in HoloLens bewegen:</span><span class="sxs-lookup"><span data-stu-id="89de7-123">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the app is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![Animation, die Unity mit vernetzten Objekten zeigt.](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="89de7-125">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="89de7-125">Congratulations</span></span>

<span data-ttu-id="89de7-126">Sie haben Ihr Projekt erfolgreich so konfiguriert, dass Objektbewegungen synchronisiert werden, damit Benutzer sehen können, wie sich die Objekte bewegen, wenn andere Benutzer sie bewegen.</span><span class="sxs-lookup"><span data-stu-id="89de7-126">You have successfully configured your project to synchronize object movements so users can see the objects move when other users move them.</span></span> <span data-ttu-id="89de7-127">Im nächsten Tutorial implementieren Sie Funktionen, um die Lösung in der physischen Welt auszurichten.</span><span class="sxs-lookup"><span data-stu-id="89de7-127">In the next tutorial, you will implement functionality to align the experience in the physical world.</span></span> <span data-ttu-id="89de7-128">Dadurch wird sichergestellt, dass die Benutzer einander an ihrem tatsächlichen physischen Standort sehen, sodass die Objekte für alle Benutzer in der gleichen physischen Position und Drehung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="89de7-128">This will ensure the users see each other in their actual physical location, and so the objects appear in the same physical position and rotation for all users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="89de7-129">Nächstes Tutorial: 5. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung</span><span class="sxs-lookup"><span data-stu-id="89de7-129">Next Tutorial: 5. Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)
