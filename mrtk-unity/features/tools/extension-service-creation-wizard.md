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
# <a name="extension-service-creation-wizard"></a>Assistent zum Erstellen des Erweiterungsdiensts

Der Übergang von Singletons zu Diensten kann schwierig sein. Dieser Assistent kann unsere andere Dokumentation und unseren Beispielcode ergänzen, indem entwicklern ermöglicht wird, neue Dienste mit (ungefähr) der gleichen Einfachheit wie beim Erstellen eines neuen MonoBehaviour-Skripts zu erstellen. Informationen zum Erstellen von Diensten von Grund auf finden Sie in unserem [Leitfaden zum Erstellen registrierter Dienste](../../configuration/mixed-reality-configuration-guide.md) (Bald verfügbar).

## <a name="launching-the-wizard"></a>Starten des Assistenten

Starten Sie den Assistenten über das Hauptmenü: **MixedRealityToolkit/Utilities/Create Extension Service.** Der Assistent führt Sie dann durch den Prozess zum Generieren Ihres Dienstskripts, ihrer Schnittstelle und Ihrer Profilklasse.

## <a name="editing-your-service-script"></a>Bearbeiten Ihres Dienstskripts

Standardmäßig werden Ihre neuen Skriptressourcen im Ordner `MixedRealityToolkit.Generated/Extensions` generiert. Nachdem Sie den Assistenten abgeschlossen haben, navigieren Sie hier, und öffnen Sie Ihr neues Dienstskript.

Generierte Dienstskripts enthalten einige Eingabeaufforderungen, die neuen MonoBehaviour-Skripts ähneln. Sie informieren Sie darüber, wo Sie Ihren Dienst initialisieren und aktualisieren müssen.

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

Wenn Sie ihren Dienst im Assistenten registrieren möchten, müssen Sie nur dieses Skript bearbeiten, und Ihr Dienst wird automatisch aktualisiert. Andernfalls können Sie hier [mehr über die Registrierung Ihres neuen Diensts erfahren.](../../configuration/mixed-reality-configuration-guide.md)
