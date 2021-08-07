---
title: 'HoloLens (1. Generation) und Azure 312: Botintegration'
description: In diesem Kurs erfahren Sie, wie Sie einen Bot mithilfe von Microsoft Bot Framework v4 erstellen und bereitstellen und mit ihm in einer Mixed Reality-Anwendung kommunizieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Computer Vision, HoloLens, immersive, vr, Microsoft Bot Framework v4, Web-App-Bot, Bot Framework, Microsoft Bot, Windows 10, Visual Studio
ms.openlocfilehash: 61a39806c2b434cb85d39a9b208ea8659ec8cbc301d8955ee1330bda4149f0db
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189810"
---
# <a name="hololens-1st-gen-and-azure-312-bot-integration"></a>HoloLens (1. Generation) und Azure 312: Botintegration

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie Sie für die entwicklung HoloLens 2.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

In diesem Kurs erfahren Sie, wie Sie einen Bot mithilfe von Microsoft Bot Framework V4 erstellen und bereitstellen und über eine Windows Mixed Reality kommunizieren. 

![](images/AzureLabs-Lab312-00.png)

Bei **Microsoft Bot Framework V4** handelt es sich um eine Reihe von APIs, mit deren Hilfe Entwickler die Tools zum Erstellen einer erweiterbaren und skalierbaren Botanwendung bereitstellen können. Weitere Informationen finden Sie auf der [Microsoft Bot Framework-Seite oder](https://dev.botframework.com/) im [V4-Git-Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).

Nach Abschluss dieses Kurses haben Sie eine Windows Mixed Reality erstellt, die Folgendes tun kann:

1. Verwenden Sie eine **Tippbewegung,** um den Bot zu starten, der auf die Stimme der Benutzer lausiert.
2. Wenn der Benutzer etwas gesagt hat, versucht der Bot, eine Antwort zu geben.
3. Zeigen Sie die Antwort der Bots als Text in der Unity-Szene an, der in der Nähe des Bots positioniert ist.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. Dieser Kurs soll Ihnen beibringen, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das Wissen aus diesem Kurs zu nutzen, um Ihre Mixed Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 312: Bot-Integration</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während sich dieser Kurs hauptsächlich auf HoloLens konzentriert, können Sie das, was Sie in diesem Kurs lernen, auch auf immersive Headsets (VR) Windows Mixed Reality anwenden. Da immersive Headsets (VR) keine zugänglichen Kameras haben, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist. Im Verlauf des Kurses finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise vornehmen müssen, um immersive Headsets (VR) zu unterstützen.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial ist für Entwickler konzipiert, die über grundlegende Erfahrung mit Unity und C# verfügen. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Juli 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, [](../../install-the-tools.md) wie im Artikel Installieren der Tools aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit dem übereinstimmen, was Sie in neuerer Software finden, als unten aufgeführt.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC, [der mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Entwicklung immersiver Headsets (VR) kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Entwicklermodus](../../install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality immersives Headset (VR)](../../../discover/immersive-headset-hardware-details.md) oder [ein](/hololens/hololens1-hardware) Microsoft HoloLens mit aktivierten Entwicklermodus
- Internetzugriff für Azure und für den Azure-Botabruf. Weitere Informationen finden Sie [unter diesem Link.](https://dev.botframework.com/)

### <a name="before-you-start"></a>Vorbereitung

1.  Um Probleme beim Erstellen dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stamm- oder Near-Root-Ordner zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).
2.  Einrichten und Testen Ihrer HoloLens. Wenn Sie Unterstützung beim Einrichten Ihrer HoloLens benötigen, lesen Sie den Artikel HoloLens [Setup.](/hololens/hololens-setup) 
3.  Es ist eine gute Idee, die Kalibrierung und Sensoroptimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen HoloLens-App beginnen (manchmal kann es helfen, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel HoloLens Kalibrierung.](/hololens/hololens-calibration#hololens-2)

Hilfe zur Sensoroptimierung finden Sie unter diesem [Link zum Artikel HoloLens Sensoroptimierung.](/hololens/hololens-updates)

## <a name="chapter-1--create-the-bot-application"></a>Kapitel 1: Erstellen der Botanwendung

Der erste Schritt besteht im Erstellen Ihres Bots als lokale ASP.Net Core-Webanwendung. Nachdem Sie es abgeschlossen und getestet haben, veröffentlichen Sie es im Azure-Portal.

1.  Öffnen Sie Visual Studio. Erstellen Sie ein neues Projekt, wählen Sie **ASP NET Core-Webanwendung** als Projekttyp aus (sie finden es im Unterabschnitt .NET Core), und nennen Sie **es MyBot**. Klicken Sie auf **OK**.

2.  Wählen Sie im angezeigten Fenster die Option **Leer aus.** Stellen Sie außerdem sicher, dass das Ziel auf **ASP NET Core 2.0** und die -Authentifizierung auf **Keine Authentifizierung festgelegt ist.** Klicken Sie auf **OK**.  

    ![Erstellen der Botanwendung](images/AzureLabs-Lab312-01.png)

3.  Die Projektmappe wird jetzt geöffnet. Klicken Sie im Projektmappen-Mybot mit der rechten **Maustaste** auf Projektmappen-Explorer klicken Sie auf Manage NuGet Packages for Solution (Pakete für  **Projektmappe verwalten).** 

    ![Erstellen der Botanwendung](images/AzureLabs-Lab312-02.png)

4.  Suchen Sie **auf der** Registerkarte Durchsuchen nach **Microsoft.Bot.Builder.Integration.AspNet.Core** (stellen Sie sicher, dass Vorabversionen **enthalten** überprüft ist). Wählen Sie die Paketversion **4.0.1-preview aus,** und aktivieren Sie die Projektfelder. Klicken Sie dann auf **Installieren.** Sie haben nun die Bibliotheken installiert, die für das Bot Framework **v4 erforderlich sind.** Schließen Sie die NuGet Seite.

    ![Erstellen der Botanwendung](images/AzureLabs-Lab312-03.png)

5.  Klicken Sie mit der rechten *Maustaste* auf Project , **MyBot,** im Projektmappen-Explorer **und** klicken Sie **auf** **|** **Klasse hinzufügen.**

    ![Erstellen der Botanwendung](images/AzureLabs-Lab312-04.png)

6.  Nennen Sie die **Klasse MyBot,** und klicken Sie **auf Hinzufügen.**

    ![Erstellen der Botanwendung](images/AzureLabs-Lab312-05.png)

7.  Wiederholen Sie den vorherigen Punkt, um eine weitere Klasse mit dem Namen **ConversationContext zu erstellen.** 

8.  Klicken Sie mit der rechten Maustaste auf **wwwroot** im **Projektmappen-Explorer** und klicken Sie **auf Neues** **|** **Element hinzufügen.** Wählen Sie  **HTML-Seite** aus (sie finden sie im Unterabschnitt Web). Nennen Sie die **Dateidefault.html**. Klicken Sie auf **Hinzufügen**.

    ![Erstellen der Botanwendung](images/AzureLabs-Lab312-06.png)

9.  Die Liste der Klassen/Objekte im Projektmappen-Explorer **sollte** wie in der folgenden Abbildung aussehen.

    ![Erstellen der Botanwendung](images/AzureLabs-Lab312-07.png)

10. Doppelklicken Sie auf die **ConversationContext-Klasse.** Diese Klasse ist für das Halten der Variablen zuständig, die vom Bot verwendet werden, um den Kontext der Konversation zu verwalten. Diese Konversationskontextwerte werden in einer Instanz dieser Klasse verwaltet, da jede Instanz der **MyBot-Klasse** jedes Mal aktualisiert wird, wenn eine Aktivität empfangen wird. Fügen Sie der -Klasse den folgenden Code hinzu:

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. Doppelklicken Sie auf die **MyBot-Klasse.** Diese Klasse hosten die Handler, die von jeder eingehenden Aktivität des Kunden aufgerufen werden. In dieser Klasse fügen Sie den Code hinzu, der zum Erstellen der Konversation zwischen dem Bot und dem Kunden verwendet wird. Wie bereits erwähnt, wird eine Instanz dieser Klasse jedes Mal initialisiert, wenn eine Aktivität empfangen wird. Fügen Sie dieser Klasse den folgenden Code hinzu:

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. Doppelklicken Sie auf die **Startup-Klasse.** Diese Klasse initialisiert den Bot. Fügen Sie der -Klasse den folgenden Code hinzu:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. Öffnen Sie die Program-Klassendatei, und vergewissern Sie sich, dass der code in ihr mit dem folgenden identisch ist: 

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. Denken Sie daran, Ihre Änderungen zu speichern. Wechseln Sie dazu in der Symbolleiste am oberen Ende des  >  Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Kapitel 2: Erstellen der Azure Bot Service

Nachdem Sie den Code für Ihren Bot erstellt haben, müssen Sie ihn in einer Instanz des *Web-App-Botdiensts* im Azure-Portal veröffentlichen. In diesem Kapitel erfahren Sie, wie Sie die Bot Service in Azure erstellen und konfigurieren und dann Ihren Code dort veröffentlichen.

1.  Melden Sie sich zunächst beim Azure-Portal an ( https://portal.azure.com) . 

    1. Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durch verwenden, bitten Sie Ihren Dozenten oder einen der Proktoren um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Klicken Sie nach der Anmeldung  in der linken oberen Ecke auf Ressource erstellen, suchen Sie nach *Web-App-Bot,* und geben Sie **ein.**

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-08.png)
 
3.  Die neue Seite enthält eine Beschreibung des *Web-App-Botdiensts.* Wählen Sie unten links auf dieser Seite die Schaltfläche **Erstellen** aus, um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-09.png)
 
4.  Nachdem Sie auf Erstellen geklickt **haben:**

    1. Fügen Sie den gewünschten **Namen für** diese Dienstinstanz ein.
    2. Wählen Sie ein **Abonnement** aus.
    3. Wählen Sie eine **Ressourcengruppe aus,** oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Kurse), unter einer gemeinsamen Ressourcengruppe zu halten.

        > Wenn Sie mehr über Azure-Ressourcengruppen erfahren möchten, folgen [Sie diesem Link.](/azure/azure-resource-manager/resource-group-portal)

    4. Bestimmen Sie den Standort für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.
    5. Wählen Sie **den für** Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen *Web-App-Botdienst* erstellen, sollte ihnen ein Free-Tarif (mit dem Namen F0) zur Verfügung stehen.
    6. **Der App-Name** kann einfach mit dem *Botnamen identisch bleiben.* 
    7. Belasse *die Botvorlage* **als Basic (C#)**.
    8. *App Service-Plan/Standort* sollte für Ihr Konto automatisch ausgefüllt worden sein.
    9. Legen Sie **die Azure Storage** fest, die Sie zum Hosten Ihres Bots verwenden möchten. Wenn Sie noch keines haben, können Sie es hier erstellen.
    10. Sie müssen auch bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.
    11. Klicken Sie auf „Erstellen“.
 
        ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-10.png)

