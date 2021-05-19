---
title: Services d’extension
description: documentation sur les fonctionnalités étendues dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: a39616a091a3f6800c429dc797ec2f3130e96f40
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144541"
---
# <a name="extension-services"></a>Services d’extension

Les services d’extension sont des composants qui étendent les fonctionnalités du kit de développement de la réalité mixte. Ces services peuvent être fournis par le MRTK ou par d’autres parties.

## <a name="creating-an-extension-service"></a>Création d’un service d’extension

La méthode la plus efficace pour créer un service d’extension consiste à utiliser l' [Assistant Création de service d’extension](../tools/extension-service-creation-wizard.md).
Pour démarrer l’Assistant Création de service d’extension, sélectionnez **Mixed Reality Toolkit > Utilities > Create extension service**.

![Assistant Création de service d’extension](../images/extension-wizard/ExtensionServiceCreationWizard.png)

L’Assistant automatise la création des composants du service et garantit l’héritage approprié de l’interface.

![Composants créés par l’Assistant Création de service d’extension](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> Dans MRTK version 2.0.0, l’Assistant service d’extension présente un problème où l’inspecteur de service et le profil de service doivent être générés. Pour plus d’informations, consultez le problème [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) .

Une fois l’Assistant terminé, les fonctionnalités du service peuvent être implémentées.

## <a name="registering-an-extension-service"></a>Inscription d’un service d’extension

Pour être accessible par une application, le nouveau service d’extension doit être inscrit auprès du kit de pratiques de la réalité mixte.

L’Assistant Création d’un service d’extension peut être utilisé pour inscrire le service.

![Inscription de l’Assistant Création de service d’extension](../images/extension-wizard/ExtensionServiceWizardRegister.png)

Le service peut également être inscrit manuellement à l’aide de l’inspecteur de configuration du kit d’outils de réalité mixte.

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
