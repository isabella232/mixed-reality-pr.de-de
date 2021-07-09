---
title: Porting von HoloLens-Apps (1. Generation) zu HoloLens 2
description: Dieses Dokument richtet sich an Entwickler, die eine vorhandene App für HoloLens (1. Generation) und ältere MRTK-Versionen haben und diese nach MRTK Version 2 und HoloLens 2 portieren möchten.
author: hferrone
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, Test, MRTK, MRTK-Version 2, HoloLens 2, Unity, Portieren, HoloLens (1. Generation), Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Migration, Bewährte Methoden, ARM
ms.openlocfilehash: 512bd3e841d40ffd606d59ee4bb4d955306cc2d0
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042251"
---
# <a name="porting-hololens-1st-gen-apps-to-hololens-2"></a>Porting von HoloLens-Apps (1. Generation) zu HoloLens 2

Dieses Handbuch soll Entwickler bei der Portierung einer vorhandenen Unity-Anwendung für HoloLens (1. Generation) in eine Anwendung für HoloLens 2-Geräte zu unterstützen. Beim Portieren einer Unity-Anwendung für HoloLens (1. Generation) in eine Anwendung für HoloLens 2 gibt es vier wichtige Schritte. 

Die folgenden Abschnitte enthalten Detailinformationen zu den einzelnen Phasen:

| Schritt 1 | Schritt 2 | Schritt 3 | Schritt 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio-Logo](../images/visualstudio_logo.png) | ![Unity-Logo](../../design/images/logo-unity.png)| ![Unity-Symbol](../unity/images/hololens2_icon.jpg) | ![MRTK-Logo](../../design/images/74-12.png) |
| Herunterladen der aktuellen Tools | Aktualisieren des Unity-Projekts | Kompilieren für ARM | Migrieren zu MRTK Version 2

## <a name="prerequisites"></a>Voraussetzungen

Vor dem Beginn des Portierungsvorgangs **empfehlen wir dringend**, dass Sie mithilfe der Quellcodeverwaltung eine Momentaufnahme des ursprünglichen Zustands Ihrer Anwendungen speichern. Während des Vorgangs ist es außerdem empfehlenswert, zu verschiedenen Zeitpunkten einen Prüfpunktstatus zu *speichern*. Es kann auch hilfreich sein, eine weitere Unity-Instanz der ursprünglichen Anwendung zu erstellen, um die beiden während des Portierungsvorgangs parallel vergleichen zu können. 

> [!NOTE]
> Stellen Sie vor dem Portieren sicher, dass die aktuellen Tools für die Windows Mixed Reality-Entwicklung installiert sind. Bei den meisten bestehenden HoloLens-Entwicklern bedeutet dies ein Update auf die neueste Version von Visual Studio 2019 und die Installation des entsprechenden Windows-SDKs. Im weiteren Verlauf werden die verschiedenen Unity-Versionen und das Mixed Reality-Toolkit (MRTK) Version 2 näher erläutert.
>
> Weitere Informationen finden Sie unter [Installieren der Tools](../install-the-tools.md).

## <a name="migrate-project-to-the-latest-version-of-unity"></a>Migrieren des Projekts zur aktuellen Unity-Version

