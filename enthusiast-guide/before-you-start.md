---
title: Avant de commencer
description: Comment s’assurer que votre ordinateur est compatible avec, et prêt pour, Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, compatible, compatibilité, prise en main, configuration, PC, configuration système requise
appliesto:
- Windows 10
ms.openlocfilehash: c76f670230a4a19b53b7e8f938b13e79bb7c8db7
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174448"
---
# <a name="before-you-start"></a>Avant de commencer

## <a name="what-youll-need-to-run-windows-mixed-reality"></a>Ce dont vous avez besoin pour exécuter Windows Mixed Reality

* [Affichage monté en tête Windows Mixed Reality (HMD)](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices).
* Un nouveau [PC Windows Mixed Reality Ready](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) ou un PC compatible Windows Mixed Reality exécutant Windows 10 version 1709 ou ultérieure.
* Une connexion Internet
* Adaptateurs d’affichage, USB et Bluetooth (s’ils ne sont pas intégrés au casque ou à l’ordinateur)
* Des contrôleurs de mouvement, un contrôleur Xbox ou une souris et un clavier
* Casque avec un microphone (si vos HMD ne les intègrent pas)
* Un grand espace ouvert

## <a name="make-sure-your-pc-is-compatible-with-windows-mixed-reality"></a>Assurez-vous que votre ordinateur est compatible avec Windows Mixed Reality