5.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-11.png) 
 
7.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen. 

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-12.png)
 
8. Klicken Sie in **der Benachrichtigung auf die** Schaltfläche Zu Ressource wechseln, um Ihre neue Dienstinstanz zu untersuchen. Sie werden zu Ihrer neuen Azure-Dienstinstanz weitergenommen. 

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-13.png)
 
9.  An diesem Punkt müssen Sie  ein Feature namens Direct Line einrichten, damit Ihre Clientanwendung mit diesem Client kommunizieren Bot Service. Klicken Sie **auf Kanäle** und dann im Abschnitt **Ausgewählte** Kanal hinzufügen auf Configure Direct Line channel (Konfigurieren **Direct Line Kanal).**

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-14.png)

10. Auf dieser Seite finden Sie die geheimen **Schlüssel,** mit denen sich Ihre Client-App beim Bot authentifizieren kann. Klicken Sie auf **die Schaltfläche** Anzeigen, und erstellen Sie eine Kopie eines der angezeigten Schlüssel, da Sie diese später in Ihrem Projekt benötigen. 

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Kapitel 3: Veröffentlichen des Bots in der Azure-Web-App-Bot Service

Nachdem Ihr Dienst nun bereit ist, müssen Sie Ihren bot-Code, den Sie zuvor erstellt haben, in Ihrer neu erstellten Web-App Bot Service.

