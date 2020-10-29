---
title: Déployer sur l’appareil dans Unreal
description: Guide de déploiement sur un appareil en non réel dans HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, réalité mixte, déployer sur un appareil, PC, documentation
appliesto:
- HoloLens 2
ms.openlocfilehash: abd5e5c28ec5e66c4f73df8edf5e0ac0212d170a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679815"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="24683-104">Déployer sur l’appareil dans Unreal</span><span class="sxs-lookup"><span data-stu-id="24683-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="24683-105">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="24683-105">Overview</span></span>
<span data-ttu-id="24683-106">Il existe deux façons de déployer une application inréelle sur HoloLens 2 :</span><span class="sxs-lookup"><span data-stu-id="24683-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="24683-107">Directement à partir de l’éditeur inréel</span><span class="sxs-lookup"><span data-stu-id="24683-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="24683-108">En tant que package téléchargé via le portail de l’appareil</span><span class="sxs-lookup"><span data-stu-id="24683-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="24683-109">Les deux options vous obligent à configurer votre HoloLens pour utiliser le portail de l' [appareil](../platform-capabilities-and-apis/using-the-windows-device-portal.md) pour le développement.</span><span class="sxs-lookup"><span data-stu-id="24683-109">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="24683-110">Déploiement sur un appareil à partir de l’éditeur inréel</span><span class="sxs-lookup"><span data-stu-id="24683-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="24683-111">Cliquez sur la flèche déroulante en regard du bouton **lancer** .</span><span class="sxs-lookup"><span data-stu-id="24683-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="24683-112">Initialement, l’option de périphérique HoloLens est grisée.</span><span class="sxs-lookup"><span data-stu-id="24683-112">Initially, the HoloLens device option will be grayed out.</span></span>

![Options de liste déroulante de lancement](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="24683-114">Ouvrez le **Device Manager** .</span><span class="sxs-lookup"><span data-stu-id="24683-114">Open the **Device Manager** .</span></span> <span data-ttu-id="24683-115">Notez que votre HoloLens ne s’affiche pas automatiquement dans la liste des appareils.</span><span class="sxs-lookup"><span data-stu-id="24683-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="24683-116">Développez la section **Ajouter un appareil non répertorié** .</span><span class="sxs-lookup"><span data-stu-id="24683-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="24683-117">Sélectionnez **HoloLens** en tant que **plateforme** .</span><span class="sxs-lookup"><span data-stu-id="24683-117">Select **HoloLens** as your **Platform** .</span></span>

5. <span data-ttu-id="24683-118">Entrez l’adresse IP et les informations de port de vos appareils, séparées par un signe deux-points ( :) comme identificateur d’appareil.</span><span class="sxs-lookup"><span data-stu-id="24683-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="24683-119">Par exemple, « 127.0.0.1:10 080 » (en cas de connexion via USB).</span><span class="sxs-lookup"><span data-stu-id="24683-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="24683-120">Utilisez les informations d’identification du nom d’utilisateur et du mot de passe du portail de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="24683-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="24683-121">Appuyez sur **Ajouter** et fermez le gestionnaire de périphériques.</span><span class="sxs-lookup"><span data-stu-id="24683-121">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="24683-122">Dans le cas d’une erreur (telle qu’une adresse incorrecte, un nom d’utilisateur ou un mot de passe), un message est imprimé dans le journal de sortie.</span><span class="sxs-lookup"><span data-stu-id="24683-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![Ajout d’un appareil non répertorié](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="24683-124">Cliquez à nouveau sur la flèche déroulante en regard du bouton **lancer** . cette fois-ci, vous devriez voir l’appareil HoloLens que vous venez d’ajouter.</span><span class="sxs-lookup"><span data-stu-id="24683-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="24683-125">Sélectionnez l’appareil HoloLens à générer et déployer sur votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="24683-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="24683-126">La génération pour l’appareil peut impliquer la recompilation des nuanceurs (surtout lors de la première exécution). cette opération peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="24683-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="24683-127">Ne laissez pas l’appareil passer en mode veille tant que l’application n’est pas en cours d’exécution (vous devrez peut-être l’utiliser).</span><span class="sxs-lookup"><span data-stu-id="24683-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="24683-128">Sinon, la compilation du nuanceur échouera.</span><span class="sxs-lookup"><span data-stu-id="24683-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="24683-129">Déploiement sur un appareil via le portail de l’appareil</span><span class="sxs-lookup"><span data-stu-id="24683-129">Deploying to device via device portal</span></span>

<span data-ttu-id="24683-130">Vous trouverez des instructions détaillées sur l' [empaquetage et le déploiement d’une application](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) dans la dernière section du prise en main avec des séries de didacticiels inréels.</span><span class="sxs-lookup"><span data-stu-id="24683-130">You can find detailed instructions on [packaging and deploying an app](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="24683-131">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="24683-131">Next Development Checkpoint</span></span>

<span data-ttu-id="24683-132">Si vous suivez le parcours du point de contrôle de développement inréel que nous avons disposé, vous êtes au cœur de l’étape de déploiement.</span><span class="sxs-lookup"><span data-stu-id="24683-132">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="24683-133">À partir de là, vous pouvez passer à l’ajout de services avancés :</span><span class="sxs-lookup"><span data-stu-id="24683-133">From here, you can proceed to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="24683-134">Services avancés</span><span class="sxs-lookup"><span data-stu-id="24683-134">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="24683-135">Vous pouvez toujours revenir aux [points de contrôle de développement inréels](unreal-development-overview.md#4-deploying-to-a-device) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="24683-135">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-deploying-to-a-device) at any time.</span></span>
