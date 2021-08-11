---
title: FAQ sur le suivi
description: le suivi Windows Mixed Reality la résolution des problèmes qui vont au-delà de notre documentation de support technique standard.
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, dépannage, erreurs, aide, Support, suivi
ms.openlocfilehash: fe5462a53de7b196db37edbbf0e56199a17c4c99b54ea1e7d9edf72e0845c9e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199475"
---
# <a name="tracking-faqs"></a>FAQ sur le suivi

## <a name="my-headset-has-stopped-tracking"></a>Mon casque a arrêté le suivi

Assurez-vous que les lumières sont allumées et qu’il n’y a aucun obstacle aux caméras de suivi à l’intérieur de votre casque. Si le suivi est perdu, la reprise peut prendre quelques secondes. redémarrez le portail Windows Mixed Reality le suivi ne redémarre pas.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Je peux me pencher, mais je ne peux pas le traduire (je suis bloqué dans 3DOF)

Cela signifie que le système de suivi ne peut pas générer de pose, ou que l’application s’est arrêtée en utilisant de nouvelles données de pose à rendre. Pour résoudre le problème :

* Assurez-vous que la salle a suffisamment de lumière.
* Assurez-vous que la salle dispose de suffisamment de détails pour effectuer le suivi.
* débranchez l’appareil, fermez Windows Mixed Reality, puis reconnectez l’appareil.
* Si le message persiste, contactez le [support](https://support.microsoft.com/) technique

## <a name="the-view-in-the-hmd-is-frozen"></a>La vue dans le HMD est figée

Cela signifie généralement que l’application ou un composant de niveau système a échoué. Essayez d’effectuer les opérations suivantes :

1. Appuyez sur le bouton « démarrage » pour fermer l’application.
2. Débranchez l’appareil, fermez le calcul MRP, puis reconnectez l’appareil.
3. Redémarrez le PC.

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>Le monde court figée rapidement et incliné ou renversé avant de revenir à la normale.

Cela peut être dû à une application ou à un composant de niveau système qui atteint une erreur irrécupérable ou un manque temporaire de mémoire ou de ressources processeur. Pour vérifier :

1. Ouvrez le gestionnaire des tâches et assurez-vous qu’au moins 20% du processeur sont libres, 400 Mo de mémoire sont disponibles et que les e/s disque doivent être inférieures à 80%.
2. accédez à **observateur d’événements > Windows journaux > Application** pour rechercher les erreurs survenues au bout du temps du gel. recherchez tout ce qui fait référence aux capteurs HoloLens, à la réalité mixte ou à l’application que vous exécutiez pendant cette période. Ces journaux peuvent expliquer ce qui a provoqué l’échec.
3. Si le problème persiste, redémarrez le PC.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>Le monde a basculé momentanément et est revenu à la normale

Cela est généralement dû à des erreurs lors de l’obtention de données de capteur à partir du casque pour informer les algorithmes de suivi. Si cela se produit fréquemment :

1. Branchez le casque sur un port USB 3,0 différent.
2. Branchez le casque directement sur le PC plutôt que sur un concentrateur USB 3,0.
3. Si le problème persiste, contactez le [support](https://support.microsoft.com/)technique.

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>Le monde est incliné, mais je peux naviguer et parcourir les Windows Mixed Reality

si des erreurs de données de capteur sont consignées dans les données d’environnement sur votre ordinateur, les Windows Mixed Reality peuvent être inclinées définitivement. Pour résoudre ce problème :

1. débranchez le casque, fermez Windows Mixed Reality et rebranchez le casque.
2. Redémarrez le PC.
3. Effacez les données de votre environnement.