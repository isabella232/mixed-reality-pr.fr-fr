---
title: Didacticiels audio spatial-4. Activation et désactivation de contenu audio spatial au moment de l’exécution
description: Utilisez un bouton pour activer et désactiver le Spatialization de l’audio au moment de l’exécution.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer
ms.openlocfilehash: 26143975707b2cd6141803a6335cec89db5bbd26
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590731"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="0a141-105">4. activation et désactivation de Spatialization au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="0a141-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="0a141-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="0a141-106">Overview</span></span>

<span data-ttu-id="0a141-107">Dans ce didacticiel, vous allez apprendre à activer et à désactiver les Spatialization au moment de l’exécution et à les tester dans l’éditeur Unity et dans HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0a141-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="0a141-108">Objectifs</span><span class="sxs-lookup"><span data-stu-id="0a141-108">Objectives</span></span>

* <span data-ttu-id="0a141-109">Ajouter un nouveau script pour contrôler Spatialization sur un objet de jeu</span><span class="sxs-lookup"><span data-stu-id="0a141-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="0a141-110">Piloter le script de contrôle Spatialization à partir d’actions Button</span><span class="sxs-lookup"><span data-stu-id="0a141-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="0a141-111">Ajouter un script de contrôle Spatialization</span><span class="sxs-lookup"><span data-stu-id="0a141-111">Add spatialization control script</span></span>

 <span data-ttu-id="0a141-112">Cliquez avec le bouton droit dans la fenêtre du projet et choisissez **créer**  >  un **script c#** pour créer un script c#, entrez un nom approprié pour le script, par exemple, _SpatializeOnOff_:</span><span class="sxs-lookup"><span data-stu-id="0a141-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![Création du script](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

<span data-ttu-id="0a141-114">Double-cliquez sur le script dans la fenêtre projet pour l’ouvrir dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a141-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="0a141-115">Remplacez le contenu du script par défaut par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0a141-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="0a141-116">Plusieurs lignes du script sont commentées. Ces lignes ne seront pas commentées dans le [chapitre suivant : utilisation de la réverbération pour ajouter une distance à un son spatial](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="0a141-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="0a141-117">Pour activer ou désactiver le Spatialization, le script ajuste uniquement la propriété **spatialBlend** , en laissant la propriété **Spatialization** activée.</span><span class="sxs-lookup"><span data-stu-id="0a141-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="0a141-118">Dans ce mode, Unity applique toujours la courbe du **volume** .</span><span class="sxs-lookup"><span data-stu-id="0a141-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="0a141-119">Dans le cas contraire, si l’utilisateur devait désactiver Spatialization en loin de la source, il entendrait l’augmentation soudaine du volume.</span><span class="sxs-lookup"><span data-stu-id="0a141-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="0a141-120">Si vous préférez désactiver complètement Spatialization, modifiez le script pour ajuster également la propriété booléenne **Spatialization** de la variable **ObjetSource** .</span><span class="sxs-lookup"><span data-stu-id="0a141-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="0a141-121">Joindre votre script et le piloter à partir du bouton</span><span class="sxs-lookup"><span data-stu-id="0a141-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="0a141-122">Sélectionnez **Quad** dans la hiérarchie et dans la fenêtre Inspector, utilisez le bouton Ajouter un composant pour ajouter **SpatializeOnOff (script)**</span><span class="sxs-lookup"><span data-stu-id="0a141-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![Ajouter un script à quatre cœurs](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

<span data-ttu-id="0a141-124">Dans la hiérarchie, recherchez **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="0a141-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="0a141-125">Lorsque l’objet **Quad** est toujours sélectionné dans la hiérarchie, dans la fenêtre Inspector, localisez le composant **spatialiser on off (script)** et faites glisser le composant **TextMeshPro** du PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="0a141-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![Rechercher l’objet PressableButtonHoloLens2 dans la hiérarchie](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

<span data-ttu-id="0a141-127">Pour définir le bouton pour appeler le script **SpatializeOnOff** quand le bouton est relâché, vous devez configurer un script d’interaction.</span><span class="sxs-lookup"><span data-stu-id="0a141-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="0a141-128">Dans la fenêtre hiérarchie, sélectionnez **PressableButtonHoloLens2**.</span><span class="sxs-lookup"><span data-stu-id="0a141-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="0a141-129">Dans la fenêtre de l’inspecteur, localisez le composant **(script) pouvant être interagi** , puis cliquez sur l’icône + sous l’événement OnClick ().</span><span class="sxs-lookup"><span data-stu-id="0a141-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="0a141-130">Avec l’objet **PressableButtonHoloLens2** toujours sélectionné dans la fenêtre hiérarchie, cliquez et faites glisser l’objet **quadruple** à partir de la fenêtre hiérarchie dans le champ **aucun (objet)** vide de l’événement que vous venez d’ajouter pour que l’objet ButtonParent écoute l’événement de clic de bouton à partir de ce bouton :</span><span class="sxs-lookup"><span data-stu-id="0a141-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="0a141-131">Cliquez sur la liste déroulante **No Function** du même événement.</span><span class="sxs-lookup"><span data-stu-id="0a141-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="0a141-132">Sélectionnez ensuite **SpatializeOnOff**  >  **SwapSpatialization ()** pour activer et désactiver le son spatial</span><span class="sxs-lookup"><span data-stu-id="0a141-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![Paramètres d’action du bouton](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="0a141-134">Félicitations</span><span class="sxs-lookup"><span data-stu-id="0a141-134">Congratulations</span></span>

<span data-ttu-id="0a141-135">Dans ce didacticiel, vous avez appris à activer et désactiver des Spatialization au moment de l’exécution, à tester l’application sur un HoloLens 2 ou dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="0a141-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="0a141-136">Dans l’application, vous pouvez maintenant cliquer sur le bouton pour activer et désactiver Spatialization de l’audio.</span><span class="sxs-lookup"><span data-stu-id="0a141-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="0a141-137">Dans le didacticiel suivant, vous allez ajouter un effet de réverbération pour fournir aux sons un sens de la distance.</span><span class="sxs-lookup"><span data-stu-id="0a141-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="0a141-138">Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="0a141-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0a141-139">Didacticiel suivant : 5. utilisation de la réverbération pour ajouter une distance à un son spatial</span><span class="sxs-lookup"><span data-stu-id="0a141-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
