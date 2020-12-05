---
title: Déployer sur l’appareil dans Unreal
description: Guide de déploiement sur un appareil en non réel dans HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, réalité mixte, déployer sur un appareil, PC, documentation, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
appliesto:
- HoloLens 2
ms.openlocfilehash: e811bc1b82aa40e658f9c855b65446483dd8bef2
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609430"
---
# <a name="deploy-to-device-in-unreal"></a>Déployer sur l’appareil dans Unreal

Il existe deux façons de déployer une application inréelle sur HoloLens 2 :
* Directement à partir de l’éditeur inréel
* En tant que package téléchargé via le portail de l’appareil

Les deux options vous obligent à configurer votre HoloLens pour utiliser le portail de l' [appareil](../platform-capabilities-and-apis/using-the-windows-device-portal.md) pour le développement.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Déploiement sur un appareil à partir de l’éditeur inréel

1. Sélectionnez la flèche déroulante en regard du bouton **lancer** . Initialement, l’option de périphérique HoloLens est grisée.

![Options de liste déroulante de lancement](images/unreal/launch-dropdown.png)

2. Ouvrez la **Device Manager** et notez que votre HoloLens ne s’affiche pas automatiquement dans la liste des appareils.

3. Développez la section **Ajouter un appareil non répertorié** .

4. Sélectionnez **HoloLens** en tant que **plateforme**.

5. Entrez l’adresse IP et les informations de port de vos appareils, séparées par un signe deux-points ( :) comme identificateur d’appareil. Par exemple, « 127.0.0.1:10 080 » (en cas de connexion via USB). Utilisez les informations d’identification du nom d’utilisateur et du mot de passe du portail de l’appareil.

6. Appuyez sur **Ajouter** et fermez le gestionnaire de périphériques.
    * En cas d’erreur, telle qu’une adresse incorrecte ou des informations d’identification de l’utilisateur, un message s’affiche dans le journal de sortie.

![Ajout d’un appareil non répertorié](images/unreal/add-unlisted-device.png)

7. Sélectionnez à nouveau la flèche déroulante à côté du bouton de **lancement** : cette fois, vous devriez voir l’appareil HoloLens que vous venez d’ajouter. Sélectionnez l’appareil HoloLens à générer et déployer sur votre HoloLens.

>[!NOTE]
>La génération pour l’appareil peut impliquer la recompilation des nuanceurs (surtout lors de la première exécution). cette opération peut prendre un certain temps. Ne laissez pas l’appareil passer en mode veille tant que l’application n’est pas en cours d’exécution (vous devrez peut-être l’utiliser). Sinon, la compilation du nuanceur échouera.

## <a name="deploying-to-device-via-device-portal"></a>Déploiement sur un appareil via le portail de l’appareil

Vous trouverez des instructions détaillées sur l’empaquetage et le déploiement d’une application dans la [série de didacticiels inréels](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement inréel que nous avons mis en place, vous êtes au cœur de l’étape de déploiement. À partir de là, vous pouvez continuer à ajouter des services avancés :

> [!div class="nextstepaction"]
> [Services avancés](unreal-development-overview.md#5-adding-services)

Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) à tout moment.
