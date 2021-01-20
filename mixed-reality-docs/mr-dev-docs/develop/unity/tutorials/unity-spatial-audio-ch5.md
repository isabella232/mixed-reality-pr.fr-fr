---
title: Didacticiels audio spatiaux-5. Utilisation de la réverbération pour ajouter une distance à du contenu audio spatial
description: Ajoutez un effet de réverbération pour améliorer le sens de la variation de distance avec l’audio spatial.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer, mélangeur audio, réverbération SFX
ms.openlocfilehash: 3d19bb0b22c507eb692a752aa318ecb82a1cf2f7
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578376"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="59657-105">5. Utilisation de la réverbération pour ajouter une distance à du contenu audio spatial</span><span class="sxs-lookup"><span data-stu-id="59657-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="59657-106">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="59657-106">Overview</span></span>

<span data-ttu-id="59657-107">Dans le didacticiel précédent, vous avez ajouté Spatialization pour les sons afin de leur offrir un sens de la direction dans ce didacticiel. vous ajouterez un effet de réverbération pour fournir aux sons une idée de la distance.</span><span class="sxs-lookup"><span data-stu-id="59657-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="59657-108">Objectifs</span><span class="sxs-lookup"><span data-stu-id="59657-108">Objectives</span></span>

* <span data-ttu-id="59657-109">Améliorez la distance perçue des sources sonores en ajoutant une réverbération.</span><span class="sxs-lookup"><span data-stu-id="59657-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="59657-110">Contrôle la distance perçue du son à l’aide de la distance de l’écouteur à l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="59657-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="59657-111">Ajouter un groupe de mixage et un effet de réverbération</span><span class="sxs-lookup"><span data-stu-id="59657-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="59657-112">Dans le didacticiel sur l' [aménagement des sons d’interaction du bouton](unity-spatial-audio-ch2.md), nous avons ajouté un mélangeur.</span><span class="sxs-lookup"><span data-stu-id="59657-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="59657-113">Le mélangeur comprend un **groupe** par défaut nommé **maître**.</span><span class="sxs-lookup"><span data-stu-id="59657-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="59657-114">Étant donné que nous voulons uniquement appliquer un effet de réverbération à certains sons, nous allons ajouter un deuxième groupe pour ces sons.</span><span class="sxs-lookup"><span data-stu-id="59657-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="59657-115">Pour ajouter un groupe, cliquez avec le bouton droit sur le groupe principal dans le **panneau Mixage audio** , choisissez **Ajouter un groupe enfant** et donnez un nom approprié pour exemple d' _espace_:</span><span class="sxs-lookup"><span data-stu-id="59657-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![Ajouter un groupe enfant](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

<span data-ttu-id="59657-117">Chaque **groupe** a son propre ensemble d’effets.</span><span class="sxs-lookup"><span data-stu-id="59657-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="59657-118">Ajoutez un effet de réverbération au nouveau groupe en cliquant sur **Ajouter...** dans le nouveau groupe, puis en choisissant **réverbe SFX**:</span><span class="sxs-lookup"><span data-stu-id="59657-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Ajouter une réverbération SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

<span data-ttu-id="59657-120">Dans la terminologie audio, le son original, unreverberated, est appelé le chemin à l' _état sec_, et l’audio après le filtrage avec le filtre de réverbération est appelé le _chemin d’accès humide_.</span><span class="sxs-lookup"><span data-stu-id="59657-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="59657-121">Les deux chemins d’accès sont envoyés à la sortie audio, et leurs forces relatives dans ce mélange sont appelées la _combinaison humide/sèche_.</span><span class="sxs-lookup"><span data-stu-id="59657-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="59657-122">La combinaison humide/sèche affecte fortement le sens de la distance.</span><span class="sxs-lookup"><span data-stu-id="59657-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="59657-123">Le **reverbe SFX** comprend des contrôles pour ajuster la combinaison humide/sèche dans l’effet.</span><span class="sxs-lookup"><span data-stu-id="59657-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="59657-124">Étant donné que le plug-in **Microsoft Spatializer** gère le chemin d’accès à sec, nous allons utiliser la **réverbération SFX** uniquement pour le chemin d’accès humide.</span><span class="sxs-lookup"><span data-stu-id="59657-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="59657-125">Dans le volet de l’inspecteur de votre **réverbération SFX**:</span><span class="sxs-lookup"><span data-stu-id="59657-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="59657-126">Définir la propriété de **niveau Dry** sur le paramètre le plus bas (-10000 Mo)</span><span class="sxs-lookup"><span data-stu-id="59657-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="59657-127">Définir la **propriété Room** sur le paramètre le plus élevé (0 Mo)</span><span class="sxs-lookup"><span data-stu-id="59657-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![Propriétés de la réverbération SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

