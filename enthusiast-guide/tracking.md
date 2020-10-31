---
title: FAQ sur le suivi
description: Suivi de la résolution des problèmes de Windows Mixed realisation qui va au-delà de notre documentation de support technique standard.
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, suivi
ms.openlocfilehash: 7a7e6add79af5917749ba241347d6cf719f6ed90
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132093"
---
# <a name="tracking-faqs"></a><span data-ttu-id="b8899-104">FAQ sur le suivi</span><span class="sxs-lookup"><span data-stu-id="b8899-104">Tracking FAQs</span></span>

## <a name="my-headset-has-stopped-tracking"></a><span data-ttu-id="b8899-105">Mon casque a arrêté le suivi</span><span class="sxs-lookup"><span data-stu-id="b8899-105">My headset has stopped tracking</span></span>

<span data-ttu-id="b8899-106">Assurez-vous que les lumières sont allumées et qu’il n’y a aucun obstacle aux caméras de suivi à l’intérieur de votre casque.</span><span class="sxs-lookup"><span data-stu-id="b8899-106">Make sure the lights are on, and that there isn't anything obstructing the inside-out tracking cameras on the front of your headset.</span></span> <span data-ttu-id="b8899-107">Si le suivi est perdu, la reprise peut prendre quelques secondes.</span><span class="sxs-lookup"><span data-stu-id="b8899-107">If tracking is lost, it can take a few seconds to resume.</span></span> <span data-ttu-id="b8899-108">Si ce n’est pas le cas, redémarrez le portail Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b8899-108">If it doesn't resume, restart the Windows Mixed Reality Portal.</span></span>

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a><span data-ttu-id="b8899-109">Je peux me pencher, mais je ne peux pas le traduire (je suis bloqué dans 3DOF)</span><span class="sxs-lookup"><span data-stu-id="b8899-109">I can look around but I can't translate (I'm stuck in 3DOF)</span></span>

<span data-ttu-id="b8899-110">Cela signifie que le système de suivi ne peut pas générer de pose, ou que l’application s’est arrêtée en utilisant de nouvelles données de pose à restituer.</span><span class="sxs-lookup"><span data-stu-id="b8899-110">This means that the tracking system cannot generate pose, or the application has stopped using new pose data to render.</span></span> <span data-ttu-id="b8899-111">Vérifiez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="b8899-111">Check the following:</span></span>

