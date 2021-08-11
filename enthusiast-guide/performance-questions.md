---
title: Questions fréquentes relatives aux performances
description: performances Windows Mixed Reality résolution des problèmes qui vont au-delà de notre documentation de support technique standard.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, dépannage, erreurs, aide, Support, performances
appliesto:
- Windows 10
ms.openlocfilehash: 6754923a07d4c75c6f0f44aad07c5d3c55c28ae4673900531d8a4af663d9e7c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219415"
---
# <a name="performance-faqs"></a>Questions fréquentes relatives aux performances

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60-hz-or-90-hz-framerate"></a>le rendu de mon casque est-il Windows Mixed Reality à 60 hz ou 90 hz.

Si vous disposez d’un GPU discret avec des ports HDMI 2,0 et un processeur avec quatre cœurs physiques ou plus, vous devez obtenir 90 Hz. Pour confirmer, sélectionnez le **portail de l’appareil > onglet performances** .

Remarque : Si votre GPU n’a qu’une sortie HDMI 1,4, vous pouvez utiliser un adaptateur DisplayPort à [hdmi 2,0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) comme solution de contournement.

remarque : les paramètres de qualité visuelle dans « affichage du casque » affectent uniquement le rendu de l’expérience d’hébergement Windows Mixed Reality.

## <a name="my-pc-is-running-slowly"></a>Mon PC fonctionne lentement

Le système peut être lent pour de nombreuses raisons, en règle générale ne durer que quelques secondes. Si vous rencontrez ce problème sur de longues périodes de temps :

1. Fermez toutes les applications inutilisées sur le bureau.
2. Assurez-vous que votre ordinateur portable est branché à une source d’alimentation.
3. Assurez-vous que le PC n’est pas en état de préchauffage.
4. réduisez la qualité visuelle de votre Windows Mixed Reality page d’hébergement.
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
* ajustez les paramètres visuels de votre casque en **Paramètres > de la réalité mixte > affichage du casque**. Lorsque la « qualité visuelle » est définie sur « automatique », l’expérience de réalité mixte pour votre ordinateur est sélectionnée automatiquement. Pour plus d’informations visuelles, définissez « qualité visuelle » sur « haute ». Si vos visuels sont saccadés, sélectionnez un paramètre inférieur.
* Réglez le bouton d’étalonnage du casque pour vous assurer que les lentilles sont réglées sur la distance appropriée entre vos élèves (« IPD »). Si vous ne connaissez pas votre IPD, un Optometrist peut le mesurer pour vous ou utiliser un site Web conçu pour mesurer l’IPD. si le casque n’a pas de bouton d’étalonnage, sélectionnez **Paramètres > la réalité mixte > affichage du casque** et réglez le « contrôle d’étalonnage ».
* Si vous utilisez un adaptateur USB-C ou DisplayPort vers HDMI, essayez-en un autre. Voir les [adaptateurs recommandés.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Déconnectez les moniteurs supplémentaires qui peuvent être connectés à la carte graphique de votre PC.
* essayez différentes applications de réalité mixte dans le magasin de Windows, certaines peuvent fonctionner mieux avec la configuration de votre ordinateur.
