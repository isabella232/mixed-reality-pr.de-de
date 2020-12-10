---
ms.openlocfilehash: a8258f1ba99fdd1607014624c4ad4d6ec0a8e330
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609606"
---
# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>Rendering von der FV-Kamera für MRC

> [!NOTE]
> Dafür ist **Unreal Engine 4.25** oder höher erforderlich.

Das System und benutzerdefinierte MRC-Rekorder erstellen Mixed Reality-Aufnahmen, indem sie die FV-Kamera mit Hologrammen kombinieren, die von der App gerendert werden.

Standardmäßig wird für die Mixed-Reality-Aufnahme die holografische Ausgabe des rechten Auges verwendet. Wenn eine immersive App hingegen [von der FV-Kamera rendert](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), wird stattdessen diese verwendet. Das Rendering von der FV-Kamera ermöglicht eine bessere Abstimmung zwischen der realen Welt und den Hologrammen im MRC-Video.

So abonnieren Sie das Rendering von der FV-Kamera:

1. Rufen Sie **SetEnabledMixedRealityCamera** und **ResizeMixedRealityCamera** auf.
    * Verwenden Sie die Werte **Size X** (Größe X) und **Size Y** (Größe Y), um die Videoabmessungen festzulegen.

![Dritte Kamera](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

Unreal verarbeitet dann Anforderungen von MRC, aus der Perspektive der FV-Kamera zu rendern.

> [!NOTE]
> Nur wenn [Mixed Reality Capture](../../../mixed-reality-capture.md) (Mixed Reality-Aufnahme) ausgelöst wird, wird die App aufgefordert, aus der Perspektive der Foto-/Videokamera zu rendern.

## <a name="using-the-pv-camera"></a>Verwenden der FV-Kamera

Die Webcam-Textur kann im Spiel zur Laufzeit abgerufen werden, dies muss jedoch im Editor unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen) aktiviert werden:
1. Wechseln Sie zu **Platforms > HoloLens > Capabilities** (Plattformen > HoloLens > Funktionen), und aktivieren Sie **Webcam**.
    * Verwenden Sie die Funktion **StartCameraCapture**, um die Webcam zur Laufzeit zu nutzen, und die Funktion **StopCameraCapture**, um die Aufzeichnung zu beenden.

