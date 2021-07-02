---
title: Erweiterungsdienste
description: Dokumentation für erweiterte Funktionen in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: f8f7b8dbac0355c226e4bbfae39246e5c1c58f69
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176275"
---
# <a name="extension-services"></a><span data-ttu-id="96a00-104">Erweiterungsdienste</span><span class="sxs-lookup"><span data-stu-id="96a00-104">Extension services</span></span>

<span data-ttu-id="96a00-105">Erweiterungsdienste sind Komponenten, die die Funktionalität des Mixed Reality-Toolkits erweitern.</span><span class="sxs-lookup"><span data-stu-id="96a00-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="96a00-106">Diese Dienste können vom MRTK oder von anderen Parteien bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="96a00-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="96a00-107">Erstellen eines Erweiterungsdiensts</span><span class="sxs-lookup"><span data-stu-id="96a00-107">Creating an extension service</span></span>

<span data-ttu-id="96a00-108">Die effizienteste Methode zum Erstellen eines Erweiterungsdiensts ist die Verwendung des Assistenten zum Erstellen [des Erweiterungsdiensts.](../tools/extension-service-creation-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="96a00-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="96a00-109">Wählen Sie zum Starten des Assistenten zum Erstellen des Erweiterungsdiensts Mixed Reality Toolkit > **Utilities > Create Extension Service (Erweiterungsdienst erstellen) aus.**</span><span class="sxs-lookup"><span data-stu-id="96a00-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![Assistent zum Erstellen des Erweiterungsdiensts](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="96a00-111">Der Assistent automatisiert die Erstellung der Dienstkomponenten und stellt die ordnungsgemäße Schnittstellenvererbung sicher.</span><span class="sxs-lookup"><span data-stu-id="96a00-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![Vom Assistenten zum Erstellen des Erweiterungsdiensts erstellte Komponenten](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="96a00-113">In MRTK Version 2.0.0 liegt ein Problem im Erweiterungsdienst-Assistenten vor, bei dem der Dienstinspektor und das Dienstprofil generiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="96a00-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="96a00-114">Weitere Informationen finden [Sie im Issue 5654.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654)</span><span class="sxs-lookup"><span data-stu-id="96a00-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="96a00-115">Nach Abschluss des Assistenten kann die Dienstfunktionalität implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="96a00-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="96a00-116">Registrieren eines Erweiterungsdiensts</span><span class="sxs-lookup"><span data-stu-id="96a00-116">Registering an extension service</span></span>

<span data-ttu-id="96a00-117">Um für eine Anwendung zugänglich zu sein, muss der neue Erweiterungsdienst beim Mixed Reality Werden registriert werden.</span><span class="sxs-lookup"><span data-stu-id="96a00-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="96a00-118">Der Assistent zum Erstellen des Erweiterungsdiensts kann zum Registrieren des Diensts verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="96a00-118">The extension service creation wizard can be used to register the service.</span></span>

![Registrierung des Assistenten zum Erstellen des Erweiterungsdiensts](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="96a00-120">Der Dienst kann auch manuell mithilfe des Konfigurationsinspektors Mixed Reality Toolkits registriert werden.</span><span class="sxs-lookup"><span data-stu-id="96a00-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![Manuelle Registrierung des Erweiterungsdiensts](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="96a00-122">Wenn der Erweiterungsdienst ein Profil verwendet, stellen Sie sicher, dass es im Inspektor angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="96a00-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![Konfigurierter Erweiterungsdienst](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="96a00-124">Der Komponentenname und die Priorität können ebenfalls angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="96a00-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="96a00-125">Zugreifen auf einen Erweiterungsdienst</span><span class="sxs-lookup"><span data-stu-id="96a00-125">Accessing an extension service</span></span>

<span data-ttu-id="96a00-126">Auf Erweiterungsdienste wird im Code mithilfe von zugegriffen, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="96a00-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="96a00-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="96a00-127">See also</span></span>

- [<span data-ttu-id="96a00-128">Systeme, Erweiterungsdienste und Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="96a00-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="96a00-129">Assistent zum Erstellen des Erweiterungsdiensts</span><span class="sxs-lookup"><span data-stu-id="96a00-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="96a00-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="96a00-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="96a00-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="96a00-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
