---
title: FAQ sur le suivi
description: Suivi de la résolution des problèmes de Windows Mixed realisation qui va au-delà de notre documentation de support technique standard.
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, suivi
ms.openlocfilehash: 2634b95cf876a5b540710f80d3dd7f9d48b3bad9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725830"
---
# <a name="tracking-faqs"></a>FAQ sur le suivi

## <a name="my-headset-has-stopped-tracking"></a>Mon casque a arrêté le suivi

Assurez-vous que les lumières sont allumées et qu’il n’y a aucun obstacle aux caméras de suivi à l’intérieur de votre casque. Si le suivi est perdu, la reprise peut prendre quelques secondes. Le suivi du portail Windows Mixed Reality n’est pas redémarré.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Je peux me pencher, mais je ne peux pas le traduire (je suis bloqué dans 3DOF)

Cela signifie que le système de suivi ne peut pas générer de pose, ou que l’application s’est arrêtée en utilisant de nouvelles données de pose à rendre. Pour résoudre le problème :

* Assurez-vous que la salle a suffisamment de lumière.
* Assurez-vous que la salle dispose de suffisamment de détails pour effectuer le suivi.
* Débranchez l’appareil, fermez Windows Mixed Reality, puis reconnectez l’appareil.
* Si le message persiste, contactez le [support](https://support.microsoft.com/) technique

## <a name="the-view-in-the-hmd-is-frozen"></a>La vue dans le HMD est figée

Cela signifie généralement que l’application ou un composant de niveau système a échoué. Essayez d’effectuer les opérations suivantes :

1. Appuyez sur le bouton « démarrage » pour fermer l’application.
2. Débranchez l’appareil, fermez le calcul MRP, puis reconnectez l’appareil.
3. Redémarrez le PC.

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>Le monde court figée rapidement et incliné ou renversé avant de revenir à la normale.

Cela peut être dû à une application ou à un composant de niveau système qui atteint une erreur irrécupérable ou un manque temporaire de mémoire ou de ressources processeur. Pour vérifier :

1. Ouvrez le gestionnaire des tâches et assurez-vous qu’au moins 20% du processeur sont libres, 400 Mo de mémoire sont disponibles et que les e/s disque doivent être inférieures à 80%.
2. Accédez à **observateur d’événements > journaux Windows > application** pour rechercher les erreurs survenues au bout du temps du gel. Recherchez tout ce qui fait référence aux capteurs HoloLens, à la réalité mixte ou à l’application que vous exécutiez pendant cette période. Ces journaux peuvent expliquer ce qui a provoqué l’échec.
3. Si le problème persiste, redémarrez le PC.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>Le monde a basculé momentanément et est revenu à la normale

Cela est généralement dû à des erreurs lors de l’obtention de données de capteur à partir du casque pour informer les algorithmes de suivi. Si cela se produit fréquemment :

1. Branchez le casque sur un port USB 3,0 différent.
2. Branchez le casque directement sur le PC plutôt que sur un concentrateur USB 3,0.
3. Si le problème persiste, contactez le [support](https://support.microsoft.com/)technique.

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>Le monde est incliné, mais je peux naviguer et parcourir Windows Mixed Reality

Si des erreurs de données de capteur sont consignées dans les données d’environnement sur votre ordinateur, cela peut entraîner l’inclinaison de Windows Mixed realisation, parfois de façon permanente. Pour résoudre ce problème :

1. Débranchez le casque, fermez Windows Mixed Reality et rebranchez le casque.
2. Redémarrez le PC.
3. Effacez les données de votre environnement.