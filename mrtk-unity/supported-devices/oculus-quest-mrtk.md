---
title: Déploiement sur Oculus Quest
description: Documentation à configurer pour Oculus Quest dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Oculus Quest
ms.openlocfilehash: c5633af09cca5e8b20eb81e897ca8129fed86174e30a97f7242efde231fb7aa1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186658"
---
# <a name="deploying-to-oculus-quest"></a>Déploiement sur Oculus Quest

Une [quête Oculus](https://www.oculus.com/quest/) est requise.

La prise en charge de MRTK pour Oculus Quest est fournie par le biais de deux sources différentes : le pipeline SDK XR de Unity et le package Unity d’intégration Oculus. le **Fournisseur de données XRSDK Oculus** permet l’utilisation des deux sources et doit être utilisé pour déployer MRTK sur Oculus Quest.

Le [pipeline Unity XR SDK](https://docs.unity3d.com/Manual/XR.html) permet d’utiliser les contrôleurs tactiles Oculus et le suivi des têtes avec le Oculus Quest.
Ce pipeline est la norme pour le développement d’applications XR dans Unity 2019,3 et les versions ultérieures. Pour utiliser ce pipeline, assurez-vous que vous utilisez **unity 2019,3 ou une version plus récente**. Cela est **nécessaire** pour déployer des applications MRTK sur Oculus Quest.

Le [package Unity d’intégration Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permet d’utiliser le suivi de la **main** avec Oculus Quest. Ce fournisseur de données n’utilise **pas** le **pipeline du kit de développement logiciel (SDK) XR** d’Unity ou le **pipeline XR hérité**.

## <a name="setting-up-project-for-the-oculus-quest"></a>Configuration de Project pour Oculus Quest

1. Procédez comme [suit](https://developer.oculus.com/documentation/unity/book-unity-gsg/) pour vous assurer que votre projet est prêt pour le déploiement sur Oculus Quest.

1. Assurez-vous que le [mode développeur](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) est activé sur votre appareil. L’installation des pilotes ADB Oculus est facultative.

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a>Configuration du pipeline du kit de développement logiciel (SDK) XR pour Oculus Quest

1. assurez-vous que le **plug-in Oculus XR** est installé sous **Window--> Gestionnaire de package**

    ![Package de plug-in XR Oculus](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. assurez-vous que le fournisseur de plug-ins Oculus est inclus dans votre projet en accédant à **modifier--> Project Paramètres--> gestion du plug-in XR--> fournisseurs de plug** -in

    ![Fournisseur de plug-ins Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Configuration du package Unity d’intégration Oculus pour activer handtracking

1. Téléchargez et importez l' [intégration Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) à partir du magasin d’actifs Unity. La dernière version testée pour fonctionner est 20.0.0. Les versions antérieures sont disponibles dans cette [Archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).

1. accédez à la réalité mixte Shared Computer Toolkit > utilitaires > Oculus > intégrer les Modules unity Oculus integration. Cela a pour effet de mettre à jour le asmdefs avec les définitions et les références nécessaires au bon fonctionnement du code Oculus Quest approprié. Il met également à jour le fichier CSC pour filtrer les avertissements obsolètes produits par les ressources d’intégration Oculus. Le référentiel MRTK contient un fichier CSC qui convertit les avertissements en erreurs, cette conversion interrompt le processus de configuration MRTK-Quest.

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. Dans le dossier Oculus importé (il doit être trouvé dans Assets/Oculus), il existe un objet scriptable appelé OculusProjectConfig. Dans ce fichier de configuration, vous devez définir HandTrackingSupport sur « Controllers and handles ».

    ![Contrôleur d’intégration Oculus et mains](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Configuration de la scène

1. Créez une nouvelle scène Unity ou ouvrez une scène préexistante telle que HandInteractionExamples.
1. ajoutez MRTK à la scène en accédant à la **réalité mixte Shared Computer Toolkit**  >  **ajouter à la scène et configurer**.

## <a name="using-the-oculus-xr-sdk-data-provider"></a>utilisation du kit de développement logiciel (SDK) Oculus XR Fournisseur de données

::: moniker range=">= mrtkunity-2021-05"

1. configurez votre profil pour utiliser le **kit de développement logiciel (SDK) Oculus XR Fournisseur de données**
    - Si vous n’avez pas l’intention de modifier les profils de configuration
        - Utilisez l’un des profils MRTK par défaut, qui sont tous configurés dans les pipelines XR d’Unity. Le DefaultXRSDKConfigurationProfile précédent est maintenant marqué comme obsolète.
        - Accédez à [Build et déployez votre projet sur Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).
    - Sinon, procédez comme suit :
        - Sélectionnez l’objet de jeu MixedRealityToolkit dans la hiérarchie, puis sélectionnez **copier et personnaliser** pour cloner le profil de réalité mixte par défaut.

        ![Cloner le profil](../images/cross-platform/CloneProfile.png)

        - Sélectionnez le profil de configuration **d’entrée** .

        ![Profil de configuration d’entrée](../images/cross-platform/InputConfigurationProfile.png)

        - Sélectionnez **clone** dans le profil de système d’entrée pour permettre la modification.

        ![Cloner le profil du système d’entrée](../images/cross-platform/CloneInputSystemProfile.png)

        - ouvrez la section **fournisseurs de données d’entrée** , sélectionnez **ajouter un Fournisseur de données** en haut, et le nouveau fournisseur de données sera ajouté à la fin de la liste.  ouvrez le nouveau fournisseur de données et définissez le **Type** sur **Microsoft. MixedReality. Shared Computer Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.

        ![Oculus ajouter XRSDK Fournisseur de données](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. configurez votre profil pour utiliser le **kit de développement logiciel (SDK) Oculus XR Fournisseur de données**
    - Si vous n’avez pas l’intention de modifier les profils de configuration
        - Remplacez votre profil par DefaultXRSDKConfigurationProfile.
        - Accédez à [Build et déployez votre projet sur Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).
    - Sinon, procédez comme suit :
        - Sélectionnez l’objet de jeu MixedRealityToolkit dans la hiérarchie, puis sélectionnez **copier et personnaliser** pour cloner le profil de réalité mixte par défaut.

        ![Cloner le profil](../images/cross-platform/CloneProfile.png)

        - Sélectionnez le profil de configuration **d’entrée** .

        ![Profil de configuration d’entrée](../images/cross-platform/InputConfigurationProfile.png)

        - Sélectionnez **clone** dans le profil de système d’entrée pour permettre la modification.

        ![Cloner le profil du système d’entrée](../images/cross-platform/CloneInputSystemProfile.png)

        - ouvrez la section **fournisseurs de données d’entrée** , sélectionnez **ajouter un Fournisseur de données** en haut, et le nouveau fournisseur de données sera ajouté à la fin de la liste.  ouvrez le nouveau fournisseur de données et définissez le **Type** sur **Microsoft. MixedReality. Shared Computer Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.

        ![Oculus ajouter XRSDK Fournisseur de données](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. le kit de développement logiciel (SDK) Oculus XR Fournisseur de données comprend une plate-forme de caméra rfp Prefab qui configure automatiquement le projet avec une plate-forme rfp et des mains rfp pour acheminer correctement les entrées. L’ajout manuel d’une plate-forme RFP à la scène nécessite une configuration manuelle des paramètres et de l’entrée.

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>Créez et déployez votre projet sur Oculus Quest

1. Branchez votre Oculus Quest via un câble USB C 3,0->
1. accédez à **fichier > générer Paramètres**
1. Changer le déploiement en **Android**
1. Vérifiez que la Oculus Quest est sélectionnée en tant qu’unité d’exécution applicable.

    ![Oculus exécuter l’appareil](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. Sélectionner générer et exécuter
    - Vous rencontrerez probablement le jeu d’erreurs de génération suivant lorsque vous sélectionnez *générer et exécuter* la première fois. Vous devez être en mesure de procéder à un déploiement en sélectionnant *générer et exécuter* à nouveau.

    ![Oculus des erreurs de build attendues](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. Accepter l’invite _autoriser le débogage USB_ de l’intérieur de la Quest
1. Consultez votre scène à l’intérieur de Oculus Quest

## <a name="removing-oculus-integration-from-the-project"></a>Suppression de l’intégration de Oculus de l’Project

1. accédez à la réalité mixte Shared Computer Toolkit > Oculus > séparer les Modules unity Oculus ![ Oculus separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. Autorisez l’actualisation Unity en tant que références dans le Microsoft. MixedReality. Shared Computer Toolkit. Providers. Oculus. asmdef et d’autres fichiers sont modifiés dans cette étape
1. Fermer Unity
1. fermer Visual Studio, s’il est ouvert
1. Ouvrez l’Explorateur de fichiers et accédez à la racine du projet MRTK Unity.
1. Supprimer le répertoire UnityProjectName/Library
1. Supprimer le répertoire UnityProjectName/Assets/Oculus
1. Supprimer le fichier UnityProjectName/Assets/Oculus. meta
1. Rouvrir Unity

## <a name="common-errors"></a>Erreurs courantes

### <a name="quest-not-recognized-by-unity"></a>Quest non reconnu par Unity

Assurez-vous que vos chemins Android sont correctement configurés. Si vous continuez à rencontrer des problèmes, suivez ce [Guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**Modifier > préférences > outils externes > Android**

![Configuration des outils Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
