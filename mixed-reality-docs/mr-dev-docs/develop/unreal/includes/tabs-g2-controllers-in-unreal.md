---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638731"
---
# <a name="all-platforms"></a>[Toutes les plateformes](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>Activation du plug-in du contrôleur de mouvement HP 

Le profil d’interaction et les mappages de contrôleur se trouvent dans le plug-in du contrôleur de mouvement HP, qui doit être activé pour exposer les mappages du contrôleur au système d’entrée non réel.

![Activation du plug-in OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>Configuration de Startup et HMDPluginPriority

L’entrée de SteamVR à l’aide de présente quelques différences.  Lors de la configuration du projet, assurez-vous d’abord qu’il utilise le nouveau système d’entrée de SteamVR en ajoutant **VR. SteamVR. EnableVRInput = 1** à la section **Startup** dans le **moteur/config/ConsoleVariables.ini** .  Ce fichier ini se trouve dans le répertoire d’installation du moteur, et non dans le répertoire du projet.

![Mise à jour de la configuration de démarrage](../images/reverb-g2-img-07.png)

Le plug-in du contrôleur de mouvement HP active OpenXR.  Si vous n’utilisez pas OpenXR, vous devrez modifier le HMDPluginPriority de SteamVR dans BaseEngine.ini dans le même répertoire que ConsoleVariables.ini.  Modifiez la valeur SteamVR pour qu’elle soit supérieure à la valeur OpenXRHMD.

![Mise à jour de la configuration HMDPluginPriority](../images/reverb-g2-img-08.png)


