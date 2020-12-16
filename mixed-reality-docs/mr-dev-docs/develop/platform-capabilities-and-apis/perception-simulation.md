---
title: Simulation des perceptions
description: Guide d’utilisation de la bibliothèque de simulation de perception pour automatiser une entrée simulée pour des applications immersifs
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, simulation, test
ms.openlocfilehash: 64028c3a1ad58cecfebc93aee325b73c3a6a649a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530400"
---
# <a name="perception-simulation"></a><span data-ttu-id="7d918-104">Simulation des perceptions</span><span class="sxs-lookup"><span data-stu-id="7d918-104">Perception simulation</span></span>

<span data-ttu-id="7d918-105">Voulez-vous créer un test automatisé pour votre application ?</span><span class="sxs-lookup"><span data-stu-id="7d918-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="7d918-106">Voulez-vous que vos tests vont au-delà des tests unitaires au niveau du composant et pour vraiment exercer votre application de bout en bout ?</span><span class="sxs-lookup"><span data-stu-id="7d918-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="7d918-107">La simulation de perception correspond à ce que vous recherchez.</span><span class="sxs-lookup"><span data-stu-id="7d918-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="7d918-108">La bibliothèque de simulation de perception envoie des données d’entrée humaines et mondiales à votre application afin que vous puissiez automatiser vos tests.</span><span class="sxs-lookup"><span data-stu-id="7d918-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="7d918-109">Par exemple, vous pouvez simuler l’entrée d’un utilisateur cherchant à une position renouvelée et spécifique, puis à utiliser un geste ou un contrôleur de mouvement.</span><span class="sxs-lookup"><span data-stu-id="7d918-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then use a gesture or motion controller.</span></span>

<span data-ttu-id="7d918-110">La simulation de perception peut envoyer une entrée simulée comme celle-ci à une HoloLens physique, à l’émulateur HoloLens (première génération), à l’émulateur HoloLens 2 ou à un PC avec portail de réalité mixte installé.</span><span class="sxs-lookup"><span data-stu-id="7d918-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (first gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="7d918-111">La simulation de perception contourne les capteurs actifs sur un appareil de réalité mixte et envoie une entrée simulée aux applications qui s’exécutent sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="7d918-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="7d918-112">Les applications reçoivent ces événements d’entrée via les mêmes API qu’ils utilisent toujours et ne peuvent pas indiquer la différence entre l’exécution avec des capteurs réels et la simulation de perception.</span><span class="sxs-lookup"><span data-stu-id="7d918-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus Perception Simulation.</span></span> <span data-ttu-id="7d918-113">La simulation de perception est la même technologie que celle utilisée par les émulateurs HoloLens pour envoyer une entrée simulée à la machine virtuelle HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7d918-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="7d918-114">Pour commencer à utiliser la simulation dans votre code, commencez par créer un objet IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="7d918-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="7d918-115">À partir de cet objet, vous pouvez émettre des commandes pour contrôler les propriétés d’un « humain » simulé, y compris la position de la tête, la position de la main et les gestes.</span><span class="sxs-lookup"><span data-stu-id="7d918-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span> <span data-ttu-id="7d918-116">Vous pouvez également activer et manipuler les contrôleurs de mouvement.</span><span class="sxs-lookup"><span data-stu-id="7d918-116">You can also enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="7d918-117">Configuration d’un projet Visual Studio pour la simulation de perception</span><span class="sxs-lookup"><span data-stu-id="7d918-117">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="7d918-118">[Installez l’émulateur HoloLens](../install-the-tools.md) sur votre PC de développement.</span><span class="sxs-lookup"><span data-stu-id="7d918-118">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="7d918-119">L’émulateur comprend les bibliothèques que vous utilisez pour la simulation de perception.</span><span class="sxs-lookup"><span data-stu-id="7d918-119">The emulator includes the libraries you' use for Perception Simulation.</span></span>
2. <span data-ttu-id="7d918-120">Créez un projet de bureau Visual Studio C# (un projet de console fonctionne bien pour commencer).</span><span class="sxs-lookup"><span data-stu-id="7d918-120">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="7d918-121">Ajoutez les fichiers binaires suivants à votre projet en tant que références (Project->Add->Reference...). Vous pouvez les Rechercher dans% ProgramFiles (x86)% \ Microsoft XDE \\ (version), par exemple **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** pour l’émulateur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7d918-121">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="7d918-122">(Remarque : bien que les fichiers binaires fassent partie de l’émulateur HoloLens 2, ils fonctionnent également pour Windows Mixed Reality sur le bureau.) un.</span><span class="sxs-lookup"><span data-stu-id="7d918-122">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="7d918-123">Wrapper C# géré par PerceptionSimulationManager.Interop.dll pour la simulation de perception.</span><span class="sxs-lookup"><span data-stu-id="7d918-123">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="7d918-124">b.</span><span class="sxs-lookup"><span data-stu-id="7d918-124">b.</span></span> <span data-ttu-id="7d918-125">PerceptionSimulationRest.dll-Library pour la configuration d’un canal de communication de sockets Web vers le HoloLens ou l’émulateur.</span><span class="sxs-lookup"><span data-stu-id="7d918-125">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="7d918-126">c.</span><span class="sxs-lookup"><span data-stu-id="7d918-126">c.</span></span> <span data-ttu-id="7d918-127">SimulationStream.Interop.dll-types partagés pour la simulation.</span><span class="sxs-lookup"><span data-stu-id="7d918-127">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="7d918-128">Ajoutez le PerceptionSimulationManager.dll binaire d’implémentation à votre projet a.</span><span class="sxs-lookup"><span data-stu-id="7d918-128">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="7d918-129">Tout d’abord, ajoutez-le en tant que fichier binaire au projet (Project->ajouter >élément existant...). Enregistrez-le en tant que lien afin qu’il ne soit pas copié dans le dossier source de votre projet.</span><span class="sxs-lookup"><span data-stu-id="7d918-129">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="7d918-130">![Ajoutez PerceptionSimulationManager.dll au projet en tant que lien ](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="7d918-130">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="7d918-131">Ensuite, assurez-vous qu’il est copié dans votre dossier de sortie lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="7d918-131">Then make sure that it gets copied to your output folder on build.</span></span> <span data-ttu-id="7d918-132">Il s’agit de la feuille de propriétés pour le binaire.</span><span class="sxs-lookup"><span data-stu-id="7d918-132">This is in the property sheet for the binary.</span></span> <span data-ttu-id="7d918-133">![Marquer PerceptionSimulationManager.dll pour copier dans le répertoire de sortie](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="7d918-133">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="7d918-134">Définissez la plateforme de votre solution active sur x64.</span><span class="sxs-lookup"><span data-stu-id="7d918-134">Set your active solution platform to x64.</span></span>  <span data-ttu-id="7d918-135">(Utilisez la Configuration Manager pour créer une entrée de plateforme pour x64, si celle-ci n’existe pas déjà.)</span><span class="sxs-lookup"><span data-stu-id="7d918-135">(Use the Configuration Manager to create a Platform entry for x64 if one doesn't already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="7d918-136">Création d’un objet IPerceptionSimulation Manager</span><span class="sxs-lookup"><span data-stu-id="7d918-136">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="7d918-137">Pour contrôler la simulation, vous allez émettre des mises à jour des objets récupérés à partir d’un objet IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="7d918-137">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="7d918-138">La première étape consiste à obtenir cet objet et à le connecter à votre appareil ou émulateur cible.</span><span class="sxs-lookup"><span data-stu-id="7d918-138">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="7d918-139">Vous pouvez récupérer l’adresse IP de votre émulateur en cliquant sur le bouton du portail de l’appareil dans la [barre d’outils](using-the-hololens-emulator.md) .</span><span class="sxs-lookup"><span data-stu-id="7d918-139">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="7d918-140">![Icône Ouvrir le portail de l’appareil ](images/emulator-deviceportal.png) **ouvrir le portail** de l’appareil : Ouvrez le portail de périphériques Windows pour le système d’exploitation HoloLens dans l’émulateur.</span><span class="sxs-lookup"><span data-stu-id="7d918-140">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="7d918-141">Pour Windows Mixed Reality, vous pouvez le récupérer dans l’application paramètres sous « mettre à jour & sécurité », puis « pour les développeurs » dans la section « se connecter à l’aide de » sous « activer le portail d’appareils ».</span><span class="sxs-lookup"><span data-stu-id="7d918-141">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="7d918-142">Veillez à noter l’adresse IP et le port.</span><span class="sxs-lookup"><span data-stu-id="7d918-142">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="7d918-143">Tout d’abord, vous devez appeler RestSimulationStreamSink. Create pour obtenir un objet RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="7d918-143">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="7d918-144">Il s’agit de l’appareil ou de l’émulateur cible que vous contrôlez sur une connexion http.</span><span class="sxs-lookup"><span data-stu-id="7d918-144">This is the target device or emulator that you'll control over an http connection.</span></span> <span data-ttu-id="7d918-145">Vos commandes sont transmises à et gérées par le [portail de périphériques Windows](using-the-windows-device-portal.md) exécuté sur l’appareil ou l’émulateur.</span><span class="sxs-lookup"><span data-stu-id="7d918-145">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="7d918-146">Les quatre paramètres dont vous avez besoin pour créer un objet sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="7d918-146">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="7d918-147">URI Uri : adresse IP de l’appareil cible (par exemple, « https://123.123.123.123 » ou «» https://123.123.123.123:50080 )</span><span class="sxs-lookup"><span data-stu-id="7d918-147">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="7d918-148">Informations d’identification System .net. NetworkCredential-nom d’utilisateur/mot de passe pour la connexion au [portail d’appareils Windows](using-the-windows-device-portal.md) sur l’appareil ou l’émulateur cible.</span><span class="sxs-lookup"><span data-stu-id="7d918-148">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="7d918-149">Si vous vous connectez à l’émulateur via son adresse locale (par exemple,*168...* \*) sur le même PC, toutes les informations d’identification seront acceptées.</span><span class="sxs-lookup"><span data-stu-id="7d918-149">If you're connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="7d918-150">bool normal-true pour la priorité normale, false pour basse priorité.</span><span class="sxs-lookup"><span data-stu-id="7d918-150">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="7d918-151">Vous souhaitez généralement définir cette propriété sur *true* pour les scénarios de test, ce qui permet à votre test de prendre le contrôle.</span><span class="sxs-lookup"><span data-stu-id="7d918-151">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="7d918-152">La simulation de l’émulateur et de la réalité mixte Windows utilise des connexions de faible priorité.</span><span class="sxs-lookup"><span data-stu-id="7d918-152">The emulator and Windows Mixed Reality simulation use low-priority connections.</span></span>  <span data-ttu-id="7d918-153">Si votre test utilise également une connexion de priorité basse, la connexion établie le plus récemment sera contrôle.</span><span class="sxs-lookup"><span data-stu-id="7d918-153">If your test also uses a low-priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="7d918-154">Jeton-jeton System. Threading. CancellationToken pour annuler l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="7d918-154">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="7d918-155">Ensuite, vous allez créer le IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="7d918-155">Second, you'll create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="7d918-156">Il s’agit de l’objet que vous utilisez pour contrôler la simulation.</span><span class="sxs-lookup"><span data-stu-id="7d918-156">This is the object you use to control simulation.</span></span> <span data-ttu-id="7d918-157">Cela doit également être fait dans une méthode Async.</span><span class="sxs-lookup"><span data-stu-id="7d918-157">This must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="7d918-158">Contrôler l’homme simulé</span><span class="sxs-lookup"><span data-stu-id="7d918-158">Control the simulated Human</span></span>

