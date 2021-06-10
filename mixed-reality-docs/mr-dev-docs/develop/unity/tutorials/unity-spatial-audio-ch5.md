---
title: Didacticiels audio spatiaux-5. Utilisation de la réverbération pour ajouter une distance à du contenu audio spatial
description: Ajoutez un effet de réverbération pour améliorer le sens de la variation de distance avec l’audio spatial.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer, mélangeur audio, réverbération SFX
ms.openlocfilehash: 6f41fe904c21591915e0ef13b61dc6bff04527fe
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712686"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Utilisation de la réverbération pour ajouter une distance à du contenu audio spatial

## <a name="overview"></a>Vue d’ensemble

Dans le didacticiel précédent, vous avez ajouté Spatialization pour les sons afin de leur offrir un sens de la direction dans ce didacticiel. vous ajouterez un effet de réverbération pour fournir aux sons une idée de la distance.

## <a name="objectives"></a>Objectifs

* Améliorez la distance perçue des sources sonores en ajoutant une réverbération.
* Contrôle la distance perçue du son à l’aide de la distance de l’écouteur à l’hologramme.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Ajouter un groupe de mixage et un effet de réverbération

Dans le didacticiel sur l' [aménagement des sons d’interaction du bouton](unity-spatial-audio-ch2.md), nous avons ajouté un mélangeur. Le mélangeur comprend un **groupe** par défaut nommé **maître**. Étant donné que nous voulons uniquement appliquer un effet de réverbération à certains sons, nous allons ajouter un deuxième groupe pour ces sons. Pour ajouter un groupe, cliquez avec le bouton droit sur le groupe principal dans le **panneau Mixage audio** , choisissez **Ajouter un groupe enfant** et donnez un nom approprié pour exemple d' _espace_:

![Ajouter un groupe enfant](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

Chaque **groupe** a son propre ensemble d’effets. Ajoutez un effet de réverbération au nouveau groupe en cliquant sur **Ajouter...** dans le nouveau groupe, puis en choisissant **réverbe SFX**:

![Ajouter une réverbération SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

Dans la terminologie audio, le son original, unreverberated, est appelé le chemin à l' _état sec_, et l’audio après le filtrage avec le filtre de réverbération est appelé le _chemin d’accès humide_. Les deux chemins d’accès sont envoyés à la sortie audio, et leurs forces relatives dans ce mélange sont appelées la _combinaison humide/sèche_. La combinaison humide/sèche affecte fortement le sens de la distance.

Le **reverbe SFX** comprend des contrôles pour ajuster la combinaison humide/sèche dans l’effet. Étant donné que le plug-in **Microsoft Spatializer** gère le chemin d’accès à sec, nous allons utiliser la **réverbération SFX** uniquement pour le chemin d’accès humide. Dans le volet de l’inspecteur de votre **réverbération SFX**:

* Définir la propriété de **niveau Dry** sur le paramètre le plus bas (-10000 Mo)
* Définir la **propriété Room** sur le paramètre le plus élevé (0 Mo)

![Propriétés de la réverbération SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

Les autres paramètres contrôlent l’apparence de la salle simulée. En particulier, le **temps de désintégration** est lié à la taille de l’espace perçu.

## <a name="enable-reverb-on-the-video-playback"></a>Activer la réverbération sur la lecture vidéo

Il existe deux étapes pour activer la réverbération sur une source audio :

* Acheminer la **source audio** vers le **groupe** approprié
* Définir le plug-in **Microsoft Spatializer** pour transmettre l’audio au **groupe** pour traitement

Dans les étapes suivantes, vous allez ajuster le script pour contrôler le routage audio et attacher un script de contrôle fourni avec le plug-in **Microsoft Spatializer** pour alimenter les données dans le réverbe.

Après avoir sélectionné le **Quad** dans la hiérarchie, cliquez sur **Ajouter un composant** dans la fenêtre de l’inspecteur et ajoutez le niveau d’envoi de l' **effet de pièce (script)**:

![Ajouter un script de niveau d’envoi](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> À moins que vous activiez la fonctionnalité de niveau d’envoi de l' **effet de salle** du plug-in **Microsoft Spatializer** , il n’envoie pas d’audio au moteur audio Unity pour le traitement de l’effet.

Le composant de niveau d’envoi de l' **effet de salle** comprend un contrôle de graphique qui définit le niveau de l’audio envoyé au moteur audio Unity pour le traitement de la réverbération. Pour ouvrir le contrôle de graphique, cliquez sur le niveau d’envoi de l' **effet de salle**.  Cliquez et faites glisser la courbe verte vers le bas pour définir le niveau sur about-30dB :

![Ajuster la courbe de réverbération](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

Ensuite, supprimez les marques de commentaire des 4 lignes commentées dans le script **SpatializeOnOff** . Le script ressemble maintenant à ce qui suit :

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

Une fois que ces lignes ne sont pas commentées, elle ajoute deux propriétés à l’inspecteur du **script SpatializeOnOff**. Affectez-les dans la fenêtre de l’inspecteur du composant **SpatializeOnOff** du **Quad**.

Lorsque l’objet Quad est toujours sélectionné dans la hiérarchie, dans la fenêtre Inspector, localisez le composant **script SpatializeOnOff** et :

* Définir la propriété **groupe d’effets** de la salle sur votre nouveau groupe de mixeur d’effets d’espace
* Définir la propriété de **groupe maître** sur le groupe de mixages principaux

![Spatialiser sur OFF étendu](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a>Félicitations

Vous avez terminé les didacticiels audio spatiaux HoloLens 2 pour Unity. Essayez l’application sur un HoloLens 2 ou Unity. Lorsque vous cliquez sur le bouton dans l’application pour activer Spatialization, le script achemine l’audio de la vidéo vers le groupe d’effets de la pièce pour ajouter une réverbération. Lorsque vous basculez en stéréo, il achemine l’audio vers le groupe maître et évite l’ajout d’une réverbération.

> [!TIP]
> Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
