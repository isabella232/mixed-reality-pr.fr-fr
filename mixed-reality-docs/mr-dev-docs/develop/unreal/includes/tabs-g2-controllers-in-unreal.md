---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638731"
---
# <a name="all-platforms"></a>[<span data-ttu-id="78be8-101">Toutes les plateformes</span><span class="sxs-lookup"><span data-stu-id="78be8-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="78be8-102">Activation du plug-in du contrôleur de mouvement HP</span><span class="sxs-lookup"><span data-stu-id="78be8-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="78be8-103">Le profil d’interaction et les mappages de contrôleur se trouvent dans le plug-in du contrôleur de mouvement HP, qui doit être activé pour exposer les mappages du contrôleur au système d’entrée non réel.</span><span class="sxs-lookup"><span data-stu-id="78be8-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![Activation du plug-in OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="78be8-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="78be8-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="78be8-106">Configuration de Startup et HMDPluginPriority</span><span class="sxs-lookup"><span data-stu-id="78be8-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="78be8-107">L’entrée de SteamVR à l’aide de présente quelques différences.</span><span class="sxs-lookup"><span data-stu-id="78be8-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="78be8-108">Lors de la configuration du projet, assurez-vous d’abord qu’il utilise le nouveau système d’entrée de SteamVR en ajoutant **VR. SteamVR. EnableVRInput = 1** à la section **Startup** dans le **moteur/config/ConsoleVariables.ini** .</span><span class="sxs-lookup"><span data-stu-id="78be8-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="78be8-109">Ce fichier ini se trouve dans le répertoire d’installation du moteur, et non dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="78be8-109">This ini is found in the engine install directory, not the project directory.</span></span>

![Mise à jour de la configuration de démarrage](../images/reverb-g2-img-07.png)

<span data-ttu-id="78be8-111">Le plug-in du contrôleur de mouvement HP active OpenXR.</span><span class="sxs-lookup"><span data-stu-id="78be8-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="78be8-112">Si vous n’utilisez pas OpenXR, vous devrez modifier le HMDPluginPriority de SteamVR dans BaseEngine.ini dans le même répertoire que ConsoleVariables.ini.</span><span class="sxs-lookup"><span data-stu-id="78be8-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="78be8-113">Modifiez la valeur SteamVR pour qu’elle soit supérieure à la valeur OpenXRHMD.</span><span class="sxs-lookup"><span data-stu-id="78be8-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![Mise à jour de la configuration HMDPluginPriority](../images/reverb-g2-img-08.png)


