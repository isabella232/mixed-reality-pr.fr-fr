---
title: Son spatial dans Unreal
description: Découvrez les tenants et aboutissants du plug-in de son spatial pour les applications de réalité mixte Unreal pour les appareils HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, communication à distance, réalité mixte, développement, démarrage, fonctionnalités, nouveau projet, émulateur, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, son spatial
ms.openlocfilehash: c9d05fdb2aa2486c301822636a86262650ad14f7cad1359a5c4b564bf324204e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218695"
---
# <a name="spatial-audio-in-unreal"></a>Son spatial dans Unreal

Contrairement à la vue, les êtres humains entendent les sons ambiants à 360 degrés. Le son spatial émule le fonctionnement de l’audition humaine, en fournissant les signaux nécessaires pour identifier les emplacements sonores dans l’espace. Quand vous ajoutez un son spatial dans vos applications de réalité mixte, vous améliorez le niveau d’immersion de l’expérience de votre utilisateur.  

Le traitement du son spatial en haute qualité est complexe : HoloLens 2 est donc fourni avec un matériel dédié pour le traitement de ces objets audio.  Pour pouvoir accéder à cette prise en charge du traitement matériel, vous devez installer le plug-in **MicrosoftSpatialSound** dans votre projet Unreal. Cet article vous guide tout au long de l’installation et de la configuration de ce plug-in, et vous oriente vers des ressources plus approfondies.

## <a name="installing-the-microsoft-spatial-sound-plugin"></a>Installation du plug-in Microsoft Spatial Sound

La première étape pour ajouter un son spatial à votre projet consiste à installer le plug-in de son spatial Microsoft, que vous trouverez en :

1. Cliquant sur **Modifier > Plug-ins** et en recherchant **MicrosoftSpatialSound** dans la zone de recherche.
2. Cochant la case **Activé** dans le plug-in **MicrosoftSpatialSound**.
3. Redémarrant l’éditeur Unreal en sélectionnant **Redémarrer maintenant** à partir de la page de plug-ins.

> [!NOTE]
> Si ce n’est déjà fait, vous devez installer les plug-ins **Microsoft Windows Mixed Reality** et **HoloLens** en suivant les instructions fournies dans la section **[Initialisation de votre projet](tutorials/unreal-uxt-ch2.md)** de notre série de tutoriels Unreal.

![Plug-in audio spatial Unreal](images/unreal-spatial-audio-img-01.png)

Une fois l’éditeur redémarré, vous pouvez commencer votre projet.

## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a>Définition du plug-in de spatialisation pour la plateforme HoloLens 2

La configuration du plug-in de spatialisation s’effectue sur la base de chaque plateforme.  Pour activer le plug-in Microsoft Spatial Sound pour HoloLens 2, effectuez les étapes suivantes :
1. Sélectionnez **Edit > Project Settings**, faites défiler jusqu’à **Platforms, puis cliquez sur **HoloLens**.
2. Développez les propriétés **Audio** et affectez la valeur **Microsoft Spatial Sound** au champ **Spatialization Plugin**.

![Plug-in de spatialisation pour la plateforme HoloLens](images/unreal-spatial-audio-img-02.png)

Si vous prévoyez d’afficher un aperçu de votre application dans l’éditeur Unreal sur un PC de bureau, vous devez répéter les étapes ci-dessus pour la plateforme **Windows** :

