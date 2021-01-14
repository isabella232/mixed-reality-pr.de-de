---
ms.openlocfilehash: ad7d530de61864528ae80e4d0086687d282e6b18
ms.sourcegitcommit: 8f9f98342aaf66645fd74dac3fad499f9d799ce7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2021
ms.locfileid: "98109545"
---
# <a name="426"></a>[<span data-ttu-id="e3edd-101">4.26</span><span class="sxs-lookup"><span data-stu-id="e3edd-101">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="e3edd-102">Setup des FV-Kamerafeeds</span><span class="sxs-lookup"><span data-stu-id="e3edd-102">PV Camera Feed Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3edd-103">Die FV-Kamera ist sowohl in Windows Mixed Reality-als auch in OpenXR-Plug-Ins implementiert.</span><span class="sxs-lookup"><span data-stu-id="e3edd-103">PV camera is implemented in both Windows Mixed Reality and OpenXR plugins.</span></span> <span data-ttu-id="e3edd-104">Für OpenXR muss allerdings das [Microsoft OpenXR-Plug-In](https://github.com/microsoft/Microsoft-OpenXR-Unreal) installiert sein.</span><span class="sxs-lookup"><span data-stu-id="e3edd-104">However OpenXR needs [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) to be installed.</span></span> <span data-ttu-id="e3edd-105">Außerdem besteht für OpenXR eine aktuelle Einschränkung, die Kamera kann mit DirectX11 RHI verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e3edd-105">Also OpenXR has current limitation, camera can work with DirectX11 RHI.</span></span> <span data-ttu-id="e3edd-106">Diese Einschränkung wird in einer kommenden Unreal-Version behoben.</span><span class="sxs-lookup"><span data-stu-id="e3edd-106">This limitation will be fixed in a further Unreal version.</span></span> 

