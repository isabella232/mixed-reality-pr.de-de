---
title: Verwenden des Unity-Paket-Managers
description: Verwenden von MRTK in Unity Paket-Manager
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK-Pakete,
ms.openlocfilehash: fb96a910b86e8ec9f6d73b8239e0ae008ea021c65f2c52edc613d2fe02719e58
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194466"
---
# <a name="using-the-unity-package-manager"></a>Verwenden des Unity-Paket-Managers

Ab Version 2.5.0 kann das Microsoft Mixed Reality Toolkit mithilfe des [Mixed Reality Feature Tools](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)in unity Paket-Manager (UPM) integriert werden, wenn Unity 2019.4 und höher verwendet wird.

## <a name="using-the-mixed-reality-feature-tool"></a>Verwenden des Mixed Reality-Featuretools

Wie unter [Willkommen beim Mixed Reality Feature-Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) beschrieben, können Sie das Tool über diesen [Link](https://aka.ms/MRFeatureTool)herunterladen.

> [!IMPORTANT]
> Wenn das Manifest des Projekts über einen `Microsoft Mixed Reality` Eintrag im `scopedRegistries` Abschnitt verfügt, wird empfohlen, es zu entfernen.
>
> Um eine konfigurierte Bereichsregistrierung zu entfernen, gehen Sie zu `Edit`  >  `Project Settings`  >  `Package Manager` .
>
> ![Entfernen einer bereichsbegrenzten Registrierung](../features/images/packaging/RemoveScopedRegistry.png)

MRTK-Pakete werden beim Ermitteln von Features unter der `Mixed Reality Toolkit` Überschrift angezeigt.

![Entdecken von Features](../features/images/packaging/DiscoverFeatures.png)

Wenn Sie Features auswählen, müssen Sie sich nicht um erforderliche Abhängigkeiten kümmern. Das Tool lädt sie automatisch herunter und integriert sie in das Projekt.

![Erforderliche Abhängigkeiten](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Verwalten Mixed Reality Features mit dem Unity-Paket-Manager

Nachdem dem Paketmanifest ein Mixed Reality Toolkit-Paket hinzugefügt wurde, kann es über die Benutzeroberfläche von Unity Paket-Manager verwaltet werden.

![MRTK Foundation UPM-Paket](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Wenn ein Mixed Reality Toolkit-Paket mithilfe des Unity-Paket-Manager entfernt wird, muss es mithilfe der [zuvor beschriebenen Schritte](#using-the-mixed-reality-feature-tool)erneut hinzugefügt werden.

### <a name="using-mixed-reality-toolkit-examples"></a>Verwenden von Beispielen für Mixed Reality Toolkit

Im Gegensatz zur Verwendung von Assetpaketdateien (UNITYPACKAGE) `com.microsoft.mixedreality.toolkit.examples` und importieren Sie die `com.microsoft.mixedreality.toolkit.handphysicsservice` Beispielszenen und Objekte nicht automatisch.

Führen Sie die folgenden Schritte aus, um eines oder mehrere der Beispiele zu verwenden:

1. Navigieren Sie im Unity-Editor zu . `Window` > `Package Manager`
1. Wählen Sie in der Liste der Pakete die Option aus. `Mixed Reality Toolkit Examples`
1. Suchen Sie die gewünschten Stichproben in der `Samples` Liste.
1. Klicken Sie auf `Import into Project`.

![Importieren von Beispielen](../features/images/packaging/MRTK_ExamplesUpm.png)

Wenn ein Beispielpaket aktualisiert wird, bietet Unity die Option zum Aktualisieren importierter Beispiele.

> [!NOTE]
> Beim Aktualisieren eines importierten Beispiels werden alle Änderungen überschrieben, die an diesem Beispiel und den zugehörigen Ressourcen vorgenommen wurden.

## <a name="see-also"></a>Weitere Informationen

- [Mixed Reality Toolkit-Pakete](../packages/mrtk-packages.md)
