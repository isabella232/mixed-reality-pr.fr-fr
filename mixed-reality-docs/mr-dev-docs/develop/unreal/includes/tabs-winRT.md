---
ms.openlocfilehash: fd44d63ad502b6807c6aa18ce6fc63493fc254dc
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354440"
---
# <a name="425"></a>[4.25](#tab/425)

Unreal ne compile pas en mode natif le code WinRT dans la version 4,25. c’est donc votre travail de générer un fichier binaire distinct qui peut être consommé par le système de génération d’un peu de temps. Ce didacticiel vous guide tout au long de ce scénario.

## <a name="objectives"></a>Objectifs
- Créer une DLL Windows universelle qui ouvre un FileSaveDialogue
- Lier cette DLL à un projet de jeu inréel
- Enregistrer un fichier sur HoloLens à partir d’un modèle non réel à l’aide de la nouvelle DLL

## <a name="getting-started"></a>Prise en main
1. Vérifiez que tous les [Outils requis](../tutorials/unreal-uxt-ch1.md) sont installés
2. [Créez un nouveau projet inréel](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) et nommez-le **Consumewinrt**
3. Activer les [plug-ins requis](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) pour le développement HoloLens
4. [Configuration pour le déploiement](../tutorials/unreal-uxt-ch6.md) sur un appareil ou un émulateur

## <a name="creating-a-winrt-dll"></a>Création d’une DLL WinRT 
1. Ouvrez un nouveau projet Visual Studio et créez un projet **dll (Windows universel)** dans le même répertoire que le fichier **uproject** du jeu inréel. 

![Création d’une DLL](../images/unreal-winrt-img-01.png)

2. Nommez le projet **HoloLensWinrtDLL** et définissez l’emplacement en tant que sous-répertoire **thirdparty** sur le fichier uproject du jeu inréel. 
    * Sélectionnez **Placer la solution et le projet dans le même répertoire** pour simplifier la recherche des chemins d’accès ultérieurement. 

