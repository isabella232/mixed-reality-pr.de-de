---
title: Allgemeine bewährte Methoden
description: Bleiben Sie auf dem neuesten Stand bei allen empfohlenen bewährten Methoden für die Entwicklung von Mixed Reality-Anwendungen in der Unreal Engine.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Editor-Erweiterungen, Unreal-Editor, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Dokumentation, Leitfäden, Features, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Portieren, Upgrade
ms.openlocfilehash: 822e64d873952bdb4bb1fb91da4c85f956a1eb513c92d4afee7bfebb18a824eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203266"
---
# <a name="general-best-practices"></a>Allgemeine bewährte Methoden

Im Folgenden finden Sie einige allgemeine bewährte Methoden, deren Einhaltung wir allen Entwicklern bei der Erstellung eines Unreal Engine-Projekts für Mixed Reality empfehlen.

## <a name="constructors"></a>Konstruktoren

Wenn Sie das Äquivalent eines „Konstruktors“ in Blaupausen benötigen, verwenden Sie das [Konstruktionsskript](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html) von Unreal. Der Hauptvorteil gegenüber der Verwendung von „BeginPlay“-Ereignissen besteht darin, dass das Konstruktionsskript ebenfalls im Editor ausgeführt wird. In den meisten Fällen können die Werte direkt beim Start oder sogar zum Zeitpunkt der Kompilierung zwischengespeichert werden.

> [!NOTE]
> Weitere hilfreiche Informationen zu Konstruktionsskripts finden Sie in unserer [Übersicht der Editor-Erweiterungen](unreal-editor-extensions.md#construction-scripts).

## <a name="3d-buttons-and-textures"></a>3D-Schaltflächen und Texturen

Es ist ganz natürlich, bei der Erstellung oder Planung der Verwendung von 3D-Schaltflächen in Mixed Reality-Anwendungen an die Leistung zu denken. Allerdings muss nicht alles aus Gittermodellen erstellt werden, um als 3D wahrgenommen zu werden. Sie haben die Möglichkeit, Paper2D mit sorgfältig erstellten Texturen zu verwenden, um diese 3D-Optik zu erhalten. Dies funktioniert hervorragend für Schaltflächen, die „wie 3D“ aussehen, aber nur bearbeitete Bilder auf einem Quader sind. Eine ausgefallene Version davon wird als [Sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html) bezeichnet.

## <a name="variants"></a>Varianten

Verwenden Sie [Unreal-Varianten](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) in Szenarien, in denen Sie eine Szene mit mehreren Objektkonfigurationen zur Laufzeit erstellen. Variationen können veränderliche Materialien oder Gittermodelle umfassen. 

## <a name="animation"></a>Animation

Profitieren Sie von der [Splinekomponente](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (nicht der „Gittermodell“-Splinekomponente) und von [Zeitachsenknoten](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html), wenn Sie viele „interagierende Animationen“ erstellen. 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>Kommunikation

Verwenden Sie eine [Ebenenblaupause](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html), wenn Sie Probleme beim dynamischen Auffinden von Objekten haben oder zu viel Bandbreite für die Kommunikation zwischen mehreren Akteuren und Blaupausen aufwenden. Denken Sie daran, dass Unreal Engine 4 nicht wie Unity funktioniert – es muss sich nicht alles innerhalb einer Komponente befinden. Ebenenblaupausen sind eine absolut gültige und empfohlene Methode zur Vereinfachung der Kommunikation zwischen mehreren Akteuren. Objektverweise können beim Start sogar im „OnBeginPlay“-Ereignis der Ebenenblaupause „zwischengespeichert“ werden.

## <a name="global-state"></a>Globaler Zustand

Sie müssen häufig ebenenspezifische Zustände wie Ergebnisse/Score, Ebenendaten, spielerspezifische Informationen oder alles andere speichern, das nicht direkt zu einem bestimmten Objekt gehört. Übersehen Sie den [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html) nicht. Die meisten vergessen, dass es ihn gibt, aber der GameMode kann pro Ebene erstellt werden und Daten enthalten, die für die jeweilige Ebene spezifisch sind.

## <a name="optimizing-blueprints"></a>Optimieren von Blaupausen

Wenn Sie feststellen, dass Ihre Blaupausen zu langsam sind, lassen Sie Unreal Ihre Blaupausen „nativisieren“, bevor Sie den Code in C++ neu schreiben. Probieren Sie zuerst die automatische [Nativisierung](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) aus, bevor Sie Ihre eigene benutzerdefinierte Lösung erstellen.

![Blaupauseneinstellung mit Nativisierungsmethode für die Blaupause und hervorgehobenem „Inclusive“ (einschließend).](images/unreal-general-practices-img-01.jpg)
