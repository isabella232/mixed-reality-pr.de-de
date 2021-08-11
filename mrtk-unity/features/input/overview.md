---
title: Übersicht über die Eingabe
description: Übersicht über das Eingabesystem im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: b175b16e2004fb00cef430335751c3aabc8c59fdd4ae78a2fc78c959a92240fb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219760"
---
# <a name="input-overview"></a>Eingabeübersicht

Das Eingabesystem im MRTK ermöglicht Ihnen:

- Nutzen Sie Eingaben aus einer Vielzahl von Eingabequellen, z. B. 6 DOF-Controller, artikulierte Hände oder Sprache, über Eingabeereignisse.
- Definieren Sie abstrakte Aktionen wie *Select* oder *Menu*, und ordnen Sie sie verschiedenen Eingaben zu.
- Richten Sie Zeiger ein, die an Controller angefügt sind, um Ui-Komponenten über Fokus- und Zeigerereignisse zu verwenden.

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Übersicht über das MRTK-Eingabesystem</sup>

Eingaben werden von [**Eingabedatenanbietern (Geräte-Manager) erstellt.**](input-providers.md) Jeder Anbieter entspricht einer bestimmten Eingabequelle: Open VR, Windows Mixed Reality (WMR), Unity Unity, Windows Speech usw. Anbieter werden Ihrem Projekt über das Profil "Registrierte Dienstanbieter" **in** [](input-events.md) der Komponente *"Mixed Reality Toolkit"* hinzugefügt und erzeugen automatisch Eingabeereignisse, wenn die entsprechenden Eingabequellen verfügbar sind (z. B. wenn ein WMR-Controller erkannt oder ein Gamepad verbunden ist).

[**Eingabeaktionen sind**](input-actions.md) Abstraktionen von rohen Eingaben, die dazu beitragen sollen, die Anwendungslogik von den spezifischen Eingabequellen zu isolieren, die eine Eingabe erzeugen. Es kann beispielsweise nützlich sein, eine *Select-Aktion* zu definieren und sie der linken Maustaste, einer Schaltfläche in einem Gamepad und einem Trigger in einem 6-DOF-Controller zu zuordnen. Sie können ihre Anwendungslogik dann  auf Ereignisse der Aktion Eingabe auswählen lauschen lassen, anstatt alle verschiedenen Eingaben kennen zu müssen, die sie erzeugen können. Eingabeaktionen werden im Eingabeaktionenprofil **definiert,** das im *Eingabesystemprofil* in der Mixed Reality *Toolkit-Komponente enthalten* ist.

[**Controller**](controllers.md) werden von *Eingabeanbietern erstellt,* wenn Eingabegeräte erkannt und zerstört werden, wenn sie verloren gehen oder getrennt werden. Der WMR-Eingabeanbieter erstellt z. B. *WMR-Controller* für 6 DOF-Geräte und *WMR-Handcontroller* mit Artikulierten Händen. Controllereingaben können Eingabeaktionen über das **Controllerzuordnungsprofil** innerhalb des *Eingabesystemprofils zugeordnet werden.* Eingabeereignisse, die von Controllern ausgelöst werden, enthalten gegebenenfalls die zugeordnete Eingabeaktion.

Controllern können [**Zeiger angefügt**](pointers.md) sein, die die Szene abfragen, um das Spielobjekt mit Fokus zu bestimmen und [**Zeigerereignisse darauf**](pointers.md#pointer-event-interfaces) zu setzen. Als Beispiel führt unser *Linienzeiger* einen Raycast für die Szene aus, indem er die Controllerpose verwendet, um den Ursprung und die Richtung des Strahls zu berechnen. Die für jeden Controller erstellten Zeiger werden im **Zeigerprofil** unter dem *Eingabesystemprofil eingerichtet.*

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Ereignisfluss.</sup>

Obwohl Sie Eingabeereignisse direkt [in](input-events.md)Benutzeroberflächenkomponenten [](pointers.md#pointer-event-interfaces) verarbeiten können, wird empfohlen, Zeigerereignisse zu verwenden, um die Implementierung geräteunabhängig zu halten.

MRTK bietet auch mehrere komfortable Methoden zum direkten Abfragen des Eingabezustands auf geräteunabhängige Weise. Weitere [Informationen finden Sie unter Zugreifen auf den Eingabezustand im MRTK.](input-state.md)
