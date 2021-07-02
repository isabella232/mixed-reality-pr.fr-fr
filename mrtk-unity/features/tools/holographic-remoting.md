---
title: Communication à distance holographique
description: Documentation sur la communication à distance holographique MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 0fbde863185a9f51b53192a338e9403dc79248db
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176640"
---
# <a name="holographic-remoting"></a>Communication à distance holographique

la communication à distance holographique diffuse du contenu holographique depuis un PC vers votre Microsoft HoloLens en temps réel, à l’aide d’une connexion Wi-Fi ou d’un câble USB. Cette fonctionnalité peut augmenter considérablement la productivité des développeurs lors du développement d’applications de réalité mixte.

Le kit de développement logiciel (SDK) XR, comme indiqué ci-dessous, fait référence au [nouveau pipeline XR unity 2019,3 et au-delà](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). Pour plus d’informations sur l’utilisation du kit de développement logiciel (SDK) XR avec MRTK, consultez [cette page](../../configuration/getting-started-with-mrtk-and-xrsdk.md) . Le XR hérité fait référence au pipeline XR existant qui est inclus dans Unity 2018, déconseillé dans Unity 2019,3 et supprimé dans Unity 2020.

## <a name="initial-setup"></a>Configuration initiale

pour activer la communication à distance à un HoloLens, il est important de s’assurer que le projet utilise les derniers composants de communication à distance.

1. ouvrez la **fenêtre > Gestionnaire de package**
    - si vous utilisez des XR hérités : vérifiez que la dernière version du package de **Windows Mixed Reality** est installée.
    - si vous utilisez le kit de développement logiciel (SDK) XR : vérifiez que la dernière version du package de **plug-in Windows XR** est installée.
1. vérifiez que la dernière application de communication à distance holographique est installée, sur le HoloLens, via le Microsoft Store.

