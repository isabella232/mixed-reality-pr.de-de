---
title: 'HoloLens (1. Generation) Freigabe 240: Mehrere HoloLens-Geräte'
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio und HoloLens, um die Details der Freigabe von Hologrammen zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, sharing, networking, academy, tutorial, HoloLens, Mixed Reality Academy, Unity, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset, Windows 10
ms.openlocfilehash: 1714c9cf1b64953ff319eefb8633b1891568d5a50f2ed778e6e890d3149d3908
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208700"
---
# <a name="hololens-1st-gen-sharing-240-multiple-hololens-devices"></a>HoloLens (1. Generation) Freigabe 240: Mehrere HoloLens Geräte

>[!IMPORTANT]
>Die Mixed Reality Academy-Tutorials wurden mit HoloLens (1. Generation), Unity 2017 und Mixed Reality immersive Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen. Diese Tutorials werden **_nicht mit_** den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 und sind möglicherweise nicht mit neueren Versionen von Unity kompatibel.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.

Hologramme in unserer Welt auftreten, indem sie im Raum an Ort und Stelle bleiben. HoloLens bleiben Hologramme mithilfe verschiedener [](../../../design/coordinate-systems.md) Koordinatensysteme zur Nachverfolgung der Position und Ausrichtung von Objekten an Ort und Stelle. Wenn wir diese Koordinatensysteme zwischen Geräten teilen, können wir eine gemeinsame Erfahrung erstellen, die es uns ermöglicht, an einer gemeinsamen holografischen Welt teil zu nehmen.

In diesem Lernprogramm wird Folgendes beschrieben:

* Richten Sie ein Netzwerk für eine freigegebene Beerfahrung ein.
* Freigeben von Hologrammen auf HoloLens Geräten.
* Entdecken Sie andere Personen in unserer gemeinsamen holografischen Welt.
* Erstellen Sie eine gemeinsame interaktive Erfahrung, in der Sie andere Spieler als Ziel haben und Projektile auf sie starten können.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR-Freigabe 240: Mehrere HoloLens-Geräte</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Vorbereitung

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10 PC, der mit den richtigen [Tools konfiguriert ist, die mit](../../../develop/install-the-tools.md) Internetzugriff installiert sind.
* Mindestens zwei HoloLens [geräte, die für die Entwicklung konfiguriert sind.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Projektdateien

* Laden Sie [die für](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) das Projekt erforderlichen Dateien herunter. Erfordert Unity 2017.2 oder höher.
  * Wenn Sie weiterhin Unity 5.6-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)
  * Wenn Sie weiterhin Unity 5.5-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)
  * Wenn Sie weiterhin Unity 5.4-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)
* Archivieren Sie die Dateien auf Ihrem Desktop oder einem anderen leicht erreichbaren Speicherort. Behalten Sie den Ordnernamen **sharedHolograms bei.**

>[!NOTE]
>Wenn Sie den Quellcode vor dem Herunterladen durchschauen möchten, ist er [auf GitHub.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)

## <a name="chapter-1---holo-world"></a>Kapitel 1 – Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

In diesem Kapitel richten wir unser erstes Unity-Projekt ein und führen den Build- und Bereitstellungsprozess schrittweise durch.

### <a name="objectives"></a>Ziele

* Richten Sie Unity ein, um holografische Apps zu entwickeln.
* Sehen Sie sich Ihr Hologramm an!

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wähle **Öffnen** aus.
* Geben Sie location als **Ordner SharedHolograms ein,** den Sie zuvor entarchiviert haben.
* Wählen Sie **Project Name aus,** und klicken Sie **auf Ordner auswählen.**
* Klicken Sie in **der Hierarchie** mit der rechten Maustaste auf **die Hauptkamera,** und wählen Sie **Löschen aus.**
* Suchen Sie **im Ordner HoloToolkit-Sharing-240/Prefabs/Camera** nach dem **Prefab Hauptkamera.**
* Drag and drop the **Main Camera** into the **Hierarchy**.
* Klicken Sie **in der** Hierarchie auf **Create** and Create **Empty (Leere erstellen).**
* Klicken Sie mit der rechten Maustaste auf das neue **GameObject,** und wählen Sie **Umbenennen aus.**
* Benennen Sie gameObject in **HologramCollection um.**
* Wählen Sie das **HologramCollection-Objekt** in der **Hierarchie aus.**
* Legen Sie **im Inspektor** die **Transformationsposition** auf **X: 0, Y: -0,25, Z: 2 fest.**
* Suchen Sie **Hologramme** Ordner im **Project** Bereich nach dem **EnergyHub-Objekt.**
* Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.
* Wählen **Sie Datei > Speichern der Szene unter... aus.**
* Nennen Sie die **Szene SharedHolograms,** und klicken Sie **auf Speichern.**
* Klicken Sie in Unity **auf** die Schaltfläche Wiedergabe, um eine Vorschau Ihrer Hologramme anzuzeigen.
* Klicken **Sie ein** zweites Mal auf Wiedergabe, um den Vorschaumodus zu beenden.

