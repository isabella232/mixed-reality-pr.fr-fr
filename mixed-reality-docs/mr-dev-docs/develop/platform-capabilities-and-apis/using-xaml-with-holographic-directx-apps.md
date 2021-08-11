---
title: Utilisation de code XAML avec les applications DirectX holographiques
description: Explique l’impact du basculement entre les vues XAML 2D et les vues immersives dans votre application DirectX, et comment utiliser efficacement un mode XAML et un affichage immersif.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, UWP, gestion des affichages des applications, XAML, clavier, procédure pas à pas, DirectX
ms.openlocfilehash: 3c7edfdf4ff2ed629699dca0514efabc9ce7241cb1781e4b9c914ad4bff1f900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220945"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Utilisation de code XAML avec les applications DirectX holographiques

> [!NOTE]
> Cet article s’applique aux API natives WinRT héritées.  Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](../native/openxr-getting-started.md)**.

Cette rubrique explique l’impact du basculement entre les [vues XAML 2D et les vues immersives](../../design/app-views.md) dans votre application DirectX, et comment utiliser efficacement un affichage XAML et une vue immersive.

## <a name="xaml-view-switching-overview"></a>Vue d’ensemble du basculement de vue XAML

sur HoloLens, une application immersif qui peut afficher ultérieurement un affichage xaml 2d doit initialiser d’abord cette vue xaml et basculer immédiatement vers une vue immersive à partir de là. XAML se chargera avant que votre application puisse faire quoi que ce soit, ce qui ajoute une petite augmentation du temps de démarrage. XAML continuera à occuper de l’espace mémoire dans le processus de votre application pendant qu’il reste en arrière-plan. Le délai de démarrage et l’utilisation de la mémoire dépendent de ce que fait votre application avec XAML avant de basculer vers la vue native. Si vous ne faites rien dans votre code de démarrage XAML dans un premier temps, sauf démarrer votre vue immersif, l’impact doit être mineur. En outre, étant donné que votre rendu holographique est effectué directement vers la vue immersive, vous évitez toute restriction XAML sur ce rendu.

Le nombre d’utilisations de la mémoire pour le processeur et le GPU. Direct3D 11 peut échanger la mémoire graphique virtuelle, mais il peut ne pas être en mesure de permuter une partie ou la totalité des ressources du GPU XAML, et il peut y avoir un impact notable sur les performances. Dans les deux cas, ne pas charger les fonctionnalités XAML dont vous n’avez pas besoin offre davantage de place pour votre application et offre une meilleure expérience.

## <a name="xaml-view-switching-workflow"></a>Flux de travail de basculement de vue XAML

Le flux de travail d’une application qui va directement du XAML au mode immersif est le suivant :
* L’application démarre en mode XAML 2D.
* La séquence de démarrage XAML de l’application détecte si le système actuel prend en charge le rendu holographique :
* Si c’est le cas, l’application crée l’affichage immersif et le met immédiatement au premier plan. le chargement XAML est ignoré pour tout élément qui n’est pas nécessaire sur les appareils Windows Mixed Reality, y compris les classes de rendu et le chargement des ressources dans la vue XAML. Si l’application utilise du code XAML pour l’entrée au clavier, cette page d’entrée doit encore être créée.
* Si ce n’est pas le cas, la vue XAML peut continuer avec l’entreprise comme d’habitude.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Conseil pour le rendu des graphiques sur les deux vues

si votre application doit implémenter une certaine quantité de rendu dans DirectX pour la vue XAML dans Windows Mixed Reality, votre meilleur résultat est de créer un convertisseur qui peut fonctionner avec les deux vues. Le convertisseur doit être une instance qui est accessible à partir des deux vues, et il doit basculer entre le rendu 2D et le rendu holographique. Ainsi, les ressources GPU ne sont chargées qu’une seule fois, ce qui réduit le temps de chargement, l’impact sur la mémoire et la quantité de ressources échangées lors du basculement des vues.
