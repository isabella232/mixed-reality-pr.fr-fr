---
title: Boutons
description: Vue d’ensemble des boutons dans MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, MRTK, boutons
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003106"
---
# <a name="button"></a>Bouton

![Bouton principal](../images/button/MRTK_Button_Main.png)

Un bouton permet à l’utilisateur de déclencher une action immédiate. Il s’agit de l’un des composants les plus fondamentaux de la réalité mixte. MRTK fournit différents types de prefabs de bouton.

## <a name="button-prefabs-in-mrtk"></a>Bouton prefabs dans MRTK

Exemples du bouton prefabs sous le ``MRTK/SDK/Features/UX/Interactable/Prefabs`` dossier

### <a name="unity-ui-imagegraphic-based-buttons"></a>Image de l’interface utilisateur Unity/boutons basés sur un graphique

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>Boutons basés sur un conflit

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    Bouton de style Shell de HoloLens 2 avec une plaque arrière qui prend en charge différents commentaires visuels tels qu’une bordure claire, une lumière de proximité et une plaque avant compressée
    :::column-end:::
    :::column:::
    Bouton de style Shell de HoloLens 2 sans arrière-plaque
    :::column-end:::
    :::column:::
    Bouton de style Shell de HoloLens 2 avec forme circulaire
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    ![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    Bouton de style Shell de la largeur de l’interface HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    Barre de boutons HoloLens 2 horizontale avec arrière partagé
    :::column-end:::
    :::column:::
    Barre de boutons HoloLens 2 verticale avec arrière partagé
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    Case à cocher de type Shell de HoloLens 2 32x32mm
    :::column-end:::
    :::column:::
    Commutateur de style Shell de HoloLens 2 32x32mm 
    :::column-end:::
    :::column:::
    32x32mm radio de style Shell de HoloLens 2
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Case à cocher de type Shell de HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    Commutateur de style Shell de HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    32x96mm radio de style Shell de HoloLens 2
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![Radial ](../images/button/MRTK_Button_Radial.png)  radial
    :::column-end:::
    :::column:::
    ![Case à cocher](../images/button/MRTK_Button_Checkbox.png) **Case à cocher**
    :::column-end:::
    :::column:::
    ![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Bouton radial 
    :::column-end:::
    :::column:::
    Case à cocher 
    :::column-end:::
    :::column:::
    Commutateur bascule
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**
    :::column-end:::
    :::column:::
    ![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton** 
    :::column-end:::
    :::column:::
    ![](../images/button/MRTK_Button_Base.png)  Bouton de base du bouton
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Bouton de style d’interpréteur de commandes HoloLens 1re génération
    :::column-end:::
    :::column:::
    Bouton de commande de la forme ronde
    :::column-end:::
    :::column:::
    Bouton de base
    :::column-end:::
:::row-end:::

Le `Button` (ressources/MRTK/SDK/features/UX/interactive/Prefabs/Button. Prefab) est basé sur le [](interactable.md) concept interactif pour fournir des contrôles d’interface utilisateur faciles pour les boutons ou d’autres types de surfaces interactives. Le bouton de ligne de base prend en charge toutes les méthodes d’entrée disponibles, y compris l’entrée articulée pour les interactions proches et le point d’appui sur l’air pour les interactions lointaines. Vous pouvez également utiliser la commande vocale pour déclencher le bouton.

`PressableButtonHoloLens2` (Ressources/MRTK/Kit de développement logiciel/fonctionnalités/UX/accessible en interaction/Prefabs/PressableButtonHoloLens2. Prefab) est un bouton de style d’interpréteur de commandes HoloLens 2 qui prend en charge le déplacement précis du bouton pour l’entrée de suivi direct. Il combine un `Interactable` script avec un `PressableButton` script.

Pour HoloLens 2, il est recommandé d’utiliser des boutons avec une plaque arrière opaque. Les boutons transparents ne sont pas recommandés en raison de ces problèmes d’utilisation et de stabilité :

* L’icône et le texte sont difficiles à lire avec l’environnement physique
* Il est difficile de comprendre quand les déclencheurs d’événements
* Les hologrammes affichés via un plan transparent peuvent être instables avec la stabilisation LSR profondeur de HoloLens 2

![Bouton plaqué](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>Comment utiliser les boutons avec pression

### <a name="unity-ui-based-buttons"></a>Boutons basés sur l’interface utilisateur Unity

Créez un canevas dans votre scène (GameObject-> UI-> canevas). Dans le panneau de l’inspecteur de votre canevas :

* Cliquez sur « convertir en canevas MRTK »
* Cliquez sur « Ajouter NearInteractionTouchableUnityUI ».
* Définissez les échelles X, Y et Z du composant de transformation Rect sur 0,001

Ensuite, faites glisser `PressableButtonUnityUI` (ressources/MRTK/Kit de développement logiciel/fonctionnalités/UX/interactive/Prefabs/PressableButtonUnityUI. Prefab), `PressableButtonUnityUICircular` (ressources/MRTK/Kit de développement logiciel (SDK)/fonctionnalités/UX/exploitable/Prefabs/PressableButtonUnityUICircular. Prefab), ou `PressableButtonHoloLens2UnityUI` (ressources/MRTK/Kit de développement logiciel/SDK/featurables/Prefabs/PressableButtonHoloLens2UnityUI. Prefab) sur le canevas

### <a name="collider-based-buttons"></a>Boutons basés sur un conflit

Il vous suffit `PressableButtonHoloLens2` de faire un glisser (ressources/MRTK/SDK/features/UX/interactive/Prefabs/PressableButtonHoloLens2. Prefab) ou `PressableButtonHoloLens2Unplated` (ressources/MRTK/SDK/features/UX/interactive/Prefabs/PressableButtonHoloLens2Unplated. Prefab) dans la scène. Ces prefabs de bouton sont déjà configurés pour obtenir des commentaires visuels audio pour les différents types d’entrées, y compris l’entrée articulée et le point de regard.

Les événements exposés dans le Prefab lui-même, ainsi que [le composant pouvant](interactable.md) être utilisé, peuvent être utilisés pour déclencher des actions supplémentaires. Les boutons d’appui de la [scène HandInteractionExample](../example-scenes/hand-interaction-examples.md) utilisent l’événement *OnClick* de l’interagissant pour déclencher une modification de la couleur d’un cube. Cet événement est déclenché pour différents types de méthodes d’entrée, telles que le point de suspension, l’air-TAP, le rayon de la main, ainsi que l’appui sur le bouton physique via le script du bouton d’appui.

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

Vous pouvez configurer le moment où le bouton enfoncé déclenche l’événement *OnClick* via le `PhysicalPressEventRouter` sur le bouton. Par exemple, vous pouvez définir *OnClick* pour qu’il se déclenche quand le bouton est activé pour la première fois, par opposition à l’enfoncement et à la libération, en définissant l’option interactiver sur *événement* sur *clic* .

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

Pour tirer parti des informations d’état d’entrée articulées spécifiques, vous pouvez utiliser les boutons accessibles par événements- *Touch Begin*, *Touch end*, *bouton enfoncé*, *bouton relâché*. Toutefois, ces événements ne sont pas déclenchés en réponse à des entrées d’entrée aérienne, de rayon de main ou d’oeil. **Pour prendre en charge à la fois les interactions proches et Far, il est recommandé d’utiliser l’événement *OnClick* d’Interactive.**

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>États d’interaction

Dans l’état inactif, la plaque avant du bouton n’est pas visible. Comme une approche par doigt ou un curseur de l’entrée de regard cible la surface, la bordure lumineuse de la plaque avant devient visible. La surface de la plaque avant présente une surbrillance supplémentaire. Quand vous appuyez sur un doigt, la plaque avant se déplace à la main. Lorsque le doigt touche la surface de la plaque avant, il affiche un effet d’impulsion subtil pour fournir un retour visuel du point tactile.

Dans le bouton de style Shell HoloLens 2, il existe de nombreux signaux visuels et intuitivité pour augmenter la confiance de l’utilisateur sur l’interaction.

|  ![Lumière de proximité](../images/button/ux_button_affordance_proximitylight.jpg) | ![Sélection du focus](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Compression du boîtier](../images/button/ux_button_affordance_compression.jpg) | ![Impulsion sur le déclencheur](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| Lumière de proximité | Sélection du focus | Compression du boîtier | Impulsion sur le déclencheur |

L’effet d’impulsion subtil est déclenché par le bouton enfoncé, qui recherche des *ProximityLight* qui vivent sur le pointeur actuellement en interaction. Si des lumières de proximité sont détectées, la `ProximityLight.Pulse` méthode est appelée, ce qui anime automatiquement les paramètres du nuanceur pour afficher une impulsion.

## <a name="inspector-properties"></a>Propriétés de l’inspecteur

![Structure de bouton](../images/button/MRTK_Button_Structure.png)

 
 Collision `Box Collider` de Box pour la plaque avant du bouton.

**Bouton enfoncé** Logique pour le mouvement du bouton avec l’interaction avec la main.

**Routeur d’événements de presse physique** Ce script envoie des événements à partir d’une interaction d’appui à la main pour [interagir](interactable.md).

**En interaction** 
 L' [interaction gère divers](interactable.md) types d’États et d’événements d’interaction. Les entrées du point de contrôle de l’entrée et du mouvement du regard HoloLens, ainsi que l’entrée du contrôleur de mouvement du casque immersif sont directement gérées par ce script.

**Source audio** Source audio Unity pour les séquences de commentaires audio.

*NearInteractionTouchable. cs* requis pour transformer tout objet touchable en entrée articulée.

## <a name="prefab-layout"></a>Disposition Prefab

L’objet *ButtonContent* contient une plaque avant, une étiquette de texte et une icône. Le *FrontPlate* répond à la proximité de l’index à l’aide du nuanceur de *Button_Box* . Il affiche les bordures lumineuses, la lumière de proximité et un effet d’impulsion sur Touch. L’étiquette de texte est créée avec TextMesh Pro. La visibilité de *SeeItSayItLabel* est contrôlée par le thème de l' [interaction](interactable.md).

![Disposition du bouton](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>Comment modifier l’icône et le texte

Les boutons MRTK utilisent un `ButtonConfigHelper` composant pour vous aider à modifier l’icône, le texte et l’étiquette du bouton. (Notez que certains champs peuvent être absents si les éléments ne sont pas présents sur le bouton sélectionné.)

![Helper de configuration de bouton](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>Création et modification de jeux d’icônes

Un **jeu d’icônes** est un ensemble partagé de ressources d’icône utilisées par le `ButtonConfigHelper` composant. Trois *styles* d’icône sont pris en charge.

* Les icônes **Quad** sont rendues sur un quadruple à l’aide d’un `MeshRenderer` . Il s’agit du style d’icône par défaut.
* Les icônes de **Sprite** sont rendues à l’aide d’un `SpriteRenderer` . Cela est utile si vous préférez importer vos icônes sous la forme d’une feuille de Sprite, ou si vous souhaitez que vos ressources d’icône soient partagées avec des composants de l’interface utilisateur Unity. Pour utiliser ce style, vous devez installer le package de l’éditeur Sprite **(Windows-> Package Manager-> 2D sprite)**
* Les icônes **char** sont rendues à l’aide d’un `TextMeshPro` composant. Cela est utile si vous préférez utiliser une police d’icône. Pour utiliser la police de l’icône HoloLens, vous devez créer une `TextMeshPro` ressource de police.

Pour modifier le style utilisé par votre bouton, développez la liste déroulante *icônes* dans le ButtonConfigHelper et sélectionnez un style dans la liste déroulante *style d’icône* .

Vous pouvez créer un jeu d’icônes de bouton à l’aide du menu Asset : **créer > ensemble d’icônes de réalité mixte > jeu d’icônes.** Pour ajouter des icônes Quad et Sprite, il suffit de les faire glisser dans leurs tableaux respectifs. Pour ajouter des icônes de type char, vous devez d’abord créer et assigner une ressource de police.

Dans MRTK 2,4 et au-delà, nous vous recommandons de déplacer les textures d’icône personnalisées vers un IconSet.
Pour mettre à niveau les ressources sur tous les boutons d’un projet au nouveau format recommandé, utilisez ButtonConfigHelperMigrationHandler.
(Kit d’outils de réalité mixte-utilitaires de >-fenêtre de migration de >-> sélection du gestionnaire de migration-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)

Importation du package Microsoft. MixedRealityToolkit. Unity. Tools requis pour mettre à niveau les boutons.

![Boîte de dialogue mettre à niveau la fenêtre](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Si aucune icône n’est trouvée dans le jeu d’icônes par défaut lors de la migration, un jeu d’icônes personnalisé est créé dans MixedRealityToolkit. generated/CustomIconSets. Une boîte de dialogue indiquera que cette opération a eu lieu.

![Notification d’icône personnalisée](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>Création d’une ressource de police d’icône HoloLens

Tout d’abord, importez la police d’icône dans Unity. Sur les ordinateurs Windows, vous pouvez trouver la police HoloLens par défaut dans *Windows/Fonts/holomdl2. ttf.* Copiez et collez ce fichier dans votre dossier de ressources.

Ensuite, ouvrez le créateur de la ressource de police TextMeshPro à l’aide de **windows > TextMeshPro > police Creator.** Voici les paramètres recommandés pour la génération d’un Atlas de polices HoloLens. Pour inclure toutes les icônes, collez la plage Unicode suivante dans le champ *séquence de caractères* :

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Création de bouton 1](../images/button/MRTK_Font_Asset_Creation_1.png)

Une fois la ressource de police générée, enregistrez-la dans votre projet et affectez-la au champ police de l' *icône de caractère* de votre jeu d’icônes. La liste déroulante *icônes disponibles* est maintenant remplie. Pour qu’une icône soit disponible en vue d’une utilisation par un bouton, cliquez dessus. Il sera ajouté à la liste déroulante des *icônes sélectionnées* et s’affichera dans le, `ButtonConfigHelper.` vous pouvez éventuellement lui attribuer une étiquette. Cela permet de définir l’icône au moment de l’exécution.

![Création de bouton 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Création de bouton 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

Pour utiliser le jeu d’icônes, sélectionnez un bouton, développez la liste déroulante des icônes dans le `ButtonConfigHelper` et affectez-le au champ *jeu d’icônes* .

![Icône de bouton définie](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>Comment modifier la taille d’un bouton

La taille du bouton de style Shell de HoloLens 2 est 32x32mm. Pour personnaliser la dimension, modifiez la taille de ces objets dans le bouton Prefab :

1. **FrontPlate**
2. **Quadruple** sous la plaque arrière
3. **Collision de Box** à la racine

Ensuite, cliquez sur le bouton **corriger les limites** dans le script NearInteractionTouchable qui se trouve à la racine du bouton.

Mettre à jour la taille de la personnalisation de la ![ taille du bouton FrontPlate 1](../images/button/MRTK_Button_SizeCustomization1.png)

Mettre à jour la taille de la personnalisation de la ![ taille du bouton quadruple 2](../images/button/MRTK_Button_SizeCustomization2.png)

Mettre à jour la taille du bouton de conflit de cases ![ personnalisation 3](../images/button/MRTK_Button_SizeCustomization3.png)

Cliquez sur la personnalisation de la taille du bouton « fixer les limites » ![ 4](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it"></a>Commande vocale ('See-It, disons-it')

**Gestionnaire d’entrée vocale** Le script d' [interaction](interactable.md) dans le bouton enfoncé implémente déjà `IMixedRealitySpeechHandler` . Un mot clé de commande vocale peut être défini ici.

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**Profil d’entrée vocal** En outre, vous devez inscrire le mot clé de commande vocale dans le *profil des commandes vocales* globales.

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**Voir-IT, étiquette** Le bouton Prefab a un espace réservé TextMesh Pro sous l’objet *SeeItSayItLabel* . Vous pouvez utiliser cette étiquette pour communiquer le mot clé de commande vocale du bouton à l’utilisateur.

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>Comment créer un bouton à partir de zéro

Vous trouverez les exemples de ces boutons dans la scène **PressableButtonExample** .

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. création d’un bouton enfoncé avec un cube (proche de l’interaction uniquement)

1. Créer un cube Unity (GameObject > 3D Object > cube)
2. Ajouter un `PressableButton.cs` script
3. Ajouter un `NearInteractionTouchable.cs` script

Dans le `PressableButton` panneau de l’inspecteur de, assignez l’objet de cube aux éléments **visuels du bouton mobile**.

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

Lorsque vous sélectionnez le cube, vous verrez plusieurs couches de couleur sur l’objet. Cela visualise les valeurs de distance sous les **paramètres de presse**. À l’aide des descripteurs, vous pouvez configurer à quel moment démarrer la pression (déplacer l’objet) et le déclenchement de l’événement.

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

Lorsque vous appuyez sur le bouton, il déplace et génère les événements appropriés exposés dans le `PressableButton.cs` script, tels que TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased ().

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>Dépannage

Si votre bouton exécute une double pression, assurez-vous que la propriété **appliquer le push frontal** est active et que le plan de la **distance de départ** est placé devant le plan **touchable near interaction** . Le plan **touchable near interaction** est indiqué par le plan bleu placé devant l’origine de la flèche blanche dans le GIF ci-dessous :

![Composant de script de bouton enfoncé avec la propriété appliquer un push frontal mis en surbrillance](../images/button/MRTK_Button_Enforce_Push.png)

![Exemple animé de déplacement de la distance de transmission de type push devant le plan touchable near interaction](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. Ajout d’un retour visuel au bouton cube de base

Le nuanceur standard MRTK fournit diverses fonctionnalités qui facilitent l’ajout de commentaires visuels. Créez un matériau et sélectionnez le nuanceur `Mixed Reality Toolkit/Standard` . Ou vous pouvez utiliser ou dupliquer l’un des matériaux existants sous `/SDK/StandardAssets/Materials/` qui utilise le nuanceur standard MRTK.

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

Activez la case à cocher `Hover Light` et `Proximity Light` sous **options Fluent**. Cela permet d’obtenir des commentaires visuels pour les interactions près de la main (lumière de proximité) et du pointeur Far (point d’éclairage).

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. Ajout de commentaires audio au bouton cube de base

Étant donné que le `PressableButton.cs` script expose des événements tels que TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased (), nous pouvons facilement assigner des commentaires audio. Ajoutez simplement Unity `Audio Source` à l’objet cube, puis affectez des clips audio en sélectionnant audiosource. PlayOneShot (). Vous pouvez utiliser MRTK_Select_Main et MRTK_Select_Secondary des clips audio dans le `/SDK/StandardAssets/Audio/` dossier.

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. Ajout d’États visuels et gestion des événements d’interaction Far

L’opération [interactive](interactable.md) est un script qui facilite la création d’un état visuel pour les différents types d’interactions d’entrée. Il gère également les événements d’interaction Far. Ajoutez `Interactable.cs` et glissez-déposez l’objet cube dans le champ **cible** sous **profils**. Créez ensuite un nouveau thème avec un type **ScaleOffsetColorTheme**. Sous ce thème, vous pouvez spécifier la couleur de l’objet pour les États d’interaction spécifiques, tels que **focus** et **enfoncé**. Vous pouvez également contrôler l’échelle et le décalage. Vérifiez l' **accélération** et définissez Duration pour lisser la transition visuelle.

![Sélectionner le thème du profil](../images/button/mrtk_button_profiles.gif)

Vous verrez que l’objet répond à la fois aux interactions Far (Ray ou point de regard) et près (main).

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>Exemples de boutons personnalisés

Dans la [scène HandInteractionExample](../example-scenes/hand-interaction-examples.md), consultez les exemples de bouton piano et rond qui utilisent tous les deux `PressableButton` .

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

Chaque clé piano est associée à un `PressableButton` et à un `NearInteractionTouchable` script. Il est important de vérifier que la direction de *transfert local* de `NearInteractionTouchable` est correcte. Elle est représentée par une flèche blanche dans l’éditeur. Assurez-vous que la flèche pointe sur la face avant du bouton :

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>Voir aussi

* [Avec interaction](interactable.md)
* [Thèmes visuels](visual-themes.md)