- <span data-ttu-id="e3edd-107">Aktivieren Sie in **Project Settings > HoloLens** (Projekteinstellungen > HoloLens) die **Webcam**-Funktionalität:</span><span class="sxs-lookup"><span data-stu-id="e3edd-107">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![Screenshot der HoloLens-Projekteinstellungen mit hervorgehobener Webcam-Eigenschaft](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="e3edd-109">Erstellen Sie einen neuen Akteur mit dem Namen „CamCapture“, und fügen Sie eine Ebene zum Rendern des Kamerafeeds hinzu:</span><span class="sxs-lookup"><span data-stu-id="e3edd-109">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![Screenshot des Akteurs mit einer hinzugefügten Ebene](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="e3edd-111">Fügen Sie Ihrer Szene den Akteur hinzu, erstellen Sie ein neues Material mit dem Namen „CamTextureMaterial“ und einem Texture-Objektparameter sowie einem Texturbeispiel.</span><span class="sxs-lookup"><span data-stu-id="e3edd-111">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="e3edd-112">Senden Sie die RGB-Daten der Textur an die Ausgabe „Emissionsfarbe“:</span><span class="sxs-lookup"><span data-stu-id="e3edd-112">Send the texture’s rgb data to the output emissive color:</span></span>

![Blaupause eines Material- und Texturbeispiels](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="e3edd-114">Rendern des FV-Kamerafeeds</span><span class="sxs-lookup"><span data-stu-id="e3edd-114">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="e3edd-115">Schalten Sie in der CamCapture-Blaupause die FV-Kamera ein:</span><span class="sxs-lookup"><span data-stu-id="e3edd-115">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![Blaupause der Funktion zum Umschalten von ARCapture mit eingeschalteter FV-Kamera](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="e3edd-117">Erstellen Sie eine dynamische Materialinstanz aus „CamTextureMaterial“, und weisen Sie dieses Material der Ebene des Akteurs zu:</span><span class="sxs-lookup"><span data-stu-id="e3edd-117">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![Blaupause der Funktion zum Erstellen einer dynamischen Materialinstanz](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="e3edd-119">Rufen Sie die Textur aus dem Kamerafeed ab, und weisen Sie sie dem dynamischen Material zu, wenn sie gültig ist.</span><span class="sxs-lookup"><span data-stu-id="e3edd-119">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="e3edd-120">Wenn die Textur nicht gültig ist, starten Sie einen Timer, und versuchen Sie es nach dessen Ablauf erneut:</span><span class="sxs-lookup"><span data-stu-id="e3edd-120">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![Blaupause der Kamerafeed-Textur, die dem dynamischen Material zugewiesen ist](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="e3edd-122">Skalieren Sie abschließend die Ebene um das Seitenverhältnis des Kamerabilds:</span><span class="sxs-lookup"><span data-stu-id="e3edd-122">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![Blaupause der Ebene, die relativ zum Seitenverhältnis des Kamerabilds skaliert ist](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="e3edd-124">Finden von Kamerapositionen im Weltbereich</span><span class="sxs-lookup"><span data-stu-id="e3edd-124">Find Camera Positions in World Space</span></span>

<span data-ttu-id="e3edd-125">Die Kamera in der HoloLens 2 ist gegenüber dem Head Tracking des Geräts vertikal versetzt.</span><span class="sxs-lookup"><span data-stu-id="e3edd-125">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="e3edd-126">Es gibt ein paar Funktionen, um die Position der Kamera im Weltbereich zu ermitteln, um diesem Versatz Rechnung zu tragen.</span><span class="sxs-lookup"><span data-stu-id="e3edd-126">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="e3edd-127">„GetPVCameraToWorldTransform“ ruft die Transformation der FV-Kamera im Weltbereich ab und wird auf der Kameralinse positioniert:</span><span class="sxs-lookup"><span data-stu-id="e3edd-127">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![Blaupause der Funktion zum Abrufen der Transformation der FV-Kamera gegenüber dem Weltbereich](../images/unreal-pvc-img-08.png)

<span data-ttu-id="e3edd-129">„GetWorldSpaceRayFromCameraPoint“ wirft einen Strahl aus dem Kameraobjektiv in die Szene im Weltbereich von Unreal, um den Inhalt eines Pixels im Kamerabild herauszufinden:</span><span class="sxs-lookup"><span data-stu-id="e3edd-129">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![Blaupause des Strahls vom Kamerapunkt zum Abrufen des Weltbereichs](../images/unreal-pvc-img-09.png)

<span data-ttu-id="e3edd-131">„GetPVCameraIntrinsics“ gibt die systeminternen Werte der Kamera zurück, die bei der Verarbeitung eines Kamerabilds beim maschinellen Sehen verwendet werden können:</span><span class="sxs-lookup"><span data-stu-id="e3edd-131">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![Blaupause der Funktionen zum Abrufen der systeminternen PVCamera-Werte](../images/unreal-pvc-img-10.png)

<span data-ttu-id="e3edd-133">Um herauszufinden, was an einer bestimmten Pixelkoordinate im Weltbereich vorhanden ist, verwenden Sie eine Zeilenablaufverfolgung mit dem Weltbereichs-Strahl:</span><span class="sxs-lookup"><span data-stu-id="e3edd-133">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![Blaupause des Weltbereich-Strahls, der verwendet wird, um zu ermitteln, was im Weltbereich an einer bestimmten Koordinate vorhanden ist](../images/unreal-pvc-img-11.png)

<span data-ttu-id="e3edd-135">Hier werfen wir einen 2-m-Strahl vom Kameraobjektiv auf die Raumposition der Kamera, die ¼ vom oberen linken Punkt des Bilds entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="e3edd-135">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="e3edd-136">Verwenden Sie dann das Trefferergebnis, um etwas an der Position zu rendern, an der das Objekt im Weltbereich vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="e3edd-136">Then use the hit result to render something where the object exists in world space:</span></span>

![Blaupause eines 2-m-Strahls, der vom Kameraobjektiv aus auf die Raumposition der Kamera geworfen wird, die 1/4 vom oberen linken Punkt des Bilds entfernt ist.](../images/unreal-pvc-img-12.png)

<span data-ttu-id="e3edd-138">Wenn räumliche Abbildung verwendet wird, stimmt diese Trefferposition mit der Oberfläche überein, die von der Kamera gesehen wird.</span><span class="sxs-lookup"><span data-stu-id="e3edd-138">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="e3edd-139">Rendern des FV-Kamerafeeds in C++</span><span class="sxs-lookup"><span data-stu-id="e3edd-139">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="e3edd-140">Erstellen Sie einen neuen C++-Akteur mit dem Namen „CamCapture“.</span><span class="sxs-lookup"><span data-stu-id="e3edd-140">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="e3edd-141">Fügen Sie in der Datei „build.cs“ des Projekts „AugmentedReality“ zur Liste „PublicDependencyModuleNames“ hinzu:</span><span class="sxs-lookup"><span data-stu-id="e3edd-141">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="e3edd-142">Schließen Sie „ARBlueprintLibrary.h“ in „CamCapture.h“ ein</span><span class="sxs-lookup"><span data-stu-id="e3edd-142">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="e3edd-143">Darüber hinaus müssen Sie lokale Variablen für das Gittermodell und das Material hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="e3edd-143">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="e3edd-144">Aktualisieren Sie in „CamCapture.cpp“ den Konstruktor, um der Szene ein statisches Gittermodell hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="e3edd-144">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

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

<span data-ttu-id="e3edd-145">Erstellen Sie in „BeginPlay“ eine dynamische Materialinstanz aus dem Kameramaterial des Projekts, wenden Sie es auf die statische Gittermodellkomponente an, und starten Sie die HoloLens-Kamera.</span><span class="sxs-lookup"><span data-stu-id="e3edd-145">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="e3edd-146">Klicken Sie im Editor mit der rechten Maustaste auf das „CamTextureMaterial“ im Inhaltsbrowser, und wählen Sie „COPY-Referenz“ aus, um die Zeichenfolge für „CameraMatPath“ abzurufen.</span><span class="sxs-lookup"><span data-stu-id="e3edd-146">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

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

<span data-ttu-id="e3edd-147">Rufen Sie in Tick die Textur bei der Kamera ab, legen Sie sie auf den Texturparameter im Material „CamTextureMaterial“ fest, und skalieren Sie die statische Gittermodellkomponente um das Seitenverhältnis des Kamerabilds:</span><span class="sxs-lookup"><span data-stu-id="e3edd-147">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

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

# <a name="425"></a>[<span data-ttu-id="e3edd-148">4.25</span><span class="sxs-lookup"><span data-stu-id="e3edd-148">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="e3edd-149">Rendering von der FV-Kamera für MRC</span><span class="sxs-lookup"><span data-stu-id="e3edd-149">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="e3edd-150">Dafür ist **Unreal Engine 4.25** oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e3edd-150">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="e3edd-151">Das System und benutzerdefinierte MRC-Rekorder erstellen Mixed Reality-Aufnahmen, indem sie die FV-Kamera mit Hologrammen kombinieren, die von der App gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="e3edd-151">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="e3edd-152">Standardmäßig wird für die Mixed-Reality-Aufnahme die holografische Ausgabe des rechten Auges verwendet.</span><span class="sxs-lookup"><span data-stu-id="e3edd-152">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="e3edd-153">Wenn eine immersive App hingegen [von der FV-Kamera rendert](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), wird stattdessen diese verwendet.</span><span class="sxs-lookup"><span data-stu-id="e3edd-153">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="e3edd-154">Das Rendering von der FV-Kamera ermöglicht eine bessere Abstimmung zwischen der realen Welt und den Hologrammen im MRC-Video.</span><span class="sxs-lookup"><span data-stu-id="e3edd-154">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="e3edd-155">So abonnieren Sie das Rendering von der FV-Kamera:</span><span class="sxs-lookup"><span data-stu-id="e3edd-155">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="e3edd-156">Rufen Sie **SetEnabledMixedRealityCamera** und **ResizeMixedRealityCamera** auf.</span><span class="sxs-lookup"><span data-stu-id="e3edd-156">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="e3edd-157">Verwenden Sie die Werte **Size X** (Größe X) und **Size Y** (Größe Y), um die Videoabmessungen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="e3edd-157">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Dritte Kamera](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="e3edd-159">Unreal verarbeitet dann Anforderungen von MRC, aus der Perspektive der FV-Kamera zu rendern.</span><span class="sxs-lookup"><span data-stu-id="e3edd-159">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="e3edd-160">Nur wenn [Mixed Reality Capture](../../../mixed-reality-capture.md) (Mixed Reality-Aufnahme) ausgelöst wird, wird die App aufgefordert, aus der Perspektive der Foto-/Videokamera zu rendern.</span><span class="sxs-lookup"><span data-stu-id="e3edd-160">Only when [Mixed Reality Capture](../../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="e3edd-161">Verwenden der FV-Kamera</span><span class="sxs-lookup"><span data-stu-id="e3edd-161">Using the PV Camera</span></span>

<span data-ttu-id="e3edd-162">Die Webcam-Textur kann im Spiel zur Laufzeit abgerufen werden, dies muss jedoch im Editor unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen) aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="e3edd-162">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="e3edd-163">Wechseln Sie zu **Platforms > HoloLens > Capabilities** (Plattformen > HoloLens > Funktionen), und aktivieren Sie **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="e3edd-163">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="e3edd-164">Verwenden Sie die Funktion **StartCameraCapture**, um die Webcam zur Laufzeit zu nutzen, und die Funktion **StopCameraCapture**, um die Aufzeichnung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="e3edd-164">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Kamera: Starten/Beenden](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="e3edd-166">Rendern eines Bilds</span><span class="sxs-lookup"><span data-stu-id="e3edd-166">Rendering an image</span></span>
<span data-ttu-id="e3edd-167">So wird das Kamerabild gerendert:</span><span class="sxs-lookup"><span data-stu-id="e3edd-167">To render the camera image:</span></span>
1. <span data-ttu-id="e3edd-168">Erstellen Sie auf der Grundlage eines Materials im Projekt eine dynamische Materialinstanz, die im Screenshot unten den Namen **PVCamMat** trägt.</span><span class="sxs-lookup"><span data-stu-id="e3edd-168">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="e3edd-169">Legen Sie die dynamische Materialinstanz auf eine **Material Instance Dynamic Object Reference**-Variable (Materialinstanz mit dynamischem Objektverweis) fest.</span><span class="sxs-lookup"><span data-stu-id="e3edd-169">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="e3edd-170">Legen Sie das Material des Objekts in der Szene, das den Kamerafeed rendern soll, auf diese neue dynamische Materialinstanz fest.</span><span class="sxs-lookup"><span data-stu-id="e3edd-170">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="e3edd-171">Starten Sie einen Timer, der dazu verwendet wird, das Kamerabild an das Material zu binden.</span><span class="sxs-lookup"><span data-stu-id="e3edd-171">Start a timer that will be used to bind the camera image to the material.</span></span>

![Kamera: Rendern](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="e3edd-173">Erstellen Sie eine neue Funktion für diesen Timer (in diesem Fall: **MaterialTimer**), und rufen Sie **GetARCameraImage** auf, um die Textur von der Webcam abzurufen.</span><span class="sxs-lookup"><span data-stu-id="e3edd-173">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="e3edd-174">Ist diese Textur gültig, legen Sie im Shader einen Texturparameter auf dieses Bild fest.</span><span class="sxs-lookup"><span data-stu-id="e3edd-174">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="e3edd-175">Falls nicht, starten Sie den Materialtimer erneut.</span><span class="sxs-lookup"><span data-stu-id="e3edd-175">Otherwise, start the material timer again.</span></span>

![Kameratextur von Webcam](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="e3edd-177">Achten Sie darauf, dass das Material über einen Parameter verfügt, der mit dem Namen in **SetTextureParameterValue** übereinstimmt, der an einen Farbeintrag gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="e3edd-177">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="e3edd-178">Ohne den Parameter kann das Kamerabild nicht ordnungsgemäß angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e3edd-178">Without the parameter, the camera image can't be displayed properly.</span></span>

![Kamera: Textur](../images/unreal-camera-material.PNG)

