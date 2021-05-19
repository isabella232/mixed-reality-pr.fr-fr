---
title: Système de scène - Bien démarrer
description: Page d’accueil du système de scène avec MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 205b89d4defdeb5418a8a82896551d681cccde3d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144299"
---
# <a name="scene-system-overview"></a>Vue d’ensemble du système de scène

## <a name="when-to-use-the-scene-system"></a>Quand utiliser le système de scène

Si votre projet est constitué d’une seule scène, le système de scène n’est probablement pas nécessaire. Elle est particulièrement utile quand une ou plusieurs des conditions suivantes sont remplies :

- Votre projet comporte plusieurs scènes.
- Vous êtes utilisé pour le chargement d’une scène unique, mais vous n’aimez pas la manière dont il détruit l’instance MixedRealityToolkit.
- Vous souhaitez disposer d’un moyen simple de charger plusieurs scènes pour créer votre expérience.
- Vous souhaitez disposer d’un moyen simple pour effectuer le suivi des opérations de chargement en cours ou un moyen simple de contrôler l’activation de scènes pour plusieurs scènes en cours de chargement à la fois.
- Vous souhaitez garantir la cohérence et la prédiction de l’éclairage dans toutes vos scènes.

## <a name="scene-system-resources"></a>Ressources système de scène

Par défaut, le système de scène utilise une paire d’objets de scène (DefaultManagerScene et DefaultLighting Scene). Si l’une de ces scènes est introuvable, un message s’affiche dans l’inspecteur de profil du système de scène.

![Message de ressources par défaut](../images/scene-system/DefaultResourcesMessage.png)

>! Observe Si le projet utilise un gestionnaire personnalisé et des scènes d’éclairage, ce message peut être ignoré en toute sécurité.

Les sections suivantes décrivent maintenant comment résoudre ce message, en fonction de la méthode utilisée pour importer le Toolkit de réalité mixte.

### <a name="unity-package-manager-upm"></a>Gestionnaire de package Unity (UPM)

Dans les packages UPM de la boîte à outils de réalité mixte, les ressources système de scène sont empaquetées comme un exemple. En raison de l’immuable des packages UPM, Unity n’est pas en mesure d’ouvrir le fichier de scène nécessaire, sauf s’ils sont importés explicitement dans le projet.

Pour importer, procédez comme suit :

- Sélectionner le  >  **Gestionnaire de package** Windows
- Sélectionner **Mixed Reality Toolkit Foundation**
- Localiser les **ressources système** de la scène dans la section **exemples**

  ![Importer des ressources système de scène](../images/scene-system/UpmImportSceneSystemResources.png)

- Sélectionner **Importer**

### <a name="asset-unitypackage-files"></a>Fichiers de ressources (. pour Unity)

Si le dossier SceneSystemResources a été supprimé ou a été désélectionné lors de l’importation, il peut être récupéré en procédant comme suit :

- Sélectionner le package  >    >  **personnalisé** du package d’importation de ressources
- Ouvrir le package **Microsoft. MixedReality. Toolkit. Foundation**
- S’assurer que les options **services/SceneSystem/SceneSystemResources** et toutes les options enfants sont sélectionnées

  ![Réimporter les ressources système de la scène](../images/scene-system/ReimportSceneSystemResources.png)

- Sélectionner **Importer**

## <a name="how-to-use-the-scene-system"></a>Comment utiliser le système de scène

- [Types de scènes](scene-system-scene-types.md)
- [Chargement de scènes de contenu](scene-system-content-loading.md)
- [Surveillance du chargement du contenu](scene-system-load-progress.md)
- [Chargement de scène d’éclairage](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>Paramètres de l’éditeur

Par défaut, le système de scène applique plusieurs comportements dans l’éditeur Unity. Si vous trouvez l’un de ces comportements, vous pouvez le désactiver dans la section paramètres de l' **éditeur** de votre profil système de scène.

- `Editor Manage Build Settings:` Si la valeur est true, le service met automatiquement à jour vos paramètres de build, garantissant ainsi que toutes les scènes de gestion, d’éclairage et de contenu sont ajoutées. Désactivez cette opération si vous souhaitez un contrôle total sur les paramètres de Build.

- `Editor Enforce Scene Order:` Si la valeur est true, le service s’assure que la scène Manager est affichée en premier dans la hiérarchie de la scène, suivie de Lighting, puis du contenu. Désactivez cette opération si vous souhaitez un contrôle total sur la hiérarchie des scènes.

- `Editor Manage Loaded Scenes:` Si la valeur est true, le service s’assure que le gestionnaire, le contenu et les scènes d’éclairage sont toujours chargés. Désactivez si vous souhaitez un contrôle total sur les scènes chargées dans l’éditeur.

- `Editor Enforce Lighting Scene Types:` Si la valeur est true, le service garantit que seuls les composants liés à l’éclairage définis dans `PermittedLightingSceneComponentTypes` sont autorisés dans les scènes d’éclairage. Désactivez si vous souhaitez un contrôle total sur le contenu des scènes d’éclairage.

![Paramètres de l’éditeur système de scène](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
