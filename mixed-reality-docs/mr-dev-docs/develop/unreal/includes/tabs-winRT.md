---
ms.openlocfilehash: 6bed33ee9b41a4ee66ce4c1c579d398f0958143d
ms.sourcegitcommit: db01faaf76bccd4f0432cf6b383fefa04ab7a085
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97745708"
---
# <a name="426"></a>[<span data-ttu-id="dd8aa-101">4.26</span><span class="sxs-lookup"><span data-stu-id="dd8aa-101">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="dd8aa-102">API WinRT standard</span><span class="sxs-lookup"><span data-stu-id="dd8aa-102">The standard WinRT APIs</span></span>

<span data-ttu-id="dd8aa-103">Le moyen le plus courant et le plus simple d’utiliser WinRT est d’appeler des méthodes à partir de WinSDK.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-103">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="dd8aa-104">Pour ce faire, ouvrez le fichier YourModule.Build.cs et ajoutez les lignes suivantes :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-104">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```csharp
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

<span data-ttu-id="dd8aa-105">Ensuite, vous devez ajouter les en-têtes WinRT suivants :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-105">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
//Before writing any code, you need to disable common warnings in WinRT headers
#pragma warning(disable : 5205 4265 4268 4946)

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

<span data-ttu-id="dd8aa-106">Le code WinRT ne peut être compilé que sur les plateformes Win64 et HoloLens, donc l’instruction if empêche les bibliothèques WinRT d’être incluses sur d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-106">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="dd8aa-107">unknwn. h a été ajouté pour l’interface IUnknown.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-107">unknwn.h was added for having the IUnknown interface.</span></span> 


## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="dd8aa-108">WinRT à partir d’un package NuGet</span><span class="sxs-lookup"><span data-stu-id="dd8aa-108">WinRT from a NuGet package</span></span>

<span data-ttu-id="dd8aa-109">C’est un peu plus compliqué si vous devez ajouter un package NuGet avec la prise en charge WinRT.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-109">It’s a little more complicated if you need to add a NuGet package with WinRT support.</span></span> <span data-ttu-id="dd8aa-110">Dans ce cas, Visual Studio peut effectuer presque tout le travail pour vous, mais pas le système de génération inréel.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-110">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="dd8aa-111">Heureusement, il n’est pas trop difficile.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-111">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="dd8aa-112">Vous trouverez ci-dessous un exemple de téléchargement du package Microsoft. MixedReality. QR.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-112">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="dd8aa-113">Vous pouvez le remplacer par un autre, vérifiez simplement que vous ne perdez pas le fichier winmd et copiez la dll correcte.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-113">You can replace it with another, just make sure you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="dd8aa-114">SDK Windows dll de la section précédente sont gérées par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-114">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="dd8aa-115">Les dll de NuGet doivent être gérées par le code de votre module.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-115">NuGet’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="dd8aa-116">Nous vous recommandons d’ajouter du code pour les télécharger, de les copier dans le dossier de fichiers binaires et de charger dans la mémoire du processus au démarrage du module.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-116">We recommend adding code to download them, copying into binaries folder, and load into the process memory at the module startup.</span></span>

<span data-ttu-id="dd8aa-117">À la première étape, vous devez ajouter un packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) dans le dossier racine de votre module.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-117">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="dd8aa-118">Vous devez ajouter tous les packages que vous souhaitez télécharger, y compris toutes leurs dépendances.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-118">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="dd8aa-119">Ici, j’ai ajouté Microsoft. MixedReality. QR en tant que charge utile principale et deux autres en tant que dépendances.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-119">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="dd8aa-120">Le format de ce fichier est le même que dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-120">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="dd8aa-121">Vous pouvez maintenant télécharger NuGet, les packages requis ou faire référence à la [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)NuGet.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-121">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="dd8aa-122">Ouvrez YourModule.Build.cs et ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-122">Open YourModule.Build.cs and add the following code:</span></span>

```csharp
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
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
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
        // fall back to default WinSDK headers
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
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
        string VCRTForwardersPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
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

<span data-ttu-id="dd8aa-123">Vous devez définir la méthode SafeCopy comme suit :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-123">You'll need to define the SafeCopy method as follows:</span></span>

