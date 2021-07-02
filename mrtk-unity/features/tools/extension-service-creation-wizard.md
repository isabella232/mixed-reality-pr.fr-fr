---
title: Assistant Création de service d’extension
description: Documentation sur l’Assistant pour effectuer la transition des singletons vers les services MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 4be9a58c7d63ab3bc93bcc326a90260cf6a3366b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176611"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="5bf3c-104">Assistant Création de service d’extension</span><span class="sxs-lookup"><span data-stu-id="5bf3c-104">Extension service creation wizard</span></span>

<span data-ttu-id="5bf3c-105">Il peut être difficile de faire la transition des singletons aux services.</span><span class="sxs-lookup"><span data-stu-id="5bf3c-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="5bf3c-106">Cet Assistant peut compléter notre documentation et des exemples de code en permettant aux développeurs de créer de nouveaux services avec (à peu près) la même facilité que la création d’un nouveau script monocomportement.</span><span class="sxs-lookup"><span data-stu-id="5bf3c-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="5bf3c-107">Pour en savoir plus sur la création de services à partir de zéro, consultez notre [Guide de création de services inscrits](../../configuration/mixed-reality-configuration-guide.md) (bientôt disponible).</span><span class="sxs-lookup"><span data-stu-id="5bf3c-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="5bf3c-108">Lancement de l’Assistant</span><span class="sxs-lookup"><span data-stu-id="5bf3c-108">Launching the wizard</span></span>

<span data-ttu-id="5bf3c-109">Lancez l’Assistant à partir du menu principal : **MixedRealityToolkit/Utilities/Create extension service** -l’Assistant vous guidera ensuite tout au long du processus de génération de votre script de service, de votre interface et de votre classe de profil.</span><span class="sxs-lookup"><span data-stu-id="5bf3c-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="5bf3c-110">Modification de votre script de service</span><span class="sxs-lookup"><span data-stu-id="5bf3c-110">Editing your service script</span></span>

<span data-ttu-id="5bf3c-111">Par défaut, vos nouvelles ressources de script sont générées dans le `MixedRealityToolkit.Generated/Extensions` dossier.</span><span class="sxs-lookup"><span data-stu-id="5bf3c-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="5bf3c-112">Une fois que vous avez terminé l’Assistant, accédez à cet emplacement et ouvrez votre script de service.</span><span class="sxs-lookup"><span data-stu-id="5bf3c-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="5bf3c-113">Les scripts de service générés incluent des invites similaires aux nouveaux scripts monocomportement.</span><span class="sxs-lookup"><span data-stu-id="5bf3c-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="5bf3c-114">Ils vous permettront de savoir où initialiser et mettre à jour votre service.</span><span class="sxs-lookup"><span data-stu-id="5bf3c-114">They will let you know where to initialize and update your service.</span></span>

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

<span data-ttu-id="5bf3c-115">Si vous avez choisi d’inscrire votre service dans l’Assistant, il vous suffit de modifier ce script et votre service sera automatiquement mis à jour.</span><span class="sxs-lookup"><span data-stu-id="5bf3c-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="5bf3c-116">Sinon, vous pouvez en savoir plus sur [l’inscription de votre nouveau service ici](../../configuration/mixed-reality-configuration-guide.md).</span><span class="sxs-lookup"><span data-stu-id="5bf3c-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
