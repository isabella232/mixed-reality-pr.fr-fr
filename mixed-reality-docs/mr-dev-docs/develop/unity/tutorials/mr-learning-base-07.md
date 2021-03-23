---
title: Interaction avec les objets 3D
description: Ce cours vous montre comment utiliser Mixed Reality Toolkit (MRTK) pour interagir avec des objets 3D et les manipuler dans des applications de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, interactions avec des objets, contrôle des limites
ms.localizationpriority: high
ms.openlocfilehash: 1ab7b3a334639be564717d77d3bbc478a25e8326
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237240"
---
# <a name="7-interacting-with-3d-objects"></a>7. Interaction avec les objets 3D

Dans ce tutoriel, vous allez apprendre à activer la manipulation proche et lointaine des objets 3D et à limiter les types de manipulation autorisés. Vous allez aussi découvrir comment ajouter des contrôles de limites autour des objets 3D afin de faciliter le contrôle de la manipulation des objets.

## <a name="objectives"></a>Objectifs

* Apprendre à configurer des objets 3D afin de pouvoir interagir avec
* Découvrir comment ajouter un contrôle de limites à des objets 3D

## <a name="manipulating-3d-objects"></a>Manipulation d’objets 3D

Dans cette section, vous allez ajouter la capacité à manipuler toutes les pièces du Rover que vous avez disposées sur la table durant le tutoriel [Positionnement des objets dans la scène](mr-learning-base-04.md).

Voici les principales étapes à suivre pour y parvenir :

1. Ajouter le composant Object Manipulator (Script) à tous les objets de la pièce
2. Ajouter le composant NearInteractionGrabbable à tous les objets de la pièce
3. Configurer le composant Object Manipulator (Script)

> [!NOTE]
> Pour pouvoir **manipuler un objet**, celui-ci doit avoir les composants suivants :
>
> * Le composant **Collider**, par exemple un Box Collider
> * Le composant **Object Manipulator (Script)**
>
> Pour pouvoir **manipuler** et **saisir** un objet avec les mains suivies, celui-ci doit avoir les composants suivants :
>
> * Le composant **Collider**, par exemple un Box Collider
> * Le composant **Object Manipulator (Script)**
> * Le composant **NearInteractionGrabbable**

De plus, vous configurerez le RoverExplorer afin de pouvoir placer les pièces du Rover sur le Rover pour en faire un assemblage complet.

Dans la fenêtre de hiérarchie, développez l’objet RoverExplorer > **RoverParts** et sélectionnez tous ses objets de pièces de Rover enfants et l’objet **RoverAssembly** puis, dans la fenêtre de l’inspecteur, utilisez le bouton **Add Component** (Ajouter un composant) pour ajouter les composants suivants à tous les objets sélectionnés :

* Le composant **Object Manipulator (Script)**
* Le composant **NearInteractionGrabbable**
* Le composant **Part Assembly Controller (Script)**

