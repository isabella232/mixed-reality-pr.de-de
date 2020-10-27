---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638729"
---
# <a name="all-platforms"></a>[Alle Plattformen](#tab/all)

Die gleichen Aktions-und Achsen Zuordnungen in den Eingabe Projekteinstellungen des Spiels können von C++ verwendet werden.

1. Neue C++-Klasse mit der Datei/neuen C++-Klasse erstellen...

![Erstellen einer neuen C++-Klasse](../images/reverb-g2-img-11.png)

2. Erstellen eines pfes

![Erstellen eines pfens](../images/reverb-g2-img-12.png)

3. Suchen Sie in der Visual Studio-Projekt Mappe des Projekts nach der neuen Klasse, und konfigurieren Sie Sie für die Eingabe.
* Legen Sie zunächst im Konstruktor autopossessplayer auf den ersten Player fest, um Eingaben an die aufzurufenden zu leiten.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* Binden Sie dann in setupplayerinputcomponent Aktionen und Achsen Ereignisse an die Aktions Namen aus den Eingabeeinstellungen des Projekts.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* Fügen Sie der-Klasse die Rückruf Funktionen hinzu:

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* Aktualisieren Sie den Header des Aufrufs mit den Rückruf Funktionsdefinitionen:

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. Kompilieren Sie aus Visual Studio, um den Editor mit den neuen aufsorten zu starten. Verschieben Sie die Seiten aus dem Inhalts Browser per Drag & amp; Drop in das Spiel, und die aufgerufenen führen die Rückrufe aus, wenn Eingaben gedrückt werden.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

Bei der Verwendung von Ministick-Achsen Ereignissen muss der Name des Achsen Ereignisses auf "_x" oder "_Y" enden, das dem verwendeten Schlüssel entspricht.

![Verwenden von Ministick-Ereignissen](../images/reverb-g2-img-09.png)

Registrieren Sie schließlich die Aktionen im Spiel mit "steamvr", indem Sie die Schaltflächen zum erneuten **generieren des Aktions Manifests** und zum erneuten **Generieren von Controller Bindungen** in den Projekteinstellungen > die Eingabe von "

![Registrieren von Aktionen in den Projekteinstellungen](../images/reverb-g2-img-10.png)