![Plug-in de spatialisation pour la plateforme Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a>Activation de l’audio spatial sur votre station de travail

L’audio spatial est désactivé par défaut sur les versions de bureau de Windows. Pour l’activer, effectuez les étapes suivantes :
* Cliquez avec le bouton droit sur l’icône de **volume** dans la barre des tâches.
    + Choisissez **Son spatial-> Windows Sonic pour casque** pour obtenir la meilleure représentation de ce que vous entendrez sur HoloLens 2.

![Plug-in de spatialisation](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
>Ce paramètre est obligatoire uniquement si vous envisagez de tester votre projet dans l’éditeur Unreal.

## <a name="creating-attenuation-objects"></a>Création d’objets d’atténuation

Une fois que vous avez installé et configuré les plug-ins nécessaires :
1. Recherchez un acteur **Ambient Sound** (Son ambiant) dans la fenêtre **Place Actors** (Placer des acteurs), puis faites-le glisser dans la fenêtre **Scene**.

![Ajout d’un acteur de son ambiant](images/unreal-spatial-audio-img-07.png)

2. Faites de l’acteur **Ambient Sound** un enfant d’un visuel dans votre scène.
    * Un acteur Ambient Sound n’a pas de représentation visuelle par défaut, donc vous n’entendrez un son que de sa position dans la scène. Si vous l’attachez à un visuel, vous pouvez voir et déplacer l’acteur comme n’importe quel autre actif multimédia.

3.  Cliquez avec le bouton droit sur **Content Browser** (Navigateur de contenu) et sélectionnez **Create Advanced Asset -> Sounds -> Sound Attenuation** (Créer un actif multimédia avancé -> Sons -> Atténuation du son) :

![Création d’un actif multimédia d’atténuation du son](images/unreal-spatial-audio-img-06.png)

4. Cliquez avec le bouton droit sur l’élément **Sound Attenuation** dans la fenêtre **Content Browser** et sélectionnez l’option **Edit** pour afficher la fenêtre de propriétés.
    * Basculez l’option **Spatialization Method** sur **Binaural**.

![Définir la méthode de spatialisation](images/unreal-spatial-audio-img-03.png)

5. Sélectionnez l’acteur **Ambient Sound** et faites défiler jusqu’à la section **Attenuation** dans le panneau **Details**.
    * Affectez l’actif **Sound Attenuation** que vous avez créé comme valeur de la propriété **Attenuation Settings**.

![Définir le paramètre d’atténuation](images/unreal-spatial-audio-img-08.png)

6. Définissez le **Sound Asset** que vous voulez attacher à l’acteur Ambient Sound :
    * Mettez à jour la propriété **Sound** de l’acteur Ambient Sound pour spécifier le fichier SoundAsset à utiliser.

![Définir l’actif sonore](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> Le fichier SoundAsset doit être mono pour être spatialisé avec le plug-in Microsoft Spatial Sound. Vous trouverez les propriétés du fichier son en pointant sur l’actif multimédia dans la fenêtre Content Browser, comme indiqué dans la capture d’écran ci-dessous.

![Nouvel actif multimédia d’atténuation du son](images/unreal-spatial-audio-img-10.png)

Quand la ressource audio est configurée, le son ambiant peut être spatialisé en utilisant la prise en charge du déchargement matériel dédié sur HoloLens 2.

## <a name="configuring-objects-for-spatialization"></a>Configuration des objets pour la spatialisation

L’utilisation de l’audio spatial signifie que vous responsable de la gestion du comportement sonore dans un environnement virtuel. Votre objectif principal est de créer des objets sonores qui semblent plus bruyants quand l’utilisateur est proche, et moins bruyants quand l’utilisateur est éloigné. C’est ce que l’on appelle l’atténuation sonore : faire en sorte que les sons semblent positionnés à un endroit fixe.

Tous les objets d’atténuation sont fournis avec des paramètres modifiables de :
* Distance
* Spatialisation
* Absorption de l’air
* Focus de l’auditeur
* Envoi de réverbération
* Occlusion

L’article [Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) fournit des détails et des informations sur l’implémentation de chacun de ces aspects.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous êtes en train d’explorer les modules de base du MRTK. À partir d’ici, vous pouvez passer au composant suivant :

> [!div class="nextstepaction"]
> [Entrée vocale](unreal-voice-input.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Caméra HoloLens](unreal-hololens-camera.md)

Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.


## <a name="see-also"></a>Voir aussi
* [Son spatial](/windows/mixed-reality/spatial-sound)
* [Conception du son spatial](/windows/mixed-reality/spatial-sound-design)
* [Réalité mixte - Fonctionnalités spatiales - Cours 220 : Son spatial](/windows/mixed-reality/holograms-220)