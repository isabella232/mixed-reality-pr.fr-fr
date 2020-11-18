---
title: Permettre le placement des modèles 3D dans la page d’accueil
description: Comment placer des modèles 3D à partir de votre site Web ou de votre application dans la page d’hébergement de Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modèle, place à la terre, lieu, monde, modélisation, Hébergement de réalité mixte, Web, application, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 192c403ce50c3a47fb19f644af78d1150bb9aa3f
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703185"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="ddb37-104">Permettre le placement d’objets 3D dans l’accueil réalité mixte</span><span class="sxs-lookup"><span data-stu-id="ddb37-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="ddb37-105">Cette fonctionnalité a été ajoutée dans le cadre de la [mise à jour 2018 de Windows 10 avril](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018).</span><span class="sxs-lookup"><span data-stu-id="ddb37-105">This feature was added as part of the [Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018).</span></span> <span data-ttu-id="ddb37-106">Les versions antérieures de Windows ne sont pas compatibles avec cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="ddb37-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="ddb37-107">La [base de la réalité Windows Mixed](../discover/navigating-the-windows-mixed-reality-home.md) est le point de départ où les utilisateurs se trouvent avant de lancer des applications.</span><span class="sxs-lookup"><span data-stu-id="ddb37-107">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="ddb37-108">Dans certains scénarios, les applications 2D (comme l’application hologrammes) permettent de placer des modèles 3D directement dans l’espace de la réalité mixte en tant que décorations ou pour une inspection supplémentaire en 3D complet.</span><span class="sxs-lookup"><span data-stu-id="ddb37-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="ddb37-109">Le *protocole Add Model* vous permet d’envoyer un modèle 3D à partir de votre site Web ou application directement dans la page d’hébergement Windows Mixed Reality, où il sera conservé comme les [lanceurs d’applications 3D](3d-app-launcher-design-guidance.md), les applications 2D et les hologrammes.</span><span class="sxs-lookup"><span data-stu-id="ddb37-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="ddb37-110">Par exemple, si vous développez une application qui couvre un catalogue de mobilier en 3D pour la conception d’un espace, vous pouvez utiliser le *protocole ajouter un modèle* pour permettre aux utilisateurs de placer ces modèles de mobilier 3D à partir du catalogue.</span><span class="sxs-lookup"><span data-stu-id="ddb37-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="ddb37-111">Une fois placés dans le monde, les utilisateurs peuvent déplacer, redimensionner et supprimer ces modèles 3D comme d’autres hologrammes de la famille.</span><span class="sxs-lookup"><span data-stu-id="ddb37-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="ddb37-112">Cet article fournit une vue d’ensemble de l’implémentation du *protocole Add Model* pour vous permettre de commencer à permettre aux utilisateurs de décorer leur monde avec des objets 3D à partir de votre application ou du Web.</span><span class="sxs-lookup"><span data-stu-id="ddb37-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="ddb37-113">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="ddb37-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ddb37-114"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="ddb37-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="ddb37-115"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ddb37-115"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ddb37-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="ddb37-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ddb37-117">Ajouter un protocole de modèle</span><span class="sxs-lookup"><span data-stu-id="ddb37-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="ddb37-118">✔️</span><span class="sxs-lookup"><span data-stu-id="ddb37-118">✔️</span></span></td>
        <td><span data-ttu-id="ddb37-119">✔️</span><span class="sxs-lookup"><span data-stu-id="ddb37-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="ddb37-120">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="ddb37-120">Overview</span></span>

<span data-ttu-id="ddb37-121">Il existe 2 étapes pour activer le placement des modèles 3D dans la page d’hébergement de la réalité mixte de Windows :</span><span class="sxs-lookup"><span data-stu-id="ddb37-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="ddb37-122">[Vérifiez que votre modèle 3D est compatible avec la page d’hébergement Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="ddb37-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="ddb37-123">Implémentez le *protocole Add Model* dans votre application ou votre page Web (cet article).</span><span class="sxs-lookup"><span data-stu-id="ddb37-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="ddb37-124">Implémentation du *protocole Add Model*</span><span class="sxs-lookup"><span data-stu-id="ddb37-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="ddb37-125">Une fois que vous disposez d’un [modèle 3D compatible](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), vous pouvez implémenter le *protocole Add Model* en activant l’URI suivant à partir d’une page Web ou d’une application :</span><span class="sxs-lookup"><span data-stu-id="ddb37-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="ddb37-126">Si l’URI pointe vers une ressource distante, il est automatiquement téléchargé et placé dans la page d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="ddb37-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="ddb37-127">Les ressources locales seront copiées dans le dossier des données d’application de la réalité mixte avant d’être placées dans la page d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="ddb37-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="ddb37-128">Nous vous recommandons de concevoir votre expérience afin de prendre en compte les scénarios dans lesquels l’utilisateur peut exécuter une version antérieure de Windows qui ne prend pas en charge cette fonctionnalité en masquant le bouton ou en le désactivant si possible.</span><span class="sxs-lookup"><span data-stu-id="ddb37-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="ddb37-129">Appel du *protocole Add Model* à partir d’une application plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="ddb37-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="ddb37-130">Appel du *protocole Add Model* à partir d’une page Web :</span><span class="sxs-lookup"><span data-stu-id="ddb37-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="ddb37-131">Considérations relatives aux casques immersifs (VR)</span><span class="sxs-lookup"><span data-stu-id="ddb37-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="ddb37-132">Pour les casques immersifs, le portail de réalité mixte n’a pas besoin d’être en cours d’exécution avant d’appeler le *protocole Add Model*.</span><span class="sxs-lookup"><span data-stu-id="ddb37-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="ddb37-133">Dans ce cas, le *protocole Add Model* lance le portail de réalité mixte et place l’objet directement là où le casque regarde une fois que vous arrivez dans la zone d’hébergement de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="ddb37-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="ddb37-134">Quand vous appelez le *protocole Add Model* à partir du bureau avec le portail de réalité mixte déjà en cours d’exécution, assurez-vous que le casque est « éveillé ».</span><span class="sxs-lookup"><span data-stu-id="ddb37-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="ddb37-135">Si ce n’est pas le cas, le positionnement échoue.</span><span class="sxs-lookup"><span data-stu-id="ddb37-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="ddb37-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddb37-136">See also</span></span>

* [<span data-ttu-id="ddb37-137">Création de modèles 3D à utiliser dans la page d’hébergement Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ddb37-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="ddb37-138">Exploration de la page d’accueil Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ddb37-138">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
