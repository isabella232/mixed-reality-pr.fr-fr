---
title: Publication sur le Microsoft Store
description: ''
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, documentation, guides, fonctionnalités, casque de réalité mixte, casque de réalité mixte Windows, casque de réalité virtuelle, publication, distribution, Microsoft Store
ms.openlocfilehash: 37a17ba4a691ca8db6ce447abd485293454b8ae3
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96583910"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="1c70a-103">Publication sur le Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="1c70a-103">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="1c70a-104">Quand vous êtes prêt à lancer votre application, vous devez mettre à jour quelques paramètres du projet avant de la soumettre au Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="1c70a-104">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="1c70a-105">Tous ces paramètres ont des valeurs par défaut, que vous devez toutefois changer pour la production afin de mieux représenter l’application.</span><span class="sxs-lookup"><span data-stu-id="1c70a-105">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="1c70a-106">Paramètres du projet pour l’empaquetage du Store</span><span class="sxs-lookup"><span data-stu-id="1c70a-106">Project settings for the store packaging</span></span>

1. <span data-ttu-id="1c70a-107">Tout d’abord, sélectionnez **Paramètres du projet > Description** et mettez à jour les informations sur le jeu et son éditeur :</span><span class="sxs-lookup"><span data-stu-id="1c70a-107">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="1c70a-108">Le **nom du jeu** apparaît dans la vignette de l’application sur le HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1c70a-108">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="1c70a-109">Le **nom unique de l’entreprise**  est utilisé lors de la génération du certificat de projet et doit être au format :</span><span class="sxs-lookup"><span data-stu-id="1c70a-109">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="1c70a-110">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName** :</span><span class="sxs-lookup"><span data-stu-id="1c70a-110">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![Capture d’écran de l’éditeur Unreal avec la section de description développée dans les paramètres du projet](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="1c70a-112">Développez la section **HoloLens** des paramètres du projet et mettez à jour les ressources d’empaquetage.</span><span class="sxs-lookup"><span data-stu-id="1c70a-112">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="1c70a-113">Ces noms de ressources seront indiquées dans la page du Store de l’application :</span><span class="sxs-lookup"><span data-stu-id="1c70a-113">These resource names will be shown on the application’s store page:</span></span>