> [!NOTE] 
> Sie müssen Ihren Bot jedes Mal im Azure-Dienst veröffentlichen, wenn Sie Änderungen an bot solution/code vornehmen.

1.  Wechseln Sie zurück zu Ihrer Visual Studio, die Sie zuvor erstellt haben. 
2.  Klicken Sie mit der rechten Maustaste auf Ihr **MyBot-Projekt,** klicken Sie im Projektmappen-Explorer **,** und klicken Sie dann **auf Veröffentlichen.**

    ![Veröffentlichen des Bots in der Azure-Web-App-Bot Service](images/AzureLabs-Lab312-16.png)

3.  Klicken Sie *auf* der Seite Veröffentlichungsziel auswählen auf **App Service** und dann auf Vorhandene auswählen. Klicken Sie abschließend  auf Profil erstellen **.** (Wenn dies nicht sichtbar ist, müssen Sie möglicherweise auf den Dropdownpfeil neben der Schaltfläche Veröffentlichen klicken.)

    ![Veröffentlichen des Bots in der Azure-Web-App-Bot Service](images/AzureLabs-Lab312-17.png)

4. Wenn Sie noch nicht bei Ihrem Microsoft-Konto angemeldet sind, müssen Sie dies hier tun.
5. Auf der **Seite** Veröffentlichen müssen Sie dasselbe Abonnement festlegen, das Sie für die Erstellung des *Web-App-Botdiensts* verwendet haben.  Legen Sie dann die **Ansicht** als **Ressourcengruppe fest,** und wählen Sie in der Dropdownordnerstruktur die Ressourcengruppe aus, die **Sie** zuvor erstellt haben. Klicken Sie auf **OK**. 

    ![Veröffentlichen des Bots in der Azure-Web-App-Bot Service](images/AzureLabs-Lab312-18.png)

