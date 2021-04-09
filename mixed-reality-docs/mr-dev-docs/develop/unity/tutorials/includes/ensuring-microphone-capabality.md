---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097413"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in Windows XR](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Activation de la fonctionnalité Microphone et ajout d’un fournisseur de données de saisie vocale

Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Microphone Capability** est grisée :

![Activer la fonctionnalité du microphone](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La fonctionnalité Microphone doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels. Toutefois, si elle n’est pas activée, veillez à l’activer maintenant.

Dans la fenêtre Hierarchy, sélectionnez l’objet MixedRealityToolkit. Ensuite, dans la fenêtre Inspector, accédez à l’onglet Input :

* Développez **Input Data Providers**, puis cliquez sur le bouton **+ Add Data Provider** pour ajouter un nouveau fournisseur de données.

![Fournisseur de données pour l’ajout de nouvelles commandes vocales](../images/mr-learning-base/base-09-section1-step1-2.png)

Affectez **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** au champ **Type** du nouveau fournisseur de données.

![Ajout de paramètres pour les nouvelles commandes vocales](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Activation de la fonctionnalité Microphone et ajout d’un fournisseur de données de saisie vocale

Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Microphone Capability** est grisée :

![Activer la fonctionnalité du microphone pour OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La fonctionnalité Microphone doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels. Toutefois, si elle n’est pas activée, veillez à l’activer maintenant.

Dans la fenêtre Hierarchy, sélectionnez l’objet MixedRealityToolkit. Ensuite, dans la fenêtre Inspector, accédez à l’onglet Input :

* Développez **Input Data Providers**, puis cliquez sur le bouton **+ Add Data Provider** pour ajouter un nouveau fournisseur de données.

![Ajout de nouvelles commandes vocales pour OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

Affectez **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** au champ **Type** du nouveau fournisseur de données.

![Ajout des paramètres des nouvelles commandes vocales pour OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Vérification de l’activation de la fonctionnalité Microphone

Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Microphone Capability** est grisée :

![Activer la fonctionnalité du microphone](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La fonctionnalité Microphone doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels. Toutefois, si elle n’est pas activée, veillez à l’activer maintenant.