<span data-ttu-id="7d918-159">Un IPerceptionSimulationManager a une propriété humaine qui retourne un objet ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="7d918-159">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="7d918-160">Pour contrôler l’homme simulé, effectuez des opérations sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="7d918-160">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="7d918-161">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7d918-161">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="7d918-162">Exemple d’application de console C# de base</span><span class="sxs-lookup"><span data-stu-id="7d918-162">Basic Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="7d918-163">Exemple d’application de console C# étendue</span><span class="sxs-lookup"><span data-stu-id="7d918-163">Extended Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="7d918-164">Remarque sur les contrôleurs 6-DDL</span><span class="sxs-lookup"><span data-stu-id="7d918-164">Note on 6-DOF controllers</span></span>

<span data-ttu-id="7d918-165">Avant d’appeler des propriétés sur des méthodes sur un contrôleur 6-DDL simulé, vous devez activer le contrôleur.</span><span class="sxs-lookup"><span data-stu-id="7d918-165">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="7d918-166">Si ce n’est pas le cas, une exception est générée.</span><span class="sxs-lookup"><span data-stu-id="7d918-166">Not doing so will result in an exception.</span></span>  <span data-ttu-id="7d918-167">À compter de la mise à jour de Windows 10 2019 mai, les contrôleurs 6-DDL simulés peuvent être installés et activés en définissant la propriété Status sur l’objet ISimulatedSixDofController sur SimulatedSixDofControllerStatus. active.</span><span class="sxs-lookup"><span data-stu-id="7d918-167">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="7d918-168">Dans la mise à jour 2018 de Windows 10 octobre et les versions antérieures, vous devez d’abord installer séparément un contrôleur 6-DDL simulé en appelant l’outil PerceptionSimulationDevice situé dans le dossier \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="7d918-168">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="7d918-169">L’utilisation de cet outil est la suivante :</span><span class="sxs-lookup"><span data-stu-id="7d918-169">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="7d918-170">Par exemple</span><span class="sxs-lookup"><span data-stu-id="7d918-170">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="7d918-171">Les actions prises en charge sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7d918-171">Supported actions are:</span></span>
* <span data-ttu-id="7d918-172">i = installation</span><span class="sxs-lookup"><span data-stu-id="7d918-172">i = install</span></span>
* <span data-ttu-id="7d918-173">q = requête</span><span class="sxs-lookup"><span data-stu-id="7d918-173">q = query</span></span>
* <span data-ttu-id="7d918-174">r = supprimer</span><span class="sxs-lookup"><span data-stu-id="7d918-174">r = remove</span></span>

<span data-ttu-id="7d918-175">Les instances prises en charge sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7d918-175">Supported instances are:</span></span>
* <span data-ttu-id="7d918-176">1 = le contrôleur 6-DDL de gauche</span><span class="sxs-lookup"><span data-stu-id="7d918-176">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="7d918-177">2 = le contrôleur 6-DDL correct</span><span class="sxs-lookup"><span data-stu-id="7d918-177">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="7d918-178">Le code de sortie du processus indique la réussite (valeur de retour zéro) ou l’échec (valeur de retour différente de zéro).</span><span class="sxs-lookup"><span data-stu-id="7d918-178">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="7d918-179">Lorsque vous utilisez l’action « q » pour demander si un contrôleur est installé, la valeur de retour est zéro (0) si le contrôleur n’est pas déjà installé ou un (1) si le contrôleur est installé.</span><span class="sxs-lookup"><span data-stu-id="7d918-179">When using the 'q' action to query whether a controller is installed, the return value will be zero (0) if the controller isn't already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="7d918-180">Lorsque vous supprimez un contrôleur sur la mise à jour 2018 de Windows 10 octobre ou une version antérieure, définissez son état sur OFF via l’API en premier, puis appelez l’outil PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="7d918-180">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="7d918-181">Cet outil doit être exécuté en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="7d918-181">This tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="7d918-182">Référence API</span><span class="sxs-lookup"><span data-stu-id="7d918-182">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="7d918-183">Microsoft. PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="7d918-183">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="7d918-184">Décrit un type d’appareil simulé</span><span class="sxs-lookup"><span data-stu-id="7d918-184">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="7d918-185">**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="7d918-185">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="7d918-186">Un appareil de référence fictif, la valeur par défaut pour PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="7d918-186">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="7d918-187">Microsoft. PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="7d918-187">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="7d918-188">Décrit un mode de suivi d’en-tête</span><span class="sxs-lookup"><span data-stu-id="7d918-188">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="7d918-189">**Microsoft. PerceptionSimulation. HeadTrackerMode. default**</span><span class="sxs-lookup"><span data-stu-id="7d918-189">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="7d918-190">Suivi des en-têtes par défaut.</span><span class="sxs-lookup"><span data-stu-id="7d918-190">Default Head Tracking.</span></span> <span data-ttu-id="7d918-191">Cela signifie que le système peut sélectionner le mode de suivi optimal en fonction des conditions d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7d918-191">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="7d918-192">**Microsoft. PerceptionSimulation. HeadTrackerMode. orientation**</span><span class="sxs-lookup"><span data-stu-id="7d918-192">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="7d918-193">Suivi d’en-tête d’orientation uniquement.</span><span class="sxs-lookup"><span data-stu-id="7d918-193">Orientation Only Head Tracking.</span></span> <span data-ttu-id="7d918-194">Cela signifie que la position suivie peut ne pas être fiable, et certaines fonctionnalités qui dépendent de la position de la tête peuvent ne pas être disponibles.</span><span class="sxs-lookup"><span data-stu-id="7d918-194">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="7d918-195">**Microsoft. PerceptionSimulation. HeadTrackerMode. position**</span><span class="sxs-lookup"><span data-stu-id="7d918-195">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="7d918-196">Suivi de l’en-tête positionnel.</span><span class="sxs-lookup"><span data-stu-id="7d918-196">Positional Head Tracking.</span></span> <span data-ttu-id="7d918-197">Cela signifie que la position et l’orientation de la tête de suivi sont fiables</span><span class="sxs-lookup"><span data-stu-id="7d918-197">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="7d918-198">Microsoft. PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="7d918-198">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="7d918-199">Décrit un mouvement simulé</span><span class="sxs-lookup"><span data-stu-id="7d918-199">Describes a simulated gesture</span></span>

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

