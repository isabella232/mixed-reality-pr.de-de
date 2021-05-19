---
title: Assistent zum Erstellen von Erweiterungsdiensten
description: Dokumentation zum Assistenten für den Übergang von Singletons zu Diensten MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 83797a9d6d465a150406b27162a5e84c157567f1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143540"
---
# <a name="extension-service-creation-wizard"></a>Assistent zum Erstellen eines Erweiterungsdiensts

Der Übergang von Singletons zu Diensten kann schwierig sein. Dieser Assistent kann unsere andere Dokumentation und unseren Beispielcode ergänzen, indem er Entwicklern ermöglicht, neue Dienste mit (ungefähr) der gleichen Einfachheit wie das Erstellen eines neuen MonoBehaviour-Skripts zu erstellen. Informationen zum Erstellen von Diensten von Grund auf finden Sie in unserem [Leitfaden zum Erstellen registrierter Dienste](../../configuration/mixed-reality-configuration-guide.md) (Bald verfügbar).

## <a name="launching-the-wizard"></a>Starten des Assistenten

Starten Sie den Assistenten über das Hauptmenü: **MixedRealityToolkit/Utilities/Create Extension Service** . Der Assistent führt Sie dann durch den Prozess zum Generieren Ihres Dienstskripts, der Schnittstelle und der Profilklasse.

## <a name="editing-your-service-script"></a>Bearbeiten ihres Dienstskripts

Standardmäßig werden Die neuen Skriptressourcen im `MixedRealityToolkit.Generated/Extensions` Ordner generiert. Nachdem Sie den Assistenten abgeschlossen haben, navigieren Sie hier, und öffnen Sie Ihr neues Dienstskript.

Generierte Dienstskripts enthalten einige Eingabeaufforderungen, die neuen MonoBehaviour-Skripts ähneln. Sie werden Sie darüber informieren, wo Sie Ihren Dienst initialisieren und aktualisieren müssen.

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

Wenn Sie sich für die Registrierung Ihres Diensts im Assistenten entschieden haben, müssen Sie nur dieses Skript bearbeiten, und Ihr Dienst wird automatisch aktualisiert. Andernfalls können Sie sich hier über [das Registrieren Ihres neuen Diensts informieren.](../../configuration/mixed-reality-configuration-guide.md)
