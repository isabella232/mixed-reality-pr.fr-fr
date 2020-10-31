---
title: Affichage du casque FAQ
description: Affichez le dépannage de Windows Mixed realisation pour les problèmes d’affichage du casque qui vont au-delà de notre documentation de support technique standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support
appliesto:
- Windows 10
ms.openlocfilehash: df91b6d131a8c2ce0faeecc659842418ef03c7c1
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132083"
---
# <a name="headset-display-faqs"></a>Affichage du casque FAQ

## <a name="my-headset-displays-are-black"></a>Mes casques s’affichent en noir

* Vérifiez les performances et la stabilité de votre ordinateur :
    * Utilisez le gestionnaire des tâches pour vérifier si des processus sont atteignant l’UC, le GPU et/ou les lecteurs de disque de votre PC.
    * Vérifiez les journaux « application » et « système » dans **observateur d’événements > journaux Windows** pour voir si vous avez une application qui s’arrête fréquemment et génère des rapports d’rapport D’ERREURS Windows (WER).
    * Vérifiez Windows Update pour vous assurer que votre version de Windows est à jour. Vous devrez peut-être sélectionner plusieurs fois « Rechercher des mises à jour ».
* Vérifier la stabilité de l’application et du jeu :
    * Assurez-vous que votre ordinateur répond à la configuration minimale requise pour exécuter une application ou un jeu qui ne fonctionne pas correctement.
    * Assurez-vous que la version du pilote GPU est récente et recherchez les nouveaux problèmes de performances et de compatibilité et les régressions sur les nouveaux pilotes.
    * Si vous utilisez des applications et des jeux SteamVR, assurez-vous que SteamVR et la réalité mixte Windows pour les composants SteamVR sont à jour.
