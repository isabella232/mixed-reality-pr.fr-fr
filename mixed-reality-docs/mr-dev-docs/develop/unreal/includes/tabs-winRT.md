---
ms.openlocfilehash: fd44d63ad502b6807c6aa18ce6fc63493fc254dc
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354440"
---
# <a name="425"></a>[<span data-ttu-id="b5869-101">4.25</span><span class="sxs-lookup"><span data-stu-id="b5869-101">4.25</span></span>](#tab/425)

<span data-ttu-id="b5869-102">Unreal ne compile pas en mode natif le code WinRT dans la version 4,25. c’est donc votre travail de générer un fichier binaire distinct qui peut être consommé par le système de génération d’un peu de temps.</span><span class="sxs-lookup"><span data-stu-id="b5869-102">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="b5869-103">Ce didacticiel vous guide tout au long de ce scénario.</span><span class="sxs-lookup"><span data-stu-id="b5869-103">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="b5869-104">Objectifs</span><span class="sxs-lookup"><span data-stu-id="b5869-104">Objectives</span></span>
- <span data-ttu-id="b5869-105">Créer une DLL Windows universelle qui ouvre un FileSaveDialogue</span><span class="sxs-lookup"><span data-stu-id="b5869-105">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="b5869-106">Lier cette DLL à un projet de jeu inréel</span><span class="sxs-lookup"><span data-stu-id="b5869-106">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="b5869-107">Enregistrer un fichier sur HoloLens à partir d’un modèle non réel à l’aide de la nouvelle DLL</span><span class="sxs-lookup"><span data-stu-id="b5869-107">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="b5869-108">Prise en main</span><span class="sxs-lookup"><span data-stu-id="b5869-108">Getting started</span></span>
1. <span data-ttu-id="b5869-109">Vérifiez que tous les [Outils requis](../tutorials/unreal-uxt-ch1.md) sont installés</span><span class="sxs-lookup"><span data-stu-id="b5869-109">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="b5869-110">[Créez un nouveau projet inréel](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) et nommez-le **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="b5869-110">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="b5869-111">Activer les [plug-ins requis](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) pour le développement HoloLens</span><span class="sxs-lookup"><span data-stu-id="b5869-111">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="b5869-112">[Configuration pour le déploiement](../tutorials/unreal-uxt-ch6.md) sur un appareil ou un émulateur</span><span class="sxs-lookup"><span data-stu-id="b5869-112">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="b5869-113">Création d’une DLL WinRT</span><span class="sxs-lookup"><span data-stu-id="b5869-113">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="b5869-114">Ouvrez un nouveau projet Visual Studio et créez un projet **dll (Windows universel)** dans le même répertoire que le fichier **uproject** du jeu inréel.</span><span class="sxs-lookup"><span data-stu-id="b5869-114">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![Création d’une DLL](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="b5869-116">Nommez le projet **HoloLensWinrtDLL** et définissez l’emplacement en tant que sous-répertoire **thirdparty** sur le fichier uproject du jeu inréel.</span><span class="sxs-lookup"><span data-stu-id="b5869-116">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="b5869-117">Sélectionnez **Placer la solution et le projet dans le même répertoire** pour simplifier la recherche des chemins d’accès ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="b5869-117">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Configuration de la DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="b5869-119">Une fois le nouveau projet compilé, vous devez prêter une attention particulière aux fichiers CPP et d’en-tête vides, nommés **HoloLensWinrtDLL. cpp** et **HoloLensWinrtDLL. h** , respectivement.</span><span class="sxs-lookup"><span data-stu-id="b5869-119">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="b5869-120">L’en-tête est le fichier include qui utilise la DLL dans Unreal, tandis que le CPP contient le corps de toutes les fonctions que vous exportez et inclut tout code WinRT qui, sans cela, ne serait pas en mesure de compiler.</span><span class="sxs-lookup"><span data-stu-id="b5869-120">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="b5869-121">Avant d’ajouter du code, vous devez mettre à jour les propriétés du projet pour vous assurer que le code WinRT dont vous avez besoin peut être compilé :</span><span class="sxs-lookup"><span data-stu-id="b5869-121">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="b5869-122">Cliquez avec le bouton droit sur le projet HoloLensWinrtDLL et sélectionnez **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="b5869-122">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="b5869-123">Remplacez la liste déroulante **configuration** par **toutes les configurations** et le menu déroulant **plateforme** à **toutes les plateformes** .</span><span class="sxs-lookup"><span data-stu-id="b5869-123">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="b5869-124">Sous **Propriétés de Configuration> C/C++> toutes les options**:</span><span class="sxs-lookup"><span data-stu-id="b5869-124">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="b5869-125">Ajouter **await** à **des options supplémentaires** pour nous assurer que nous pouvons attendre des tâches asynchrones</span><span class="sxs-lookup"><span data-stu-id="b5869-125">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="b5869-126">Remplacez la **norme du langage c++** par la norme **ISO C++ 17 (/std : C++ 17)** pour inclure tout code WinRT</span><span class="sxs-lookup"><span data-stu-id="b5869-126">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Mise à niveau des propriétés de projet](../images/unreal-winrt-img-03.png)

