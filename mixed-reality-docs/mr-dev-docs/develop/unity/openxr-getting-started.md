---
title: Utilisation du plug-in OpenXR de la réalité mixte pour Unity
description: Découvrez comment activer le plug-in OpenXR de réalité mixte pour les projets Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, réalité mixte, MRTK, boîte à outils de réalité mixte, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main
ms.openlocfilehash: a4606eeb1fa6c8dc0858653a196c1e536ae473d4
ms.sourcegitcommit: e2228b9585302eeff1d853ddb54be8421a21c954
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102189121"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Utilisation du plug-in OpenXR de la réalité mixte pour Unity

À partir de Unity version 2020,2, le package de plug-in OpenXR de réalité mixte de Microsoft est disponible à l’aide du gestionnaire de package Unity (UPM).

## <a name="prerequisites"></a>Prérequis

* Unity 2020,2 ou version ultérieure
* Plug-in Unity OpenXR 0.1.3 ou version ultérieure
* Visual Studio 2019 ou version ultérieure
* Installer la prise en charge de plateforme **UWP** dans Unity pour les applications HoloLens 2

> [!NOTE]
> Si vous générez des applications VR sur un PC Windows, le plug-in OpenXR de réalité mixte n’est pas obligatoire. Toutefois, vous souhaiterez installer le plug-in si vous personnalisez le mappage de contrôleur pour les contrôleurs de reréverbérations de HP ou si vous créez des applications qui fonctionnent à la fois sur les casques HoloLens 2 et VR.

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a>Installation de OpenXR avec l’outil de la fonctionnalité de réalité mixte

Installez le plug-in OpenXR avec la nouvelle application outil de la fonctionnalité de réalité mixte. Suivez les [instructions d’installation et d’utilisation](welcome-to-mr-feature-tool.md) , puis sélectionnez le package de **plug-in OpenXR de la réalité mixte** dans la catégorie de la réalité mixte Toolkit :

![Fenêtre packages de l’outil de réalité mixte avec plug-in Open XR mis en surbrillance](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>Configuration de la gestion des plug-ins XR pour OpenXR

Pour définir OpenXR comme Runtime dans Unity :

1. Dans l’éditeur Unity, accédez à **modifier > paramètres du projet**
2. Dans la liste des paramètres, sélectionnez **gestion des plug-ins XR**
3. Cochez les cases **Initialize XR on Startup** et **OpenXR (Preview)**
4. Si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez **ensemble de fonctionnalités Microsoft HoloLens** .

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](images/openxr-img-05.png)

> [!IMPORTANT]
> Si une icône d’avertissement rouge s’affiche en regard du **plug-in OpenXR (version préliminaire)**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer. L’éditeur Unity peut avoir besoin de redémarrer lui-même pour que les modifications prennent effet.

![Capture d’écran de la fenêtre de validation du projet OpenXR](images/openxr-img-06.png)

Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !  Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.

## <a name="optimization"></a>Optimization

Si vous développez pour HoloLens 2, accédez à la **réalité mixte> OpenXR > appliquer les paramètres de projet recommandés pour HoloLens 2** afin d’obtenir de meilleures performances d’application.

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>Essayer les scènes de l’exemple Unity

Pour utiliser un ou plusieurs des exemples, installez [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) à partir du **Gestionnaire de package**:

![Capture d’écran du gestionnaire de package Unity ouverte dans l’éditeur Unity avec AR Foundation en surbrillance](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>Exemples HoloLens 2

1. Dans l’éditeur Unity, accédez à **fenêtre > gestionnaire de package**
2. Dans la liste des packages, sélectionnez le **plug-in OpenXR de réalité mixte**
3. Recherchez l’exemple dans la liste d' **exemples** et sélectionnez **Importer**

![Capture d’écran du gestionnaire de package Unity ouverte dans l’éditeur Unity avec le plug-in OpenXR de réalité mixte sélectionné et le bouton d’importation en surbrillance](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Lorsqu’un package est mis à jour, Unity offre la possibilité de mettre à jour les exemples importés.  La mise à jour d’un échantillon importé remplace toutes les modifications apportées à l’exemple et aux ressources associées.

## <a name="using-mrtk-with-openxr-support"></a>Utilisation de MRTK avec prise en charge de OpenXR

MRTK-Unity prend en charge le plug-in OpenXR de réalité mixte à partir de la version 2.5.3.

1. Ouvrez de nouveau l' [outil Mixed Reality Feature](welcome-to-mr-feature-tool.md) pour installer la boîte à outils de la réalité mixte, si ce n’est déjà fait. La prise en charge de OpenXR est dans le package de **base** .
2. Accédez au script du composant MixedReality Toolkit dans l’inspecteur et basculez vers le profil **DefaultOpenXRConfigurationProfile** :

    ![Capture d’écran de basculement de la configuration MRTK dans le composant de la réalité mixte du composant dans l’inspecteur](images/openxr-img-11.png)

    1. Pour [plus d’informations sur la migration vers OpenXR](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline), consultez la documentation MRTK.

> [!NOTE]
> Lorsque vous effectuez une mise à niveau à partir d’une version antérieure de MRTK, vérifiez que la ligne suivante se trouve dans le fichier **Assets/MixedRealityToolkit. generated/link.xml** :
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Cette ligne sera ajoutée par défaut si vous avez démarré avec MRTK 2.5.4 ou une version plus récente.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que votre projet est configuré pour OpenXR et que vous avez accès à des exemples, consultez les [fonctionnalités](openxr-supported-features.md) actuellement prises en charge dans notre plug-in OpenXR.

## <a name="have-feedback"></a>Vous avez des commentaires ?

OpenXR est toujours expérimental. nous apprécions donc des commentaires que vous pouvez nous aider à améliorer. Vous les trouverez sur les [Forums Unity](https://aka.ms/unityforums) en marquant votre billet de forum avec **Microsoft**  +  **OpenXR** et **HoloLens 2** ou **Windows Mixed Reality**.

## <a name="see-also"></a>Voir aussi

* [Configuration de votre projet sans MRTK](configure-unity-project.md)
* [Paramètres recommandés pour Unity](recommended-settings-for-unity.md)
* [Recommandations de performances pour Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