![Configuration de la DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Une fois le nouveau projet compilé, vous devez prêter une attention particulière aux fichiers CPP et d’en-tête vides, nommés **HoloLensWinrtDLL. cpp** et **HoloLensWinrtDLL. h** , respectivement. L’en-tête est le fichier include qui utilise la DLL dans Unreal, tandis que le CPP contient le corps de toutes les fonctions que vous exportez et inclut tout code WinRT qui, sans cela, ne serait pas en mesure de compiler. 

3. Avant d’ajouter du code, vous devez mettre à jour les propriétés du projet pour vous assurer que le code WinRT dont vous avez besoin peut être compilé : 
    * Cliquez avec le bouton droit sur le projet HoloLensWinrtDLL et sélectionnez **Propriétés** .  
    * Remplacez la liste déroulante **configuration** par **toutes les configurations** et le menu déroulant **plateforme** à **toutes les plateformes** .  
    * Sous **Propriétés de Configuration> C/C++> toutes les options**:
        * Ajouter **await** à **des options supplémentaires** pour nous assurer que nous pouvons attendre des tâches asynchrones  
        * Remplacez la **norme du langage c++** par la norme **ISO C++ 17 (/std : C++ 17)** pour inclure tout code WinRT

![Mise à niveau des propriétés de projet](../images/unreal-winrt-img-03.png)

Votre projet est prêt à mettre à jour la source de la DLL avec le code WinRT qui ouvre une boîte de dialogue de fichier et enregistre un fichier sur le disque HoloLens.  

## <a name="adding-the-dll-code"></a>Ajout du code de la DLL
1. Ouvrez **HoloLensWinrtDLL. h** et ajoutez une fonction dll exportée pour l’utilisation de l’inréel : 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Ouvrez **HoloLensWinrtDLL. cpp** et ajoutez tous les en-têtes qui seront utilisés par la classe :  

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
> Tout le code WinRT est stocké dans **HoloLensWinrtDLL. cpp** , si bien que non réel n’essaie pas d’inclure de code WinRT lors du référencement de l’en-tête. 

3. Toujours dans **HoloLensWinrtDLL. cpp**, ajoutez un corps de fonction pour OpenFileDialogue () et tout le code pris en charge : 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Ajoutez une classe SaveGameManager à **HoloLensWinrtDLL. cpp** pour gérer la boîte de dialogue de fichier et enregistrer le fichier : 

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

5. Générez la solution pour la **version > ARM64** pour générer la dll dans le répertoire enfant ARM64/Release/HoloLensWinrtDLL à partir de la solution dll. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Ajout du fichier binaire WinRT à Unreal 
La liaison et l’utilisation d’une DLL dans unreally requièrent un projet C++. Si vous utilisez un projet Blueprint, il peut être facilement converti en projet C++ en ajoutant une classe C++ :  

1. Dans l’éditeur inréaliste, ouvrez le **fichier > nouvelle classe C++...** et créez un **acteur** nommé **WinrtActor** pour exécuter le code dans la dll : 

![Création d’un acteur](../images/unreal-winrt-img-04.png)

> [!NOTE]
> Une solution a été créée dans le même répertoire que le fichier uproject, avec un nouveau script de compilation nommé source/ConsumeWinRT/ConsumeWinRT. Build. cs.

2. Ouvrez la solution, recherchez le dossier **Games/ConsumeWinRT/source/ConsumeWinRT** , puis ouvrez **ConsumeWinRT.Build.cs**:

![Ouverture du fichier ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Liaison de la DLL
1. Dans **ConsumeWinRT.Build.cs**, ajoutez une propriété pour rechercher le chemin d’accès include pour la dll (répertoire contenant HoloLensWinrtDLL. h). La DLL se trouve dans un répertoire enfant du chemin d’accès include. cette propriété sera donc utilisée comme répertoire racine binaire :

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

2. Dans le constructeur de classe, ajoutez le code suivant pour mettre à jour le chemin d’accès include, liez la nouvelle bibliothèque et Retardez le chargement, puis copiez la DLL dans l’emplacement AppX empaqueté :

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

3. Ouvrez **WinrtActor. h** et ajoutez une définition de fonction, celle qu’un Blueprint appellera : 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. Ouvrez **WinrtActor. cpp** et mettez à jour BeginPlay pour charger la dll : 

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
> La DLL doit être chargée avant d’appeler l’une de ses fonctions.

### <a name="building-the-game"></a>Création du jeu
1. Générez la solution Game pour lancer l’éditeur inréel ouvert dans le projet Game : 
    * Dans l’onglet **Placer les acteurs** , recherchez le nouveau **WinrtActor** et faites-le glisser dans la scène. 
    * Ouvrez le plan de niveau pour exécuter la fonction Blueprint Callable dans **WinrtActor** 

![Placement de la WinrtActor dans la scène](../images/unreal-winrt-img-06.png)

2. Dans le **monde entier**, recherchez le **WindrtActor** précédemment déposé dans la scène et faites-le glisser vers le plan de niveau : 

![Glissement du WinrtActor dans le plan de niveau](../images/unreal-winrt-img-07.png)

3. Dans le plan de niveau, faites glisser le nœud de sortie à partir de WinrtActor, recherchez la **boîte de dialogue Ouvrir le fichier**, puis routez le nœud à partir de n’importe quelle entrée d’utilisateur.  Dans ce cas, la boîte de dialogue Ouvrir un fichier est appelée à partir d’un événement vocal : 

![Configuration des nœuds dans le plan de niveau](../images/unreal-winrt-img-08.png)

4. [Empaquetez ce jeu pour HoloLens](../tutorials/unreal-uxt-ch6.md), déployez-le et exécutez-le.  

Lorsque l’appel d’OpenFileDialogue n’est pas vrai, une boîte de dialogue fichier s’ouvre sur le fichier HoloLens invitant à entrer un nom de fichier. txt.  Une fois le fichier enregistré, accédez à l’onglet **Explorateur de fichiers** dans le portail de l’appareil pour afficher le contenu « Hello WinRT ». 

## <a name="summary"></a>Résumé 

Nous vous encourageons à utiliser le code de ce didacticiel comme point de départ pour consommer du code WinRT dans des conditions inréelles.  Elle permet aux utilisateurs d’enregistrer des fichiers sur le disque HoloLens en utilisant la même boîte de dialogue de fichier que Windows.  Suivez le même processus pour exporter toutes les fonctions supplémentaires à partir de l’en-tête HoloLensWinrtDLL et les utiliser dans Unreal.  Notez le code DLL qui attend un code WinRT asynchrone dans un thread MTA d’arrière-plan, ce qui évite le blocage du thread de jeu inréel. 

# <a name="426"></a>[4,26](#tab/426)

## <a name="the-standard-winrt-apis"></a>API WinRT standard

Le moyen le plus courant et le plus simple d’utiliser WinRT est d’appeler des méthodes à partir de WinSDK. Pour ce faire, ouvrez le fichier YourModule.Build.cs et ajoutez les lignes suivantes :

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

Ensuite, vous devez ajouter les en-têtes WinRT suivants : 

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

Le code WinRT ne peut être compilé que sur les plateformes Win64 et HoloLens, donc l’instruction if empêche les bibliothèques WinRT d’être incluses sur d’autres plateformes. unknwn. h a été ajouté pour l’interface IUnknown. 

Avant d’écrire du code, vous devez désactiver les avertissements courants dans les en-têtes WinRT à l’aide de :

```cpp
#pragma warning(disable : 5205 4265)
```

## <a name="winrt-from-a-nuget-package"></a>WinRT à partir d’un package NuGet

C’est un peu plus compliqué si vous devez ajouter un package NuGet avec la prise en charge WinRT. Dans ce cas, Visual Studio peut effectuer presque tout le travail pour vous, mais pas le système de génération inréel. Heureusement, il n’est pas trop difficile. Vous trouverez ci-dessous un exemple de téléchargement du package Microsoft. MixedReality. QR. Vous pouvez le remplacer par un autre. Assurez-vous simplement de ne pas perdre le fichier winmd et de copier la dll correcte. 

SDK Windows dll de la section précédente sont gérées par le système d’exploitation. Les dll de NuGet doivent être gérées par le code de votre module. Vous devez ajouter du code pour les télécharger, les copier dans le dossier de fichiers binaires et les charger dans la mémoire du processus au démarrage du module.

À la première étape, vous devez ajouter un packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) dans le dossier racine de votre module. Vous devez ajouter tous les packages que vous souhaitez télécharger, y compris toutes leurs dépendances. Ici, j’ai ajouté Microsoft. MixedReality. QR en tant que charge utile principale et deux autres en tant que dépendances. Le format de ce fichier est le même que dans Visual Studio :

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

Vous pouvez maintenant télécharger NuGet, les packages requis ou faire référence à la [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)NuGet.

Ouvrez YourModule.Build.cs et ajoutez le code suivant :

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

Vous devez définir la méthode SafeCopy comme suit :

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

Les dll NuGet doivent être chargées dans votre mémoire de processus Win32 manuellement. Vous devez ajouter le chargement manuel dans la méthode de démarrage de votre module :

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

Enfin, vous pouvez inclure des en-têtes WinRT dans votre code, comme décrit dans la section précédente.