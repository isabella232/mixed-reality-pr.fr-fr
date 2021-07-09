---
title: 6. Empaquetage et déploiement sur un appareil ou un émulateur
description: Partie 6 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 7dbf72a477f376e338d346965b5276eba00ab543
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110711558"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Empaquetage et déploiement sur un appareil ou un émulateur

Dans le tutoriel précédent, vous avez ajouté un bouton simple qui rétablit la pièce de jeu d’échecs à sa position d’origine. Dans cette section finale, vous allez préparer l’application à être exécutée sur un appareil ou un émulateur HoloLens 2. Si vous disposez d’un appareil HoloLens 2, vous pouvez effectuer un streaming depuis votre ordinateur ou empaqueter l’application pour qu’elle s’exécute directement sur l’appareil. Si vous n’avez pas d’appareil, vous allez empaqueter l’application pour qu’elle s’exécute sur l’émulateur. À la fin de cette section, vous aurez une application de réalité mixte déployée que vous pourrez lire, complète avec des interactions et une interface utilisateur.

## <a name="objectives"></a>Objectifs

* [Appareil uniquement] Streaming sur HoloLens 2 avec communication à distance de l’application holographique
* Empaquetage et déploiement de l’application sur un appareil ou émulateur HoloLens 2

## <a name="device-only-streaming"></a>[Appareil uniquement] Streaming

La [communication à distance holographique](/windows/mixed-reality/add-holographic-remoting) signifie le streaming de données à partir d’un PC ou d’un appareil UWP autonome vers HoloLens 2, sans changer de canal. Une application hôte de communication à distance reçoit un flux de données d’entrée d’un appareil HoloLens, rend le contenu dans une vue immersive virtuelle et rediffuse en streaming les images de contenu à HoloLens via Wi-Fi. Le streaming vous permet d’ajouter des vues immersives distantes dans des logiciels de PC de bureau existants et d’accéder à plus de ressources système.

Si vous suivez ce chemin avec l’application de jeu d’échecs, vous aurez besoin de quelques éléments :

1.  Installez **Holographic Remoting Player** à partir du Microsoft Store sur votre HoloLens 2 et exécutez l’application. Notez votre adresse IP affichée dans l’application.
    * Accédez à **Modifier > Paramètres du projet** et vérifiez que la **valeur de RHI par défaut** Windows est définie sur **Valeur par défaut** ou sur **D3D11** :

![RHI par défaut](../images/unreal/performance-recommendations-img-09.png)

2.  De retour dans l’éditeur Unreal, accédez à **Modifier > Paramètres du projet** et cochez la case **Activer la communication à distance** dans la section **Communication à distance holographique Open XR**.

3.  Redémarrez l’éditeur, entrez l’adresse IP de votre appareil (qui figure dans l’application Holographic Remoting Player), puis cliquez sur **Connect**.

Une fois que vous êtes connecté, cliquez sur la flèche déroulante à droite du bouton **Play** et sélectionnez **VR Preview**. L’application est exécutée dans la fenêtre VR Preview, qui est diffusée en streaming sur le casque HoloLens.

## <a name="packaging-and-deploying-the-app-via-device-portal"></a>Empaquetage et déploiement de l’application par le biais du portail de l’appareil

>[!NOTE]
>S’il s’agit de la première fois que vous empaquetez une application Unreal pour HoloLens, vous devrez télécharger les fichiers de prise en charge à partir de l’Epic Launcher.
>- Accédez à **Préférences de l’éditeur > Général > Code source > Éditeur de code source** et vérifiez que Visual Studio 2019 est sélectionné.
>- Accédez à l’onglet **Library** dans Epic Games Launcher, sélectionnez la flèche déroulante à côté de **Launch**, puis cliquez sur **Options**.
>- Sous **Target Platforms**, sélectionnez **HoloLens 2** et cliquez sur **Apply**.
>![Changer de plateforme cible dans les paramètres du projet](images/unreal-uxt/6-installationoptions.PNG)

