---
title: Outil de mise à jour du nuanceur
description: Documentation sur la mise à jour des nuanceurs standard MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: ed9f9fa5e6337850f31ecce9d07bc82a8ea12060
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145131"
---
# <a name="updating-shaders"></a><span data-ttu-id="1b4f1-104">Mise à jour des nuanceurs</span><span class="sxs-lookup"><span data-stu-id="1b4f1-104">Updating Shaders</span></span>

<span data-ttu-id="1b4f1-105">À partir de la version 2.6.0, les nuanceurs MRTK sont mis à niveau via le MRTK. Fichier shaderers. Sentinel.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="1b4f1-106">Lors de la mise à niveau vers une nouvelle version de MRTK, le message suivant peut s’afficher.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![Invite mettre à jour les nuanceurs](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="1b4f1-108">La sélection de l’option **Oui** indique à MRTK de remplacer le contenu des nuanceurs MRTK des **éléments** multimédias  >    >   par la dernière version.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="1b4f1-109">La sélection de l’option **non** permet de conserver les fichiers en cours.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="1b4f1-110">L’option **Ignorer** crée un fichier ( `IgnoreUpdateCheck.sentinel` ) dans  >    >  les **nuanceurs** MRTK actifs, ce qui supprime les futures vérifications des mises à jour de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b4f1-111">Lors du remplacement des fichiers du nuanceur, toute modification personnalisée est perdue.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="1b4f1-112">Veillez à sauvegarder tous les fichiers de nuanceur modifiés avant de procéder à la mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="1b4f1-113">Si le projet a été configuré pour utiliser le pipeline de rendu universel (URP)-anciennement le pipeline de rendu léger (LWRP), relancez la mise à niveau des utilitaires de la boîte à outils de la **réalité mixte** >  >
>  **MRTK nuanceur standard pour le pipeline de rendu léger**.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="1b4f1-114">Il est également possible de rechercher des mises à jour de nuanceur à tout moment à l’aide des utilitaires de la **boîte à outils de réalité mixte**  >    >  **pour vérifier les mises à jour de nuanceur** dans la barre de menus de l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-114">At is also possible to check for shader updates at any time using **Mixed Reality Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![Rechercher les mises à jour de nuanceur](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="1b4f1-116">**Rechercher les mises à jour de nuanceur** ignore le `IgnoreUpdateCheck.sentinel` fichier et permet la mise à jour du nuanceur à la demande.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="1b4f1-117">La vérification des mises à jour du nuanceur n’est pas nécessaire lors de l’importation des fichiers MRTK. pour Unity.</span><span class="sxs-lookup"><span data-stu-id="1b4f1-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