<span data-ttu-id="7d918-200">**Microsoft. PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="7d918-200">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="7d918-201">Valeur de sentinelle utilisée pour indiquer l’absence de gestes.</span><span class="sxs-lookup"><span data-stu-id="7d918-201">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="7d918-202">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="7d918-202">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="7d918-203">Mouvement appuyé sur le doigt.</span><span class="sxs-lookup"><span data-stu-id="7d918-203">A finger pressed gesture.</span></span>

<span data-ttu-id="7d918-204">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="7d918-204">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="7d918-205">Mouvement de libération d’un doigt.</span><span class="sxs-lookup"><span data-stu-id="7d918-205">A finger released gesture.</span></span>

<span data-ttu-id="7d918-206">**Microsoft. PerceptionSimulation. SimulatedGesture. orig**</span><span class="sxs-lookup"><span data-stu-id="7d918-206">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="7d918-207">Mouvement de démarrage/système.</span><span class="sxs-lookup"><span data-stu-id="7d918-207">The home/system gesture.</span></span>

<span data-ttu-id="7d918-208">**Microsoft. PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="7d918-208">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="7d918-209">Mouvement maximal valide.</span><span class="sxs-lookup"><span data-stu-id="7d918-209">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="7d918-210">Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="7d918-210">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="7d918-211">États possibles d’un contrôleur 6-DDL simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-211">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="7d918-212">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. OFF**</span><span class="sxs-lookup"><span data-stu-id="7d918-212">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="7d918-213">Le contrôleur 6-DDL est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7d918-213">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="7d918-214">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. active**</span><span class="sxs-lookup"><span data-stu-id="7d918-214">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="7d918-215">Le contrôleur 6-DDL est activé et suivi.</span><span class="sxs-lookup"><span data-stu-id="7d918-215">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="7d918-216">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="7d918-216">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="7d918-217">Le contrôleur 6-DDL est activé, mais ne peut pas être suivi.</span><span class="sxs-lookup"><span data-stu-id="7d918-217">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="7d918-218">Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="7d918-218">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="7d918-219">Les boutons pris en charge sur un contrôleur 6-DDL simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-219">The supported buttons on a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

<span data-ttu-id="7d918-220">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="7d918-220">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="7d918-221">Valeur de sentinelle utilisée pour indiquer qu’aucun bouton n’est présent.</span><span class="sxs-lookup"><span data-stu-id="7d918-221">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="7d918-222">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. orig**</span><span class="sxs-lookup"><span data-stu-id="7d918-222">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="7d918-223">Le bouton d’hébergement est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="7d918-223">The Home button is pressed.</span></span>

<span data-ttu-id="7d918-224">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. menu**</span><span class="sxs-lookup"><span data-stu-id="7d918-224">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="7d918-225">Le bouton de menu est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="7d918-225">The Menu button is pressed.</span></span>

<span data-ttu-id="7d918-226">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. poignée**</span><span class="sxs-lookup"><span data-stu-id="7d918-226">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="7d918-227">Le bouton de la poignée est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="7d918-227">The Grip button is pressed.</span></span>

<span data-ttu-id="7d918-228">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="7d918-228">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="7d918-229">Le pavé tactile est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="7d918-229">The TouchPad is pressed.</span></span>

<span data-ttu-id="7d918-230">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="7d918-230">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="7d918-231">Le bouton Sélectionner est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="7d918-231">The Select button is pressed.</span></span>

<span data-ttu-id="7d918-232">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="7d918-232">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="7d918-233">Le pavé tactile est touché.</span><span class="sxs-lookup"><span data-stu-id="7d918-233">The TouchPad is touched.</span></span>

<span data-ttu-id="7d918-234">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Stick**</span><span class="sxs-lookup"><span data-stu-id="7d918-234">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="7d918-235">Le stick analogique est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="7d918-235">The Thumbstick is pressed.</span></span>

<span data-ttu-id="7d918-236">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="7d918-236">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="7d918-237">Le bouton nombre maximal valide.</span><span class="sxs-lookup"><span data-stu-id="7d918-237">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="7d918-238">Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="7d918-238">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="7d918-239">État d’étalonnage des yeux simulés</span><span class="sxs-lookup"><span data-stu-id="7d918-239">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="7d918-240">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. non disponible**</span><span class="sxs-lookup"><span data-stu-id="7d918-240">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="7d918-241">L’étalonnage des yeux n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="7d918-241">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="7d918-242">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="7d918-242">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="7d918-243">Les yeux ont été étalonnés.</span><span class="sxs-lookup"><span data-stu-id="7d918-243">The eyes have been calibrated.</span></span>  <span data-ttu-id="7d918-244">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7d918-244">This is the default value.</span></span>

<span data-ttu-id="7d918-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configutilisons**</span><span class="sxs-lookup"><span data-stu-id="7d918-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="7d918-246">Les yeux sont calibrés.</span><span class="sxs-lookup"><span data-stu-id="7d918-246">The eyes are being calibrated.</span></span>

<span data-ttu-id="7d918-247">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="7d918-247">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="7d918-248">Les yeux doivent être étalonnés.</span><span class="sxs-lookup"><span data-stu-id="7d918-248">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="7d918-249">Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="7d918-249">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="7d918-250">Précision de suivi d’une jointure de la main.</span><span class="sxs-lookup"><span data-stu-id="7d918-250">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="7d918-251">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. non disponible**</span><span class="sxs-lookup"><span data-stu-id="7d918-251">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="7d918-252">La jointure n’est pas suivie.</span><span class="sxs-lookup"><span data-stu-id="7d918-252">The joint isn't tracked.</span></span>

<span data-ttu-id="7d918-253">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. approximatif**</span><span class="sxs-lookup"><span data-stu-id="7d918-253">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="7d918-254">La position conjointe est déduite.</span><span class="sxs-lookup"><span data-stu-id="7d918-254">The joint position is inferred.</span></span>

<span data-ttu-id="7d918-255">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. visible**</span><span class="sxs-lookup"><span data-stu-id="7d918-255">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="7d918-256">L’articulation est entièrement suivie.</span><span class="sxs-lookup"><span data-stu-id="7d918-256">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="7d918-257">Microsoft. PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="7d918-257">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="7d918-258">Précision de suivi d’une jointure de la main.</span><span class="sxs-lookup"><span data-stu-id="7d918-258">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

