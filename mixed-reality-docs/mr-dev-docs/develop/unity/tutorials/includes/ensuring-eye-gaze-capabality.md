---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097796"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in Windows XR](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Activation de la fonctionnalité d’entrée par pointage du regard et ajout du fournisseur de données de pointage du regard

Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Eye Gaze Input Capability** est grisée :

![Fenêtre MRTK Project Configurator d’Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> La fonctionnalité Gaze Input doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels. Toutefois, si elle n’est pas activée, activez-la maintenant.

Dans la fenêtre Hierarchy, sélectionnez l’objet MixedRealityToolkit. Ensuite, dans la fenêtre Inspector, accédez à l’onglet Input :

* Développez **Input Data Providers**, puis cliquez sur le bouton **+ Add Data Provider** pour ajouter un nouveau fournisseur de données.

![Ajout du fournisseur de données de pointage du regard 1](../images/mr-learning-base/base-08-section1-step1-2.png)

Affectez **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** au champ **Type** du nouveau fournisseur de données.

![Ajout du fournisseur de données de pointage du regard 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Activation de la fonctionnalité d’entrée par pointage du regard et ajout du fournisseur de données de pointage du regard

Dans la fenêtre Hierarchy, sélectionnez l’objet MixedRealityToolkit. Ensuite, dans la fenêtre Inspector, accédez à l’onglet Input :

* Développez **Input Data Providers**, puis cliquez sur le bouton **+ Add Data Provider** pour ajouter un nouveau fournisseur de données.

![Ajout du fournisseur de données de pointage du regard 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

Affectez **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** au champ **Type** du nouveau fournisseur de données.

![Ajout du fournisseur de données de pointage du regard 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Vérifier que la fonctionnalité d’entrée avec le pointage du regard est activée

Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Eye Gaze Input Capability** est grisée :

![Fenêtre MRTK Project Configurator d’Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> La fonctionnalité Gaze Input doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels. Toutefois, si elle n’est pas activée, activez-la maintenant.
