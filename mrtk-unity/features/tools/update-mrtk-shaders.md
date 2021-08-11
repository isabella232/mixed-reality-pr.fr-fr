---
title: Outil de mise à jour du nuanceur
description: Documentation sur la mise à jour des nuanceurs standard MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 9ed8a1e439b2bf911d8144a90259d99bf38b12e0404d9ad3365152bed633042c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197065"
---
# <a name="updating-shaders"></a>Mise à jour des nuanceurs

À partir de la version 2.6.0, les nuanceurs MRTK sont mis à niveau via le MRTK. Fichier shaderers. Sentinel. Lors de la mise à niveau vers une nouvelle version de MRTK, le message suivant peut s’afficher.

![Invite mettre à jour les nuanceurs](../images/tools/UpdateShaderPrompt.png)

La sélection de l’option **Oui** indique à MRTK de remplacer le contenu des nuanceurs MRTK des **éléments** multimédias  >    >   par la dernière version. La sélection de l’option **non** permet de conserver les fichiers en cours. L’option **Ignorer** crée un fichier ( `IgnoreUpdateCheck.sentinel` ) dans  >    >  les **nuanceurs** MRTK actifs, ce qui supprime les futures vérifications des mises à jour de nuanceur.

> [!IMPORTANT]
> Lors du remplacement des fichiers du nuanceur, toute modification personnalisée est perdue. Veillez à sauvegarder tous les fichiers de nuanceur modifiés avant de procéder à la mise à niveau.
>
> si le projet a été configuré pour utiliser le pipeline de rendu universel (URP)-anciennement le pipeline de rendu léger (LWRP), relancez la **réalité mixte** > **Shared Computer Toolkit** > **utilitaires** >
>  **mettre à niveau le nuanceur Standard MRTK pour le pipeline de rendu léger**.

il est également possible de rechercher des mises à jour de nuanceur à tout moment à l’aide de la **réalité mixte**  >  **Shared Computer Toolkit**  >  **utilitaires**  >  **recherchent les mises à jour de nuanceur** dans la barre de menus de l’éditeur unity.

![Rechercher les mises à jour de nuanceur](../images/tools/ShaderUpdateMenu.png)

**Rechercher les mises à jour de nuanceur** ignore le `IgnoreUpdateCheck.sentinel` fichier et permet la mise à jour du nuanceur à la demande.

> [!NOTE]
> La vérification des mises à jour du nuanceur n’est pas nécessaire lors de l’importation des fichiers MRTK. pour Unity.