6.  Klicken Sie nun auf die **Schaltfläche Veröffentlichen,** und warten Sie, bis der Bot veröffentlicht wurde (es kann einige Minuten dauern).

    ![Veröffentlichen des Bots in der Azure-Web-App-Bot Service](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Kapitel 4: Einrichten des Unity-Projekts

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity,* und klicken Sie **auf Neu.** 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-20.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. Fügen **Sie HoloLens Bot ein.** Stellen Sie sicher, dass die Projektvorlage auf **3D festgelegt ist.** Legen Sie **den Speicherort** auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass die Nähe zu Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-21.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio.** Wechseln Sie **zu > Bearbeiten,** und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern **Sie den editor für externe** **Skripts in Visual Studio 2017**. Schließen Sie das **Fenster Einstellungen.**

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-22.png)

4.  Wechseln Sie als Nächstes zu **Datei > Build Einstellungen,** wählen Sie **Universelle Windows-Plattform** aus, und klicken Sie dann auf die Schaltfläche Plattform wechseln, um Ihre Auswahl anzuwenden. 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-23.png)

5.  Vergewissern Sie **sich, dass > Datei Einstellungen** erstellen, und stellen Sie Sicher, dass:

    1.  **Das Zielgerät** ist **auf** HoloLens

        > Legen Sie für die immersiven Headsets **Zielgerät auf** *Beliebiges Gerät fest.*

    2.  **Buildtyp** ist auf **D3D festgelegt**

    3.  **SDK** ist auf **Latest installed (Neueste installiert) festgelegt.**

    4.  **Visual Studio version** ist auf **Latest installed (Neueste installiert) festgelegt.**

    5.  **Erstellen und Ausführen** ist auf Lokaler **Computer festgelegt.**

    6.  Speichern Sie die Szene, und fügen Sie sie dem Build hinzu. 

        1. Wählen Sie hierzu Geöffnete Szenen **hinzufügen aus.** Ein Speicherfenster wird angezeigt.
        
            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-24.png)

        2. Erstellen Sie einen neuen Ordner für diesen und jede  zukünftige Szene, und wählen Sie dann die Schaltfläche Neuer Ordner aus, um einen neuen Ordner zu erstellen, und nennen Sie **ihn Scenes**.

             ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-25.png)

        3. Öffnen Sie den neu erstellten **Ordner Scenes,** und geben Sie dann im Feld Dateiname *:* Text **botScene** ein, und klicken Sie dann **auf Speichern.**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-26.png)

    7. Die restlichen Einstellungen in **Build Einstellungen** sollten vorerde als Standardeinstellung be übrig bleiben.

6. Klicken Sie *im Fenster Build Einstellungen* auf die Schaltfläche Player **Einstellungen,** um den entsprechenden Bereich in dem Bereich zu öffnen, in dem sich der *Inspektor* befindet. 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-27.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Führen Sie **auf Einstellungen** Registerkarte Andere Optionen aus:

        1. **Die Skriptlaufzeitversion** sollte **experimentell sein (NET 4.6-Entsprechung).** Wenn Sie dies ändern, ist ein Neustart des Editors erforderlich.
        2. **Das Skript-Back-End** sollte **.NET sein.**
        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6 sein.**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-28.png)
      
    2. Aktivieren Sie **auf Einstellungen** Registerkarte Publishing Einstellungen unter **Capabilities (Funktionen)** die folgenden Optionen:

        - **InternetClient**
        - **Mikrofon**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-29.png)

    3. Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (unter Publish **Einstellungen)** **(Virtual Reality** unterstützt), und stellen Sie sicher, dass das Windows Mixed Reality **SDK** hinzugefügt wird.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-30.png)

8.  Zurück in *Build Einstellungen* _Unity C#-Projekte_ ist nicht mehr ausgegraut. aktivieren Sie das Kontrollkästchen daneben. 
9.  Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).
10. Speichern Sie Ihre Szene und Ihr Projekt (**FILE > SAVE SCENE/FILE > SAVE PROJECT**).


## <a name="chapter-5--camera-setup"></a>Kapitel 5– Kameraeinrichtung

