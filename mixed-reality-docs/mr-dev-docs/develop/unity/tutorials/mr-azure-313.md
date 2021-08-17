---
title: 'HoloLens (1. Generation) und Azure 313: IoT Hub-Dienst'
description: Erfahren Sie, wie Azure IoT Hub Service auf einem virtuellen Computer mit Ubuntu 16.4 implementiert und die Nachrichtendaten mithilfe eines Microsoft HoloLens VR-Headsets visualisiert werden.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, mixed reality, academy, edge, iot edge, tutorial, api, notification, functions, tables, hololens, immersive, vr, iot, virtual machine, ubuntu, python, Windows 10, Visual Studio
ms.openlocfilehash: fbd793a5941a5fa1b236403672680aa7df375f8d
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905761"
---
# <a name="hololens-1st-gen-and-azure-313-iot-hub-service"></a>HoloLens (1. Generation) und Azure 313: IoT Hub Service

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie Sie für die Entwicklung HoloLens 2.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

![Kursergebnis](images/AzureLabs-Lab313-00.png)

In diesem Kurs erfahren Sie, wie Sie einen **Azure IoT Hub-Dienst** auf einem virtuellen Computer implementieren, auf dem das Ubuntu 16.4-Betriebssystem ausgeführt wird. Anschließend **wird eine Azure-Funktions-App** verwendet, um Nachrichten von Ihrer Ubuntu-VM zu empfangen und das Ergebnis in einem **Azure-Tabellendienst zu speichern.** Anschließend können Sie diese Daten mithilfe von Power BI oder immersiven Headsets (VR) Microsoft HoloLens immersiven Headsets anzeigen. 

Der Inhalt dieses  Kurses gilt für IoT Edge-Geräte. Für diesen Kurs liegt der Schwerpunkt jedoch auf einer Umgebung für virtuelle Computer, sodass kein Zugriff auf ein physisches Edgegerät erforderlich ist.

In diesem Kurs lernen Sie:

- Stellen Sie **IoT Edge modul auf** einem virtuellen Computer (Ubuntu 16 OS) zur Darstellung Ihres IoT-Geräts.
- Fügen Sie **dem Edge Custom Vision-Modul ein Azure Custom Vision Tensorflow-Modell** mit Code hinzu, mit dem im Container gespeicherte Bilder analysiert werden.
- Richten Sie das Modul so ein, dass die Analyseergebnisnachricht zurück an Ihren IoT Hub **Service gesendet wird.**
- Verwenden Sie eine **Azure-Funktions-App,** um die Nachricht in einer **Azure-Tabelle zu speichern.**
- Richten **Sie** Power BI ein, um die gespeicherte Nachricht zu sammeln und einen Bericht zu erstellen.
- Visualisieren Sie Ihre IoT-Nachrichtendaten **in Power BI**.

Folgende Dienste werden verwendet:

