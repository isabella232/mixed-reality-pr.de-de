---
ms.openlocfilehash: 4dde9dcb34553e1ad39d9c732f32f9d0ef174eaf2a6b6fbe7b59b8fdc9facf8d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204272"
---
# <a name="all-platforms"></a>[Alle Plattformen](#tab/all)

Die gleichen Aktions- und Achsenzuordnungen in den Eingabeprojekteinstellungen des Spiels können in C++ verwendet werden.

1. Erstellen Einer neuen C++-Klasse mit File/New C++-Klasse...

![Erstellen einer neuen C++-Klasse](../images/reverb-g2-img-11.png)

2. Erstellen eines Pawns

![Erstellen eines Pawns](../images/reverb-g2-img-12.png)

3. Suchen Sie im Visual Studio Projektmappe des Projekts nach der neuen Pawn-Klasse, und konfigurieren Sie sie für die Eingabe.
* Legen Sie zunächst im Konstruktor AutoPossessPlayer auf den ersten Player fest, um die Eingabe an den Pawn weiterzuleiten.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* Binden Sie dann in SetupPlayerInputComponent Aktionen und Achsenereignisse aus den Eingabeeinstellungen des Projekts an die Aktionsnamen.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* Fügen Sie der -Klasse die Rückruffunktionen hinzu:

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

* Aktualisieren Sie den Header des Pawns mit den Definitionen der Rückruffunktion:

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. Kompilieren Sie aus Visual Studio, um den Editor mit dem neuen Pawn zu starten. Ziehen Sie den Pawn aus dem Inhaltsbrowser in das Spiel, und der Pawn führt jetzt die Rückrufe aus, wenn die Eingabe gedrückt wird.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

Bei Verwendung von Thumbstick-Achsenereignissen muss der Name des Achsenereignisses auf "_X" oder "_Y" enden, der dem verwendeten Schlüssel entspricht.

![Verwenden von Thumbstickereignissen](../images/reverb-g2-img-09.png)

Registrieren Sie schließlich die Aktionen im Spiel mitHilfe der Schaltflächen **Aktionsmanifest** erneut generieren und **Controllerbindungen** erneut generieren in Project Einstellungen > Vr-Eingabe für Denkdruck.

![Registrieren von Aktionen in Projekteinstellungen](../images/reverb-g2-img-10.png)