<span data-ttu-id="7d918-259">**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**</span><span class="sxs-lookup"><span data-stu-id="7d918-259">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="7d918-260">Les jointures Finger de la main sont configurées pour refléter une pose fermée.</span><span class="sxs-lookup"><span data-stu-id="7d918-260">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="7d918-261">**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="7d918-261">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="7d918-262">Les jointures Finger de la main sont configurées pour refléter une pose ouverte.</span><span class="sxs-lookup"><span data-stu-id="7d918-262">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="7d918-263">**Microsoft. PerceptionSimulation. SimulatedHandPose. point**</span><span class="sxs-lookup"><span data-stu-id="7d918-263">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="7d918-264">Les jointures Finger de la main sont configurées pour refléter une pose de pointage.</span><span class="sxs-lookup"><span data-stu-id="7d918-264">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="7d918-265">**Microsoft. PerceptionSimulation. SimulatedHandPose. pincement**</span><span class="sxs-lookup"><span data-stu-id="7d918-265">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="7d918-266">Les jointures Finger de la main sont configurées pour refléter une pose de pincement.</span><span class="sxs-lookup"><span data-stu-id="7d918-266">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="7d918-267">**Microsoft. PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="7d918-267">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="7d918-268">Valeur maximale valide pour SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="7d918-268">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="7d918-269">Microsoft. PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="7d918-269">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="7d918-270">Décrit l’état d’une lecture.</span><span class="sxs-lookup"><span data-stu-id="7d918-270">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="7d918-271">**Microsoft. PerceptionSimulation. PlaybackState. Stopped**</span><span class="sxs-lookup"><span data-stu-id="7d918-271">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="7d918-272">L’enregistrement est actuellement arrêté et prêt pour la lecture.</span><span class="sxs-lookup"><span data-stu-id="7d918-272">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="7d918-273">**Microsoft. PerceptionSimulation. PlaybackState. Playing**</span><span class="sxs-lookup"><span data-stu-id="7d918-273">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="7d918-274">L’enregistrement est en cours de diffusion.</span><span class="sxs-lookup"><span data-stu-id="7d918-274">The recording is currently playing.</span></span>

<span data-ttu-id="7d918-275">**Microsoft. PerceptionSimulation. PlaybackState. Paused**</span><span class="sxs-lookup"><span data-stu-id="7d918-275">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="7d918-276">L’enregistrement est actuellement suspendu.</span><span class="sxs-lookup"><span data-stu-id="7d918-276">The recording is currently paused.</span></span>

<span data-ttu-id="7d918-277">**Microsoft. PerceptionSimulation. PlaybackState. end**</span><span class="sxs-lookup"><span data-stu-id="7d918-277">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="7d918-278">L’enregistrement a atteint la fin.</span><span class="sxs-lookup"><span data-stu-id="7d918-278">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="7d918-279">Microsoft. PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="7d918-279">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="7d918-280">Décrit un vecteur à trois composants, qui peut décrire un point ou un vecteur dans l’espace 3D.</span><span class="sxs-lookup"><span data-stu-id="7d918-280">Describes a three components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="7d918-281">**Microsoft. PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="7d918-281">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="7d918-282">Composant X du vecteur.</span><span class="sxs-lookup"><span data-stu-id="7d918-282">The X component of the vector.</span></span>

<span data-ttu-id="7d918-283">**Microsoft. PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="7d918-283">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="7d918-284">Composant Y du vecteur.</span><span class="sxs-lookup"><span data-stu-id="7d918-284">The Y component of the vector.</span></span>

<span data-ttu-id="7d918-285">**Microsoft. PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="7d918-285">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="7d918-286">Composant Z du vecteur.</span><span class="sxs-lookup"><span data-stu-id="7d918-286">The Z component of the vector.</span></span>

<span data-ttu-id="7d918-287">**Microsoft. PerceptionSimulation. Vector3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="7d918-287">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="7d918-288">Construisez un nouveau Vector3.</span><span class="sxs-lookup"><span data-stu-id="7d918-288">Construct a new Vector3.</span></span>

<span data-ttu-id="7d918-289">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-289">Parameters</span></span>
* <span data-ttu-id="7d918-290">x-composant x du vecteur.</span><span class="sxs-lookup"><span data-stu-id="7d918-290">x - The x component of the vector.</span></span>
* <span data-ttu-id="7d918-291">y : composant y du vecteur.</span><span class="sxs-lookup"><span data-stu-id="7d918-291">y - The y component of the vector.</span></span>
* <span data-ttu-id="7d918-292">z-composant z du vecteur.</span><span class="sxs-lookup"><span data-stu-id="7d918-292">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="7d918-293">Microsoft. PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="7d918-293">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="7d918-294">Décrit une rotation de trois composants.</span><span class="sxs-lookup"><span data-stu-id="7d918-294">Describes a three components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="7d918-295">**Microsoft. PerceptionSimulation. Rotation3. brai**</span><span class="sxs-lookup"><span data-stu-id="7d918-295">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="7d918-296">Composant de pas de la rotation, en hauteur autour de l’axe X.</span><span class="sxs-lookup"><span data-stu-id="7d918-296">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="7d918-297">**Microsoft. PerceptionSimulation. Rotation3. lacet**</span><span class="sxs-lookup"><span data-stu-id="7d918-297">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="7d918-298">Composant de lacet de la rotation, à droite autour de l’axe Y.</span><span class="sxs-lookup"><span data-stu-id="7d918-298">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="7d918-299">**Microsoft. PerceptionSimulation. Rotation3. Roll**</span><span class="sxs-lookup"><span data-stu-id="7d918-299">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="7d918-300">Composant de roulement de la rotation, à droite autour de l’axe Z.</span><span class="sxs-lookup"><span data-stu-id="7d918-300">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="7d918-301">**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="7d918-301">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="7d918-302">Construisez un nouveau Rotation3.</span><span class="sxs-lookup"><span data-stu-id="7d918-302">Construct a new Rotation3.</span></span>

<span data-ttu-id="7d918-303">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-303">Parameters</span></span>
* <span data-ttu-id="7d918-304">tangage : composant de pas de la rotation.</span><span class="sxs-lookup"><span data-stu-id="7d918-304">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="7d918-305">lacet : composant de lacet de la rotation.</span><span class="sxs-lookup"><span data-stu-id="7d918-305">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="7d918-306">Roll-le composant Roll de la rotation.</span><span class="sxs-lookup"><span data-stu-id="7d918-306">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="7d918-307">Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d918-307">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="7d918-308">Décrit la configuration d’un joint sur une main simulée.</span><span class="sxs-lookup"><span data-stu-id="7d918-308">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="7d918-309">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. position**</span><span class="sxs-lookup"><span data-stu-id="7d918-309">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="7d918-310">Position de la jointure.</span><span class="sxs-lookup"><span data-stu-id="7d918-310">The position of the joint.</span></span>

<span data-ttu-id="7d918-311">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. rotation**</span><span class="sxs-lookup"><span data-stu-id="7d918-311">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="7d918-312">Rotation de la jointure.</span><span class="sxs-lookup"><span data-stu-id="7d918-312">The rotation of the joint.</span></span>

