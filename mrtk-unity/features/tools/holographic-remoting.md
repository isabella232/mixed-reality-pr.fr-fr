---
title: Communication à distance holographique
description: Documentation sur la communication à distance holographique MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 637f68e5ad5f360aea4b5c0603a682d61d152a89
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144586"
---
# <a name="holographic-remoting"></a>Communication à distance holographique

La communication à distance holographique diffuse du contenu holographique depuis un PC vers votre Microsoft HoloLens en temps réel, à l’aide d’un Wi-Fi ou d’une connexion par câble USB. Cette fonctionnalité peut augmenter considérablement la productivité des développeurs lors du développement d’applications de réalité mixte.

Le kit de développement logiciel (SDK) XR, comme indiqué ci-dessous, fait référence au [nouveau pipeline XR unity 2019,3 et au-delà](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). Pour plus d’informations sur l’utilisation du kit de développement logiciel (SDK) XR avec MRTK, consultez [cette page](../../configuration/getting-started-with-mrtk-and-xrsdk.md) . Le XR hérité fait référence au pipeline XR existant qui est inclus dans Unity 2018, déconseillé dans Unity 2019,3 et supprimé dans Unity 2020.

## <a name="initial-setup"></a>Configuration initiale

Pour activer la communication à distance à un HoloLens, il est important de s’assurer que le projet utilise les derniers composants de communication à distance.

1. Ouvrir la **fenêtre > le gestionnaire de package**
    - Si vous utilisez des XR hérités : Vérifiez que la dernière version du package **Windows Mixed Reality** est installée.
    - Si vous utilisez le kit de développement logiciel (SDK) XR : Vérifiez que la dernière version du package de **plug-in XR Windows** est installée.
1. Vérifiez que la dernière application de communication à distance holographique est installée, sur le HoloLens, via le Microsoft Store.

