---
title: Vue d’ensemble du système d’appareil photo
description: Page d’accueil du système d’appareil photo dans MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, appareil photo,
ms.openlocfilehash: e3b7caacaa9baa67fd81f6d32f3fd8c9f123e66d
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121287"
---
# <a name="camera-system"></a>Système de caméra

Le système de caméra permet à Microsoft Mixed Reality Toolkit de configurer et d’optimiser l’appareil photo de l’application afin de l’utiliser dans des applications de réalité mixte. À l’aide du système d’appareil photo, les applications peuvent être écrites pour prendre en charge à la fois les appareils opaques (par exemple, la réalité virtuelle) et les périphériques transparents (par ex. Microsoft HoloLens) sans avoir à écrire du code pour distinguer et s’adapter à chaque type d’affichage.

## <a name="enabling-the-camera-system"></a>Activation du système de caméra

Le système de caméra est géré par l’objet MixedRealityToolkit (ou un autre composant d’inscription de service).

Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit. Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.

1. Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Dans le panneau de l’inspecteur, accédez à la section système de l’appareil photo et vérifiez que l’option **activer l’appareil photo** est cochée.

    ![Activation du système de caméra](../images/camera-system/EnableCameraSystem.png)

3. Sélectionnez l’implémentation du système de l’appareil photo. L’implémentation de classe par défaut fournie par le MRTK est `MixedRealityCameraSystem` .

    ![Sélectionner l’implémentation du système de l’appareil photo](../images/camera-system/SelectCameraSystemType.png)

4. Sélectionner le profil de configuration souhaité

    ![Sélectionner un profil de système d’appareil photo](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>Configuration du système de caméra

### <a name="settings-providers"></a>Fournisseurs de paramètres

![Fournisseurs de paramètres d’appareil photo](../images/camera-system/CameraSettingsProviders.png)

Les fournisseurs de paramètres d’appareil photo activent la configuration spécifique à la plateforme de l’appareil photo. Ces paramètres peuvent inclure des étapes de configuration personnalisées et/ou des composants.

Vous pouvez ajouter des fournisseurs en cliquant sur le bouton **Ajouter un fournisseur de paramètres d’appareil photo** . Vous pouvez les supprimer en cliquant sur le **-** bouton situé à droite du nom du fournisseur.

> [!Note]
> Toutes les plateformes ne nécessitent pas de fournisseur de paramètres d’appareil photo. Si aucun fournisseur n’est compatible avec la plateforme sur laquelle l’application s’exécute, le kit de connaissances Microsoft Mixed Reality Toolkit applique les valeurs par défaut de base.

### <a name="display-settings"></a>Paramètres d'affichage

![Paramètres d’affichage de l’appareil photo](../images/camera-system/CameraDisplaySettings.png)

Les paramètres d’affichage sont spécifiés pour les affichages opaques (par exemple : réalité virtuelle) et transparent (par ex. Microsoft HoloLens). L’appareil photo est configuré au moment de l’exécution à l’aide de ces paramètres.

**Presque clip**

Le plan near clip est le plus proche, en mètres, qu’un objet virtuel peut être à l’appareil photo et qu’il est toujours rendu. Pour un plus grand confort de l’utilisateur, il est recommandé de faire en sorte que cette valeur soit supérieure à zéro. L’image précédente contient des valeurs qui ont été jugées familières sur divers appareils.

**Clip Far**

Le plan de clip FAR est le plus éloigné, en mètres, qu’un objet virtuel peut être à l’appareil photo et est toujours rendu. Pour les appareils transparents, il est recommandé de ne pas dépasser de trop près l’espace du monde réel et de rompre les qualités immersifs de l’application.

**Effacer les indicateurs**

La valeur Clear flags indique comment l’affichage est effacé lorsqu’il est dessiné. Pour les expériences de réalité virtuelle, cette valeur est le plus souvent définie sur skybox. Pour les affichages transparents, il est recommandé d’affecter la valeur couleur à cette option.

**Couleur d’arrière-plan**

Si les indicateurs Clear ne sont pas définis sur skybox, la propriété couleur d’arrière-plan s’affiche.

**Paramètres de qualité**

La valeur des paramètres de qualité indique la qualité graphique qu’Unity doit utiliser lors du rendu de la scène. Le niveau de qualité est un paramètre au niveau du projet et n’est pas spécifique à un appareil photo. Pour plus d’informations, consultez l’article sur la [qualité](https://docs.unity3d.com/Manual/class-QualitySettings.html) dans la documentation d’Unity.

## <a name="see-also"></a>Voir aussi

- [Documentation de l’API système de l’appareil photo](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Création d’un fournisseur de paramètres d’appareil photo](create-settings-provider.md)
