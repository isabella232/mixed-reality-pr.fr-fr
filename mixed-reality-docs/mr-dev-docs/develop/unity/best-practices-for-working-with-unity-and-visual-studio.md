---
title: Meilleures pratiques pour Unity et Visual Studio
description: Trucs et astuces pour rationaliser le flux de travail de création d’une application de réalité mixte avec Unity et Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Déployez, Unity, Visual Studio, HoloLens, HoloLens 2, casque immersif, meilleures pratiques, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, UWP, Visual Studio Tools, SDK Windows
ms.openlocfilehash: edd79b95d02cfeb1da4effc485fc57078e3d24a3
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042260"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Bonnes pratiques sur l’utilisation d’Unity et de Visual Studio

Lorsque vous créez une application de réalité mixte avec Unity, vous devez basculer entre Unity et Visual Studio pour générer et déployer le package d’application sur HoloLens ou sur un casque immersif. Par défaut, deux instances de Visual Studio sont nécessaires : une instance pour modifier les scripts Unity et une autre pour le déploiement sur l’appareil et le débogage. Les instructions suivantes vous permettent de développer à l’aide d’une instance de Visual Studio unique, en réduisant la fréquence de l’exportation des projets Unity et en améliorant l’expérience de débogage.

## <a name="improving-iteration-time"></a>Amélioration de l’heure des itérations

La prise en charge du serveur principal de script .NET dans Unity a été dépréciée dans Unity 2018 et supprimée à partir de Unity 2019 +. nous vous recommandons donc de basculer vers [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). Toutefois, il se peut que vous rencontriez des temps de génération plus longs entre Unity et Visual Studio. Pour améliorer l’itération plus rapidement, configurez votre environnement pour obtenir les meilleurs résultats de compilation :

1) Utilisez la génération incrémentielle en générant votre projet dans le même répertoire à chaque fois, en réutilisant les fichiers prédéfinis
2) Désactiver les analyses logicielles anti-programme malveillant pour votre projet & les dossiers de build
   - Ouvrir la **protection contre les menaces contre les Virus &** sous votre application Paramètres Windows 10
   - Sélectionnez **gérer les paramètres** sous **virus & les paramètres de protection contre les menaces**
   - Sélectionnez **Ajouter ou supprimer des exclusions** sous la section **exclusions** .
   - Sélectionnez **Ajouter une exclusion** , puis sélectionnez le dossier contenant le code de votre projet Unity et les sorties de génération
3) Utiliser un SSD pour la génération

Pour plus d’informations, consultez [optimisation des temps de génération pour IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) . Examinez également [le débogage sur le serveur principal IL2CPP Scripting](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Envisagez d’installer l' [extension Visual Studio *UnityScriptAnalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Cet outil analyse vos scripts C# Unity pour le code qui peut être écrit de façon plus optimisée.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools pour Unity

Télécharger [outils Visual Studio pour Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Avantages de Outils Visual Studio pour Unity**
* Déboguez Unity en mode de lecture de l’éditeur à partir de Visual Studio en plaçant des points d’arrêt, en évaluant des variables et des expressions complexes.
* Utilisez l’Explorateur de projets Unity pour rechercher votre script avec exactement la même hiérarchie que celle affichée par Unity.
* Récupérez la console Unity directement à l’intérieur de Visual Studio.
* Utilisez les assistants pour créer rapidement des scripts ou y accéder.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Exposer des variables de classe C# pour faciliter le paramétrage

Il existe deux façons d’exposer des variables de classe. La méthode recommandée consiste à ajouter l’attribut [SerializeField] à vos variables privées. Les champs sérialisés sont accessibles à partir de l’éditeur, mais ne sont pas exposés par programmation.  L’autre option consiste à rendre les variables de classe C# publiques pour les exposer dans l’interface utilisateur de l’éditeur. 

Les deux approches permettent de modifier facilement les variables tout en lisant dans l’éditeur, ce qui est particulièrement utile pour le paramétrage des propriétés de mécanicien d’interaction.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Régénérer les solutions Visual Studio UWP après une mise à niveau de SDK Windows ou Unity

Les solutions Visual Studio UWP archivées dans le contrôle de code source peuvent être obsolètes après la mise à niveau vers un nouveau SDK Windows ou un moteur Unity. Vous pouvez résoudre les solutions obsolètes après en générant une nouvelle solution UWP à partir d’Unity et en fusionnant les différences dans la solution archivée.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Utiliser des ressources au format texte pour faciliter la comparaison des modifications de contenu

Le stockage des ressources au format texte facilite l’examen des différences de modification de contenu dans Visual Studio. Vous pouvez stocker des éléments multimédias au format texte en sélectionnant **modifier > paramètres du projet > éditeur** et en sélectionnant le mode de **sérialisation** du **texte**. Toutefois, la fusion de modifications de fichiers de ressources texte est sujette aux erreurs et n’est pas recommandée. vous pouvez donc envisager d’activer des extractions binaires exclusives dans votre contrôle de code source.

## <a name="see-also"></a>Voir aussi
- [Visual Studio Tools pour Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Optimisation des temps de génération pour IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Extension Visual Studio](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)