Reportez-vous aux [instructions de configuration de XR héritées](#legacy-xr-setup-instructions) ou aux [instructions d’installation du kit de développement logiciel (SDK) XR](#xr-sdk-setup-instructions) en fonction du pipeline utilisé dans le projet.

## <a name="legacy-xr-setup-instructions"></a>Instructions d’installation de XR héritées

Les instructions ci-dessous s’appliquent uniquement à la communication à distance avec HoloLens 2. Si vous effectuez uniquement la communication à distance avec HoloLens (1re génération), passez à [la connexion à hololens avec Wi-Fi](#connecting-to-the-hololens-with-wi-fi).

Lors de l’utilisation d’un HoloLens 2, la prise en charge de la main et des données de suivi oculaire à distance a été ajoutée à MRTK. Pour activer ces fonctionnalités, suivez les étapes décrites dans [importer des DotNetWinRT dans le projet](#import-dotnetwinrt-into-the-project).

Une fois l’importation effectuée, l’étape suivante consiste à sélectionner la configuration de la vérification de la  >    >  **réalité mixte Windows Mixed Reality** Toolkit  >  . Cette étape ajoute une définition de script qui active la dépendance DotNetWinRT.

> [!NOTE]
> Si vous utilisez Unity 2019,4 et versions ultérieures, il n’est pas nécessaire d’exécuter l’utilitaire de vérification de la configuration.

Pour activer le suivi des articulations et du suivi oculaire, suivez les étapes décrites dans le **débogage de l’accès distant HoloLens 2 via l’importation de package Unity** et les sections associées.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Débogage de l’accès distant HoloLens 2 via l’importation de package Unity

Si les jonctions de la main et le suivi oculaire de HoloLens 2 ne fonctionnent pas sur la communication à distance, il existe quelques points courants de problèmes potentiels. Ils sont listés ci-dessous dans l’ordre dans lequel ils doivent être vérifiés.

Ces problèmes sont particulièrement pertinents lors de l’exécution sur **unity 2019,3** ou une version ultérieure.

#### <a name="import-dotnetwinrt-into-the-project"></a>Importer DotNetWinRT dans le projet

1. Télécharger l' [outil de la fonctionnalité de réalité mixte](https://aka.ms/MRFeatureTool)

1. Dans la vue **découvrir les fonctionnalités** , sélectionnez *projections WinRT de réalité mixte*

    ![Sélectionner le package DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. Cliquez sur **recevoir des fonctionnalités** et continuer à [importer le package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT définir les paramètres écrits dans le lecteur

> [!NOTE]
> Si vous utilisez Unity 2019,4 et versions ultérieures, la DOTNETWINRT_PRESENT définir est contenue dans les fichiers. asmdef appropriés et non dans les paramètres du lecteur Unity. L’étape de configuration de la vérification n’est pas obligatoire.

À partir de MRTK version 2.5.0, pour des raisons de performances, cette #define n’est plus définie automatiquement. Pour activer cet indicateur, utilisez l'   >    >    >  élément de menu **Vérifier la configuration** de la vérification de la réalité mixte de la réalité des outils de la réalité mixte.

> [!Note]
> L’élément vérifier la configuration n’affiche pas de confirmation. Pour confirmer que la définition a été définie, accédez aux paramètres du lecteur Unity. À partir de là, sous l’onglet UWP, activez la case à cocher autres paramètres pour les symboles de définition de script. Assurez-vous que DOTNETWINRT_PRESENT est correctement écrit dans cette liste. Si c’est le cas, cette étape a réussi.

![DotNetWinRT présente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>Suppression de la prise en charge de l’accès distant spécifique à HoloLens 2

Si vous rencontrez des conflits ou d’autres problèmes en raison de la présence de l’adaptateur DotNetWinRT, veuillez [contacter l’une de nos ressources d’aide](../../index.md#getting-help).

## <a name="xr-sdk-setup-instructions"></a>Instructions d’installation du kit SDK XR

Suivez les [instructions d’installation de Windows Mixed Reality sur la page prise en main de MRTK et du kit de développement logiciel (SDK) XR](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) et assurez-vous d’effectuer l’étape requise pour la communication à distance HoloLens dans l’éditeur.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Connexion au HoloLens avec Wi-Fi

Une fois que le projet a été configuré, une connexion peut être établie avec HoloLens.

1. Dans **fichier > paramètres de build**, assurez-vous que le type de génération du projet est défini sur **plateforme Windows universelle**
1. Sur HoloLens, lancez l’application de **communication à distance holographique** .
1. Dans Unity, sélectionnez **windows > XR > émulation holographique (si vous utilisez un plug-in XR)/Windows XR Remoting (si vous utilisez le kit de développement logiciel (SDK) XR)**.

    ![Démarrer l’émulation holographique](../images/tools/remoting/StartHolographicEmulation.png)

1. Définissez le **mode d’émulation** à **distant sur appareil**.

    ![Définir le mode d’émulation](../images/tools/remoting/SelectEmulationMode.png)

1. (**_S’applique uniquement aux XR hérités_**) Sélectionnez la **version** de l’appareil.

    ![Sélectionner la version de l’appareil](../images/tools/remoting/SelectDeviceVersion.png)

1. À l’aide de l’adresse IP affichée par l’application de lecteur de communication à distance holographique, définissez le champ **ordinateur distant** .

    ![Entrer l’adresse IP](../images/tools/remoting/EnterIPAddress.png)

1. Cliquez sur **Connecter**.

> [!NOTE]
> Si vous ne pouvez pas vous connecter, assurez-vous que votre HoloLens 2 n’est pas branché sur votre ordinateur et redémarrez Unity.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>Connexion au HoloLens à l’aide d’un câble USB

La connexion par câble USB offre une meilleure qualité de rendu et une meilleure stabilité. Pour utiliser la connexion par câble USB, déconnectez-vous du HoloLens de Wi-Fi dans les paramètres de HoloLens et lancez l’application de lecteur de communication à distance holographique. Elle affiche une adresse IP commençant par 169. Utilisez cette adresse IP dans le paramètre d’émulation holographique d’Unity pour vous connecter. Une fois que l’adresse IP pour le câble USB a été identifiée, il est possible de connecter à nouveau le HoloLens à Wi-Fi.

## <a name="starting-a-remoting-session"></a>Démarrage d’une session de communication à distance

Avec Unity connectée à HoloLens, entrez en mode lecture dans l’éditeur.

Une fois la session terminée, quittez le mode lecture.

> [!NOTE]
> Il existe un problème connu avec certaines versions de Unity dans laquelle l’éditeur peut se bloquer lors de l’entrée en mode lecture pendant une session de communication à distance. Ce problème peut se manifester si la fenêtre holographique est ouverte lorsque le projet est chargé. Pour vous assurer que ce problème ne se produit pas, fermez toujours la boîte de dialogue holographique avant de quitter Unity.

## <a name="see-also"></a>Voir aussi

- [Résolution des problèmes et limitations de la communication à distance holographique](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Termes du contrat de licence logiciel Microsoft holographique Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)