---
title: Mode de recherche HoloLens
description: En utilisant le mode de recherche sur HoloLens, une application peut accéder aux flux de capteur de périphérique clé (profondeur, suivi de l’environnement et réflectivité de l’IR).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Mode de recherche, CV, RS4, vision par ordinateur, recherche, HoloLens, HoloLens 2
ms.openlocfilehash: 327ee932dce99a2559e406630611dcc3c69a0002
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679903"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="0fbc4-104">Mode de recherche HoloLens</span><span class="sxs-lookup"><span data-stu-id="0fbc4-104">HoloLens Research Mode</span></span>

<span data-ttu-id="0fbc4-105">Le mode de recherche a été introduit dans le HoloLens de 1re génération pour permettre l’accès aux capteurs de clé sur l’appareil, en particulier pour les applications de recherche qui ne sont pas destinées au déploiement.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="0fbc4-106">Le mode de recherche pour HoloLens 2 conserve les fonctionnalités de HoloLens 1, en ajoutant l’accès aux flux supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="0fbc4-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="0fbc4-107">**Caméras de suivi de l’environnement clair visibles** -caméras de nuances de gris utilisées par le système pour le suivi des têtes et la génération de cartes.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="0fbc4-108">**Appareil photo de profondeur** : fonctionne en deux modes :</span><span class="sxs-lookup"><span data-stu-id="0fbc4-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="0fbc4-109">Détection presque-profondeur AHAT, à fréquence élevée (45 FPS) utilisée pour le suivi des handles.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="0fbc4-110">De la même façon que le mode de levée abrégée de la première version, AHAT fournit une Pseudo-profondeur avec un retour à la ligne au-delà de 1 mètre.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="0fbc4-111">Détection de longueurs longues, à faible fréquence (1-5 FPS), utilisée par le [mappage spatial](../../design/spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="0fbc4-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="0fbc4-112">**Deux versions du flux de réflectivité IR** -utilisées par le HoloLens pour calculer la profondeur.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="0fbc4-113">Ces images sont éclairées par infrarouge et ne sont pas affectées par la lumière visible ambiante.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="0fbc4-114">Si vous utilisez un HoloLens 2, vous avez également accès aux entrées supplémentaires ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="0fbc4-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="0fbc4-115">**Accéléromètre** : utilisé par le système pour déterminer l’accélération linéaire le long des axes X, Y et Z et la gravité.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="0fbc4-116">**Gyroscope** : utilisé par le système pour déterminer les rotations.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="0fbc4-117">**Magnétomètre** : utilisé par le système pour estimer l’orientation absolue.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fbc4-118">Le mode de recherche est actuellement en version préliminaire publique.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="0fbc4-119">![Capture d’écran de l’application en mode recherche](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="0fbc4-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="0fbc4-120">*Capture de réalité mixte d’une application de test qui affiche les huit flux de capteurs disponibles en mode de recherche*</span><span class="sxs-lookup"><span data-stu-id="0fbc4-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="0fbc4-121">Usage</span><span class="sxs-lookup"><span data-stu-id="0fbc4-121">Usage</span></span>

<span data-ttu-id="0fbc4-122">Le mode de recherche est conçu pour les chercheurs universitaires et industriels qui explorent de nouvelles idées dans les domaines de la Vision par ordinateur et de la robotique.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="0fbc4-123">Elle n’est pas destinée aux applications déployées dans des environnements d’entreprise ou disponibles via le Microsoft Store ou d’autres canaux de distribution.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="0fbc4-124">En outre, Microsoft ne garantit pas que le mode de recherche ou les fonctionnalités équivalentes seront pris en charge dans les futures mises à jour du matériel ou du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="0fbc4-125">Toutefois, cela ne vous empêche pas de l’utiliser pour développer et tester de nouvelles idées !</span><span class="sxs-lookup"><span data-stu-id="0fbc4-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="0fbc4-126">Sécurité et performances</span><span class="sxs-lookup"><span data-stu-id="0fbc4-126">Security and performance</span></span>

<span data-ttu-id="0fbc4-127">N’oubliez pas que l’activation du mode de recherche utilise davantage de batterie que l’utilisation de la mise à l’aide du système HoloLens 2 dans des conditions normales.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-127">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="0fbc4-128">Cela est vrai même si l’application qui utilise les fonctionnalités du mode de recherche n’est pas en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-128">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="0fbc4-129">L’activation de ce mode peut également réduire la sécurité globale de votre appareil, car les applications peuvent avoir recours à des données de capteur.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="0fbc4-130">Vous trouverez plus d’informations sur la sécurité des appareils dans le [Forum aux questions sur la sécurité HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="0fbc4-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="0fbc4-131">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="0fbc4-131">Device support</span></span>
<table><span data-ttu-id="0fbc4-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="0fbc4-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="0fbc4-133"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="0fbc4-133"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="0fbc4-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0fbc4-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="0fbc4-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="0fbc4-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="0fbc4-136">Caméras de suivi des têtes</span><span class="sxs-lookup"><span data-stu-id="0fbc4-136">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="0fbc4-137">✔️</span><span class="sxs-lookup"><span data-stu-id="0fbc4-137">✔️</span></span></td>
        <td><span data-ttu-id="0fbc4-138">✔️</span><span class="sxs-lookup"><span data-stu-id="0fbc4-138">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0fbc4-139">Caméra de profondeur & IR</span><span class="sxs-lookup"><span data-stu-id="0fbc4-139">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="0fbc4-140">✔️</span><span class="sxs-lookup"><span data-stu-id="0fbc4-140">✔️</span></span></td>
        <td><span data-ttu-id="0fbc4-141">✔️</span><span class="sxs-lookup"><span data-stu-id="0fbc4-141">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0fbc4-142">Accéléromètre</span><span class="sxs-lookup"><span data-stu-id="0fbc4-142">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="0fbc4-143">✔️</span><span class="sxs-lookup"><span data-stu-id="0fbc4-143">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0fbc4-144">Gyroscope</span><span class="sxs-lookup"><span data-stu-id="0fbc4-144">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="0fbc4-145">✔️</span><span class="sxs-lookup"><span data-stu-id="0fbc4-145">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0fbc4-146">Magnétomètre</span><span class="sxs-lookup"><span data-stu-id="0fbc4-146">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="0fbc4-147">✔️</span><span class="sxs-lookup"><span data-stu-id="0fbc4-147">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="0fbc4-148">Activation du mode de recherche (HoloLens 1re génération et HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="0fbc4-148">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="0fbc4-149">Le mode de recherche est une extension du mode développeur.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-149">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="0fbc4-150">Avant de commencer, les fonctionnalités de développement de l’appareil doivent être activées pour accéder aux paramètres du mode de recherche :</span><span class="sxs-lookup"><span data-stu-id="0fbc4-150">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="0fbc4-151">Ouvrez le **menu démarrer > paramètres** , puis sélectionnez **mises à jour** .</span><span class="sxs-lookup"><span data-stu-id="0fbc4-151">Open **Start Menu > Settings** and select **Updates** .</span></span>
* <span data-ttu-id="0fbc4-152">Sélectionnez **pour les développeurs** et activer le **mode développeur** .</span><span class="sxs-lookup"><span data-stu-id="0fbc4-152">Select **For Developers** and enable **Developer Mode** .</span></span>
* <span data-ttu-id="0fbc4-153">Faites défiler la liste et activez le **portail d’appareil** .</span><span class="sxs-lookup"><span data-stu-id="0fbc4-153">Scroll down and enable **Device Portal** .</span></span>

<span data-ttu-id="0fbc4-154">Une fois les fonctionnalités du développeur activées, [Connectez-vous au portail de l’appareil](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) pour activer les fonctionnalités du mode de recherche :</span><span class="sxs-lookup"><span data-stu-id="0fbc4-154">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="0fbc4-155">Accédez à **système > le mode de recherche** dans le portail de l' **appareil** .</span><span class="sxs-lookup"><span data-stu-id="0fbc4-155">Go to **System > Research Mode** in the **Device Portal** .</span></span>
* <span data-ttu-id="0fbc4-156">Sélectionnez **autoriser l’accès au flux de capteur** .</span><span class="sxs-lookup"><span data-stu-id="0fbc4-156">Select **Allow access to sensor stream** .</span></span>
* <span data-ttu-id="0fbc4-157">Redémarrez l’appareil à partir de l’élément de menu **Power** situé en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-157">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="0fbc4-158">Une fois que vous avez redémarré l’appareil, les applications chargées via le portail de l' **appareil** peuvent accéder aux flux en mode de recherche.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-158">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="0fbc4-159">![Onglet mode de recherche du portail de l’appareil HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="0fbc4-159">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="0fbc4-160">*Fenêtre du mode de recherche dans le portail d’appareils HoloLens*</span><span class="sxs-lookup"><span data-stu-id="0fbc4-160">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fbc4-161">Le mode de recherche pour HoloLens 2 est disponible à partir de la build 19041,1356.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-161">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="0fbc4-162">Si vous avez besoin d’accéder à une version antérieure, inscrivez-vous à notre programme [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="0fbc4-162">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="0fbc4-163">Utilisation des données de capteur dans vos applications</span><span class="sxs-lookup"><span data-stu-id="0fbc4-163">Using sensor data in your apps</span></span>

<span data-ttu-id="0fbc4-164">Les applications peuvent accéder aux données de flux de capteur de la même façon que les flux de photos et les vidéos de caméra vidéo sont accessibles par le biais de [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="0fbc4-164">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="0fbc4-165">Toutes les API qui fonctionnent pour le développement HoloLens sont également disponibles en mode de recherche.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-165">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="0fbc4-166">En particulier, l’application sait précisément où HoloLens se trouve dans l’espace 6DoF à chaque fois que la capture de l’image du capteur est terminée.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-166">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="0fbc4-167">Vous trouverez des exemples d’applications sur l’accès aux différents flux en mode de recherche, à l’aide des [fonctions intrinsèques et extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), et l’enregistrement de flux dans les dépôts de mode de recherche respectifs :</span><span class="sxs-lookup"><span data-stu-id="0fbc4-167">You can find sample applications on accessing the various Research Mode streams, using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams in the respective Research Mode repos:</span></span>
* [<span data-ttu-id="0fbc4-168">HoloLens (1ère génération)</span><span class="sxs-lookup"><span data-stu-id="0fbc4-168">HoloLens (1st gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="0fbc4-169">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0fbc4-169">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="0fbc4-170">Support</span><span class="sxs-lookup"><span data-stu-id="0fbc4-170">Support</span></span>

<span data-ttu-id="0fbc4-171">Pour HoloLens (1ère génération), utilisez le [suivi des problèmes](https://github.com/Microsoft/HololensForCV/issues) dans le référentiel HoloLensForCV pour publier des commentaires et effectuer le suivi des problèmes connus.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-171">For HoloLens (1st gen), please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="0fbc4-172">Pour HoloLens 2, utilisez le [suivi des problèmes](https://github.com/microsoft/HoloLens2ForCV/issues) dans le référentiel HoloLens2ForCV pour publier des commentaires et effectuer le suivi des problèmes connus.</span><span class="sxs-lookup"><span data-stu-id="0fbc4-172">For HoloLens 2, please use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fbc4-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fbc4-173">See also</span></span>

* [<span data-ttu-id="0fbc4-174">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="0fbc4-174">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="0fbc4-175">HoloLensForCV GitHub référentiel</span><span class="sxs-lookup"><span data-stu-id="0fbc4-175">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="0fbc4-176">HoloLens2ForCV GitHub référentiel</span><span class="sxs-lookup"><span data-stu-id="0fbc4-176">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="0fbc4-177">Utilisation du portail d’appareil Windows</span><span class="sxs-lookup"><span data-stu-id="0fbc4-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
