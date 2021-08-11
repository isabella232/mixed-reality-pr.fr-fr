---
ms.openlocfilehash: ce1f02bd2846cadc4e970fef738fb4b46bc3a09f10742b820a0998491c590c80
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204207"
---
# <a name="all-platforms"></a>[Toutes les plateformes](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>Activation du plug-in du contrôleur de mouvement HP 

Le profil d’interaction et les mappages de contrôleur se trouvent dans le plug-in du contrôleur de mouvement HP, qui doit être activé pour exposer les mappages du contrôleur au système d’entrée non réel.

![Activation du plug-in OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>Configuration de Startup et HMDPluginPriority

L’entrée de SteamVR à l’aide de présente quelques différences.  Lors de la configuration du projet, assurez-vous d’abord qu’il utilise le nouveau système d’entrée de SteamVR en ajoutant **VR. SteamVR. EnableVRInput = 1** à la section **Startup** dans le **moteur/config/ConsoleVariables.ini**.  Ce fichier ini se trouve dans le répertoire d’installation du moteur, et non dans le répertoire du projet.

![Mise à jour de la configuration de démarrage](../images/reverb-g2-img-07.png)

Le plug-in du contrôleur de mouvement HP active OpenXR.  Si vous n’utilisez pas OpenXR, vous devrez modifier le HMDPluginPriority de SteamVR dans BaseEngine.ini dans le même répertoire que ConsoleVariables.ini.  Modifiez la valeur SteamVR pour qu’elle soit supérieure à la valeur OpenXRHMD.

![Mise à jour de la configuration HMDPluginPriority](../images/reverb-g2-img-08.png)


