---
title: Bien démarrer avec OpenXR
description: Prise en main de l’API OpenXR portable standard sur Windows Mixed Reality et les casques HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality, OpenXR Outils de développement, DirectX, native, application native, moteur personnalisé, intergiciel, prise en main, 101, extensions préliminaires, version du runtime OpenXR, état du système
ms.openlocfilehash: 918dfb1f336598548735b1699c61d1b350fed293
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613193"
---
# <a name="getting-started-with-openxr"></a>Bien démarrer avec OpenXR

Vous pouvez développer avec OpenXR sur HoloLens 2 ou un casque immersif Windows Mixed Reality sur le bureau.  Si vous n’avez pas accès à un casque, vous pouvez utiliser l’émulateur HoloLens 2 ou Windows Mixed Reality Simulator à la place.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Prise en main de OpenXR pour HoloLens 2

Pour commencer à développer des applications OpenXR pour HoloLens 2 :

1. Configurez un HoloLens 2 ou suivez les instructions pour [installer une version récente de l’émulateur hololens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md). Vous devez déjà disposer de OpenXR 1,0 prêt à l’emploi si vous utilisez une image d’émulateur récente ou si l’appareil a mis à jour son système d’exploitation.
2. Assurez-vous que vous disposez de la dernière version du runtime OpenXR avec toutes les [Extensions](openxr.md#roadmap) présentes en lançant l’application du Windows **Store** à partir de l’appareil ou de l’émulateur.
    * Ouvrez le menu en haut à droite, sélectionnez **téléchargements et mises à jour**, puis choisissez **récupérer les mises à jour**.  

> [!NOTE]
> Si vous utilisez l’émulateur, l’image de l’émulateur est réinitialisée à chaque fois que vous la démarrez. par conséquent, il est préférable de s’assurer que vous disposez [de la dernière version de l’image de l’émulateur HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Prise en main de OpenXR pour les casques Windows Mixed Reality

Pour commencer à développer des applications OpenXR pour des casques Windows mixtes immersifs :

1. Assurez-vous que vous exécutez au moins la mise à jour Windows 10 2019 (1903), qui est la configuration minimale requise pour que les utilisateurs finaux Windows Mixed realisation exécutent des applications OpenXR.  Si vous utilisez une version antérieure de Windows 10, vous pouvez procéder à une mise à niveau à l’aide de l' <a href="https://www.microsoft.com/software-download/windows10" target="_blank">Assistant Mise à jour de Windows 10</a>.
2. Configurez un casque Windows Mixed Reality ou suivez les instructions pour [activer le simulateur Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md).

C’est tout !  Le runtime OpenXR Windows Mixed Reality est installé et activé automatiquement pour tous les utilisateurs de Windows Mixed Reality.  Le Microsoft Store maintient le runtime à jour.

Pour réactiver le runtime OpenXR Windows Mixed Reality, lancez le portail de réalité mixte à partir du menu Démarrer, puis sélectionnez « corriger » en haut de la fenêtre.  Si ce bouton est manquant, le runtime OpenXR est déjà actif.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Obtention de la Outils de développement OpenXR pour Windows Mixed Reality

Pour tester le runtime OpenXR Windows Mixed Reality, vous pouvez installer l' <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">application OpenXR outils de développement pour Windows Mixed Reality</a>.  Cette application fournit une démonstration de diverses fonctionnalités OpenXR, ainsi qu’une page d’État du système avec des informations clés sur le runtime actif et le casque actuel.

Lors de l’utilisation de l’émulateur HoloLens 2, le moyen le plus simple d’installer OpenXR Outils de développement pour Windows Mixed Reality se fait via le [portail de périphériques Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md). Accédez à la page « OpenXR », puis cliquez sur le bouton « installer » sous « fonctionnalités pour les développeurs », qui fonctionne également sur les appareils HoloLens 2 physiques.

![OpenXR Outils de développement pour l’application Windows Mixed Reality](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Création d’un exemple d’application OpenXR

Veillez à [installer les outils](../install-the-tools.md) dont vous aurez besoin pour le développement OpenXR si vous ne l’avez pas déjà fait.

Le projet <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> illustre un exemple OpenXR simple avec des fichiers projet Win32 et UWP 2 dans Visual Studio. Étant donné que la solution contient un projet UWP HoloLens, vous avez besoin de la [charge de travail de développement plateforme Windows universelle](../install-the-tools.md#installation-checklist) installée dans Visual Studio pour l’ouvrir entièrement.

Alors que les fichiers de projet Win32 et UWP sont distincts en raison des différences d’empaquetage et de déploiement, le code de l’application à l’intérieur de chaque projet est presque exactement le même !

Après la génération d’un bureau OpenXR Win32. EXE, vous pouvez l’utiliser avec un casque VR sur toute plateforme Desktop VR qui prend en charge OpenXR, quel que soit le type de casque.

Après avoir créé un package d’application OpenXR UWP, vous pouvez [déployer ce package](../platform-capabilities-and-apis/using-visual-studio.md) sur un appareil hololens 2 ou sur l’émulateur hololens 2.

## <a name="learning-the-openxr-api"></a>Apprentissage de l’API OpenXR

Pour une visite guidée de l’API OpenXR, consultez cette vidéo de 60 minutes de l’exemple <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> dans Visual Studio.  La vidéo montre comment chacun des composants principaux de l’API OpenXR peut être utilisé dans votre propre moteur et illustre également certaines des applications générées sur OpenXR aujourd’hui :

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Intégrer le chargeur OpenXR dans un projet

Pour commencer à utiliser OpenXR dans un projet existant, vous devez inclure le chargeur OpenXR.  Le chargeur Découvre le runtime OpenXR actif sur l’appareil et donne accès aux fonctions de base et aux fonctions d’extension qu’il implémente.

Vous pouvez [référencer le package NuGet officiel OpenXR](#reference-official-openxr-nuget-package) à partir de votre projet Visual Studio ou [inclure la source OpenXR Loader officielle](#include-official-openxr-loader-source) à partir du Khronos GitHub référentiel.  Les deux approches vous permettront d’accéder aux fonctionnalités principales de OpenXR 1,0, `KHR` ainsi `EXT` qu’aux extensions publiées et `MSFT` .

Si vous êtes intéressé par l’expérimentation des `MSFT_preview` Extensions, vous pouvez [copier les en-têtes OpenXR en](#using-preview-extensions) préversion à partir du GitHub référentiel de la réalité mixte.

### <a name="reference-official-openxr-nuget-package"></a>Référencer le package NuGet officiel OpenXR

Le <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">package NuGet **OpenXR. Loader**</a> est le moyen le plus simple de référencer un chargeur OpenXR prédéfini. DLL dans votre solution Visual Studio C++.  Cela vous permet d’accéder aux fonctionnalités principales de OpenXR 1,0, ainsi `KHR` `EXT` qu’aux `MSFT` Extensions publiées et.

Pour ajouter une référence de package NuGet OpenXR. Loader à votre solution Visual Studio C++ :
1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet qui utilisera OpenXR et sélectionnez **gérer les packages NuGet...**.
2. Basculez vers l’onglet **Parcourir** et recherchez **OpenXR. Loader**.
3. Sélectionnez le package **OpenXR. Loader** et sélectionnez installer dans le volet des détails à droite.
4. Sélectionnez OK pour accepter les modifications apportées à votre projet.
5. Ajoutez `#include <openxr/openxr.h>` à un fichier source pour commencer à utiliser l’API OpenXR.

Pour voir un exemple de l’API OpenXR en action, consultez l’exemple d’application <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> .

### <a name="include-official-openxr-loader-source"></a>Inclure la source de chargeur OpenXR officielle

Si vous souhaitez créer vous-même le chargeur, par exemple pour éviter le chargeur supplémentaire. DLL, vous pouvez extraire les sources officielles Khronos OpenXR Loader dans votre projet.  Cela vous permet d’accéder aux fonctionnalités principales de OpenXR 1,0, ainsi `KHR` `EXT` qu’aux `MSFT` Extensions publiées et.

Pour commencer, suivez les instructions de la <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">Khronos OpenXR-SDK référentiel sur GitHub</a>.  Le projet est configuré pour être généré avec CMake : Si vous utilisez MSBuild, vous devez copier le code dans votre propre projet.

## <a name="using-preview-extensions"></a>Utilisation des extensions d’aperçu

Les `MSFT_preview` Extensions répertoriées dans la feuille de [route d’extension](openxr.md#roadmap) sont des extensions de fournisseur expérimentales prévisualisées pour recueillir des commentaires.  Ces extensions sont destinées aux appareils de développement uniquement et seront supprimées lors de la livraison de l’extension réelle.

Si vous souhaitez essayer les extensions disponibles, effectuez `MSFT_preview` les étapes suivantes pour mettre à jour votre projet :
1. Suivez l’une des approches ci-dessus pour intégrer un chargeur OpenXR à votre projet.
2. Remplacez les en-têtes OpenXR standard de votre projet par les <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">en-têtes d’aperçu de la OpenXR de la réalité mixte référentiel sur GitHub</a>.

Pour activer la prise en charge de l’extension de préversion sur votre ordinateur de bureau ou HoloLens 2 cible :
  1. Pour vous assurer que vous disposez de la dernière version du runtime OpenXR avec toutes les [Extensions](openxr.md#roadmap) présentes, lancez l’application du Windows **Store** à partir de l’appareil ou de l’émulateur cible, ouvrez le menu en haut à droite, sélectionnez **téléchargements et mises à jour** , puis choisissez **récupérer les mises à jour**.
  2. Installez l' <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">application OpenXR outils de développement pour Windows Mixed Reality</a> à partir du Microsoft Store sur le périphérique cible et exécutez-le.
  3. Accédez à l’onglet **paramètres du développeur** et activez utiliser la **dernière version d’évaluation OpenXR Runtime**.  Cela active le runtime Preview sur votre appareil, pour lequel les extensions d’aperçu sont activées.
     ![OpenXR Outils de développement de l’onglet Paramètres du développeur de l’application Windows Mixed Reality](images/mixed-reality-openxr-developer-tools-settings.png)
  4. Confirmez la **version du runtime** affichée sous l’onglet État du **système** de la [outils de développement OpenXR pour Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) correspond à la version requise des extensions préliminaires que vous envisagez d’essayer.  Dans ce cas, l’extension doit apparaître dans la liste **Extensions** .  Une fois qu’une extension stable est disponible, son extension d’aperçu est supprimée.<br />
     ![OpenXR Outils de développement de l’onglet État du système de l’application Windows Mixed Reality](images/mixed-reality-openxr-developer-tools-status.png)

Pour obtenir de la documentation sur ces extensions préliminaires et des exemples d’utilisation, consultez le <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">référentiel OpenXR de la réalité mixte</a> .

## <a name="troubleshooting"></a>Dépannage

Si vous ne parvenez pas à vous lancer avec le développement OpenXR, consultez nos [conseils de dépannage](openxr-troubleshooting.md).