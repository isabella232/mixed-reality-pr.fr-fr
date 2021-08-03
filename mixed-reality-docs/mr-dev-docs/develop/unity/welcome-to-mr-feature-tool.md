---
title: Bienvenue dans Mixed Reality Feature Tool
description: Découvrez les principes de base de Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 1244f9cd4da0d6ae0b5c6f92698f87f0edd812e2
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757090"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>Bienvenue dans Mixed Reality Feature Tool

![Image de la bannière de Mixed Reality Feature Tool](images/feature-tool-banner.jpg)

> [!IMPORTANT]
> Pour le moment, Mixed Reality Feature Tool est disponible seulement pour Unity. Si vous développez dans Unreal, reportez-vous à la documentation sur l’[installation des outils](../install-the-tools.md).

Mixed Reality Feature Tool est un nouveau moyen pour les développeurs de découvrir, de mettre à jour et d’ajouter des packages de fonctionnalités de réalité mixte dans des projets Unity. Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation. Si vous n’avez peut-être jamais travaillé avec un fichier manifeste auparavant, sachez qu’il s’agit d’un fichier JSON contenant tous vos packages de projet. Une fois que vous avez validé les packages souhaités, Mixed Reality Feature Tool les télécharge dans le projet de votre choix.

## <a name="system-requirements"></a>Configuration requise

Pour pouvoir exécuter Mixed Reality Feature Tool, voici ce dont vous avez besoin :

