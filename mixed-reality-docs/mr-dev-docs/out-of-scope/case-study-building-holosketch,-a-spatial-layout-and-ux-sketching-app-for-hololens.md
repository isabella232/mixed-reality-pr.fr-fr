---
title: 'Étude de cas : création de HoloSketch, mise en page spatiale et application d’esquisse de l’expérience utilisateur pour HoloLens'
description: HoloSketch est une disposition spatiale et un outil d’esquisse de l’expérience utilisateur sur un appareil pour HoloLens pour vous aider à créer des expériences holographiques.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, ébauche, application
ms.openlocfilehash: 24929d38f97a3c02946a28184d7702c151dc22b2
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757321"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Étude de cas : création de HoloSketch, mise en page spatiale et application d’esquisse de l’expérience utilisateur pour HoloLens

HoloSketch est une disposition spatiale et un outil d’esquisse de l’expérience utilisateur sur un appareil pour HoloLens pour vous aider à créer des expériences holographiques. HoloSketch fonctionne avec un clavier et une souris Bluetooth associés, ainsi que des commandes de mouvement et de voix. L’objectif de HoloSketch est de fournir un outil de disposition d’expérience utilisateur simple pour une visualisation et une itération rapides.

![HoloSketch : une présentation spatiale et une application d’esquisse de l’expérience utilisateur pour HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch : présentation spatiale et application d’esquisse de l’expérience utilisateur pour HoloLens*

![Outil de disposition d’expérience utilisateur simple pour une visualisation et une itération rapides.](images/holosketch-image-02.png)<br>
*Outil de disposition d’expérience utilisateur simple pour une visualisation et une itération rapides*

## <a name="features"></a>Fonctionnalités

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitives pour les études rapides et le prototypage à l’échelle

![Utilisation de formes primitives](images/holosketch-primitives-giphy.gif)

Utilisez des formes primitives pour les études de masse rapide et le prototypage à l’échelle.

### <a name="import-objects-through-onedrive"></a>Importer des objets par le biais de OneDrive

![importation d’objets](images/holosketch-importobjects-giphy.gif)

Importez des images PNG/JPG ou des objets 3D FBX (nécessite un Packaging dans Unity) dans l’espace de la réalité mixte via OneDrive.

### <a name="manipulate-objects"></a>Manipuler des objets

![manipulation d’objets](images/manipulate-objects-640px.jpg)

Manipuler des objets (déplacer/faire pivoter/mettre à l’échelle) avec une interface d’objet 3D familière.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, souris/clavier, mouvements et commandes vocales

![prend en charge Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch prend en charge Bluetooth souris, le clavier, les gestes et les commandes vocales.

## <a name="background"></a>Contexte

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importance de la conception de l’appareil

lorsque vous concevez un élément pour HoloLens, il est important d’expérimenter votre conception dans l’appareil. L’un des plus grands défis de la conception d’applications de réalité mixte est qu’il est difficile d’avoir une idée de la mise à l’échelle, de la position et de la profondeur, en particulier par le biais des croquis 2D traditionnels.

### <a name="cost-of-2d-based-communication"></a>Coût de la communication en 2D

Pour communiquer efficacement des flux et des scénarios d’expérience utilisateur à d’autres utilisateurs, un concepteur peut finir par consacrer beaucoup de temps à la création de ressources à l’aide d’outils 2D traditionnels comme Illustrator, Photoshop et PowerPoint. Ces conceptions 2D nécessitent souvent des efforts supplémentaires pour les convertir en 3D. Certaines idées sont perdues dans cette traduction de 2D en 3D.

### <a name="complex-deployment-process"></a>Processus de déploiement complexe

Étant donné que la réalité mixte est un nouveau canevas pour nous, elle implique un grand nombre d’itérations de conception et d’essais et d’erreurs par nature. pour les concepteurs qui ne sont pas familiarisés avec les outils tels que unity et Visual Studio, il n’est pas facile de rassembler des éléments dans HoloLens. En général, vous devez suivre le processus ci-dessous pour voir votre illustration 2D/3D dans l’appareil. C’était un grand obstacle pour les concepteurs qui itèrent rapidement sur les idées et les scénarios.

![Processus de déploiement complexe](images/holosketch-image-03-1000px.png)<br>
*Processus de déploiement*

### <a name="simplified-process-with-holosketch"></a>Processus simplifié avec HoloSketch

Avec HoloSketch, nous souhaitons simplifier ce processus sans impliquer les outils de développement et le jumelage des portails de périphériques. à l’aide de OneDrive, les utilisateurs peuvent facilement placer des éléments 2d/3d dans des HoloLens.

![Processus simplifié avec HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Processus simplifié avec HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Encourager la pensée et les solutions de conception à trois dimensions

Nous avons pensé que cet outil donne aux concepteurs la possibilité d’explorer les solutions dans un espace véritablement tridimensionnel et de ne pas être coincé en 2D. Ils n’ont pas à se soucier de la création d’un arrière-plan 3D pour leur interface utilisateur, car l’arrière-plan est le monde réel dans le cas de HoloLens. HoloSketch permet aux concepteurs d’explorer facilement la conception 3D sur HoloLens.

## <a name="get-started"></a>Bien démarrer

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Comment importer des images 2D (JPG/PNG) dans HoloSketch

* Télécharger images JPG/PNG dans votre dossier OneDrive’Documents/HoloSketch'.
* à partir du menu OneDrive dans HoloSketch, vous pourrez sélectionner et placer l’image dans l’environnement.

![Importation d’images 2D](images/import-2d-images-1000px.jpg)<br>
*Importation d’images et d’objets 3D via OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Comment importer des objets 3D dans HoloSketch

avant de charger votre dossier OneDrive, suivez les étapes ci-dessous pour empaqueter vos objets 3d dans un bundle d’actifs unity. À l’aide de ce processus, vous pouvez importer vos fichiers FBX/OBJ à partir de logiciels 3D tels que Maya, Cinema 4D et Microsoft Paint 3D.

>[!IMPORTANT]
>Actuellement, la création d’un groupe de ressources est prise en charge avec Unity version 5.4.5 F1.

1. Téléchargez et ouvrez le projet Unity ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Ce projet Unity comprend le script pour la génération de la ressource bundle.
2. Créez un nouveau GameObject.
3. Nommez le GameObject en fonction du contenu.
4. Dans le panneau de l’inspecteur, cliquez sur « Ajouter un composant » et ajoutez « conflit de boîte ». 

   ![Dans le panneau de l’inspecteur, cliquez sur « Ajouter un composant » et ajoutez « conflit de boîte »](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Dans le panneau de l’inspecteur, cliquez sur « Ajouter un composant » et ajoutez le #2 « Box de collision »](images/holosketch-10b-assetbundles-1000px.png)

5. Importez le fichier 3D FBX en le faisant glisser dans le panneau projet.
6. Faites glisser l’objet dans le volet de la hiérarchie **sous votre nouvelle gameobject**.

   ![Faites glisser l’objet dans le volet de la hiérarchie sous votre nouvelle GameObject](images/holosketch-12-assetbundles-1000px.png)

7. Ajustez la dimension de conflit si elle ne correspond pas à l’objet. Faites pivoter l’objet en face **Z-AXIS**.

   ![Ajustez la dimension de conflit si elle ne correspond pas à l’objet.](images/holosketch-13-assetbundles-1000px.png)

8. faites glisser l’objet du panneau de la hiérarchie vers le panneau Project pour le **rendre prefab**.
9. En bas du panneau de l’inspecteur, cliquez sur la liste déroulante, créez et attribuez un nouveau nom unique. L’exemple ci-dessous montre comment ajouter et assigner « brownchair » pour le nom de AssetBundle. 

   ![En bas du panneau de l’inspecteur, cliquez sur la liste déroulante et attribuez un nouveau nom unique.](images/holosketch-14-assetbundles-1000px.png)

10. Préparez une image miniature pour l’objet de modèle. 
   ![Faites glisser une image dans le panneau projet et attribuez le nom utilisé pour l’objet.](images/holosketch-15-assetbundles-1000px.png)

11. Créez un dossier nommé « Assetbundles » sous le dossier « Asset » du projet Unity.

12. Dans le menu ressources, sélectionnez « Générer AssetBundles » pour générer le fichier. 
   ![Dans le menu ressources, sélectionnez « Générer AssetBundles » pour générer le fichier.](images/holosketch-15a-assetbundles.png)


13. **Télécharger le fichier généré dans le dossier/Files/Documents/HoloSketch sur OneDrive.** Télécharger le fichier de asset_unique_name uniquement. Vous n’avez pas besoin de charger des fichiers manifeste ou un fichier AssetBundles. <br>
![ajouter des fichiers à des fichiers/Documents/HoloSketch/dossier ](images/holosketch-onedriveupload-1000px.png)
 ![ vous verrez un objet 3d ajouté dans le menu OneDrive de HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Comment manipuler les objets

HoloSketch prend en charge l’interface traditionnelle couramment utilisée dans les logiciels 3D. Vous pouvez utiliser déplacer, faire pivoter, mettre à l’échelle les objets avec des gestes et une souris. Vous pouvez rapidement basculer entre les différents modes avec la voix ou le clavier.

### <a name="object-manipulation-modes"></a>Modes de manipulation d’objets

![Comment manipuler les objets](images/holosketch-image-06-1000px.png)<br>
*Comment manipuler les objets*

### <a name="contextual-and-tool-belt-menus"></a>Menus contextuels et de la ceinture d’outils

**Utilisation du menu contextuel**

Appuyez deux fois sur air pour ouvrir le menu contextuel. 

Éléments de menu :
* **Surface de disposition :** Il s’agit d’un système de grille 3D dans lequel vous pouvez mettre en page plusieurs objets et les gérer en tant que groupe. Appuyez deux fois sur l’aire de disposition pour y ajouter des objets.
* **Primitives :** Utilisez des cubes, des sphères, des cylindres et des cônes pour les études de masse.
* **OneDrive :** ouvrez le menu OneDrive pour importer des objets.
* **Aide :** Affiche l’écran d’aide.

![Menu contextuel](images/holosketch-image-07.png)<br>
*Menu contextuel*

**Utilisation du menu de la ceinture d’outils**

Déplacer, faire pivoter, mettre à l’échelle, enregistrer et charger la scène sont disponibles dans le menu de la ceinture d’outils. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Utilisation du clavier, des mouvements et des commandes vocales

![Clavier, mouvements et commandes vocales](images/holosketch-image-08-1000px.png)<br>
*Clavier, mouvements et commandes vocales*

## <a name="download-the-app"></a>Télécharger l’application

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Téléchargez et installez l’application HoloSketch gratuitement à partir du Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problèmes connus
* La création du groupement d’actifs est prise en charge avec **Unity version 5.4.5 F1.**
* selon la quantité de données de votre OneDrive, l’application peut apparaître comme si elle s’est arrêtée lors du chargement de OneDrive contenu
* Actuellement, la fonctionnalité d’enregistrement et de chargement ne prend en charge que les objets primitifs
* Les menus texte, audio, vidéo et photo sont désactivés dans le menu contextuel
* Le bouton de lecture du menu de la ceinture d’outils efface le gizmos de manipulation.

## <a name="sharing-your-sketches"></a>Partage de vos croquis

vous pouvez utiliser la fonctionnalité d’enregistrement vidéo de HoloLens en disant « bonjour Cortana, démarrer/arrêter l’enregistrement ». Appuyez sur la touche haut/flèche du volume pour prendre une photo de votre croquis.

## <a name="about-the-authors"></a>À propos des auteurs

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Parc Yoon</b></a><br>Concepteur d’expérience utilisateur @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick</b><br>Revel @Microsoft</td>
</tr>
</table> 