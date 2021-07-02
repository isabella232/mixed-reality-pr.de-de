---
title: Assistent zum Erstellen des Erweiterungsdiensts
description: Dokumentation zum Assistenten für den Übergang von Singletons zu MrTK-Diensten
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 4be9a58c7d63ab3bc93bcc326a90260cf6a3366b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176609"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="0d22c-104">Assistent zum Erstellen des Erweiterungsdiensts</span><span class="sxs-lookup"><span data-stu-id="0d22c-104">Extension service creation wizard</span></span>

<span data-ttu-id="0d22c-105">Der Übergang von Singletons zu Diensten kann schwierig sein.</span><span class="sxs-lookup"><span data-stu-id="0d22c-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="0d22c-106">Dieser Assistent kann unsere andere Dokumentation und unseren Beispielcode ergänzen, indem entwicklern ermöglicht wird, neue Dienste mit (ungefähr) der gleichen Einfachheit wie beim Erstellen eines neuen MonoBehaviour-Skripts zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0d22c-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="0d22c-107">Informationen zum Erstellen von Diensten von Grund auf finden Sie in unserem [Leitfaden zum Erstellen registrierter Dienste](../../configuration/mixed-reality-configuration-guide.md) (Bald verfügbar).</span><span class="sxs-lookup"><span data-stu-id="0d22c-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="0d22c-108">Starten des Assistenten</span><span class="sxs-lookup"><span data-stu-id="0d22c-108">Launching the wizard</span></span>

<span data-ttu-id="0d22c-109">Starten Sie den Assistenten über das Hauptmenü: **MixedRealityToolkit/Utilities/Create Extension Service.** Der Assistent führt Sie dann durch den Prozess zum Generieren Ihres Dienstskripts, ihrer Schnittstelle und Ihrer Profilklasse.</span><span class="sxs-lookup"><span data-stu-id="0d22c-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="0d22c-110">Bearbeiten Ihres Dienstskripts</span><span class="sxs-lookup"><span data-stu-id="0d22c-110">Editing your service script</span></span>

<span data-ttu-id="0d22c-111">Standardmäßig werden Ihre neuen Skriptressourcen im Ordner `MixedRealityToolkit.Generated/Extensions` generiert.</span><span class="sxs-lookup"><span data-stu-id="0d22c-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="0d22c-112">Nachdem Sie den Assistenten abgeschlossen haben, navigieren Sie hier, und öffnen Sie Ihr neues Dienstskript.</span><span class="sxs-lookup"><span data-stu-id="0d22c-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="0d22c-113">Generierte Dienstskripts enthalten einige Eingabeaufforderungen, die neuen MonoBehaviour-Skripts ähneln.</span><span class="sxs-lookup"><span data-stu-id="0d22c-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="0d22c-114">Sie informieren Sie darüber, wo Sie Ihren Dienst initialisieren und aktualisieren müssen.</span><span class="sxs-lookup"><span data-stu-id="0d22c-114">They will let you know where to initialize and update your service.</span></span>

```csharp
namespace Microsoft.MixedReality.Toolkit.Extensions
{
    [MixedRealityExtensionService(SupportedPlatforms.WindowsStandalone|SupportedPlatforms.MacStandalone|SupportedPlatforms.LinuxStandalone|SupportedPlatforms.WindowsUniversal)]
    public class NewService : BaseExtensionService, INewService, IMixedRealityExtensionService
    {
        private NewServiceProfile newServiceProfile;

        public NewService(IMixedRealityServiceRegistrar registrar,  string name,  uint priority,  BaseMixedRealityProfile profile) : base(registrar, name, priority, profile) 
        {
            newServiceProfile = (NewServiceProfile)profile;
        }

        public override void Initialize()
        {
            // Do service initialization here.
        }

        public override void Update()
        {
            // Do service updates here.
        }
    }
}
```

<span data-ttu-id="0d22c-115">Wenn Sie ihren Dienst im Assistenten registrieren möchten, müssen Sie nur dieses Skript bearbeiten, und Ihr Dienst wird automatisch aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="0d22c-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="0d22c-116">Andernfalls können Sie hier [mehr über die Registrierung Ihres neuen Diensts erfahren.](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="0d22c-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
