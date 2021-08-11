---
title: Création d’interfaces utilisateur
description: Ce cours vous montre comment utiliser Mixed Reality Toolkit (MRTK) pour créer des interfaces utilisateur statiques et dynamiques.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, préfabriqués, hologrammes, info-bulles
ms.localizationpriority: high
ms.openlocfilehash: 605379be0e2f3238ddb5de5c47b6df005c4bf2eb82a2e04156f1317e0e7659fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227772"
---
# <a name="6-creating-user-interfaces"></a>6. Création d’interfaces utilisateur

Dans ce tutoriel, vous allez voir comment créer une interface utilisateur simple avec les préfabriqués de boutons et de menus MRTK, ainsi qu’avec le composant TextMeshPro d’Unity. Vous allez également voir comment configurer les boutons pour déclencher des événements, et comment ajouter des éléments d’interface utilisateur d’info-bulle dynamiques pour fournir des informations supplémentaires à l’utilisateur.

## <a name="objectives"></a>Objectifs

* Apprendre à organiser les boutons dans une collection
* Apprendre à utiliser les préfabriqués de menu de MRTK
* Apprendre à interagir avec des hologrammes en utilisant des menus et des boutons
* Apprendre à ajouter des éléments de texte
* Apprendre à générer dynamiquement des info-bulles pour des objets

## <a name="creating-a-static-panel-of-buttons"></a>Création d’un panneau de boutons statique

Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **RoverExplorer**, puis sélectionnez **Create Empty** (Créer un élément vide) pour ajouter un objet vide en tant qu’enfant de RoverExplorer. Ensuite, nommez l’objet **Buttons**, puis configurez le composant **Transform** de la façon suivante :

* **Position** : X = -0.6, Y = 0.036, Z = -0.5
* **Rotation** : X = 90, Y = 0, Z = 0
* **Scale** (Échelle) : X = 1, Y = 1, Z = 1

![Unity avec l’objet Boutons nouvellement créé, sélectionné et positionné](images/mr-learning-base/base-06-section1-step1-1.png)

Dans la fenêtre Project, accédez au dossier **Ressources** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, cliquez sur le préfabriqué **PressableRoundButton** puis faites-le glisser vers l’objet **Buttons**. Ensuite, cliquez avec le bouton droit sur PressableRoundButton, puis sélectionnez **Duplicate** pour créer une copie. Répétez l’opération jusqu’à obtenir un total de trois objets PressableRoundButton :

![Unity avec le préfabriqué PressableRoundButton nouvellement ajouté](images/mr-learning-base/base-06-section1-step1-2.png)

Dans la fenêtre Hierarchy, sélectionnez l’objet **Buttons**, puis, dans la fenêtre Inspector (Inspecteur), utilisez le bouton **Add Component** pour ajouter le composant **GridObjectCollection** et le configurer de la façon suivante :

* **Sort Type** (Type de tri) : Child Order (Classement enfant)
* **Layout** (Disposition) : Horizontale
* **Cell Width** (Largeur de cellule) : 0.2
* **Anchor** (Ancrage) : Middle Left (Milieu gauche)

Cliquez ensuite sur le bouton **Update Collection** (Mettre à jour la collection) pour mettre à jour la position des objets enfants de l’objet Buttons :

![Objet Buttons d’Unity avec le composant GridObjectCollection ajouté, configuré et appliqué](images/mr-learning-base/base-06-section1-step1-3.png)

Dans la fenêtre Hierarchy, nommez les boutons **Hints**, **Explode** et **Reset**.

Pour chaque bouton, sélectionnez l’objet enfant **SeeItSayItLabel** > **TextMeshPro**, puis, dans la fenêtre Inspector, modifiez le texte du composant **TextMeshPro - Text** pour qu’il corresponde aux noms des boutons :

![Unity avec des étiquettes de texte de bouton configurées](images/mr-learning-base/base-06-section1-step1-4.png)

Une fois terminé, réduisez les objets enfants de l’objet Buttons.

Dans la fenêtre Hierarchy, sélectionnez l’objet de bouton **Hints**, puis, dans la fenêtre Inspector, configurez l’événement **Interactable.OnClick ()** de la façon suivante :

* Affectez l’objet **RoverAssembly** au champ **None (Object)** .
* Dans la liste déroulante **No Function**, sélectionnez **PlacementHintsController** > **TogglePlacementHints ()** pour définir cette fonction en tant qu’action à exécuter lorsque l’événement est déclenché.

