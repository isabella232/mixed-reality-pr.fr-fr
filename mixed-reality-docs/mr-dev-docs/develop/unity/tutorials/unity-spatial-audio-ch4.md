---
title: Activation et désactivation de contenu audio spatial au moment de l’exécution
description: Apprenez à écrire un script C# qui utilise un bouton pour activer et désactiver l’audio Spatialization au moment de l’exécution.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer
ms.openlocfilehash: eaaf8a05088b5bab674ca11b15b0c63383faa479
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007339"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="36ad4-104">Activation et désactivation de Spatialization au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="36ad4-104">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="36ad4-105">Objectifs</span><span class="sxs-lookup"><span data-stu-id="36ad4-105">Objectives</span></span>

<span data-ttu-id="36ad4-106">Dans ce quatrième chapitre, vous allez :</span><span class="sxs-lookup"><span data-stu-id="36ad4-106">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="36ad4-107">Ajouter un nouveau script pour contrôler Spatialization sur un objet de jeu</span><span class="sxs-lookup"><span data-stu-id="36ad4-107">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="36ad4-108">Piloter le script de contrôle Spatialization à partir d’actions Button</span><span class="sxs-lookup"><span data-stu-id="36ad4-108">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="36ad4-109">Ajouter un script de contrôle Spatialization</span><span class="sxs-lookup"><span data-stu-id="36ad4-109">Add spatialization control script</span></span>

<span data-ttu-id="36ad4-110">Cliquez avec le bouton droit dans le volet **projet** et créez un script c# en choisissant **créer > script c#**.</span><span class="sxs-lookup"><span data-stu-id="36ad4-110">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="36ad4-111">Nommez votre script « SpatializeOnOff ».</span><span class="sxs-lookup"><span data-stu-id="36ad4-111">Name your script "SpatializeOnOff".</span></span>

![Création du script](images/spatial-audio/create-script.png)

<span data-ttu-id="36ad4-113">Double-cliquez sur le script dans le volet **projet** pour l’ouvrir dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36ad4-113">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="36ad4-114">Remplacez le contenu du script par défaut par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="36ad4-114">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="36ad4-115">Plusieurs lignes du script sont commentées. Ces lignes ne seront pas commentées dans le [Chapitre 5](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="36ad4-115">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="36ad4-116">Pour activer ou désactiver Spatialization, le script ajuste uniquement la propriété **spatialBlend** , en laissant la propriété **Spatialization** activée.</span><span class="sxs-lookup"><span data-stu-id="36ad4-116">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="36ad4-117">Dans ce mode, Unity applique toujours la courbe du **volume** .</span><span class="sxs-lookup"><span data-stu-id="36ad4-117">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="36ad4-118">Dans le cas contraire, si l’utilisateur devait désactiver Spatialization en loin de la source, il entendrait l’augmentation soudaine du volume.</span><span class="sxs-lookup"><span data-stu-id="36ad4-118">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="36ad4-119">Si vous préférez désactiver complètement Spatialization, modifiez le script pour ajuster également la propriété booléenne **Spatialization** de la variable **ObjetSource** .</span><span class="sxs-lookup"><span data-stu-id="36ad4-119">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="36ad4-120">Joindre votre script et le piloter à partir du bouton</span><span class="sxs-lookup"><span data-stu-id="36ad4-120">Attach your script and drive it from the button</span></span>

<span data-ttu-id="36ad4-121">Dans le volet de l' **inspecteur** du **Quad**, cliquez sur **Ajouter un composant** et ajoutez le script **spatial on off** :</span><span class="sxs-lookup"><span data-stu-id="36ad4-121">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![Ajouter un script à quatre cœurs](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="36ad4-123">Sur le composant **spatialiser on off** du **Quad**:</span><span class="sxs-lookup"><span data-stu-id="36ad4-123">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="36ad4-124">Recherchez l’objet **PressableButtonHoloLens2-> IconAndText-> TextMeshPro** dans la **hiérarchie**:</span><span class="sxs-lookup"><span data-stu-id="36ad4-124">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subject in the **Hierarchy**:</span></span>

![Rechercher l’objet PressableButtonHoloLens2 dans la hiérarchie](images/spatial-audio/pressable-button-object.png)

2. <span data-ttu-id="36ad4-126">Faites glisser le sujet **TextMeshPro** dans le champ **ButtonTextObject** du composant **spatialiser sur OFF** .</span><span class="sxs-lookup"><span data-stu-id="36ad4-126">Drag the **TextMeshPro** subject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="36ad4-127">Une fois ces modifications effectuées, le composant **spatial on off** du **Quad** ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="36ad4-127">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Spatialiser en dehors de la base](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="36ad4-129">Pour définir le bouton pour appeler le script **spatial on off** lorsque le bouton est relâché, ouvrez le volet **Inspector** de l’objet **PressableButtonHoloLens2** , recherchez **le composant** interactif et :</span><span class="sxs-lookup"><span data-stu-id="36ad4-129">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="36ad4-130">Recherche la région **OnClick ()** de la sous-section **événements**</span><span class="sxs-lookup"><span data-stu-id="36ad4-130">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="36ad4-131">Faites glisser le **Quad** de la **hiérarchie** dans l’emplacement de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="36ad4-131">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="36ad4-132">Sélectionnez **SpatializeOnOff. SwapSpatialization** dans la zone de liste déroulante action.</span><span class="sxs-lookup"><span data-stu-id="36ad4-132">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="36ad4-133">Une fois ces modifications effectuées, le composant **interagissant** peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="36ad4-133">After these changes, the **Interactable** component will look like this:</span></span>

![Paramètres d’action du bouton](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="36ad4-135">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="36ad4-135">Next steps</span></span>

<span data-ttu-id="36ad4-136">Essayez votre application sur un HoloLens 2 ou dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="36ad4-136">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="36ad4-137">Dans l’application, vous pouvez maintenant toucher le bouton pour activer et désactiver Spatialization sur la vidéo.</span><span class="sxs-lookup"><span data-stu-id="36ad4-137">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="36ad4-138">Lors du test dans l’éditeur Unity, appuyez sur la barre d’espace et faites défiler la molette pour activer la simulation manuelle.</span><span class="sxs-lookup"><span data-stu-id="36ad4-138">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="36ad4-139">Chapitre 5</span><span class="sxs-lookup"><span data-stu-id="36ad4-139">Chapter 5</span></span>](unity-spatial-audio-ch5.md) 

