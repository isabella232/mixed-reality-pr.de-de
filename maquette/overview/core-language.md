---
title: Kernsprache
description: Erfahren Sie mehr über die Details der Kernsprache von Maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, Prototyperstellung, gemischte Realität, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935537"
---
# <a name="maquettescript-core-language-details"></a>Details der maquettescript-Kernsprache

<!-- TODO(Harrison): Need consolidated logo with text -->
![Makett-Logo ](../images/MaquetteIcon.png) maquettescript-Kern Sprachen Details

## <a name="accessing-maquette-object-and-namespace"></a>Zugreifen auf `Maquette` Objekt und Namespace

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette macht interne Objekte und Schnittstellen in JavaScript durch das `Maquette` -Objekt und seine untergeordneten Elemente verfügbar. Diese Funktionalität wird in der Dokumentation zu [Maquette-Objekten und Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) beschrieben. 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Das `Maquette` -Objekt verfügt über Funktionen der obersten Ebene, um die Interaktion mit Maquette selbst zu vereinfachen und sich wiederholende Probleme leichter lösen zu können. Dies wird in der Dokumentation von [maquettescriptobject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)beschrieben.

## <a name="maquette-startup-and-loading"></a>Starten und Laden von Maketten

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette lädt und wertet bestimmte JavaScript-Dateien aus, um die Konfiguration, Einrichtung und Initialisierung zu folgenden Zeitpunkten zu ermöglichen:

Beim Starten der Makette:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

Jedes Mal, wenn ein Projekt geladen wird:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

Projekte laden ihre jeweiligen Projekt Skripts:
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>JavaScript-Implementierung

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
Der in Maquette verwendete JavaScript-Interpreter basiert auf [Jint](https://github.com/sebastienros/jint). Jint ist ECMAScript 5,1-kompatibel und unterstützt zusätzliche [Erweiterungen von ECMAScript 6](https://github.com/sebastienros/jint/issues/343). 

Die Erweiterung `.mqjs` wird verwendet, um Makett-JavaScript-Dateien von normalem JavaScript zu unterscheiden.

## <a name="see-also"></a>Weitere Informationen 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->