**Exportieren des Projekts aus Unity in Visual Studio**

* Wählen Sie in Unity **Datei > Build Einstellungen.**
* Klicken **Sie auf Geöffnete Szenen hinzufügen,** um die Szene hinzuzufügen.
* Wählen **Sie universelle Windows Plattform** in der **Liste Plattform aus,** und klicken Sie **auf Plattform wechseln.**
* Legen **Sie SDK** auf Universal **10 fest.**
* Legen **Sie Zielgerät** auf **HoloLens** **und UWP-Buildtyp auf** **D3D fest.**
* Überprüfen Sie **Unity C#-Projekte.**
* Klicken Sie auf **Erstellen**.
* Erstellen Sie im angezeigten Datei-Explorer-Fenster einen neuen Ordner mit **dem** Namen "App".
* Klicken Sie mit nur einem Klick **auf den Ordner App.**
* Klicken Sie **auf Ordner auswählen.**
* Wenn Unity fertig ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen Sie den **Ordner App.**
* Öffnen **Sie SharedHolograms.sln,** um die Visual Studio.
* Ändern Sie in der oberen Symbolleiste Visual Studio Ziel von Debuggen in **Release** und von ARM in **X86.**
* Klicken Sie auf den Dropdownpfeil neben Lokaler Computer, und wählen Sie **Remotegerät aus.**
    * Legen Sie **die Adresse** auf den Namen oder die IP-Adresse Ihrer HoloLens. Wenn Sie Ihre Geräte-IP-Adresse nicht kennen, sehen Sie sich die erweiterten Optionen für **Einstellungen > Network & Internet >** an, oder fragen Sie Cortana **"Hey Cortana, What es my IP address?" (Hey Cortana,** Was ist meine IP-Adresse?).
    * Lassen Sie den **Authentifizierungsmodus** auf **Universell festgelegt.**
    * Klicken Sie auf **Auswählen**.
* Klicken **Sie auf Debuggen > Starten ohne Debuggen,** oder drücken Sie **STRG+F5.** Wenn Dies die erste Bereitstellung auf Ihrem Gerät ist, müssen Sie es mit [einem Visual Studio.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)
* Legen Sie ihre HoloLens, und suchen Sie das EnergyHub-Hologramm.

## <a name="chapter-2---interaction"></a>Kapitel 2: Interaktion

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

