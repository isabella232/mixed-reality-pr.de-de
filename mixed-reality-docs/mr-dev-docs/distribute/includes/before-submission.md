---
ms.openlocfilehash: c9ce068adc3b4b550ecaf1b1c106d9b12f363ac0
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443502"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

Wenn Sie über eine hololens-Anwendung verfügen, wählen Sie Ihre bevorzugte [Verteilungs Option](../distribute-overview.md#distribution-options) aus der folgenden Tabelle aus. Wenn Sie die Microsoft Store veröffentlichen, haben Sie die Möglichkeit, [in-App-Käufe](../in-app-purchases.md) hinzuzufügen, um Ihre Inhalte zu verdienen.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Wenn Sie mit einer immersiven Anwendung arbeiten, die ein Windows Mixed Reality-Headset als Ziel hat, erstellen Sie ein 3D-App-Startfeld, und wählen Sie dann Ihre bevorzugte [Verteilungs Option](../distribute-overview.md#distribution-options) aus der folgenden Tabelle aus. Wenn Sie die Microsoft Store veröffentlichen, haben Sie die Möglichkeit, [in-App-Käufe](../in-app-purchases.md) hinzuzufügen, um Ihre Inhalte zu verdienen.

### <a name="designing-3d-app-launchers-for-vr"></a>Entwerfen von 3D-App-launchern für VR 

3D-App-Launcher werden als Objekte in der Windows Mixed Reality-Start Umgebung angezeigt, die immer dann angezeigt wird, wenn ein Benutzer ein immersives Headset einfügt. Diese Objekte können Sie nach Belieben erstellen und anpassen. es wird jedoch empfohlen, dass Sie mit unserem [Entwurfs Leit Faden](../3d-app-launcher-design-guidance.md) Artikel beginnen, um den Einsatz guter Entwurfs Praktiken zu erreichen, einschließlich Skalierung, Typ, Farbauswahl, Texturierung und darüber, dass Sie sich in einer virtuellen Umgebung befinden.

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modellieren und Exportieren von 3D-App-launchern

Nachdem Sie die Idee für das 3D-App-Startfeld festgelegt haben, müssen Sie sicherstellen, dass Sie die Microsoft Store Anforderungen erfüllt, einschließlich des assetdateiformats, der Dreiecks Anzahl, der Größe der Animation und der assetoptimierung. Dieser Prozess kann sehr technisch sein. Daher wird empfohlen, den Artikel zur [3D-Modell Erstellung](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) zu verwenden, um alle Felder zu überprüfen. Assets, die diese Erstellungs Spezifikation nicht erfüllen, werden nicht in der Windows Mixed Reality-Startseite gerendert.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Hinzufügen von 3D-App-launchern in ihren apps

Nachdem Sie sichergestellt haben, dass das 3D-App-Start Programm den Windows Mixed Reality-Erstellungs Richtlinien entspricht, kann es verwendet werden, um das 2D-Standard Startfeld für Ihre Anwendung in der Windows Mixed Reality-Start Umgebung zu überschreiben Der Prozess für die Integration eines 3D-App-Start Programms in Ihre Anwendung hängt von der Art der Anwendung ab, die Sie entwickeln:

* [UWP-Apps](../implementing-3d-app-launchers.md)
* [Win32-Apps](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>Optionale Platzieren von 3D-Modellen in der Windows Mixed Reality-Startseite

Als zusätzlichen Bonus können Sie mit einigen 2D-Anwendungen 3D-Modelle direkt in den Windows Mixed Reality-Start als Dekorationen oder für eine weitere Prüfung in vollständiger 3D platzieren. Das Add Model-Protokoll ermöglicht Ihnen das Senden eines 3D-Modells von Ihrer Website oder Anwendung an das Windows Mixed Reality-Zuhause, wo es wie 3D-App-Launcher, 2D-apps und holograms persistent gespeichert wird. Sehen Sie sich an, [wie 3D-Modelle in der Windows Mixed Reality-Startseite platziert](../enable-placement-of-3d-models-in-the-home.md) werden, um weitere Details und Anweisungen zum Durchsuchen Ihrer eigenen apps zu erhalten.