---
title: Système de scène - Types de scènes
description: Documentation sur différents types de scènes dans MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144569"
---
# <a name="scene-types"></a><span data-ttu-id="c5f1f-104">Types de scènes</span><span class="sxs-lookup"><span data-stu-id="c5f1f-104">Scene types</span></span>

<span data-ttu-id="c5f1f-105">Les scènes ont été divisées en trois types, et chaque type a une fonction différente.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![Système de scène dans la hiérarchie](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="c5f1f-107">Scènes du contenu</span><span class="sxs-lookup"><span data-stu-id="c5f1f-107">Content scenes</span></span>

<span data-ttu-id="c5f1f-108">Il s’agit des scènes que vous utilisez pour gérer.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="c5f1f-109">N’importe quel type de contenu peut être stocké dans ceux-ci, et ils peuvent être chargés ou déchargés dans n’importe quelle combinaison.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="c5f1f-110">Les scènes de contenu sont activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="c5f1f-111">Toutes les scènes incluses dans le tableau de votre profil `Content Scenes` peuvent être chargées/déchargées par le service.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="c5f1f-112">Scènes du gestionnaire</span><span class="sxs-lookup"><span data-stu-id="c5f1f-112">Manager scenes</span></span>

<span data-ttu-id="c5f1f-113">Une seule scène avec une instance MixedRealityToolkit requise.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="c5f1f-114">Cette scène sera chargée en premier au lancement et restera chargée pendant la durée de vie de l’application.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="c5f1f-115">La scène Manager peut également héberger d’autres objets qui ne doivent jamais être détruits.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="c5f1f-116">Il s’agit de l’alternative préférée à DontDestroyOnLoad.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="c5f1f-117">Pour activer cette fonctionnalité, archivez `Use Manager Scene` votre profil et faites glisser un objet de scène dans le `Manager Scene` champ.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="c5f1f-118">Scènes d’éclairage</span><span class="sxs-lookup"><span data-stu-id="c5f1f-118">Lighting scenes</span></span>

<span data-ttu-id="c5f1f-119">Ensemble de scènes qui stockent des informations d’éclairage et des objets d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="c5f1f-120">Un seul peut être chargé à la fois et leurs paramètres peuvent être mélangés pendant les charges pour des transitions d’éclairage lisse.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="c5f1f-121">Les paramètres d’éclairage de Unity (lumière ambiante, skyboxes, etc.) peuvent être difficiles à gérer lors de l’utilisation d’un chargement additif, car ils sont liés à des scènes individuelles et le comportement de remplacement n’est pas simple.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="c5f1f-122">En pratique, cela peut entraîner des confusions lorsque des ressources sont créées dans des conditions d’éclairage qui n’obtiennent pas au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![Paramètres d’éclairage du système de scène](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="c5f1f-124">Le système de scène utilise des scènes d’éclairage pour s’assurer que ces paramètres restent cohérents, quelles que soient les scènes chargées ou actives, en mode édition et en mode lecture.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="c5f1f-125">Pour activer cette fonctionnalité, archivez `Use Lighting Scene` votre profil et remplissez le `Lighting Scenes` tableau.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="c5f1f-126">Paramètres d’éclairage mis en cache</span><span class="sxs-lookup"><span data-stu-id="c5f1f-126">Cached lighting settings</span></span>

<span data-ttu-id="c5f1f-127">Votre profil stocke des copies mises en cache des paramètres d’éclairage conservés dans vos scènes d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="c5f1f-128">Si ces paramètres changent dans vos scènes d’éclairage, vous devrez mettre à jour votre cache pour vous assurer que l’éclairage s’affiche comme prévu en mode lecture.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="c5f1f-129">Votre profil affiche un avertissement quand il soupçonne que vos paramètres mis en cache sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="c5f1f-130">Cliquez sur `Update Cached Lighting Settings` charge chacune de vos scènes d’éclairage, extrayez leurs paramètres, puis stockez-les dans votre profil.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![Paramètres d’éclairage mis en cache du système de scène](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="c5f1f-132">Comportement de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="c5f1f-132">Editor behavior</span></span>

<span data-ttu-id="c5f1f-133">L’un des avantages de l’utilisation des scènes d’éclairage est de savoir que votre contenu est correctement allumé lors de la modification.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="c5f1f-134">À cette fin, le service Scene garde une scène d’éclairage chargée à tout moment et copie les paramètres d’éclairage de cette scène sur la scène active actuelle.\*</span><span class="sxs-lookup"><span data-stu-id="c5f1f-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="c5f1f-135">Vous pouvez modifier la scène d’éclairage chargée en ouvrant l' [inspecteur de service](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) du système de scène.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="c5f1f-136">En mode édition, vous pouvez passer instantanément d’une scène d’éclairage à une autre.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="c5f1f-137">En mode lecture, vous pouvez afficher un aperçu des transitions.</span><span class="sxs-lookup"><span data-stu-id="c5f1f-137">In play mode, you can preview transitions.</span></span>

![Inspecteur de système de scène](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="c5f1f-139">\**Remarque : en général, la scène active détermine vos paramètres d’éclairage dans l’éditeur. Toutefois, nous choisissons de ne pas utiliser cette fonctionnalité pour appliquer les paramètres d’éclairage, car la scène active est également l’endroit où les objets nouvellement créés sont placés par défaut, et les scènes d’éclairage sont uniquement autorisées à contenir des composants d’éclairage. Au lieu de cela, les paramètres actuels de la scène d’éclairage sont automatiquement copiés dans les paramètres de la scène active. N’oubliez pas que cela entraînera le Surécriture des paramètres d’éclairage de votre scène de contenu.*</span><span class="sxs-lookup"><span data-stu-id="c5f1f-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
