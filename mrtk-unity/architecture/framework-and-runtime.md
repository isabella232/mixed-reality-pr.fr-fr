---
title: Framework et Runtime
description: Informations relatives à l’infrastructure et au runtime dans MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121607"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="be0c5-104">Framework et Runtime</span><span class="sxs-lookup"><span data-stu-id="be0c5-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="be0c5-105">Modifications apportées à la scène</span><span class="sxs-lookup"><span data-stu-id="be0c5-105">Changes to the scene</span></span>

<span data-ttu-id="be0c5-106">Pour utiliser la boîte à outils, une instance du script MixedRealityToolkit doit se trouver dans votre scène.</span><span class="sxs-lookup"><span data-stu-id="be0c5-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="be0c5-107">Pour en ajouter un, utilisez l’option de menu : Mixed Reality Toolkit-> ajouter à la scène et configurer.</span><span class="sxs-lookup"><span data-stu-id="be0c5-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="be0c5-108">Cette instance est responsable de l’inscription, de la mise à jour et de la suppression des services.</span><span class="sxs-lookup"><span data-stu-id="be0c5-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="be0c5-109">C’est également là que votre profil de configuration est choisi.</span><span class="sxs-lookup"><span data-stu-id="be0c5-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="be0c5-110">Outre l’ajout du GameObject MRTK à la scène, l’option de menu permet également :</span><span class="sxs-lookup"><span data-stu-id="be0c5-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="be0c5-111">Ajoutez le MixedRealityPlayspace, qui est utilisé par de nombreux autres composants MRTK pour être à l’origine des transformations d’espace universelles et locales.</span><span class="sxs-lookup"><span data-stu-id="be0c5-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="be0c5-112">Déplacez l’appareil photo principal en tant qu’enfant du MixedRealityPlayspace (et ajoutez également des scripts d’entrée et de regard pour l’appareil photo principal, qui aident à UnityUI et aux fonctionnalités d’entrée de regard).</span><span class="sxs-lookup"><span data-stu-id="be0c5-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="be0c5-113">Objet MixedRealityToolkit et Runtime</span><span class="sxs-lookup"><span data-stu-id="be0c5-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="be0c5-114">Le MRTK possède plusieurs services principaux.</span><span class="sxs-lookup"><span data-stu-id="be0c5-114">The MRTK has several core services.</span></span> <span data-ttu-id="be0c5-115">Une coordonnée les unes avec les autres ; d’autres sont indépendantes.</span><span class="sxs-lookup"><span data-stu-id="be0c5-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="be0c5-116">Tous partagent le même cycle de vie : le démarrage, l’inscription, la mise à jour et la destruction, et ce cycle de vie se distingue du cycle de vie monocomportement d’Unity.</span><span class="sxs-lookup"><span data-stu-id="be0c5-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="be0c5-117">Cette [publication de taille moyenne](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explique quelques-unes des raisons de cette approche.</span><span class="sxs-lookup"><span data-stu-id="be0c5-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="be0c5-118">MRTK possède un objet unique qui gère la vie et l’exécution de ses services.</span><span class="sxs-lookup"><span data-stu-id="be0c5-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="be0c5-119">Cette entité garantit que :</span><span class="sxs-lookup"><span data-stu-id="be0c5-119">This entity ensures that:</span></span>

- <span data-ttu-id="be0c5-120">Lorsque le jeu démarre, la découverte et l’initialisation des services s’effectuent dans un ordre prédéfini.</span><span class="sxs-lookup"><span data-stu-id="be0c5-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="be0c5-121">Il fournit un mécanisme permettant aux services de s’inscrire eux-mêmes (par exemple, « je prend en charge ce service ! ») et pour d’autres appelants d’obtenir un blocage de ces services.</span><span class="sxs-lookup"><span data-stu-id="be0c5-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="be0c5-122">Il fournit les appels Update ()/LateUpdate () et les transfère vers les différents services (par exemple, via UpdateAllServices/LateUpdateAllServices).</span><span class="sxs-lookup"><span data-stu-id="be0c5-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