![Kamera: Starten/Beenden](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Rendern eines Bilds
So wird das Kamerabild gerendert:
1. Erstellen Sie auf der Grundlage eines Materials im Projekt eine dynamische Materialinstanz, die im Screenshot unten den Namen **PVCamMat** trägt.  
2. Legen Sie die dynamische Materialinstanz auf eine **Material Instance Dynamic Object Reference**-Variable (Materialinstanz mit dynamischem Objektverweis) fest.  
3. Legen Sie das Material des Objekts in der Szene, das den Kamerafeed rendern soll, auf diese neue dynamische Materialinstanz fest.
    * Starten Sie einen Timer, der dazu verwendet wird, das Kamerabild an das Material zu binden.

![Kamera: Rendern](../images/unreal-camera-render.PNG)

4. Erstellen Sie eine neue Funktion für diesen Timer (in diesem Fall: **MaterialTimer**), und rufen Sie **GetARCameraImage** auf, um die Textur von der Webcam abzurufen.  
5. Ist diese Textur gültig, legen Sie im Shader einen Texturparameter auf dieses Bild fest.  Falls nicht, starten Sie den Materialtimer erneut.

![Kameratextur von Webcam](../images/unreal-camera-texture.PNG)

5. Achten Sie darauf, dass das Material über einen Parameter verfügt, der mit dem Namen in **SetTextureParameterValue** übereinstimmt, der an einen Farbeintrag gebunden ist. Ohne den Parameter kann das Kamerabild nicht ordnungsgemäß angezeigt werden.

![Kamera: Textur](../images/unreal-camera-material.PNG)

# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>Setup des FV-Kamerafeeds

- Aktivieren Sie in **Project Settings > HoloLens** (Projekteinstellungen > HoloLens) die **Webcam**-Funktionalität:

![Screenshot der HoloLens-Projekteinstellungen mit hervorgehobener Webcam-Eigenschaft](../images/unreal-pvc-img-01.png)

- Erstellen Sie einen neuen Akteur mit dem Namen „CamCapture“, und fügen Sie eine Ebene zum Rendern des Kamerafeeds hinzu:

![Screenshot des Akteurs mit einer hinzugefügten Ebene](../images/unreal-pvc-img-02.png)

- Fügen Sie Ihrer Szene den Akteur hinzu, erstellen Sie ein neues Material mit dem Namen „CamTextureMaterial“ und einem Texture-Objektparameter sowie einem Texturbeispiel.  Senden Sie die RGB-Daten der Textur an die Ausgabe „Emissionsfarbe“:

![Blaupause eines Material- und Texturbeispiels](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>Rendern des FV-Kamerafeeds

- Schalten Sie in der CamCapture-Blaupause die FV-Kamera ein:

![Blaupause der Funktion zum Umschalten von ARCapture mit eingeschalteter FV-Kamera](../images/unreal-pvc-img-04.png)

- Erstellen Sie eine dynamische Materialinstanz aus „CamTextureMaterial“, und weisen Sie dieses Material der Ebene des Akteurs zu:

![Blaupause der Funktion zum Erstellen einer dynamischen Materialinstanz](../images/unreal-pvc-img-05.png)

- Rufen Sie die Textur aus dem Kamerafeed ab, und weisen Sie sie dem dynamischen Material zu, wenn sie gültig ist.  Wenn die Textur nicht gültig ist, starten Sie einen Timer, und versuchen Sie es nach dessen Ablauf erneut:

![Blaupause der Kamerafeed-Textur, die dem dynamischen Material zugewiesen ist](../images/unreal-pvc-img-06.png)

- Skalieren Sie abschließend die Ebene um das Seitenverhältnis des Kamerabilds:

![Blaupause der Ebene, die relativ zum Seitenverhältnis des Kamerabilds skaliert ist](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>Finden von Kamerapositionen im Weltbereich

Die Kamera in der HoloLens 2 ist gegenüber dem Head Tracking des Geräts vertikal versetzt.  Es gibt ein paar Funktionen, um die Position der Kamera im Weltbereich zu ermitteln, um diesem Versatz Rechnung zu tragen.

„GetPVCameraToWorldTransform“ ruft die Transformation der FV-Kamera im Weltbereich ab und wird auf der Kameralinse positioniert:

![Blaupause der Funktion zum Abrufen der Transformation der FV-Kamera gegenüber dem Weltbereich](../images/unreal-pvc-img-08.png)

„GetWorldSpaceRayFromCameraPoint“ wirft einen Strahl aus dem Kameraobjektiv in die Szene im Weltbereich von Unreal, um den Inhalt eines Pixels im Kamerabild herauszufinden:

![Blaupause des Strahls vom Kamerapunkt zum Abrufen des Weltbereichs](../images/unreal-pvc-img-09.png)

„GetPVCameraIntrinsics“ gibt die systeminternen Werte der Kamera zurück, die bei der Verarbeitung eines Kamerabilds beim maschinellen Sehen verwendet werden können:

![Blaupause der Funktionen zum Abrufen der systeminternen PVCamera-Werte](../images/unreal-pvc-img-10.png)

Um herauszufinden, was an einer bestimmten Pixelkoordinate im Weltbereich vorhanden ist, verwenden Sie eine Zeilenablaufverfolgung mit dem Weltbereichs-Strahl:

![Blaupause des Weltbereich-Strahls, der verwendet wird, um zu ermitteln, was im Weltbereich an einer bestimmten Koordinate vorhanden ist](../images/unreal-pvc-img-11.png)

Hier werfen wir einen 2-m-Strahl vom Kameraobjektiv auf die Raumposition der Kamera, die ¼ vom oberen linken Punkt des Bilds entfernt ist.  Verwenden Sie dann das Trefferergebnis, um etwas an der Position zu rendern, an der das Objekt im Weltbereich vorhanden ist:

![Blaupause eines 2-m-Strahls, der vom Kameraobjektiv aus auf die Raumposition der Kamera geworfen wird, die 1/4 vom oberen linken Punkt des Bilds entfernt ist.](../images/unreal-pvc-img-12.png)

Wenn räumliche Abbildung verwendet wird, stimmt diese Trefferposition mit der Oberfläche überein, die von der Kamera gesehen wird.

## <a name="rendering-the-pv-camera-feed-in-c"></a>Rendern des FV-Kamerafeeds in C++

- Erstellen Sie einen neuen C++-Akteur mit dem Namen „CamCapture“.
- Fügen Sie in der Datei „build.cs“ des Projekts „AugmentedReality“ zur Liste „PublicDependencyModuleNames“ hinzu:

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- Schließen Sie „ARBlueprintLibrary.h“ in „CamCapture.h“ ein

```cpp
#include "ARBlueprintLibrary.h"
```

- Darüber hinaus müssen Sie lokale Variablen für das Gittermodell und das Material hinzufügen:

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- Aktualisieren Sie in „CamCapture.cpp“ den Konstruktor, um der Szene ein statisches Gittermodell hinzuzufügen:

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

Erstellen Sie in „BeginPlay“ eine dynamische Materialinstanz aus dem Kameramaterial des Projekts, wenden Sie es auf die statische Gittermodellkomponente an, und starten Sie die HoloLens-Kamera. 
 
Klicken Sie im Editor mit der rechten Maustaste auf das „CamTextureMaterial“ im Inhaltsbrowser, und wählen Sie „COPY-Referenz“ aus, um die Zeichenfolge für „CameraMatPath“ abzurufen.

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMateriall = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

Rufen Sie in Tick die Textur bei der Kamera ab, legen Sie sie auf den Texturparameter im Material „CamTextureMaterial“ fest, und skalieren Sie die statische Gittermodellkomponente um das Seitenverhältnis des Kamerabilds:

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

