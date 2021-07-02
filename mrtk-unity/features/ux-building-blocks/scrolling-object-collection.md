---
title: Scrollen der Objektsammlung
description: Übersichtsmenütypen MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, Scrolling Object
ms.openlocfilehash: a724b9fb4a0f72910e16353a6c76b9e31005a76e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176600"
---
# <a name="scrolling-object-collection"></a>Scrollen der Objektsammlung

![Scrollen der Objektsammlung](../images/scrolling-collection/ScrollingCollection_Main.jpg)

Die MRTK-Objektsammlung zum Scrollen ist eine UX-Komponente, die das Scrollen von 3D-Inhalten durch einen enthaltenen ansichtsbaren Bereich ermöglicht. Die Scrollbewegung kann durch nah oder ferne Eingabeinteraktion und durch diskrete Pagination ausgelöst werden. Sie unterstützt sowohl interaktive als auch nicht interaktive Objekte.

## <a name="getting-started-with-the-scrolling-object-collection"></a>Erste Schritte mit der Objektsammlung zum Scrollen

### <a name="setting-up-the-scene"></a>Einrichten der Szene

1. Erstellen Sie eine neue Unity-Szene.
1. Fügen Sie der Szene MRTK hinzu, indem Sie zum Mixed Reality **Toolkit** Add to Scene navigieren  >  **und konfigurieren.**

### <a name="setting-up-the-scrolling-object"></a>Einrichten des Scrollobjekts

1. Erstellen Sie ein leeres Spielobjekt in der Szene, und ändern Sie seine Position in (0, 0, 1).
1. Fügen Sie dem [Spielobjekt eine Scrollobjektsammlungskomponente](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) hinzu.

    Wenn die Bildlaufobjektsammlung hinzugefügt wird, werden [](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) automatisch ein Box-Collider und eine nahezu interaktionsfähige Komponente an das Stammspielobjekt angefügt. Mit diesen Komponenten kann das Bildlaufobjekt auf Eingabeereignisse in der Nähe und fernen Interaktion lauschen, z. B. eine Zeigereingabe oder ein Klick.  

    Die MRTK-Objektsammlung zum Scrollen verfügt über zwei wichtige Elemente, die als untergeordnete Spielobjekte unter der Stammobjekthierarchie erstellt werden:
    * `Container` – Alle Bildlaufinhaltsobjekte müssen dem Containerspielobjekt unter-nen.
    * `Clipping bounds` – Wenn die Bildlaufinhaltsmaskierung aktiviert ist, stellt das Clipping bounds-Element sicher, dass nur der scrollbare Inhalt innerhalb seiner Grenzen sichtbar ist. Das Spielobjekt für Clipping-Begrenzungen verfügt über zwei Komponenten: einen deaktivierten Feld-Collider und ein [Clippingfeld.](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)