<span data-ttu-id="59657-129">Les autres paramètres contrôlent l’apparence de la salle simulée.</span><span class="sxs-lookup"><span data-stu-id="59657-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="59657-130">En particulier, le **temps de désintégration** est lié à la taille de l’espace perçu.</span><span class="sxs-lookup"><span data-stu-id="59657-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="59657-131">Activer la réverbération sur la lecture vidéo</span><span class="sxs-lookup"><span data-stu-id="59657-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="59657-132">Il existe deux étapes pour activer la réverbération sur une source audio :</span><span class="sxs-lookup"><span data-stu-id="59657-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="59657-133">Acheminer la **source audio** vers le **groupe** approprié</span><span class="sxs-lookup"><span data-stu-id="59657-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="59657-134">Définir le plug-in **Microsoft Spatializer** pour transmettre l’audio au **groupe** pour traitement</span><span class="sxs-lookup"><span data-stu-id="59657-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="59657-135">Dans les étapes suivantes, vous allez ajuster le script pour contrôler le routage audio et attacher un script de contrôle fourni avec le plug-in **Microsoft Spatializer** pour alimenter les données dans le réverbe.</span><span class="sxs-lookup"><span data-stu-id="59657-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="59657-136">Après avoir sélectionné le **Quad** dans la hiérarchie, cliquez sur **Ajouter un composant** dans la fenêtre de l’inspecteur et ajoutez le niveau d’envoi de l' **effet de pièce (script)**:</span><span class="sxs-lookup"><span data-stu-id="59657-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![Ajouter un script de niveau d’envoi](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="59657-138">À moins que vous activiez la fonctionnalité de niveau d’envoi de l' **effet de salle** du plug-in **Microsoft Spatializer** , il n’envoie pas d’audio au moteur audio Unity pour le traitement de l’effet.</span><span class="sxs-lookup"><span data-stu-id="59657-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="59657-139">Le composant de niveau d’envoi de l' **effet de salle** comprend un contrôle de graphique qui définit le niveau de l’audio envoyé au moteur audio Unity pour le traitement de la réverbération.</span><span class="sxs-lookup"><span data-stu-id="59657-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="59657-140">Pour ouvrir le contrôle de graphique, cliquez sur le niveau d’envoi de l' **effet de salle**.</span><span class="sxs-lookup"><span data-stu-id="59657-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="59657-141">Cliquez et faites glisser la courbe verte vers le bas pour définir le niveau sur about-30dB :</span><span class="sxs-lookup"><span data-stu-id="59657-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![Ajuster la courbe de réverbération](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

<span data-ttu-id="59657-143">Ensuite, supprimez les marques de commentaire des 4 lignes commentées dans le script **SpatializeOnOff** .</span><span class="sxs-lookup"><span data-stu-id="59657-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="59657-144">Le script ressemble maintenant à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="59657-144">The script will now look like this:</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

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
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="59657-145">Une fois que ces lignes ne sont pas commentées, elle ajoute deux propriétés à l’inspecteur du **script SpatializeOnOff**.</span><span class="sxs-lookup"><span data-stu-id="59657-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="59657-146">Affectez-les dans la fenêtre de l’inspecteur du composant **SpatializeOnOff** du **Quad**.</span><span class="sxs-lookup"><span data-stu-id="59657-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="59657-147">Lorsque l’objet Quad est toujours sélectionné dans la hiérarchie, dans la fenêtre Inspector, localisez le composant **script SpatializeOnOff** et :</span><span class="sxs-lookup"><span data-stu-id="59657-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="59657-148">Définir la propriété **groupe d’effets** de la salle sur votre nouveau groupe de mixeur d’effets d’espace</span><span class="sxs-lookup"><span data-stu-id="59657-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="59657-149">Définir la propriété de **groupe maître** sur le groupe de mixages principaux</span><span class="sxs-lookup"><span data-stu-id="59657-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatialiser sur OFF étendu](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="59657-151">Félicitations</span><span class="sxs-lookup"><span data-stu-id="59657-151">Congratulations</span></span>

<span data-ttu-id="59657-152">Vous avez terminé les didacticiels audio spatiaux HoloLens 2 pour Unity.</span><span class="sxs-lookup"><span data-stu-id="59657-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="59657-153">Essayez l’application sur un HoloLens 2 ou Unity.</span><span class="sxs-lookup"><span data-stu-id="59657-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="59657-154">Lorsque vous cliquez sur le bouton dans l’application pour activer Spatialization, le script achemine l’audio de la vidéo vers le groupe d’effets de la pièce pour ajouter une réverbération.</span><span class="sxs-lookup"><span data-stu-id="59657-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="59657-155">Lorsque vous basculez en stéréo, il achemine l’audio vers le groupe maître et évite l’ajout d’une réverbération.</span><span class="sxs-lookup"><span data-stu-id="59657-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="59657-156">Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="59657-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