* <span data-ttu-id="b8899-112">Assurez-vous que la salle a suffisamment de lumière.</span><span class="sxs-lookup"><span data-stu-id="b8899-112">Make sure the room has enough light.</span></span>
* <span data-ttu-id="b8899-113">Assurez-vous que la salle dispose de suffisamment de détails pour effectuer le suivi.</span><span class="sxs-lookup"><span data-stu-id="b8899-113">Make sure the room has enough details to track.</span></span>
* <span data-ttu-id="b8899-114">Débranchez l’appareil, fermez Windows Mixed Reality, puis reconnectez l’appareil.</span><span class="sxs-lookup"><span data-stu-id="b8899-114">Unplug the device, close Windows Mixed Reality, and plug in the device again.</span></span>
* <span data-ttu-id="b8899-115">Si le message persiste, contactez le [support](https://support.microsoft.com/) technique</span><span class="sxs-lookup"><span data-stu-id="b8899-115">If the message persists, contact [customer support](https://support.microsoft.com/)</span></span>

## <a name="the-view-in-the-hmd-is-completely-frozen"></a><span data-ttu-id="b8899-116">La vue dans le HMD est complètement figée</span><span class="sxs-lookup"><span data-stu-id="b8899-116">The view in the HMD is completely frozen</span></span>

<span data-ttu-id="b8899-117">Cela signifie généralement que l’application ou un composant de niveau système a échoué.</span><span class="sxs-lookup"><span data-stu-id="b8899-117">This usually means the application or a system level component has failed.</span></span> <span data-ttu-id="b8899-118">Essayez d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b8899-118">Try to:</span></span>

1. <span data-ttu-id="b8899-119">Appuyez sur le bouton « démarrage » pour fermer l’application.</span><span class="sxs-lookup"><span data-stu-id="b8899-119">Press the "home" button to leave the application.</span></span>
2. <span data-ttu-id="b8899-120">Débranchez l’appareil, fermez MRP et rebranchez l’appareil.</span><span class="sxs-lookup"><span data-stu-id="b8899-120">Unplug the device, close MRP and plug the device back in.</span></span>
3. <span data-ttu-id="b8899-121">Redémarrez le PC.</span><span class="sxs-lookup"><span data-stu-id="b8899-121">Restart the PC.</span></span>

## <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-down-before-returning-to-normal"></a><span data-ttu-id="b8899-122">Le monde court figée et peut-être incliné ou renversé avant de revenir à la normale.</span><span class="sxs-lookup"><span data-stu-id="b8899-122">The world briefly froze and perhaps tilted or flipped upside down before returning to normal</span></span>

<span data-ttu-id="b8899-123">Cela peut être dû à une application ou à un composant de niveau système qui atteint une erreur irrécupérable, ou à un manque temporaire de mémoire ou de ressources processeur.</span><span class="sxs-lookup"><span data-stu-id="b8899-123">This could be caused by an application or system level component hitting a fatal error, or a temporary lack of memory or CPU resources.</span></span> <span data-ttu-id="b8899-124">Pour vérifier :</span><span class="sxs-lookup"><span data-stu-id="b8899-124">To check:</span></span>

1. <span data-ttu-id="b8899-125">Ouvrez le gestionnaire des tâches et assurez-vous qu’au moins 20% du processeur sont libres, 400 Mo de mémoire est disponible et l’e/s disque doit être inférieure à 80%.</span><span class="sxs-lookup"><span data-stu-id="b8899-125">Open Task Manager and ensure that at least 20% of the CPU is free, 400MB of memory is available and disk IO should be below 80%.</span></span>
2. <span data-ttu-id="b8899-126">Accédez à **observateur d’événements > journaux Windows > application** pour rechercher les erreurs survenues au bout du temps du gel.</span><span class="sxs-lookup"><span data-stu-id="b8899-126">Go to **Event Viewer > Windows Logs > Application** to look for any errors from around the time of the freeze.</span></span> <span data-ttu-id="b8899-127">Recherchez tout ce qui fait référence aux capteurs HoloLens, à la réalité mixte ou à l’application que vous exécutiez pendant cette période.</span><span class="sxs-lookup"><span data-stu-id="b8899-127">Look for anything that refers to HoloLens sensors, Mixed Reality, or the application that you were running around that time.</span></span> <span data-ttu-id="b8899-128">Ces journaux peuvent expliquer ce qui a provoqué l’échec.</span><span class="sxs-lookup"><span data-stu-id="b8899-128">Those logs might explain what caused the failure.</span></span>
3. <span data-ttu-id="b8899-129">Si le problème persiste, redémarrez le PC.</span><span class="sxs-lookup"><span data-stu-id="b8899-129">Restart the PC if the problem persists.</span></span>

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a><span data-ttu-id="b8899-130">Le monde a basculé momentanément et est revenu à la normale</span><span class="sxs-lookup"><span data-stu-id="b8899-130">The world flipped upside down momentarily and returned to normal</span></span>

<span data-ttu-id="b8899-131">Cela est généralement dû à des erreurs lors de l’obtention de données de capteur à partir du casque pour informer les algorithmes de suivi.</span><span class="sxs-lookup"><span data-stu-id="b8899-131">This is typically caused by errors in obtaining sensor data from the headset to inform the tracking algorithms.</span></span> <span data-ttu-id="b8899-132">Si cela se produit fréquemment :</span><span class="sxs-lookup"><span data-stu-id="b8899-132">If this happens frequently:</span></span>

1. <span data-ttu-id="b8899-133">Branchez le casque sur un port USB 3,0 différent.</span><span class="sxs-lookup"><span data-stu-id="b8899-133">Plug the headset into a different USB 3.0 port.</span></span>
2. <span data-ttu-id="b8899-134">Branchez le casque directement sur le PC plutôt que sur un concentrateur USB 3,0.</span><span class="sxs-lookup"><span data-stu-id="b8899-134">Plug the headset directly into the PC rather than into a USB 3.0 hub.</span></span>
3. <span data-ttu-id="b8899-135">Si le problème persiste, contactez le [support](https://support.microsoft.com/)technique.</span><span class="sxs-lookup"><span data-stu-id="b8899-135">If the problem persists, contact [customer support](https://support.microsoft.com/).</span></span>

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a><span data-ttu-id="b8899-136">Le monde est incliné, mais je peux naviguer et parcourir Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b8899-136">The world is tilted but I can navigate and walk around in Windows Mixed Reality</span></span>

<span data-ttu-id="b8899-137">Si des erreurs de données de capteur sont consignées dans les données d’environnement sur votre ordinateur, cela peut entraîner l’inclinaison de Windows Mixed realisation, parfois de façon permanente.</span><span class="sxs-lookup"><span data-stu-id="b8899-137">If sensor data errors are recorded into the environment data on your PC, it can cause Windows Mixed Reality to appear tilted, sometimes permanently.</span></span> <span data-ttu-id="b8899-138">Pour résoudre ce problème :</span><span class="sxs-lookup"><span data-stu-id="b8899-138">To fix this:</span></span>

1. <span data-ttu-id="b8899-139">Débranchez le casque, fermez Windows Mixed Reality et rebranchez le casque.</span><span class="sxs-lookup"><span data-stu-id="b8899-139">Unplug the headset, close Windows Mixed Reality and plug the headset back in.</span></span>
2. <span data-ttu-id="b8899-140">Redémarrez le PC.</span><span class="sxs-lookup"><span data-stu-id="b8899-140">Restart the PC.</span></span>
3. <span data-ttu-id="b8899-141">Effacez les données de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="b8899-141">Clear your environment data.</span></span>