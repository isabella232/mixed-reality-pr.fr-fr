---
title: Déployer sur l’appareil dans Unreal
description: Guide de déploiement sur un appareil en non réel dans HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, réalité mixte, déployer sur un appareil, PC, documentation
appliesto:
- HoloLens 2
ms.openlocfilehash: abd5e5c28ec5e66c4f73df8edf5e0ac0212d170a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679815"
---
# <a name="deploy-to-device-in-unreal"></a>Déployer sur l’appareil dans Unreal

## <a name="overview"></a>Vue d’ensemble
Il existe deux façons de déployer une application inréelle sur HoloLens 2 :
* Directement à partir de l’éditeur inréel
* En tant que package téléchargé via le portail de l’appareil

Les deux options vous obligent à configurer votre HoloLens pour utiliser le portail de l' [appareil](../platform-capabilities-and-apis/using-the-windows-device-portal.md) pour le développement.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Déploiement sur un appareil à partir de l’éditeur inréel

1. Cliquez sur la flèche déroulante en regard du bouton **lancer** . Initialement, l’option de périphérique HoloLens est grisée.

![Options de liste déroulante de lancement](images/unreal/launch-dropdown.png)

2. Ouvrez le **Device Manager** . Notez que votre HoloLens ne s’affiche pas automatiquement dans la liste des appareils.

3. Développez la section **Ajouter un appareil non répertorié** .

4. Sélectionnez **HoloLens** en tant que **plateforme** .

5. Entrez l’adresse IP et les informations de port de vos appareils, séparées par un signe deux-points ( :) comme identificateur d’appareil. Par exemple, « 127.0.0.1:10 080 » (en cas de connexion via USB). Utilisez les informations d’identification du nom d’utilisateur et du mot de passe du portail de l’appareil.

6. Appuyez sur **Ajouter** et fermez le gestionnaire de périphériques.
    * Dans le cas d’une erreur (telle qu’une adresse incorrecte, un nom d’utilisateur ou un mot de passe), un message est imprimé dans le journal de sortie.

![Ajout d’un appareil non répertorié](images/unreal/add-unlisted-device.png)

7. Cliquez à nouveau sur la flèche déroulante en regard du bouton **lancer** . cette fois-ci, vous devriez voir l’appareil HoloLens que vous venez d’ajouter. Sélectionnez l’appareil HoloLens à générer et déployer sur votre HoloLens.

>[!NOTE]
>La génération pour l’appareil peut impliquer la recompilation des nuanceurs (surtout lors de la première exécution). cette opération peut prendre un certain temps. Ne laissez pas l’appareil passer en mode veille tant que l’application n’est pas en cours d’exécution (vous devrez peut-être l’utiliser). Sinon, la compilation du nuanceur échouera.

## <a name="deploying-to-device-via-device-portal"></a>Déploiement sur un appareil via le portail de l’appareil

Vous trouverez des instructions détaillées sur l' [empaquetage et le déploiement d’une application](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) dans la dernière section du prise en main avec des séries de didacticiels inréels.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours du point de contrôle de développement inréel que nous avons disposé, vous êtes au cœur de l’étape de déploiement. À partir de là, vous pouvez passer à l’ajout de services avancés :

> [!div class="nextstepaction"]
> [Services avancés](unreal-development-overview.md#5-adding-services)

Vous pouvez toujours revenir aux [points de contrôle de développement inréels](unreal-development-overview.md#4-deploying-to-a-device) à tout moment.
