---
title: Son spatial dans Unity
description: Lire le son spatial à partir d’un point 3D spécifique dans votre scène Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, son spatial, HRTF, taille de la salle
ms.openlocfilehash: 9c5f71b2d9d13fa40f0d1674237d2da6c769e584
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679726"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="1cd15-104">Son spatial dans Unity</span><span class="sxs-lookup"><span data-stu-id="1cd15-104">Spatial sound in Unity</span></span>

<span data-ttu-id="1cd15-105">Cette page contient des liens vers des ressources pour le son spatial dans Unity.</span><span class="sxs-lookup"><span data-stu-id="1cd15-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="1cd15-106">Options de Spatializer</span><span class="sxs-lookup"><span data-stu-id="1cd15-106">Spatializer options</span></span>
<span data-ttu-id="1cd15-107">Les options Spatializer pour les applications de réalité mixte sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1cd15-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="1cd15-108">*Spatializer MS HRTF* .</span><span class="sxs-lookup"><span data-stu-id="1cd15-108">The *MS HRTF Spatializer* .</span></span> <span data-ttu-id="1cd15-109">Unity fournit cela dans le cadre du package facultatif *Windows Mixed Reality* .</span><span class="sxs-lookup"><span data-stu-id="1cd15-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="1cd15-110">Cela s’exécute sur le processeur dans une architecture à source unique à coût plus élevé.</span><span class="sxs-lookup"><span data-stu-id="1cd15-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="1cd15-111">Elle est fournie à des fins de compatibilité descendante avec les applications HoloLens d’origine.</span><span class="sxs-lookup"><span data-stu-id="1cd15-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="1cd15-112">*Microsoft Spatializer* .</span><span class="sxs-lookup"><span data-stu-id="1cd15-112">The *Microsoft Spatializer* .</span></span> <span data-ttu-id="1cd15-113">Celui-ci est disponible à partir du [dépôt github Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="1cd15-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="1cd15-114">Cela utilise une architecture à plusieurs sources moins onéreuse.</span><span class="sxs-lookup"><span data-stu-id="1cd15-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="1cd15-115">Sur HoloLens 2, cette valeur est déchargée sur un accélérateur matériel.</span><span class="sxs-lookup"><span data-stu-id="1cd15-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="1cd15-116">Pour les nouvelles applications, nous vous recommandons *Microsoft Spatializer* .</span><span class="sxs-lookup"><span data-stu-id="1cd15-116">For new applications, we recommend the *Microsoft Spatializer* .</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="1cd15-117">Activer Spatialization</span><span class="sxs-lookup"><span data-stu-id="1cd15-117">Enable spatialization</span></span>

<span data-ttu-id="1cd15-118">Utilisez [NuGet pour Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) pour installer _Microsoft. SpatialAudio. Spatializer. Unity_ et choisissez **Microsoft Spatializer** dans les paramètres audio de votre projet.</span><span class="sxs-lookup"><span data-stu-id="1cd15-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="1cd15-119">Ensuite :</span><span class="sxs-lookup"><span data-stu-id="1cd15-119">Then:</span></span>
* <span data-ttu-id="1cd15-120">Attacher une **source audio** à un objet dans la hiérarchie</span><span class="sxs-lookup"><span data-stu-id="1cd15-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="1cd15-121">Cochez la case **Enable Spatialization**</span><span class="sxs-lookup"><span data-stu-id="1cd15-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="1cd15-122">Déplacez le curseur de **lissage spatial** sur « 1 »</span><span class="sxs-lookup"><span data-stu-id="1cd15-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="1cd15-123">Assurez-vous que l’audio spatial est activé sur votre station de travail de développeur.</span><span class="sxs-lookup"><span data-stu-id="1cd15-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="1cd15-124">Activez-le en cliquant avec le bouton droit sur l’icône de volume dans la barre des tâches et en vous assurant que le son spatial est défini sur une valeur autre que « désactivé ».</span><span class="sxs-lookup"><span data-stu-id="1cd15-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="1cd15-125">Pour obtenir la meilleure représentation de ce que vous entendez sur HoloLens 2, choisissez **Windows Sonic pour casque** .</span><span class="sxs-lookup"><span data-stu-id="1cd15-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones** .</span></span>

