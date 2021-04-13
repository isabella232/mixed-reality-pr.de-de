---
title: Scrolling-Objektsammlung
description: Übersichts Menü Typen mrtk
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity, hololens, hololens 2, gemischte Realität, Entwicklung, mrtk, scrollobjekt
ms.openlocfilehash: 0ed1d61aed203a5daa45c5d89990e66115cc3abb
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300115"
---
# <a name="scrolling-object-collection"></a>Bildlauf-Objekt Auflistung

![Bildlauf-Objekt Auflistung](../images/scrolling-collection/ScrollingCollection_Main.jpg)

Die mrtk-scrollobjektauflistung ist eine UX-Komponente, die das Scrollen von 3D-Inhalten über einen enthaltenen sichtbaren Bereich ermöglicht. Die scrollbewegung kann durch die Near-oder die weite Eingabe Interaktion und durch diskrete Paginierung ausgelöst werden. Es unterstützt interaktive und nicht interaktive Objekte.

## <a name="getting-started-with-the-scrolling-object-collection"></a>Ersten Schritte mit der scrollobjektauflistung

### <a name="setting-up-the-scene"></a>Einrichten der Szene

1. Erstellen Sie eine neue Unity-Szene.
1. Fügen Sie mrtk der Szene hinzu, indem Sie zum **Mixed Reality-Toolkit** navigieren, das  >  **Sie zu Szene hinzufügen und konfigurieren**.

### <a name="setting-up-the-scrolling-object"></a>Einrichten des scrollobjekts

1. Erstellen Sie ein leeres Spielobjekt in der Szene, und ändern Sie seine Position in (0,0).
1. Fügen Sie dem Spielobjekt eine Komponente für die Bild Lauf [Objekt](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) Auflistung hinzu.

    Wenn die scrollobjektauflistung hinzugefügt wird, werden ein Box-Collider und eine [touchfähige Komponente der Near-Interaktion](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) automatisch an das Stamm Spielobjekt angefügt. Diese Komponenten ermöglichen es dem Bild Lauf Objekt, auf Eingabeereignisse der Near-und Far-Interaktion zu lauschen, wie z. b. ein Zeiger oder ein Klick  

    Die mrtk-scrollobjektauflistung verfügt über zwei wichtige Elemente, die als untergeordnete Spielobjekte in der Objekthierarchie des Stamm Bildlaufs erstellt werden:
    * `Container` -Alle scrollinhaltsobjekte müssen untergeordnete Elemente des Container Spiel Objekts sein.
    * `Clipping bounds` -Wenn scrollinhalts Maskierung aktiviert ist, stellt das clippingbounds-Element sicher, dass nur der Bild lauffähige Inhalt in seinen Grenzen sichtbar ist. Das clippingbounds-Spielobjekt hat zwei Komponenten: einen deaktivierten Box-Collider und ein [clippingbox](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).