- **Azure IoT Hub ist** ein Microsoft Azure-Dienst, mit dem Entwickler IoT-Ressourcen verbinden, überwachen und verwalten können. Weitere Informationen finden Sie auf der Seite [ **Azure IoT Hub-Dienst.**](https://azure.microsoft.com/services/iot-hub/)

- **Azure Container Registry** ist ein Microsoft Azure Service, mit dem Entwickler Containerimages für verschiedene Containertypen speichern können. Weitere Informationen finden Sie auf der Seite [ **Azure Container Registry-Dienst.**](https://azure.microsoft.com/services/container-registry/)

- **Die Azure-Funktions-App** ist Microsoft Azure Service, mit dem Entwickler kleine Codeteile ,Funktionen' in Azure ausführen können. Dies bietet eine Möglichkeit zum Delegieren von Arbeit an die Cloud und nicht an Ihre lokale Anwendung, was viele Vorteile haben kann. **Azure Functions** unterstützt mehrere Entwicklungssprachen, einschließlich C \# , F , \# Node.js, Java und PHP. Weitere Informationen finden Sie auf der Azure Functions [  Seite](/azure/azure-functions/functions-overview).

- **Azure Storage:** Tabellen ist ein Microsoft Azure-Dienst, mit dem Entwickler strukturierte, nicht SQL Daten in der Cloud speichern können, wodurch sie überall leicht zugänglich sind. Der Dienst bietet einen schemabasierten Entwurf, der die Weiterentwicklung von Tabellen nach Bedarf ermöglicht und daher sehr flexibel ist. Weitere Informationen finden Sie auf der [ **Seite "Azure-Tabellen".**](/azure/cosmos-db/table-storage-overview)

In diesem Kurs erfahren Sie, wie Sie den IoT Hub Service einrichten und verwenden und dann eine von einem Gerät bereitgestellte Antwort visualisieren. Sie müssen diese Konzepte auf ein benutzerdefiniertes Setup IoT Hub Service anwenden, das Sie möglicherweise erstellen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 313: IoT Hub-Dienst</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Voraussetzungen

Die neuesten Voraussetzungen für die Entwicklung mit Mixed Reality, einschließlich der Microsoft HoloLens, finden Sie im Artikel [Installieren der](../../install-the-tools.md) Tools.

> [!NOTE]
> Dieses Tutorial ist für Entwickler konzipiert, die über grundlegende Erfahrung mit Python verfügen. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Juli 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, [](../../install-the-tools.md) wie im Artikel Installieren der Tools aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit den Informationen übereinstimmen, die Sie in neuerer Software finden als die unten aufgeführten.

Die folgende Hardware und Software ist erforderlich:

- Windows 10 Fall Creators Update (oder höher), **Entwicklermodus aktiviert**

    > [!WARNING]
    > Sie können einen virtuellen Computer nicht mit Hyper-V in Windows 10 Home Edition ausführen.

- Windows 10 SDK (neueste Version)
- Ein HoloLens, **Entwicklermodus aktiviert**
- Visual Studio 2017.15.4 (wird nur für den Zugriff auf die Azure-Cloud-Explorer)
- Internetzugriff für Azure und IoT Hub Service. Weitere Informationen finden Sie unter diesem Link [zur Seite IoT Hub Service.](https://azure.microsoft.com/services/iot-hub/)
- Ein Machine Learning-Modell. Wenn Sie nicht über ein eigenes einsatzbereites Modell verfügen, können Sie das [in diesem Kurs bereitgestellte Modell verwenden.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)
- **Hyper-V-Software,** die auf Ihrem Windows 10-Entwicklungscomputer aktiviert ist.
- Ein virtueller Computer mit Ubuntu (16.4 oder 18.4), der auf Ihrem Entwicklungscomputer ausgeführt wird, oder alternativ können Sie einen separaten Computer unter Linux (Ubuntu 16.4 oder 18.4) verwenden. Weitere Informationen zum Erstellen eines virtuellen Computers auf Windows Hyper-V finden Sie im Kapitel ["Vor dem Start".](#before-you-start) (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Vorbereitung

1. Einrichten und Testen Ihrer HoloLens. Wenn Sie Unterstützung beim Einrichten Ihrer HoloLens benötigen, lesen Sie den Artikel HoloLens [Setup.](/hololens/hololens-setup)
2. Es ist eine gute  Idee, die Kalibrierung und **Sensoroptimierung** durchzuführen, wenn Sie mit der Entwicklung einer neuen HoloLens-App beginnen (manchmal kann es helfen, diese Aufgaben für jeden Benutzer auszuführen).

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel HoloLens Kalibrierung.](/hololens/hololens-calibration#hololens-2)

Hilfe zur Sensoroptimierung finden Sie unter diesem [Link zum Artikel HoloLens Sensoroptimierung.](/hololens/hololens-updates)

3. Richten Sie Ihren **virtuellen Ubuntu-Computer mithilfe** **von Hyper-V ein.** Die folgenden Ressourcen helfen Ihnen beim Prozess.
    1.  Folgen Sie zunächst diesem Link, [um die ISO-Datei Ubuntu 16.04.4 LTS (Xenial Xerus) herunterzuladen.](https://au.releases.ubuntu.com/16.04/) Wählen Sie das Desktopimage des **64-Bit-PCs (AMD64) aus.**
    2.  Stellen Sie **sicher, dass Hyper-V** auf Ihrem Windows 10 aktiviert ist. Unter diesem Link finden Sie Anleitungen zum [Installieren und Aktivieren von Hyper-V auf Windows 10.](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
    3.  Starten Sie Hyper-V, und erstellen Sie eine neue Ubuntu-VM. Unter diesem Link finden Sie eine [Schritt-für-Schritt-Anleitung](/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)zum Erstellen eines virtuellen Computers mit Hyper-V. Wenn Sie aufgefordert **werden, ein Betriebssystem aus einer** startbaren Imagedatei zu installieren, wählen Sie die **Ubuntu-ISO-Datei aus,** die Sie zuvor heruntergeladen haben.

    > [!NOTE]
    > Die **Verwendung von Hyper-V Quick Create** wird nicht empfohlen.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Kapitel 1: Abrufen des Custom Vision Modells

In diesem Kurs haben Sie Zugriff auf ein vorgefertigte Custom Vision, das Tastaturen und [Mausen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) von Bildern erkennt. Wenn Sie dies verwenden, fahren Sie mit [Kapitel 2 fort.](#chapter-2---the-container-registry-service)

Sie können jedoch die folgenden Schritte ausführen, wenn Sie Ihr eigenes Modell Custom Vision möchten:

1. Wechseln Sie **Custom Vision Project** die Registerkarte **Leistung.**

    > [!WARNING]
    > Ihr Modell muss eine kompakte *Domäne verwenden,* um das Modell zu exportieren. Sie können ihre Modelldomäne in den Einstellungen für Ihr Projekt ändern.

    ![Registerkarte "Leistung"](images/AzureLabs-Lab313-01.png)

2. Wählen Sie die **Iteration aus,** die Sie exportieren möchten, und klicken Sie auf **Exportieren.** Ein Blatt wird angezeigt.

    ![Blatt "Exportieren"](images/AzureLabs-Lab313-02.png)

3. Klicken Sie auf dem Blatt auf **Docker-Datei**.

    ![Docker auswählen](images/AzureLabs-Lab313-03.png)

4. Klicken Sie im Dropdownmenü auf **Linux** und dann auf **Herunterladen.**

    ![Klicken Sie auf Herunterladen.](images/AzureLabs-Lab313-04.png)

5. Entzippen Sie den Inhalt. Sie werden sie später in diesem Kurs verwenden.

## <a name="chapter-2---the-container-registry-service"></a>Kapitel 2: Der Container Registry Dienst

Der **Container Registry Service** ist das Repository, das zum Hosten Ihrer Container verwendet wird.

Der **IoT Hub-Dienst,** den Sie in diesem Kurs erstellen und verwenden, bezieht sich auf **Container Registry Service,** um die Container zu erhalten, die auf Ihrem Edgegerät bereitgestellt werden sollen.

1. Folgen Sie zunächst diesem [Link zum Azure-Portal,](https://portal.azure.com/)und melden Sie sich mit Ihren Anmeldeinformationen an.

2. Wechseln Sie **zu Ressource erstellen,** und suchen Sie **nach Container Registry**.

    ![Containerregistrierung](images/AzureLabs-Lab313-05.png)

3. Klicken Sie auf **Erstellen**.

    ![](images/AzureLabs-Lab313-06.png)

4. Legen Sie die Diensteinrichtungsparameter fest:

    1. Fügen Sie einen Namen für Ihr Projekt ein. In diesem Beispiel heißt er **IoTCRegistry.**

    2. Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Kurse), in einer gemeinsamen Ressourcengruppe zu speichern.

    3. Legen Sie den Speicherort des Diensts fest.

    4. Legen Sie **Administratorbenutzer** auf **Aktivieren fest.**

    5. Legen Sie **SKU** auf **Basic** fest. 

    ![](images/AzureLabs-Lab313-07.png)

5. Klicken Sie auf **Erstellen,** und warten Sie, bis die Dienste erstellt wurden. 

6. Sobald die Benachrichtigung angezeigt wird, die Sie über die erfolgreiche Erstellung des *Container Registry* informiert, klicken Sie auf **Zu Ressource** wechseln, um zur Seite Dienst umgeleitet zu werden.

    ![](images/AzureLabs-Lab313-08.png)

7. Klicken  Sie auf der Seite Container Registry-Diensts auf **Zugriffsschlüssel**.

8. Notieren Sie sich (Sie können Ihre Editor verwenden) die folgenden Parameter:
    1. **Anmeldeserver**
    2. **Benutzername**
    3. **Kennwort**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Kapitel 3: The IoT Hub Service

Nun beginnen Sie mit der Erstellung und Einrichtung Ihres **IoT Hub-Diensts.**

1. Wenn Sie noch nicht angemeldet sind, melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

2.  Klicken Sie nach der Anmeldung oben links auf **Ressource erstellen,** suchen Sie **nach IoT Hub**, und drücken Sie **die EINGABETASTE.**

 ![Nach Speicherkonto suchen](images/AzureLabs-Lab313-10.png)

3.  Die neue Seite enthält eine Beschreibung des **Storage-Kontodiensts.** Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen,** um eine Instanz dieses Diensts zu erstellen.

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-11.png)

4.  Nachdem Sie auf **Erstellen** geklickt haben, wird ein Bereich angezeigt:

    1. Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Kurse), in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe.](/azure/azure-resource-manager/resource-group-portal)


    2. Wählen Sie einen geeigneten **Standort** aus (Verwenden Sie den gleichen Standort für alle Dienste, die Sie in diesem Kurs erstellen).

    3. Fügen Sie den gewünschten **Namen** für diese Dienstinstanz ein.    

5.  Klicken Sie unten auf der Seite auf **Weiter: Größe und Skalierung.**

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-12.png)

6.  Wählen Sie auf dieser Seite Ihren **Tarif und Skalierungstarif** aus (wenn dies Ihre erste IoT Hub Service-Instanz ist, sollte Ihnen ein kostenloser Tarif zur Verfügung stehen).  

7.  Klicken Sie auf **Überprüfen + erstellen.**

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-13.png)

8.  Überprüfen Sie Ihre Einstellungen, und klicken Sie auf **Erstellen.**

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-14.png)

9. Sobald die Benachrichtigung angezeigt wird, die Sie über die erfolgreiche Erstellung des *IoT Hub-Diensts* informiert, klicken Sie auf Zu **Ressource** wechseln, um zur Seite Dienst umgeleitet zu werden.

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-15.png)

10. Scrollen Sie im Seitenbereich auf der linken Seite, bis *Automatische Geräteverwaltung* angezeigt wird, und klicken Sie auf **IoT Edge**.

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-16.png)

11. Klicken Sie im Fenster, das rechts angezeigt wird, auf **IoT Edge Gerät hinzufügen.** Rechts wird ein Blatt angezeigt.

12. Geben Sie auf dem Blatt ihrem neuen Gerät eine **Geräte-ID** (einen Namen Ihrer Wahl) an. Klicken Sie dann auf **Speichern**. Der *primäre* und *der sekundäre Schlüssel* werden automatisch generiert, wenn Sie Auto **Generate** aktiviert haben.

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-17.png)

