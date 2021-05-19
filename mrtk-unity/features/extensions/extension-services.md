---
title: Erweiterungsdienste
description: Dokumentation für erweiterte Funktionen in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: a39616a091a3f6800c429dc797ec2f3130e96f40
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144539"
---
# <a name="extension-services"></a>Erweiterungsdienste

Erweiterungsdienste sind Komponenten, die die Funktionalität des Mixed Reality-Toolkits erweitern. Diese Dienste können vom MRTK oder von anderen Parteien bereitgestellt werden.

## <a name="creating-an-extension-service"></a>Erstellen eines Erweiterungsdiensts

Die effizienteste Methode zum Erstellen eines Erweiterungsdiensts ist die Verwendung des Assistenten zum Erstellen [des Erweiterungsdiensts.](../tools/extension-service-creation-wizard.md)
Wählen Sie zum Starten des Assistenten zum Erstellen des Erweiterungsdiensts Mixed Reality **Toolkit > Hilfsprogramme > Erweiterungsdienst erstellen aus.**

![Assistent zum Erstellen des Erweiterungsdiensts](../images/extension-wizard/ExtensionServiceCreationWizard.png)

Der Assistent automatisiert die Erstellung der Dienstkomponenten und stellt die ordnungsgemäße Schnittstellenvererbung sicher.

![Vom Assistenten zum Erstellen des Erweiterungsdiensts erstellte Komponenten](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> In MRTK Version 2.0.0 liegt ein Problem im Erweiterungsdienst-Assistenten vor, bei dem der Dienstinspektor und das Dienstprofil generiert werden müssen. Weitere Informationen finden [Sie im Issue 5654.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654)

Nach Abschluss des Assistenten kann die Dienstfunktionalität implementiert werden.

## <a name="registering-an-extension-service"></a>Registrieren eines Erweiterungsdiensts

Um für eine Anwendung zugänglich zu sein, muss der neue Erweiterungsdienst beim Mixed Reality Werden registriert werden.

Der Assistent zum Erstellen des Erweiterungsdiensts kann verwendet werden, um den Dienst zu registrieren.

![Registrierung des Assistenten zum Erstellen des Erweiterungsdiensts](../images/extension-wizard/ExtensionServiceWizardRegister.png)

Der Dienst kann auch manuell mithilfe des Konfigurationsinspektors Mixed Reality Toolkits registriert werden.

![Manuelle Registrierung des Erweiterungsdiensts](../images/profiles/RegisterExtensionService.png)

Wenn der Erweiterungsdienst ein Profil verwendet, stellen Sie sicher, dass es im Inspektor angegeben ist.

![Konfigurierter Erweiterungsdienst](../images/profiles/ConfiguredExtensionService.png)

Der Komponentenname und die Priorität können ebenfalls angepasst werden.

## <a name="accessing-an-extension-service"></a>Zugreifen auf einen Erweiterungsdienst

Auf Erweiterungsdienste wird im Code mithilfe von zugegriffen, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) wie im folgenden Beispiel gezeigt.

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>Weitere Informationen

- [Systeme, Erweiterungsdienste und Datenanbieter](../../architecture/systems-extensions-providers.md)
- [Assistent zum Erstellen eines Erweiterungsdiensts](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