```csharp
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

<span data-ttu-id="dd8aa-124">Les dll NuGet doivent être chargées dans votre mémoire de processus Win32 manuellement. Nous vous recommandons d’ajouter le chargement manuel dans la méthode de démarrage de votre module :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-124">NuGet DLLs needs to load into your Win32 process memory manually; we recommend adding manual loading into the startup method of your module:</span></span>

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

<span data-ttu-id="dd8aa-125">Enfin, vous pouvez inclure des en-têtes WinRT dans votre code, comme décrit dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-125">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>

# <a name="425"></a>[<span data-ttu-id="dd8aa-126">4.25</span><span class="sxs-lookup"><span data-stu-id="dd8aa-126">4.25</span></span>](#tab/425)

<span data-ttu-id="dd8aa-127">Non réel ne compile pas en mode natif le code WinRT dans la version 4,25. c’est donc votre travail de générer un fichier binaire distinct que le système de génération inréel peut consommer.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-127">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary that Unreal’s build system can consume.</span></span> 

## <a name="objectives"></a><span data-ttu-id="dd8aa-128">Objectifs</span><span class="sxs-lookup"><span data-stu-id="dd8aa-128">Objectives</span></span>

- <span data-ttu-id="dd8aa-129">Créer une DLL Windows universelle qui ouvre un FileSaveDialogue</span><span class="sxs-lookup"><span data-stu-id="dd8aa-129">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="dd8aa-130">Lier cette DLL à un projet de jeu inréel</span><span class="sxs-lookup"><span data-stu-id="dd8aa-130">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="dd8aa-131">Enregistrer un fichier sur HoloLens à partir d’un modèle non réel à l’aide de la nouvelle DLL</span><span class="sxs-lookup"><span data-stu-id="dd8aa-131">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="dd8aa-132">Prise en main</span><span class="sxs-lookup"><span data-stu-id="dd8aa-132">Getting started</span></span>

1. <span data-ttu-id="dd8aa-133">Vérifiez que tous les [Outils requis](../tutorials/unreal-uxt-ch1.md) sont installés</span><span class="sxs-lookup"><span data-stu-id="dd8aa-133">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="dd8aa-134">[Créez un nouveau projet inréel](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) et nommez-le **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="dd8aa-134">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="dd8aa-135">Activer les [plug-ins requis](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) pour le développement HoloLens</span><span class="sxs-lookup"><span data-stu-id="dd8aa-135">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="dd8aa-136">[Configuration pour le déploiement](../tutorials/unreal-uxt-ch6.md) sur un appareil ou un émulateur</span><span class="sxs-lookup"><span data-stu-id="dd8aa-136">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="dd8aa-137">Création d’une DLL WinRT</span><span class="sxs-lookup"><span data-stu-id="dd8aa-137">Creating a WinRT DLL</span></span> 

1. <span data-ttu-id="dd8aa-138">Ouvrez un nouveau projet Visual Studio et créez un projet **dll (Windows universel)** dans le même répertoire que le fichier **uproject** du jeu inréel.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-138">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory as the Unreal game’s **uproject** file.</span></span> 

![Création d’une DLL](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="dd8aa-140">Nommez le projet **HoloLensWinrtDLL** et définissez l’emplacement en tant que sous-répertoire **thirdparty** sur le fichier uproject du jeu inréel.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-140">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="dd8aa-141">Sélectionnez **Placer la solution et le projet dans le même répertoire** pour simplifier la recherche des chemins d’accès ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-141">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Configuration de la DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="dd8aa-143">Une fois le nouveau projet compilé, portez une attention particulière aux fichiers d’en-tête et CPP vides, appelés respectivement **HoloLensWinrtDLL. cpp** et **HoloLensWinrtDLL. h** .</span><span class="sxs-lookup"><span data-stu-id="dd8aa-143">After the new project compiles, pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="dd8aa-144">L’en-tête est le fichier include qui utilise la DLL dans Unreal, tandis que le CPP contient le corps de toutes les fonctions que vous exportez et inclut tout code WinRT qui, sans cela, ne serait pas en mesure de compiler.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-144">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="dd8aa-145">Avant d’ajouter du code, vous devez mettre à jour les propriétés du projet pour vous assurer que le code WinRT dont vous avez besoin peut être compilé :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-145">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="dd8aa-146">Cliquez avec le bouton droit sur le projet HoloLensWinrtDLL et sélectionnez **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="dd8aa-146">Right-click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="dd8aa-147">Remplacez la liste déroulante **configuration** par **toutes les configurations** et le menu déroulant **plateforme** à **toutes les plateformes** .</span><span class="sxs-lookup"><span data-stu-id="dd8aa-147">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="dd8aa-148">Sous **Propriétés de Configuration> C/C++> toutes les options**:</span><span class="sxs-lookup"><span data-stu-id="dd8aa-148">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="dd8aa-149">Ajouter **await** à **des options supplémentaires** pour nous assurer que nous pouvons attendre des tâches asynchrones</span><span class="sxs-lookup"><span data-stu-id="dd8aa-149">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="dd8aa-150">Remplacez la **norme du langage c++** par la norme **ISO C++ 17 (/std : C++ 17)** pour inclure tout code WinRT</span><span class="sxs-lookup"><span data-stu-id="dd8aa-150">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Mise à niveau des propriétés de projet](../images/unreal-winrt-img-03.png)

<span data-ttu-id="dd8aa-152">Votre projet est prêt à mettre à jour la source de la DLL avec le code WinRT qui ouvre une boîte de dialogue de fichier et enregistre un fichier sur le disque HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-152">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="dd8aa-153">Ajout du code de la DLL</span><span class="sxs-lookup"><span data-stu-id="dd8aa-153">Adding the DLL code</span></span>

1. <span data-ttu-id="dd8aa-154">Ouvrez **HoloLensWinrtDLL. h** et ajoutez une fonction dll exportée pour l’utilisation de l’inréel :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-154">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="dd8aa-155">Ouvrez **HoloLensWinrtDLL. cpp** et ajoutez tous les en-têtes qui seront utilisés par la classe :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-155">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="dd8aa-156">Tout le code WinRT est stocké dans **HoloLensWinrtDLL. cpp** , si bien que non réel n’essaie pas d’inclure de code WinRT lors du référencement de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-156">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="dd8aa-157">Toujours dans **HoloLensWinrtDLL. cpp**, ajoutez un corps de fonction pour OpenFileDialogue () et tout le code pris en charge :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-157">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="dd8aa-158">Ajoutez une classe SaveGameManager à **HoloLensWinrtDLL. cpp** pour gérer la boîte de dialogue de fichier et enregistrer le fichier :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-158">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="dd8aa-159">Générez la solution pour la **version > ARM64** pour générer la dll dans le répertoire enfant ARM64/Release/HoloLensWinrtDLL à partir de la solution dll.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-159">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="dd8aa-160">Ajout du fichier binaire WinRT à Unreal</span><span class="sxs-lookup"><span data-stu-id="dd8aa-160">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="dd8aa-161">La liaison et l’utilisation d’une DLL dans unreally requièrent un projet C++.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-161">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="dd8aa-162">Si vous utilisez un projet Blueprint, il peut être facilement converti en projet C++ en ajoutant une classe C++ :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-162">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="dd8aa-163">Dans l’éditeur inréaliste, ouvrez le **fichier > nouvelle classe C++...**</span><span class="sxs-lookup"><span data-stu-id="dd8aa-163">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="dd8aa-164">et créez un **acteur** nommé **WinrtActor** pour exécuter le code dans la dll :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-164">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Création d’un acteur](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="dd8aa-166">Une solution a été créée dans le même répertoire que le fichier uproject, avec un nouveau script de compilation nommé source/ConsumeWinRT/ConsumeWinRT. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-166">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="dd8aa-167">Ouvrez la solution, recherchez le dossier **Games/ConsumeWinRT/source/ConsumeWinRT** , puis ouvrez **ConsumeWinRT.Build.cs**:</span><span class="sxs-lookup"><span data-stu-id="dd8aa-167">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Ouverture du fichier ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="dd8aa-169">Liaison de la DLL</span><span class="sxs-lookup"><span data-stu-id="dd8aa-169">Linking the DLL</span></span>
1. <span data-ttu-id="dd8aa-170">Dans **ConsumeWinRT.Build.cs**, ajoutez une propriété pour rechercher le chemin d’accès include pour la dll (répertoire contenant HoloLensWinrtDLL. h).</span><span class="sxs-lookup"><span data-stu-id="dd8aa-170">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="dd8aa-171">La DLL se trouve dans un répertoire enfant du chemin d’accès include. cette propriété sera donc utilisée comme répertoire racine binaire :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-171">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="dd8aa-172">Dans le constructeur de classe, ajoutez le code suivant pour mettre à jour le chemin d’accès include, liez la nouvelle bibliothèque et Retardez le chargement, puis copiez la DLL dans l’emplacement AppX empaqueté :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-172">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="dd8aa-173">Ouvrez **WinrtActor. h** et ajoutez une définition de fonction, celle qu’un Blueprint appellera :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-173">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="dd8aa-174">Ouvrez **WinrtActor. cpp** et mettez à jour BeginPlay pour charger la dll :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-174">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="dd8aa-175">La DLL doit être chargée avant d’appeler l’une de ses fonctions.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-175">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="dd8aa-176">Création du jeu</span><span class="sxs-lookup"><span data-stu-id="dd8aa-176">Building the game</span></span>
1. <span data-ttu-id="dd8aa-177">Générez la solution Game pour lancer l’éditeur inréel ouvert dans le projet Game :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-177">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="dd8aa-178">Dans l’onglet **Placer les acteurs** , recherchez le nouveau **WinrtActor** et faites-le glisser dans la scène.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-178">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="dd8aa-179">Ouvrez le plan de niveau pour exécuter la fonction Blueprint Callable dans **WinrtActor**</span><span class="sxs-lookup"><span data-stu-id="dd8aa-179">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Placement de la WinrtActor dans la scène](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="dd8aa-181">Dans le **monde entier**, recherchez le **WindrtActor** précédemment déposé dans la scène et faites-le glisser vers le plan de niveau :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-181">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Glissement du WinrtActor dans le plan de niveau](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="dd8aa-183">Dans le plan de niveau, faites glisser le nœud de sortie à partir de WinrtActor, recherchez la **boîte de dialogue Ouvrir le fichier**, puis routez le nœud à partir de n’importe quelle entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-183">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="dd8aa-184">Dans ce cas, la boîte de dialogue Ouvrir un fichier est appelée à partir d’un événement vocal :</span><span class="sxs-lookup"><span data-stu-id="dd8aa-184">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Configuration des nœuds dans le plan de niveau](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="dd8aa-186">[Empaquetez ce jeu pour HoloLens](../tutorials/unreal-uxt-ch6.md), déployez-le et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-186">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="dd8aa-187">Lorsque l’appel d’OpenFileDialogue n’est pas vrai, une boîte de dialogue fichier s’ouvre sur le fichier HoloLens invitant à entrer un nom de fichier. txt.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-187">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="dd8aa-188">Une fois le fichier enregistré, accédez à l’onglet **Explorateur de fichiers** dans le portail de l’appareil pour afficher le contenu « Hello WinRT ».</span><span class="sxs-lookup"><span data-stu-id="dd8aa-188">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="dd8aa-189">Résumé</span><span class="sxs-lookup"><span data-stu-id="dd8aa-189">Summary</span></span> 

<span data-ttu-id="dd8aa-190">Nous vous encourageons à utiliser ce didacticiel comme point de départ pour consommer du code WinRT dans des conditions imréelless lorsque vous devez enregistrer des fichiers sur le disque HoloLens en utilisant la même boîte de dialogue de fichier que Windows.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-190">We encourage you to use this tutorial as a starting point for consuming WinRT code in Unreal when you need to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="dd8aa-191">Le même processus s’applique à l’exportation de fonctions supplémentaires à partir de l’en-tête HoloLensWinrtDLL et utilisées dans des conditions inréelless.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-191">The same process applies to exporting additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="dd8aa-192">Portez une attention particulière au code DLL qui attend le code asynchrone asynchrone dans un thread MTA en arrière-plan, ce qui évite le blocage du thread de jeu inréel.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-192">Pay special attention to the DLL code that waits on async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

