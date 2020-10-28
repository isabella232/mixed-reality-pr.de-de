---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638729"
---
# <a name="all-platforms"></a>[<span data-ttu-id="43cde-101">Alle Plattformen</span><span class="sxs-lookup"><span data-stu-id="43cde-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="43cde-102">Die gleichen Aktions-und Achsen Zuordnungen in den Eingabe Projekteinstellungen des Spiels können von C++ verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="43cde-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="43cde-103">Neue C++-Klasse mit der Datei/neuen C++-Klasse erstellen...</span><span class="sxs-lookup"><span data-stu-id="43cde-103">Create a new C++ Class with File/New C++ Class...</span></span>

![Erstellen einer neuen C++-Klasse](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="43cde-105">Erstellen eines pfes</span><span class="sxs-lookup"><span data-stu-id="43cde-105">Create a pawn</span></span>

![Erstellen eines pfens](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="43cde-107">Suchen Sie in der Visual Studio-Projekt Mappe des Projekts nach der neuen Klasse, und konfigurieren Sie Sie für die Eingabe.</span><span class="sxs-lookup"><span data-stu-id="43cde-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="43cde-108">Legen Sie zunächst im Konstruktor autopossessplayer auf den ersten Player fest, um Eingaben an die aufzurufenden zu leiten.</span><span class="sxs-lookup"><span data-stu-id="43cde-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="43cde-109">Binden Sie dann in setupplayerinputcomponent Aktionen und Achsen Ereignisse an die Aktions Namen aus den Eingabeeinstellungen des Projekts.</span><span class="sxs-lookup"><span data-stu-id="43cde-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="43cde-110">Fügen Sie der-Klasse die Rückruf Funktionen hinzu:</span><span class="sxs-lookup"><span data-stu-id="43cde-110">Add the callback functions to the class:</span></span>

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

* <span data-ttu-id="43cde-111">Aktualisieren Sie den Header des Aufrufs mit den Rückruf Funktionsdefinitionen:</span><span class="sxs-lookup"><span data-stu-id="43cde-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="43cde-112">Kompilieren Sie aus Visual Studio, um den Editor mit den neuen aufsorten zu starten.</span><span class="sxs-lookup"><span data-stu-id="43cde-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="43cde-113">Verschieben Sie die Seiten aus dem Inhalts Browser per Drag & amp; Drop in das Spiel, und die aufgerufenen führen die Rückrufe aus, wenn Eingaben gedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="43cde-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="43cde-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="43cde-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="43cde-115">Bei der Verwendung von Ministick-Achsen Ereignissen muss der Name des Achsen Ereignisses auf "_x" oder "_Y" enden, das dem verwendeten Schlüssel entspricht.</span><span class="sxs-lookup"><span data-stu-id="43cde-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![Verwenden von Ministick-Ereignissen](../images/reverb-g2-img-09.png)

<span data-ttu-id="43cde-117">Registrieren Sie schließlich die Aktionen im Spiel mit "steamvr", indem Sie die Schaltflächen zum erneuten **generieren des Aktions Manifests** und zum erneuten **Generieren von Controller Bindungen** in den Projekteinstellungen > die Eingabe von "</span><span class="sxs-lookup"><span data-stu-id="43cde-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![Registrieren von Aktionen in den Projekteinstellungen](../images/reverb-g2-img-10.png)

