---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603709"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Le plug-in OpenXR de réalité mixte est **recommandé par Microsoft** pour **Unity 2020 LTS** ou version ultérieure. À mesure que de nouvelles fonctionnalités sont développées à l’avenir, elles sont uniquement incluses dans le plug-in OpenXR de la réalité mixte.

Le plug-in OpenXR de réalité mixte prend entièrement en charge les implémentations de 4,0 base de ARPlaneManager et de ARRaycastManager. cela vous permet d’écrire le code raycasting une seule fois qui s’étend sur les téléphones et tablettes HoloLens 2 et ARCore/ARKit.

### <a name="prerequisites"></a>Prérequis 

* [outils les plus récents pour le développement de HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Dernière Unity 2020,3 LTS : version 2020.3.8 F1 ou version ultérieure

### <a name="recommended-package-versions"></a>Versions de package recommandées

les instructions de cette page vous permettent de configurer les packages OpenXR core unity nécessaires au déploiement d’applications HoloLens 2 ou Windows Mixed Reality :

* Plug-in Unity OpenXR : version 1,2 ou ultérieure
* Plug-in OpenXR de réalité mixte : version 1.0.0 ou ultérieure

Si vous utilisez les packages suivants dans votre projet, vous devez vous assurer que vous utilisez au moins les versions minimales listées ci-dessous :

* MRTK : version 2.7.2 ou ultérieure
* AR-base : version 4.1.1 ou ultérieure
* Pipeline de rendu universel (URP) : version 10.5.1 ou ultérieure
* Ancres spatiales Azure : version 2,10 ou ultérieure
* Rendu distant Azure : version 1.0.15 ou ultérieure

> [!NOTE]
> si vous créez des applications VR sur Windows PC, le plug-in OpenXR de réalité mixte n’est pas strictement requis. toutefois, vous souhaiterez installer le plug-in si vous configurez des liaisons d’entrée pour les contrôleurs de réinitialisation HP ou si vous créez des applications qui fonctionnent sur les écouteurs HoloLens 2 et VR.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft ne recommande pas l’utilisation du plug-in Windows XR pour les nouveaux projets dans unity 2020.  Au lieu de cela, vous devez utiliser le plug-in OpenXR de la réalité mixte.

Toutefois, si vous utilisez Unity 2019 et que vous avez besoin de l’unité de 2,0 base de ARCore/ARKit pour la compatibilité avec les appareils/, ce plug-in active la prise en charge.

> [!IMPORTANT]
> L’utilisation de ce plug-in Unity 2019 n’est pas compatible avec les ancres spatiales Azure.

# <a name="legacy-xr"></a>[XR antérieur](#tab/legacy)

Si vous êtes toujours sur **unity 2019** ou une version antérieure, Microsoft recommande d’utiliser la **prise en charge XR intégrée héritée**.

alors que le plug-in Windows XR est fonctionnel sur unity 2019, ce n’est pas recommandé, car ce plug-in n’est pas compatible avec les ancres spatiales Azure sur unity 2019.

Si vous démarrez un nouveau projet, nous vous recommandons d' [installer unity 2020](../../choosing-unity-version.md) à la place et d’utiliser le plug-in OpenXR de la réalité mixte.