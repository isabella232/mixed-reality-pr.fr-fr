---
title: Holographic Remoting Player
description: découvrez le lecteur de communication à distance holographique et le contenu de diffusion en continu holographique depuis un PC vers votre HoloLens en temps réel via Wi-Fi.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 07/27/2021
ms.topic: article
keywords: HoloLens, communication à distance, accès distant holographique, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, diagnostics, performances
ms.openlocfilehash: f467b32ddab231286fc916916b0a40f210a66eb1
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757017"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting Player

[Découvrez les principes de base de la communication à distance holographique.](platform-capabilities-and-apis/holographic-remoting-overview.md)

>[!IMPORTANT]
>la communication à distance holographique pour HoloLens 2 est une modification majeure de la version. [les applications distantes pour **HoloLens (1re génération)**](add-holographic-remoting.md) doivent utiliser NuGet package version **1. x.** x et [les applications distantes pour **HoloLens 2**](holographic-remoting-create-remote-wmr.md) doivent utiliser **2. x**. x. cela implique que les applications distantes écrites pour HoloLens 2 ne sont pas compatibles avec HoloLens (1er génération) et vice versa.

Le [lecteur de communication à distance holographique](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) est une application auxiliaire qui se connecte aux applications de PC et aux jeux qui prennent en charge la communication à distance holographique. le lecteur est disponible pour les HoloLens (première génération) et HoloLens 2.  les applications PC qui prennent en charge la communication à distance holographique avec HoloLens doivent être mises à jour pour prendre en charge la communication à distance holographique avec HoloLens 2. Si vous avez des questions sur les versions prises en charge, contactez le fournisseur de votre application.