![Scrollen von Objekt Auflistungs Elementen](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>Hinzufügen von Inhalt zum scrollobjekt

Die scrollobjektauflistung kann mit einer [Raster Objekt](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) Auflistung kombiniert werden, um Inhalt in einem Raster von ausgerichteten Elementen mit einheitlicher Größe und Abstand zu Layout.

1. Erstellen Sie ein leeres Spielobjekt als untergeordnetes Element des scrollcontainers.
1. Fügen Sie eine Raster Objekt Auflistungs Komponente zum Spielobjekt hinzu.
1. Konfigurieren Sie für einen vertikalen Bildlauf mit einer einzelnen Spalte auf der Registerkarte Inspektor die Raster Objekt Auflistung wie folgt:
    * **NUM Spalten**: 1
    * **Layout**: Spalte und Zeile
    * **Anker**: oben links
1. Ändern Sie die Breite und **Höhe** der **Zelle** entsprechend den Dimensionen der Inhalts Objekte.
1. Fügen Sie die Inhalts Objekte dem Raster Objekt als untergeordnete Elemente hinzu.
1. Klicken Sie auf **Sammlung aktualisieren**.

![Rasterlayout](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> Alle Bild Lauf Inhalts Objekt Materialien müssen den [mrtk-Standard-Shader](../rendering/MRTK-standard-shader.md) verwenden, damit der Clipping-Effekt auf den sichtbaren Bereich ordnungsgemäß funktioniert.

> [!NOTE]
> Wenn scrollinhaltsmaskierung aktiviert ist, fügt die scrollobjektauflistung allen Inhalts Objekten, denen ein Renderer angefügt ist, eine Komponente für [Material Instanzen](../rendering/material-instance.md) hinzu. Diese Komponente dient zum Verwalten der Lebensdauer von instanzierten Materialien und zur Verbesserung der Arbeitsspeicher Leistung.

### <a name="configuring-the-scrolling-viewable-area"></a>Konfigurieren des sichtbaren scrollbaren Bereichs

1. Für einen vertikalen Bildlauf durch eine einzelne Spalte von Objekten konfigurieren Sie auf der Registerkarte Inspektor die scrollobjektauflistung wie folgt:
    * **Zellen pro Ebene**: 1
    * Wählen Sie die Anzahl der **Ebenen pro Seite** gemäß der gewünschten Anzahl sichtbarer Zeilen aus.
1. Ändern Sie die Breite, **Höhe** und **Tiefe** der **Seiten Zellen** entsprechend den Dimensionen der Inhalts Objekte.

Beachten Sie, dass die Inhalts Objekte, die sich außerhalb des sichtbaren scrollfähigen Bereichs befinden, jetzt deaktiviert sind, während Objekte, die den scrollwireframe überschneiden, möglicherweise teilweise durch das clippingprimitive maskiert werden.

![Sichtbarer Bereich](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>Testen der scrollobjektauflistung im Editor

1. Halten Sie die Leertaste gedrückt, um eine Eingabe Simulations Seite anzuzeigen.
1. Verschieben Sie die Hand, bis der Bildlauf-Collider oder ein interaktiver Bild Lauf Inhalt im Fokus ist, und führen Sie die scrollbewegung aus, indem Sie mit der linken Maustaste klicken und nach oben und unten ziehen.

## <a name="controlling-the-scrolling-object-from-code"></a>Steuern des scrollobjekts aus dem Code

Die mrtk-scrollobjektauflistung stellt einige öffentliche Methoden zur Verfügung, mit denen Sie den scrollcontainer verschieben können, indem Sie seine Position entsprechend der `pagination` Eigenschaften Konfiguration ausrichten.

Ein Beispiel für den Zugriff auf die Paginierungs Schnittstelle der Bild Lauf Objekt Auflistung ist für die Verwendung im ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` Ordner verfügbar. Das Beispielskript für die Bild lauffähige [Paginierung](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) kann mit einer beliebigen vorhandenen scrollobjektauflistung in der Szene verknüpft werden. Auf das Skript kann dann von Szenen Komponenten verwiesen werden, die Unity-Ereignisse verfügbar machen (z. b. [mrtk Button](button.md)).

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

## <a name="scrolling-object-collection-properties"></a>Scrollen von Objekt Auflistungs Eigenschaften

| Allgemein                                                                                                                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Scrollrichtung             | Die Richtung, in der der Inhalt Scrollen soll.|

| Paginierung                   |               BESCHREIBUNG                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Zellen pro Ebene               | Die Anzahl von Zellen in einer Zeile auf der Bild Lauf Ansicht oder der Anzahl von Zellen in einer Spalte in der linken rechten scrollansicht.                                                                                                         |
| Ebenen pro Seite               | Anzahl der sichtbaren Ebenen im scrollbereich.                                                                                                                                                                         |
| Seiten Zelle                    | Dimensionen der Paginierungs Zelle.                  |

| Erweiterte Einstellungen            |                  BESCHREIBUNG                                                                                                                                                                                    |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Masken Bearbeitungsmodus               | Bearbeitungsmodi zum Definieren der Ausschneide Feld Maskierungs Grenzen. Wählen Sie "automatisch" aus, um automatisch Paginierungs Werte zu verwenden. Wählen Sie "manuell" aus, um die direkte Bearbeitung des Clipping Box-Objekts zu aktivieren.|
| Collider-Bearbeitungsmodus           | Bearbeitungsmodi zum Definieren der Collider-Begrenzungen der scrollinteraktion. Wählen Sie "automatisch" aus, um automatisch Paginierungs Werte zu verwenden. Wählen Sie "manuell" aus, um die direkte Manipulation des Colliders zu aktivieren.|
| Bildlauf möglich                   | Aktiviert/deaktiviert den Bildlauf mit Near-/--Interaktions.                  |
| Verwendung bei vorrendering            | Schaltet ein/aus, ob die scrollingobjectcollection das Kamera OnPreRender-Ereignis zum Verwalten der Inhalts Sichtbarkeit verwendet.                  |
| Paginierungs Kurve             | Animations Kurve für die Paginierung.                  |
| Animations Länge             | Die Zeitspanne (in Sekunden), die die paginationcurve zum Auswerten benötigt.                  |
| Bild Lauf Schwellenwert für Hand Delta  | Der Abstand (in Meter), den der aktuelle Zeiger entlang der Scrollrichtung bewegen kann, bevor ein Drag-Drag-Vorgang ausgelöst wird.                  |
| Vordere Berührungs Distanz         | Abstand in Metern, um eine lokale XY-Ebene zu positionieren, mit der überprüft wird, ob eine Berührungs Interaktion am Anfang der scrollansicht gestartet wurde.                  |
| Freigabe Schwellenwert            | Ziehen Sie die Menge der für die Umstellung auf die freigegebenen Eingaben erforderlichen Bild Lauf Begrenzungen in Meter zurück.                  |

| Geschwindigkeit |               BESCHREIBUNG                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Typ der Geschwindigkeit       | Der gewünschte Typ der Geschwindigkeits Zuordnung für die scrola.                                                                                        |
| Velocity-Multiplikator     | Menge an (zusätzlicher) Geschwindigkeit, die auf Scroller angewendet werden soll.                                                                                                                                                        |
| Geschwindigkeits Dämpfung     | Menge der auf die Geschwindigkeit angewendeten fzuweisung. |
| Sprung Multiplikator     | Multiplikator zum Hinzufügen von mehr Sprung zum overscroll einer Liste bei Verwendung von fzuweisung pro Frame oder fzuweisung pro Element. |

| Debugoptionen |            BESCHREIBUNG                                                                                                                                                                         |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Maske aktiviert       | Sichtbarkeits Modus des Bild Lauf Inhalts. Mit dem Standardwert werden alle Objekte außerhalb des sichtbaren scrollbereichs maskiert.                                                                                        |
| Schwellenwert Ebenen anzeigen     | True gibt an, dass der Editor die Fingereingabe-Schwellenwert Ebenen um die scrollgrenzen zuweist.                                                                                                                                                        |
| Paginierung Debuggen     | Verwenden Sie diesen Abschnitt, um die scrollpaginierung während der Laufzeit zu debuggen. |

| Events|    BESCHREIBUNG                                                                                                                                                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Beim Klicken       | Das Ereignis, das ausgelöst wird, wenn der Bild Lauf Hintergrund-Collider oder ein interaktiver Inhalt einen Klick erhält.                                                                                        |
| Beim Einstieg     | Das Ereignis, das ausgelöst wird, wenn der Hintergrund des Bildlauf-Hintergrunds oder eines seiner interaktiven Inhalte einen near Interaktion-Fingerabdruck erhält                                                                                                                                                        |
| Beim berühren beendet     | Das Ereignis wird ausgelöst, wenn eine aktive Berührungs Interaktion beendet wird, indem der Near-Interaktions Zeiger eine der releaseschutzschwell-Ebenen überschreitet. |
| Beim Einstieg     | Das Ereignis wird ausgelöst, wenn der scrollcontainer durch Interaktion, Velocity fzuweisung oder Paginierung verschoben wird. |
| Beim Ende der Dynamik     | Das Ereignis, das ausgelöst wird, wenn der scrollcontainer nicht mehr durch Interaktion, Velocity fzuweisung oder Paginierung verschoben wird. |

## <a name="scrolling-example-scene"></a>Scrollbeispielszene

Die Beispiel Szene **scrollingobjectcollection. unity** besteht aus drei scrollbaren Beispielen, von denen jede eine andere Konfiguration mit einer anderen Geschwindigkeits Konfiguration aufweist. Die Beispiel Szene enthält Wände, um das Verhalten der Oberflächen Platzierung anzuzeigen, das in der Hierarchie standardmäßig deaktiviert ist. Die Beispiel Szene finden Sie unter dem ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` Ordner.

![Beispiel Szene für das Scrollen von Objekt Sammlungen](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>Bild Lauf Beispiel präfabs

Aus Gründen der praktische Verwendung stehen zwei vorab Definitionen für scrollobjektauflistungen zur Verfügung. Die Beispiel präfabs finden Sie unter dem ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` Ordner.

![Prefabs für Bildlauf-Objekt Auflistung](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>Weitere Informationen

* [Zuschnitt-Primitiv](../rendering/clipping-primitive.md)
* [Materialinstanz](../rendering/material-instance.md)
* [Standard-Shader](../rendering/MRTK-standard-shader.md)
* [Objektsammlung](object-collection.md)