In diesem Kapitel interagieren wir mit unseren Hologrammen. Zunächst fügen wir einen Cursor hinzu, um unseren Anvisieren [zu visualisieren.](../../../design/gaze-and-commit.md) Anschließend fügen wir Gesten hinzu [und](../../../design/gaze-and-commit.md#composite-gestures) verwenden unsere Hand, um unsere Hologramme im Raum zu platzieren.

### <a name="objectives"></a>Ziele

* Verwenden Sie die Eingabe anving, um einen Cursor zu steuern.
* Verwenden Sie gesteneingaben, um mit Hologrammen zu interagieren.

### <a name="instructions"></a>Anweisungen

**Anvisieren**

* Wählen Sie **im Hierarchiebereich** das **HologramCollection-Objekt** aus.
* Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
* Geben Sie im Menü in das Suchfeld Gaze **Manager ein.** Wählen Sie das Suchergebnis aus.
* Suchen Sie **im Ordner HoloToolkit-Sharing-240\Prefabs\Input** nach dem **Cursor-Objekt.**
* Drag and drop the **Cursor** asset onto the **Hierarchy**.

**Geste**

* Wählen Sie **im Hierarchiebereich** das **HologramCollection-Objekt** aus.
* Klicken **Sie auf Komponente hinzufügen,** und geben Sie im Suchfeld **Gesten-Manager** ein. Wählen Sie das Suchergebnis aus.
* Erweitern Sie **im Bereich Hierarchie** den Bereich **HologramCollection.**
* Wählen Sie das untergeordnete **EnergyHub-Objekt** aus.
* Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
* Geben Sie im Menü in das Suchfeld **Hologram Placement (Hologrammplatzierung) ein.** Wählen Sie das Suchergebnis aus.
* Speichern Sie die Szene, indem Sie **Datei > Szene speichern auswählen.**

**Bereitstellen und Nutzen**

* Erstellen Sie mithilfe der Anweisungen aus dem vorherigen HoloLens, und stellen Sie sie für Ihre Anwendung HoloLens.
* Sobald die App in Ihrer App gestartet HoloLens, bewegen Sie den Kopf, und sehen Sie, wie der EnergyHub Ihrem Anvieren folgt.
* Beachten Sie, wie der Cursor angezeigt wird, wenn Sie auf das Hologramm anvieren, und ändert sich in ein Punktlicht, wenn sie nicht an ein Hologramm schwelen.
* Führen Sie einen Tippen in die Luft aus, um das Hologramm zu platzieren. Zu diesem Zeitpunkt in unserem Projekt können Sie das Hologramm nur einmal platzieren (erneut bereitstellen, um es erneut zu versuchen).

## <a name="chapter-3---shared-coordinates"></a>Kapitel 3: Gemeinsame Koordinaten

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Es macht Spaß, Hologramme zu sehen und mit ihnen zu interagieren, aber wir gehen noch weiter. Wir richten unsere erste gemeinsame Erfahrung ein– ein Hologramm, das jeder gemeinsam sehen kann.

### <a name="objectives"></a>Ziele

* Richten Sie ein Netzwerk für eine freigegebene Beerfahrung ein.
* Richten Sie einen gemeinsamen Referenzpunkt ein.
* Geräteübergreifendes Freigeben von Koordinatensystemen.
* Alle sehen das gleiche Hologramm!

>[!NOTE]
>Die **Funktionen InternetClientServer** und **PrivateNetworkClientServer** müssen deklariert werden, damit eine App eine Verbindung mit dem Freigabeserver herstellen kann. Dies erfolgt für Sie bereits in Hologramme 240, aber beachten Sie dies für Ihre eigenen Projekte.

>1. Navigieren Sie im Unity-Editor zu den Playereinstellungen, indem Sie zu "Bearbeiten > Project Einstellungen > Player" navigieren.
>2. Klicken Sie auf die Registerkarte "Windows Store"
>3. Überprüfen Sie im Abschnitt "Einstellungen > Funktionen" die **Funktion InternetClientServer** und **die Funktion "PrivateNetworkClientServer".**

### <a name="instructions"></a>Anweisungen

* Navigieren Sie **Project Bereich** zum **Ordner HoloToolkit-Sharing-240\Prefabs\Sharing.**
* Drag and drop the **Sharing** prefab into the **Hierarchy panel**.

Als Nächstes müssen wir den Freigabedienst starten. Für **diesen Schritt** muss nur ein PC in der freigegebenen Beerfahrung verwendet werden.

* Wählen Sie in Unity im oberen Menü das **Menü HoloToolkit-Sharing-240 aus.**
* Wählen Sie **in der Dropdownliste** das Element Freigabedienst starten aus.
* Aktivieren Sie die **Option Privates Netzwerk,** und klicken **Sie auf Zugriff zulassen,** wenn die Firewallaufforderung angezeigt wird.
* Notieren Sie sich die IPv4-Adresse, die im Konsolenfenster des Freigabediensts angezeigt wird. Dies ist die gleiche IP-Adresse wie der Computer, auf dem der Dienst ausgeführt wird.

Befolgen Sie die restlichen Anweisungen auf **allen PCs,** die der freigegebenen Erfahrung beitreten.

* Wählen Sie **in der** Hierarchie das **Freigabeobjekt** aus.
* Ändern Sie im  **Inspektor** in der Komponente Freigabephase die **Serveradresse** von "localhost" in die IPv4-Adresse des Computers, auf dem SharingService.exe.
* Wählen Sie **in der Hierarchie** das **HologramCollection-Objekt** aus.
* Klicken Sie im **Inspektor** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
* Geben Sie im Suchfeld Import **Export Anchor Manager ein.** Wählen Sie das Suchergebnis aus.
* Navigieren Sie **Project Bereich** zum Ordner **Skripts.**
* Doppelklicken Sie auf das **HologramPlacement-Skript,** um es in der Visual Studio.
* Ersetzen Sie den Inhalt durch den folgenden Code:

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Wählen Sie in Unity im **Hierarchiebereich die HologramCollection** **aus.**
* Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
* Geben Sie im Menü in das Suchfeld **App State Manager ein.** Wählen Sie das Suchergebnis aus.

**Bereitstellen und Nutzen**

* Erstellen Sie das Projekt für Ihre HoloLens Geräte.
* Bestimmen Sie HoloLens, die zuerst bereitgestellt werden soll. Sie müssen warten, bis der Anker in den Dienst hochgeladen wurde, bevor Sie den EnergyHub platzieren können (dies kann ca. 30 bis 60 Sekunden dauern). Bis der Upload erfolgt ist, werden Ihre Tippgesten ignoriert.
* Nachdem der EnergyHub platziert wurde, wird sein Speicherort in den Dienst hochgeladen, und Sie können es dann auf allen anderen HoloLens bereitstellen.
* Wenn ein neuer HoloLens zum ersten Mal der Sitzung beitritt, ist der Speicherort des EnergyHub auf diesem Gerät möglicherweise nicht richtig. Sobald der Anker und die EnergyHub-Standorte jedoch vom Dienst heruntergeladen wurden, sollte der EnergyHub zum neuen, freigegebenen Standort springen. Wenn dies nicht innerhalb von ca. 30 bis 60 Sekunden geschieht, gehen Sie zu dem Ort, an dem sich die ursprüngliche HoloLens beim Festlegen des Ankers zum Sammeln weiterer Umgebungsankungen befing. Wenn der Standort immer noch nicht gesperrt ist, stellen Sie die Bereitstellung auf dem Gerät erneut vor.
* Wenn alle Geräte bereit sind und die App ausführen, suchen Sie nach EnergyHub. Können Sie sich alle über die Position des Hologramms und die Richtung des Texts einigen?

## <a name="chapter-4---discovery"></a>Kapitel 4: Ermittlung

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Jetzt kann jeder das gleiche Hologramm sehen! Sehen wir uns nun alle anderen an, die mit unserer gemeinsamen holografischen Welt verbunden sind. In diesem Kapitel greifen wir den Hauptstandort und die Drehung aller anderen HoloLens Geräte in derselben Freigabesitzung an.

### <a name="objectives"></a>Ziele

* Entdecken Sie sich gegenseitig in unserer gemeinsamen Erfahrung.
* Wählen Sie einen Player-Avatar aus, und geben Sie diesen frei.
* Fügen Sie den Player-Avatar neben den Kopf aller an.

### <a name="instructions"></a>Anweisungen

* Navigieren Sie **Project Bereich** zum **Ordner** Hologramme Ordner .
* Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.
* Navigieren Sie **Project Bereich** zum Ordner **Skripts.**
* Doppelklicken Sie auf das **Skript AvatarSelector,** um es in der Visual Studio.
* Ersetzen Sie den Inhalt durch den folgenden Code:

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* Wählen Sie **in der Hierarchie** das **HologramCollection-Objekt** aus.
* Klicken Sie im **Inspektor** auf **Komponente hinzufügen.**
* Geben Sie im Suchfeld Local **Player Manager ein.** Wählen Sie das Suchergebnis aus.
* Wählen Sie **in der Hierarchie** das **HologramCollection-Objekt** aus.
* Klicken Sie im **Inspektor** auf **Komponente hinzufügen.**
* Geben Sie im Suchfeld Remote **Player Manager ein.** Wählen Sie das Suchergebnis aus.
* Öffnen Sie **das HologramPlacement-Skript** in Visual Studio.
* Ersetzen Sie den Inhalt durch den folgenden Code:

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Öffnen Sie **das AppStateManager-Skript** in Visual Studio.
* Ersetzen Sie den Inhalt durch den folgenden Code:

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Bereitstellen und Nutzen**

* Erstellen Sie das Projekt, und stellen Sie es auf Ihren HoloLens zur Verfügung.
* Wenn Sie einen Pingklang hören, suchen Sie das Menü für die Avatarauswahl, und wählen Sie einen Avatar mit der Geste zum Tippen in die Luft aus.
* Wenn Sie keine Hologramme sehen, wird das Punktlicht um den Cursor eine andere Farbe drehen, wenn Ihre HoloLens mit dem Dienst kommuniziert: Initialisieren (dunkel violett), Herunterladen des Ankers (grün), Importieren/Exportieren von Standortdaten (gelb), Hochladen des Ankers (blau). Wenn Das Punktlicht um den Cursor die Standardfarbe (hellviolett) ist, können Sie mit anderen Playern in Ihrer Sitzung interagieren!
* Sehen Sie sich andere Personen an, die mit Ihrem Raum verbunden sind. Ein holografischer Roboter schwebt über ihren Händen und imitiert ihre Kopfbewegungen!

## <a name="chapter-5---placement"></a>Kapitel 5: Platzierung

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

In diesem Kapitel machen wir den Anker in der Lage, auf realen Oberflächen platziert zu werden. Wir verwenden gemeinsame Koordinaten, um diesen Anker im Mittelpunkt zwischen allen Beteiligten zu platzieren, die mit der gemeinsamen Erfahrung verbunden sind.

### <a name="objectives"></a>Ziele

* Platzieren Sie Hologramme basierend auf der Kopfposition des Spielers auf dem Gitternetz für die räumliche Zuordnung.

### <a name="instructions"></a>Anweisungen

* Navigieren Sie im **bereich Project** zum Ordner **Hologramme.**
* Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.
* Navigieren Sie im **bereich Project** zum Ordner **Skripts.**
* Doppelklicken Sie auf das **Skript AppStateManager,** um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code:

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* Navigieren Sie im **bereich Project** zum Ordner **Skripts.**
* Doppelklicken Sie auf das **HologramPlacement-Skript,** um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code:

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Bereitstellen und Nutzen**

* Erstellen Sie das Projekt, und stellen Sie es auf Ihren HoloLens Geräten bereit.
* Wenn die App bereit ist, stehen Sie in einem Kreis, und beachten Sie, wie der EnergyHub in der Mitte aller angezeigt wird.
* Tippen Sie auf , um den EnergyHub zu platzieren.
* Probieren Sie den Sprachbefehl "Ziel zurücksetzen" aus, um die EnergyHub-Sicherung zu wählen und als Gruppe zusammenzuarbeiten, um das Hologramm an einen neuen Speicherort zu verschieben.

## <a name="chapter-6---real-world-physics"></a>Kapitel 6 : Real-World-Physik

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

In diesem Kapitel fügen wir Hologramme hinzu, die von realen Oberflächen abprallen. Beobachten Sie, wie Ihr Platz mit Projekten gefüllt ist, die sowohl von Ihnen als auch von Ihren Freunden gestartet wurden!

### <a name="objectives"></a>Ziele

* Starten Sie Projektile, die von realen Oberflächen abprallen.
* Teilen Sie die Projektile, damit andere Spieler sie sehen können.

### <a name="instructions"></a>Anweisungen

* Wählen Sie in der **Hierarchie** das **HologramCollection-Objekt** aus.
* Klicken Sie im **Inspektor** auf **Komponente hinzufügen.**
* Geben Sie im Suchfeld **Projectile Startprogramm** ein. Wählen Sie das Suchergebnis aus.

**Bereitstellen und Nutzen**

* Erstellen Sie Ihre HoloLens Geräte, und stellen Sie sie bereit.
* Wenn die App auf allen Geräten ausgeführt wird, führen Sie einen Tipp in die Luft aus, um das Projektil auf realen Oberflächen zu starten.
* Sehen Sie, was geschieht, wenn Ihr Projektil mit dem Avatar eines anderen Spielers kollidiert!

## <a name="chapter-7---grand-finale"></a>Kapitel 7 – Großes Finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

In diesem Kapitel erfahren Sie, wie Sie ein Portal entdecken, das nur mit Zusammenarbeit ermittelt werden kann.

### <a name="objectives"></a>Ziele

* Arbeiten Sie zusammen, um genügend Projektile am Anker zu starten, um ein geheimes Portal zu entdecken!

### <a name="instructions"></a>Anweisungen

* Navigieren Sie im **bereich Project** zum Ordner **Hologramme.**
* Drag and drop the **Underworld** asset as a **child of HologramCollection**.
* Wenn **HologramCollection** ausgewählt ist, klicken Sie im **Inspektor** auf die Schaltfläche **Komponente hinzufügen.**
* Geben Sie im Menü in das Suchfeld **PloxenZiel ein.** Wählen Sie das Suchergebnis aus.
* Ziehen Sie bei ausgewählter **HologramCollection** aus der **Hierarchie** das **EnergyHub-Objekt** in das **Feld Ziel** im **Inspektor**.
* Ziehen Sie bei ausgewählter **HologramCollection** aus der **Hierarchie** das **Underworld-Objekt** in das **Feld Underworld** im **Inspektor**.

**Bereitstellen und Nutzen**

* Erstellen Sie Ihre HoloLens Geräte, und stellen Sie sie bereit.
* Wenn die App gestartet wurde, arbeiten Sie zusammen, um Projektile auf dem EnergyHub zu starten.
* Wenn die Unterwelt angezeigt wird, starten Sie Projektile bei Underworld-Robotern (dreimal auf einen Roboter, um zusätzlichen Spaß zu machen).