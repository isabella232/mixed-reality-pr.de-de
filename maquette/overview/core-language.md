---
title: Kernsprache
description: Erfahren Sie mehr über die Kernsprachdetails von Ma csv.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Ma bugs, prototyping, Mixed Reality, Virtual Reality, VR, MR, Feedback, Feedback-Hub, bugs
ms.openlocfilehash: 290b1442c3cc7fed10b315f4beeebfe2eab4a775d4909d5411c651362e24d94e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197400"
---
# <a name="maquettescript-core-language-details"></a>Details zur Kernsprache "Ma vbscript"

<!-- TODO(Harrison): Need consolidated logo with text -->
![Ma javascript-Logo– ](../images/MaquetteIcon.png) Ma javascriptScript Core Language Details (Details zur Ma javascript-Core-Sprache)

## <a name="accessing-maquette-object-and-namespace"></a>Zugreifen auf `Maquette` Objekt und Namespace

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Ma interfaces macht interne Objekte und Schnittstellen in JavaScript über das `Maquette` -Objekt und seine untergeordneten Elemente verfügbar. Diese Funktionalität wird in der [Dokumentation ma csv object and namespace (Ma csv-Objekt und -Namespace)](https://www.maquette.ms/doc_staging/objects/Maquette.html) beschrieben. 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Das `Maquette` Objekt verfügt über Funktionen der obersten Ebene, um die Interaktion mit Ma iterativen Funktionen zu vereinfachen und sich wiederholende Probleme einfacher zu lösen. Dies wird in der Dokumentation von [MaobjectScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)beschrieben.

## <a name="maquette-startup-and-loading"></a>Start und Laden von Ma bytes

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maconfig lädt und wertet bestimmte JavaScript-Dateien aus, um die Konfiguration, Einrichtung und Initialisierung zu den folgenden Zeiten zu aktivieren:

Beim Start von Ma bytes:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

Jedes Mal, wenn ein Projekt geladen wird:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

Projekte laden ihre jeweiligen Projektskripts:
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>JavaScript-Implementierung

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
Der in Ma csv verwendete JavaScript-Interpreter basiert auf [Jint](https://github.com/sebastienros/jint). Jint ist ECMAScript 5.1-kompatibel und unterstützt zusätzliche [Erweiterungen von ECMAScript 6.](https://github.com/sebastienros/jint/issues/343) 

Die Erweiterung `.mqjs` wird verwendet, um Ma javascript-Dateien von normalen JavaScript-Dateien zu unterscheiden.

## <a name="see-also"></a>Siehe auch 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->