> [!IMPORTANT]
> Wenn Sie die *Unity-Komponente* Einrichten dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie diese [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)herunterladen, als benutzerdefiniertes Paket in Ihr Projekt importieren und dann mit Kapitel [7](#chapter-8--create-the-botobjects-class)fortfahren. [](https://docs.unity3d.com/Manual/AssetPackages.html)

1.  Wählen Sie *im Bereich Hierarchie* die **Hauptkamera aus.** 
2.  Nach der Auswahl können Sie alle Komponenten  der Hauptkamera im Inspektorbereich *sehen.*

    1. Das **Camera-Objekt** muss den Namen **Hauptkamera haben** (beachten Sie die Schreibweise).
    2. Das Main Camera **Tag** muss auf **MainCamera** festgelegt werden (beachten Sie die Schreibweise).
    3. Stellen Sie **sicher, dass die Transformationsposition** auf **0, 0, 0 festgelegt ist.**
    4. Legen **Sie Clear Flags auf** **Volltonfarbe fest.**
    5. Legen Sie **die Hintergrundfarbe** der Kamerakomponente auf **Schwarz, Alpha 0 (Hexadezimalcode: #00000000) fest.**

    ![Kameraeinrichtung](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Kapitel 6 : Importieren der Newtonsoft-Bibliothek

Um Sie beim Deserialisieren und Serialisieren von empfangenen und an die Bot Service müssen Sie die **Newtonsoft-Bibliothek** herunterladen. Eine kompatible Version, [die bereits mit der richtigen Unity-Ordnerstruktur organisiert ist, finden Sie hier.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage) 

Um die Newtonsoft-Bibliothek in Ihr Projekt zu importieren, verwenden Sie das Unity-Paket, das in diesem Kurs enthalten ist.

1.  Fügen Sie *unitypackage mithilfe der* Menüoption Assets Import Package Custom Package **(Benutzerdefiniertes** Paket importieren) zu Unity  >    >   hinzu.

    ![Importieren der Newtonsoft-Bibliothek](images/AzureLabs-Lab312-34.png)

2.  Vergewissern Sie sich im angezeigten Feld **Unity-Paket** importieren, dass alles unter (und einschließlich) **Plug-Ins** ausgewählt ist.

    ![Importieren der Newtonsoft-Bibliothek](images/AzureLabs-Lab312-35.png)

3.  Klicken Sie auf **die Schaltfläche** Importieren, um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie in der  Projektansicht unter Plug-Ins zum Ordner **Newtonsoft,** und wählen Sie das Newtonsoft-Plug-In aus.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Vergewissern Sie sich bei ausgewähltem Newtonsoft-Plug-In, dass Any **Platform** (Beliebige Plattform) deaktiviert **ist,** stellen Sie sicher, dass **auch WSAPlayer** deaktiviert **ist,** und klicken Sie dann **auf Anwenden.** Dadurch wird lediglich bestätigt, dass die Dateien ordnungsgemäß konfiguriert sind.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Durch das Markieren dieser Plug-Ins werden sie so konfiguriert, dass sie nur im Unity-Editor verwendet werden. Es gibt einen anderen Satz von ihnen im WSA-Ordner, der verwendet wird, nachdem das Projekt aus Unity exportiert wurde.

6.  Als Nächstes müssen Sie den **Ordner WSA** im **Ordner Newtonsoft** öffnen. Sie sehen eine Kopie derselben Datei, die Sie gerade konfiguriert haben. Wählen Sie die Datei aus, und stellen Sie dann im Inspektor sicher, dass
    -   **Alle Plattformen** **sind deaktiviert.** 
    -   **Nur** **WSAPlayer** **ist überprüft.**
    -   **Nicht überprüfter** **Prozess**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Kapitel 7: Erstellen des BotTags

1.  Erstellen Sie ein neues **Tag-Objekt** mit dem **Namen BotTag.** Wählen Sie die Hauptkamera in der Szene aus. Klicken Sie im Inspektorbereich auf das Dropdownmenü Tag. Klicken Sie auf **Tag hinzufügen.**

    ![Kameraeinrichtung](images/AzureLabs-Lab312-32.png)
 
2.  Klicken Sie auf das **+** Symbol. Nennen Sie das **neue Tag** **BotTag,** speichern *Sie*.

    ![Kameraeinrichtung](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **Wenden Sie** **botTag nicht auf** die Hauptkamera an. Wenn Sie dies versehentlich getan haben, stellen Sie sicher, dass Sie das Tag Hauptkamera wieder in *MainCamera ändern.*

## <a name="chapter-8--create-the-botobjects-class"></a>Kapitel 8: Erstellen der BotObjects-Klasse

Das erste Skript, das Sie erstellen müssen, ist die **BotObjects-Klasse,** bei der es sich um eine leere Klasse handelt, die erstellt wurde, sodass eine Reihe anderer Klassenobjekte innerhalb desselben Skripts gespeichert und von anderen Skripts in der Szene aufgerufen werden kann.

Die Erstellung dieser Klasse ist eine rein architektonische Wahl. Diese Objekte könnten stattdessen im Botskript gehostet werden, das Sie später in diesem Kurs erstellen.

So erstellen Sie diese Klasse: 

1.  Klicken Sie mit der rechten Maustaste in *Project Bereich*, und klicken Sie dann auf **> Ordner**. Nennen Sie den Ordner **Scripts**. 

    ![Erstellen Sie den Ordner skripts.](images/AzureLabs-Lab312-36.png)

2.  Doppelklicken Sie auf den Ordner **Skripts,** um ihn zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste, und wählen Sie **Create > C# Script (C#-Skript erstellen) aus.** Nennen Sie das **Skript BotObjects**. 

3.  Doppelklicken Sie auf das neue **BotObjects-Skript,** um es mit **Visual Studio.**

4.  Löschen Sie den Inhalt des Skripts, und ersetzen Sie ihn durch den folgenden Code:

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  Achten Sie darauf, dass Sie Ihre Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity zurückkehren.*

## <a name="chapter-9--create-the-gazeinput-class"></a>Kapitel 9: Erstellen der GazeInput-Klasse

Die nächste Klasse, die Sie erstellen, ist die **GazeInput-Klasse.** Diese Klasse ist für Folgendes verantwortlich:

- Erstellen eines Cursors, der den *Anving des* Players repräsentiert.
- Erkennen von Objekten, die durch das Anvieren des Players getroffen werden, und Halten eines Verweises auf erkannte Objekte.

So erstellen Sie diese Klasse: 

1.  Wechseln Sie zum **Ordner Skripts,** den Sie zuvor erstellt haben. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner Create **> C#-Skript.** Rufen Sie das Skript **GazeInput auf.** 
3.  Doppelklicken Sie auf das neue **GazeInput-Skript,** um es **mit** Visual Studio.
4.  Fügen Sie die folgende Zeile direkt über dem Klassennamen ein:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Fügen Sie dann die folgenden Variablen in der **GazeInput-Klasse** über der **Start()-Methode** hinzu:

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  Code für **die Start()-Methode** sollte hinzugefügt werden. Dies wird aufgerufen, wenn die -Klasse initialisiert wird:

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Implementieren Sie eine Methode, die den Anvistikcursor instanziiert und einsetze: 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  Implementieren Sie die Methoden, die raycast von der Hauptkamera einrichten und das aktuelle Fokusobjekt nachverfolgen.

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  Achten Sie darauf, dass Sie Ihre Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity zurückkehren.*

## <a name="chapter-10--create-the-bot-class"></a>Kapitel 10 – Erstellen der Bot-Klasse

Das Skript, das Sie jetzt erstellen möchten, heißt **Bot.** Dies ist die Kernklasse Ihrer Anwendung. Sie speichert: 

- Anmeldeinformationen für Ihren Web-App-Bot
- Die Methode, die die Benutzerstimmenbefehle sammelt
- Die Methode, die zum Initiieren von Konversationen mit Ihrem Web-App-Bot erforderlich ist 
- Die Methode, die zum Senden von Nachrichten an Ihren Web-App-Bot erforderlich ist 

Um Nachrichten an den Bot Service zu senden, erstellt die **SendMessageToBot()-Coroutine** eine Aktivität, bei der es sich um ein Objekt handelt, das vom Bot Framework als vom Benutzer gesendete Daten erkannt wird. 
 
So erstellen Sie diese Klasse: 

1. Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen. 
2. Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken Sie **> C#-Skript erstellen.** Nennen Sie das **Skript Bot**. 
3. Doppelklicken Sie auf das neue Skript, um es mit dem Visual Studio.
4. Aktualisieren Sie die Namespaces am Anfang der **Bot-Klasse** so, dass sie mit den folgenden identisch sind:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. Fügen Sie **in der Bot-Klasse** die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > Stellen Sie sicher, dass Sie Ihren **geheimen Botschlüssel** in die **Variable botSecret** einfügen. Sie haben ihren geheimen **Botschlüssel** zu Beginn dieses Kurses notiert, in **[Kapitel 2](#chapter-2---create-the-azure-bot-service), Schritt 10.**

7. Code für **"Awake()"** **und "Start()"** muss nun hinzugefügt werden. 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. Fügen Sie die beiden Handler hinzu, die von den Sprachbibliotheken aufgerufen werden, wenn die Spracherfassung beginnt und endet. Der *DictationRecognizer* beendet automatisch die Erfassung der Benutzerstimme, wenn der Benutzer nicht mehr spricht.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. Der folgende Handler erfasst das Ergebnis der Benutzerstimmeneingabe und ruft die Coroutine auf, die für das Senden der Nachricht an die Web-App-Bot Service.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. Die folgende Coroutine wird aufgerufen, um eine Konversation mit dem Bot zu beginnen. Sie werden feststellen, dass nach Abschluss des Konversationsaufrufs **SendMessageToCoroutine()** aufgerufen wird, indem eine Reihe von Parametern übergeben wird, die die aktivität, die an den Bot Service gesendet werden soll, als leere Nachricht festlegen. Dies erfolgt, um den Benutzer auf Bot Service, den Dialog zu initiieren.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. Die folgende Coroutine wird aufgerufen, um die Aktivität zu erstellen, die an die Bot Service. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. Die folgende Coroutine wird aufgerufen, um nach dem Senden einer Aktivität an die Bot Service. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. Die letzte Methode, die dieser Klasse hinzugefügt werden soll, ist erforderlich, um die Meldung in der Szene anzuzeigen:

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > Möglicherweise wird in der Unity-Editor-Konsole ein Fehler angezeigt, dass die **SceneOrganiser-Klasse fehlt.** Ignorieren Sie diese Meldung, da Sie diese Klasse später in diesem Tutorial erstellen.

14.  Stellen Sie sicher, dass Sie Ihre Änderungen *in* Visual Studio speichern, bevor Sie zu *Unity zurückkehren.*

## <a name="chapter-11--create-the-interactions-class"></a>Kapitel 11 – Erstellen der Interactions-Klasse

Die Klasse, die Sie jetzt erstellen möchten, heißt **Interaktionen.** Diese Klasse wird verwendet, um zu erkennen, HoloLens Benutzer auf Eingabe tippt. 

Wenn der Benutzer beim Sehen des *Botobjekts* in der Szene tippt und der Bot bereit  ist, auf Spracheingaben zu lauschen, ändert das Bot-Objekt die Farbe in Rot und beginnt mit dem Lauschen auf Spracheingaben. 

Diese Klasse erbt von der **GazeInput-Klasse** und kann daher auf die **Start()-Methode** und Variablen dieser Klasse verweisen, die durch die Verwendung der Basisklasse **bezeichnet werden.** 
 
So erstellen Sie diese Klasse:

1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken Sie **> C#-Skript erstellen.** Nennen Sie das Skript **Interaktionen**. 
3.  Doppelklicken Sie auf das neue Skript, um es mit dem Visual Studio.
4.  Aktualisieren Sie die Namespaces und die Klassenvererbung so, dass sie am Anfang der **Interactions-Klasse** mit den folgenden identisch sind:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  Fügen Sie **in der Interactions-Klasse** die folgende Variable hinzu:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Fügen Sie dann die **Start()-Methode** hinzu:

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  Fügen Sie den Handler hinzu, der ausgelöst wird, wenn der Benutzer die Tippbewegung vor der HoloLens ausführt.

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. Stellen Sie sicher, dass Sie Ihre Änderungen *in* Visual Studio speichern, bevor Sie zu *Unity zurückkehren.*

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Kapitel 12 – Erstellen der SceneOrganiser-Klasse

Die letzte klasse, die in diesem Lab erforderlich ist, heißt **SceneOrganiser.** Mit dieser Klasse wird die Szene programmgesteuert eingerichtet, indem der Hauptkamera Komponenten und Skripts hinzugefügt und die entsprechenden Objekte in der Szene erstellt werden.
 
So erstellen Sie diese Klasse:

1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken Sie **> C#-Skript erstellen.** Nennen Sie das **Skript SceneOrganiser**. 
3.  Doppelklicken Sie auf das neue Skript, um es mit dem Visual Studio.
4.  Fügen Sie **in der SceneOrganiser-Klasse** die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  Fügen Sie dann die **Methoden "Awake()"** **und "Start()"** hinzu:

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  Fügen Sie die folgende Methode hinzu, die für das Erstellen des Bot-Objekts in der Szene und das Einrichten der Parameter und Komponenten zuständig ist:

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  Fügen Sie die folgende Methode hinzu, die für das Erstellen des UI-Objekts in der Szene verantwortlich ist und die Antworten des Bots darstellt:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  Stellen Sie sicher, dass Sie Ihre Änderungen *in* Visual Studio speichern, bevor Sie zu *Unity zurückkehren.*
9.  Ziehen Sie im Unity-Editor das **Skript SceneOrganiser** aus dem Ordner Skripts auf die Hauptkamera. Die Komponente Szenenszenen sollte nun auf dem Hauptkameraobjekt angezeigt werden, wie in der folgenden Abbildung dargestellt.

    ![Erstellen des Azure Bot Service](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Kapitel 13 – Vor dem Erstellen

Um ihre Anwendung gründlich zu testen, müssen Sie sie auf die HoloLens.
Bevor Sie dies tun, stellen Sie Sicher, dass:

-   Alle in Kapitel [**4 erwähnten**](#chapter-4--set-up-the-unity-project) Einstellungen sind ordnungsgemäß festgelegt. 
-   Das Skript **SceneOrganiser** ist an das **Hauptkameraobjekt** angefügt. 
-   Stellen Sie **in der Bot-Klasse** sicher, dass Sie Ihren geheimen **Botschlüssel** in die **Variable botSecret eingefügt** haben.

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Kapitel 14 : Erstellen und Sideloaden in HoloLens

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, wurde abgeschlossen, daher ist es an der Zeit, es aus Unity zu erstellen.

1.  Navigieren Sie **zu Build Einstellungen**, Datei > Build **Einstellungen...**.
2.  Klicken Sie **im Fenster Build Einstellungen** auf **Erstellen.**

    ![Erstellen der App aus Unity](images/AzureLabs-Lab312-38.png)

3.  Wenn nicht bereits, aktivieren Sie **Unity C#-Projekte**.
4.  Klicken Sie auf **Erstellen**. Unity startet ein **Datei-Explorer-Fenster,** in dem Sie einen Ordner erstellen und dann einen Ordner auswählen müssen, in dem die App erstellt werden soll. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn **App**. Klicken Sie dann bei ausgewähltem **App-Ordner** **auf Ordner auswählen.** 
5.  Unity beginnt damit, Ihr Projekt im Ordner **App zu** erstellen. 
6.  Sobald Unity die Erstellung abgeschlossen hat (dies kann einige Zeit dauern), wird ein **Datei-Explorer-Fenster** am Speicherort Ihres Buildfensters geöffnet (überprüfen Sie Ihre Taskleiste, da sie möglicherweise nicht immer über Ihren Fenstern angezeigt wird, sondern Sie über das Addition eines neuen Fensters benachrichtigt).

## <a name="chapter-15--deploy-to-hololens"></a>Kapitel 15 – Bereitstellen in HoloLens

So stellen Sie auf HoloLens:

1.  Sie benötigen die IP-Adresse Ihres HoloLens (für Remote Deploy) und um sicherzustellen, dass sich HoloLens im **Entwicklermodus befindet.** Aufgabe:

    1. Öffnen Sie die HoloLens, während Sie **Einstellungen.**
    2. Wechseln Sie **zu Netzwerk & Internet > Wi-Fi > Erweiterte Optionen.**
    3. Notieren Sie sich **die IPv4-Adresse.**
    4. Navigieren Sie als Nächstes zurück zu **Einstellungen**, und navigieren Sie dann zu **Update & Security > For Developers .)** 
    5. Legen Sie entwicklermodus ein fest.

2.  Navigieren Sie zu Ihrem neuen Unity-Build (dem **Ordner App),** und öffnen Sie die Projektmappendatei mit **Visual Studio.**
3.  Wählen Sie in **der Projektmappenkonfiguration** **Debuggen aus.**
4.  Wählen Sie **auf der Projektmappenplattform** **x86**, **Remotecomputer aus.** 

    ![Stellen Sie die Lösung über Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie auf **Projektmappe bereitstellen,** um die Anwendung in Ihre HoloLens.
6.  Ihre App sollte jetzt in der Liste der installierten Apps auf Ihrer HoloLens angezeigt werden, die zum Start bereit sind!

    > [!NOTE]
    > Legen Sie zum Bereitstellen für immersive Headsets die  **Projektmappenplattform** auf *Lokaler* Computer und die Konfiguration auf *Debuggen* mit *x86* als Plattform **fest.** Stellen Sie dann auf dem lokalen Computer mithilfe des **Menüs Erstellen die** Option *Projektmappe bereitstellen aus.* 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Kapitel 16 – Verwenden der Anwendung auf HoloLens

- Nachdem Sie die Anwendung gestartet haben, sehen Sie den Bot als blaue Kugel vor Ihnen.

- Verwenden Sie **die Tippgeste,** während Sie sich an der Kugel befinden, um eine Konversation zu initiieren. 
 
- Warten Sie, bis die Konversation gestartet wird (die Benutzeroberfläche zeigt eine Meldung an, wenn sie eintritt). Sobald Sie die einführungsmeldung vom Bot erhalten haben, tippen Sie erneut auf den Bot, damit er rot wird und mit dem Lauschen auf Ihre Stimme beginnt. 

- Wenn Sie nicht mehr sprechen, sendet Ihre Anwendung Ihre Nachricht an den Bot, und Sie erhalten sofort eine Antwort, die auf der Benutzeroberfläche angezeigt wird. 

- Wiederholen Sie den Vorgang, um weitere Nachrichten an Ihren Bot zu senden (Sie müssen jedes Mal tippen, wenn Sie eine Nachricht senden möchten).

In dieser Konversation wird veranschaulicht, wie der Bot Informationen (Ihren Namen) beibehalten und gleichzeitig bekannte Informationen bereitstellen kann (z. B. die elemente, die vorbefüllt sind).

#### <a name="some-questions-to-ask-the-bot"></a>Einige Fragen, die dem Bot gestellt werden müssen:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>Ihre fertige Web-App-Botanwendung (v4)

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure-Web-App-Bot Microsoft Bot Framework v4 nutzt.

![Endgültiges Produkt](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Die Konversationsstruktur in diesem Lab ist sehr einfach. Verwenden Sie Microsoft LUIS, um Ihrem Bot Funktionen zum Verstehen natürlicher Sprache zu bieten.

### <a name="exercise-2"></a>Übung 2

Dieses Beispiel umfasst nicht das Beenden einer Konversation und das Neustarten einer neuen Konversation. Um das Botfeature vollständig zu machen, versuchen Sie, den Abschluss der Konversation zu implementieren.