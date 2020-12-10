---
title: Didacticiels audio spatial-4. Activation et désactivation de contenu audio spatial au moment de l’exécution
description: Utilisez un bouton pour activer et désactiver le Spatialization de l’audio au moment de l’exécution.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer
ms.openlocfilehash: c9e510e544962c5d1a4c462d20dafa222c6a5289
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002604"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a>Activation et désactivation de Spatialization au moment de l’exécution

## <a name="objectives"></a>Objectifs
Dans ce quatrième chapitre, vous allez :
* Ajouter un nouveau script pour contrôler Spatialization sur un objet de jeu
* Piloter le script de contrôle Spatialization à partir d’actions Button

## <a name="add-spatialization-control-script"></a>Ajouter un script de contrôle Spatialization
Cliquez avec le bouton droit dans le volet **projet** et créez un script c# en choisissant **créer > script c#**. Nommez votre script « SpatializeOnOff ».

![Création du script](images/spatial-audio/create-script.png)

Double-cliquez sur le script dans le volet **projet** pour l’ouvrir dans Visual Studio. Remplacez le contenu du script par défaut par ce qui suit :

> [!NOTE]
> Plusieurs lignes du script sont commentées. Ces lignes ne seront pas commentées dans le [Chapitre 5](unity-spatial-audio-ch5.md).

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
> Pour activer ou désactiver Spatialization, le script ajuste uniquement la propriété **spatialBlend** , en laissant la propriété **Spatialization** activée. Dans ce mode, Unity applique toujours la courbe du **volume** . Dans le cas contraire, si l’utilisateur devait désactiver Spatialization en loin de la source, il entendrait l’augmentation soudaine du volume. <br> <br>
> Si vous préférez désactiver complètement Spatialization, modifiez le script pour ajuster également la propriété booléenne **Spatialization** de la variable **ObjetSource** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Joindre votre script et le piloter à partir du bouton
Dans le volet de l' **inspecteur** du **Quad**, cliquez sur **Ajouter un composant** et ajoutez le script **spatial on off** :

![Ajouter un script à quatre cœurs](images/spatial-audio/add-script-to-quad.png)

Sur le composant **spatialiser on off** du **Quad**:
1. Recherchez l’objet **PressableButtonHoloLens2-> IconAndText-> TextMeshPro** dans la **hiérarchie**:

![Rechercher l’objet PressableButtonHoloLens2 dans la hiérarchie](images/spatial-audio/pressable-button-object.png)

2. Faites glisser le sujet **TextMeshPro** dans le champ **ButtonTextObject** du composant **spatialiser sur OFF** .

Une fois ces modifications effectuées, le composant **spatial on off** du **Quad** ressemble à ce qui suit :

![Spatialiser en dehors de la base](images/spatial-audio/spatialize-on-off-basic.png)

Pour définir le bouton pour appeler le script **spatial on off** lorsque le bouton est relâché, ouvrez le volet **Inspector** de l’objet **PressableButtonHoloLens2** , recherchez **le composant** interactif et :
1. Recherche la région **OnClick ()** de la sous-section **événements**
2. Faites glisser le **Quad** de la **hiérarchie** dans l’emplacement de l’objet cible.
3. Sélectionnez **SpatializeOnOff. SwapSpatialization** dans la zone de liste déroulante action.

Une fois ces modifications effectuées, le composant **interagissant** peut se présenter comme suit :

![Paramètres d’action du bouton](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a>Étapes suivantes
Essayez votre application sur un HoloLens 2 ou dans l’éditeur Unity. Dans l’application, vous pouvez maintenant toucher le bouton pour activer et désactiver Spatialization sur la vidéo. Lors du test dans l’éditeur Unity, appuyez sur la barre d’espace et faites défiler la molette pour activer la simulation manuelle. 

> [!div class="nextstepaction"]
> [Chapitre 5](unity-spatial-audio-ch5.md) 

