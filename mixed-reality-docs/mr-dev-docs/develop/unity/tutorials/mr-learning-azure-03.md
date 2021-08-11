---
title: Integrieren von Azure-Custom Vision
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Custom Vision innerhalb einer HoloLens 2-Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Custom Vision, Azure Cognitive Services, Azure Cloud Services, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: e5914b99e83df0c8ed7bf5aa26f11bf5b224b64107a6ca8e05994bc6ee41147f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190464"
---
# <a name="3-integrating-azure-custom-vision"></a>3. Integrieren von Azure-Custom Vision

In diesem Tutorial erfahren Sie, wie Sie **Azure Custom Vision** verwenden. Sie laden einen Satz Fotos hoch, um sie einem *nachverfolgten Objekt* zuzuordnen. Laden Sie sie in den **Custom Vision**-Dienst hoch, und starten Sie den Trainingsvorgang. Anschließend verwenden Sie den Dienst, um das *nachverfolgte Objekt* zu erkennen, indem Sie Fotos aus dem Webcamfeed erfassen.

## <a name="objectives"></a>Ziele

* Grundlagen zu Azure Custom Vision
* Erfahren Sie, wie Sie die Szene einrichten, um Azure Custom Vision in diesem Projekt zu verwenden
* Erfahren Sie, wie Sie Uploads, Training und die Erkennung von Bildern integrieren

## <a name="understanding-azure-custom-vision"></a>Grundlegendes zu Azure Custom Vision

**Azure Custom Vision** ist Teil der **Cognitive Services**-Produktfamilie und wird zum Trainieren von Bildklassifizierern verwendet. Der Bildklassifizierer ist ein KI-Dienst, der das trainierte Modell verwendet, um entsprechende Tags anzuwenden. Diese Klassifizierungsfunktion wird von unserer Anwendung verwendet, um *nachverfolgte Objekte* zu erkennen.

Weitere Informationen zu [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).

## <a name="preparing-azure-custom-vision"></a>Vorbereiten von Azure-Custom Vision

Bevor Sie beginnen können, müssen Sie ein Custom Vision-Projekt erstellen. Am schnellsten geht dies über das Webportal.

Befolgen Sie dieses [Schnellstarttutorial](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) zum Einrichten Ihres Kontos und Projekts bis zum Abschnitt *Hochladen und Taggen von Bildern*.

> [!WARNING]
> Zum Trainieren eines Modells benötigen Sie mindestens zwei Tags und fünf Bilder pro Tag. Um diese Anwendung zu verwenden, sollten Sie mindestens ein Tag mit fünf Bildern erstellen, damit der Trainingsvorgang später nicht fehlschlägt.

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.

![Unity mit Projekt-Fenster, in dem der Pfad zum ObjectDetectionManager-Prefab angezeigt wird](images/mr-learning-azure/tutorial3-section4-step1-1.png)

Ziehen Sie dort das Prefab **ObjectDetectionManager** in die Hierarchie der Szene.

![Unity mit im Inspektor angezeigten Konfigurationsfeldern der ObjectDetectionManager (Skript)-Komponente](images/mr-learning-azure/tutorial3-section4-step1-2.png)

Suchen Sie im Hierarchiefenster nach dem **ObjectDetectionManager**-Objekt, und wählen Sie es aus.
Das Prefab **ObjectDetectionManager** enthält die Komponente **ObjectDetectionManager (Skript)** , und wie Sie im Inspektorfenster sehen können, hängt sie von Azure-Einstellungen und Projekteinstellungen ab.

## <a name="retrieving-azure-api-resource-credentials"></a>Abrufen von Azure-API-Ressourcenanmeldeinformationen

Die erforderlichen Anmeldeinformationen für die Einstellungen von **ObjectDetectionManager (Script)** können aus dem Azure-Portal und aus dem Custom Vision-Portal abgerufen werden.

### <a name="retrieving-azure-settings-credentials"></a>Abrufen der Anmeldeinformationen für Azure-Einstellungen

Suchen Sie nach der Custom Vision-Ressource vom Typ **Cognitive Services**, die Sie im Abschnitt *Vorbereiten der Szene* dieses Tutorials erstellt haben (wählen Sie den Namen der Custom Vision-Ressource aus, gefolgt von *-Prediction*). Klicken Sie dort auf *Overview* (Übersicht) oder *Keys and Endpoint* (Schlüssel und Endpunkt), um die erforderlichen Anmeldeinformationen abzurufen.

### <a name="retrieving-project-settings-credentials"></a>Abrufen der Anmeldeinformationen für Projekteinstellungen