<span data-ttu-id="7d918-313">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="7d918-313">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="7d918-314">Précision de suivi de la jointure.</span><span class="sxs-lookup"><span data-stu-id="7d918-314">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="7d918-315">Microsoft. PerceptionSimulation. frustum</span><span class="sxs-lookup"><span data-stu-id="7d918-315">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="7d918-316">Décrit un frustum d’affichage, tel qu’il est généralement utilisé par un appareil photo.</span><span class="sxs-lookup"><span data-stu-id="7d918-316">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="7d918-317">**Microsoft. PerceptionSimulation. frustum. Near**</span><span class="sxs-lookup"><span data-stu-id="7d918-317">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="7d918-318">Distance minimale contenue dans le frustum.</span><span class="sxs-lookup"><span data-stu-id="7d918-318">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="7d918-319">**Microsoft. PerceptionSimulation. frustum. Far**</span><span class="sxs-lookup"><span data-stu-id="7d918-319">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="7d918-320">Distance maximale contenue dans le frustum.</span><span class="sxs-lookup"><span data-stu-id="7d918-320">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="7d918-321">**Microsoft. PerceptionSimulation. frustum. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="7d918-321">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="7d918-322">Champ horizontal de la vue de frustum, en radians (inférieur à PI).</span><span class="sxs-lookup"><span data-stu-id="7d918-322">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="7d918-323">**Microsoft. PerceptionSimulation. frustum. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="7d918-323">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="7d918-324">Rapport entre le champ horizontal de la vue et le champ vertical de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="7d918-324">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="7d918-325">Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d918-325">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="7d918-326">Décrit la configuration de l’affichage du casque simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-326">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="7d918-327">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="7d918-327">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="7d918-328">Transformation à partir du centre de la tête vers l’œil gauche à des fins de rendu stéréo.</span><span class="sxs-lookup"><span data-stu-id="7d918-328">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="7d918-329">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="7d918-329">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="7d918-330">Rotation de l’œil gauche à des fins de rendu stéréo.</span><span class="sxs-lookup"><span data-stu-id="7d918-330">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="7d918-331">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="7d918-331">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="7d918-332">Transformation à partir du centre de la tête vers le bon œil à des fins de rendu stéréo.</span><span class="sxs-lookup"><span data-stu-id="7d918-332">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="7d918-333">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="7d918-333">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="7d918-334">Rotation de l’œil droit à des fins de rendu stéréo.</span><span class="sxs-lookup"><span data-stu-id="7d918-334">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="7d918-335">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. IPD**</span><span class="sxs-lookup"><span data-stu-id="7d918-335">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="7d918-336">Valeur IPD signalée par le système à des fins de rendu stéréo.</span><span class="sxs-lookup"><span data-stu-id="7d918-336">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="7d918-337">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="7d918-337">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="7d918-338">Si les valeurs fournies pour les transformations d’œil gauche et droit doivent être considérées comme valides et appliquées au système en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7d918-338">Whether the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="7d918-339">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="7d918-339">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="7d918-340">Indique si la valeur fournie pour IPD doit être considérée comme valide et appliquée au système en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7d918-340">Whether the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="7d918-341">Microsoft. PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="7d918-341">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="7d918-342">Racine pour la génération des paquets utilisés pour contrôler un appareil.</span><span class="sxs-lookup"><span data-stu-id="7d918-342">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="7d918-343">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**</span><span class="sxs-lookup"><span data-stu-id="7d918-343">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="7d918-344">Récupérez l’objet d’appareil simulé qui interprète l’homme simulé et le monde simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-344">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="7d918-345">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**</span><span class="sxs-lookup"><span data-stu-id="7d918-345">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="7d918-346">Récupérez l’objet qui contrôle l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-346">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="7d918-347">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**</span><span class="sxs-lookup"><span data-stu-id="7d918-347">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="7d918-348">Rétablit l’État par défaut de la simulation.</span><span class="sxs-lookup"><span data-stu-id="7d918-348">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="7d918-349">Microsoft. PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="7d918-349">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="7d918-350">Interface décrivant l’appareil, qui interprète le monde simulé et l’homme simulé</span><span class="sxs-lookup"><span data-stu-id="7d918-350">Interface describing the device, which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="7d918-351">**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="7d918-351">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="7d918-352">Récupérez le dispositif de suivi des têtes à partir de l’appareil simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-352">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="7d918-353">**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="7d918-353">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="7d918-354">Récupérez le dispositif de suivi de main à partir de l’appareil simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-354">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="7d918-355">**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="7d918-355">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="7d918-356">Définissez les propriétés de l’appareil simulé pour qu’elles correspondent au type d’appareil fourni.</span><span class="sxs-lookup"><span data-stu-id="7d918-356">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="7d918-357">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-357">Parameters</span></span>
* <span data-ttu-id="7d918-358">type-le nouveau type d’appareil simulé</span><span class="sxs-lookup"><span data-stu-id="7d918-358">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="7d918-359">Microsoft. PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="7d918-359">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="7d918-360">Des propriétés supplémentaires sont disponibles en convertissant le ISimulatedDevice en ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="7d918-360">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="7d918-361">**Microsoft. PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="7d918-361">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="7d918-362">Récupérer ou définir si l’homme simulé porte activement le casque.</span><span class="sxs-lookup"><span data-stu-id="7d918-362">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="7d918-363">**Microsoft. PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="7d918-363">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="7d918-364">Récupérer ou définir les propriétés de l’affichage simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-364">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="7d918-365">Microsoft. PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="7d918-365">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="7d918-366">Interface décrivant la partie de l’appareil simulé qui effectue le suivi du chef de l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-366">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="7d918-367">**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="7d918-367">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="7d918-368">Récupère et définit le mode de suivi d’en-tête actuel.</span><span class="sxs-lookup"><span data-stu-id="7d918-368">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="7d918-369">Microsoft. PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="7d918-369">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="7d918-370">Interface décrivant la partie de l’appareil simulé qui effectue le suivi des mains de l’homme simulé</span><span class="sxs-lookup"><span data-stu-id="7d918-370">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

<span data-ttu-id="7d918-371">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7d918-371">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="7d918-372">Récupérer la position du nœud par rapport au monde, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-372">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="7d918-373">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. position**</span><span class="sxs-lookup"><span data-stu-id="7d918-373">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="7d918-374">Récupère et définit la position du suivi de la main simulé, par rapport au centre de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="7d918-374">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="7d918-375">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. brai**</span><span class="sxs-lookup"><span data-stu-id="7d918-375">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="7d918-376">Récupérer et définir le pas à pas bas du suivi simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-376">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="7d918-377">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="7d918-377">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="7d918-378">Récupérez et définissez si le frustum du suivi de la main simulé est ignoré.</span><span class="sxs-lookup"><span data-stu-id="7d918-378">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="7d918-379">Lorsqu’ils sont ignorés, les deux mains sont toujours visibles.</span><span class="sxs-lookup"><span data-stu-id="7d918-379">When ignored, both hands are always visible.</span></span> <span data-ttu-id="7d918-380">Lorsqu’elles ne sont pas ignorées (par défaut), elles ne sont visibles que lorsqu’elles se trouvent dans le frustum du dispositif de suivi de la main.</span><span class="sxs-lookup"><span data-stu-id="7d918-380">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="7d918-381">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. frustum**</span><span class="sxs-lookup"><span data-stu-id="7d918-381">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="7d918-382">Récupérez et définissez les propriétés frustum utilisées pour déterminer si les mains sont visibles pour le suivi de la main simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-382">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="7d918-383">Microsoft. PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="7d918-383">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="7d918-384">Interface de niveau supérieur pour le contrôle de l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-384">Top-level interface for controlling the simulated human.</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="7d918-385">**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7d918-385">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="7d918-386">Récupérer et définir la position du nœud par rapport au monde, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-386">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="7d918-387">La position correspond à un point au centre des pieds de l’homme.</span><span class="sxs-lookup"><span data-stu-id="7d918-387">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="7d918-388">**Microsoft. PerceptionSimulation. ISimulatedHuman. direction**</span><span class="sxs-lookup"><span data-stu-id="7d918-388">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="7d918-389">Récupérez et définissez le sens des visages humains simulés dans le monde.</span><span class="sxs-lookup"><span data-stu-id="7d918-389">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="7d918-390">0 radians est confronté à l’axe Z négatif.</span><span class="sxs-lookup"><span data-stu-id="7d918-390">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="7d918-391">Les radians positifs pivotent dans le sens des aiguilles d’une montre autour de l’axe Y.</span><span class="sxs-lookup"><span data-stu-id="7d918-391">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="7d918-392">**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="7d918-392">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="7d918-393">Récupérez et définissez la hauteur de l’homme simulé, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-393">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="7d918-394">**Microsoft. PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="7d918-394">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="7d918-395">Récupérez la main gauche de l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-395">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="7d918-396">**Microsoft. PerceptionSimulation. ISimulatedHuman. à droite**</span><span class="sxs-lookup"><span data-stu-id="7d918-396">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="7d918-397">Récupérez la main droite de l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-397">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="7d918-398">**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="7d918-398">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="7d918-399">Récupérez l’en-tête de l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-399">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="7d918-400">**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="7d918-400">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="7d918-401">Déplacer le humain simulé par rapport à sa position actuelle, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-401">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="7d918-402">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-402">Parameters</span></span>
* <span data-ttu-id="7d918-403">translation : translation à déplacer, par rapport à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="7d918-403">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="7d918-404">**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="7d918-404">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="7d918-405">Faire pivoter l’homme simulé par rapport à sa direction actuelle, dans le sens des aiguilles d’une montre autour de l’axe Y</span><span class="sxs-lookup"><span data-stu-id="7d918-405">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="7d918-406">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-406">Parameters</span></span>
* <span data-ttu-id="7d918-407">radians-la valeur de rotation autour de l’axe Y.</span><span class="sxs-lookup"><span data-stu-id="7d918-407">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="7d918-408">Microsoft. PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="7d918-408">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="7d918-409">Des propriétés supplémentaires sont disponibles en convertissant le ISimulatedHuman en ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="7d918-409">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="7d918-410">**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="7d918-410">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="7d918-411">Récupérez le contrôleur 6-DDL de gauche.</span><span class="sxs-lookup"><span data-stu-id="7d918-411">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="7d918-412">**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="7d918-412">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="7d918-413">Récupérez le contrôleur 6-DDL approprié.</span><span class="sxs-lookup"><span data-stu-id="7d918-413">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="7d918-414">Microsoft. PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="7d918-414">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="7d918-415">Interface décrivant une main de l’homme simulé</span><span class="sxs-lookup"><span data-stu-id="7d918-415">Interface describing a hand of the simulated human</span></span>

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