>[!NOTE]
><span data-ttu-id="1cd15-126">Si vous recevez une erreur dans Unity sur l’impossibilité de charger le plug-in Microsoft. SpatialAudio. Spatializer. Unity, car l’une de ses dépendances est manquante, vérifiez que vous disposez de la dernière version du [Microsoft Visual C++ redistribuable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1cd15-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="1cd15-127">Pour plus d'informations, consultez la page suivante :</span><span class="sxs-lookup"><span data-stu-id="1cd15-127">For more details, see:</span></span>
* [<span data-ttu-id="1cd15-128">Dépôt GitHub Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="1cd15-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="1cd15-129">Didacticiel Spatializer de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1cd15-129">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="1cd15-130">Documentation de la source audio de Unity</span><span class="sxs-lookup"><span data-stu-id="1cd15-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="1cd15-131">Documentation Spatializer de Unity</span><span class="sxs-lookup"><span data-stu-id="1cd15-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="1cd15-132">Atténuation basée sur la distance</span><span class="sxs-lookup"><span data-stu-id="1cd15-132">Distance-based attenuation</span></span>
<span data-ttu-id="1cd15-133">La dégradation basée sur les distances par défaut d’Unity a une distance minimale de 1 mètre et une distance maximale de 500 mètres, avec un Rolloff logarithmique.</span><span class="sxs-lookup"><span data-stu-id="1cd15-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="1cd15-134">Ces paramètres peuvent fonctionner pour votre scénario, ou vous pouvez constater que les sources s’atténuent trop rapidement ou trop lentement.</span><span class="sxs-lookup"><span data-stu-id="1cd15-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="1cd15-135">Pour plus d'informations, consultez la page suivante :</span><span class="sxs-lookup"><span data-stu-id="1cd15-135">For more details, see:</span></span>
* <span data-ttu-id="1cd15-136">[Conception audio en réalité mixte](../../design/spatial-sound-design.md) pour les paramètres recommandés.</span><span class="sxs-lookup"><span data-stu-id="1cd15-136">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="1cd15-137">[Documentation de la source audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) pour obtenir des instructions sur la définition de ces courbes.</span><span class="sxs-lookup"><span data-stu-id="1cd15-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="1cd15-138">Réverbération</span><span class="sxs-lookup"><span data-stu-id="1cd15-138">Reverb</span></span>
<span data-ttu-id="1cd15-139">Le _Spatializer Microsoft_ désactive les effets postérieurs à Spatializer par défaut.</span><span class="sxs-lookup"><span data-stu-id="1cd15-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="1cd15-140">Pour activer la réverbération et d’autres effets pour les sources spatiales :</span><span class="sxs-lookup"><span data-stu-id="1cd15-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="1cd15-141">Attacher le composant de niveau d’envoi de l' **effet de salle** à chaque source</span><span class="sxs-lookup"><span data-stu-id="1cd15-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="1cd15-142">Ajustez la courbe de niveau d’envoi pour chaque source, afin de contrôler le gain sur le son renvoyé au graphique pour le traitement des effets</span><span class="sxs-lookup"><span data-stu-id="1cd15-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="1cd15-143">Pour plus d’informations, consultez [le chapitre 5 du didacticiel Spatializer](tutorials/unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="1cd15-143">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="1cd15-144">Exemples de sons spatiaux Unity</span><span class="sxs-lookup"><span data-stu-id="1cd15-144">Unity spatial sound examples</span></span>
<span data-ttu-id="1cd15-145">Pour obtenir des exemples de son spatial dans Unity, consultez :</span><span class="sxs-lookup"><span data-stu-id="1cd15-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="1cd15-146">Démonstrations MRTK</span><span class="sxs-lookup"><span data-stu-id="1cd15-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="1cd15-147">[Exemple de projet Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="1cd15-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="1cd15-148">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="1cd15-148">Next Development Checkpoint</span></span>

<span data-ttu-id="1cd15-149">Si vous suivez le parcours du point de contrôle de développement Unity que nous avons mis en place, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="1cd15-149">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="1cd15-150">À partir de là, vous pouvez passer au bloc de construction suivant :</span><span class="sxs-lookup"><span data-stu-id="1cd15-150">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1cd15-151">Text</span><span class="sxs-lookup"><span data-stu-id="1cd15-151">Text</span></span>](text-in-unity.md)

<span data-ttu-id="1cd15-152">Ou accédez aux API et fonctionnalités de la plateforme de réalité mixte :</span><span class="sxs-lookup"><span data-stu-id="1cd15-152">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1cd15-153">Expériences partagées</span><span class="sxs-lookup"><span data-stu-id="1cd15-153">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="1cd15-154">Vous pouvez toujours revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="1cd15-154">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cd15-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cd15-155">See also</span></span>
* [<span data-ttu-id="1cd15-156">Conception audio en réalité mixte</span><span class="sxs-lookup"><span data-stu-id="1cd15-156">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="1cd15-157">Didacticiel Spatializer de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1cd15-157">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
