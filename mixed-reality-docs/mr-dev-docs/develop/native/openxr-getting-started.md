---
title: Bien démarrer avec OpenXR
description: commencez à utiliser la norme de l’API OpenXR portable sur des casques Windows Mixed Reality et HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality, OpenXR Outils de développement, DirectX, native, application native, moteur personnalisé, intergiciel, prise en main, 101, extensions préliminaires, version du runtime OpenXR, état du système
ms.openlocfilehash: 6d334b491d231ab5987dd1bc6a3eb43f5e0fe30a82c6525bca1935fbf1cd83bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189148"
---
# <a name="getting-started-with-openxr"></a>Bien démarrer avec OpenXR

Vous pouvez développer avec OpenXR sur HoloLens 2 ou un casque immersif Windows Mixed Reality sur le bureau.  si vous n’avez pas accès à un casque, vous pouvez utiliser le HoloLens 2 Emulator ou le simulateur Windows Mixed Reality à la place.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Prise en main de OpenXR pour HoloLens 2

Pour commencer à développer des applications OpenXR pour HoloLens 2 :

1. configurez un HoloLens 2 ou suivez les instructions pour [installer une version récente de l’émulateur HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md). Vous devez déjà disposer de OpenXR 1,0 prêt à l’emploi si vous utilisez une image d’émulateur récente ou si l’appareil a mis à jour son système d’exploitation.
2. Assurez-vous que vous disposez de la dernière version du runtime OpenXR avec toutes les [Extensions](openxr.md#roadmap) présentes en lançant l’application du Windows **Store** à partir de l’appareil ou de l’émulateur.
    * Ouvrez le menu en haut à droite, sélectionnez **téléchargements et mises à jour**, puis choisissez **récupérer les mises à jour**.  

> [!NOTE]
> si vous utilisez l’émulateur, l’image de l’émulateur est réinitialisée à chaque fois que vous la démarrez. par conséquent, il est préférable de s’assurer que vous disposez [de la dernière version de l’image de l’émulateur HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>prise en main de OpenXR pour les casques Windows Mixed Reality

pour commencer à développer des applications OpenXR pour des casques Windows Mixed Reality immersifs :

1. assurez-vous que vous exécutez au moins la Mise à jour de mai 2019 de Windows 10 (1903), qui est la configuration minimale requise pour Windows Mixed Reality les utilisateurs finaux d’exécuter des applications OpenXR.  si vous utilisez une version antérieure de Windows 10, vous pouvez procéder à une mise à niveau à l’aide de l' <a href="https://www.microsoft.com/software-download/windows10" target="_blank">Assistant Windows 10 Update</a>.
2. configurez un Windows Mixed Reality casque ou suivez les instructions pour [activer le simulateur Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md).

Et voilà !  le Windows Mixed Reality runtime OpenXR est installé et activé automatiquement pour tous les utilisateurs Windows Mixed Reality.  le Microsoft Store maintient le runtime à jour.

pour réactiver le Windows Mixed Reality Runtime OpenXR, lancez le portail de réalité mixte à partir du menu Démarrer et sélectionnez « Fix it » en haut de la fenêtre.  Si ce bouton est manquant, le runtime OpenXR est déjà actif.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Obtention de la Outils de développement OpenXR pour Windows Mixed Reality

pour tester le Windows Mixed Reality Runtime OpenXR, vous pouvez installer le <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">Outils de développement OpenXR pour Windows Mixed Reality application</a>.  Cette application fournit une démonstration de diverses fonctionnalités OpenXR, ainsi qu’une page d’État du système avec des informations clés sur le runtime actif et le casque actuel.

lors de l’utilisation de l’émulateur de HoloLens 2, le moyen le plus simple d’installer le Outils de développement OpenXR pour Windows Mixed Reality s’effectue via le [portail des appareils Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md). accédez à la page « OpenXR », puis cliquez sur le bouton « installer » sous « fonctionnalités du développeur », qui fonctionne également sur les appareils HoloLens 2 physiques.

![Outils de développement OpenXR pour l’application Windows Mixed Reality](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Création d’un exemple d’application OpenXR

Veillez à [installer les outils](../install-the-tools.md) dont vous aurez besoin pour le développement OpenXR si vous ne l’avez pas déjà fait.

le projet <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> présente un exemple OpenXR simple avec les fichiers de projet Win32 et UWP HoloLens 2 dans Visual Studio. étant donné que la solution contient un projet HoloLens UWP, vous avez besoin de la [charge de travail de développement plateforme Windows universelle](../install-the-tools.md#installation-checklist) installée dans Visual Studio pour l’ouvrir entièrement.

Alors que les fichiers de projet Win32 et UWP sont distincts en raison des différences d’empaquetage et de déploiement, le code de l’application à l’intérieur de chaque projet est presque exactement le même !

Après avoir créé un .EXE de bureau Win32 OpenXR, vous pouvez l’utiliser avec un casque en VR sur toute plateforme de bureau VR prenant en charge OpenXR, quel que soit le type de casque.

après avoir créé un package d’application OpenXR UWP, vous pouvez [déployer ce package](../platform-capabilities-and-apis/using-visual-studio.md) sur un appareil HoloLens 2 ou sur le Emulator HoloLens 2.

## <a name="learning-the-openxr-api"></a>Learning de l’API OpenXR

Pour une visite guidée de l’API OpenXR, consultez cette vidéo de 60 minutes de l’exemple <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> dans Visual Studio.  La vidéo montre comment chacun des composants principaux de l’API OpenXR peut être utilisé dans votre propre moteur et illustre également certaines des applications générées sur OpenXR aujourd’hui :

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Intégrer le chargeur OpenXR dans un projet

Pour commencer à utiliser OpenXR dans un projet existant, vous devez inclure le chargeur OpenXR.  Le chargeur Découvre le runtime OpenXR actif sur l’appareil et donne accès aux fonctions de base et aux fonctions d’extension qu’il implémente.

vous pouvez [référencer le package NuGet officiel OpenXR](#reference-official-openxr-nuget-package) à partir de votre projet Visual Studio ou [inclure la source OpenXR loader officielle](#include-official-openxr-loader-source) à partir du Khronos GitHub référentiel.  Les deux approches vous permettront d’accéder aux fonctionnalités principales de OpenXR 1,0, `KHR` ainsi `EXT` qu’aux extensions publiées et `MSFT` .

si vous êtes intéressé par l’expérimentation des `MSFT_preview` extensions, vous pouvez [copier les en-têtes OpenXR en version préliminaire](#using-preview-extensions) à partir de la réalité mixte GitHub référentiel.

### <a name="reference-official-openxr-nuget-package"></a>référencer le package NuGet officiel OpenXR

le <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">package **OpenXR. loader** NuGet</a> est le moyen le plus simple de référencer un chargeur OpenXR prédéfini .DLL dans votre solution Visual Studio C++.  Cela vous permet d’accéder aux fonctionnalités principales de OpenXR 1,0, ainsi `KHR` `EXT` qu’aux `MSFT` Extensions publiées et.

pour ajouter un OpenXR. loader NuGet référence du package à votre solution Visual Studio C++ :
1. dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet qui utilisera OpenXR et sélectionnez **gérer NuGet Packages.**...
2. Basculez vers l’onglet **Parcourir** et recherchez **OpenXR. Loader**.
3. Sélectionnez le package **OpenXR. Loader** et sélectionnez installer dans le volet des détails à droite.
4. Sélectionnez OK pour accepter les modifications apportées à votre projet.
5. Ajoutez `#include <openxr/openxr.h>` à un fichier source pour commencer à utiliser l’API OpenXR.

Pour voir un exemple de l’API OpenXR en action, consultez l’exemple d’application <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> .

### <a name="include-official-openxr-loader-source"></a>Inclure la source de chargeur OpenXR officielle

Si vous souhaitez créer vous-même le chargeur, par exemple pour éviter que le chargeur supplémentaire .DLL, vous pouvez extraire les sources de chargeur OpenXR Khronos officielles dans votre projet.  Cela vous permet d’accéder aux fonctionnalités principales de OpenXR 1,0, ainsi `KHR` `EXT` qu’aux `MSFT` Extensions publiées et.

Pour commencer, suivez les instructions de <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">Khronos OpenXR-SDK référentiel sur GitHub</a>.  le projet est configuré pour être généré avec CMake : si vous utilisez MSBuild, vous devez copier le code dans votre propre projet.

## <a name="using-preview-extensions"></a>Utilisation des extensions d’aperçu

Les `MSFT_preview` Extensions répertoriées dans la feuille de [route d’extension](openxr.md#roadmap) sont des extensions de fournisseur expérimentales prévisualisées pour recueillir des commentaires.  Ces extensions sont destinées aux appareils de développement uniquement et seront supprimées lors de la livraison de l’extension réelle.

Si vous souhaitez essayer les extensions disponibles, effectuez `MSFT_preview` les étapes suivantes pour mettre à jour votre projet :
1. Suivez l’une des approches ci-dessus pour intégrer un chargeur OpenXR à votre projet.
2. Remplacez les en-têtes OpenXR standard de votre projet par les <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">en-têtes d’aperçu de la OpenXR de la réalité mixte référentiel sur GitHub</a>.

pour activer la prise en charge de l’extension preview sur votre HoloLens 2 cible ou votre ordinateur de bureau :
  1. Pour vous assurer que vous disposez de la dernière version du runtime OpenXR avec toutes les [Extensions](openxr.md#roadmap) présentes, lancez l’application du Windows **Store** à partir de l’appareil ou de l’émulateur cible, ouvrez le menu en haut à droite, sélectionnez **téléchargements et mises à jour** , puis choisissez **récupérer les mises à jour**.
  2. installez le <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">Outils de développement OpenXR pour Windows Mixed Reality application</a> à partir du Microsoft Store sur le périphérique cible, puis exécutez-le.
  3. accédez à l’onglet **Paramètres du développeur** et activez utiliser la **dernière version préliminaire du runtime OpenXR**.  Cela active le runtime Preview sur votre appareil, pour lequel les extensions d’aperçu sont activées.
     ![OpenXR Outils de développement pour Windows Mixed Reality onglet Paramètres de développement d’applications](images/mixed-reality-openxr-developer-tools-settings.png)
  4. confirmez la **version du Runtime** affichée sous l’onglet état du **système** de la [Outils de développement OpenXR pour Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) correspond à la version requise des extensions préliminaires que vous envisagez d’essayer.  Dans ce cas, l’extension doit apparaître dans la liste **Extensions** .  Une fois qu’une extension stable est disponible, son extension d’aperçu est supprimée.<br />
     ![OpenXR Outils de développement pour Windows Mixed Reality onglet état du système de l’application](images/mixed-reality-openxr-developer-tools-status.png)

Pour obtenir de la documentation sur ces extensions préliminaires et des exemples d’utilisation, consultez le <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">référentiel OpenXR de la réalité mixte</a> .

## <a name="troubleshooting"></a>Dépannage

Si vous ne parvenez pas à vous lancer avec le développement OpenXR, consultez nos [conseils de dépannage](openxr-troubleshooting.md).