![Scrollen von Objektsammlungselementen](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>Hinzufügen von Inhalt zum Bildlaufobjekt

Die Bildlaufobjektauf auflistung kann [](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) mit einer Rasterobjektaufsammlung kombiniert werden, um Inhalt in einem Raster ausgerichteter Elemente mit einheitlicher Größe und einheitlichem Abstand zu layouten.

1. Erstellen Sie ein leeres Spielobjekt als untergeordnetes Objekt des Scrollcontainers.
1. Fügen Sie dem Spielobjekt eine Rasterobjektsammlungskomponente hinzu.
1. Konfigurieren Sie für einen vertikalen Bildlauf mit einer einzelnen Spalte auf der Registerkarte Inspektor die Rasterobjektsammlung wie folgt:
    * **Num-Spalten:** 1
    * **Layout:** Spalte und dann Zeile
    * **Anker:** oben links
1. Ändern Sie **die Zellenbreite** **und -höhe** entsprechend den Dimensionen der Inhaltsobjekte.
1. Fügen Sie die Inhaltsobjekte als children des Rasterobjekts hinzu.
1. Klicken Sie **auf Updatesammlung**.

![Rasterlayout](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> Jedes Bildlaufinhaltsobjektmaterial muss den [MRTK-Standard-Shader](../rendering/MRTK-standard-shader.md) verwenden, damit der Clippingeffekt auf den anzeigebaren Bereich ordnungsgemäß funktioniert.

> [!NOTE]
> Wenn die Bildlaufinhaltsmaskierung aktiviert ist, [](../rendering/material-instance.md) fügt die Bildlaufobjektsammlung jedem Inhaltsobjekt, an das ein Renderer angefügt ist, eine Materialinstanzkomponente hinzu. Diese Komponente wird verwendet, um die Lebensdauer von Instanzmaterialien zu verwalten und die Arbeitsspeicherleistung zu verbessern.

### <a name="configuring-the-scrolling-viewable-area"></a>Konfigurieren des bildlaufbaren Bildlaufbereichs

1. Für vertikales Scrollen durch eine einzelne Spalte von Objekten konfigurieren Sie auf der Registerkarte Inspektor die Objektsammlung für den Bildlauf wie folgt:
    * **Zellen pro Ebene:** 1
    * Wählen Sie die Anzahl **der Ebenen pro Seite** entsprechend der gewünschten Anzahl sichtbarer Zeilen aus.
1. Ändern Sie **die Breite,** Höhe und **Tiefe** **der** Seitenzelle entsprechend den Dimensionen der Inhaltsobjekte.

Beachten Sie, dass die Inhaltsobjekte, die sich außerhalb des bildlaufbaren Bildlaufbereichs befinden, jetzt deaktiviert sind, während Objekte, die den Bildlauf-Wireframe überschneiden, vom Clippingprimitiven teilweise maskiert werden können.

![Einsetzbarer Bereich](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>Testen der Bildlaufobjektsammlung im Editor

1. Drücken Sie die Wiedergabe, und halten Sie die Leerzeichenleiste gedrückt, um eine Eingabesimulationshand zu zeigen.
1. Bewegen Sie die Hand so lange, bis sich der Scroll-Collider oder ein interaktiver Bildlaufinhalt im Fokus befindet, und lösen Sie die Scrollbewegung aus, indem Sie mit der linken Maus nach oben und unten klicken und ziehen.

## <a name="controlling-the-scrolling-object-from-code"></a>Steuern des Bildlaufobjekts aus dem Code

Die MRTK-Objektsammlung zum Scrollen macht einige öffentliche Methoden verfügbar, die das Verschieben des Scrollcontainers durch Ausrichten seiner Position gemäß der `pagination` Eigenschaftenkonfiguration ermöglichen.

Ein Beispiel für den Zugriff auf die Paginationsschnittstelle für scrollende Objektsammlungen finden Sie unter dem ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` Ordner . Das [Beispielskript für die scrollbare Pagination](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) kann mit jeder vorhandenen Bildlaufobjektsammlung in der Szene verknüpft werden. Auf das Skript kann dann von Szenenkomponenten verwiesen werden, die Unity-Ereignisse verfügbar machen (z.B. [MRTK-Schaltfläche).](button.md)

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }
}
```

## <a name="scrolling-object-collection-properties"></a>Scrollen von Objektsammlungseigenschaften

| Allgemein          | Beschreibung                                   |
| :--------------- | :-------------------------------------------- |
| Scrollrichtung | Die Richtung, in die der Inhalt scrollen soll. |

| Paginierung     | Beschreibung                                                                                               |
| :------------- | :-------------------------------------------------------------------------------------------------------- |
| Zellen pro Ebene | Anzahl der Zellen in einer Zeile in der Bildlaufansicht nach oben oder Anzahl von Zellen in einer Spalte in der Bildlaufansicht links rechts. |
| Ebenen pro Seite | Anzahl der sichtbaren Ebenen im Scrollbereich.                                                            |
| Seitenzelle      | Dimensionen der Paginationszelle.                                                                        |

| Erweiterte Einstellungen           | Beschreibung                                                                                                                                                                |
| :-------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Maskierungsbearbeitungsmodus              | Bearbeitungsmodi zum Definieren der Begrenzungen für die Beschneidungsfeldmaskierung. "Auto" verwendet automatisch Paginationswerte. "Manuell" ermöglicht die direkte Bearbeitung des Clipping box-Objekts. |
| Collider-Bearbeitungsmodus          | Bearbeitungsmodi zum Definieren der Begrenzungen des Scrollinteraktions-Colliders. "Auto" verwendet automatisch Paginationswerte. "Manuell" ermöglicht die direkte Manipulation des Colliders.     |
| Scrollen kann                  | Aktiviert/deaktiviert das Scrollen mit Nah-/Ferninteraktion.                                                                                                                      |
| Verwenden beim Vorrendering           | Umschalten, ob scrollingObjectCollection das Camera OnPreRender-Ereignis verwendet, um die Sichtbarkeit von Inhalten zu verwalten.                                                          |
| Paginationskurve            | Animationskurve für pagination.                                                                                                                                            |
| Animationslänge            | Die Zeit (in Sekunden), die die PaginationCurve für die Auswertung dauert.                                                                                                 |
| Schwellenwert für Handdelta-Bildlauf | Die Entfernung in Metern, die der aktuelle Zeiger entlang der Bildlaufrichtung bewegen kann, bevor ein Bildlaufziehpunkt ausgelöst wird.                                                        |
| Abstand der Touch-Front-Touch-Verbindung        | Abstand in Metern, um eine lokale Xy-Ebene zu positionieren, die verwendet wird, um zu überprüfen, ob eine Touchinteraktion am Anfang der Bildlaufansicht gestartet wurde.                                           |
| Releaseschwellenwert           | Betrag in Metern von den Bildlaufgrenzen abgenommen, die für den Übergang von touch eingeschaltet zu freigegeben erforderlich sind.                                                                |

| Geschwindigkeit            | Beschreibung                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------- |
| Geschwindigkeitstyp    | Der gewünschte Typ des Geschwindigkeitsfalloffs für den Scroller.                                                      |
| Geschwindigkeitsmultiplikator | Die Menge der (zusätzlichen) Geschwindigkeit, die auf den Scroller angewendet werden soll.                                                       |
| Geschwindigkeitsdämpfung     | Die Menge des auf die Geschwindigkeit angewendeten Falloffs.                                                                  |
| Bounce-Multiplikator   | Multiplikator zum Hinzufügen eines zusätzlichen Bounces zum Overscroll einer Liste bei Verwendung von Falloff pro Frame oder Falloff pro Element. |

| Debugoptionen         | Beschreibung                                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| Maskierung aktiviert          | Sichtbarkeitsmodus von Bildlaufinhalten. Der Standardwert maskiert alle Objekte außerhalb des bildlauffähigen Bereichs. |
| Anzeigen von Schwellenwertebenen | True gibt an, dass der Editor die Schwellenwertebenen für touch-Freigaben um die Scrollgrenzen rendert.            |
| Debugpaginierung      | Verwenden Sie diesen Abschnitt, um die Scrollpaginierung während der Laufzeit zu debuggen.                                             |

| Events              | BESCHREIBUNG                                                                                                                   |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Klicken Sie auf            | Wird ausgelöst, wenn der Bildlaufhintergrund-Collider oder einer seiner interaktiven Inhalte einen Klick empfängt.                             |
| On touch started (Bei Berührung gestartet)    | Wird ausgelöst, wenn der Bildlaufhintergrund-Collider oder einer seiner interaktiven Inhalte eine Nahinteraktion empfängt.            |
| Bei Berührung beendet      | Wird ausgelöst, wenn eine aktive Touchinteraktion beendet wird, wenn der Near Interaction-Zeiger eine Freigabeschwellenwertebene überschreitet. |
| Bei Beginn der Entwicklung | Wird ausgelöst, wenn der Scrollcontainer durch Interaktion, Geschwindigkeitsfalloff oder Paginierung verschoben wird.                            |
| Am Ende der Zeit   | Wird ausgelöst, wenn sich der Scrollcontainer nicht mehr durch Interaktion, Geschwindigkeitsfalloff oder Paginierung bewegt.                             |

## <a name="scrolling-example-scene"></a>Bildlaufbeispielszene

**ScrollingObjectCollection.unity-Beispielszene** besteht aus drei bildlauffähigen Beispielen, die jeweils eine andere Geschwindigkeitsfalloffkonfiguration aufweisen. Die Beispielszene enthält Wände, um das Oberflächenplatzierungsverhalten anzuzeigen, das standardmäßig in der Hierarchie deaktiviert ist. Die Beispielszene befindet sich unter dem ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` Ordner .

![Beispielszene für bildlaufende Objektsammlungen](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>Scrollen von Beispielpräfabs

Der Einfachheit halber stehen zwei Prefabs für bildlaufende Objektsammlungen zur Verfügung. Die Beispiel-Prefabs finden Sie unter dem ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` Ordner .

![Scrollen von Objektsammlungs-Prefabs](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>Siehe auch

* [Zuschnitt-Primitiv](../rendering/clipping-primitive.md)
* [Materialinstanz](../rendering/material-instance.md)
* [Standard-Shader](../rendering/MRTK-standard-shader.md)
* [Objektsammlung](object-collection.md)
