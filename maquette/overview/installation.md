---
title: Installation de maquette
description: Découvrez comment installer et configurer maquette dans VSCode.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototypage, réalité mixte, réalité virtuelle, VR, MR, commentaires, Hub de commentaires, bogues
ms.openlocfilehash: c31f461adbe553a5c10e7acfff3037ea0c2b65caf2bbe63bfc234e067a6369e8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214762"
---
# <a name="installing-maquette"></a>Installation de maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![Installation du logo ](../images/MaquetteIcon.png) MaquetteScript

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
Le développement MaquetteScript s’effectue principalement dans VSCode. MaquetteScript peut s’exécuter à partir d’un script contenu dans des `.mqjs` fichiers et également via une interface d’extension VSCode spéciale. L’intégration entre VSCode et maquette pour activer l’interface d’extension s’effectue à l’aide d’une extension VSCode MaquetteScript.

## <a name="installing-the-vscode-extension"></a>Installation de l’extension VSCode

* Téléchargez et installez [VSCode](https://code.visualstudio.com). 

l’extension javascript Maquette se trouve dans la place de [marché Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).

* Exécutez la [procédure d’installation de l’extension](vscode:extension/ms-maquette.vscode-maquette-javascript).

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>Activation des scripts

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

Pour rendre les scripts accessibles pendant la version préliminaire :

* Placez un fichier portant le nom `scripting.enabled` dans le répertoire des documents utilisateurs pour maquette dans : `~/Documents/Maquette/Settings` .

Après l’installation, les scripts sont désactivés par défaut pour des raisons de sécurité.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* Pour activer l’exécution du script, activez-le sous l’onglet principal de la fenêtre associée ou dans le fichier de paramètres JSON.

![Activation des scripts dans VS Code](images/IntroductionEnableScripting.png)


