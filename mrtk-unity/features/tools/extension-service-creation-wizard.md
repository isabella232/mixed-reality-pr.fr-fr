---
title: Assistant Création de service d’extension
description: Documentation sur l’Assistant pour effectuer la transition des singletons vers les services MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 83797a9d6d465a150406b27162a5e84c157567f1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143544"
---
# <a name="extension-service-creation-wizard"></a>Assistant Création de service d’extension

Il peut être difficile de faire la transition des singletons aux services. Cet Assistant peut compléter notre documentation et des exemples de code en permettant aux développeurs de créer de nouveaux services avec (à peu près) la même facilité que la création d’un nouveau script monocomportement. Pour en savoir plus sur la création de services à partir de zéro, consultez notre [Guide de création de services inscrits](../../configuration/mixed-reality-configuration-guide.md) (bientôt disponible).

## <a name="launching-the-wizard"></a>Lancement de l’Assistant

Lancez l’Assistant à partir du menu principal : **MixedRealityToolkit/Utilities/Create extension service** -l’Assistant vous guidera ensuite tout au long du processus de génération de votre script de service, de votre interface et de votre classe de profil.

## <a name="editing-your-service-script"></a>Modification de votre script de service

Par défaut, vos nouvelles ressources de script sont générées dans le `MixedRealityToolkit.Generated/Extensions` dossier. Une fois que vous avez terminé l’Assistant, accédez à cet emplacement et ouvrez votre script de service.

Les scripts de service générés incluent des invites similaires aux nouveaux scripts monocomportement. Ils vous permettront de savoir où initialiser et mettre à jour votre service.

```csharp
namespace Microsoft.MixedReality.Toolkit.Extensions
{
    [MixedRealityExtensionService(SupportedPlatforms.WindowsStandalone|SupportedPlatforms.MacStandalone|SupportedPlatforms.LinuxStandalone|SupportedPlatforms.WindowsUniversal)]
    public class NewService : BaseExtensionService, INewService, IMixedRealityExtensionService
    {
        private NewServiceProfile newServiceProfile;

        public NewService(IMixedRealityServiceRegistrar registrar,  string name,  uint priority,  BaseMixedRealityProfile profile) : base(registrar, name, priority, profile) 
        {
            newServiceProfile = (NewServiceProfile)profile;
        }

        public override void Initialize()
        {
            // Do service initialization here.
        }

        public override void Update()
        {
            // Do service updates here.
        }
    }
}
```

Si vous avez choisi d’inscrire votre service dans l’Assistant, il vous suffit de modifier ce script et votre service sera automatiquement mis à jour. Sinon, vous pouvez en savoir plus sur [l’inscription de votre nouveau service ici](../../configuration/mixed-reality-configuration-guide.md).
