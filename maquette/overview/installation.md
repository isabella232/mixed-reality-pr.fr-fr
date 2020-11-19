---
title: Installation de maquette
description: Découvrez comment installer et configurer maquette dans VSCode.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, maquette, prototypage, réalité mixte, réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935362"
---
# <a name="installing-maquette"></a><span data-ttu-id="397cb-104">Installation de maquette</span><span class="sxs-lookup"><span data-stu-id="397cb-104">Installing Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text. -->
<span data-ttu-id="397cb-105">![Installation du logo ](../images/MaquetteIcon.png) MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="397cb-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Installation</span></span>

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
<span data-ttu-id="397cb-106">Le développement MaquetteScript s’effectue principalement dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="397cb-106">MaquetteScript development is primarily done within VSCode.</span></span> <span data-ttu-id="397cb-107">MaquetteScript peut s’exécuter à partir d’un script contenu dans des `.mqjs` fichiers et également via une interface d’extension VSCode spéciale.</span><span class="sxs-lookup"><span data-stu-id="397cb-107">MaquetteScript can run from script contained in `.mqjs` files and also via a special VSCode extension interface.</span></span> <span data-ttu-id="397cb-108">L’intégration entre VSCode et maquette pour activer l’interface d’extension s’effectue à l’aide d’une extension VSCode MaquetteScript.</span><span class="sxs-lookup"><span data-stu-id="397cb-108">Integration between VSCode and Maquette to enable the extension interface is accomplished with a MaquetteScript VSCode extension.</span></span>

## <a name="installing-the-vscode-extension"></a><span data-ttu-id="397cb-109">Installation de l’extension VSCode</span><span class="sxs-lookup"><span data-stu-id="397cb-109">Installing the VSCode Extension</span></span>

* <span data-ttu-id="397cb-110">Téléchargez et installez [VSCode](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="397cb-110">Download and install [VSCode](https://code.visualstudio.com).</span></span> 

<span data-ttu-id="397cb-111">L’extension JavaScript maquette se trouve dans [le Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="397cb-111">The Maquette javascript extension is in [the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span></span>

* <span data-ttu-id="397cb-112">Exécutez la [procédure d’installation de l’extension](vscode:extension/ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="397cb-112">Run the [installation procedure for the extension](vscode:extension/ms-maquette.vscode-maquette-javascript).</span></span>

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a><span data-ttu-id="397cb-113">Activation des scripts</span><span class="sxs-lookup"><span data-stu-id="397cb-113">Enabling Scripting</span></span>

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

<span data-ttu-id="397cb-114">Pour rendre les scripts accessibles pendant la version préliminaire :</span><span class="sxs-lookup"><span data-stu-id="397cb-114">To make scripting accessible during pre-release:</span></span>

* <span data-ttu-id="397cb-115">Placez un fichier portant le nom `scripting.enabled` dans le répertoire des documents utilisateurs pour maquette dans : `~/Documents/Maquette/Settings` .</span><span class="sxs-lookup"><span data-stu-id="397cb-115">Put a file with the name `scripting.enabled` in the Users Documents directory for Maquette in: `~/Documents/Maquette/Settings`.</span></span>

<span data-ttu-id="397cb-116">Après l’installation, les scripts sont désactivés par défaut pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="397cb-116">After installation, scripting will be disabled by default for security reasons.</span></span>

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* <span data-ttu-id="397cb-117">Pour activer l’exécution du script, activez-le sous l’onglet principal de la fenêtre associée ou dans le fichier de paramètres JSON.</span><span class="sxs-lookup"><span data-stu-id="397cb-117">To enable execution of script, turn it ON in the main tab of the companion window or in the json settings file.</span></span>

![Activation des scripts dans VS Code](images/IntroductionEnableScripting.png)


