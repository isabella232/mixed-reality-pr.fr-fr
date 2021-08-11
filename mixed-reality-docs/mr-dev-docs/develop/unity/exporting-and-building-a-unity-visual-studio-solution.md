---
title: Exportation et création de solutions Unity Visual Studio
description: Cet article décrit l’exportation de votre projet de réalité mixte à partir d’Unity afin que vous puissiez le créer et le déployer dans Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity, visual studio, exporter, générer, déployer, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, UWP, déploiement
ms.openlocfilehash: 78410da352b1cce1377b35737376437608f3017c00334c1a489ede26d5170d2d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203606"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportation et création de solutions Unity Visual Studio

Si votre application n’a pas besoin du clavier système, nous vous recommandons de *l’utiliser pour que votre* application utilise légèrement moins de mémoire et un temps de lancement plus rapide. Toutefois, si vous utilisez le clavier du système via l’API TouchScreenKeyboard, vous devez exporter le projet en tant que *code XAML*.

## <a name="how-to-export-from-unity"></a>Exportation à partir d’Unity

![Paramètres de build Unity](images/unitybuildsettings-300px.png)<br>
*Paramètres de build dans l’éditeur Unity*

1. lorsque vous êtes prêt à exporter votre projet à partir d’unity, ouvrez le menu **fichier** et sélectionnez **générer Paramètres...**
2. Sélectionnez **Ajouter des scènes ouvertes** pour ajouter votre scène à la Build.
3. dans la boîte de dialogue **Paramètres de Build** , choisissez les options suivantes à exporter pour HoloLens :
   * **plateforme :** *plateforme Windows universelle* et veillez à sélectionner **basculer la plateforme** pour que votre sélection prenne effet.
   * **SDK :** *Universal 10*.
   * **Type de build UWP :** *D3D*.
4. **Facultatif**: **Unity C# Projects :** Checked.

>[!NOTE]
>L’activation de cette case à cocher vous permet d’effectuer les opérations suivantes :
>* déboguez votre application dans le débogueur distant Visual Studio.
>* Modifiez les scripts dans le projet Unity C# tout en utilisant IntelliSense pour les API WinRT.

5. à partir de la fenêtre **Paramètres de Build..** ., ouvrez le **Paramètres Player...**
6. sélectionnez l' **Paramètres pour plateforme Windows universelle** onglet.
7. Développez le groupe **XR Settings**.
8. dans la section **XR Paramètres** , cochez la case **virtual really supported** pour ajouter une nouvelle liste d' **appareils virtual reality** et confirmez que **« Windows Mixed Reality »** est répertorié comme appareil pris en charge.
9. revenez à la boîte de dialogue **Paramètres de Build** .
10. Sélectionnez **Build**.
11. dans la boîte de dialogue Windows Explorer qui s’affiche, créez un nouveau dossier pour contenir la sortie de la génération unity. En règle générale, nous nommez le dossier « App ».
12. Sélectionnez le dossier que vous venez de créer, puis sélectionnez **Sélectionner un dossier**.
13. une fois la génération de unity terminée, une fenêtre d’explorateur de Windows s’ouvre dans le répertoire racine du projet. Accédez au dossier nouvellement créé.
14. ouvrez le fichier solution Visual Studio généré situé dans ce dossier.

## <a name="when-to-re-export-from-unity"></a>Moment de la réexportation à partir d’Unity

l’activation de la case à cocher **projets C#** lors de l’exportation de votre application à partir d’unity crée une solution Visual Studio qui comprend tous vos fichiers de script unity. L’utilisation de tous vos scripts dans un même emplacement vous permet d’effectuer une itération sans réexportation à partir d’Unity. Toutefois, si vous apportez des modifications à votre projet qui ne modifient pas simplement le contenu des scripts, vous devez réexporter à partir d’Unity. Voici quelques exemples de tentatives de réexportation à partir d’Unity :
* vous ajoutez ou supprimez des ressources dans l’onglet Project.
* Vous pouvez modifier n’importe quelle valeur sous l’onglet Inspector.
* Vous ajoutez ou supprimez des objets dans l’onglet hiérarchie.
* Vous modifiez les paramètres d’un projet Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>création et déploiement d’une solution unity Visual Studio

Le reste de la génération et du déploiement d’applications se produit dans [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md). Vous devrez spécifier une configuration de build Unity. Les conventions d’affectation des noms de Unity peuvent différer de ce que vous utilisez dans Visual Studio :

|  Configuration  |  Explication | 
|----------|----------|
|  Débogage  |  Toutes les optimisations désactivées et le profileur est activé. Utilisé pour déboguer les scripts. | 
|  Master  |  Toutes les optimisations sont activées et le profileur est désactivé. Utilisé pour soumettre des applications au Windows Store. | 
|  Libérer  |  Toutes les optimisations sont activées et le profileur est activé. Utilisé pour évaluer les performances de l’application. | 

notez que la liste ci-dessus est un sous-ensemble des déclencheurs courants qui entraînent la génération du projet Visual Studio. en général, la modification des fichiers. cs à partir de Visual Studio ne nécessite pas la régénération du projet à partir d’unity.

## <a name="troubleshooting"></a>Dépannage

si vous constatez que les modifications apportées à vos fichiers. cs ne sont pas reconnues dans votre projet Visual Studio, assurez-vous que les **projets unity C#** sont vérifiés lorsque vous générez le projet visual studio à partir du menu générer de unity.