Pour voir si votre ordinateur est compatible avec Windows Mixed Reality, vérifiez la [Configuration matérielle PC minimale requise pour Windows Mixed Reality](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou exécutez le [portail Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) sur votre PC.

Pour plus d’informations sur les problèmes de compatibilité des PC, cliquez [ici](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality).

## <a name="make-sure-you-have-the-windows-10-version-1709-or-newer-installed"></a>Vérifiez que la version 1709 ou une version ultérieure de Windows 10 est installée

Vous devez exécuter la version 1709 de Windows 10 (la mise à jour des créateurs de automne) ou une version plus récente pour utiliser Windows Mixed Reality. Les versions compatibles de Windows 10 sont les suivantes :
* Windows 10 version 1709 (automne Creators Update, Build 16299)
* Windows 10 version 1803 (mise à jour de printemps, Build 17134)
* Windows 10 version 1809 (mise à jour d’octobre, Build 17763)

Pour voir la version de Windows 10 que votre appareil est en cours d’exécution, sélectionnez le bouton **Démarrer** , puis sélectionnez **paramètres > système > à propos de**.

Pour vous assurer que Windows 10 est à jour sur votre ordinateur, sélectionnez le bouton **Démarrer** , puis sélectionnez **paramètres > mettre à jour & sécurité > Windows Update**.  Sélectionnez **Rechercher des mises à jour**. Si des mises à jour sont disponibles, installez-les.

Pour plus d’informations sur la façon de maintenir votre ordinateur à jour, cliquez [ici](https://support.microsoft.com/en-us/help/12373/windows-update-faq)

## <a name="make-sure-your-pc-is-connected-to-the-internet"></a>Vérifier que votre ordinateur est connecté à Internet

Vérifiez que votre ordinateur est connecté à Internet. Vous devrez télécharger des pilotes et d’autres logiciels supplémentaires pour que Windows Mixed realisation soit opérationnel.  Si votre Wi-Fi connexion réseau est définie sur contrôlé, remplacez-la par non contrôlé. [Plus d’informations](https://support.microsoft.com/en-us/help/4028458/windows-metered-connections-in-windows-10)

## <a name="make-sure-you-have-a-compatible-graphics-driver"></a>Vérifiez que vous disposez d’un pilote graphique compatible.

Votre ordinateur doit disposer d’un pilote graphique WDDM 2,2 ou version ultérieure pour terminer la configuration de la réalité mixte. Si ce n’est pas déjà le cas, essayez les sources suivantes :

* Recherchez les dernières mises à jour de pilotes critiques à l’aide de Windows Update (**> paramètres Windows > mise à jour et sécurité > vérification des mises à jour**)
* Recherchez les dernières mises à jour de pilote facultatives :
    1. Cliquez avec le bouton droit sur **démarrer > Device Manager**.
    2. Développez les **adaptateurs d’affichage**.
    3. Cliquez avec le bouton droit sur la carte graphique et sélectionnez **mettre à jour le pilote > Rechercher automatiquement le logiciel de pilote mis à jour**.
* Consultez le site Web du fabricant (OEM) de votre PC.
* Vérifiez sur le site Web le fabricant de la carte graphique de votre ordinateur (par exemple, AMD, Intel ou NVIDIA).

## <a name="make-sure-that-you-have-any-required-adapters"></a>Assurez-vous que vous disposez des adaptateurs requis

Il se peut que votre PC compatible Windows Mixed Reality ne dispose pas des ports HDMI et USB 3,0 de taille intégrale nécessaires pour connecter votre casque immersif. Ou vous aurez peut-être besoin d’un adaptateur Bluetooth pour répondre aux exigences du portail de réalité mixte.  Si c’est le cas, vous aurez besoin d’adaptateurs pour connecter votre casque et vos contrôleurs de mouvement. Vous trouverez la liste des types d’adaptateurs dont vous pouvez avoir besoin et des recommandations sur les modèles d’adaptateur spécifiques [ici](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).

## <a name="make-sure-that-you-have-input-devices"></a>Vérifiez que vous avez des périphériques d’entrée.

Windows Mixed Reality est conçu pour fonctionner de façon optimale avec les contrôleurs de mouvement Windows Mixed Reality, qui fournissent des interactions précises et précises sans avoir besoin d’installer le matériel sur vos murs. Toutefois, vous pouvez également utiliser un contrôleur Xbox ou une souris et un clavier.

## <a name="get-headphones-if-your-headset-didnt-come-with-them"></a>Recevez un casque si votre casque n’y est pas arrivé

À moins que vous n’achetiez des casques Samsung HMD Odyssey, HP réverbération ou HP réverbération G2 (qui comportent un casque AKG intégré et un microphone intégré à deux baies), vous devez obtenir un casque audio avec une paire de casque qui peut se brancher à la prise jack audio headset’s 3,5 mm de votre HMD.

## <a name="make-sure-that-you-have-a-large-open-space"></a>Vérifiez que vous disposez d’un grand espace ouvert

Si vous souhaitez vous déplacer tout en utilisant Windows Mixed Reality, vous devez disposer d’un grand espace ouvert.  Pendant l’installation, vous êtes invité à choisir entre « assiste » ou « toutes les expériences ». Choisissez « toutes les expériences » et configurez une limite si vous souhaitez vous déplacer.

### <a name="seated-and-standing-no-boundary"></a>Assis et debout (aucune limite)

Si vous sélectionnez « assis et debout », vous utiliserez votre casque sans limite. Cela signifie que vous devez rester en un seul endroit lors de l’utilisation du casque, afin de pouvoir éviter les obstacles physiques et le déclenchement des dangers. Vous pouvez vous asseoir, mais vous ne devez pas vous déplacer. Certaines applications peuvent être conçues pour fonctionner avec une limite. vous ne pourrez peut-être pas les utiliser ou ne pas avoir la même expérience, si vous les utilisez sans limite.

### <a name="all-experiences-boundary"></a>Toutes les expériences (limite)

Si vous choisissez « toutes les expériences », vous configurerez une limite et vous serez en mesure de vous déplacer et d’utiliser les applications et les expériences qui fonctionnent avec une limite, ainsi que celles qui n’en ont pas besoin. Vous devez préparer votre espace pour vous assurer qu’il n’y a pas d’obstacles, de dangers ou d’éléments fragiles dans le domaine que vous utiliserez (y compris au-dessus de votre tête). Ne pas configurer en haut d’un escalier ou sous un ventilateur à plafond très faible. Retirez les breakables et les obstacles de la zone, et assurez-vous que vous et toute personne qui utilise votre casque lisent et comprennent les [consignes de sécurité](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

## <a name="see-also"></a>Voir aussi

* [Connectez-vous à votre HMD](plug-in-your-headset.md)
* [Configuration matérielle minimale requise pour PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* [Adaptateurs recommandés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)