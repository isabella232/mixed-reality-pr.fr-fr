---
title: Services d’extension
description: documentation sur les fonctionnalités étendues dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 0f9f30bb7d2d44cef828b79bc916d933a6355dbb1068b09e73317d1c977ef45a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186994"
---
# <a name="extension-services"></a>Services d’extension

les services d’Extension sont des composants qui étendent les fonctionnalités de la réalité mixte Shared Computer Toolkit. Ces services peuvent être fournis par le MRTK ou par d’autres parties.

## <a name="creating-an-extension-service"></a>Création d’un service d’extension

La méthode la plus efficace pour créer un service d’extension consiste à utiliser l' [Assistant Création de service d’extension](../tools/extension-service-creation-wizard.md).
pour démarrer l’assistant création de service d’extension, sélectionnez Shared Computer Toolkit de la **réalité mixte > utilitaires > créer un service d’extension**.

![Assistant Création de service d’extension](../images/extension-wizard/ExtensionServiceCreationWizard.png)

L’Assistant automatise la création des composants du service et garantit l’héritage approprié de l’interface.

![Composants créés par l’Assistant Création de service d’extension](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> Dans MRTK version 2.0.0, l’Assistant service d’extension présente un problème où l’inspecteur de service et le profil de service doivent être générés. Pour plus d’informations, consultez le problème [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) .

Une fois l’Assistant terminé, les fonctionnalités du service peuvent être implémentées.

## <a name="registering-an-extension-service"></a>Inscription d’un service d’extension

pour être accessible par une application, le nouveau service d’extension doit être inscrit avec la réalité mixte Shared Computer Toolkit.

L’Assistant Création d’un service d’extension peut être utilisé pour inscrire le service.

![Inscription de l’Assistant Création de service d’extension](../images/extension-wizard/ExtensionServiceWizardRegister.png)

le service peut également être enregistré manuellement à l’aide de la réalité mixte Shared Computer Toolkit l’inspecteur de configuration.

![Inscription manuelle du service d’extension](../images/profiles/RegisterExtensionService.png)

Si le service d’extension utilise un profil, vérifiez qu’il est spécifié dans l’inspecteur.

![Service d’extension configuré](../images/profiles/ConfiguredExtensionService.png)

Le nom et la priorité du composant peuvent également être ajustés.

## <a name="accessing-an-extension-service"></a>Accès à un service d’extension

Les services d’extension sont accessibles, dans le code, à l’aide de, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) comme indiqué dans l’exemple ci-dessous.

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>Voir aussi

- [Systèmes, services d’extension et fournisseurs de données](../../architecture/systems-extensions-providers.md)
- [Assistant Création de service d’extension](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
