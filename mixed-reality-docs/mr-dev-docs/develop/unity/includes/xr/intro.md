---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906939"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Le plug-in OpenXR de réalité mixte est **recommandé par Microsoft** pour unity 2020 LTS ou version ultérieure. À mesure que de nouvelles fonctionnalités sont développées à l’avenir, elles sont uniquement incluses dans le plug-in OpenXR de la réalité mixte.

Le plug-in OpenXR de réalité mixte prend entièrement en charge les implémentations de 4,0 base de ARPlaneManager et de ARRaycastManager. Cela vous permet d’écrire le code Raycasting une seule fois qui s’étend ensuite sur les téléphones et tablettes HoloLens 2 et ARCore/ARKit.

### <a name="prerequisites"></a>Prérequis 

* [Outils les plus récents pour le développement HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Dernière Unity 2020,3 LTS, (nous recommandons 2020.3.8 F1 ou supérieur)

### <a name="minimum-versions"></a>Versions minimales

Les instructions de cette page vous configurent avec les exigences les plus récentes et les OpenXR les plus importantes indiquées ci-dessous :

* Dernier plug-in OpenXR Unity, (nous vous recommandons 1,2 ou version ultérieure)
* Dernier plug-in OpenXR de réalité mixte, (nous vous recommandons la version 1.0.0 ou ultérieure)
* **(Facultatif)** Dernière version de MRTK, (nous recommandons la version 2,7 ou ultérieure)
* **(Facultatif)** Dernier package de pipeline de rendu universel, (nous recommandons la version 10.5.1 ou ultérieure)

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> Si vous générez des applications VR sur un PC Windows, le plug-in OpenXR de réalité mixte n’est pas obligatoire. Toutefois, vous souhaiterez installer le plug-in si vous personnalisez le mappage de contrôleur pour les contrôleurs de reréverbérations de HP ou si vous créez des applications qui fonctionnent à la fois sur les casques HoloLens 2 et VR.

# <a name="windows-xr"></a>[XR Windows](#tab/windowsxr)

Microsoft ne recommande pas l’utilisation du plug-in XR Windows pour les nouveaux projets dans Unity 2020.

Toutefois, si vous utilisez Unity 2019 et que vous avez besoin de l’unité de 2,0 base de ARCore/ARKit pour la compatibilité avec les appareils/, ce plug-in active la prise en charge.

> [!IMPORTANT]
> L’utilisation de ce plug-in Unity 2019 ne prend pas en charge les ancres spatiales Azure. 

# <a name="legacy-xr"></a>[XR antérieur](#tab/legacy)

Si vous êtes toujours sur Unity 2019 ou une version antérieure, Microsoft recommande d’utiliser la prise en charge XR intégrée héritée. Alors que le plug-in XR Windows est fonctionnel sur Unity 2019, cela n’est pas recommandé, car les ancres spatiales Azure ne sont pas prises en charge.