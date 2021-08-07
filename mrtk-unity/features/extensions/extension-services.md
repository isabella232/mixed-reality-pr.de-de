---
title: Erweiterungsdienste
description: Dokumentation zu erweiterten Funktionen in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 0f9f30bb7d2d44cef828b79bc916d933a6355dbb1068b09e73317d1c977ef45a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186996"
---
# <a name="extension-services"></a>Erweiterungsdienste

Erweiterungsdienste sind Komponenten, die die Funktionalität des Mixed Reality Toolkits erweitern. Diese Dienste können vom MRTK oder von anderen Parteien bereitgestellt werden.

## <a name="creating-an-extension-service"></a>Erstellen eines Erweiterungsdiensts

Die effizienteste Möglichkeit zum Erstellen eines Erweiterungsdiensts ist die Verwendung des Assistenten zum [Erstellen des Erweiterungsdiensts.](../tools/extension-service-creation-wizard.md)
Wählen Sie zum Starten des Assistenten zum Erstellen des Erweiterungsdiensts **Mixed Reality Toolkit > Hilfsprogramme > Erweiterungsdienst erstellen** aus.

![Assistent zum Erstellen von Erweiterungsdiensten](../images/extension-wizard/ExtensionServiceCreationWizard.png)

Der Assistent automatisiert die Erstellung der Dienstkomponenten und stellt die ordnungsgemäße Schnittstellenvererbung sicher.

![Vom Assistenten zum Erstellen des Erweiterungsdiensts erstellte Komponenten](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> In MRTK Version 2.0.0 gibt es ein Problem im Assistenten für Erweiterungsdienst, bei dem der Dienstinspektor und das Dienstprofil generiert werden müssen. Weitere Informationen finden Sie im Issue [5654.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654)

Nach Abschluss des Assistenten kann die Dienstfunktion implementiert werden.

## <a name="registering-an-extension-service"></a>Registrieren eines Erweiterungsdiensts

Damit eine Anwendung darauf zugreifen kann, muss der neue Erweiterungsdienst beim Mixed Reality Toolkit registriert werden.

Der Assistent zum Erstellen des Erweiterungsdiensts kann zum Registrieren des Diensts verwendet werden.

![Registrierung des Assistenten zum Erstellen eines Erweiterungsdiensts](../images/extension-wizard/ExtensionServiceWizardRegister.png)

Der Dienst kann auch manuell mithilfe des Konfigurationsinspektors Mixed Reality Toolkit registriert werden.

![Registrierung des manuellen Erweiterungsdiensts](../images/profiles/RegisterExtensionService.png)

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
- [Assistent zum Erstellen von Erweiterungsdiensten](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
