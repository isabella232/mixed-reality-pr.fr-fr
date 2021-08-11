---
ms.openlocfilehash: 695db2d7e6765d3584c9e9a6459071ab537c1f003d13461ce5736481b98b7495
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202751"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Pour commencer à utiliser un **nouveau projet Unity** à l’aide de MRTK, commencez à l’étape 2 dans le didacticiel MRTK :

> [!div class="nextstepaction"]
> [Configurer un nouveau projet OpenXR avec MRTK](../../tutorials/mr-learning-base-02.md?tabs=openxr)

Si vous effectuez la mise à niveau d’un **projet MRTK existant vers OpenXR**, vous devez d’abord mettre à niveau MRTK-Unity vers la dernière version (version 2.7.2 ou ultérieure) pour obtenir des correctifs clés pour la compatibilité avec le plug-in de réalité mixte OpenXR.  Utilisez l' [outil de la fonctionnalité de réalité mixte](../../welcome-to-mr-feature-tool.md) pour effectuer une mise à niveau vers la dernière version de MRTK, puis suivez les [étapes de configuration manuelle de OpenXR ci-dessous](#manual-setup-without-mrtk). Pour [plus d’informations sur la migration d’un projet MRTK existant vers OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline), consultez la documentation MRTK.

> [!NOTE]
> Lorsque vous effectuez une mise à niveau à partir d’une version antérieure de MRTK antérieure à **2.5.3**, vérifiez que la ligne suivante se trouve dans le fichier **Assets/MixedRealityToolkit. generated/link.xml** :
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Cette ligne sera ajoutée par défaut si vous avez démarré avec MRTK 2.5.4 ou une version plus récente.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Pour commencer à utiliser un **nouveau projet Unity** à l’aide de MRTK, commencez à l’étape 2 dans le didacticiel MRTK :

> [!div class="nextstepaction"]
> [configurer un nouveau projet Windows XR avec MRTK](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[XR antérieur](#tab/legacy)

Pour commencer à utiliser un **nouveau projet Unity** à l’aide de MRTK, commencez à l’étape 2 dans le didacticiel MRTK :

> [!div class="nextstepaction"]
> [Configurer un nouveau projet XR hérité avec MRTK](../../tutorials/mr-learning-base-02.md?tabs=wsa)