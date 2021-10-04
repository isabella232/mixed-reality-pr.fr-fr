---
title: Notes de publication-mai 2020
description: restez à jour dans les notes de publication de Windows Mixed Reality pour la mise à jour Windows 10 mai 2020.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Notes de publication, version, Windows 10, Build, 19h1, OS, mai 2020
ms.openlocfilehash: 462fcbfa10cfff8df23c970fd54ee0754a4d9472
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439164"
---
# <a name="windows-10-release-notes---may-2020"></a>notes de publication de Windows 10-mai 2020

la **Windows 10 mai 2020 Update (v2004)** comprend de nouvelles fonctionnalités pour les casques de Windows Mixed Reality (VR), telles que la possibilité de lancer des applications Win32 dans la réalité mixte. HoloLens (1re génération) est dans LTS (Long Term maintenance), avec les mises à jour de maintenance à publier chaque mois.

en procédant à une mise à niveau vers la dernière version de PC pour les casques Windows Mixed Reality immersifs, ouvrez **Paramètres > mettre à jour & sécurité** et sélectionnez **rechercher les mises à jour**. sur un PC Windows 10, vous pouvez également installer manuellement la **mise à jour Windows 10 2020** à l’aide de l' [outil de création de médias Windows](https://www.microsoft.com/software-download/windows10).

**dernière version de Desktop**: Windows 10 v2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>mises à jour pour Windows Mixed Reality les casques immersifs

### <a name="introducing-the-new-microsoft-edge"></a>Présentation du nouveau Microsoft Edge

comme [annoncé précédemment](/windows/mixed-reality/new-microsoft-edge), nous avons apporté des mises à jour pour une meilleure prise en charge de l’utilisation du nouveau navigateur Microsoft Edge dans Windows Mixed Reality. le nouveau Microsoft Edge adopte le Chromium projet open source pour créer une meilleure compatibilité web pour les clients et moins de fragmentation du web pour tous les développeurs web. Il prend également en charge WebXR, la nouvelle norme pour créer des expériences Web immersifs pour les casques VR, à la place de WebVR.

### <a name="improved-settings-for-wmr"></a>Paramètres amélioré pour WMR

Grâce à vos commentaires, nous avons ajouté et clarifié les paramètres sur la page d’affichage du casque :

* **Qualité visuelle de mon domicile** -la modification de ces paramètres affecte uniquement l’environnement d’hébergement de la réalité mixte (maison et Skyloft de la falaise) :

* **Ajuster le niveau de détail et la qualité des effets dans la vie de la réalité mixte** : cela modifie certains des effets de rendu que nous utilisons dans la page d’hébergement. En particulier, la qualité visuelle des différents matériaux (le bois, le béton, etc.) sera mise à l’échelle à mesure que vous modifiez ce paramètre de faible à élevé.

* **Modifier la résolution** de la fenêtre d’application : par défaut, la plupart des fenêtres 2D lancées à la page d’hébergement sont lancées avec une résolution de 720-p. Si vous pouvez les redimensionner manuellement horizontalement & verticalement, vous pouvez également choisir de les lancer tous sur 1080p à la place. Précédemment, cette option était disponible en tant qu’option très élevée (bêta) sous qualité visuelle. Nous l’avons correctement scindée en tant que paramètre distinct maintenant.

* **Options d’expérience** : ces options permettent d’ajuster l’expérience de la réalité mixte afin de réduire la charge sur les systèmes où le matériel peut éprouver des difficultés à respecter une 90 d’images à une fréquence illimitée. vous pouvez activer ou désactiver explicitement ces paramètres supplémentaires, ou choisir laisser Windows décider et laisser nos heuristiques décider quand les activer ou les désactiver.

* **Résolution** : Si vous avez un casque haute résolution tel que le réverbe HP, nous prenons en charge son exécution à sa résolution native ou à une résolution réduite pour des raisons de performances. Les casques antérieurs, tels que Samsung Odyssey et Odyssey +, ne prennent en charge qu’une seule résolution, vous ne pouvez donc pas modifier ce paramètre sur ces casques.

* **fréquence d’images** : vous pouvez maintenant définir manuellement la fréquence d’images de l’affichage du casque, ou continuer à laisser Windows utiliser ses heuristiques pour déterminer si 60 hz ou 90 hz est plus approprié.

* **Étalonnage** : comme précédemment, vous pouvez ajuster votre IPD (distance interpupillary) si elle est prise en charge par votre casque.

* **Basculement d’entrée** : basculez le comportement de basculement du focus d’entrée (Win + Y) pour qu’il soit automatique (en fonction des commentaires du capteur de présence) ou manuel.

### <a name="new-cortana-app"></a>nouvelle Cortana application

cette mise à jour de Windows comprend la version la plus récente de l’application Cortana, qui est actuellement en anglais uniquement et qui ne prend plus en charge certaines commandes spécifiques à la réalité mixte comme « prendre une photo » et « prendre une vidéo ». vous pouvez utiliser le nouveau Cortana pour lancer des applications, et il prend également en charge de nouvelles commandes axées sur la productivité comme « quand est-ce que j’ai ma prochaine réunion ? ». ou « envoyez un e-mail à \< name \> ce que je suis en retard ».
    
### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Mises à jour supplémentaires disponibles dans 19041,546 (publiée le 2020 octobre)

cette mise à jour mensuelle de maintenance des postes de travail comprend les modifications suivantes pour les appareils Windows Mixed Reality : 
* réduit les distorsions et les aberrations dans Windows Mixed Reality les affichages montés en tête (HMD). 
* ajoute la prise en charge des contrôleurs de mouvement HP Windows Mixed Reality à venir. 
* modifie le comportement du paramètre de fréquence d’actualisation de 90 hz dans Windows Mixed Reality de manière à ce qu’il ne repasse plus automatiquement à 60 hz dans certains cas quand 90 hz ne peut pas être atteint. 

### <a name="help-us-improve"></a>Aidez-nous à améliorer !

Nous cherchons continuellement à améliorer la compatibilité.  si vous trouvez que votre application Win32 classique favorite ne se comporte pas correctement dans Windows Mixed Reality, envoyez vos commentaires via notre [Hub de commentaires](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

## <a name="prior-release-notes"></a>Notes de publication antérieures

* [Notes de publication-mai 2019](release-notes-may-2019.md)
* [Notes de publication - Octobre 2018](release-notes-october-2018.md)
* [Notes de publication-2018 avril](release-notes-april-2018.md)
* [Notes de publication - Octobre 2017](release-notes-october-2017.md)
* [Notes de publication - Août 2016](release-notes-august-2016.md)
* [Notes de publication - Mai 2016](release-notes-may-2016.md)
* [Notes de publication - Mars 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Voir aussi
* [Prise en charge des casques immersifs (lien externe)](./troubleshooting-windows-mixed-reality.md)
* [prise en charge des HoloLens (lien externe)](https://support.microsoft.com/products/hololens)
* [Installer les outils](/windows/mixed-reality/develop/install-the-tools)
* [Envoyer vos commentaires](/windows/mixed-reality/give-us-feedback)