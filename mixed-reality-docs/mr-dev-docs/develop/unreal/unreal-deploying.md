---
title: Déployer sur l’appareil dans Unreal
description: Guide de déploiement sur un appareil en non réel dans HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, réalité mixte, déployer sur un appareil, PC, documentation, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
appliesto:
- HoloLens 2
ms.openlocfilehash: 390bd1a9f1bc643efb1a342421e8c96574e74334
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925908"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="a8067-104">Déployer sur l’appareil dans Unreal</span><span class="sxs-lookup"><span data-stu-id="a8067-104">Deploy to device in Unreal</span></span>

<span data-ttu-id="a8067-105">Il existe deux façons de déployer une application inréelle sur HoloLens 2 :</span><span class="sxs-lookup"><span data-stu-id="a8067-105">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="a8067-106">Directement à partir de l’éditeur inréel</span><span class="sxs-lookup"><span data-stu-id="a8067-106">Directly from the Unreal editor</span></span>
* <span data-ttu-id="a8067-107">En tant que package téléchargé via le portail de l’appareil</span><span class="sxs-lookup"><span data-stu-id="a8067-107">As a package uploaded via the device portal</span></span>

<span data-ttu-id="a8067-108">Les deux options vous obligent à configurer votre HoloLens pour utiliser le portail de l' [appareil](../platform-capabilities-and-apis/using-the-windows-device-portal.md) pour le développement.</span><span class="sxs-lookup"><span data-stu-id="a8067-108">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="a8067-109">Déploiement sur un appareil à partir de l’éditeur inréel</span><span class="sxs-lookup"><span data-stu-id="a8067-109">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="a8067-110">Sélectionnez la flèche déroulante en regard du bouton **lancer** .</span><span class="sxs-lookup"><span data-stu-id="a8067-110">Select the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="a8067-111">Initialement, l’option de périphérique HoloLens est grisée.</span><span class="sxs-lookup"><span data-stu-id="a8067-111">Initially, the HoloLens device option will be grayed out.</span></span>

![Options de liste déroulante de lancement](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="a8067-113">Ouvrez la **Device Manager** et notez que votre HoloLens ne s’affiche pas automatiquement dans la liste des appareils.</span><span class="sxs-lookup"><span data-stu-id="a8067-113">Open the **Device Manager** and note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="a8067-114">Développez la section **Ajouter un appareil non répertorié** .</span><span class="sxs-lookup"><span data-stu-id="a8067-114">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="a8067-115">Sélectionnez **HoloLens** en tant que **plateforme**.</span><span class="sxs-lookup"><span data-stu-id="a8067-115">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="a8067-116">Entrez l’adresse IP et les informations de port de vos appareils, séparées par un signe deux-points ( :) comme identificateur d’appareil.</span><span class="sxs-lookup"><span data-stu-id="a8067-116">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="a8067-117">Par exemple, « 127.0.0.1:10 080 » (en cas de connexion via USB).</span><span class="sxs-lookup"><span data-stu-id="a8067-117">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="a8067-118">Utilisez les informations d’identification du nom d’utilisateur et du mot de passe du portail de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="a8067-118">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="a8067-119">Appuyez sur **Ajouter** et fermez le gestionnaire de périphériques.</span><span class="sxs-lookup"><span data-stu-id="a8067-119">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="a8067-120">En cas d’erreur, telle qu’une adresse incorrecte ou des informations d’identification de l’utilisateur, un message s’affiche dans le journal de sortie.</span><span class="sxs-lookup"><span data-stu-id="a8067-120">If there's an error, such as wrong address or user credentials, a message will print to the Output Log.</span></span>

![Ajout d’un appareil non répertorié](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="a8067-122">Sélectionnez à nouveau la flèche déroulante à côté du bouton de **lancement** : cette fois, vous devriez voir l’appareil HoloLens que vous venez d’ajouter.</span><span class="sxs-lookup"><span data-stu-id="a8067-122">Select the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="a8067-123">Sélectionnez l’appareil HoloLens à générer et déployer sur votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a8067-123">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="a8067-124">La génération pour l’appareil peut impliquer la recompilation des nuanceurs (surtout lors de la première exécution). cette opération peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="a8067-124">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="a8067-125">Ne laissez pas l’appareil passer en mode veille tant que l’application n’est pas en cours d’exécution (vous devrez peut-être l’utiliser).</span><span class="sxs-lookup"><span data-stu-id="a8067-125">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="a8067-126">Sinon, la compilation du nuanceur échouera.</span><span class="sxs-lookup"><span data-stu-id="a8067-126">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="a8067-127">Déploiement sur un appareil via le portail de l’appareil</span><span class="sxs-lookup"><span data-stu-id="a8067-127">Deploying to device via device portal</span></span>

<span data-ttu-id="a8067-128">Vous trouverez des instructions détaillées sur l’empaquetage et le déploiement d’une application dans la [série de didacticiels inréels](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span><span class="sxs-lookup"><span data-stu-id="a8067-128">You can find detailed instructions on packaging and deploying an app in the [Unreal tutorial series](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a8067-129">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="a8067-129">Next Development Checkpoint</span></span>

<span data-ttu-id="a8067-130">Si vous suivez le parcours de développement inréel que nous avons mis en place, vous êtes au cœur de l’étape de déploiement.</span><span class="sxs-lookup"><span data-stu-id="a8067-130">If you're following the Unreal development journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="a8067-131">À partir de là, vous pouvez continuer à ajouter des services avancés :</span><span class="sxs-lookup"><span data-stu-id="a8067-131">From here, you can continue to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a8067-132">Services avancés</span><span class="sxs-lookup"><span data-stu-id="a8067-132">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="a8067-133">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="a8067-133">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
