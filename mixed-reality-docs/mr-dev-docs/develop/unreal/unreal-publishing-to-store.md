---
title: Publication sur le Microsoft Store
description: Découvrez comment empaqueter, certifier et publier vos applications de réalité mixte Unreal sur le Microsoft Store.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, documentation, guides, fonctionnalités, casque de réalité mixte, casque de réalité mixte Windows, casque de réalité virtuelle, publication, distribution, Microsoft Store
ms.openlocfilehash: 3a975d9c66e64f56919163e9d3aa65a3126d6379
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583594"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="41845-104">Publication sur le Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="41845-104">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="41845-105">Quand vous êtes prêt à lancer votre application, vous devez mettre à jour quelques paramètres du projet avant de la soumettre au Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="41845-105">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="41845-106">Tous ces paramètres ont des valeurs par défaut, que vous devez toutefois changer pour la production afin de mieux représenter l’application.</span><span class="sxs-lookup"><span data-stu-id="41845-106">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="41845-107">Paramètres du projet pour l’empaquetage du Store</span><span class="sxs-lookup"><span data-stu-id="41845-107">Project settings for the store packaging</span></span>

1. <span data-ttu-id="41845-108">Tout d’abord, sélectionnez **Paramètres du projet > Description** et mettez à jour les informations sur le jeu et son éditeur :</span><span class="sxs-lookup"><span data-stu-id="41845-108">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="41845-109">Le **nom du jeu** apparaît dans la vignette de l’application sur le HoloLens.</span><span class="sxs-lookup"><span data-stu-id="41845-109">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="41845-110">Le **nom unique de l’entreprise**  est utilisé lors de la génération du certificat de projet et doit être au format :</span><span class="sxs-lookup"><span data-stu-id="41845-110">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="41845-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName** :</span><span class="sxs-lookup"><span data-stu-id="41845-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![Capture d’écran de l’éditeur Unreal avec la section de description développée dans les paramètres du projet](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="41845-113">Développez la section **HoloLens** des paramètres du projet et mettez à jour les ressources d’empaquetage.</span><span class="sxs-lookup"><span data-stu-id="41845-113">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="41845-114">Ces noms de ressources seront indiquées dans la page du Store de l’application :</span><span class="sxs-lookup"><span data-stu-id="41845-114">These resource names will be shown on the application’s store page:</span></span>

![Capture d’écran de l’éditeur Unreal avec la section d’empaquetage développée dans les paramètres du projet](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="41845-116">Développez la section **Images** et mettez à jour les images du Store par défaut avec les textures qui représentent l’application du Store.</span><span class="sxs-lookup"><span data-stu-id="41845-116">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="41845-117">Cochez éventuellement la case **Logo 3D** pour charger un fichier glb à utiliser comme cube 3D lors du lancement de l’application :</span><span class="sxs-lookup"><span data-stu-id="41845-117">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![Capture d’écran de l’éditeur Unreal avec la section des images développée dans les paramètres du projet](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="41845-119">Enfin, sélectionnez **Générer** pour générer un certificat de signature à partir du nom du projet et du nom unique de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="41845-119">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="41845-120">Définissez une **couleur d’arrière-plan de vignette**, qui va remplacer tous les pixels transparents dans les images du Store.</span><span class="sxs-lookup"><span data-stu-id="41845-120">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="41845-121">Développez la liste déroulante et activez **Utiliser l’environnement du Windows Store** pour une exécution sur des appareils verrouillés par le Store, non déverrouillés par le développeur.</span><span class="sxs-lookup"><span data-stu-id="41845-121">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![Capture d’écran de l’éditeur Unreal avec la section de génération de certificats développée dans les paramètres du projet](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="41845-123">Programme d’installation d’application facultatif</span><span class="sxs-lookup"><span data-stu-id="41845-123">Optional App Installer</span></span>

<span data-ttu-id="41845-124">Un fichier de programme d’installation d’application peut être créé à partir de **Paramètres du projet > HoloLens**, lequel peut servir à distribuer l’application en dehors du Store.</span><span class="sxs-lookup"><span data-stu-id="41845-124">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="41845-125">Cochez la case permettant de **créer un programme d’installation d’application** et définissez une URL ou un chemin réseau où stocker le fichier appxbundle du jeu.</span><span class="sxs-lookup"><span data-stu-id="41845-125">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![Capture d’écran de l’éditeur Unreal avec la section du programme d’installation d’application développée dans les paramètres du projet](images/unreal-publishing-img-05.png)

<span data-ttu-id="41845-127">Quand l’application est empaquetée, les fichiers appxbundle et appinstaller sont générés.</span><span class="sxs-lookup"><span data-stu-id="41845-127">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="41845-128">Chargez le fichier appxbundle sur l’URL d’installation, puis lancez le fichier appinstaller pour installer l’application à partir de l’emplacement réseau.</span><span class="sxs-lookup"><span data-stu-id="41845-128">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="41845-129">Kit de certification des applications Windows</span><span class="sxs-lookup"><span data-stu-id="41845-129">Windows App Certification Kit</span></span>

<span data-ttu-id="41845-130">Le SDK Windows 10 est fourni avec le kit de certification des applications Windows (WACK) pour valider les problèmes courants susceptibles d’affecter le chargement d’un package dans le Store.</span><span class="sxs-lookup"><span data-stu-id="41845-130">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="41845-131">Vous pouvez trouver le WACK dans le répertoire des kits Windows, généralement sous le chemin suivant :</span><span class="sxs-lookup"><span data-stu-id="41845-131">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="41845-132">Une fois votre fichier appx est empaqueté pour la publication, exécutez **appcertui.exe** et suivez les invites pour analyser le fichier appx :</span><span class="sxs-lookup"><span data-stu-id="41845-132">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Capture d’écran de l’application sélectionnée à des fins de validation dans le kit de certification des applications Windows](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="41845-134">Sélectionnez **Valider l’application du Store** :</span><span class="sxs-lookup"><span data-stu-id="41845-134">Select **Validate Store App**:</span></span>

![Capture d’écran de la sélection de la validation dans le kit de certification des applications Windows](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="41845-136">Recherchez le fichier appx dans la section supérieure et sélectionnez **Suivant** :</span><span class="sxs-lookup"><span data-stu-id="41845-136">Browse for the appx in the top section and select **Next**:</span></span>

![Capture d’écran de la sélection des tests dans le kit de certification des applications Windows](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="41845-138">Sélectionnez **Suivant** pour exécuter les tests et créer un rapport :</span><span class="sxs-lookup"><span data-stu-id="41845-138">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="41845-139">Tous les tests disponibles exécutables sur l’ordinateur hôte sont activés par défaut.</span><span class="sxs-lookup"><span data-stu-id="41845-139">All available tests that can be run on the host PC will be enabled by default</span></span>

![Capture d’écran de la progression de la validation de l’application dans le kit de certification des applications Windows](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="41845-141">Attendez la fin des tests.</span><span class="sxs-lookup"><span data-stu-id="41845-141">Wait for the tests to finish.</span></span> <span data-ttu-id="41845-142">Une fois l’opération terminée, la fenêtre finale indique une réussite ou un échec, que vous pouvez consulter dans le rapport enregistré.</span><span class="sxs-lookup"><span data-stu-id="41845-142">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Capture d’écran des résultats du rapport final dans le kit de certification des applications Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="41845-144">Échec du WACK connu avec la version 4.25</span><span class="sxs-lookup"><span data-stu-id="41845-144">Known WACK failure with 4.25</span></span>

<span data-ttu-id="41845-145">Le plug-in Windows Mixed Reality dans Unreal 4.25 fait échouer le WACK, car certains binaires x64 sont inclus lors de l’empaquetage pour HoloLens.</span><span class="sxs-lookup"><span data-stu-id="41845-145">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="41845-146">L’échec ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="41845-146">The failure will look like this:</span></span>

![Capture d’écran d’un échec en raison de l’analyseur binaire et des API prises en charge par le kit de certification des applications Windows](images/unreal-publishing-img-11.png)

<span data-ttu-id="41845-148">Pour résoudre le problème :</span><span class="sxs-lookup"><span data-stu-id="41845-148">To fix the issue:</span></span>
1. <span data-ttu-id="41845-149">Accédez à la racine de l’installation ou du répertoire source Unreal en ouvrant un projet Unreal et cliquez avec le bouton droit sur l’icône Unreal dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="41845-149">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="41845-150">Cliquez avec le bouton droit sur UE4Editor, sélectionnez Propriétés, puis accédez au chemin dans l’entrée **Emplacement** :</span><span class="sxs-lookup"><span data-stu-id="41845-150">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="41845-151">Dans **WindowsMixedRealityHMD.Build.cs**, modifiez la **ligne 32** suivante :</span><span class="sxs-lookup"><span data-stu-id="41845-151">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="41845-152">to:</span><span class="sxs-lookup"><span data-stu-id="41845-152">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="41845-153">Fermez Unreal, rouvrez le projet, puis réempaquetez pour HoloLens.</span><span class="sxs-lookup"><span data-stu-id="41845-153">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="41845-154">Réexécutez le WACK et l’erreur sera supprimée.</span><span class="sxs-lookup"><span data-stu-id="41845-154">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="41845-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41845-155">See also</span></span>

* [<span data-ttu-id="41845-156">Envoi d’une application au Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="41845-156">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="41845-157">Kit de certification des applications Windows</span><span class="sxs-lookup"><span data-stu-id="41845-157">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="41845-158">Créer un fichier Programme d’installation d’application manuellement</span><span class="sxs-lookup"><span data-stu-id="41845-158">Create an App Installer file manually</span></span>](/windows/msix/app-installer/how-to-create-appinstaller-file)