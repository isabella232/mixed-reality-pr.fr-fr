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
# <a name="updating-shaders"></a>Mise à jour des nuanceurs

À partir de la version 2.6.0, les nuanceurs MRTK sont mis à niveau via le MRTK. Fichier shaderers. Sentinel. Lors de la mise à niveau vers une nouvelle version de MRTK, le message suivant peut s’afficher.

![Invite mettre à jour les nuanceurs](../images/tools/UpdateShaderPrompt.png)

La sélection de l’option **Oui** indique à MRTK de remplacer le contenu des nuanceurs MRTK des **éléments** multimédias  >    >   par la dernière version. La sélection de l’option **non** permet de conserver les fichiers en cours. L’option **Ignorer** crée un fichier ( `IgnoreUpdateCheck.sentinel` ) dans  >    >  les **nuanceurs** MRTK actifs, ce qui supprime les futures vérifications des mises à jour de nuanceur.

> [!IMPORTANT]
> Lors du remplacement des fichiers du nuanceur, toute modification personnalisée est perdue. Veillez à sauvegarder tous les fichiers de nuanceur modifiés avant de procéder à la mise à niveau.
>
> Si le projet a été configuré pour utiliser le pipeline de rendu universel (URP)-anciennement le pipeline de rendu léger (LWRP), relancez la mise à niveau des utilitaires de la boîte à outils de la **réalité mixte** >  >
>  **MRTK nuanceur standard pour le pipeline de rendu léger**.

Il est également possible de rechercher des mises à jour de nuanceur à tout moment à l’aide des utilitaires de la **boîte à outils de réalité mixte**  >    >  **pour vérifier les mises à jour de nuanceur** dans la barre de menus de l’éditeur Unity.

![Rechercher les mises à jour de nuanceur](../images/tools/ShaderUpdateMenu.png)

**Rechercher les mises à jour de nuanceur** ignore le `IgnoreUpdateCheck.sentinel` fichier et permet la mise à jour du nuanceur à la demande.

> [!NOTE]
> La vérification des mises à jour du nuanceur n’est pas nécessaire lors de l’importation des fichiers MRTK. pour Unity.
