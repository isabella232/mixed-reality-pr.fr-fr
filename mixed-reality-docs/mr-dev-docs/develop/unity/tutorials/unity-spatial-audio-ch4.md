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
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. activation et désactivation de Spatialization au moment de l’exécution

## <a name="overview"></a>Vue d’ensemble

Dans ce didacticiel, vous allez apprendre à activer et à désactiver les Spatialization au moment de l’exécution et à les tester dans l’éditeur Unity et dans HoloLens 2.

## <a name="objectives"></a>Objectifs

* Ajouter un nouveau script pour contrôler Spatialization sur un objet de jeu
* Piloter le script de contrôle Spatialization à partir d’actions Button

## <a name="add-spatialization-control-script"></a>Ajouter un script de contrôle Spatialization

 Cliquez avec le bouton droit dans la fenêtre du projet et choisissez **créer**  >  un **script c#** pour créer un script c#, entrez un nom approprié pour le script, par exemple, _SpatializeOnOff_:

![Création du script](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

Double-cliquez sur le script dans la fenêtre projet pour l’ouvrir dans Visual Studio. Remplacez le contenu du script par défaut par ce qui suit :

> [!NOTE]
> Plusieurs lignes du script sont commentées. Ces lignes ne seront pas commentées dans le [chapitre suivant : utilisation de la réverbération pour ajouter une distance à un son spatial](unity-spatial-audio-ch5.md).

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
> Pour activer ou désactiver le Spatialization, le script ajuste uniquement la propriété **spatialBlend** , en laissant la propriété **Spatialization** activée. Dans ce mode, Unity applique toujours la courbe du **volume** . Dans le cas contraire, si l’utilisateur devait désactiver Spatialization en loin de la source, il entendrait l’augmentation soudaine du volume.
> Si vous préférez désactiver complètement Spatialization, modifiez le script pour ajuster également la propriété booléenne **Spatialization** de la variable **ObjetSource** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Joindre votre script et le piloter à partir du bouton

Sélectionnez **Quad** dans la hiérarchie et dans la fenêtre Inspector, utilisez le bouton Ajouter un composant pour ajouter **SpatializeOnOff (script)**

![Ajouter un script à quatre cœurs](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

Dans la hiérarchie, recherchez **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.

Lorsque l’objet **Quad** est toujours sélectionné dans la hiérarchie, dans la fenêtre Inspector, localisez le composant **spatialiser on off (script)** et faites glisser le composant **TextMeshPro** du PressableButtonHoloLens2.

![Rechercher l’objet PressableButtonHoloLens2 dans la hiérarchie](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

Pour définir le bouton pour appeler le script **SpatializeOnOff** quand le bouton est relâché, vous devez configurer un script d’interaction.

Dans la fenêtre hiérarchie, sélectionnez **PressableButtonHoloLens2**. Dans la fenêtre de l’inspecteur, localisez le composant **(script) pouvant être interagi** , puis cliquez sur l’icône + sous l’événement OnClick ().

* Avec l’objet **PressableButtonHoloLens2** toujours sélectionné dans la fenêtre hiérarchie, cliquez et faites glisser l’objet **quadruple** à partir de la fenêtre hiérarchie dans le champ **aucun (objet)** vide de l’événement que vous venez d’ajouter pour que l’objet ButtonParent écoute l’événement de clic de bouton à partir de ce bouton :

* Cliquez sur la liste déroulante **No Function** du même événement. Sélectionnez ensuite **SpatializeOnOff**  >  **SwapSpatialization ()** pour activer et désactiver le son spatial

![Paramètres d’action du bouton](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a>Félicitations

Dans ce didacticiel, vous avez appris à activer et désactiver des Spatialization au moment de l’exécution, à tester l’application sur un HoloLens 2 ou dans l’éditeur Unity. Dans l’application, vous pouvez maintenant cliquer sur le bouton pour activer et désactiver Spatialization de l’audio.

Dans le didacticiel suivant, vous allez ajouter un effet de réverbération pour fournir aux sons un sens de la distance.

> [!TIP]
> Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Didacticiel suivant : 5. utilisation de la réverbération pour ajouter une distance à un son spatial](unity-spatial-audio-ch5.md)
