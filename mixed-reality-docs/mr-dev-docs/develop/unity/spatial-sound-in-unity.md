---
title: Son spatial dans Unity
description: Lire le son spatial à partir d’un point 3D spécifique dans votre scène Unity.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, son spatial, HRTF, taille de la salle, casque de la réalité mixte, casque Windows Mixed realisation, casque de la réalité virtuelle, MRTK, boîte à outils de la réalité mixte, Spatializer, réverbération
ms.openlocfilehash: 1efe287855cc5b7738069c6d8183c2ecb5bd6d59
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010140"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="6d597-104">Son spatial dans Unity</span><span class="sxs-lookup"><span data-stu-id="6d597-104">Spatial sound in Unity</span></span>

<span data-ttu-id="6d597-105">Cette page contient des liens vers des ressources pour le son spatial dans Unity.</span><span class="sxs-lookup"><span data-stu-id="6d597-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="6d597-106">Options de Spatializer</span><span class="sxs-lookup"><span data-stu-id="6d597-106">Spatializer options</span></span>
<span data-ttu-id="6d597-107">Les options Spatializer pour les applications de réalité mixte sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d597-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="6d597-108">Unity fournit le *Spatializer MS HRTF* dans le cadre du package facultatif *Windows Mixed Reality* .</span><span class="sxs-lookup"><span data-stu-id="6d597-108">Unity provides the *MS HRTF Spatializer* as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="6d597-109">S’exécute sur le processeur dans une architecture à source unique à coût plus élevé.</span><span class="sxs-lookup"><span data-stu-id="6d597-109">Runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="6d597-110">Fourni pour la compatibilité descendante avec les applications HoloLens d’origine.</span><span class="sxs-lookup"><span data-stu-id="6d597-110">Provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="6d597-111">*Microsoft Spatializer* est disponible dans le [dépôt github Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="6d597-111">The *Microsoft Spatializer* is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="6d597-112">Utilise une architecture à plusieurs sources à moindre coût.</span><span class="sxs-lookup"><span data-stu-id="6d597-112">Uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="6d597-113">Déchargée sur un accélérateur matériel sur le HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6d597-113">Offloaded to a hardware accelerator on the HoloLens 2.</span></span> 

<span data-ttu-id="6d597-114">Pour les nouvelles applications, nous vous recommandons *Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="6d597-114">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="6d597-115">Activer Spatialization</span><span class="sxs-lookup"><span data-stu-id="6d597-115">Enable spatialization</span></span>

<span data-ttu-id="6d597-116">Utilisez [NuGet pour Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) pour installer _Microsoft. SpatialAudio. Spatializer. Unity_ et choisissez **Microsoft Spatializer** dans les paramètres audio de votre projet.</span><span class="sxs-lookup"><span data-stu-id="6d597-116">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="6d597-117">Ensuite :</span><span class="sxs-lookup"><span data-stu-id="6d597-117">Then:</span></span>
* <span data-ttu-id="6d597-118">Attacher une **source audio** à un objet dans la hiérarchie</span><span class="sxs-lookup"><span data-stu-id="6d597-118">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="6d597-119">Cochez la case **Enable Spatialization**</span><span class="sxs-lookup"><span data-stu-id="6d597-119">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="6d597-120">Déplacez le curseur de **lissage spatial** sur « 1 »</span><span class="sxs-lookup"><span data-stu-id="6d597-120">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="6d597-121">Assurez-vous que l’audio spatial est activé sur votre station de travail de développeur.</span><span class="sxs-lookup"><span data-stu-id="6d597-121">Ensure spatial audio is enabled on your developer workstation.</span></span> 
    * <span data-ttu-id="6d597-122">Cliquez avec le bouton droit sur l’icône de volume dans la barre des tâches et assurez-vous que le son spatial est défini sur une valeur autre que « désactivé ».</span><span class="sxs-lookup"><span data-stu-id="6d597-122">Right-click on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off".</span></span> 
    * <span data-ttu-id="6d597-123">Choisissez **Windows Sonic pour casque** pour obtenir la meilleure représentation de ce que vous entendez sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6d597-123">Choose **Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

>[!NOTE]
><span data-ttu-id="6d597-124">Si vous recevez une erreur dans Unity sur l’impossibilité de charger le plug-in Microsoft. SpatialAudio. Spatializer. Unity, car l’une de ses dépendances est manquante, vérifiez que vous disposez de la dernière version du [Microsoft Visual C++ redistribuable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6d597-124">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="6d597-125">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d597-125">For more information, see:</span></span>
* [<span data-ttu-id="6d597-126">Dépôt GitHub Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="6d597-126">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="6d597-127">Didacticiel Spatializer de Microsoft</span><span class="sxs-lookup"><span data-stu-id="6d597-127">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="6d597-128">Documentation de la source audio de Unity</span><span class="sxs-lookup"><span data-stu-id="6d597-128">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="6d597-129">Documentation Spatializer de Unity</span><span class="sxs-lookup"><span data-stu-id="6d597-129">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="6d597-130">Atténuation basée sur la distance</span><span class="sxs-lookup"><span data-stu-id="6d597-130">Distance-based attenuation</span></span>
<span data-ttu-id="6d597-131">La dégradation basée sur les distances par défaut d’Unity a une distance minimale de 1 mètre et une distance maximale de 500 mètres, avec un Rolloff logarithmique.</span><span class="sxs-lookup"><span data-stu-id="6d597-131">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="6d597-132">Ces paramètres peuvent fonctionner pour votre scénario, ou vous pouvez constater que les sources s’atténuent trop rapidement ou trop lentement.</span><span class="sxs-lookup"><span data-stu-id="6d597-132">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="6d597-133">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d597-133">For more information, see:</span></span>
* <span data-ttu-id="6d597-134">[Conception audio en réalité mixte](../../design/spatial-sound-design.md) pour les paramètres recommandés.</span><span class="sxs-lookup"><span data-stu-id="6d597-134">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="6d597-135">[Documentation de la source audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) pour obtenir des instructions sur la définition de ces courbes.</span><span class="sxs-lookup"><span data-stu-id="6d597-135">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="6d597-136">Réverbération</span><span class="sxs-lookup"><span data-stu-id="6d597-136">Reverb</span></span>
<span data-ttu-id="6d597-137">Le _Spatializer Microsoft_ désactive les effets postérieurs à Spatializer par défaut.</span><span class="sxs-lookup"><span data-stu-id="6d597-137">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="6d597-138">Pour activer la réverbération et d’autres effets pour les sources spatiales :</span><span class="sxs-lookup"><span data-stu-id="6d597-138">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="6d597-139">Attacher le composant de niveau d’envoi de l' **effet de salle** à chaque source</span><span class="sxs-lookup"><span data-stu-id="6d597-139">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="6d597-140">Ajustez la courbe de niveau d’envoi pour chaque source, afin de contrôler le gain sur le son renvoyé au graphique pour le traitement des effets</span><span class="sxs-lookup"><span data-stu-id="6d597-140">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="6d597-141">Pour plus d’informations, consultez [le chapitre 5 du didacticiel Spatializer](tutorials/unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="6d597-141">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="6d597-142">Exemples de sons spatiaux Unity</span><span class="sxs-lookup"><span data-stu-id="6d597-142">Unity spatial sound examples</span></span>
<span data-ttu-id="6d597-143">Pour obtenir des exemples de son spatial dans Unity, consultez :</span><span class="sxs-lookup"><span data-stu-id="6d597-143">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="6d597-144">Démonstrations MRTK</span><span class="sxs-lookup"><span data-stu-id="6d597-144">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="6d597-145">[Exemple de projet Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="6d597-145">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="6d597-146">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="6d597-146">Next Development Checkpoint</span></span>

<span data-ttu-id="6d597-147">Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="6d597-147">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="6d597-148">À partir de là, vous pouvez passer au bloc de construction suivant :</span><span class="sxs-lookup"><span data-stu-id="6d597-148">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6d597-149">Text</span><span class="sxs-lookup"><span data-stu-id="6d597-149">Text</span></span>](text-in-unity.md)

<span data-ttu-id="6d597-150">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="6d597-150">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6d597-151">Expériences partagées</span><span class="sxs-lookup"><span data-stu-id="6d597-151">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="6d597-152">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="6d597-152">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d597-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d597-153">See also</span></span>
* [<span data-ttu-id="6d597-154">Conception audio en réalité mixte</span><span class="sxs-lookup"><span data-stu-id="6d597-154">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="6d597-155">Didacticiel Spatializer de Microsoft</span><span class="sxs-lookup"><span data-stu-id="6d597-155">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
