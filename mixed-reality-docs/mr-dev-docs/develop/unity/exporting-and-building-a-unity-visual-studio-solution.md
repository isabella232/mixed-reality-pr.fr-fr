---
title: Exportation et création de solutions Unity Visual Studio
description: Cet article décrit l’exportation de votre projet de réalité mixte à partir d’Unity afin que vous puissiez le générer et le déployer dans Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Visual Studio, exporter, générer, déployer, HoloLens, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, UWP, déploiement
ms.openlocfilehash: 4da20a30375c7204c532a19c129c9265c0fa27d9
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010410"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportation et création de solutions Unity Visual Studio

Si votre application n’a pas besoin du clavier système, nous vous recommandons de *l’utiliser pour que votre* application utilise légèrement moins de mémoire et un temps de lancement plus rapide. Toutefois, si vous utilisez le clavier du système via l’API TouchScreenKeyboard, vous devez exporter le projet en tant que *code XAML*.

## <a name="how-to-export-from-unity"></a>Exportation à partir d’Unity

![Paramètres de build Unity](images/unitybuildsettings-300px.png)<br>
*Paramètres de build dans l’éditeur Unity*

1. Quand vous êtes prêt à exporter votre projet à partir d’Unity, ouvrez le menu **fichier** et sélectionnez **paramètres de Build...**
2. Sélectionnez **Ajouter des scènes ouvertes** pour ajouter votre scène à la Build.
3. Dans la boîte de dialogue **paramètres de build** , choisissez les options suivantes à exporter pour HoloLens :
   * **Plateforme :** *plateforme Windows universelle* et veillez à sélectionner **basculer la plateforme** pour que votre sélection prenne effet.
   * **SDK :** *Universal 10*.
   * **Type de build UWP :** *D3D*.
4. **Facultatif**: **Unity C# Projects :** Checked.

>[!NOTE]
>L’activation de cette case à cocher vous permet d’effectuer les opérations suivantes :
>* Déboguez votre application dans le débogueur distant Visual Studio.
>* Modifiez les scripts dans le projet Unity C# tout en utilisant IntelliSense pour les API WinRT.

5. Dans la fenêtre **paramètres de Build...** , ouvrez paramètres du **lecteur...**
6. Sélectionnez les **paramètres de plateforme Windows universelle** onglet.
7. Développez le groupe **XR Settings**.
8. Dans la section **paramètres XR** , cochez la case **Virtual Really Supported** pour ajouter une nouvelle liste d' **appareils de réalité virtuelle** et confirmer **« Windows Mixed Reality »** est répertoriée en tant qu’appareil pris en charge.
9. Revenez à la boîte de dialogue **paramètres de build** .
10. Sélectionnez **Build**.
11. Dans la boîte de dialogue de l’Explorateur Windows qui s’affiche, créez un nouveau dossier pour contenir la sortie de la génération d’Unity. En règle générale, nous nommez le dossier « App ».
12. Sélectionnez le dossier que vous venez de créer, puis sélectionnez **Sélectionner un dossier**.
13. Une fois la génération de Unity terminée, une fenêtre de l’Explorateur Windows s’ouvre sur le répertoire racine du projet. Accédez au dossier nouvellement créé.
14. Ouvrez le fichier de solution Visual Studio généré situé dans ce dossier.

## <a name="when-to-re-export-from-unity"></a>Moment de la réexportation à partir d’Unity

Cochez la case **projets C#** lors de l’exportation de votre application à partir d’Unity crée une solution Visual Studio qui comprend tous vos fichiers de script Unity. L’utilisation de tous vos scripts dans un même emplacement vous permet d’effectuer une itération sans réexportation à partir d’Unity. Toutefois, si vous apportez des modifications à votre projet qui ne modifient pas simplement le contenu des scripts, vous devez réexporter à partir d’Unity. Voici quelques exemples de tentatives de réexportation à partir d’Unity :
* Vous ajoutez ou supprimez des ressources dans l’onglet projet.
* Vous pouvez modifier n’importe quelle valeur sous l’onglet Inspector.
* Vous ajoutez ou supprimez des objets dans l’onglet hiérarchie.
* Vous modifiez les paramètres d’un projet Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Génération et déploiement d’une solution Unity Visual Studio

Le reste de la génération et du déploiement d’applications s’effectue dans [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md). Vous devrez spécifier une configuration de build Unity. Les conventions d’affectation des noms de Unity peuvent différer de ce que vous utilisez dans Visual Studio :

|  Configuration  |  Explication | 
|----------|----------|
|  Débogage  |  Toutes les optimisations désactivées et le profileur est activé. Utilisé pour déboguer les scripts. | 
|  Master  |  Toutes les optimisations sont activées et le profileur est désactivé. Utilisé pour soumettre des applications au Windows Store. | 
|  Libérer  |  Toutes les optimisations sont activées et le profileur est activé. Utilisé pour évaluer les performances de l’application. | 

Notez que la liste ci-dessus est un sous-ensemble des déclencheurs courants qui entraînent la génération du projet Visual Studio. En général, la modification des fichiers. cs à partir de Visual Studio ne nécessite pas la régénération du projet à partir d’Unity.

## <a name="troubleshooting"></a>Dépannage

Si vous constatez que les modifications apportées à vos fichiers. cs ne sont pas reconnues dans votre projet Visual Studio, vérifiez que les **projets Unity C#** sont activés lorsque vous générez le projet vs à partir du menu générer de Unity.