Reportez-vous aux [instructions de configuration de XR héritées](#legacy-xr-setup-instructions) ou aux [instructions d’installation du kit de développement logiciel (SDK) XR](#xr-sdk-setup-instructions) en fonction du pipeline utilisé dans le projet.

## <a name="legacy-xr-setup-instructions"></a>Instructions d’installation de XR héritées

Les instructions ci-dessous s’appliquent uniquement à la communication à distance avec HoloLens 2. si vous effectuez uniquement la communication à distance avec HoloLens (1re génération), passez à [la connexion au HoloLens avec Wi-Fi](#connecting-to-the-hololens-with-wi-fi).

lors de l’utilisation d’un HoloLens 2, la prise en charge de la main et des données de suivi oculaire à distance a été ajoutée à MRTK. Pour activer ces fonctionnalités, suivez les étapes décrites dans [importer des DotNetWinRT dans le projet](#import-dotnetwinrt-into-the-project).

une fois importé, l’étape suivante consiste à sélectionner la **réalité mixte**  >  **Shared Computer Toolkit**  >  **utilitaires**  >  **Windows Mixed Reality**  >  **vérifier la Configuration**. Cette étape ajoute une définition de script qui active la dépendance DotNetWinRT.

> [!NOTE]
> Si vous utilisez Unity 2019,4 et versions ultérieures, il n’est pas nécessaire d’exécuter l’utilitaire de vérification de la configuration.

pour activer le suivi des jointures manuelles et du suivi oculaire, suivez les étapes décrites dans le **débogage HoloLens 2 la communication à distance via l’importation de packages unity** et les sections associées.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>débogage HoloLens 2 la communication à distance via l’importation de package unity

si HoloLens 2 jointures manuelles et le suivi oculaire ne fonctionnent pas sur la communication à distance, il existe quelques points courants de problèmes potentiels. Ils sont listés ci-dessous dans l’ordre dans lequel ils doivent être vérifiés.

Ces problèmes sont particulièrement pertinents lors de l’exécution sur **unity 2019,3** ou une version ultérieure.

#### <a name="import-dotnetwinrt-into-the-project"></a>Importer DotNetWinRT dans le projet

1. Télécharger l' [outil de la fonctionnalité de réalité mixte](https://aka.ms/MRFeatureTool)

1. Dans la vue **découvrir les fonctionnalités** , sélectionnez *projections WinRT de réalité mixte*

    ![Sélectionner le package DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. Cliquez sur **recevoir des fonctionnalités** et continuer à [importer le package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT définir les paramètres écrits dans le lecteur

> [!NOTE]
> si vous utilisez unity 2019,4 et versions ultérieures, la DOTNETWINRT_PRESENT définir est contenue dans les fichiers. asmdef appropriés et non dans le Paramètres de lecteur unity. L’étape de configuration de la vérification n’est pas obligatoire.

À partir de MRTK version 2.5.0, pour des raisons de performances, cette #define n’est plus définie automatiquement. pour activer cet indicateur, utilisez l’élément de menu vérifier la **réalité mixte Shared Computer Toolkit**  >  **utilitaires**  >  **Windows Mixed Reality**  >  **vérifier la Configuration** .

> [!Note]
> L’élément vérifier la configuration n’affiche pas de confirmation. pour confirmer que la définition a été définie, accédez au Paramètres du lecteur unity. à partir de là, sous l’onglet UWP, cochez autres Paramètres pour les symboles de définition de script. Assurez-vous que DOTNETWINRT_PRESENT est correctement écrit dans cette liste. Si c’est le cas, cette étape a réussi.

![DotNetWinRT présente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>suppression de la prise en charge de la communication à distance spécifique à HoloLens 2

Si vous rencontrez des conflits ou d’autres problèmes en raison de la présence de l’adaptateur DotNetWinRT, veuillez [contacter l’une de nos ressources d’aide](../../index.md#getting-help).

## <a name="xr-sdk-setup-instructions"></a>Instructions d’installation du kit SDK XR

suivez les [instructions d’installation de Windows Mixed Reality sur la page prise en main du kit de développement logiciel (SDK) MRTK et XR](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) et assurez-vous d’effectuer l’étape requise dans le cadre de l’éditeur HoloLens la communication à distance.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>connexion au HoloLens avec Wi-Fi

Une fois que le projet a été configuré, une connexion peut être établie avec l’HoloLens.

1. dans **fichier > build Paramètres**, vérifiez que le type de génération du projet est défini sur **plateforme Windows universelle**
1. sur la HoloLens, lancez l’application de **communication à distance holographique** .
1. dans unity, sélectionnez **windows > XR > émulation holographique (si vous utilisez le kit de développement logiciel (SDK) XR hérité XR)/Windows la communication à distance du plug-in (si vous utilisez XR SDK)**.

    ![Démarrer l’émulation holographique](../images/tools/remoting/StartHolographicEmulation.png)

1. Définissez le **mode d’émulation** à **distant sur appareil**.

    ![Définir le mode d’émulation](../images/tools/remoting/SelectEmulationMode.png)

1. (**_S’applique uniquement aux XR hérités_**) Sélectionnez la **version** de l’appareil.

    ![Sélectionner la version de l’appareil](../images/tools/remoting/SelectDeviceVersion.png)

1. À l’aide de l’adresse IP affichée par l’application de lecteur de communication à distance holographique, définissez le champ **ordinateur distant** .

    ![Entrer l’adresse IP](../images/tools/remoting/EnterIPAddress.png)

1. Cliquez sur **Se connecter**.

> [!NOTE]
> si vous ne pouvez pas vous connecter, assurez-vous que votre HoloLens 2 n’est pas branché sur votre ordinateur et redémarrez unity.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>connexion au HoloLens à l’aide d’un câble USB

La connexion par câble USB offre une meilleure qualité de rendu et une meilleure stabilité. pour utiliser la connexion par câble USB, déconnectez-vous du HoloLens de Wi-Fi dans le Paramètres de HoloLens et lancez l’application de lecteur de communication à distance holographique. Elle affiche une adresse IP commençant par 169. Utilisez cette adresse IP dans le paramètre d’émulation holographique d’Unity pour vous connecter. une fois que l’adresse IP pour le câble USB a été identifiée, il est possible de connecter à nouveau le HoloLens à Wi-Fi.

## <a name="starting-a-remoting-session"></a>Démarrage d’une session de communication à distance

avec unity connectée au HoloLens, entrez en mode lecture dans l’éditeur.

Une fois la session terminée, quittez le mode lecture.

> [!NOTE]
> Il existe un problème connu avec certaines versions de Unity dans laquelle l’éditeur peut se bloquer lors de l’entrée en mode lecture pendant une session de communication à distance. Ce problème peut se manifester si la fenêtre holographique est ouverte lorsque le projet est chargé. Pour vous assurer que ce problème ne se produit pas, fermez toujours la boîte de dialogue holographique avant de quitter Unity.

## <a name="see-also"></a>Voir aussi

- [Résolution des problèmes et limitations de la communication à distance holographique](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Termes du contrat de licence logiciel Microsoft holographique Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
