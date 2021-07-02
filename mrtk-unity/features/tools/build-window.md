---
title: Fenêtre Build
description: Documentation sur l’utilisation de la fenêtre de génération dans MRTK pour Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, générer, fenêtre de génération, outils
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176152"
---
# <a name="build-window"></a><span data-ttu-id="3982c-104">Fenêtre Build</span><span class="sxs-lookup"><span data-stu-id="3982c-104">Build window</span></span>
![Générer & déployer le Flow](images/MRTK_BuildWindow0.png)

<span data-ttu-id="3982c-106">La fenêtre de génération de MRTK facilite la création de & déployer vos projets MRTK-Unity.</span><span class="sxs-lookup"><span data-stu-id="3982c-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="3982c-107">avec un simple clic sur un bouton, vous pouvez générer un projet unity et générer Visual Studio solution (. SLN), le package d’application UWP (. APPX) et installer le package d’application sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="3982c-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="3982c-108">Options de build Unity</span><span class="sxs-lookup"><span data-stu-id="3982c-108">Unity Build Options</span></span>
![Fenêtre de génération-options de build Unity 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="3982c-110">ces scènes proviennent de la Paramètres de Build unity.</span><span class="sxs-lookup"><span data-stu-id="3982c-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="3982c-111">Vous pouvez modifier le type d’appareil cible à l’aide du menu déroulant.</span><span class="sxs-lookup"><span data-stu-id="3982c-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="3982c-112">Options de build AppX</span><span class="sxs-lookup"><span data-stu-id="3982c-112">Appx Build Options</span></span>
![Fenêtre de génération-options de build AppX 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="3982c-114">cet onglet affiche la configuration de la solution Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3982c-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="3982c-115">pour activer la fonctionnalité d’entrée de suivi oculaire de HoloLens 2, activez la case à cocher **capacité d’entrée en regard** .</span><span class="sxs-lookup"><span data-stu-id="3982c-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="3982c-116">vous pouvez affecter le fichier. glb dans le champ **modèle d’Lanceur d’application 3d** pour l’icône du lanceur d’applications 3d personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3982c-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="3982c-117">Pour plus d’informations, consultez [instructions de conception du lanceur d’applications en 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) .</span><span class="sxs-lookup"><span data-stu-id="3982c-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="3982c-118">Par défaut, l' **incrémentation automatique** est vérifiée dans les options de contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="3982c-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="3982c-119">Les versions d’AppX seront automatiquement incrémentées.</span><span class="sxs-lookup"><span data-stu-id="3982c-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="3982c-120">Options de déploiement</span><span class="sxs-lookup"><span data-stu-id="3982c-120">Deploy Options</span></span>
![Fenêtre de génération-options de déploiement 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="3982c-122">Dans cet onglet, vous pouvez vous connecter à l’appareil en entrant un nom d’utilisateur et un mot de passe pour le portail de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="3982c-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="3982c-123">En bas de la page, vous trouverez la liste des packages d’application qui ont été créés.</span><span class="sxs-lookup"><span data-stu-id="3982c-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

