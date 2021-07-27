---
ms.openlocfilehash: 7cd9400ddb83b95f145a9b962be51aaed30df47b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224466"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Dans le menu Unity, sélectionnez Gestionnaire de package **Windows** >  pour ouvrir la fenêtre **Gestionnaire de package**, puis vérifiez que la version 4.1.7 d’**AR Foundation** >  est installée **.**

![Package Manager d’Unity avec AR Foundation sélectionné](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

> [!NOTE]
> Vous installez le package intégré AR Foundation, car il est nécessaire pour le SDK Azure Spatial Anchors que vous allez importer dans la section suivante.

## <a name="importing-the-tutorial-assets"></a>Importation des ressources du tutoriel

Ajoutez le SDK AzurespatialAnchors V2.10 à votre projet. Pour ajouter les packages, suivez ce [tutoriel](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

Téléchargez et **importez** les packages personnalisés Unity suivants **dans l’ordre où ils sont listés** :

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](../images/mr-learning-azure/tutorial1-section4-step1-1-OpenXR.png)

> [!TIP]
> Pour vous rappeler comment importer un package personnalisé Unity, reportez-vous aux instructions fournies dans  [Importation du Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) .

# <a name="unity-2020--windows-xr-plugin"></a>[Unity 2020 + Plug-in Windows XR](#tab/winxr)

Dans le menu Unity, sélectionnez **Windows** > **Package Manager** pour ouvrir la fenêtre Package Manager, sélectionnez une version d’**AR Foundation ultérieure à la version 4.0.12**, puis cliquez sur le bouton **Install** pour installer le package :

![Package Manager d’Unity avec AR Foundation sélectionné](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

> [!NOTE]
> Vous installez le package intégré AR Foundation, car il est nécessaire pour le SDK Azure Spatial Anchors que vous allez importer dans la section suivante.

## <a name="importing-the-tutorial-assets"></a>Importation des ressources du tutoriel

Ajoutez le SDK AzurespatialAnchors V2.10 à votre projet. Pour ajouter les packages, suivez ce [tutoriel](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

Téléchargez et **importez** les packages personnalisés Unity suivants **dans l’ordre où ils sont listés** :

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](../images/mr-learning-azure/tutorial1-section4-step1-1-XRSDK.png)

> [!TIP]
> Pour vous rappeler comment importer un package personnalisé Unity, reportez-vous aux instructions fournies dans  [Importation du Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) .

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

Dans le menu Unity, sélectionnez **Windows** > **Package Manager** pour ouvrir la fenêtre Package Manager, sélectionnez une version d’**AR Foundation ultérieure à la version 3.1.3**, puis cliquez sur le bouton **Install** pour installer le package :

![Package Manager d’Unity avec AR Foundation sélectionné](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

> [!NOTE]
> Vous installez le package intégré AR Foundation, car il est nécessaire pour le SDK Azure Spatial Anchors que vous allez importer dans la section suivante.

## <a name="importing-the-tutorial-assets"></a>Importation des ressources du tutoriel

Ajoutez le SDK AzurespatialAnchors V2.7.2 à votre projet. Pour ajouter les packages, suivez ce [tutoriel](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

Téléchargez et **importez** les packages personnalisés Unity suivants **dans l’ordre où ils sont listés** :

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage)

Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](../images/mr-learning-azure/tutorial1-section4-step1-1-Legacy.png)

> [!NOTE]
> Si vous voyez des avertissements CS0618 signalant que « WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) » et « WorldAnchor.GetNativeSpatialAnchorPtr() » sont obsolètes, vous pouvez les ignorer.

> [!TIP]
> Pour vous rappeler comment importer un package personnalisé Unity, reportez-vous aux instructions fournies dans  [Importation du Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) .