![Unity avec l’événement OnClick de l’objet de bouton Hints configuré](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> Le composant Interactable est un conteneur tout-en-un qui permet à tout objet de pouvoir facilement interagir et répondre aux entrées. Le composant Interactable agit comme un fourre-tout pour tous les types d’entrée, notamment les entrées tactiles, les rayons manuels, la parole, entre autres, et achemine ces interactions dans des événements et des réponses de thème visuel. Pour savoir comment le configurer pour différents types d’entrée et pour personnaliser son thème visuel, vous pouvez consulter le guide [Interactable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) dans le [portail de la documentation MRTK](/windows/mixed-reality/mrtk-unity/).

Dans la fenêtre Hierarchy, sélectionnez l’objet de bouton **Explode**, puis, dans la fenêtre Inspector, configurez l’événement **Interactable.OnClick ()** de la façon suivante :

* Affectez l’objet **RoverAssembly** au champ **None (Object)** .
* Dans la liste déroulante **No Function**, sélectionnez **ExplodedViewController** > **ToggleExplodedView ()** pour définir cette fonction en tant qu’action à exécuter lorsque l’événement est déclenché.

![Unity avec l’événement OnClick de l’objet de bouton Explode configuré](images/mr-learning-base/base-06-section1-step1-6.png)

Appuyez sur le bouton Play pour passer en mode jeu. Ensuite, maintenez le bouton de la barre d’espace appuyé pour activer la main, et utilisez la souris pour appuyer sur le bouton **Hints** afin d’activer/désactiver la visibilité des objets indicateurs de placement :

![Vue partagée du mode Play d’Unity avec le bouton Hints enfoncé](images/mr-learning-base/base-06-section1-step1-7.png)

et le bouton **Explode** pour activer ou désactiver la vue éclatée :

![Vue partagée du mode Play d’Unity avec le bouton Explode enfoncé](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>Création d’un menu dynamique qui suit l’utilisateur

Dans la fenêtre Project, accédez au dossier **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus**. Cliquez sur le préfabriqué **NearMenu4x1** puis faites-le glisser vers la fenêtre Hierarchy. Définissez la **Position** du composant Transform sur X = 0, Y =-0.4, Z = 0, puis configurez-le de la façon suivante :

* Vérifiez que le **Tracked Target Type** du composant **SolverHandler** est défini sur **Head**.
* Cochez la case à côté de **RadialView** pour le composant Solver afin de l’activer par défaut.

![Unity avec le préfabriqué Menu nouvellement ajouté à proximité sélectionné](images/mr-learning-base/base-06-section2-step1-1.png)

Dans la fenêtre Hierarchy, attribuez le nom **Menu** à l’objet, puis développez son objet enfant **ButtonCollection** pour afficher les quatre boutons :

![Unity avec l’objet Menu sélectionné et l’objet ButtonCollection développé](images/mr-learning-base/base-06-section2-step1-2.png)

Renommez le premier bouton de ButtonCollection en Indicator puis, dans la fenêtre Inspector, configurez le composant Button Config Helper (Script) comme suit :

* Modifiez la valeur de **Main Label Text** pour qu’elle corresponde au nom du bouton.
* Affectez l’objet Indicator qui ressemble à un chevron au champ None (Object).
* Dans la liste déroulante **No Function**, sélectionnez **GameObject** > **SetActive (bool)** pour définir cette fonction en tant qu’action à exécuter lorsque l’événement est déclenché.
* Vérifiez que la case de l’argument est **cochée**.
* Remplacez la valeur **Icon** par l’icône de recherche.

![Unity avec l’objet de bouton Indicator et le Button Config Helper configuré](images/mr-learning-base/base-06-section2-step1-3.png)

Pour désactiver l’objet Indicator de chevron, dans la fenêtre Hierarchy, sélectionnez l’objet Indicator qui ressemble à un chevron, puis dans la fenêtre Inspector :

* Décochez la case à côté de son nom pour le rendre inactif par défaut.
* Utilisez le bouton **Add Component** pour ajouter le composant **Directional Indicator Controller (Script)**

![Unity avec l’objet Indicator sélectionné et désactivé, et le composant DirectionalIndicatorController ajouté](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> Maintenant, quand l’application démarre, l’objet Indicator de chevron est désactivé par défaut ; vous pouvez l’activer en appuyant sur le bouton Indicator.

> [!NOTE]
> Directional Indicator Controller (Script) ne fait pas partie du MRTK, mais il a été inclus avec les ressources du tutoriel.

Renommez le deuxième bouton **TapToPlace**, puis, dans la fenêtre Inspector, configurez le composant **Button Config Helper (Script)** de la façon suivante :

* Modifiez la valeur de **Main Label Text** pour qu’elle corresponde au nom du bouton.
* Affectez l’objet RoverExplorer > **RoverAssembly** au champ **None (Object)** .
* Dans la liste déroulante **No Function**, sélectionnez **TapToPlace** > **bool Enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.
* Vérifiez que la case de l’argument est **cochée**.
* Remplacez la valeur **Icon** par l’icône représentant un rayon émanant d’une main.

![Unity avec l’objet de bouton TapToPlace et le Button Config Helper configuré](images/mr-learning-base/base-06-section2-step1-5.png)

Dans la fenêtre Hierarchy, sélectionnez l’objet **RoverAssembly** puis, dans la fenêtre Inspector, configurez le composant **Tap To Place (Script)** de la façon suivante :

* Décochez la case à côté de son nom pour le rendre inactif par défaut.
* Dans la section d’événement **On Placing Stopped ()** , cliquez sur l’icône **+** pour ajouter un événement :
* Affectez l’objet RoverExplorer > **RoverAssembly** au champ **None (Object)** .
* Dans la liste déroulante **No Function**, sélectionnez **TapToPlace** > **bool Enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.
* Vérifiez que la case de l’argument est **décochée**.

![Unity avec le composant TapToPlace reconfiguré](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> Désormais, lorsque l’application démarre, la fonctionnalité Tap to Place est désactivée par défaut. Vous pouvez l’activer en appuyant sur le bouton Tap to Place. En outre, une fois que l’opération Tap to Place est terminée, cette fonctionnalité est désactivée.

## <a name="adding-text-to-the-scene"></a>Ajout de texte à la scène

Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **Table**, puis sélectionnez **3D Object** > **Text - TextMeshPro** pour ajouter un objet texte en tant qu’enfant de l’objet Table. Ensuite, dans la fenêtre Inspector, configurez le composant **Rect Transform** de la façon suivante :

* Attribuez la valeur 1 à **Pos Y**.
* Attribuez la valeur 1 à **Width**.
* Attribuez la valeur 1 à **Height**.
* Attribuez la valeur 90 à **Rotation X**.

![Unity avec l’objet TextMeshPro nouvellement créé sélectionné](images/mr-learning-base/base-06-section3-step1-1.png)

Configurez ensuite le composant **TextMeshPro - Text** de la façon suivante :

* Remplacez la valeur de **Text** par Rover Explorer.
* Remplacez la valeur de **Font Style** par Bold.
* Attribuez la valeur 1 à **Font Size**.
* Modifiez la valeur de Extra Settings > **Margins** sur 0.03.

![Unity avec le composant TextMeshPro configuré](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>Ajout d’info-bulles

Dans la fenêtre Project, accédez au dossier **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** pour trouver les préfabriqués d’info-bulle :

![Fenêtre de projet Unity avec le dossier ToolTips sélectionné](images/mr-learning-base/base-06-section4-step1-1.png)

Dans la fenêtre Hierarchy, développez l’objet RoverExplorer > **RoverParts**, puis sélectionnez tous les objets enfants RoverParts. Ensuite, dans la fenêtre Inspector, utilisez le bouton **Add Component** (Ajouter un composant) pour ajouter le composant **ToolTipSpawner** et le configurer de la façon suivante :

* Vérifiez que la case **Focus Enabled** (Focus activé) est cochée, afin que l’affichage de l’info-bulle soit déclenché lorsque l’utilisateur regarde le composant.
* Affectez le préfabriqué **Simple Line ToolTip** de la fenêtre Project au champ **Prefab**.
* Configurez ToolTip Override Settings > **Settings Mode** sur **Override**.
* Configurez ToolTip Override Settings > **Manual Pivot Local Position Y** sur **1.5**

![Unity avec tous les objets de composant du Rover sélectionnés, et le composant ToolTipSpawner ajouté et configuré](images/mr-learning-base/base-06-section4-step1-2.png)

Dans la fenêtre Hiérarchie, sélectionnez le premier composant Camera_Part, RoverParts > **Camera_Part**, puis configurez le composant **ToolTipSpawner** de la façon suivante :

* Remplacez la valeur de **Tool Tip Text** pour qu’elle reflète le nom du composant, en l’occurrence, **Camera**.

![Unity avec la caméra ToolTipText configurée](images/mr-learning-base/base-06-section4-step1-3.png)

**Répétez** cette étape pour chacun des objets du composant Rover afin de configurer le composant **ToolTipSpawner** de la façon suivante :

* Pour **Generator_Part**, remplacez la valeur de **Tool Tip Text** par **Generator**.
* Pour **Lights_Part**, remplacez la valeur de **Tool Tip Text** par **Lights**.
* Pour **UHFAntenna_Part**, remplacez la valeur de **Tool Tip Text** par **UHF Antenna**.
* Pour **Spectrometer_Part**, remplacez la valeur de **Tool Tip Text** par **Spectrometer**.

Appuyez sur le bouton Play pour passer en mode jeu. Ensuite, maintenez le bouton droit de la souris appuyé tout en déplaçant la souris jusqu’à ce que le regard atteigne l’un des composants et que l’info-bulle de ce composant s’affiche :

![Vue partagée du mode Play d’Unity avec une info-bulle déclenchée par le suivi](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez vu comment créer une interface utilisateur simple avec les préfabriqués de boutons et de menus MRTK, ainsi qu’avec le composant TextMeshPro d’Unity. Vous avez également vu comment configurer les boutons pour déclencher des événements lorsque l’utilisateur appuie dessus. Enfin, vous avez vu comment ajouter des info-bulles dynamiques pour fournir à l’utilisateur des informations supplémentaires.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 7. Interaction avec les objets 3D](mr-learning-base-07.md)