1.  Accédez à **Edit > Project Settings**.
    * Ajoutez un nom de projet sous **Project > Description > About > Project Name**.
    * Ajoutez **CN=NomVotreSociété** sous **Project > Description > Publisher > Company Distinguished Name**.
    * Sélectionnez **Start in VR** sous **Project > Description > Settings**.

> [!IMPORTANT]
> Si vous laissez l’un de ces champs vide, une erreur se produit quand vous tentez de générer un nouveau certificat à l’étape 3.

> [!IMPORTANT]
> Le nom de l’éditeur doit être au [format de nom unique LADPv3](https://www.ietf.org/rfc/rfc2253.txt). Un nom d’éditeur incorrect provoque l’affichage du message d’erreur « Clé de signature introuvable. L’application n’a pas pu être signée numériquement. » lors de l’empaquetage.

> [!IMPORTANT]
> Si vous ne sélectionnez pas « Start in VR », votre application essaie de démarrer dans une ardoise

![Paramètres du projet - Description](images/unreal-uxt/6-cn-new.PNG)

2.  Cochez les cases **Build for HoloLens Emulation** et/ou **Build for HoloLens Device** sous **Platforms > HoloLens**.

3.  Cliquez sur **Generate new** dans la section **Packaging** (en regard de **Signing Certificate**).

> [!IMPORTANT]
> Si vous utilisez un certificat déjà généré, le nom de l’éditeur du certificat doit être identique au nom de l’éditeur de l’application. Sinon, le message d’erreur « Clé de signature introuvable. L’application n’a pas pu être signée numériquement. » erreur.

![Paramètres du projet - Plateformes - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. Cliquez sur **None** à des fins de test quand vous êtes invité à créer un mot de passe de clé privée.

![Génération du nouveau certificat](images/unreal-uxt/6-private-key-testing.png)

5. Accédez à **File > Package Project** et sélectionnez **HoloLens**.
    * Créez un dossier où enregistrer votre package, puis cliquez sur **Select Folder**.

6.  Ouvrez le [Portail d’appareil Windows](/windows/mixed-reality/using-the-windows-device-portal) une fois l’application empaquetée, accédez à **Views > Apps** et recherchez la section **Deploy apps**.

7.  Cliquez sur **Browse...** , accédez à votre fichier **ChessApp.appxbundle**, puis cliquez sur **Open**.

    * Cochez la case en regard de **Allow me to select framework packages** si vous installez l’application sur votre appareil pour la première fois.
    * Dans la boîte de dialogue suivante, incluez les fichiers **VCLibs** et **appx** appropriés, **arm64** pour l’appareil et **x64** pour l’émulateur. Vous trouverez les fichiers sous **HoloLens** dans le dossier où vous avez enregistré votre package.

8.  Cliquez sur **Install**.
    * Vous pouvez maintenant accéder à **All Apps** et appuyer sur l’application que vous venez d’installer pour l’exécuter, ou démarrer l’application directement à partir du **Portail d’appareil Windows**. 

Félicitations ! Votre application de réalité mixte HoloLens est terminée et prête à l’emploi. Vous n’en avez cependant pas terminé. MRTK comporte un grand nombre de fonctionnalités autonomes que vous pouvez ajouter à vos projets, notamment le mappage spatial, le pointage du regard et l’entrée vocale, voire même les codes QR. Pour plus d’informations sur ces fonctionnalités, consultez la [vue d’ensemble du développement Unreal](/windows/mixed-reality/unreal-development-overview).

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous êtes en train d’explorer les modules de base du MRTK. À partir d’ici, vous pouvez passer au composant suivant :

> [!div class="nextstepaction"]
> [Entrée avec le pointage du regard](../unreal-gaze-input.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Caméra HoloLens](../unreal-hololens-camera.md)

Vous pouvez revenir aux [points de contrôle de développement Unreal](../unreal-development-overview.md#2-core-building-blocks) à tout moment.