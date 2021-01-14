---
title: Mise à jour des applications SteamVR pour Windows Mixed Reality
description: Bonnes pratiques pour la mise à jour de votre application SteamVR afin d’optimiser la compatibilité avec les casques de Windows Mixed Reality.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, compatibilité, Portage, HoloLens 1ère génération, casque de réalité mixte, casque Windows Mixed realisation, migration, Windows 10, vapeur, contrôleurs de mouvement, haptique
ms.openlocfilehash: c67eed489f626c804583592e496fcfaff5d8c291
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192627"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>Mise à jour des applications SteamVR pour Windows Mixed Reality

Nous encourageons les développeurs à tester et à optimiser leurs expériences SteamVR pour qu’elles s’exécutent sur des casques Windows de réalité mixte. Cette documentation couvre les améliorations courantes que vous pouvez apporter pour faire fonctionner vos expériences sur Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Instructions d’installation initiales

Pour commencer à tester votre jeu ou votre application sur Windows Mixed Reality, veillez à suivre tout d’abord notre [Guide de prise](https://aka.ms/WindowsMixedRealitySteamVR) en main.

## <a name="controller-models"></a>Modèles de contrôleur

1. Si votre application restitue des modèles de contrôleur :
    * Utiliser les [modèles de contrôleur de mouvement Windows Mixed Reality](../../design/motion-controllers.md#rendering-the-motion-controller-model)
    * Utilisez IVRRenderModel :: GetComponentState pour obtenir des transformations locales en parties de composant (par exemple, une pose de pointeur)
2. Les expériences qui ont une notion de droitier doivent obtenir des indications des API d’entrée aux contrôleurs de différenciation [(exemple Unity)](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Contrôles

Lors de la conception ou de l’ajustement de la disposition des contrôles, gardez à l’esprit l’ensemble suivant de commandes réservées :
1. Cliquer sur le **bouton gauche et le stick analogique droit** est réservé au **tableau de bord** de la vapeur.

> [!NOTE]
> Si vous utilisez un contrôleur de réverbes HP G2, le fait de cliquer sur le bouton de menu droit est réservé au **tableau de bord** de la vapeur.

2. Le **bouton Windows** renvoie toujours les utilisateurs vers la page d’hébergement Windows Mixed Reality.

Dans la mesure du possible, par défaut, les téléportions basées sur le stick analogique correspondent au comportement de téléportage de la [page d’hébergement Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home)

## <a name="tooltips-and-ui"></a>Info-bulles et interface utilisateur

De nombreux jeux VR tirent parti des info-bulles et des superpositions des contrôleurs motion pour enseigner aux utilisateurs leurs commandes d’application ou de jeux les plus importantes. Lorsque vous paramétrez votre application pour Windows Mixed Reality, nous vous recommandons de consulter cette partie de votre expérience pour vous assurer que les info-bulles sont mappées aux modèles de contrôleur Windows.

En outre, si vous avez des points dans votre expérience où vous affichez des images des contrôleurs, veillez à fournir des images mises à jour à l’aide des contrôleurs de mouvement Windows Mixed Reality.

## <a name="haptics"></a>Haptique

À compter de la [mise à jour 2018 de Windows 10 avril](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), les interfaces tactiles sont désormais prises en charge pour les expériences SteamVR sur Windows Mixed Reality. Si votre application ou jeu SteamVR prend déjà en charge les haptique, elle doit maintenant fonctionner (sans travail supplémentaire) avec les [contrôleurs de mouvement Windows Mixed Reality](../../design/motion-controllers.md).

Les contrôleurs de mouvement Windows Mixed Reality utilisent un moteur haptique standard, par opposition aux actionneurs linéaires présents dans d’autres contrôleurs de mouvement SteamVR. Cela peut aboutir à une expérience utilisateur légèrement différente de celle attendue. Nous vous recommandons donc de tester et de paramétrer votre conception haptique avec les contrôleurs de mouvement Windows Mixed Reality. Par exemple, parfois des impulsions tactiles courtes (5-10 ms) sont moins perceptibles sur les contrôleurs de mouvement Windows Mixed Reality. Pour produire une impulsion plus notable, expérimentez l’envoi d’un « clic » plus long (40-70 ms) pour donner au moteur plus de temps pour s’arrêter avant d’être informé de nouveau.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Lancement des applications SteamVR à partir du menu Démarrer de Windows Mixed Reality

Pour les expériences VR distribuées par vapeur, nous avons [mis à jour Windows Mixed Reality for SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) avec les dernières [versions de Windows](https://insider.windows.com). Les titres SteamVR s’affichent désormais dans le menu Démarrer de la réalité mixte Windows dans la liste « toutes les applications ».

## <a name="windows-mixed-reality-logo"></a>Logo Windows Mixed Reality

Pour afficher la prise en charge de Windows Mixed Reality pour votre titre, accédez au lien « modifier la page du magasin » sur la page d’accueil de votre application, sélectionnez l’onglet « informations de base », puis faites défiler jusqu’à « réalité virtuelle ». Décochez la case « masquer la réalité mixte Windows », puis publiez-la dans le Windows Store.

## <a name="bugs-and-feedback"></a>Bogues et commentaires

Vos commentaires sont précieux lorsqu’il s’agit d’améliorer l’expérience SteamVR Windows Mixed Reality. Envoyez tous les commentaires et bogues via le [Hub de commentaires Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Voici quelques [conseils sur la façon de rendre vos commentaires SteamVR aussi utiles que possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Si vous avez des questions ou des commentaires à partager, vous pouvez également nous contacter sur notre [Forum de vapeur](https://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>FAQ et résolution des problèmes

Si vous rencontrez des problèmes généraux lors de la configuration ou de la diffusion de votre expérience, [consultez les dernières étapes de dépannage](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>Voir aussi

* [Installer les outils](../install-the-tools.md)
* [Historique du pilote du contrôleur de mouvement et du casque](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Instructions de compatibilité matérielle PC minimale pour Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
