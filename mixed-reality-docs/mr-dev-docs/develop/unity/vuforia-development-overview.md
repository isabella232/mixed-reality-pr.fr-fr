---
title: Utilisation de Vuforia avec Unity
description: utilisez Vuforia pour générer des applications Windows Mixed Reality dans unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, marqueurs, coordonnées, cadre de référence, suivi, casque de réalité mixte, casque de réalité windows mixte, casque de réalité virtuelle, unity, HoloLens, suivi des appareils, mode de performances, portail des développeurs Vuforia
ms.openlocfilehash: dd5153b5e4986ebf1ecc2c133f3d431de08ce5b923cc7d2327d9cbda4f4df61c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216415"
---
# <a name="using-vuforia-engine-with-unity"></a>Utilisation du moteur Vuforia avec Unity

le moteur Vuforia offre une fonctionnalité importante pour HoloLens, la puissance permettant de connecter les expériences AR à des images et objets spécifiques dans l’environnement. Vous pouvez utiliser cette fonctionnalité pour superposer des instructions pas à pas guidées par-dessus des machines pour l’entreprise industrielle ou ajouter des fonctionnalités et expériences numériques à un produit ou un jeu physique.

Le moteur Vuforia offre un large éventail de fonctionnalités et de cibles pour améliorer la flexibilité de votre processus de développement. L’une de nos fonctionnalités les plus récentes, Vuforia Model targets, est une fonctionnalité clé pour les utilisations commerciales et industrielles. Les cibles de modèle permettent aux applications de reconnaître des objets physiques tels que des machines, des automobiles ou des jouets et de les suivre en fonction d’un modèle de CAO ou d’un modèle 3D numérique. Pour les utilisations industrielles, cette fonctionnalité permet aux travailleurs d’assemblage et aux techniciens de service d’utiliser des instructions de travail et des instructions de procédure dans la fabrique ou dans le champ.

Les applications de moteur Vuforia existantes qui ont été créées pour les téléphones et les tablettes peuvent facilement être configurées dans Unity pour s’exécuter sur HoloLens. vous pouvez même utiliser le moteur Vuforia pour mettre votre nouvelle application HoloLens sur des tablettes Windows 10 telles que le Surface Pro et le Surface Book.


## <a name="get-the-tools"></a>Obtenir les outils

[installez les versions recommandées](../install-the-tools.md) de Visual Studio et unity, puis configurez unity pour utiliser Visual Studio et l’IDE et le compilateur préférés. 

lors de l’installation d’unity, veillez à installer le « Backend de script IL2CPP de la banque de Windows ».

Ajoutez le package du moteur Vuforia comme décrit [ici.](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)

## <a name="getting-started-with-vuforia-engine"></a>Prise en main du moteur Vuforia

le meilleur point de départ pour en savoir plus sur le moteur Vuforia et HoloLens est l' [exemple de HoloLens de moteur Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponible dans le magasin d’actifs unity). l’exemple fournit un projet de HoloLens complet, y compris des scènes préconfigurées qui peuvent être déployées sur un HoloLens.

les scènes montrent comment utiliser des cibles d’image Vuforia pour reconnaître une image et l’enrichir avec du contenu numérique dans une expérience HoloLens. l’exemple de HoloLens du moteur Vuforia comprend également une scène qui montre l’utilisation des cibles du modèle et VuMarks sur HoloLens. vous pouvez facilement substituer votre propre contenu en coulisses pour expérimenter la création d’applications HoloLens qui utilisent le moteur Vuforia.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Configuration d’une application Vuforia pour HoloLens