>[!TIP]
>à partir de la version [2.2.0](holographic-remoting-version-history.md#v2.2.0) , le lecteur de communication à distance holographique est également disponible pour les pc Windows exécutant [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md).

>[!TIP]
>À partir de la version [2.4.0](holographic-remoting-version-history.md#v2.4.0) , vous pouvez créer des applications distantes à l’aide de l' [API OpenXR](../native/openxr.md) . Pour commencer, consultez [écriture d’une application distante holographique à distance à l’aide des API OpenXR](holographic-remoting-create-remote-openxr.md).

## <a name="connecting-to-the-holographic-remoting-player"></a>Connexion au lecteur de communication à distance holographique

Suivez les instructions de votre application pour vous connecter au lecteur de communication à distance holographique. vous devez entrer l’adresse IP de votre appareil HoloLens, que vous pouvez voir sur l’écran principal du lecteur de communication à distance, comme suit :

![Holographic Remoting Player](images/holographicremotingplayer.png)

Chaque fois que vous voyez l’écran principal, vous savez que vous n’avez pas de connexion à une application.

La connexion de communication à distance holographique n’est **pas chiffrée**. Vous devez toujours utiliser la communication à distance holographique sur une connexion de Wi-Fi sécurisée à laquelle vous faites confiance.

## <a name="quality-and-performance"></a>Qualité et performances

La qualité et les performances de votre expérience varient en fonction de trois facteurs :
* **L’expérience holographique que vous exécutez-les** applications qui restituent du contenu haute résolution ou très détaillé peuvent nécessiter un PC plus rapide ou une connexion sans fil plus rapide.
* Le **matériel de votre PC** : votre ordinateur doit être en mesure d’exécuter et d’encoder votre expérience holographique à 60 images par seconde. Pour une carte graphique, nous recommandons généralement une solution GeForce GTX 970 ou AMD Radeon R9 290 ou plus. Une fois encore, votre expérience particulière peut nécessiter une carte de niveau supérieur ou inférieur.
* **Votre connexion Wi-Fi** : votre expérience holographique est diffusée via Wi-Fi. Utilisez un réseau rapide avec une faible congestion pour optimiser la qualité. L’utilisation d’un PC connecté via un câble Ethernet plutôt que le Wi-Fi peut également améliorer la qualité.

## <a name="diagnostics"></a>Diagnostics

Pour mesurer la qualité de votre connexion, dites **« activer les diagnostics »** dans l’écran principal du lecteur de communication à distance holographique. lorsque les diagnostics sont activés, sur **HoloLens (première génération)** , l’application vous indique :

* **Fps** : nombre moyen de trames rendues que le lecteur de communication à distance reçoit et restitue par seconde. L’idéal est de 60 FPS.
* **Latence** : durée moyenne nécessaire à la mise en place d’une image à partir de votre PC jusqu’au HoloLens. Plus la solution est performante. Cela dépend en grande partie de votre réseau Wi-Fi.

sur **HoloLens 2** l’application vous indique :

![Diagnostics de lecteur de communication à distance holographique](images/holographicremotingplayer-diag.png)

* **Render** : nombre d’images rendu par le joueur de communication à distance au cours de la dernière seconde. Notez que cette valeur est indépendante du nombre de frames, qui sont arrivés via le réseau (voir **images vidéo**). L’heure Delta de rendu moyenne/maximale en millisecondes au cours de la dernière seconde entre les images rendues est affichée.

* **Trames vidéo** : le premier nombre affiché est ignoré, le second est une trame vidéo réutilisée, et la troisième les images vidéo. Tous les nombres représentent le nombre au cours de la dernière seconde.
    * ```Received frames``` nombre de trames vidéo arrivant au cours de la dernière seconde. Dans des conditions normales, cette valeur doit être 60, mais si ce n’est pas le cas, l’un des cadres est abandonné en raison de problèmes réseau ou le côté distant/distant ne produit pas de trames avec la vitesse attendue.
    * ```Reused frames``` nombre de trames vidéo utilisées plusieurs fois au cours de la dernière seconde. Par exemple, si des images vidéo arrivent en retard, la boucle de rendu du lecteur affiche toujours un frame, mais doit *réutiliser* le frame vidéo qu’il a déjà utilisé pour le frame précédent.
    * ```Skipped frames``` nombre de trames vidéo qui n’ont pas été utilisées par la boucle de rendu du lecteur. Par exemple, l’instabilité du réseau peut avoir pour effet que les trames vidéo arrivant ne sont plus distribuées uniformément. Par exemple, si certains sont en retard et que d’autres arrivent dans le temps avec le résultat, ils n’ont plus de Delta de 16,66 millisecondes lorsqu’ils s’exécutent sur 60 Hz. Cela peut se produire si plusieurs frames arrivent entre deux graduations de la boucle de rendu du joueur. Dans ce cas, le lecteur *ignore* un ou plusieurs frames, car il est supposé afficher toujours la dernière image vidéo reçue.

    >[!NOTE]
    >En cas d’instabilité du réseau, les trames ignorées et réutilisées sont généralement à la même. En revanche, si vous voyez uniquement les frames ignorés, cela indique que le lecteur n’atteint pas sa fréquence d’images cible. Dans ce cas, vous devez garder un œil sur l’heure de Delta de rendu maximale lors du diagnostic des problèmes.

* **Images vidéo Delta** : Delta minimum/maximum entre les trames vidéo reçues au cours de la dernière seconde. Ce nombre est généralement mis en corrélation avec les frames ignorés/réutilisés en cas de problèmes dus à l’instabilité du réseau.
* **Latence** : fréquence moyenne en millisecondes au cours de la dernière seconde. dans ce contexte, le fait d’envoyer des données de pose/de capteur de l’HoloLens au côté distant/distant jusqu’à l’affichage de la trame vidéo pour ces données de pose/de télémétrie sur l’HoloLens affiche.
* **Images vidéo ignorées** -nombre de trames vidéo rejetées au cours de la dernière seconde et depuis qu’une connexion a été établie. La cause principale des trames vidéo ignorées est lorsqu’une image vidéo n’arrive pas dans l’ordre et, pour cette raison, doit être ignorée, car il existe déjà une version plus récente. Cela est similaire aux *Trames ignorées* , mais la cause se trouve à un niveau inférieur dans la pile de communication à distance. Les trames vidéo ignorées ne sont attendues que dans des conditions de réseau incorrectes.

Dans l’écran principal, vous pouvez indiquer **« Désactiver les diagnostics »** pour désactiver les Diagnostics.

## <a name="pc-system-requirements"></a>Configuration système requise pour PC
* votre ordinateur **doit** exécuter la Windows 10 mise à jour anniversaire ou une version plus récente.
* Nous vous recommandons d’utiliser une carte graphique GeForce GTX 970 ou AMD Radeon R9 290 ou supérieure.
* Nous vous recommandons de connecter votre ordinateur à votre réseau via Ethernet pour réduire le nombre de sauts sans fil.

## <a name="see-also"></a>Voir aussi
* [HoloLens (première génération) : ajouter la communication à distance holographique](add-holographic-remoting.md)
* [écriture d’une application distante de communication à distance holographique à l’aide d’api Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Écriture d’une application distante de communication à distance holographique à l’aide d’API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Termes du contrat de licence de la communication à distance holographique](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)