* Vérifier la compatibilité des adaptateurs HDMI :
    * Assurez-vous que le câble HDMI est branché.
    * Si vous utilisez un adaptateur HDMI (par exemple, un mini-Adaptateur DisplayPort pour HDMI), assurez-vous qu’il est compatible avec Windows Mixed Reality. L’adaptateur doit prendre en charge l’HDMI 2,0 et il existe de nombreux adaptateurs plus anciens qui prennent uniquement en charge 1080p. Consultez [adaptateurs recommandés pour Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * La commande de plug-in peut être importante. Connectez l’adaptateur HDMI à votre ordinateur avant de connecter le casque à la carte, en particulier si vous utilisez un adaptateur USB-C à HDMI.
    * Essayez de supprimer les câbles d’extension si vous les utilisez.
* Vérifier la compatibilité de la carte graphique et du pilote :
    * Essayez le port HDMI de votre PC à l’aide d’un moniteur d’ordinateur. Certains PC peuvent avoir plus d’un port HDMI, et tous ne peuvent pas être actifs.
    * Si votre ordinateur dispose à la fois d’une unité de traitement graphique (iGPU) et d’une unité de traitement graphique (dGPU) discrètes, assurez-vous que vous êtes connecté au port HDMI de votre dGPU.
    * Vérifiez la version de votre pilote GPU. Assurez-vous qu’elle est récente, mais faites attention aux nouveaux problèmes de performances et de compatibilité et aux régressions sur les nouveaux pilotes.
    * Si vous utilisez la réalité mixte sur un ordinateur portable et que vous avez installé un pilote graphique plus récent à partir du site Web du fabricant de la carte graphique, essayez de rétrograder vers le pilote de carte graphique le plus récent fourni sur le site Web du fabricant de votre ordinateur, ou sur Windows Update.
    * Si vous disposez de plusieurs moniteurs PC connectés à votre ordinateur, essayez de déconnecter temporairement tout le moniteur PC sauf un.
    * Si vous avez défini un taux de rafraîchissement personnalisé pour votre moniteur PC, essayez de rétablir temporairement un taux de rafraîchissement standard, par exemple 60 Hz.
    * Si vous avez récemment modifié votre carte graphique sans réinstaller Windows, vérifiez que le pilote du moniteur de casque est toujours installé. Une fois votre casque branché, vérifiez que « casque de réalité mixte » est listé sous le nœud analyses dans Device Manager.
    * Si votre ordinateur dispose d’une carte graphique NVIDIA, assurez-vous que le logiciel de vision 3D de NVIDIA est désactivé.
    * Sur certaines cartes graphiques (en particulier les cartes plus anciennes), le port HDMI peut ne pas prendre en charge la norme HDMI 2,0 ou ne pas être entièrement compatible avec Windows Mixed Reality. Essayez d’utiliser le DisplayPort de votre carte graphique avec un [adaptateur displayport 1,2 à HDMI 2,0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * Les PC HP Omen avec HP Product Number 1RJ99EA # ABU ont des ports HDMI qui sont incompatibles avec Windows Mixed Reality (ouvrez l' « Assistant de support HP » et le numéro sera répertorié vers le bas de l’application).
    * Si votre ordinateur possède une carte graphique AMD R9-Series et que vous utilisez un casque de réalité mixte Samsung, mettez à jour le microprogramme de votre casque vers la version 1.0.8 ou ultérieure pour utiliser le port HDMI de votre carte graphique avec le casque.
    * Si vous utilisez un livre surface 2, assurez-vous que vous utilisez l' [adaptateur USB-C vers HDMI](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
* Vérifiez la présence d’un problème matériel de casque de réalité mixte :
    * Pour confirmer ou éliminer les problèmes matériels avec votre casque, connectez votre casque de réalité mixte à un autre PC.
    * Vérifiez la compatibilité du PC et les problèmes d’installation en premier, car les symptômes sont très similaires.
* Assurez-vous que le câble USB est branché sur un port USB 3,0 ou plus rapide. Les ports USB 3,0 ont la valeur SS (Super Speed) en regard de ceux-ci et sont souvent en couleur bleue.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Mon casque s’affiche parfois en noir après une certaine utilisation

* Essayez de désactiver les fonctionnalités de suspension ou d’économie d’énergie USB sur votre PC. Par exemple, dans **paramètres > système > Power & Sleep > la [suspension sélective USB](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend)** , le paramètre « autoriser l’ordinateur à éteindre cet appareil pour économiser de l’énergie » dans Device Manager et les paramètres d’économie d’énergie USB dans le microprogramme de votre PC.
* Déconnectez temporairement les autres périphériques USB et les périphériques connectés à votre PC.
* Vérifiez que la version du pilote GPU est récente et recherchez les nouveaux problèmes de performances et de compatibilité et les régressions sur les nouveaux pilotes.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>L’un des écrans de mon casque est noir

* Si vous utilisez un adaptateur HDMI, assurez-vous qu’il prend en charge l’HDMI 2,0.
* Retirez tous les câbles d’extension USB et HDMI que vous utilisez peut-être.
* Assurez-vous que votre pilote graphique est à jour.
* Essayez le casque de la réalité mixte sur un autre PC.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-re-initializes"></a>Mon casque affiche bleu, puis le portail de réalité mixte réinitialise

Cela indique généralement un problème de fiabilité du contrôleur USB occasionnel sur votre ordinateur :

* Essayez un autre port USB. Votre ordinateur peut avoir plusieurs contrôleurs USB 3,0.
* Retirez tous les câbles d’extension (le cas échéant).
* Débranchez tous les autres périphériques USB de votre PC.
* Connectez un concentrateur USB 3,0 en externe à votre PC et connectez votre casque au Hub.
* Si vous utilisez un PC de bureau, envisagez d’acheter une carte USB 3,0 PCIe pour ajouter un autre contrôleur USB à votre PC.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Mon casque provoque le blocage de mon ordinateur ou l’affichage d’un écran noir lors du démarrage

Sur certains PC, le fait de laisser votre casque branché avant de mettre sous tension ou pendant le redémarrage de votre PC peut interférer avec son processus de démarrage. Votre ordinateur peut sélectionner le casque s’affiche comme « moniteur principal » pour afficher la progression du démarrage du PC, ne pas démarrer correctement, ou « bloquer » et/ou produire un code d’erreur de signal sonore. Le comportement dépend de la marque et du modèle du PC et/ou de la marque et du modèle de la carte graphique. Pour résoudre ce problème :

* Connectez votre casque à un autre port de votre carte graphique (vous devrez peut-être utiliser un adaptateur pour utiliser les autres ports).
* Assurez-vous que le microprogramme BIOS/UEFI de votre ordinateur est à jour (mais mettez à jour uniquement le microprogramme BIOS/UEFI de votre ordinateur si vous y êtes familiarisé).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Mon PC ou casque affiche le scintillement, le clignotement ou le reste noir lors de l’utilisation d’un PC surface

* Assurez-vous que vous utilisez un adaptateur HDMI qui prend en charge l’HDMI 2,0. De nombreux adaptateurs HDMI plus anciens prennent uniquement en charge la résolution de 1080p, ce qui est insuffisant pour les casques de réalité mixte.
* Assurez-vous que votre pilote graphique est à jour. Consultez Windows Update et le site Web du fabricant du PC pour obtenir un pilote graphique mis à jour.
* Certains appareils surface sont incompatibles avec Windows Mixed Reality. En savoir plus sur la [compatibilité des surfaces et les exigences](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>L’affichage de mon casque ne fonctionne pas après l’arrêt et le démarrage rapide

Débranchez le câble HDMI et le câble USB du casque, puis replacez-les.

## <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Les affichages de mon casque sont très saccadés, mais la fenêtre d’aperçu du portail de réalité mixte s’affiche

* Vérifiez que les ressources système de votre ordinateur (processeur, mémoire et disque dur) sont disponibles et qu’elles ne sont pas consommées par une autre application ou un autre processus.
* Mettez à jour votre pilote Graphics.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>J’obtiens une erreur « la classe d’installation n’est pas présente ou n’est pas valide » dans Device Manager

Si vous voyez « capteurs HoloLens » avec un point d’exclamation jaune dans Device Manager, sélectionnez l’appareil pour obtenir des détails supplémentaires. Si vous voyez un message indiquant «les pilotes de cet appareil ne sont pas installés. (Code 28)--la classe d’installation n’est pas présente ou n’est pas valide. cela est généralement dû au fait que votre ordinateur exécute [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). Notez que N éditions de Windows 10 ne prennent pas en charge Windows Mixed Reality et que vous devez installer une version non N de Windows 10.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Mon environnement WMR est instable ou subit des interruptions lorsque je déplace mon tête et affiche une double vision

Sur un ordinateur portable doté d’un graphique intégré et d’un GPU NVIDIA, une erreur se produit au bout d’un laps de temps qui semble entraîner l’affichage d’une image précédente après le cadre suivant, ce qui a pour effet de doubler la vision. Le problème semble se trouver sur les pilotes après le pilote graphique NVIDIA 436,48.  L’installation de ce pilote permet de résoudre le problème jusqu’à ce que NVIDIA résout le problème dans les pilotes mis à jour. Pour une installation directe du pilote graphique NVIDIA 436,48, visitez [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>Je ne suis pas familiarisé avec mon casque

Pour obtenir des informations générales sur le confort de Windows Mixed Reality, consultez [intégrité, sécurité et confort du casque Windows Mixed Reality](wmr-health-safety-comfort.md). Pour plus d’informations sur votre casque spécifique, contactez le fabricant du casque.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Comment obtenir une vue plus claire dans mon casque

Essayez d’ajuster l’adéquation de votre casque. Déplacez-le vers le haut ou vers le haut, ou vers la gauche et la droite, sur votre visage et ajustez les sangs pour qu’il s’ajuste.

Si votre casque a un bouton pour ajuster l’étalonnage, ajustez ses paramètres d’étalonnage. Si ce n’est pas le cas, accédez à **paramètres > réalité mixte > qualité visuelle** et ajustez l’étalonnage à cet endroit. Pour plus d’informations sur l’étalonnage de votre appareil spécifique, contactez le fabricant de votre casque.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Je vois souvent une bordure noire autour de la vue dans le casque. Parfois, c’est comme je regarde un tunnel

Cela signifie que l’application ne peut pas atteindre la fréquence d’images sur votre PC et que le système utilise des trames anciennes pour afficher la vue dans le casque. Étant donné que les applications affichent uniquement la partie du monde que vous regardez, si elles n’atteignent pas régulièrement leurs fréquences d’images, le système essaiera de rendre le monde à partir d’un point de vue antérieur et remplira les détails manquants avec le noir. Si cela se produit fréquemment :

1. Fermez ou terminez tous les programmes inutiles pour libérer de la mémoire et de l’UC.
2. Réduisez les paramètres de détail dans votre application.
3. Accédez à **paramètres > la réalité mixte > affichage du casque** pour réduire la quantité de détails affichée dans la page d’hébergement de la réalité mixte Windows.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>La vue du casque est instable et subit beaucoup de perturbations

Il se peut que le système ne puisse pas afficher le contenu sur le casque ou que le système de suivi rencontre des problèmes. Vérifiez les points suivants :

1. Ouvrez le gestionnaire des tâches pour vous assurer que votre ordinateur dispose de suffisamment de ressources de calcul. Vous devez avoir 80% de l’UC libre, 400 Mo de RAM, et les e/s disque doivent être inférieures à 80%.
2. Assurez-vous que vous disposez des derniers pilotes graphiques pour votre matériel. Consultez la [section du pilote Graphics](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Assurez-vous que la salle a suffisamment de lumière.
4. Débranchez l’appareil, fermez Windows Mixed Reality et rebranchez-le.
5. Redémarrez votre PC.
6. Si le problème persiste, contactez le [support](https://support.microsoft.com/)technique.