13. Sie navigieren zurück zum Abschnitt *IoT Edge Geräte,* in dem Ihr neues Gerät aufgeführt wird. Klicken Sie auf Ihr neues Gerät (in der folgenden Abbildung rot dargestellt). 

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-18.png)

14. Erstellen Sie auf der angezeigten Seite *Gerätedetails* eine Kopie der **Verbindungszeichenfolge** (Primärschlüssel).

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-19.png)

15. Wechseln Sie zurück zum Bereich auf der linken Seite, und klicken Sie auf *Freigegebene Zugriffsrichtlinien*, um sie zu öffnen. 

16. Klicken Sie auf der angezeigten Seite auf **iothubowner,** und rechts neben dem Bildschirm wird ein Blatt angezeigt. 

17. Notieren Sie sich (auf Ihrem Editor) die **Verbindungszeichenfolge** (Primärschlüssel), um sie später beim Festlegen der *Verbindungszeichenfolge* auf Ihr Gerät zu verwenden.

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Kapitel 4: Einrichten der Entwicklungsumgebung

Zum Erstellen und Bereitstellen von *Modulen* für IoT Hub Edge müssen die folgenden Komponenten auf dem Entwicklungscomputer installiert sein, auf dem Windows 10 ausgeführt wird:

1.  [Docker für Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows): Sie werden aufgefordert, ein Konto zu erstellen, um es herunterladen zu können. 

    [![Docker für Windows herunterladen](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker *erfordert,* dass Windows 10 PRO *, Enterprise 14393* oder *Windows Server 2016 RTM* ausgeführt wird. Wenn Sie andere Versionen von Windows 10 ausführen, können Sie versuchen, Docker mit der [Docker-Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)zu installieren.

2.  [Python 3.6](https://www.python.org/downloads/).

    [![Herunterladen von Python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (auch als VS Code bezeichnet).](https://code.visualstudio.com/download)

    [![herunterladen VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Nach der Installation der oben genannten Software müssen Sie Ihren Computer neu starten.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Kapitel 5: Einrichten der Ubuntu-Umgebung

Jetzt können Sie mit dem Einrichten Ihres Geräts **mit Ubuntu OS** fortfahren. Führen Sie die folgenden Schritte aus, um die erforderliche Software zu installieren, um Ihre Container auf Ihrem Board bereitzustellen:

> [!IMPORTANT]
> Sie sollten den Terminalbefehlen immer **"sudo"** vorangestellt haben, um als Administratorbenutzer auszuführen. Dh:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Öffnen Sie das **Ubuntu-Terminal,** und verwenden Sie den folgenden Befehl, um **pip** zu installieren:

    > [! HINWEIS] Sie können *terminal* sehr einfach öffnen, indem Sie die Tastenkombination **verwenden: STRG+ALT+T.**

    ```bash
        sudo apt-get install python-pip
    ```

2.  In diesem Kapitel werden Sie möglicherweise vom *Terminal* aufgefordert, die Berechtigung zum Verwenden Ihres Gerätespeichers einzugeben und **y/n** (ja oder nein) einzugeben, **"y"** einzugeben und dann die **EINGABETASTE** zu drücken, um dies zu akzeptieren.

3.  Verwenden Sie nach Abschluss dieses Befehls den folgenden Befehl, um **curl** zu installieren:

    ```bash
        sudo apt install curl
    ```

4.  Sobald **pip** und **curl** installiert sind, verwenden Sie den folgenden Befehl, um die **IoT Edge Runtime** zu installieren. Dies ist erforderlich, um die Module auf Ihrem Board bereitzustellen und zu steuern:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. An diesem Punkt werden Sie aufgefordert, die *Laufzeitkonfigurationsdatei* zu öffnen, um die **Geräteverbindungszeichenfolge** einzufügen, die Sie sich notiert haben (in Ihrem Editor), beim Erstellen des **IoT Hub-Diensts** ([in Schritt 14 von Kapitel 3](#chapter-3---the-iot-hub-service)). Führen Sie die folgende Zeile im Terminal aus, um diese Datei zu öffnen:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. Die Datei **"config.yaml"** wird angezeigt und kann bearbeitet werden:

    > [!WARNING]
    > Wenn diese Datei geöffnet wird, kann sie etwas verwirrend sein. Sie bearbeiten diese Datei im *Terminal* selbst. 

    1.  Verwenden Sie die Pfeiltasten auf der Tastatur, um nach unten zu scrollen (Sie müssen ein wenig nach unten scrollen), um die Zeile mit zu erreichen:

        "**\<ADD DEVICE CONNECTION STRING HERE>**".

    2. Ersetzen Sie zeile, **einschließlich der Klammern,** durch die **Geräteverbindungszeichenfolge,** die Sie zuvor notiert haben.

7. Drücken Sie bei vorhandener Verbindungszeichenfolge auf der Tastatur die TASTEN **STRG+X,** um die Datei zu speichern. Sie werden aufgefordert, dies zu bestätigen, indem **Sie Y** eingeben. Drücken Sie dann die **EINGABETASTE,** um dies zu bestätigen. Sie kehren zum regulären *Terminal* zurück. 

8. Sobald alle diese Befehle erfolgreich ausgeführt wurden, haben Sie die **IoT Edge Runtime** installiert. Nach der Initialisierung startet die Runtime bei jedem Einschalten des Geräts eigenständig und befindet sich im Hintergrund und wartet auf die Bereitstellung von Modulen über den **IoT Hub-Dienst.**

9.  Führen Sie die folgende Befehlszeile aus, um die *IoT Edge Runtime* zu initialisieren:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Wenn Sie Änderungen an Der YAML-Datei oder dem obigen Setup vornehmen, müssen Sie die obige Neustartzeile erneut in *Terminal* ausführen.

10. Überprüfen Sie den *IoT Edge Runtimestatus,* indem Sie die folgende Befehlszeile ausführen. Die Runtime sollte mit dem Status **aktiv (wird ausgeführt)** in grünem Text angezeigt werden.

    ```bash
        sudo systemctl status iotedge
    ```

11. Drücken Sie **STRG+C,** um die Statusseite zu beenden. Sie können überprüfen, ob die *IoT Edge Runtime* die Container ordnungsgemäß abruft, indem Sie den folgenden Befehl eingeben:

    ```bash
        sudo docker ps
    ```

12. Eine Liste mit zwei (2) Containern sollte angezeigt werden. Dies sind die Standardmodule, die automatisch vom IoT Hub Service (edgeAgent und edgeHub) erstellt werden. Nachdem Sie Ihre eigenen Module erstellt und bereitgestellt haben, werden sie in dieser Liste unterhalb der Standardmodule angezeigt.

## <a name="chapter-6---install-the-extensions"></a>Kapitel 6: Installieren der Erweiterungen

> [!IMPORTANT]
> Die nächsten Kapitel (6-9) müssen auf Ihrem computerbasierten Windows 10 werden.

1. Öffnen **Sie VS Code**.

2. Klicken Sie auf **die Schaltfläche Erweiterungen** (quadratisch) auf der linken Leiste VS Code, um den Bereich **Erweiterungen zu öffnen.**

3. Suchen und installieren Sie die folgenden Erweiterungen (wie in der folgenden Abbildung dargestellt):

    1. Azure IoT Edge
    2. Azure IoT-Toolkit
    3. Docker   

    ![Erstellen Ihres Containers](images/AzureLabs-Lab313-24.png)

4. Schließen Sie die Erweiterungen, und öffnen Sie sie VS Code.

5. Wenn VS Code öffnen, navigieren Sie zu **Integriertes**  >  **Terminal anzeigen.**

6. Sie installieren nun **Cookiecutter**. Führen Sie im Terminal den folgenden Bash-Befehl aus:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! HINWEIS] Wenn Sie Probleme mit diesem Befehl haben: 
    >1. Starten VS Code und/oder Ihren Computer neu.
    >2. Es kann erforderlich sein, das **VS Code Terminal auf** das zu wechseln, das Sie zum Installieren von Python verwendet haben, d. h. **PowerShell** (insbesondere für den Fall, dass die Python-Umgebung bereits auf Ihrem Computer installiert ist). Wenn das Terminal geöffnet ist, finden Sie das Dropdownmenü auf der rechten Seite des Terminals.
     ![Erstellen Ihres Containers](images/AzureLabs-Lab313-24b.png) 
    >3. Stellen Sie sicher, **dass der Python-Installationspfad** als **Umgebungsvariable auf** Ihrem Computer hinzugefügt wird. Cookiecutter sollte Teil desselben Speicherortpfads sein. Weitere Informationen zu Umgebungsvariablen finden Sie [unter diesem Link.](/windows/win32/procthread/environment-variables) 

7. Sobald **Cookiecutter** die Installation abgeschlossen hat, sollten Sie Ihren Computer neu starten, damit **Cookiecutter** in der Umgebung Ihres Systems als Befehl erkannt wird.

## <a name="chapter-7---create-your-container-solution"></a>Kapitel 7: Erstellen Ihrer Containerlösung

An diesem Punkt müssen Sie den Container mit dem Modul erstellen, der in die *-Container Registry.* Nachdem Sie Ihren Container mithilfe von Push übertragen haben, verwenden Sie den *IoT Hub Edge-Dienst,* um ihn auf Ihrem Gerät bereitzustellen, auf dem die IoT Edge Runtime ausgeführt *wird.*

1. Klicken VS Code auf **Befehlspalette**  >  **anzeigen.**

2. Suchen Sie in der Palette nach , und führen Sie **Azure IoT Edge: Neue Iot Edge-Projektmappe aus.**

3. Navigieren Sie zu einem Speicherort, an dem Sie Ihre Lösung erstellen möchten. Drücken Sie die **EINGABETASTE,** um den Speicherort zu akzeptieren.

4. Geben Sie Ihrer Projektmappe einen Namen. Drücken Sie die **EINGABETASTE,** um ihren angegebenen Namen zu bestätigen.

5. Nun werden Sie aufgefordert, das Vorlagenframework für Ihre Lösung zu wählen. Klicken Sie **auf Python-Modul**. Drücken Sie die **EINGABETASTE,** um diese Auswahl zu bestätigen.

6. Geben Sie Ihrem Modul einen Namen. Drücken Sie die **EINGABETASTE,** um den Namen Ihres Moduls zu bestätigen. Notieren Sie sich (mit Ihrem Editor) den Modulnamen, da er später verwendet wird.

7. Sie werden feststellen, dass eine vorgefertigte *Docker Image Repository-Adresse* in der Palette angezeigt wird. Dies sieht wie in etwa wie hier aus:

    **localhost:5000/-THE NAME OF YOUR MODULE-**. 

8. Löschen **Sie localhost:5000,** und fügen Sie an seiner Stelle die Adresse des *Container Registry-Anmeldeservers*  ein, die Sie beim Erstellen des **Container Registry-Diensts** notiert haben ( in Schritt [8 von](#chapter-2---the-container-registry-service)Kapitel 2 ). Drücken Sie die **EINGABETASTE,** um die Adresse zu bestätigen.

9. An diesem Punkt wird die Lösung erstellt, die die Vorlage für Ihr Python-Modul enthält, und ihre Struktur wird auf der Registerkarte "Erkunden" von VS Code auf der linken Seite des Bildschirms angezeigt. Wenn die **Registerkarte "Untersuchen"** nicht geöffnet ist, können Sie sie öffnen, indem Sie in der Leiste auf der linken Seite auf die schaltfläche oben klicken.

    ![Erstellen Ihres Containers](images/AzureLabs-Lab313-25.png)

10. Der letzte Schritt für dieses Kapitel besteht im Klicken und Öffnen der **ENV-Datei** auf der Registerkarte *Untersuchen*  **und** hinzufügen Container Registry Benutzername und **Kennwort.** Diese Datei wird von Git ignoriert, aber beim Erstellen des Containers werden die Anmeldeinformationen für den Zugriff auf den Container Registry **Service festgelegt.**

    ![Erstellen Ihres Containers](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Kapitel 8: Bearbeiten Ihrer Containerlösung

Sie vervollständigen nun die Containerlösung, indem Sie die folgenden Dateien aktualisieren:

- *<span></span> py-Python-Hauptskript.*
- *requirements.txt*.
- *deployment.template.jsauf .*
- *Dockerfile.amd64*

Anschließend erstellen Sie den Ordner *images,* der vom Python-Skript verwendet wird, um nach Bildern zu überprüfen, die mit Ihrem Custom Vision *übereinstimmen.* Schließlich fügen Sie die  Dateilabels.txthinzu, um Ihr Modell zu lesen, und die Datei *model.pb,* die Ihr Modell ist.

1. Wenn VS Code geöffnet ist, navigieren Sie zu Ihrem Modulordner, und suchen Sie nach dem Skript **main <span></span> .py.** Öffnen Sie die Datei, indem Sie darauf doppelklicken.

2. Löschen Sie den Inhalt der Datei, und fügen Sie den folgenden Code ein:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  Öffnen Sie die Datei **requirements.txt**, und ersetzen Sie ihren Inhalt durch Folgendes:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Öffnen Sie die Dateideployment.template.js **auf**, und ersetzen Sie ihren Inhalt nach der folgenden Richtlinie:

    1. Da Sie über eine eigene, eindeutige JSON-Struktur verfügen, müssen Sie sie von Hand bearbeiten (anstatt ein Beispiel zu kopieren). Um dies zu ermöglichen, verwenden Sie die folgende Abbildung als Leitfaden.
    2. Bereiche, die sich von Ihren unterscheiden, die Sie jedoch NICHT ändern **sollten, sind gelb hervorgehoben.**
    3. **Abschnitte, die Sie löschen müssen, sind rot hervorgehoben.**
    4. Achten Sie darauf, die richtigen Klammern zu löschen und auch die Kommas zu entfernen.

        ![Erstellen Ihres Containers](images/AzureLabs-Lab313-27.png)

    5. Der fertige JSON-Code sollte wie in der folgenden Abbildung aussehen (mit Ihren eindeutigen Unterschieden: *Benutzername/Kennwort/Modulname/Modulverweise):*

        ![Erstellen Ihres Containers](images/AzureLabs-Lab313-28.png)

5.  Öffnen Sie die Datei **Dockerfile.amd64,** und ersetzen Sie ihren Inhalt durch Folgendes:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  Klicken Sie mit der rechten Maustaste auf den Ordner unter **den** Modulen (er hat den Namen, den Sie zuvor angegeben haben; im Beispiel weiter unten wird es *pythonmodule* genannt), und klicken Sie **auf Neuer Ordner**. Nennen Sie die **Ordnerbilder**.

7.  Fügen Sie im Ordner einige Bilder hinzu, die Maus oder Tastatur enthalten. Dies sind die Bilder, die vom Tensorflow-Modell analysiert werden.

    > [!WARNING]
    > Wenn Sie Ihr eigenes Modell verwenden, müssen Sie dies ändern, um Ihre eigenen Modelldaten widerzubildern.

8.  Sie müssen nun die Dateien **labels.txt** und **model.pb** aus dem Ordner model abrufen, den Sie zuvor in Kapitel 1 heruntergeladen (oder aus Ihrem eigenen **Custom Vision-Dienst erstellt)** [haben.](#chapter-1---retrieve-the-custom-vision-model) Sobald Sie über die Dateien verfügen, platzieren Sie sie zusammen mit den anderen Dateien in Ihrer Projektmappe. Das Endergebnis sollte wie in der folgenden Abbildung aussehen:

    ![Erstellen Ihres Containers](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Kapitel 9: Packen der Lösung als Container

1.  Nun können Sie Ihre Dateien als Container "packen" und in Ihren **Azure Container Registry.** Öffnen VS Code in VS Code das integrierte *Terminal* **(** Integriertes Terminal anzeigen oder STRG), und verwenden Sie die folgende Zeile, um sich bei Docker anzumelden (ersetzen Sie die Werte des Befehls durch die Anmeldeinformationen Ihrer  >   Azure Container Registry  + **\`** **(ACR)**): 

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Klicken Sie mit der rechten Maustaste auf **die Dateideployment.template.js,** und klicken Sie auf **Projektmappe IoT Edge erstellen.** Dieser Buildprozess dauert (abhängig von Ihrem Gerät) einige Zeit, daher sollten Sie darauf vorbereitet sein, zu warten. Nach Abschluss des Buildprozesses wurde **deployment.js** in einem neuen Ordner namens **config erstellt.**

    ![Erstellen der Bereitstellung](images/AzureLabs-Lab313-30.png)

3. Öffnen Sie erneut **die Befehlspalette,** und suchen Sie **nach Azure: Anmelden.** Befolgen Sie die Anweisungen unter Verwendung Ihrer Azure-Kontoanmeldeinformationen. VS Code ihnen eine Option zum Kopieren und Öffnen zur Verfügung, um den Gerätecode zu kopieren, den Sie in Kürze benötigen, und Ihren Standardwebbrowser zu öffnen. Wenn Sie dazu aufgefordert werden, fügen Sie den Gerätecode ein, um Ihren Computer zu authentifizieren.

    ![Kopieren und Öffnen](images/AzureLabs-Lab313-31.png)

4. Sobald Sie angemeldet sind, sehen Sie  unten im Bereich "Erkunden" einen neuen Abschnitt mit dem Namen Azure IoT **Hub-Geräte**. Klicken Sie auf diesen Abschnitt, um ihn zu erweitern.

    ![Edgegerät](images/AzureLabs-Lab313-32.png)

5. Wenn Ihr Gerät nicht hier ist, müssen Sie mit der rechten Maustaste auf *Azure IoT Hub-Geräte* klicken und dann auf **Set IoT Hub Connection String (Verbindungszeichenfolge festlegen) klicken.** Sie sehen dann, dass Sie in der Befehlspalette **(am** oberen VS Code) aufgefordert werden, Ihre *Verbindungszeichenfolge eingibt.* Dies ist die *Verbindungszeichenfolge,* die Sie sich am Ende von [Kapitel 3 notiert haben.](#chapter-3---the-iot-hub-service) Drücken Sie **die EINGABETASTE,** nachdem Sie die Zeichenfolge kopiert haben.    

6. Ihr Gerät sollte geladen und angezeigt werden. Klicken Sie mit der rechten Maustaste auf den Gerätenamen, und klicken Sie dann **auf Bereitstellung für einzelnes Gerät erstellen.**

    ![Erstellen der Bereitstellung](images/AzureLabs-Lab313-33b.png)

7. Sie erhalten eine *Datei-Explorer-Eingabeaufforderung,* in der Sie zum Ordner **config** navigieren und dann die Dateideployment.js **auswählen** können. Klicken Sie bei ausgewählter Datei auf die Schaltfläche **Edgebereitstellungsmanifest auswählen.**

    ![Erstellen der Bereitstellung](images/AzureLabs-Lab313-34.png)

8. An diesem Punkt haben Sie Ihrem **IoT Hub-Dienst** das Manifest für die Bereitstellung Ihres Containers als Modul von Ihrem **Azure Container Registry** bereitgestellt, um ihn effektiv auf Ihrem Gerät bereitzustellen.

9. Um die Nachrichten anzuzeigen, die von Ihrem Gerät an die IoT Hub gesendet werden, klicken Sie im Abschnitt **Azure IoT Hubgeräte** im **Explorer-Bereich** erneut auf ihren Gerätenamen, und klicken Sie auf **Überwachung der D2C-Nachricht starten.** Die von Ihrem Gerät gesendeten Nachrichten sollten im VS-Terminal angezeigt werden. Seien Sie mit Vorsicht, da dies einige Zeit in Anspruch nehmen kann. Im nächsten Kapitel finden Sie Informationen zum Debuggen und überprüfen, ob die Bereitstellung erfolgreich war.

Dieses Modul durchlauft nun zwischen den Bildern im Ordner **images** und analysiert sie bei jeder Iteration. Dies ist natürlich nur eine Demonstration, wie das grundlegende Machine Learning-Modell in einer IoT Edge Geräteumgebung funktioniert. 

Um die Funktionalität dieses Beispiels zu erweitern, können Sie auf verschiedene Weise fortfahren. Eine Möglichkeit wäre das Einschließen von Code in den Container, der Fotos von einer Webcam erfasst, die mit dem Gerät verbunden ist, und die Bilder im Ordner images speichert. 

Eine andere Möglichkeit ist das Kopieren der Images vom IoT-Gerät in den Container. Eine praktische Möglichkeit hierzu besteht darin, den folgenden Befehl im IoT-Geräteterminal auszuführen (möglicherweise könnte eine kleine App die Aufgabe erledigen, wenn Sie den Prozess automatisieren möchten). Sie können diesen Befehl testen, indem Sie ihn manuell aus dem Ordnerspeicherort ausführen, in dem Ihre Dateien gespeichert sind:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Kapitel 10: Debuggen der IoT Edge Runtime

Im Folgenden sind eine Liste der Befehlszeilen und Tipps aufgeführt, mit denen Sie die Messagingaktivität der *IoT Edge Runtime* von Ihrem **Ubuntu-Gerät** aus überwachen und debuggen können. 

- Überprüfen Sie den *IoT Edge Runtime-Status,* indem Sie die folgende Befehlszeile ausführen:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Denken Sie daran, **STRG+C** zu drücken, um die Statusanzeige abzuschließen.

- Listen Sie die Container auf, die derzeit bereitgestellt sind. Wenn der *IoT Hub-Dienst* die Container erfolgreich bereitgestellt hat, werden sie über die folgende Befehlszeile angezeigt:

    ```bash
        sudo iotedge list
    ```

    oder

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Das obige Beispiel ist eine gute Möglichkeit, um zu überprüfen, ob Ihr Modul erfolgreich bereitgestellt wurde, da es in der Liste angezeigt wird. Andernfalls werden **nur** *edgeHub* und *edgeAgent* angezeigt.

- Führen Sie die folgende Befehlszeile aus, um die Codeprotokolle eines Containers anzuzeigen:

    ```bash
        journalctl -u iotedge
    ```

**Nützliche Befehle zum Verwalten der IoT Edge Runtime:**

-  So löschen Sie alle Container auf dem Host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  So beenden Sie die *IoT Edge Runtime:*

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Kapitel 11: Erstellen eines Tabellendiensts 

Navigieren Sie zurück zu Ihrem Azure-Portal, in dem Sie einen Azure-Tabellendienst erstellen, indem Sie eine Storage Ressource erstellen.

1. Wenn Sie noch nicht angemeldet sind, melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

2. Klicken Sie nach der Anmeldung oben links auf **Ressource erstellen,** suchen Sie **nach Storage Konto,** und drücken Sie die **EINGABETASTE,** um die Suche zu starten.

3. Sobald es angezeigt wird, klicken Sie in der Liste auf Storage Konto : **Blob, Datei, Tabelle, Warteschlange.**

    ![Nach Speicherkonto suchen](images/AzureLabs-Lab313-35.png)

4. Die neue Seite enthält eine Beschreibung des **Storage-Kontodiensts.** Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen,** um eine Instanz dieses Diensts zu erstellen.

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab313-36.png)

5. Nachdem Sie auf **Erstellen** geklickt haben, wird ein Bereich angezeigt:

    1. Fügen Sie den gewünschten **Namen** für diese Dienstinstanz ein (*muss nur aus Kleinbuchstaben sein).*

    2. Klicken Sie für **Bereitstellungsmodell** auf **Ressourcen-Manager**.

    3. Klicken Sie unter **Kontoart** im Dropdownmenü auf **Storage (Allgemein v1).**

    4. Klicken Sie auf einen geeigneten **Speicherort.**
    
    5. Klicken Sie im Dropdownmenü **Replikation** auf **Georedundanter Speicher mit Lesezugriff (RA-GRS).**

    6. Klicken Sie für **Leistung** auf **Standard**.

    7. Klicken Sie im Abschnitt **Sichere Übertragung erforderlich** auf **Deaktiviert.**

    8. Klicken Sie im Dropdownmenü **Abonnement** auf ein entsprechendes Abonnement.

    9. Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Kurse), in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe.](/azure/azure-resource-manager/resource-group-portal)

    10. Belassen Sie **Virtuelle Netzwerke** als **Deaktiviert,** wenn dies eine Option für Sie ist.

    11. Klicken Sie auf **Erstellen**.

        ![Eingeben von Speicherdetails](images/AzureLabs-Lab313-37.png)

6. Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

7. Sobald die Dienstinstanz erstellt wurde, wird eine Benachrichtigung im Portal angezeigt. Klicken Sie auf die Benachrichtigungen, um Ihre neue Dienstinstanz zu untersuchen.

    ![Benachrichtigung über neuen Speicher](images/AzureLabs-Lab313-38.png)

8. Klicken Sie in der Benachrichtigung auf die Schaltfläche **Zu Ressource** wechseln, und Sie gelangen zur Übersichtsseite ihrer neuen Storage Dienstinstanz.

    ![Zu Ressource wechseln](images/AzureLabs-Lab313-39.png)

9. Klicken Sie auf der Übersichtsseite auf der rechten Seite auf **Tabellen.**
    
    ![Tabellen](images/AzureLabs-Lab313-40.png)

10. Der Bereich auf der rechten Seite wird so geändert, dass die **Tabellendienstinformationen** angezeigt werden, in denen Sie eine neue Tabelle hinzufügen müssen. Klicken Sie hierzu in der linken oberen Ecke auf die Schaltfläche **+ Tabelle.**

    ![Öffnen von Tabellen](images/AzureLabs-Lab313-41.png)

11. Es wird eine neue Seite angezeigt, auf der Sie einen **Tabellennamen** eingeben müssen. Dies ist der Name, den Sie verwenden, um in späteren Kapiteln (Erstellen einer Funktions-App und Power BI) auf die Daten in Ihrer Anwendung zu verweisen. Fügen Sie **IoTMessages** als Namen ein (Sie können Ihre eigene Auswählen, sie sich einfach merken, wenn Sie sie später in diesem Dokument verwenden), und klicken Sie auf **OK**. 

12. Nachdem die neue Tabelle erstellt wurde, wird sie auf der Seite **Tabellendienst** (unten) angezeigt.

    ![Neue Tabelle erstellt](images/AzureLabs-Lab313-42.png)  

13. Klicken Sie nun auf **Zugriffsschlüssel,** und nehmen Sie eine Kopie des **kontonamens** **und** schlüssels Storage (unter Verwendung Ihrer Editor) entgegen. Sie verwenden diese Werte später in diesem Kurs beim Erstellen der **Azure-Funktions-App**.

    ![Neue Tabelle erstellt](images/AzureLabs-Lab313-43.png) 

14. Scrollen Sie im Bereich auf der linken Seite erneut zum Abschnitt *Tabellendienst,* klicken Sie auf **Tabellen** (oder **Tabellen durchsuchen**, in neueren Portalen), und erstellen Sie eine Kopie der **Tabellen-URL** (mithilfe Ihrer Editor). Sie verwenden diesen Wert später in diesem Kurs, wenn Sie Ihre Tabelle mit Ihrer **Power BI** Anwendung verknüpfen.

    ![Neue Tabelle erstellt](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Kapitel 12: Abschließen der Azure-Tabelle

Nachdem Ihr **Table Service-Speicherkonto** eingerichtet wurde, ist es an der Zeit, diesem Daten hinzuzufügen, die zum Speichern und Abrufen von Informationen verwendet werden. Die Bearbeitung Ihrer Tabellen kann über **Visual Studio** erfolgen.

1. Öffnen **Sie Visual Studio** (**nicht** Visual Studio Code).

2. Klicken Sie im Menü auf  >  **Ansicht Cloud-Explorer**.

    ![Öffnen des Cloud-Explorers](images/AzureLabs-Lab313-45.png)

3. Die **Cloud-Explorer** wird als angedocktes Element geöffnet (seien Sie dabei, da das Laden eine Weile dauern kann).

    > [!WARNING] 
    > Wenn das Abonnement, das Sie zum Erstellen Ihrer *Storage-Konten* verwendet haben, nicht sichtbar ist, stellen Sie sicher, dass Sie über Folgendes verfügen: 
    > - Angemeldet bei demselben Konto wie das Konto, das Sie für das Azure-Portal verwendet haben.
    > - Wählen Sie auf der Seite Kontoverwaltung Ihr Abonnement aus (Möglicherweise müssen Sie einen Filter aus Ihren Kontoeinstellungen anwenden):  
    >
    >   ![Abonnement suchen](images/AzureLabs-Lab313-46.png)

4. Ihre Azure-Clouddienste werden angezeigt. Suchen Sie **nach Storage Konten,** und klicken Sie auf den Pfeil links davon, um Ihre Konten zu erweitern.

    ![Öffnen von Speicherkonten](images/AzureLabs-Lab313-47.png)

5. Nach dem Erweitern sollte Ihr neu erstelltes **Storage-Konto** verfügbar sein. Klicken Sie auf den Pfeil links neben Ihrem Speicher, und suchen Sie nach dem Erweitern nach **Tabellen,** und klicken Sie auf den Pfeil daneben, um die **Tabelle** zu öffnen, die Sie im letzten Kapitel erstellt haben. Doppelklicken Sie auf Ihre **Tabelle**.

6. Die Tabelle wird in der Mitte des fensters Visual Studio geöffnet. Klicken Sie auf das Tabellensymbol mit dem **+** (Pluszeichen) darauf.

    ![Neue Tabelle hinzufügen](images/AzureLabs-Lab313-48.png)

7. Es wird ein Fenster angezeigt, in dem Sie aufgefordert werden, *Entität hinzuzufügen.* Sie erstellen nur eine Entität, obwohl sie drei Eigenschaften hat. Sie werden feststellen, dass *PartitionKey* und *RowKey* bereits bereitgestellt wurden, da diese von der Tabelle verwendet werden, um Ihre Daten zu suchen. 

    ![Partition und Zeilenschlüssel](images/AzureLabs-Lab313-49.png)

8. Ändern Sie die folgenden Werte:

    - Name: **PartitionKey,** Wert: **PK_IoTMessages** 

    - Name: **RowKey,** Wert: **RK_1_IoTMessages** 

9. Klicken Sie dann auf **Eigenschaft hinzufügen** (links unten im Fenster *Entität hinzufügen),* und fügen Sie die folgende Eigenschaft hinzu:

    - **MessageContent** als *Zeichenfolge* lässt den Wert leer.

10. Ihre Tabelle sollte mit der Tabelle in der folgenden Abbildung übereinstimmen:

    ![Richtige Werte hinzufügen](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > Der Grund, warum die Entität die Zahl 1 im Zeilenschlüssel enthält, liegt daran, dass Sie möglicherweise weitere Nachrichten hinzufügen möchten, wenn Sie mit diesem Kurs weiter experimentieren möchten.

11. Klicken Sie anschließend auf **OK**. Die Tabelle kann nun verwendet werden.

## <a name="chapter-13---create-an-azure-function-app"></a>Kapitel 13: Erstellen einer Azure-Funktions-App 

Es ist nun an der Zeit, eine *Azure-Funktions-App* zu erstellen, die vom *IoT Hub-Dienst* aufgerufen wird, um die *IoT Edge* Gerätenachrichten im **Tabellenspeicherdienst** zu speichern, den Sie im vorherigen Kapitel erstellt haben.

Zunächst müssen Sie eine Datei erstellen, mit der Ihre Azure-Funktion die benötigten Bibliotheken laden kann.

1.  Öffnen **Sie Editor** (drücken Sie die Windows *Taste*, und geben Sie *Editor* ein.

    ![Editor öffnen](images/AzureLabs-Lab313-51.png)

2.  Fügen Sie bei geöffneter Editor die unten stehende JSON-Struktur ein. Sobald Sie dies getan haben, speichern Sie sie auf Ihrem Desktop als **project.jsauf**. Diese Datei definiert die Bibliotheken, die Ihre Funktion verwenden wird. Wenn Sie NuGet verwendet haben, wird es ihnen vertraut vorkommen.
    
    > [!WARNING]
    > Es ist wichtig, dass die Benennung richtig ist. stellen Sie  sicher, dass keine .txt-Dateierweiterung enthalten ist. Weitere Informationen finden Sie unten:
    >
    > ![JSON-Speicher](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

4.  Nachdem Sie sich angemeldet haben, klicken Sie oben links auf **Ressource erstellen,** suchen Sie nach **Funktions-App,** und drücken Sie die **EINGABETASTE,** um zu suchen. Klicken Sie in den Ergebnissen auf *Funktions-App,* um einen neuen Bereich zu öffnen.

    ![Suchen nach Funktions-App](images/AzureLabs-Lab313-53.png)

5.  Der neue Bereich stellt eine Beschreibung des **Funktions-App-Diensts** bereit. Klicken Sie unten links in diesem Bereich auf die Schaltfläche **Erstellen,** um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Funktions-App-Instanz](images/AzureLabs-Lab313-54.png)

6.  Nachdem Sie auf **Erstellen** geklickt haben, geben Sie Folgendes ein:

    1. Fügen Sie unter **App-Name** den gewünschten Namen für diese Dienstinstanz ein.

    2. Wählen Sie ein **Abonnement** aus.

    3. Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal eine **Funktion App Service** erstellen, sollte Ihnen ein kostenloser Tarif zur Verfügung stehen.

    4. Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Kurse), in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe.](/azure/azure-resource-manager/resource-group-portal)

    5. Klicken Sie für **Betriebssystem** auf Windows, da dies die vorgesehene Plattform ist.

    6. Wählen Sie einen **Hostingplan** aus (in diesem Tutorial wird ein **Verbrauchstarif verwendet).**

    7. Wählen Sie einen **Standort** aus (wählen Sie den gleichen Standort wie der Speicher aus, den Sie im vorherigen Schritt erstellt haben).

    8. Für den **Abschnitt Storage** **müssen Sie den Storage-Dienst auswählen, den Sie im vorherigen Schritt erstellt haben.**

    9. Sie benötigen keine *Application Insights* in dieser App. Lassen Sie **sie** daher aus.

    10. Klicken Sie auf **Erstellen**.

        ![Erstellen einer neuen Instanz](images/AzureLabs-Lab313-55.png)

7.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

8.  Sobald die Dienstinstanz erstellt wurde, wird eine Benachrichtigung im Portal angezeigt.

    ![neue Benachrichtigung](images/AzureLabs-Lab313-56.png)

9.  Klicken Sie auf die Benachrichtigung, sobald die Bereitstellung erfolgreich war (abgeschlossen).

10. Klicken Sie in der Benachrichtigung auf die Schaltfläche **Zu Ressource** wechseln, um Ihre neue Dienstinstanz zu untersuchen. 

    ![Zu Ressource wechseln](images/AzureLabs-Lab313-57.png)

11. Klicken Sie auf der linken Seite des neuen Bereichs neben Funktionen auf das **+** Symbol (Pluszeichen), um eine neue Funktion zu erstellen. 

    ![Neue Funktion hinzufügen](images/AzureLabs-Lab313-58.png)

12. Im zentralen Bereich wird das Fenster **Funktionserstellung** angezeigt. Scrollen Sie weiter nach unten, und klicken Sie auf **Benutzerdefinierte Funktion**.

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-59.png)

13. Scrollen Sie auf der nächsten Seite nach unten, bis Sie **IoT Hub (Event Hub)** finden, und klicken Sie dann darauf.

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-60.png)

14. Legen Sie auf dem Blatt **IoT Hub (Event Hub)** die **Sprache** auf **C#** fest, und klicken Sie dann auf **neu.**

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-61.png)

15. Stellen Sie im daraufhin angezeigten Fenster sicher, dass **IoT Hub** ausgewählt ist und der Name des *Felds IoT Hub* dem Namen Ihres zuvor erstellten *IoT Hub-Diensts* entspricht ([in Schritt 8 von Kapitel 3](#chapter-3---the-iot-hub-service)). Klicken Sie dann auf die Schaltfläche **Auswählen.**

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-62.png)

16. Klicken Sie auf dem Blatt **IoT Hub (Event Hub)** auf **Erstellen.**

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-63.png)

17. Sie werden zum Funktions-Editor umgeleitet.

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-64.png)

18. Löschen Sie den gesamten Code darin, und ersetzen Sie ihn durch Folgendes:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. Ändern Sie die folgenden Variablen so, dass sie den entsprechenden Werten **(Tabelle** und **Storage** Werte aus [Schritt 11 bzw. 13 von Kapitel 11) entsprechen,](#chapter-11---create-table-service)die Sie in Ihrem **Storage-Konto** finden:

    - **tableName** mit dem Namen Ihrer **Tabelle** in Ihrem **Storage-Konto.**
    - **tableURL** mit der URL Ihrer **Tabelle** in Ihrem **Storage-Konto.**
    - **storageAccountName** mit dem Namen des Werts, der dem Namen Ihres **Storage Kontonamens** entspricht.
    - **storageAccountKey** mit dem Schlüssel, den Sie in der zuvor erstellten Storage Service abgerufen haben.

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-65.png)

20. Wenn der Code vorhanden ist, klicken Sie auf **Speichern.**

21. Klicken Sie als Nächstes auf das **\<** Symbol (Pfeil) auf der rechten Seite der Seite.

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-66.png)

22. Ein Bereich wird von rechts eingeblendet. Klicken Sie in diesem Bereich auf **Hochladen**, und ein *Dateibrowser* wird angezeigt.

23. Navigieren Sie zu dem **project.js** in der Datei, die Sie zuvor in **Editor** erstellt haben, und klicken Sie darauf, und klicken Sie dann auf die Schaltfläche **Öffnen.** Diese Datei definiert die Bibliotheken, die ihre Funktion verwenden wird.

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-67.png)

24. Wenn die Datei hochgeladen wurde, wird sie im Bereich auf der rechten Seite angezeigt. Wenn Sie darauf klicken, wird es im **Funktions-Editor** geöffnet. Er muss **genau** wie das nächste Bild aussehen.

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-68.png)

25. An diesem Punkt wäre es gut, die Funktion Ihrer Funktion zum Speichern der Nachricht in Ihrer *Tabelle* zu testen. Klicken Sie oben rechts im Fenster auf **Testen.**

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-69.png)

26. Fügen Sie eine Meldung im **Anforderungstext** ein, wie in der Abbildung oben gezeigt, und klicken Sie auf **Ausführen.** 

27. Die Funktion wird ausgeführt und zeigt den Ergebnisstatus an (Sie werden den grünen **Status 202 Akzeptiert** über dem *Fenster Ausgabe* sehen, was bedeutet, dass es sich um einen erfolgreichen Aufruf handelt):

    ![Ausgabeergebnis](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Kapitel 14: Anzeigen aktiver Nachrichten

Wenn Sie nun Visual Studio **(nicht** Visual Studio Code) öffnen, können Sie das Ergebnis der Testmeldung visualisieren, da es im *Zeichenfolgenbereich MessageContent* gespeichert wird.

![Benutzerdefinierte Funktion](images/AzureLabs-Lab313-71.png)

Wenn der Tabellendienst und die Funktions-App vorhanden sind, werden Ihre Ubuntu-Gerätenachrichten in Ihrer *IoTMessages-Tabelle* angezeigt. Wenn sie noch nicht ausgeführt wird, starten Sie Ihr Gerät erneut, und Sie können die Ergebnismeldungen von Ihrem Gerät und Modul in Ihrer Tabelle anzeigen, indem Sie Visual Studio *Cloud-Explorer* verwenden.

![Visualisieren von Daten](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Kapitel 15 – Power BI Setup

Um die Daten von Ihrem IoT-Gerät zu visualisieren, richten Sie **Power BI** (Desktopversion) ein, um die Daten aus dem soeben erstellten *Tabellendienst* zu sammeln. Die *HoloLens* Version von Power BI verwendet diese Daten dann, um das Ergebnis zu visualisieren.

1.  Öffnen Sie die Microsoft Store unter Windows 10, und suchen Sie **nach Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Laden Sie die Anwendung herunter. Nachdem der Download abgeschlossen ist, öffnen Sie ihn.

3.  Melden Sie sich mit Ihrem **Microsoft 365-Konto** bei Power BI an.  Sie werden möglicherweise an einen Browser umgeleitet, um sich zu registrieren. Nachdem Sie sich angemeldet haben, kehren Sie zur Power BI-App zurück, und melden Sie sich erneut an.

4.  Klicken Sie auf **Daten abrufen** und dann auf **Mehr...**.

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Klicken Sie auf **Azure**, **Azure Table Storage** und dann auf **Verbinden**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Sie werden beim Erstellen des Tabellendiensts aufgefordert, die zuvor erfasste **Tabellen-URL** [(in Schritt 13 von Kapitel 11)](#chapter-11---create-table-service)einzufügen. Löschen Sie nach dem Einfügen der URL den Teil des Pfads, der auf die Tabelle "sub-folder" verweist (in diesem Kurs IoTMessages). Das Endergebnis sollte wie in der folgenden Abbildung dargestellt sein. Klicken Sie dann auf **OK.**

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Sie werden aufgefordert, den **Storage Schlüssel** einzufügen, den Sie zuvor beim Erstellen der Tabelle Storage notiert haben ( in Schritt [11 von Kapitel 11](#chapter-11---create-table-service)). Klicken Sie dann auf **Verbinden**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Ein **Navigatorbereich** wird angezeigt, aktivieren Sie das Kontrollkästchen neben Ihrer Tabelle, und klicken Sie auf **Laden.**

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. Die Tabelle wurde jetzt auf Power BI geladen, erfordert jedoch eine Abfrage, um die darin enthaltenen Werte anzuzeigen. Klicken Sie hierzu mit der rechten Maustaste auf den Tabellennamen im **Bereich FELDER** auf der rechten Seite des Bildschirms. Klicken Sie dann auf **Abfrage bearbeiten.**

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Ein **Power Query-Editor**  wird als neues Fenster geöffnet, in dem Ihre Tabelle angezeigt wird. Klicken Sie in der Spalte *Inhalt* der Tabelle auf das Wort **Datensatz,** um den gespeicherten Inhalt zu visualisieren.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Klicken Sie oben links im Fenster auf **In Tabelle** ein. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Klicken Sie auf **Schließen & Übernehmen.**

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Sobald das Laden der Abfrage abgeschlossen ist, aktivieren Sie im **Bereich FELDER** auf der rechten Seite des Bildschirms die Kontrollkästchen, die den Parametern **Name** und **Wert** entsprechen, um den Inhalt der **MessageContent-Spalte** zu visualisieren.

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Klicken Sie oben links im Fenster auf das **blaue Datenträgersymbol,** um Ihre Arbeit in einem Ordner Ihrer Wahl zu speichern.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Sie können jetzt auf die Schaltfläche Veröffentlichen klicken, um Ihre Tabelle in Ihren Arbeitsbereich hochzuladen. Wenn Sie dazu aufgefordert werden, klicken Sie auf **Mein Arbeitsbereich** und dann auf *Auswählen.* Warten Sie, bis das erfolgreiche Ergebnis der Übermittlung angezeigt wird.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> Das folgende Kapitel ist HoloLens spezifisch. Power BI ist derzeit nicht als immersive Anwendung verfügbar. Sie können die Desktopversion jedoch über die Desktop-App im Windows Mixed Reality-Portal (auch als Haus an den Klippen bezeichnet) ausführen.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Kapitel 16: Anzeigen Power BI Daten auf HoloLens

1. Melden Sie sich auf Ihrem HoloLens beim **Microsoft Store** an, indem Sie in der Anwendungsliste auf das zugehörige Symbol tippen.

    ![Power BI Hl](images/AzureLabs-Lab313-87.png)

2. Suchen Sie die **anwendung Power BI,** und laden Sie sie herunter.

    ![Power BI Hl](images/AzureLabs-Lab313-88.png)

3. Starten Sie **Power BI** aus der Anwendungsliste. 

4. **Power BI** bitten Sie möglicherweise, sich bei Ihrem **Microsoft 365-Konto** anzumelden.

5. In der App sollte der Arbeitsbereich standardmäßig wie in der folgenden Abbildung dargestellt angezeigt werden. Wenn dies nicht der Fall ist, klicken Sie einfach auf das Arbeitsbereichssymbol auf der linken Seite des Fensters.

    ![Power BI Hl](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Ihre IoT Hub-Anwendung wurde abgeschlossen.

Herzlichen Glückwunsch! Sie haben erfolgreich einen IoT Hub Service mit einem simulierten Virtual Machine Edge-Gerät erstellt. Ihr Gerät kann die Ergebnisse eines Machine Learning-Modells mit einem Azure-Tabellendienst kommunizieren, der von einer Azure-Funktions-App ermöglicht wird, die in Power BI gelesen und innerhalb eines Microsoft HoloLens visualisiert wird.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Erweitern Sie die in der Tabelle gespeicherte Messagingstruktur, und zeigen Sie sie als Diagramm an. Möglicherweise möchten Sie weitere Daten sammeln und in derselben Tabelle speichern, um später angezeigt zu werden.

### <a name="exercise-2"></a>Übung 2

Erstellen Sie ein zusätzliches "Kameraaufnahmemodul", das auf dem IoT-Board bereitgestellt werden soll, damit es Bilder über die zu analysierende Kamera erfassen kann.
