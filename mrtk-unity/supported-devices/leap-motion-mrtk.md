---
title: Utilisation de Leap Motion
description: Documentation à configurer pour le mouvement LEAP
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, mouvement Leap,
ms.openlocfilehash: e675521a3a688bc0f9f8afdf1bdc01e583d0b47808d0aaff8b2eff263fce35bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222904"
---
# <a name="using-leap-motion"></a>Utilisation de Leap Motion

Un [contrôleur de mouvement LEAP](https://www.ultraleap.com/product/leap-motion-controller/) est requis pour utiliser ce fournisseur de données.

le Fournisseur de données de mouvement Leap active le suivi articulé pour VR et peut être utile pour le prototypage rapide dans l’éditeur.  Le fournisseur de données peut être configuré pour utiliser le contrôleur de mouvement LEAP monté sur un casque ou placé sur un bureau.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

Ce fournisseur peut être utilisé dans l’éditeur et sur l’appareil sur la plateforme autonome.  Il peut également être utilisé dans l’éditeur sur la plateforme UWP, mais pas dans une génération UWP.

| Version de MRTK | Versions des modules Unity de mouvement LEAP prises en charge |
| --- | --- |
|2.6. x | 4.5.0, 4.5.1|
|2.7. x| 4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Utilisation du suivi des mouvements LEAP (par Ultraleap) dans MRTK

1. Importation de MRTK et des modules Unity de mouvement LEAP
    - Installer le dernier [Kit de développement logiciel (SDK) LEAP](https://developer.leapmotion.com/releases/?category=orion) le plus récent s’il n’est pas déjà installé
    - importez le **Microsoft. MixedReality. Shared Computer Toolkit.** Package de base dans le projet Unity.
    - Téléchargez et importez la dernière version des [modules Unity LEAP](https://developer.leapmotion.com/unity) dans le projet
        - Importer uniquement le package de **base** dans les modules Unity

1. Intégrer les modules LEAP Motion Unity avec MRTK
    - une fois les modules unity dans le projet, accédez à la **réalité mixte Shared Computer Toolkit** les  >    >  **modules unity de mouvement leap**
    > [!NOTE]
    > l’intégration des Modules unity à MRTK ajoute 10 définitions d’assembly au projet et ajoute des références à **Microsoft. MixedReality. Shared Computer Toolkit. Définition d’assembly Providers. LeapMotion** . Vérifiez que Visual Studio est fermé.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. ajout de la Fournisseur de données de mouvement Leap
    - Créer une nouvelle scène Unity
    - ajoutez MRTK à la scène en accédant à la **réalité mixte Shared Computer Toolkit**  >  **ajouter à la scène et configurer**
    - Sélectionnez l’objet de jeu MixedRealityToolkit dans la hiérarchie, puis sélectionnez **copier et personnaliser** pour cloner le profil de réalité mixte par défaut.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - Sélectionner le profil de configuration **d’entrée**

    ![Profil de configuration d’entrée 1](../images/cross-platform/InputConfigurationProfile.png)

    - Sélectionnez **clone** dans le profil de système d’entrée pour permettre la modification.

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - ouvrez la section **fournisseurs de données d’entrée** , sélectionnez **ajouter des Fournisseur de données** en haut, un nouveau fournisseur de données sera ajouté à la fin de la liste.  ouvrez le nouveau fournisseur de données et définissez le **Type** sur **Microsoft. MixedReality. Shared Computer Toolkit. LeapMotion. Input > LeapMotionDeviceManager**

    ![Fournisseur de données d’ajout Leap](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - Sélectionnez **clone** pour modifier les paramètres de mouvement LEAP par défaut.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - le Fournisseur de données de mouvement leap contient la `LeapControllerOrientation` propriété qui correspond à l’emplacement du contrôleur de mouvement leap. `LeapControllerOrientation.Headset` indique que le contrôleur est monté sur un casque. `LeapControllerOrientation.Desk` indique que le contrôleur est placé à plat sur le bureau. La valeur par défaut est `LeapControllerOrientation.Headset` .
    - Chaque orientation de contrôleur contient des propriétés de décalage :
      - Les propriétés de décalage d’orientation du **casque** reflètent les propriétés de décalage dans le composant LeapXRServiceProvider.  Le `LeapVRDeviceOffsetMode` a trois options : par défaut, décalage manuel de l’en-tête et transformation.  Si le mode de décalage est défini par défaut, aucun décalage n’est appliqué au contrôleur de mouvement LEAP.  Le mode de décalage manuel en tête permet la modification de trois propriétés : `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` et `LeapVRDeviceTiltX` .  Les valeurs des propriétés de décalage de l’axe sont ensuite appliquées au placement du contrôleur par défaut.  Le mode de décalage de transformation contient la `LeapVRDeviceOrigin` propriété de transformation qui spécifie une nouvelle origine pour le contrôleur de mouvement LEAP.
      - L’orientation du **Bureau** contient la `LeapControllerOffset` propriété qui définit la position d’ancrage des aiguilles du bureau.  Le décalage est calculé par rapport à la position de la caméra principale et la valeur par défaut est (0,-0,2, 0,35) pour s’assurer que les mains s’affichent au premier plan et en vue de l’appareil photo.

        > [!NOTE]
        > Les propriétés de décalage dans le profil sont appliquées une fois au démarrage de l’application.  Pour modifier les valeurs lors de l’exécution, procurez-vous le fournisseur de service de mouvement LEAP à partir de la Gestionnaire de périphériques de mouvement LEAP :
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` et `ExitPinchDistance` sont les seuils de distance pour la détection de mouvement pincement/taraudage.  Le mouvement de pincement est calculé en mesurant la distance entre l’info-bulle de l’index et la pointe du curseur.  Pour déclencher un événement lors de l’entrée vers le dessous, la valeur par défaut `EnterPinchDistance` est 0,02.  Pour déclencher un événement lors de l’entrée vers le haut (en quittant le pincement), la distance par défaut entre l’info-bulle de l’index et l’info-bulle est 0,05.

    `LeapControllerOrientation`: Casque (par défaut) |  `LeapControllerOrientation`: Bureau
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. test de la Fournisseur de données de mouvement Leap
    - une fois que le Fournisseur de données de mouvement Leap a été ajouté au profil de système d’entrée, appuyez sur play, déplacez votre main devant le contrôleur de mouvement leap. vous devriez voir la représentation conjointe de la main.

1. Génération de votre projet
    - accédez à **fichier > générer Paramètres**
    - seules les builds autonomes sont prises en charge si vous utilisez la Fournisseur de données de mouvement Leap.
    - pour obtenir des instructions sur l’utilisation d’un Windows Mixed Reality casque pour les builds autonomes, consultez la page [création et déploiement de MRTK sur des casques WMR (autonomes)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).

## <a name="getting-the-hand-joints"></a>Obtention des articulations de la main

l’obtention de jointures à l’aide de la Fournisseur de données de mouvement Leap est identique à la récupération conjointe de la main pour un MRTK articulé.  Pour plus d’informations, consultez [suivi manuel](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).

avec MRTK dans une scène unity et le mouvement Leap Fournisseur de données ajouté comme Fournisseur de données d’entrée dans le profil de système d’entrée, créez un objet de jeu vide et attachez l’exemple de script suivant.

Ce script est un exemple simple de la façon dont vous pouvez récupérer la pose de l’articulation de Palm dans une main de mouvement LEAP.  Une sphère suit la main gauche, tandis qu’un cube suit la main à droite.

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a>Astuce du flux de travail de l’éditeur Unity

l’utilisation de la Fournisseur de données de mouvement Leap ne nécessite pas de casque de VR.  Les modifications apportées à une application MRTK peuvent être testées dans l’éditeur avec les aiguilles de l’avant sans casque.

Les mains des mouvements LEAPS s’affichent dans l’éditeur, sans un casque de VR branché.  Si le `LeapControllerOrientation` est défini sur **casque**, le contrôleur de mouvement LEAP devra être maintenu d’une main à l’autre.

> [!NOTE]
> Si l’appareil photo est déplacé à l’aide de clés WASD dans l’éditeur et que le `LeapControllerOrientation` **casque** est, les mains ne suivent pas l’appareil photo. Les mains suivent uniquement le mouvement de l’appareil photo si un casque VR est branché alors que le `LeapControllerOrientation` est défini comme **casque**.  Les aiguilles du Bond suivent le mouvement de l’appareil photo dans l’éditeur si le `LeapControllerOrientation` est défini sur **Bureau**.

## <a name="removing-leap-motion-from-the-project"></a>Suppression du mouvement LEAP de la Project

1. accédez à la **réalité mixte Shared Computer Toolkit**  >    >  **Modules d’unity de mouvement leap distincts**
    - autorisez l’actualisation unity en tant que références dans **Microsoft. MixedReality. Shared Computer Toolkit. Le fichier Providers. LeapMotion. asmdef** est modifié dans cette étape
1. Fermer Unity
1. fermer Visual Studio, s’il est ouvert
1. Ouvrez l’Explorateur de fichiers et accédez à la racine du projet MRTK Unity.
    - Supprimer le répertoire **UnityProjectName/Library**
    - Supprimer le répertoire **UnityProjectName/Assets/plugin/LeapMotion**
    - Supprimer le fichier **UnityProjectName/Assets/plugin/LeapMotion. meta**
1. Rouvrir Unity

Dans Unity 2018,4, vous remarquerez peut-être que des erreurs subsistent dans la console après la suppression de la bibliothèque et des ressources de noyau de mouvement LEAP.
Si les erreurs sont consignées après la réouverture, redémarrez Unity.

## <a name="common-errors"></a>Erreurs courantes

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Le mouvement LEAP n’a pas été intégré à MRTK

Pour tester si les modules Unity de mouvement LEAP sont intégrés à MRTK :

- accédez à la **réalité mixte Shared Computer Toolkit > utilitaires > Motion Motion > vérifier l’état d’intégration**
  - Une fenêtre contextuelle s’affiche avec un message indiquant si les modules d’unité de mouvement LEAP sont intégrés à MRTK.
- Si le message indique que les ressources n’ont pas été intégrées :
  - S’assurer que les modules Unity de mouvement LEAP se trouvent dans le projet
  - Assurez-vous que la version ajoutée est prise en charge, consultez le tableau en haut de la page pour connaître les versions prises en charge.
  - essayez la Shared Computer Toolkit de la **réalité mixte > utilitaires > le mouvement leap > intégrer les Modules unity de mouvement leap**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>Échec de la copie des HLAPI multijoueur de l’assembly

Cette erreur peut être consignée lors de l’importation des ressources principales de l’Unity de mouvement LEAP :

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**Solution**

- Une solution à bref terme consiste à redémarrer Unity. Pour plus d’informations, consultez le [problème 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) .

## <a name="leap-motion-example-scene"></a>Exemple de scène de mouvement LEAP

l’exemple de scène utilise le profil DefaultLeapMotionConfiguration et détermine si le projet unity a été configuré correctement pour utiliser le Fournisseur de données de mouvement Leap.

l’exemple de scène est contenu dans **Microsoft. MixedReality. Shared Computer Toolkit. Exemples** de package dans le répertoire **MRTK/examples/démos/HandTracking/** .  

## <a name="see-also"></a>Voir aussi

- [Fournisseurs d’entrée](../features/input/input-providers.md)
- [Suivi de la main](../features/input/hand-tracking.md)