<span data-ttu-id="7d918-416">**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7d918-416">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="7d918-417">Récupérer la position du nœud par rapport au monde, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-417">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="7d918-418">**Microsoft. PerceptionSimulation. ISimulatedHand. position**</span><span class="sxs-lookup"><span data-stu-id="7d918-418">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="7d918-419">Récupérer et définir la position de la main simulée par rapport à l’homme, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-419">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="7d918-420">**Microsoft. PerceptionSimulation. ISimulatedHand. Activated**</span><span class="sxs-lookup"><span data-stu-id="7d918-420">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="7d918-421">Récupère et définit si la main est actuellement activée.</span><span class="sxs-lookup"><span data-stu-id="7d918-421">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="7d918-422">**Microsoft. PerceptionSimulation. ISimulatedHand. visible**</span><span class="sxs-lookup"><span data-stu-id="7d918-422">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="7d918-423">Récupère si la main est actuellement visible pour le SimulatedDevice (autrement dit, si elle se trouve dans une position à détecter par le HandTracker).</span><span class="sxs-lookup"><span data-stu-id="7d918-423">Retrieve whether the hand is currently visible to the SimulatedDevice (that is, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="7d918-424">**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="7d918-424">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="7d918-425">Déplacez la main de manière à ce qu’elle soit visible par le SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="7d918-425">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="7d918-426">**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="7d918-426">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="7d918-427">Déplacer la position de la main simulée par rapport à sa position actuelle, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-427">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="7d918-428">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-428">Parameters</span></span>
* <span data-ttu-id="7d918-429">translation-le montant pour traduire la main simulée.</span><span class="sxs-lookup"><span data-stu-id="7d918-429">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="7d918-430">**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="7d918-430">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="7d918-431">Effectuez un mouvement à l’aide de la main simulée.</span><span class="sxs-lookup"><span data-stu-id="7d918-431">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="7d918-432">Elle sera détectée uniquement par le système si la main est activée.</span><span class="sxs-lookup"><span data-stu-id="7d918-432">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="7d918-433">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-433">Parameters</span></span>
* <span data-ttu-id="7d918-434">geste : mouvement à effectuer.</span><span class="sxs-lookup"><span data-stu-id="7d918-434">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="7d918-435">Microsoft. PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="7d918-435">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="7d918-436">Des propriétés supplémentaires sont disponibles en convertissant un ISimulatedHand en ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="7d918-436">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="7d918-437">**Microsoft. PerceptionSimulation. ISimulatedHand2. orientation**</span><span class="sxs-lookup"><span data-stu-id="7d918-437">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="7d918-438">Récupère ou définit la rotation de la main simulée.</span><span class="sxs-lookup"><span data-stu-id="7d918-438">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="7d918-439">Les radians positifs pivotent dans le sens des aiguilles d’une montre sur l’axe.</span><span class="sxs-lookup"><span data-stu-id="7d918-439">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="7d918-440">Microsoft. PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="7d918-440">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="7d918-441">Des propriétés supplémentaires sont disponibles en convertissant un ISimulatedHand en ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="7d918-441">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="7d918-442">**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="7d918-442">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="7d918-443">Obtient la configuration conjointe pour l’articulation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7d918-443">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="7d918-444">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="7d918-444">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="7d918-445">Définit la configuration conjointe pour l’articulation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7d918-445">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="7d918-446">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="7d918-446">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="7d918-447">Définissez la main sur une pose connue avec un indicateur facultatif à animer.</span><span class="sxs-lookup"><span data-stu-id="7d918-447">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="7d918-448">Remarque : l’animation ne permettra pas aux jointures de refléter immédiatement leurs configurations conjointes finales.</span><span class="sxs-lookup"><span data-stu-id="7d918-448">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="7d918-449">Microsoft. PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="7d918-449">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="7d918-450">Interface décrivant l’en-tête de l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-450">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="7d918-451">**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7d918-451">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="7d918-452">Récupérer la position du nœud par rapport au monde, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-452">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="7d918-453">**Microsoft. PerceptionSimulation. ISimulatedHead. rotation**</span><span class="sxs-lookup"><span data-stu-id="7d918-453">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="7d918-454">Récupère la rotation de la tête simulée.</span><span class="sxs-lookup"><span data-stu-id="7d918-454">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="7d918-455">Les radians positifs pivotent dans le sens des aiguilles d’une montre sur l’axe.</span><span class="sxs-lookup"><span data-stu-id="7d918-455">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="7d918-456">**Microsoft. PerceptionSimulation. ISimulatedHead. diametre**</span><span class="sxs-lookup"><span data-stu-id="7d918-456">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="7d918-457">Récupérer le diamètre de la tête simulée.</span><span class="sxs-lookup"><span data-stu-id="7d918-457">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="7d918-458">Cette valeur est utilisée pour déterminer le centre de l’en-tête (point de rotation).</span><span class="sxs-lookup"><span data-stu-id="7d918-458">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="7d918-459">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="7d918-459">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="7d918-460">Faire pivoter la tête simulée par rapport à sa rotation actuelle.</span><span class="sxs-lookup"><span data-stu-id="7d918-460">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="7d918-461">Les radians positifs pivotent dans le sens des aiguilles d’une montre sur l’axe.</span><span class="sxs-lookup"><span data-stu-id="7d918-461">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="7d918-462">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-462">Parameters</span></span>
* <span data-ttu-id="7d918-463">rotation : quantité à faire pivoter.</span><span class="sxs-lookup"><span data-stu-id="7d918-463">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="7d918-464">Microsoft. PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="7d918-464">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="7d918-465">Des propriétés supplémentaires sont disponibles en convertissant un ISimulatedHead en ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="7d918-465">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="7d918-466">**Microsoft. PerceptionSimulation. ISimulatedHead2. Eyes**</span><span class="sxs-lookup"><span data-stu-id="7d918-466">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="7d918-467">Récupérez les yeux de l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-467">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="7d918-468">Microsoft. PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="7d918-468">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="7d918-469">Interface décrivant un contrôleur 6-DDL associé à l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-469">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

<span data-ttu-id="7d918-470">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7d918-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="7d918-471">Récupérer la position du nœud par rapport au monde, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-471">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="7d918-472">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Status**</span><span class="sxs-lookup"><span data-stu-id="7d918-472">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="7d918-473">Récupère ou définit l’état actuel du contrôleur.</span><span class="sxs-lookup"><span data-stu-id="7d918-473">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="7d918-474">L’état du contrôleur doit être défini sur une valeur autre que désactivé avant que les appels aux boutons déplacer, faire pivoter ou appuyer ne fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="7d918-474">The controller status must be set to a value other than Off before any calls to move, rotate, or press buttons will succeed.</span></span>

<span data-ttu-id="7d918-475">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. position**</span><span class="sxs-lookup"><span data-stu-id="7d918-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="7d918-476">Récupérez ou définissez la position du contrôleur simulé par rapport à l’homme, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-476">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="7d918-477">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. orientation**</span><span class="sxs-lookup"><span data-stu-id="7d918-477">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="7d918-478">Récupérer ou définir l’orientation du contrôleur simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-478">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="7d918-479">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="7d918-479">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="7d918-480">Déplacer la position du contrôleur simulé par rapport à sa position actuelle, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-480">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="7d918-481">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-481">Parameters</span></span>
* <span data-ttu-id="7d918-482">Traduction : quantité de conversion du contrôleur simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-482">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="7d918-483">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="7d918-483">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="7d918-484">Appuyez sur un bouton sur le contrôleur simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-484">Press a button on the simulated controller.</span></span>  <span data-ttu-id="7d918-485">Il ne sera détecté par le système que si le contrôleur est activé.</span><span class="sxs-lookup"><span data-stu-id="7d918-485">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="7d918-486">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-486">Parameters</span></span>
* <span data-ttu-id="7d918-487">Button-bouton sur lequel appuyer.</span><span class="sxs-lookup"><span data-stu-id="7d918-487">button - The button to press.</span></span>