Wenn Sie [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)verwenden, wird empfohlen, vor dem Upgrade Ihres Projekts auf [Unity 2020.3 LTS](../unity/choosing-unity-version.md) auf MRTK 2.7 zu aktualisieren. MRTK 2.7 unterstützt Unity 2018, 2019 und 2020, sodass Sie sicherstellen können, dass Ihr Projekt bereits vor dem Upgrade von Unity für Unity 2020 bereit ist. Beurteilen Sie alle [Plug-In-Abhängigkeiten](https://docs.unity3d.com/Manual/Plugins.html), die derzeit in Ihrem Projekt vorhanden sind, und bestimmen Sie, ob diese DLLs für ARM64 erstellt werden können. Für Projekte mit einem von ARM64-Hardware abhängigen Plug-In müssen Sie möglicherweise damit fortfahren, Ihre App für ARM zu erstellen.

## <a name="update-sceneproject-settings-in-unity"></a>Aktualisieren von Szenen-/Projekteinstellungen in Unity

Nach dem Update auf [Unity 2020.3 LTS](https://unity3d.com/unity/qa/lts-releases) ist es für optimale Ergebnisse empfehlenswert, auf dem Gerät bestimmte Einstellungen in Unity zu aktualisieren. Diese Einstellungen werden ausführlich unter [Empfohlene Einstellungen für Unity](../unity/Recommended-settings-for-Unity.md) beschrieben.

Zur Erinnerung: Das [.NET-Back-End für die Skripterstellung](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) ist seit Unity 2018 veraltet und wurde in Unity 2019 **entfernt**. Entwickler sollten Ihre Projekte auf [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html) umstellen.

> [!NOTE]
> Das IL2CPP-Skriptverarbeitungs-Back-End kann von Unity bis zu Visual Studio längere Buildzeiten verursachen. Entwickler sollten ihren Entwicklungscomputer für eine [Optimierung der IL2CPP-Buildzeiten](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) einrichten.
> Es kann außerdem vorteilhaft sein, besonders für Unity-Projekte mit sehr vielen Ressourcen (mit Ausnahme von Skriptdateien) oder ständig wechselnden Szenen und Ressourcen, einen [Cacheserver](https://docs.unity3d.com/Manual/CacheServer.html) einzurichten. Beim Öffnen eines Projekts speichert Unity die qualifizierenden Ressourcen in einem internen Cacheformat auf dem Entwicklercomputer. Bei Änderungen müssen Elemente neu importiert und neu verarbeitet werden. Dieser Prozess kann einmal durchgeführt, in einem Cacheserver gespeichert und anschließend für andere Entwickler freigegeben werden, damit diese Zeit sparen und den erneuten Import der Änderungen nicht mehr einzeln und lokal verarbeiten müssen.

Wenn nach der Umstellung auf die aktualisierte Unity-Version alle Breaking Changes behoben wurden, erstellen Sie Ihre aktuellen Anwendungen auf HoloLens (1. Generation), und testen Sie sie. Dies ist ein guter Zeitpunkt, ein Commit in die Quellcodeverwaltung zu erstellen und zu speichern.

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Kompilieren von Abhängigkeiten/Plug-Ins für ARM-Prozessor

HoloLens (1. Generation) führt Anwendungen auf einem x86-Prozessor aus, während HoloLens 2 einen ARM-Prozessor verwendet. Vorhandene HoloLens-Anwendungen müssen für die Unterstützung von ARM portiert werden. Wie bereits erwähnt, unterstützt Unity 2018 LTS die Kompilierung von ARM32-Apps, während Unity 2019 und höher die Kompilierung von ARM32- und ARM64-Apps unterstützt. Die Entwicklung für ARM64-Anwendungen wird bevorzugt, da es einen wesentlichen Unterschied in Bezug auf die Leistung gibt. Dies setzt jedoch voraus, dass auch alle [Plug-In-Abhängigkeiten](https://docs.unity3d.com/Manual/Plugins.html) für ARM64 erstellt werden müssen.

Überprüfen Sie alle in Ihrer Anwendung vorhandenen DLL-Abhängigkeiten. Es empfiehlt sich, Abhängigkeiten zu entfernen, die für Ihr Projekt nicht mehr benötigt werden. Nehmen Sie für die verbleibenden Plug-Ins, die erforderlich sind, die entsprechenden ARM32- oder ARM64-Binärdateien in Ihr Unity-Projekt auf.

Erstellen Sie nach der Aufnahme der relevanten DLLs aus Unity eine Visual Studio-Projektmappe, und kompilieren Sie in Visual Studio eine AppX für ARM, um zu testen, ob Ihre Anwendung für ARM-Prozessoren erstellt werden kann. Es empfiehlt sich, die Anwendung als Commit in der Quellcodeverwaltungslösung zu speichern.

> [!IMPORTANT]
> Anwendungen, die MRTK v1 verwenden, können auf HoloLens 2 ausgeführt werden, nachdem das Buildziel in ARM geändert wurde, wobei vorausgesetzt wird, dass alle anderen Anforderungen erfüllt sind. Dies umfasst die Sicherstellung, dass Sie über ARM-Versionen aller Ihrer Plug-Ins verfügen. Ihre App erhält jedoch keinen Zugriff auf HoloLens 2-spezifische Funktionen wie artikuliertes Hand- und Eye-Tracking. MRTK v1 und MRTK v2 verfügen über unterschiedliche Namespaces, die ermöglichen, dass beide Versionen im selben Projekt vorkommen, was für den Übergang von einer Version zur anderen nützlich ist.

## <a name="update-to-mrtk-version-2"></a>Update auf MRTK Version 2

[MRTK Version 2](https://github.com/microsoft/MixedRealityToolkit-Unity) ist das neue Toolkit über Unity, das sowohl HoloLens (1. Generation) als auch HoloLens 2 unterstützt. Hier wurden auch alle neuen Funktionen der HoloLens 2 hinzugefügt, z. B. Handinteraktionen und Eyetracking.

Weitere Informationen zur Verwendung von MRTK Version 2 finden Sie in den folgenden Ressourcen:

- [Startseite der MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity)
- [Installationshandbuch](/windows/mixed-reality/mrtk-unity/install-the-tools)
- [MRTK – Handtracking](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
- [MRTK – Eyetracking](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

### <a name="prepare-for-the-migration"></a>Vorbereitungen für die Migration

Vor der Übernahme der neuen [*.unitypackage-Dateien für MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) ist es empfehlenswert, ein Inventar von **(1) jeglichem benutzerdefinierten Code, der in MRTK v1 integriert ist**, und **(2) jeglichem benutzerdefinierten Code für Eingabeinteraktionen oder Komponenten der Benutzerumgebung** zu erstellen. Ein häufiger und weit verbreiteter Konflikt, der bei der Aufnahme des MRTK v2 auftritt, bezieht sich auf Eingabe und Interaktionen. Ein Mixed Reality-Entwickler sollte unbedingt das [MRTK v2-Eingabemodell](/windows/mixed-reality/mrtk-unity/features/input/overview) lesen und verstehen.

Schließlich wurde beim neuen [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) die Umstellung von einem Modell mit Skripts und Managerobjekten in den Szenen zu einer Architektur mit Konfiguration und Dienstanbietern vollzogen. Daraus ergibt sich ein übersichtlicheres Szenenhierarchie- und Architekturmodell, das jedoch einen gewissen Lernaufwand erfordert, um die neuen Konfigurationsprofile zu verstehen. Lesen Sie das [Konfigurationshandbuch zum Mixed Reality-Toolkit](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide), um sich mit den wichtigen Einstellungen und Profilen zum Anpassen an die Anforderungen Ihrer Anwendung vertraut zu machen.

### <a name="migrating-the-project"></a>Migrieren des Projekts

Nach dem Import von [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) weist Ihr Unity-Projekt höchstwahrscheinlich viele compilerbezogene Fehler auf. Diese sind aufgrund der neuen Namespacestruktur und der neuen Komponentennamen häufig anzutreffen. Fahren Sie mit der Behebung dieser Fehler fort, indem Sie Ihre Skripts ändern und an die neuen Namespaces und Komponenten anpassen.

Informationen zu speziellen API-Unterschieden zwischen HTK/MRTK und MRTK v2, finden Sie im Portierungshandbuch im [MRTK Version 2-Wiki](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide).

### <a name="best-practices"></a>Empfohlene Methoden

- Bevorzugen Sie die Verwendung des [standardmäßigen MRTK-Shaders](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).
- Arbeiten Sie nur jeweils an einem wichtigen Änderungstyp (z.B. IFocusable in [IMixedRealityFocusHandler](/dotnet/api/microsoft.mixedreality.toolkit.input.imixedrealityfocushandler)).
- Führen Sie nach jeder Änderung einen Test aus, und nutzen Sie die Quellcodeverwaltung.
- Verwenden Sie nach Möglichkeit die MRTK-Standardbenutzerumgebung (Schaltflächen, Tafeln usw.).
- Ändern Sie MRTK Dateien nicht direkt, sondern erstellen Sie Wrapper um MRTK-Komponenten.
  - Diese Aktion erleichtert die zukünftige Erfassung und Updates des MRTK.
- Prüfen und untersuchen Sie die Beispielszenen, die im MRTK bereitgestellt werden, insbesondere *HandInteractionExamples.scene*.
- Erstellen Sie eine canvasbasierte Benutzeroberfläche neu mit Quads, Collidern und TextMeshPro-Text.
- Aktivieren Sie [gemeinsame Nutzung des Tiefenpuffers](../unity/camera-in-unity.md#sharing-depth-buffers) oder [Festlegen des Fokuspunkts](../unity/focus-point-in-unity.md). Verwenden Sie bevorzugt einen 16-Bit-Tiefenpuffer, um die Leistung zu verbessern. Stellen Sie sicher, dass Sie beim Rendern von Farbe auch Tiefe rendern. Unity schreibt im Allgemeinen keine Tiefe für transparente und Text-gameobjects.
- Legen Sie den Single Pass-instanziierten Renderingpfad fest.
- Verwenden Sie das [HoloLens 2-Konfigurationsprofil für MRTK](/windows/mixed-reality/mrtk-unity/features/profiles/profiles#hololens-2-profile)

### <a name="testing-your-application"></a>Testen der Anwendung

In MRTK Version 2 können Sie Handinteraktionen direkt in Unity simulieren und Entwicklungen mit den neuen APIs für Handinteraktionen und Eyetracking vornehmen. Das HoloLens 2-Gerät ist erforderlich, um eine zufriedenstellende Benutzererfahrung zu erzeugen. Ihnen wird empfohlen, die Dokumentation und die Tools zu studieren, um Ihr Verständnis zu erhöhen. [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) unterstützt die Entwicklung auf HoloLens (1. Generation), und es können herkömmliche Eingabemodelle wie die Auswahl durch Tippen in die Luft auf HoloLens (1. Generation) getestet werden. 

## <a name="updating-your-interaction-model-for-hololens-2"></a>Aktualisieren des Interaktionsmodells für HoloLens 2

> [!CAUTION]
> Wenn Ihr Projekt eine der XR.WSA-APIs verwendet: Diese werden in zukünftigen Unity-Releases zugunsten der neuen XR-Eingabe-APIs von Unity eingestellt. Weitere Informationen zu den [XR-Eingabe-APIs finden Sie hier](https://docs.unity3d.com/Manual/xr_input.html).

Nachdem Sie Ihre Anwendung portiert und für HoloLens 2 vorbereitet haben, können Sie die Aktualisierung Ihres Interaktionsmodells und der Hologrammentwurfsplatzierungen in Betracht ziehen.
In HoloLens (1. Generation) verfügt Ihre Anwendung wahrscheinlich über das Interaktionsmodell „Anvisieren und Ausführen“, bei dem die Hologramme relativ weit entfernt sind, damit sie in das Sichtfeld passen.

Schritte zum Aktualisieren Ihres Anwendungsentwurfs, damit dieser für HoloLens 2 optimal geeignet ist:
1.  MRTK-Komponenten: Wenn Sie [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) hinzugefügt haben, gibt es aufgrund der Vorarbeit verschiedene Komponenten/Skripts, die für HoloLens 2 konzipiert und optimiert wurden, und die Sie nutzen können.

2.  Interaktionsmodell: Ziehen Sie die Aktualisierung Ihres Interaktionsmodells in Betracht. In den meisten Fällen empfehlen wir, vom Anvisieren und Ausführen zur Handinteraktion zu wechseln. Wenn Sie mit Ihren Hologrammen, die sich in der Regel außer Reichweite befinden, zur Handinteraktion wechseln, ergibt sich daraus eine ferne Interaktion mit zielendem Lichtstrahl und Greifgesten.

3.  Hologrammplatzierung: Erwägen Sie nach dem Wechsel zum Handinteraktionsmodell, einige Hologramme in den Nahbereich zu verschieben, damit eine direkte Interaktion mit diesen mit den Händen über Greifgesten der nahen Interaktion möglich wird. Zu den Hologrammtypen, die zum direkten Greifen oder für eine direkte Interaktion in den Nahbereich verschoben werden sollten, zählen kleine Zielmenüs, Steuerelemente, Schaltflächen und kleinere Hologramme, die beim Greifen und Untersuchen des Hologramms in das HoloLens 2-Sichtfeld passen.
<br>
Jede Anwendung und jedes Szenario ist anders, und wir werden auch in Zukunft anhand von Feedback oder durch fortgesetztes Lernen Entwurfsrichtlinien optimieren und veröffentlichen.


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>Zusätzliche Einschränkungen und Erkenntnisse beim Verschieben von Anwendungen von x86 zu ARM

- Reine Unity-Anwendungen sind einfach, da Sie ein ARM-Anwendungspaket direkt auf dem Gerät erstellen oder bereitstellen können, auf dem das Paket laufen soll. Einige native Unity-Plug-Ins können bestimmte Herausforderungen bezüglich der Entwicklung darstellen. Aus diesem Grund müssen Sie ein Upgrade aller nativen Unity-Plug-Ins auf Visual Studio 2019 vornehmen und dann für ARM neu erstellen.

- Eine Anwendung hat das Unity AudioKinetic Wwise-Plug-In verwendet, und diese Version von Unity enthielt kein UWP ARM-Plug-In, was einen beträchtlichen Aufwand verursacht hat, um Soundfunktionen in der fraglichen Anwendung so neu zu konstruieren, dass sie auf ARM liefen. Stellen Sie sicher, dass alle erforderlichen Plug-Ins für Ihre Entwicklungspläne in Unity installiert und verfügbar sind.

- In manchen Fällen ist ein UWP/ARM-Plug-In für die Plug-Ins vorhanden, die für die Anwendung erforderlich sind, wodurch die Möglichkeit zum Portieren und Ausführen der Anwendung auf HoloLens 2 versperrt ist. Wenden Sie sich an Ihren Plug-In-Anbieter, um das Problem zu beheben und Support für ARM zu erhalten.

- Variablen des Typs „minfloat“ (und Varianten wie „min16float“, „minint“ usw.) in Shadern verhalten sich auf HoloLens 2 möglicherweise anders als auf HoloLens (1. Generation). Diese sorgen insbesondere dafür, dass „mindestens die angegebene Bitanzahl verwendet wird“. Auf Intel/Nvidia-GPUs werden minfloats größtenteils als 32-Bit behandelt. Auf ARM wird tatsächlich die angegebene Bitanzahl eingehalten. Dies bedeutet in der Praxis, dass diese Zahlen auf HoloLens 2 möglicherweise eine geringere Genauigkeit oder einen kleineren Bereich als auf HoloLens (1. Generation) aufweisen.

- Die „_asm“-Anweisungen funktionieren anscheinend auf ARM nicht, was bedeutet, dass jeder Code mit „_asm“-Anweisungen neu geschrieben werden muss.

- ARM unterstützt den SIMD-Instruktionssatz nicht, weil verschiedene Header wie „xmmintrin.h“, „emmintrin.h“," tmmintrin.h“ und „immintrin.h“ für ARM nicht verfügbar sind.

- Der Shader-Compiler auf ARM wird beim ersten Draw-Aufruf nach dem Laden des Shaders oder nach der Änderung einer Komponente, auf die sich der Shader stützt, ausgeführt, und nicht zur Ladezeit des Shaders. Die Auswirkung auf die Framerate kann – abhängig von der Anzahl der zu kompilierenden Shader – erkennbar sein. Dies hat Auswirkungen darauf, wie Shader auf HoloLens 2 im Vergleich zu HoloLens (1. Gen) behandelt, verpackt und aktualisiert werden sollten.

## <a name="see-also"></a>Siehe auch

* [Installieren der Tools](../install-the-tools.md)
* [MRTK – Installationshandbuch](/windows/mixed-reality/mrtk-unity/install-the-tools)
* [Startseite der MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity)
* [Portieren von HoloToolkit/MRTK zu MRTK, Version 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
* [Empfohlene Einstellungen für Unity](../unity/recommended-settings-for-unity.md)
* [Grundlegendes zur Leistung für Mixed Reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)