Öffnen Sie das Projekt, das Sie für dieses Tutorial erstellt haben, im [Custom Vision](https://www.customvision.ai/projects)-Dashboard, und klicken Sie auf das Zahnradsymbol in der rechten oberen Ecke der Seite, um die Seite mit den Einstellungen zu öffnen. Hier finden Sie die erforderlichen Anmeldeinformationen im Abschnitt *Ressourcen* auf der rechten Seite.

Nachdem **ObjectDetectionManager (Script)** ordnungsgemäß eingerichtet wurde, suchen Sie in der Hierarchie der Szene nach dem **SceneController**-Objekt, und wählen Sie es aus.

![Unity mit im Inspektor angezeigten Konfigurationsfeldern der SceneController (Script)-Komponente](images/mr-learning-azure/tutorial3-section4-step1-3.png)

Sie sehen, dass das Feld *Object Detection Manager* (Objekterkennungs-Manager) in der **SceneController**-Komponente leer ist. Ziehen Sie **ObjectDetectionManager** aus der Hierarchie in dieses Feld, und speichern Sie die Szene.

![Unity mit konfigurierter SceneController-Skriptkomponente](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a>Aufnehmen und Hochladen von Bildern

Führen Sie die Szene aus, klicken Sie auf **Set Object** (Objekt festlegen), und geben Sie den Namen für eines der **nachverfolgten Objekte** ein, die Sie in der [vorherigen Lektion](mr-learning-azure-02.md) erstellt haben. Klicken Sie nun auf die Schaltfläche **Computer Vision** (Maschinelles Sehen), die Sie unten auf der **Objektkarte** finden.

Ein neues Fenster wird geöffnet, in dem Sie sechs Fotos aufnehmen müssen, um das Modell für die Bilderkennung zu trainieren. Klicken Sie auf die Schaltfläche **Camera** (Kamera), und führen Sie eine AirTap-Aktion aus, wenn Sie das Objekt ansehen, das Sie nachverfolgen möchten. Führen Sie diesen Vorgang sechs Mal aus.

> [!TIP]
> Um das Modelltraining zu verbessern, versuchen Sie, jedes Bild aus unterschiedlichen Winkeln und unter verschiedenen Beleuchtungsbedingungen aufzunehmen.

Wenn Sie über genügend Bilder verfügen, klicken Sie auf die Schaltfläche **Train** (Trainieren), um den Modelltrainingsprozess in der Cloud zu starten. Wenn Sie das Training aktivieren, werden alle Bilder hochgeladen, und das Training wird gestartet. Dies kann bis zu einer Minute oder auch länger dauern. Eine Meldung innerhalb des Menüs zeigt den aktuellen Status an, und sobald der Abschluss angezeigt wird, können Sie die Anwendung beenden.

> [!TIP]
> **ObjectDetectionManager (Script)** lädt die aufgenommenen Bilder direkt in den Custom Vision-Dienst hoch. Als Alternative akzeptiert die Custom Vision-API URLs zu den Bildern. Als Übung können Sie **ObjectDetectionManager (Script)** , ändern, um die Bilder stattdessen in einen Blobspeicher hochzuladen.

## <a name="detect-objects"></a>Erkennen von Objekten

Sie können das trainierte Modell nun testen, die Anwendung ausführen und im *Hauptmenü* auf **Search Object** (Objekt suchen) klicken und den Namen des betreffenden **nachverfolgten Objekts** eingeben. Die **Objektkarte** wird angezeigt. Klicken Sie auf die Schaltfläche **Custom Vision**. Hier beginnt **ObjectDetectionManager**, Bilder von der Kamera im Hintergrund zu erfassen, und der Status wird im Menü angezeigt. Richten Sie die Kamera auf das Objekt, mit dem Sie das Modell trainiert haben, und Sie sehen, dass das Objekt nach kurzer Zeit erkannt wird.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie mithilfe von Azure Custom Vision Bilder trainieren und den Klassifizierungsdienst verwenden können, um Bilder zu erkennen, die dem zugehörigen **nachverfolgten Objekt** entsprechen.

Im nächsten Tutorial erfahren Sie, wie Sie mithilfe von Azure Spatial Anchors ein *nachverfolgtes Objekt* mit einer Position in der physischen Welt verknüpfen und einen Pfeil anzeigen, der den Benutzer zurück zur verknüpften Position des nachverfolgten Objekts führt.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 4. Integrieren von Azure Spatial Anchors](mr-learning-azure-04.md)