<span data-ttu-id="7d918-488">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="7d918-488">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="7d918-489">Publiez un bouton sur le contrôleur simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-489">Release a button on the simulated controller.</span></span>  <span data-ttu-id="7d918-490">Il ne sera détecté par le système que si le contrôleur est activé.</span><span class="sxs-lookup"><span data-stu-id="7d918-490">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="7d918-491">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-491">Parameters</span></span>
* <span data-ttu-id="7d918-492">Button-bouton à libérer.</span><span class="sxs-lookup"><span data-stu-id="7d918-492">button - The button to release.</span></span>

<span data-ttu-id="7d918-493">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (sortie float, out float)**</span><span class="sxs-lookup"><span data-stu-id="7d918-493">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="7d918-494">Obtient la position d’un doigt simulé sur le pavé tactile du contrôleur simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-494">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="7d918-495">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-495">Parameters</span></span>
* <span data-ttu-id="7d918-496">x-la position horizontale du doigt.</span><span class="sxs-lookup"><span data-stu-id="7d918-496">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="7d918-497">y : position verticale du doigt.</span><span class="sxs-lookup"><span data-stu-id="7d918-497">y - The vertical position of the finger.</span></span>

<span data-ttu-id="7d918-498">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="7d918-498">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="7d918-499">Définit la position d’un doigt simulé sur le pavé tactile du contrôleur simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-499">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="7d918-500">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-500">Parameters</span></span>
* <span data-ttu-id="7d918-501">x-la position horizontale du doigt.</span><span class="sxs-lookup"><span data-stu-id="7d918-501">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="7d918-502">y : position verticale du doigt.</span><span class="sxs-lookup"><span data-stu-id="7d918-502">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="7d918-503">Microsoft. PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="7d918-503">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="7d918-504">Des propriétés et méthodes supplémentaires sont disponibles en convertissant un ISimulatedSixDofController en ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="7d918-504">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="7d918-505">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (sortie float, out float)**</span><span class="sxs-lookup"><span data-stu-id="7d918-505">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="7d918-506">Obtient la position du stick analogique simulé sur le contrôleur simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-506">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="7d918-507">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-507">Parameters</span></span>
* <span data-ttu-id="7d918-508">x-la position horizontale du stick analogique.</span><span class="sxs-lookup"><span data-stu-id="7d918-508">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="7d918-509">y : position verticale du stick analogique.</span><span class="sxs-lookup"><span data-stu-id="7d918-509">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="7d918-510">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="7d918-510">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="7d918-511">Définissez la position du stick analogique simulé sur le contrôleur simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-511">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="7d918-512">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-512">Parameters</span></span>
* <span data-ttu-id="7d918-513">x-la position horizontale du stick analogique.</span><span class="sxs-lookup"><span data-stu-id="7d918-513">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="7d918-514">y : position verticale du stick analogique.</span><span class="sxs-lookup"><span data-stu-id="7d918-514">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="7d918-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="7d918-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="7d918-516">Récupérez ou définissez le niveau de batterie du contrôleur simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-516">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="7d918-517">La valeur doit être supérieure à 0,0 et inférieure ou égale à 100,0.</span><span class="sxs-lookup"><span data-stu-id="7d918-517">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="7d918-518">Microsoft. PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="7d918-518">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="7d918-519">Interface décrivant les yeux de l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-519">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="7d918-520">**Microsoft. PerceptionSimulation. ISimulatedEyes. rotation**</span><span class="sxs-lookup"><span data-stu-id="7d918-520">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="7d918-521">Récupérer la rotation des yeux simulés.</span><span class="sxs-lookup"><span data-stu-id="7d918-521">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="7d918-522">Les radians positifs pivotent dans le sens des aiguilles d’une montre sur l’axe.</span><span class="sxs-lookup"><span data-stu-id="7d918-522">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="7d918-523">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="7d918-523">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="7d918-524">Faire pivoter les yeux simulés par rapport à sa rotation actuelle.</span><span class="sxs-lookup"><span data-stu-id="7d918-524">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="7d918-525">Les radians positifs pivotent dans le sens des aiguilles d’une montre sur l’axe.</span><span class="sxs-lookup"><span data-stu-id="7d918-525">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="7d918-526">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-526">Parameters</span></span>
* <span data-ttu-id="7d918-527">rotation : quantité à faire pivoter.</span><span class="sxs-lookup"><span data-stu-id="7d918-527">rotation - The amount to rotate.</span></span>

<span data-ttu-id="7d918-528">**Microsoft. PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="7d918-528">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="7d918-529">Récupère ou définit l’état d’étalonnage des yeux simulés.</span><span class="sxs-lookup"><span data-stu-id="7d918-529">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="7d918-530">**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7d918-530">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="7d918-531">Récupérer la position du nœud par rapport au monde, en mètres.</span><span class="sxs-lookup"><span data-stu-id="7d918-531">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="7d918-532">Microsoft. PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="7d918-532">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="7d918-533">Interface pour l’interaction avec un enregistrement unique chargé pour la lecture.</span><span class="sxs-lookup"><span data-stu-id="7d918-533">Interface for interacting with a single recording loaded for playback.</span></span>

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

<span data-ttu-id="7d918-534">**Microsoft. PerceptionSimulation. ISimulationRecording. DataTypes**</span><span class="sxs-lookup"><span data-stu-id="7d918-534">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="7d918-535">Récupère la liste des types de données dans l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="7d918-535">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="7d918-536">**Microsoft. PerceptionSimulation. ISimulationRecording. State**</span><span class="sxs-lookup"><span data-stu-id="7d918-536">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="7d918-537">Récupère l’état actuel de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="7d918-537">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="7d918-538">**Microsoft. PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="7d918-538">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="7d918-539">Démarrez la lecture.</span><span class="sxs-lookup"><span data-stu-id="7d918-539">Start the playback.</span></span> <span data-ttu-id="7d918-540">Si l’enregistrement est suspendu, la lecture reprendra à partir de l’emplacement suspendu ; s’il est arrêté, la lecture démarre au début.</span><span class="sxs-lookup"><span data-stu-id="7d918-540">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="7d918-541">Si elle est déjà en cours d’exécution, cet appel est ignoré.</span><span class="sxs-lookup"><span data-stu-id="7d918-541">If already playing, this call is ignored.</span></span>