<span data-ttu-id="b5869-128">Votre projet est prêt à mettre à jour la source de la DLL avec le code WinRT qui ouvre une boîte de dialogue de fichier et enregistre un fichier sur le disque HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5869-128">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="b5869-129">Ajout du code de la DLL</span><span class="sxs-lookup"><span data-stu-id="b5869-129">Adding the DLL code</span></span>
1. <span data-ttu-id="b5869-130">Ouvrez **HoloLensWinrtDLL. h** et ajoutez une fonction dll exportée pour l’utilisation de l’inréel :</span><span class="sxs-lookup"><span data-stu-id="b5869-130">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="b5869-131">Ouvrez **HoloLensWinrtDLL. cpp** et ajoutez tous les en-têtes qui seront utilisés par la classe :</span><span class="sxs-lookup"><span data-stu-id="b5869-131">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> <span data-ttu-id="b5869-132">Tout le code WinRT est stocké dans **HoloLensWinrtDLL. cpp** , si bien que non réel n’essaie pas d’inclure de code WinRT lors du référencement de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="b5869-132">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="b5869-133">Toujours dans **HoloLensWinrtDLL. cpp**, ajoutez un corps de fonction pour OpenFileDialogue () et tout le code pris en charge :</span><span class="sxs-lookup"><span data-stu-id="b5869-133">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="b5869-134">Ajoutez une classe SaveGameManager à **HoloLensWinrtDLL. cpp** pour gérer la boîte de dialogue de fichier et enregistrer le fichier :</span><span class="sxs-lookup"><span data-stu-id="b5869-134">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. <span data-ttu-id="b5869-135">Générez la solution pour la **version > ARM64** pour générer la dll dans le répertoire enfant ARM64/Release/HoloLensWinrtDLL à partir de la solution dll.</span><span class="sxs-lookup"><span data-stu-id="b5869-135">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="b5869-136">Ajout du fichier binaire WinRT à Unreal</span><span class="sxs-lookup"><span data-stu-id="b5869-136">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="b5869-137">La liaison et l’utilisation d’une DLL dans unreally requièrent un projet C++.</span><span class="sxs-lookup"><span data-stu-id="b5869-137">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="b5869-138">Si vous utilisez un projet Blueprint, il peut être facilement converti en projet C++ en ajoutant une classe C++ :</span><span class="sxs-lookup"><span data-stu-id="b5869-138">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="b5869-139">Dans l’éditeur inréaliste, ouvrez le **fichier > nouvelle classe C++...**</span><span class="sxs-lookup"><span data-stu-id="b5869-139">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="b5869-140">et créez un **acteur** nommé **WinrtActor** pour exécuter le code dans la dll :</span><span class="sxs-lookup"><span data-stu-id="b5869-140">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Création d’un acteur](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="b5869-142">Une solution a été créée dans le même répertoire que le fichier uproject, avec un nouveau script de compilation nommé source/ConsumeWinRT/ConsumeWinRT. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="b5869-142">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="b5869-143">Ouvrez la solution, recherchez le dossier **Games/ConsumeWinRT/source/ConsumeWinRT** , puis ouvrez **ConsumeWinRT.Build.cs**:</span><span class="sxs-lookup"><span data-stu-id="b5869-143">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Ouverture du fichier ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="b5869-145">Liaison de la DLL</span><span class="sxs-lookup"><span data-stu-id="b5869-145">Linking the DLL</span></span>
1. <span data-ttu-id="b5869-146">Dans **ConsumeWinRT.Build.cs**, ajoutez une propriété pour rechercher le chemin d’accès include pour la dll (répertoire contenant HoloLensWinrtDLL. h).</span><span class="sxs-lookup"><span data-stu-id="b5869-146">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="b5869-147">La DLL se trouve dans un répertoire enfant du chemin d’accès include. cette propriété sera donc utilisée comme répertoire racine binaire :</span><span class="sxs-lookup"><span data-stu-id="b5869-147">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. <span data-ttu-id="b5869-148">Dans le constructeur de classe, ajoutez le code suivant pour mettre à jour le chemin d’accès include, liez la nouvelle bibliothèque et Retardez le chargement, puis copiez la DLL dans l’emplacement AppX empaqueté :</span><span class="sxs-lookup"><span data-stu-id="b5869-148">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. <span data-ttu-id="b5869-149">Ouvrez **WinrtActor. h** et ajoutez une définition de fonction, celle qu’un Blueprint appellera :</span><span class="sxs-lookup"><span data-stu-id="b5869-149">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="b5869-150">Ouvrez **WinrtActor. cpp** et mettez à jour BeginPlay pour charger la dll :</span><span class="sxs-lookup"><span data-stu-id="b5869-150">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="b5869-151">La DLL doit être chargée avant d’appeler l’une de ses fonctions.</span><span class="sxs-lookup"><span data-stu-id="b5869-151">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="b5869-152">Création du jeu</span><span class="sxs-lookup"><span data-stu-id="b5869-152">Building the game</span></span>
1. <span data-ttu-id="b5869-153">Générez la solution Game pour lancer l’éditeur inréel ouvert dans le projet Game :</span><span class="sxs-lookup"><span data-stu-id="b5869-153">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="b5869-154">Dans l’onglet **Placer les acteurs** , recherchez le nouveau **WinrtActor** et faites-le glisser dans la scène.</span><span class="sxs-lookup"><span data-stu-id="b5869-154">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="b5869-155">Ouvrez le plan de niveau pour exécuter la fonction Blueprint Callable dans **WinrtActor**</span><span class="sxs-lookup"><span data-stu-id="b5869-155">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Placement de la WinrtActor dans la scène](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="b5869-157">Dans le **monde entier**, recherchez le **WindrtActor** précédemment déposé dans la scène et faites-le glisser vers le plan de niveau :</span><span class="sxs-lookup"><span data-stu-id="b5869-157">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Glissement du WinrtActor dans le plan de niveau](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="b5869-159">Dans le plan de niveau, faites glisser le nœud de sortie à partir de WinrtActor, recherchez la **boîte de dialogue Ouvrir le fichier**, puis routez le nœud à partir de n’importe quelle entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b5869-159">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="b5869-160">Dans ce cas, la boîte de dialogue Ouvrir un fichier est appelée à partir d’un événement vocal :</span><span class="sxs-lookup"><span data-stu-id="b5869-160">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Configuration des nœuds dans le plan de niveau](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="b5869-162">[Empaquetez ce jeu pour HoloLens](../tutorials/unreal-uxt-ch6.md), déployez-le et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="b5869-162">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="b5869-163">Lorsque l’appel d’OpenFileDialogue n’est pas vrai, une boîte de dialogue fichier s’ouvre sur le fichier HoloLens invitant à entrer un nom de fichier. txt.</span><span class="sxs-lookup"><span data-stu-id="b5869-163">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="b5869-164">Une fois le fichier enregistré, accédez à l’onglet **Explorateur de fichiers** dans le portail de l’appareil pour afficher le contenu « Hello WinRT ».</span><span class="sxs-lookup"><span data-stu-id="b5869-164">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="b5869-165">Résumé</span><span class="sxs-lookup"><span data-stu-id="b5869-165">Summary</span></span> 

<span data-ttu-id="b5869-166">Nous vous encourageons à utiliser le code de ce didacticiel comme point de départ pour consommer du code WinRT dans des conditions inréelles.</span><span class="sxs-lookup"><span data-stu-id="b5869-166">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="b5869-167">Elle permet aux utilisateurs d’enregistrer des fichiers sur le disque HoloLens en utilisant la même boîte de dialogue de fichier que Windows.</span><span class="sxs-lookup"><span data-stu-id="b5869-167">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="b5869-168">Suivez le même processus pour exporter toutes les fonctions supplémentaires à partir de l’en-tête HoloLensWinrtDLL et les utiliser dans Unreal.</span><span class="sxs-lookup"><span data-stu-id="b5869-168">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="b5869-169">Notez le code DLL qui attend un code WinRT asynchrone dans un thread MTA d’arrière-plan, ce qui évite le blocage du thread de jeu inréel.</span><span class="sxs-lookup"><span data-stu-id="b5869-169">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

# <a name="426"></a>[<span data-ttu-id="b5869-170">4,26</span><span class="sxs-lookup"><span data-stu-id="b5869-170">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="b5869-171">API WinRT standard</span><span class="sxs-lookup"><span data-stu-id="b5869-171">The standard WinRT APIs</span></span>

<span data-ttu-id="b5869-172">Le moyen le plus courant et le plus simple d’utiliser WinRT est d’appeler des méthodes à partir de WinSDK.</span><span class="sxs-lookup"><span data-stu-id="b5869-172">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="b5869-173">Pour ce faire, ouvrez le fichier YourModule.Build.cs et ajoutez les lignes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5869-173">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```cpp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

<span data-ttu-id="b5869-174">Ensuite, vous devez ajouter les en-têtes WinRT suivants :</span><span class="sxs-lookup"><span data-stu-id="b5869-174">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

<span data-ttu-id="b5869-175">Le code WinRT ne peut être compilé que sur les plateformes Win64 et HoloLens, donc l’instruction if empêche les bibliothèques WinRT d’être incluses sur d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="b5869-175">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="b5869-176">unknwn. h a été ajouté pour l’interface IUnknown.</span><span class="sxs-lookup"><span data-stu-id="b5869-176">unknwn.h was added for having the IUnknown interface.</span></span> 

<span data-ttu-id="b5869-177">Avant d’écrire du code, vous devez désactiver les avertissements courants dans les en-têtes WinRT à l’aide de :</span><span class="sxs-lookup"><span data-stu-id="b5869-177">Before writing any code, you need to disable common warnings in WinRT headers by using:</span></span>

```cpp
#pragma warning(disable : 5205 4265)
```

## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="b5869-178">WinRT à partir d’un package NuGet</span><span class="sxs-lookup"><span data-stu-id="b5869-178">WinRT from a NuGet package</span></span>

<span data-ttu-id="b5869-179">C’est un peu plus compliqué si vous devez ajouter un package NuGet avec la prise en charge WinRT.</span><span class="sxs-lookup"><span data-stu-id="b5869-179">It’s a little more complicated if you need to add a nuget package with WinRT support.</span></span> <span data-ttu-id="b5869-180">Dans ce cas, Visual Studio peut effectuer presque tout le travail pour vous, mais pas le système de génération inréel.</span><span class="sxs-lookup"><span data-stu-id="b5869-180">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="b5869-181">Heureusement, il n’est pas trop difficile.</span><span class="sxs-lookup"><span data-stu-id="b5869-181">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="b5869-182">Vous trouverez ci-dessous un exemple de téléchargement du package Microsoft. MixedReality. QR.</span><span class="sxs-lookup"><span data-stu-id="b5869-182">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="b5869-183">Vous pouvez le remplacer par un autre. Assurez-vous simplement de ne pas perdre le fichier winmd et de copier la dll correcte.</span><span class="sxs-lookup"><span data-stu-id="b5869-183">You can replace it with another, just make sure that you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="b5869-184">SDK Windows dll de la section précédente sont gérées par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b5869-184">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="b5869-185">Les dll de NuGet doivent être gérées par le code de votre module.</span><span class="sxs-lookup"><span data-stu-id="b5869-185">Nuget’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="b5869-186">Vous devez ajouter du code pour les télécharger, les copier dans le dossier de fichiers binaires et les charger dans la mémoire du processus au démarrage du module.</span><span class="sxs-lookup"><span data-stu-id="b5869-186">You should add code to download them, copy into binaries folder and load into the process memory at the module startup.</span></span>

<span data-ttu-id="b5869-187">À la première étape, vous devez ajouter un packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) dans le dossier racine de votre module.</span><span class="sxs-lookup"><span data-stu-id="b5869-187">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="b5869-188">Vous devez ajouter tous les packages que vous souhaitez télécharger, y compris toutes leurs dépendances.</span><span class="sxs-lookup"><span data-stu-id="b5869-188">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="b5869-189">Ici, j’ai ajouté Microsoft. MixedReality. QR en tant que charge utile principale et deux autres en tant que dépendances.</span><span class="sxs-lookup"><span data-stu-id="b5869-189">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="b5869-190">Le format de ce fichier est le même que dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="b5869-190">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="b5869-191">Vous pouvez maintenant télécharger NuGet, les packages requis ou faire référence à la [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)NuGet.</span><span class="sxs-lookup"><span data-stu-id="b5869-191">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="b5869-192">Ouvrez YourModule.Build.cs et ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b5869-192">Open YourModule.Build.cs and add the following code:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

            PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
                                myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);

    }
    else
    {
        // fall to default WinSDK headers
                        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
            }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }
```

<span data-ttu-id="b5869-193">Vous devez définir la méthode SafeCopy comme suit :</span><span class="sxs-lookup"><span data-stu-id="b5869-193">You'll need to define the SafeCopy method as follows:</span></span>

```cpp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

<span data-ttu-id="b5869-194">Les dll NuGet doivent être chargées dans votre mémoire de processus Win32 manuellement.</span><span class="sxs-lookup"><span data-stu-id="b5869-194">Nuget DLLs needs to load into your Win32 process memory manually.</span></span> <span data-ttu-id="b5869-195">Vous devez ajouter le chargement manuel dans la méthode de démarrage de votre module :</span><span class="sxs-lookup"><span data-stu-id="b5869-195">You should add manual loading into the startup method of your module:</span></span>

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

<span data-ttu-id="b5869-196">Enfin, vous pouvez inclure des en-têtes WinRT dans votre code, comme décrit dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="b5869-196">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>