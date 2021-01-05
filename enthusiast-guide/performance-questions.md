---
title: Questions fréquentes relatives aux performances
description: Résolution des problèmes de performances de Windows Mixed realisation qui va au-delà de notre documentation de support technique standard.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, performances
appliesto:
- Windows 10
ms.openlocfilehash: dea2e81d53bfbb16a8803fc3f7c4e011741dfce6
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726000"
---
# <a name="performance-faqs"></a>Questions fréquentes relatives aux performances

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60-hz-or-90-hz-framerate"></a>Le rendu du casque Windows Mixed Reality est-il à 60 Hz ou 90 Hz.

Si vous disposez d’un GPU discret avec des ports HDMI 2,0 et un processeur avec quatre cœurs physiques ou plus, vous devez obtenir 90 Hz. Pour confirmer, sélectionnez le **portail de l’appareil > onglet performances** .

Remarque : Si votre GPU n’a qu’une sortie HDMI 1,4, vous pouvez utiliser un adaptateur DisplayPort à [hdmi 2,0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) comme solution de contournement.

Remarque : les paramètres de qualité visuelle dans « affichage du casque » affectent uniquement le rendu de l’expérience d’hébergement Windows Mixed Reality.

## <a name="my-pc-is-running-slowly"></a>Mon PC fonctionne lentement

Le système peut être lent pour de nombreuses raisons, en règle générale ne durer que quelques secondes. Si vous rencontrez ce problème sur de longues périodes de temps :

1. Fermez toutes les applications inutilisées sur le bureau.
2. Assurez-vous que votre ordinateur portable est branché à une source d’alimentation.
3. Assurez-vous que le PC n’est pas en état de préchauffage.
4. Réduisez la qualité visuelle dans votre page d’hébergement Windows Mixed Reality.
5. Vérifiez que vous disposez des derniers [pilotes graphiques](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) pour votre PC.

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Mon PC est en état de préchauffage lorsque j’exécute les expériences de réalité mixte. Comment faire le garder refroidi

1. Vérifiez que la batterie est chargée et que la source d’alimentation est branchée.
2. Assurez-vous que les ventilateurs du PC ne sont pas bloqués.
3. Utilisez l’ordinateur dans un environnement relativement froid.
4. Assurez-vous qu’il n’existe aucune source de chaleur (par exemple, le soleil ou les orifices de chauffage) pointé sur le PC.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Mes éléments visuels sont saccadés, se chargent lentement ou ne semblent pas corrects

* Assurez-vous que votre casque est branché à la bonne carte graphique sur votre PC. Certains PC ont des cartes graphiques intégrées et discrètes. La carte discrète offre généralement les meilleures performances. [En savoir plus sur le matériel PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Fermez les applications inutilisées sur votre bureau.
* Assurez-vous que votre casque est ajusté (déplacez-le vers le bas et vers le haut, ou à gauche et à droite pour ajuster).
* Réglez les paramètres visuels de votre casque dans **paramètres > la réalité mixte > affichage du casque**. Lorsque la « qualité visuelle » est définie sur « automatique », l’expérience de réalité mixte pour votre ordinateur est sélectionnée automatiquement. Pour plus d’informations visuelles, définissez « qualité visuelle » sur « haute ». Si vos visuels sont saccadés, sélectionnez un paramètre inférieur.
* Réglez le bouton d’étalonnage du casque pour vous assurer que les lentilles sont réglées sur la distance appropriée entre vos élèves (« IPD »). Si vous ne connaissez pas votre IPD, un Optometrist peut le mesurer pour vous ou utiliser un site Web conçu pour mesurer l’IPD. Si le casque n’a pas de bouton d’étalonnage, sélectionnez **paramètres > réalité mixte > affichage du casque** et réglez le « contrôle d’étalonnage ».
* Si vous utilisez un adaptateur USB-C ou DisplayPort vers HDMI, essayez-en un autre. Voir les [adaptateurs recommandés.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Déconnectez les moniteurs supplémentaires qui peuvent être connectés à la carte graphique de votre PC.
* Essayez différentes applications de réalité mixte à partir du Windows Store, certaines peuvent fonctionner mieux avec la configuration de votre ordinateur.