* [Runtime .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> Mixed Reality Feature Tool fonctionne actuellement seulement sur Windows, mais la prise en charge de MacOS sera bientôt disponible !

## <a name="download"></a>Téléchargement

Une fois que votre environnement est configuré :

* [Téléchargez la dernière version de Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) à partir du Centre de téléchargement Microsoft.
* Une fois le téléchargement terminé, décompressez le fichier et enregistrez-le sur votre ordinateur.
    * Nous vous recommandons de créer un raccourci vers le fichier exécutable pour un accès plus rapide.

> [!NOTE]
> Si vous n’avez jamais utilisé le Gestionnaire de package Unity, suivez nos [instructions UPM](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).

## <a name="changes-in-this-release"></a>Changements dans cette version

La version bêta 1.0.2103 comprend les correctifs suivants :

* Améliorations de la détection d’erreurs de téléchargement.
* Mises à jour sur la façon dont les manifestes sont écrits pour éviter l’échec de la mise à jour.
* L’échappement a été supprimé des chemins d’accès des fichiers dans le manifeste du projet.

Les fonctionnalités suivantes ont été ajoutées dans cette version :

* Le catalogue de fonctionnalités est maintenant mis en cache. Pour rechercher de nouvelles fonctionnalités et mises à jour, utilisez le bouton Actualiser dans Découverte.
* Déplacez la sélection de projet de l’étape Importation avant la Découverte.
* Les packages disponibles sont filtrés par la version Unity spécifiée du projet.
* L’affichage Découverte montre maintenant les packages actuellement installés.

## <a name="1-getting-started"></a>1. Mise en route

Lancez Mixed Reality Feature Tool à partir du fichier exécutable, qui affiche la page de démarrage lors du premier lancement :

![Mise en route](images/FeatureToolStart.png)

Dans la page de démarrage, vous pouvez :

* [Configurer](configuring-feature-tool.md) les paramètres de l’outil en utilisant le bouton avec l’**icône d’engrenage**
* Utiliser le bouton avec le **point d’interrogation** pour lancer le navigateur web par défaut et afficher notre documentation
* Sélectionner **Start** pour commencer la découverte des packages de fonctionnalités

## <a name="2-selecting-your-unity-project"></a>2. Sélection de votre projet Unity

Pour vous assurer que toutes les fonctionnalités découvertes sont prises en charge sur la version d’Unity de votre projet, la première étape consiste à faire pointer Mixed Reality Feature Tool sur votre projet à l’aide du bouton représentant des **points de suspension** (à droite du champ de chemin d’accès au projet).

![Sélectionnez le projet Unity](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier. Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.

Une fois le dossier de votre projet localisé, cliquez sur le bouton Ouvrir pour revenir à Mixed Reality Feature Tool.

> [!IMPORTANT]
> Mixed Reality Feature Tool effectue la validation pour s’assurer qu’il a été dirigé vers un dossier de projet Unity. Le dossier doit contenir les dossiers `Assets`, `Packages` et `Project Settings`.

## <a name="3-discovering-and-acquiring-feature-packages"></a>3. Découverte et acquisition de packages de fonctionnalités

> [!NOTE]
> La version bêta 1.0.2103 met désormais en cache le contenu du catalogue de fonctionnalités à chaque accès au serveur. Cette modification permet un accès rapide aux fonctionnalités disponibles, au détriment de l’affichage des dernières données absolues. Pour mettre à jour le catalogue, utilisez le bouton **Actualiser**.

Les fonctionnalités sont regroupées par catégorie pour faciliter les recherches. Par exemple, la catégorie **Mixed Reality Toolkit** vous permet de choisir parmi plusieurs fonctionnalités :

![Découverte et acquisition](images/FeatureToolDiscovery.png)

Lorsque Mixed Reality Feature Tool reconnaît des fonctionnalités précédemment importées, il affiche un message de notification pour chaque fonctionnalité.

![Notification de fonctionnalité importée](images/feature-tool-imported-note.png)


Une fois que vous avez effectué vos choix, sélectionnez **Get features** pour récupérer tous les packages nécessaires auprès du catalogue. Pour plus d’informations, consultez [Découverte et acquisition des fonctionnalités](discovering-features.md).

## <a name="4-importing-feature-packages"></a>4. Importation de packages de fonctionnalités

Après l’acquisition, l’ensemble complet des packages est présenté ainsi qu’une liste des dépendances requises. Si vous avez besoin de modifier des sélections de fonctionnalités ou de packages, c’est le moment :

![Importation de packages](images/FeatureToolImport.png)

Nous vous recommandons vivement d’utiliser le bouton **Validate** pour vérifier que le projet Unity peut importer correctement les fonctionnalités sélectionnées. Après la validation, vous voyez une boîte de dialogue contextuelle avec un message indiquant la réussite ou bien une liste des problèmes identifiés.

Sélectionnez **Import**  pour continuer.

> [!NOTE]
> Une fois que vous avez cliqué sur le bouton **Import**, si des problèmes subsistent, vous voyez un simple message. La recommandation est de cliquer sur No et d’utiliser le bouton **Validate** pour visualiser et résoudre les problèmes.

Pour plus d’informations, consultez [Importation des fonctionnalités](importing-features.md).

## <a name="5-reviewing-and-approving-project-changes"></a>5. Examen et approbation des modifications de projet

La dernière étape consiste à examiner et à approuver les modifications proposées dans le manifeste et les fichiers de projet :

* Les modifications proposées pour le manifeste s’affichent à gauche.
* Les fichiers à ajouter au projet sont listés à droite.
* Le bouton **Compare** permet l’affichage côte à côte du manifeste actuel et des modifications proposées.

![Autorisation](images/FeatureToolApprovalRequest.png)

Pour plus d’informations, consultez [Examen et approbation des modifications du projet](reviewing-changes.md).

## <a name="6-project-updated"></a>6. Projet mis à jour

Une fois les modifications proposées approuvées, votre projet Unity cible est mis à jour de façon à référencer les fonctionnalités de réalité mixte sélectionnées.

![Projet mis à jour](images/FeatureToolProjectUpdated.png)

Le dossier **Packages** du projet Unity contient maintenant un sous-dossier **MixedReality** avec le ou les fichiers de package de fonctionnalités, et le manifeste contient la ou les références appropriées.

Revenez à Unity, attendez que les nouvelles fonctionnalités sélectionnées se chargent, puis commencez à créer !

## <a name="see-also"></a>Voir aussi

- [Configuration de Feature Tool](configuring-feature-tool.md)
- [Découverte et acquisition](discovering-features.md)
- [Visualisation des détails des packages de fonctionnalités](viewing-package-details.md)
- [Importation des packages sélectionnés](importing-features.md)
- [Examen et approbation des modifications du projet](reviewing-changes.md)