le développement d’une application de moteur Vuforia pour HoloLens est fondamentalement identique au développement d’applications de moteur Vuforia pour d’autres appareils. Vous pouvez ensuite appliquer les paramètres de build et les configurations décrits dans la section ci-dessous. c’est tout ce qui est nécessaire pour permettre au moteur Vuforia de fonctionner avec les systèmes de mappage spatial et de suivi positionnel HoloLens.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Générer et exécuter l’exemple de moteur Vuforia pour HoloLens
1.  télécharger l' [exemple de moteur Vuforia pour HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) à partir du magasin d’actifs unity
2.  Appliquer les [options de moteur Unity recommandées pour l’alimentation et les performances](performance-recommendations-for-unity.md)
3.  Ajoutez les exemples de scènes aux **scènes** dans la **Build.**
4.  dans **Paramètres de build**, basculez la plateforme de génération vers **UWP** en cliquant sur le bouton **ajouter des scènes ouvertes** .
![image](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  sélectionnez le bouton **Paramètres du lecteur** .  
   * sélectionnez l’icône **UWP** et développez la section **XR Paramètres** .
   * Vérifiez que **la réalité virtuelle prise en charge** est activée.    
   * Sous les kits de développement logiciel ( **SDK) Virtual Reality** , vérifiez que :
     * La **réalité mixte** de la fenêtre est incluse dans la liste et l’activation du partage de **mémoire tampon de profondeur** est activée. 
     * Le **format de profondeur** est défini sur **profondeur 16 bits.** 
   * Assurez-vous que le **mode de rendu stéréo** est défini sur **une seule instance de passage.**
6.  développez la section **Paramètres de publication** .
   * Sous **fonctionnalités** , assurez-vous que **client Internet, webcam, microphone** et **SpatialPerception** sont sélectionnés.
   * **Remarque : SpatialPerception** doit être sélectionné uniquement si vous avez l’intention d’utiliser l’API observateur de surface.
   * Sous **familles d’appareils prises en charge**, assurez-vous qu' **holographique** est sélectionné. 
7.  Développez la section **résolution et présentation** .
   * Désactivez **exécuter en arrière-plan** afin que le moteur Vuforia s’interrompt lorsque l’application est placée en arrière-plan et peut accéder à nouveau à l’appareil photo lors de la reprise de l’application. 
   * Dans la liste déroulante **orientation par défaut** , assurez-vous que l’option **paysage gauche** est sélectionnée.
8.  revenez à la fenêtre de **Paramètres de build** et sélectionnez **générer** pour générer un projet de Visual Studio.
9.  générez le fichier exécutable à partir de Visual Studio et installez-le sur votre HoloLens.

## <a name="the-vuforia-developer-portal"></a>Portail des développeurs Vuforia

les développeurs qui cherchent à créer leurs propres expériences AR avec le moteur Vuforia et HoloLens doivent s’inscrire sur notre portail des développeurs Vuforia sur [developer.vuforia.com](https://developer.vuforia.com/). Dans le portail, les développeurs ont accès aux [forums du moteur Vuforia](https://developer.vuforia.com/forum) où ils peuvent rejoindre les discussions de la Communauté, une [bibliothèque](https://library.vuforia.com/) avec une documentation détaillée sur toutes les fonctionnalités du moteur Vuforia, et le [Gestionnaire cible Vuforia](https://developer.vuforia.com/target-manager) où les utilisateurs peuvent créer leurs propres cibles personnalisées. Les développeurs peuvent également s’inscrire pour obtenir une licence de développeur gratuite à l’aide du [Gestionnaire de licences Vuforia](https://developer.vuforia.com/license-manager).

## <a name="device-tracking-with-vuforia"></a>Suivi des appareils avec Vuforia

Le [suivi des appareils](https://library.vuforia.com/features/environments/device-tracker-overview.html) gère le suivi, même lorsqu’une cible n’est plus en vue. Elle est automatiquement activée pour toutes les cibles lorsque le dispositif de suivi de périphérique positionnel est activé. pour les applications HoloLens, le dispositif de suivi positionnel est démarré automatiquement dans unity.

le moteur Vuforia fusionne automatiquement les poses du suivi de l’appareil photo et le suivi spatial de HoloLens pour fournir des poses cibles stables, indépendamment du fait que la cible est ou non visible par l’appareil photo.

Étant donné que le processus est géré automatiquement, il ne nécessite aucune programmation par le développeur.


**Vous trouverez ci-dessous une description détaillée du processus :**
1. Le dispositif de suivi cible de Vuforia reconnaît la cible
2. Le suivi cible est ensuite initialisé
3. La position et la rotation de la cible sont analysées pour fournir une estimation de pose robuste pour le HoloLens
4. le moteur Vuforia transforme la pose de la cible dans le HoloLens espace de coordonnées de mappage spatial
5. HoloLens prend le suivi si la cible n’est plus dans la vue. À chaque fois que vous examinez à nouveau la cible, Vuforia continuera à suivre les images et les objets avec précision.

Les cibles qui sont détectées, mais qui ne sont plus en vue, sont signalées comme EXTENDED_TRACKED. Dans ce cas, le script DefaultTrackableEventHandler utilisé sur toutes les cibles continue d’afficher le contenu d’augmentation. Le développeur peut contrôler ce comportement en implémentant un script de gestionnaire d’événements suivi personnalisé.

## <a name="performance-mode-with-vuforia-engine"></a>Mode de performance avec moteur Vuforia 

il est possible d’utiliser le moteur Vuforia pour gérer les performances sur les HoloLens pour les expériences de gestion des ressources et réduire la charge de travail sur le processeur. Le moteur Vuforia offre trois modes qui peuvent être sélectionnés : par défaut, pour optimiser la vitesse et pour optimiser la qualité. 

*   MODE_OPTIMIZE_SPEED vous permet de réduire la charge de travail sur l’appareil HoloLens et est très utile pour l’extension des expériences AR. Nous vous recommandons de suivre les cas où l’application effectue le suivi des objets/cibles statiques.
*   MODE_DEFAULT est le mode normal, qui peut être utilisé dans la plupart des scénarios.
*   MODE_OPTIMIZE_QUALITY est mieux adapté au suivi des cibles mobiles ou des cibles de modèle que vous prévoyez de choisir.

**Définition du mode**

Pour modifier le mode de performance dans Unity, accédez à configuration de Vuforia (Ctrl + Maj + V/Cmd + Maj + V) qui se trouve en tant que composant dans le GameObject ARCamera. 
*   Sélectionnez le menu déroulant mode périphérique de l’appareil photo et sélectionnez l’une des trois options.


## <a name="see-also"></a>Voir aussi
* [Installer les outils](../install-the-tools.md)
* [Systèmes de coordonnées](../../design/coordinate-systems.md)
* [Mappage spatial](../../design/spatial-mapping.md)
* [Appareil photo dans Unity](camera-in-unity.md)
* [Exportation et création de solutions Unity Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [documentation Vuforia : Prise en main avec le moteur Vuforia pour le développement de Windows 10](https://library.vuforia.com/articles/Training/Getting-Started-with-Vuforia-for-Windows-10-Development.html)
* [Documentation Vuforia : Prise en main avec le moteur Vuforia dans Unity](https://library.vuforia.com/articles/Training/getting-started-with-vuforia-in-unity.html)
* [documentation Vuforia : utilisation de l’exemple HoloLens dans unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity.html)
* [Documentation Vuforia : suivi des appareils dans Vuforia](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Documentation Vuforia : fréquence d’images et optimisation des performances](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