<span data-ttu-id="7d918-542">**Microsoft. PerceptionSimulation. ISimulationRecording. pause**</span><span class="sxs-lookup"><span data-stu-id="7d918-542">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="7d918-543">Suspend la lecture à son emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="7d918-543">Pauses the playback at its current location.</span></span> <span data-ttu-id="7d918-544">Si l’enregistrement est arrêté, l’appel est ignoré.</span><span class="sxs-lookup"><span data-stu-id="7d918-544">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="7d918-545">**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="7d918-545">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="7d918-546">Recherche l’enregistrement à l’heure spécifiée (intervalles de 100 nanosecondes à partir du début) et s’interrompt à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="7d918-546">Seeks the recording to the specified time (in 100-nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="7d918-547">Si l’heure se situe au-delà de la fin de l’enregistrement, elle est suspendue à la dernière image.</span><span class="sxs-lookup"><span data-stu-id="7d918-547">If the time is beyond the end of the recording, it's paused at the last frame.</span></span>

<span data-ttu-id="7d918-548">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-548">Parameters</span></span>
* <span data-ttu-id="7d918-549">cycles : heure à laquelle effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="7d918-549">ticks - The time to which to seek.</span></span>

<span data-ttu-id="7d918-550">**Microsoft. PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="7d918-550">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="7d918-551">Arrête la lecture et réinitialise la position au début.</span><span class="sxs-lookup"><span data-stu-id="7d918-551">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="7d918-552">Microsoft. PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="7d918-552">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="7d918-553">Interface pour la réception des modifications d’État pendant la lecture.</span><span class="sxs-lookup"><span data-stu-id="7d918-553">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="7d918-554">**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="7d918-554">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="7d918-555">Appelé lorsque l’état de lecture d’un ISimulationRecording a changé.</span><span class="sxs-lookup"><span data-stu-id="7d918-555">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="7d918-556">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-556">Parameters</span></span>
* <span data-ttu-id="7d918-557">newState : nouvel état de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="7d918-557">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="7d918-558">Microsoft. PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="7d918-558">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="7d918-559">Objet racine pour la création d’objets de simulation de perception.</span><span class="sxs-lookup"><span data-stu-id="7d918-559">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="7d918-560">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="7d918-560">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="7d918-561">Créez sur un objet pour générer des paquets simulés et les fournir au récepteur fourni.</span><span class="sxs-lookup"><span data-stu-id="7d918-561">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="7d918-562">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-562">Parameters</span></span>
* <span data-ttu-id="7d918-563">Sink : récepteur qui recevra tous les paquets générés.</span><span class="sxs-lookup"><span data-stu-id="7d918-563">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="7d918-564">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7d918-564">Return value</span></span>

<span data-ttu-id="7d918-565">Gestionnaire créé.</span><span class="sxs-lookup"><span data-stu-id="7d918-565">The created Manager.</span></span>

<span data-ttu-id="7d918-566">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="7d918-566">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="7d918-567">Créez un récepteur, qui stocke tous les paquets reçus dans un fichier au chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="7d918-567">Create a sink, which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="7d918-568">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-568">Parameters</span></span>
* <span data-ttu-id="7d918-569">chemin d’accès : chemin d’accès du fichier à créer.</span><span class="sxs-lookup"><span data-stu-id="7d918-569">path - The path of the file to create.</span></span>

<span data-ttu-id="7d918-570">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7d918-570">Return value</span></span>

<span data-ttu-id="7d918-571">Récepteur créé.</span><span class="sxs-lookup"><span data-stu-id="7d918-571">The created sink.</span></span>

<span data-ttu-id="7d918-572">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="7d918-572">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="7d918-573">Charge un enregistrement à partir du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="7d918-573">Load a recording from the specified file.</span></span>

<span data-ttu-id="7d918-574">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-574">Parameters</span></span>
* <span data-ttu-id="7d918-575">chemin d’accès : chemin d’accès du fichier à charger.</span><span class="sxs-lookup"><span data-stu-id="7d918-575">path - The path of the file to load.</span></span>
* <span data-ttu-id="7d918-576">Factory : fabrique utilisée par l’enregistrement pour créer un ISimulationStreamSink quand cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="7d918-576">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="7d918-577">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7d918-577">Return value</span></span>

<span data-ttu-id="7d918-578">Enregistrement chargé.</span><span class="sxs-lookup"><span data-stu-id="7d918-578">The loaded recording.</span></span>

<span data-ttu-id="7d918-579">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="7d918-579">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="7d918-580">Charge un enregistrement à partir du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="7d918-580">Load a recording from the specified file.</span></span>

<span data-ttu-id="7d918-581">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-581">Parameters</span></span>
* <span data-ttu-id="7d918-582">chemin d’accès : chemin d’accès du fichier à charger.</span><span class="sxs-lookup"><span data-stu-id="7d918-582">path - The path of the file to load.</span></span>
* <span data-ttu-id="7d918-583">Factory : fabrique utilisée par l’enregistrement pour créer un ISimulationStreamSink quand cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="7d918-583">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="7d918-584">callback : rappel, qui reçoit les mises à jour qui regradent l’état de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="7d918-584">callback - A callback, which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="7d918-585">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7d918-585">Return value</span></span>

<span data-ttu-id="7d918-586">Enregistrement chargé.</span><span class="sxs-lookup"><span data-stu-id="7d918-586">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="7d918-587">Microsoft. PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="7d918-587">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="7d918-588">Décrit les différents types de données de flux.</span><span class="sxs-lookup"><span data-stu-id="7d918-588">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="7d918-589">**Microsoft. PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="7d918-589">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="7d918-590">Valeur de sentinelle utilisée pour indiquer l’absence de type de données de flux.</span><span class="sxs-lookup"><span data-stu-id="7d918-590">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="7d918-591">**Microsoft. PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="7d918-591">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="7d918-592">Flux de données pour la position et l’orientation de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="7d918-592">Stream of data for the position and orientation of the head.</span></span>

<span data-ttu-id="7d918-593">**Microsoft. PerceptionSimulation. StreamDataTypes. mains**</span><span class="sxs-lookup"><span data-stu-id="7d918-593">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="7d918-594">Flux de données pour la position et les gestes des mains.</span><span class="sxs-lookup"><span data-stu-id="7d918-594">Stream of data for the position and gestures of hands.</span></span>

<span data-ttu-id="7d918-595">**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="7d918-595">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="7d918-596">Flux de données pour le mappage spatial de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="7d918-596">Stream of data for spatial mapping of the environment.</span></span>

<span data-ttu-id="7d918-597">**Microsoft. PerceptionSimulation. StreamDataTypes. étalonnage**</span><span class="sxs-lookup"><span data-stu-id="7d918-597">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="7d918-598">Flux de données pour l’étalonnage de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="7d918-598">Stream of data for calibration of the device.</span></span> <span data-ttu-id="7d918-599">Les paquets d’étalonnage sont acceptés uniquement par un système en mode distant.</span><span class="sxs-lookup"><span data-stu-id="7d918-599">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="7d918-600">**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="7d918-600">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="7d918-601">Flux de données pour l’environnement de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="7d918-601">Stream of data for the environment of the device.</span></span>

<span data-ttu-id="7d918-602">**Microsoft. PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="7d918-602">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="7d918-603">Flux de données pour les contrôleurs de mouvement.</span><span class="sxs-lookup"><span data-stu-id="7d918-603">Stream of data for motion controllers.</span></span>

<span data-ttu-id="7d918-604">**Microsoft. PerceptionSimulation. StreamDataTypes. Eyes**</span><span class="sxs-lookup"><span data-stu-id="7d918-604">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="7d918-605">Flux de données avec les yeux de l’homme simulé.</span><span class="sxs-lookup"><span data-stu-id="7d918-605">Stream of data with the eyes of the simulated human.</span></span>

<span data-ttu-id="7d918-606">**Microsoft. PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="7d918-606">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="7d918-607">Flux de données avec la configuration d’affichage de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="7d918-607">Stream of data with the display configuration of the device.</span></span>

<span data-ttu-id="7d918-608">**Microsoft. PerceptionSimulation. StreamDataTypes. All**</span><span class="sxs-lookup"><span data-stu-id="7d918-608">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="7d918-609">Valeur de sentinelle utilisée pour indiquer tous les types de données enregistrés.</span><span class="sxs-lookup"><span data-stu-id="7d918-609">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="7d918-610">Microsoft. PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="7d918-610">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="7d918-611">Objet qui reçoit les paquets de données d’un flux de simulation.</span><span class="sxs-lookup"><span data-stu-id="7d918-611">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="7d918-612">**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint Length, Byte [] paquet)**</span><span class="sxs-lookup"><span data-stu-id="7d918-612">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="7d918-613">Reçoit un paquet unique, qui est typé en interne et avec version.</span><span class="sxs-lookup"><span data-stu-id="7d918-613">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="7d918-614">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d918-614">Parameters</span></span>
* <span data-ttu-id="7d918-615">Length-Longueur du paquet.</span><span class="sxs-lookup"><span data-stu-id="7d918-615">length - The length of the packet.</span></span>
* <span data-ttu-id="7d918-616">paquet : données du paquet.</span><span class="sxs-lookup"><span data-stu-id="7d918-616">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="7d918-617">Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="7d918-617">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="7d918-618">Objet qui crée ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="7d918-618">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="7d918-619">**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="7d918-619">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="7d918-620">Crée une seule instance de ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="7d918-620">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="7d918-621">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7d918-621">Return value</span></span>

<span data-ttu-id="7d918-622">Récepteur créé.</span><span class="sxs-lookup"><span data-stu-id="7d918-622">The created sink.</span></span>
