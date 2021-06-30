---
title: Framework und Runtime
description: Informationen im Zusammenhang mit Framework und Runtime in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121608"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="4b1b3-104">Framework und Runtime</span><span class="sxs-lookup"><span data-stu-id="4b1b3-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="4b1b3-105">Änderungen an der Szene</span><span class="sxs-lookup"><span data-stu-id="4b1b3-105">Changes to the scene</span></span>

<span data-ttu-id="4b1b3-106">Um das Toolkit zu verwenden, muss sich eine Instanz des MixedRealityToolkit-Skripts in Ihrer Szene enthalten.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="4b1b3-107">Um eine hinzuzufügen, verwenden Sie die Menüoption Mixed Reality Toolkit -> Zu Szene hinzufügen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="4b1b3-108">Diese Instanz ist für das Registrieren, Aktualisieren und Ablöschen von Diensten verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="4b1b3-109">Dort wird auch Ihr Konfigurationsprofil ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="4b1b3-110">Neben dem Hinzufügen des MRTK GameObject zur Szene bietet die Menüoption auch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="4b1b3-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="4b1b3-111">Fügen Sie mixedRealityPlayspace hinzu, das von vielen anderen MRTK-Komponenten verwendet wird, um über die Welt und lokale Raumtransformationen zu denken.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="4b1b3-112">Verschieben Sie die Hauptkamera als untergeordnetes Element des MixedRealityPlayspace (und fügen Sie der Hauptkamera auch einige Eingabe- und Anvischer-Skripts hinzu, die UnityUI und die damit verbundene Eingabefunktionalität unterstützen).</span><span class="sxs-lookup"><span data-stu-id="4b1b3-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="4b1b3-113">MixedRealityToolkit-Objekt und -Laufzeit</span><span class="sxs-lookup"><span data-stu-id="4b1b3-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="4b1b3-114">Das MRTK verfügt über mehrere Kerndienste.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-114">The MRTK has several core services.</span></span> <span data-ttu-id="4b1b3-115">Einige stimmen miteinander ab. andere sind unabhängig.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="4b1b3-116">Alle verwenden denselben Lebenszyklus – Start, Registrierung, Update und Abgrenzung – und dieser Lebenszyklus unterscheidet sich vom MonoBehaviour-Lebenszyklus von Unity.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="4b1b3-117">In diesem [mittleren Beitrag](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) werden einige Hintergrundinformationen und Die Beweggründe für diesen Ansatz erläutert.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="4b1b3-118">MRTK verfügt über ein einzelnes Objekt, das die Lebensdauer und Laufzeit seiner Dienste verwaltet.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="4b1b3-119">Diese Entität stellt Sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="4b1b3-119">This entity ensures that:</span></span>

- <span data-ttu-id="4b1b3-120">Wenn das Spiel beginnt, erfolgt die Ermittlung und Initialisierung von Diensten in einer vordefinierten Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="4b1b3-121">sie bietet einen Mechanismus für Dienste, um sich selbst zu registrieren (d. h. "Ich supportiere diesen Dienst!") und damit andere Aufrufer diese Dienste abrufen können.</span><span class="sxs-lookup"><span data-stu-id="4b1b3-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="4b1b3-122">sie stellt die Update()/LateUpdate()-Aufrufe bereit und leitet sie an die verschiedenen Dienste weiter (d.h. über UpdateAllServices/LateUpdateAllServices).</span><span class="sxs-lookup"><span data-stu-id="4b1b3-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