![Capture d’écran de l’éditeur Unreal avec la section d’empaquetage développée dans les paramètres du projet](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="1c70a-115">Développez la section **Images** et mettez à jour les images du Store par défaut avec les textures qui représentent l’application du Store.</span><span class="sxs-lookup"><span data-stu-id="1c70a-115">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="1c70a-116">Cochez éventuellement la case **Logo 3D** pour charger un fichier glb à utiliser comme cube 3D lors du lancement de l’application :</span><span class="sxs-lookup"><span data-stu-id="1c70a-116">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![Capture d’écran de l’éditeur Unreal avec la section des images développée dans les paramètres du projet](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="1c70a-118">Enfin, sélectionnez **Générer** pour générer un certificat de signature à partir du nom du projet et du nom unique de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="1c70a-118">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="1c70a-119">Définissez une **couleur d’arrière-plan de vignette**, qui va remplacer tous les pixels transparents dans les images du Store.</span><span class="sxs-lookup"><span data-stu-id="1c70a-119">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="1c70a-120">Développez la liste déroulante et activez **Utiliser l’environnement du Windows Store** pour une exécution sur des appareils verrouillés par le Store, non déverrouillés par le développeur.</span><span class="sxs-lookup"><span data-stu-id="1c70a-120">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![Capture d’écran de l’éditeur Unreal avec la section de génération de certificats développée dans les paramètres du projet](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="1c70a-122">Programme d’installation d’application facultatif</span><span class="sxs-lookup"><span data-stu-id="1c70a-122">Optional App Installer</span></span>

<span data-ttu-id="1c70a-123">Un fichier de programme d’installation d’application peut être créé à partir de **Paramètres du projet > HoloLens**, lequel peut servir à distribuer l’application en dehors du Store.</span><span class="sxs-lookup"><span data-stu-id="1c70a-123">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="1c70a-124">Cochez la case permettant de **créer un programme d’installation d’application** et définissez une URL ou un chemin réseau où stocker le fichier appxbundle du jeu.</span><span class="sxs-lookup"><span data-stu-id="1c70a-124">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![Capture d’écran de l’éditeur Unreal avec la section du programme d’installation d’application développée dans les paramètres du projet](images/unreal-publishing-img-05.png)

<span data-ttu-id="1c70a-126">Quand l’application est empaquetée, les fichiers appxbundle et appinstaller sont générés.</span><span class="sxs-lookup"><span data-stu-id="1c70a-126">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="1c70a-127">Chargez le fichier appxbundle sur l’URL d’installation, puis lancez le fichier appinstaller pour installer l’application à partir de l’emplacement réseau.</span><span class="sxs-lookup"><span data-stu-id="1c70a-127">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="1c70a-128">Kit de certification des applications Windows</span><span class="sxs-lookup"><span data-stu-id="1c70a-128">Windows App Certification Kit</span></span>

<span data-ttu-id="1c70a-129">Le SDK Windows 10 est fourni avec le kit de certification des applications Windows (WACK) pour valider les problèmes courants susceptibles d’affecter le chargement d’un package dans le Store.</span><span class="sxs-lookup"><span data-stu-id="1c70a-129">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="1c70a-130">Vous pouvez trouver le WACK dans le répertoire des kits Windows, généralement sous le chemin suivant :</span><span class="sxs-lookup"><span data-stu-id="1c70a-130">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="1c70a-131">Une fois votre fichier appx est empaqueté pour la publication, exécutez **appcertui.exe** et suivez les invites pour analyser le fichier appx :</span><span class="sxs-lookup"><span data-stu-id="1c70a-131">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Capture d’écran de l’application sélectionnée à des fins de validation dans le kit de certification des applications Windows](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="1c70a-133">Sélectionnez **Valider l’application du Store** :</span><span class="sxs-lookup"><span data-stu-id="1c70a-133">Select **Validate Store App**:</span></span>

![Capture d’écran de la sélection de la validation dans le kit de certification des applications Windows](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="1c70a-135">Recherchez le fichier appx dans la section supérieure et sélectionnez **Suivant** :</span><span class="sxs-lookup"><span data-stu-id="1c70a-135">Browse for the appx in the top section and select **Next**:</span></span>

![Capture d’écran de la sélection des tests dans le kit de certification des applications Windows](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="1c70a-137">Sélectionnez **Suivant** pour exécuter les tests et créer un rapport :</span><span class="sxs-lookup"><span data-stu-id="1c70a-137">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="1c70a-138">Tous les tests disponibles exécutables sur l’ordinateur hôte sont activés par défaut.</span><span class="sxs-lookup"><span data-stu-id="1c70a-138">All available tests that can be run on the host PC will be enabled by default</span></span>

![Capture d’écran de la progression de la validation de l’application dans le kit de certification des applications Windows](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="1c70a-140">Attendez la fin des tests.</span><span class="sxs-lookup"><span data-stu-id="1c70a-140">Wait for the tests to finish.</span></span> <span data-ttu-id="1c70a-141">Une fois l’opération terminée, la fenêtre finale indique une réussite ou un échec, que vous pouvez consulter dans le rapport enregistré.</span><span class="sxs-lookup"><span data-stu-id="1c70a-141">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Capture d’écran des résultats du rapport final dans le kit de certification des applications Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="1c70a-143">Échec du WACK connu avec la version 4.25</span><span class="sxs-lookup"><span data-stu-id="1c70a-143">Known WACK failure with 4.25</span></span>

<span data-ttu-id="1c70a-144">Le plug-in Windows Mixed Reality dans Unreal 4.25 fait échouer le WACK, car certains binaires x64 sont inclus lors de l’empaquetage pour HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1c70a-144">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="1c70a-145">L’échec ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="1c70a-145">The failure will look like this:</span></span>

![Capture d’écran d’un échec en raison de l’analyseur binaire et des API prises en charge par le kit de certification des applications Windows](images/unreal-publishing-img-11.png)

<span data-ttu-id="1c70a-147">Pour résoudre le problème :</span><span class="sxs-lookup"><span data-stu-id="1c70a-147">To fix the issue:</span></span>
1. <span data-ttu-id="1c70a-148">Accédez à la racine de l’installation ou du répertoire source Unreal en ouvrant un projet Unreal et cliquez avec le bouton droit sur l’icône Unreal dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="1c70a-148">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="1c70a-149">Cliquez avec le bouton droit sur UE4Editor, sélectionnez Propriétés, puis accédez au chemin dans l’entrée **Emplacement** :</span><span class="sxs-lookup"><span data-stu-id="1c70a-149">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="1c70a-150">Dans **WindowsMixedRealityHMD.Build.cs**, modifiez la **ligne 32** suivante :</span><span class="sxs-lookup"><span data-stu-id="1c70a-150">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="1c70a-151">to:</span><span class="sxs-lookup"><span data-stu-id="1c70a-151">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="1c70a-152">Fermez Unreal, rouvrez le projet, puis réempaquetez pour HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1c70a-152">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="1c70a-153">Réexécutez le WACK et l’erreur sera supprimée.</span><span class="sxs-lookup"><span data-stu-id="1c70a-153">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="1c70a-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c70a-154">See also</span></span>
* [<span data-ttu-id="1c70a-155">Envoi d’une application au Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="1c70a-155">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="1c70a-156">Kit de certification des applications Windows</span><span class="sxs-lookup"><span data-stu-id="1c70a-156">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="1c70a-157">Créer un fichier Programme d’installation d’application manuellement</span><span class="sxs-lookup"><span data-stu-id="1c70a-157">Create an App Installer file manually</span></span>](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)