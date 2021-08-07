---
title: Framework et runtime
description: Informations relatives à l’infrastructure et au runtime dans MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: f2391ab0c67880c8902092be6fcecefcf30f008c7f31ea76879d399e35e1491b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212670"
---
# <a name="framework-and-runtime"></a>Framework et runtime

## <a name="changes-to-the-scene"></a>Modifications apportées à la scène

Pour utiliser la boîte à outils, une instance du script MixedRealityToolkit doit se trouver dans votre scène.
pour en ajouter un, utilisez l’option de menu : Shared Computer Toolkit de la réalité mixte-> ajouter à la scène et configurer. Cette instance est responsable de l’inscription, de la mise à jour et de la suppression des services. C’est également là que votre profil de configuration est choisi.

Outre l’ajout du GameObject MRTK à la scène, l’option de menu permet également :

- Ajoutez le MixedRealityPlayspace, qui est utilisé par de nombreux autres composants MRTK pour être à l’origine des transformations d’espace universelles et locales.
- Déplacez l’appareil photo principal en tant qu’enfant du MixedRealityPlayspace (et ajoutez également des scripts d’entrée et de regard pour l’appareil photo principal, qui aident à UnityUI et aux fonctionnalités d’entrée de regard).

## <a name="mixedrealitytoolkit-object-and-runtime"></a>Objet MixedRealityToolkit et Runtime

Le MRTK possède plusieurs services principaux. Une coordonnée les unes avec les autres ; d’autres sont indépendantes.
Tous partagent le même cycle de vie : le démarrage, l’inscription, la mise à jour et la destruction, et ce cycle de vie se distingue du cycle de vie monocomportement d’Unity. Cette [publication de taille moyenne](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explique quelques-unes des raisons de cette approche. MRTK possède un objet unique qui gère la vie et l’exécution de ses services.

Cette entité garantit que :

- Lorsque le jeu démarre, la découverte et l’initialisation des services s’effectuent dans un ordre prédéfini.
- Il fournit un mécanisme permettant aux services de s’inscrire eux-mêmes (par exemple, « je prend en charge ce service ! ») et pour d’autres appelants d’obtenir un blocage de ces services.
- Il fournit les appels Update ()/LateUpdate () et les transfère vers les différents services (par exemple, via UpdateAllServices/LateUpdateAllServices).
