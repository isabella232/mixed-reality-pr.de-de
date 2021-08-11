---
ms.openlocfilehash: d811df7f0dbd7c44a5135ed82c9061e19c1335e3e23dda6398562317f7ee8861
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198785"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

Wenn Sie über eine HoloLens Anwendung verfügen, wählen Sie ihre bevorzugte [Verteilungsoption](../distribute-overview.md#distribution-options) aus der folgenden Tabelle aus. Wenn Sie im Microsoft Store veröffentlichen, haben Sie die Möglichkeit, [In-App-Käufe](../in-app-purchases.md) hinzuzufügen, um Ihre Inhalte zu monetarisieren.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Wenn Sie mit einer immersiven Anwendung arbeiten, die auf ein Windows Mixed Reality Headset ausgerichtet ist, erstellen Sie einen 3D-App-Starter, und wählen Sie dann ihre bevorzugte [Verteilungsoption](../distribute-overview.md#distribution-options) aus der folgenden Tabelle aus. Wenn Sie im Microsoft Store veröffentlichen, haben Sie die Möglichkeit, [In-App-Käufe](../in-app-purchases.md) hinzuzufügen, um Ihre Inhalte zu monetarisieren.

### <a name="designing-3d-app-launchers-for-vr"></a>Entwerfen von 3D-App-Startern für VR 

3D-App-Starter werden als Objekte in der Windows Mixed Reality Home-Umgebung angezeigt, die angezeigt wird, wenn ein Benutzer ein immersives Headset anlegt. Diese Objekte können Sie nach Belieben erstellen und anpassen. Es wird jedoch empfohlen, mit unserem Artikel zur [Entwurfsanleitung](../3d-app-launcher-design-guidance.md) zu beginnen, um bewährte Entwurfsmethoden wie Skalierung, Typ, Farbauswahl, Texturierung und vor allem das Herausstellen in einer virtuellen Umgebung zu unterstützen.

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modellieren und Exportieren von 3D-App-Startmodellen

Sobald Sie die Idee für ihr 3D-App-Startfeld festgelegt haben, müssen Sie sicherstellen, dass es die Microsoft Store Anforderungen erfüllt, einschließlich Assetdateiformat, Dreiecksanzahl, Texturgrößen, Animationslänge und Ressourcenoptimierung. Dieser Prozess kann sehr technisch sein. Daher wird empfohlen, den Artikel [zur Erstellung des 3D-Modells](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) zu verwenden, um alle Kontrollkästchen zu aktivieren. Objekte, die diese Erstellungsspezifikation nicht erfüllen, werden im Windows Mixed Reality Home nicht gerendert.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Hinzufügen von 3D-App-Startern in Ihren Apps

Nachdem Sie sichergestellt haben, dass ihr 3D-App-Starter die Windows Mixed Reality Erstellungsrichtlinien erfüllt, kann es verwendet werden, um das Standardmäßige 2D-Starter für Ihre Anwendung in der Windows Mixed Reality Home-Umgebung außer Kraft zu setzen. Der Prozess zum Integrieren eines 3D-App-Starters in Ihre Anwendung hängt vom Typ der Anwendung ab, die Sie entwickeln:

* [UWP-Apps](../implementing-3d-app-launchers.md)
* [Win32-Apps](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>[Optional] Platzieren von 3D-Modellen im Windows Mixed Reality Home

Als zusätzlichen Bonus können Sie mit einigen 2D-Anwendungen 3D-Modelle direkt im Windows Mixed Reality Haus als Dekoration oder zur weiteren Untersuchung in vollständigem 3D platzieren. Mit dem Add Model-Protokoll können Sie ein 3D-Modell von Ihrer Website oder Anwendung an die Windows Mixed Reality-Startseite senden, wo es wie 3D-App-Startprogramme, 2D-Apps und Hologramme beibehalten wird. Sehen Sie [sich an, wie Sie 3D-Modelle im Windows Mixed Reality Home platzieren,](../enable-placement-of-3d-models-in-the-home.md) um weitere Details und Anweisungen zum Beleben Ihrer eigenen Apps zu erhalten.