![Unity avec RoverAssembly et tous les objets de composant du Rover sélectionnés, et les composants ajoutés](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> Pour sélectionner plusieurs objets qui ne sont pas les uns à côté des autres, appuyez sur la touche Ctrl et maintenez-la enfoncée pendant que vous utilisez la souris pour sélectionner un objet.

> [!NOTE]
> Quand vous ajoutez un Object Manipulator (Script), dans ce cas, le Constraint Manager (Script) est ajouté automatiquement, car Object Manipulator (Script) en dépend.

> [!NOTE]
> Dans le cadre de ce tutoriel, des colliders ont déjà été ajoutés aux pièces du Rover. Pour plus d’informations sur les colliders, vous pouvez consulter la documentation <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> d’Unity.

> [!NOTE]
> Part Assembly Controller (Script) ne fait pas partie du MRTK, mais il a été inclus avec les ressources du tutoriel.

Toujours avec les objets de pièces de Rover et l’objet RoverAssembly sélectionnés, dans la fenêtre de l’inspecteur, configurez le composant **Object Manipulator (Script)** comme suit :

* Dans la liste déroulante **Two Handed Manipulation Type** (Type de manipulation à deux mains), décochez Scale (Mise à l’échelle) afin que seuls **Move** (Déplacer) et **Rotate** (Faire pivoter) soient activés.

![Unity avec Two Handed Manipulation Type configuré](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> À ce stade, vous avez activé la manipulation d’objet pour tous les objets de pièces de Rover et l’objet RoverAssembly.

Dans la fenêtre Project, accédez au dossier **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** pour trouver les clips audio :

![Fenêtre de projet Unity avec le dossier Audio sélectionné](images/mr-learning-base/base-07-section1-step1-3.png)

Dans la fenêtre de hiérarchie, resélectionnez tous les **objets de pièces de Rover** puis, dans la fenêtre de l’inspecteur, utilisez le bouton **Add Component** pour ajouter le composant **Audio Sources** et configurez-le comme suit :

* Affectez le clip audio **MRTK_Scale_Start** au champ **AudioClip**.
* Décochez la case **Play On Awake** (Lire en cas d’activité)
* Affectez la valeur 1 à **Spatial Blend**.

![Unity avec tous les objets de composant du Rover sélectionnés, et le composant Audio Source ajouté et configuré](images/mr-learning-base/base-07-section1-step1-4.png)

Dans la fenêtre de hiérarchie, développez l’objet RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** pour révéler tous les objets d’indicateur de placement, puis sélectionnez la première pièce de Rover, RoverParts > **Camera_Part**, et configurez le composant **Part Assembly Controller (Script)** comme suit :

* Assignez l’objet **Camera_PlacementHint** au champ **Location To Place** (Emplacement).

![Unity avec composant Camera_Part PartAssemblyController configuré](images/mr-learning-base/base-07-section1-step1-5.png)

**Répétez** cette étape pour chacun des objets de pièces de Rover restants et l’objet RoverAssembly afin de configurer le composant **Part Assembly Controller (Script)** comme suit :

* Pour **Generator_Part**, assignez l’objet **Generator_PlacementHint** au champ **Location To Place**.
* Pour **Lights_Part**, assignez l’objet **Lights_PlacementHint** au champ **Location To Place**.
* Pour **UHFAntenna_Part**, assignez l’objet **UHFAntenna_PlacementHint** au champ **Location To Place**.
* Pour **Spectrometer_Part**, assignez l’objet **Spectrometer_PlacementHint** au champ **Location To Place**.
* Pour **RoverAssembly**, assignez l’objet lui-même (c’est-à-dire le même objet **RoverAssembly**), au champ **Location To Place**.

Dans la fenêtre de hiérarchie, sélectionnez l’objet de bouton RoverExplorer > Buttons > **Reset** puis, dans la fenêtre de l’inspecteur, configurez l’événement **OnClick ()** comme suit :

* Assignez l’objet **RoverAssembly** au champ **None (Object)** .
* Dans la liste déroulante **No Function**, sélectionnez **PartAssemblyController** > **ResetPlacement ()** pour définir cette fonction en tant qu’action à exécuter lorsque l’événement est déclenché.

![Unity avec l’événement OnClick de l’objet de bouton Reset configuré](images/mr-learning-base/base-07-section1-step1-6.png)

Si vous basculez maintenant en mode Game, vous pouvez utiliser l’interaction proche ou lointaine pour placer les pièces sur le Rover. Une fois que la pièce est proche de l’indicateur de placement correspondant, elle s’imbrique en place et devient partie intégrante du Rover. Pour réinitialiser les placements, vous pouvez appuyer sur le bouton Reset :

![Vue partagée du mode Play d’Unity avec le bouton Reset enfoncé](images/mr-learning-base/base-07-section1-step1-7.png)

Pour en savoir plus sur le composant Object Manipulator et ses propriétés associées, vous pouvez consulter le guide [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) dans le [portail de la documentation MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).

## <a name="adding-bounds-control"></a>Ajout d’un contrôle des limites

Un contrôle des limites (BoundsControl) rend plus facile et plus intuitive la manipulation d’objets avec une main pour l’interaction proche et lointaine, en fournissant des poignées qui peuvent être utilisées pour la mise à l’échelle et la rotation.

Dans cet exemple, vous allez ajouter un BoundsControl à l’objet RoverExplorer pour faciliter son déplacement, sa rotation et sa mise à l’échelle. Vous allez aussi configurer le menu afin de pouvoir activer ou désactiver le contrôle des limites.

Dans la fenêtre de hiérarchie, sélectionnez l’objet **RoverExplorer** puis, dans la fenêtre de l’inspecteur, utilisez le bouton **Add Component** pour ajouter les composants suivants :

* Composant **BoundsControl**
* Le composant **Object Manipulator (Script)**

Ensuite, **décochez** la case en regard de tous les composants afin de les rendre **désactivés** par défaut :

![Unity avec l’objet RoverExplorer sélectionné, et des composants ajoutés et désactivés](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> La visualisation du contrôle des limites est créée au moment de l’exécution et n’est donc pas visible avant l’entrée en mode Game.

> [!NOTE]
>Object Manipulator (Script) ajoute automatiquement Constraint Manager (Script)

Dans la fenêtre de hiérarchie, développez l’objet Menu > **ButtonCollection** pour afficher les quatre boutons et renommez le troisième bouton **BoundsControl_Enable** puis, dans la fenêtre de l’inspecteur, configurez le composant **Button Config Helper (Script)** comme suit :

* Affectez la valeur **Enable** à **Main Label Text** (Texte de l'étiquette principale).
* Assignez l’objet **RoverExplorer** au champ **None (Object)** .
* Dans la liste déroulante **No Function**, sélectionnez **BoundsControl** > **bool enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.
* Vérifiez que la case de l’argument est **cochée**.
* Cliquez sur la petite icône **+** pour ajouter un autre événement.
* Assignez l’objet **RoverExplorer** au champ **None (Object)** .
* Dans la liste déroulante **No Function**, sélectionnez **ObjectManipulator** > **bool Enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.
* Vérifiez que la case de l’argument est **cochée**.
* Conservez « cube avec contrôle des limites » comme **icône**.

![Unity avec l’objet de bouton BoundsControl_Enable sélectionné et le composant Button Config Helper configuré](images/mr-learning-base/base-07-section2-step1-2.png)

Renommez **BoundsControl_Disable** le quatrième et dernier bouton puis, dans la fenêtre de l’inspecteur, configurez le composant **Button Config Helper (Script)** comme suit :

* Affectez la valeur **Disable** à **Main Label Text**.
* Assignez l’objet **RoverExplorer** au champ **None (Object)** .
* Dans la liste déroulante **No Function**, sélectionnez **BoundsControl** > **bool enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.
* Vérifiez que la case de l’argument est **décochée**.
* Cliquez sur la petite icône **+** pour ajouter un autre événement.
* Assignez l’objet **RoverExplorer** au champ **None (Object)** .
* Dans la liste déroulante **No Function**, sélectionnez **ObjectManipulator** > **bool Enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.
* Vérifiez que la case de l’argument est **décochée**.
* Remplacez l’**icône** par « cube avec contrôle des limites ».

![Unity avec l’objet de bouton BoundsControl_Disable sélectionné et le composant Button Config Helper configuré](images/mr-learning-base/base-07-section2-step1-3.png)

Si vous passez maintenant en mode Game et que vous activez le contrôle des limites en cliquant sur le bouton Enable, vous pouvez utiliser l’interaction proche ou lointaine pour le déplacer, faire pivoter et mettre à l’échelle, et utiliser le bouton Disable pour le désactiver à nouveau :

![Vue partagée du mode Play de Unity avec le contrôle des limites en train d’être manipulé](images/mr-learning-base/base-07-section2-step1-4.png)

Pour plus d’informations sur le composant BoundsControl et ses propriétés associées, vous pouvez consulter le guide [Bounds Control](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) dans le [portail de la documentation MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez appris à activer la manipulation proche et lointaine pour les objets 3D et comment limiter les types de manipulation autorisés. Vous avez aussi appris à ajouter un contrôle des limites autour des objets 3D afin de faciliter le contrôle de la manipulation des objets.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 8. Utilisation du suivi oculaire](mr-learning-base-08.md)
