---
title: FAQ sur l’utilisation de Windows Mixed Reality
description: Recevez des réponses aux questions courantes lors de l’utilisation de Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
appliesto:
- Windows 10
ms.openlocfilehash: cf02ccfc92d80ee1d1a8f6ca3d4ab55650f4a62c
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044435"
---
# <a name="using-windows-mixed-reality-faq"></a>FAQ sur l’utilisation de Windows Mixed Reality

Si vous avez besoin d’aide concernant l’utilisation de votre casque immersif Windows Mixed Reality, consultez ces rubriques pour obtenir des informations générales et des conseils de dépannage.

Encore besoin d’aide ? Pour un dépannage avancé, consultez cet article.

## <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Je vois un message indiquant « perte de suivi » ou « nous n’avons pas de limite pour cet espace ».

Sélectionnez **démarrer > portail de réalité mixte** sur votre bureau. Sélectionnez **menu** , puis **Exécutez le programme d’installation** pour créer une nouvelle limite. Windows Mixed Reality prend en charge plusieurs emplacements et identifie l’espace dans lequel vous vous trouvez au démarrage tant que la salle n’a pas changé de manière significative.  


## <a name="i-cant-hear-any-sound-or-the-sound-is-coming-from-my-computer-instead-of-my-headset"></a>Je n’entends aucun son, ou le son provient de mon ordinateur au lieu de mon casque

Si votre casque immersif n’inclut pas de casque intégré, vous devez connecter le casque à la prise jack audio sur le casque. (Le Jack est souvent situé derrière le visière ou les lentilles du casque ; Vérifiez auprès du fabricant de votre casque si vous avez des difficultés à le trouver.) 

Certains casques audio ont des boutons physiques pour contrôler le volume. Si l’audio ne fonctionne pas, vérifiez si le volume est désactivé ou désactivé.

Windows Mixed Reality est conçu pour émettre du son via votre casque immersif lorsque vous l’utilisez et que vous y êtes connecté. Quand vous mettez le casque hors tension ou retournez le pare-soleil, le son est basculé vers votre appareil de lecture Windows par défaut. Vous pouvez modifier ce paramètre dans **paramètres > la réalité mixte > l’audio et la parole** .

> [!NOTE]
> * Le son spatial Windows Mixed Reality fonctionne mieux avec les casques intégrés ou connectés directement à votre casque immersif. Les haut-parleurs ou les écouteurs du PC connectés à l’ordinateur risquent de ne pas fonctionner correctement pour le son spatial.
> * Windows Mixed Reality ne prend pas en charge les casques audio Bluetooth.

## <a name="speech-commands-arent-working"></a>Les commandes vocales ne fonctionnent pas

Pour utiliser les commandes vocales, les paramètres de langue et de voix de votre ordinateur doivent être définis sur une [langue et une langue Windows Mixed Reality prises en charge](wmr-setup-faq.md#what-languages-are-supported-in-windows-mixed-reality). Pour vérifier votre région et votre langue Windows, sélectionnez **paramètres > heure & langue > région & langue** . Pour vérifier la langue de votre voix, sélectionnez **paramètres > heure & langue > la reconnaissance vocale** .

Si votre casque n’a pas de MIC intégré, attachez un casque avec un micro au casque ou sur votre PC. Pour que le commutateur d’entrée MIC soit automatiquement relié à votre casque lorsque votre casque y est directement connecté, sélectionnez **paramètres > réalité mixte > audio et discours** , et assurez-vous que **lorsque j’utilise mon casque, basculez vers le micro du casque** est activé.

Certains casques audio ont un bouton physique pour activer et désactiver le microphone. Si les commandes vocales ne fonctionnent pas, vérifiez si votre micro est muet.

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>La limite est toujours visible. Comment faire disparaître ?

Lorsque vous êtes près de la limite, il s’affiche. Si votre limite comprend des sections qui ont une forme étroite ou irrégulière, vous pouvez vous y retrouver et l’afficher, ce qui est plus souvent que vous le souhaitez. Pour résoudre ce problème, essayez de créer à nouveau votre limite à l’aide d’une forme plus grande et plus normale. Sélectionnez **démarrer > portail de réalité mixte** sur votre bureau, puis sélectionnez **exécuter le programme d’installation** . 

Vous pouvez également désactiver temporairement la limite à partir du portail de réalité mixte : sélectionnez **menu** , puis utilisez le bouton bascule pour désactiver la limite. Lorsque la limite est désactivée, vous devez rester sur un seul endroit pour éviter les obstacles.

## <a name="im-having-trouble-with-my-motion-controllers"></a>Je rencontre des problèmes avec mes contrôleurs de mouvement

Si vos contrôleurs de mouvement ne fonctionnent pas correctement, ne vous connectez pas ou si vous ne voyez pas d’image des contrôleurs quand vous enportez votre casque, essayez ce qui suit :

* Assurez-vous que vos contrôleurs sont activés. Pour les activer, appuyez sur le bouton **Windows** et maintenez-le enfoncé pendant 2 secondes.
* Sélectionnez **démarrer > portail de réalité mixte** sur votre ordinateur, puis sélectionnez **menu** pour voir vos contrôleurs de mouvement listés, ainsi qu’un message d’État :
    * Prêt : les contrôleurs sont tous définis.
    * Suivi perdu : le portail de réalité mixte ne trouve pas vos contrôleurs. Tenez-les devant votre casque et redémarrez-les en appuyant sur le bouton **Windows** pendant 4 secondes, puis de nouveau pendant 2 secondes.
    * Batterie faible : remplacez les piles du contrôleur.
* Si vous utilisez le Wi-Fi, essayez de connecter votre PC à un réseau Wi-Fi 5 GHz pour réduire les interférences sans fil. 
* Pour les nouveaux casques associés directement aux contrôleurs, sélectionnez l’option **« ... »** dans le **portail de réalité mixte** et choisissez **configurer les contrôleurs** . Cela vous permet de vous connecter à l’application du casque pour associer les contrôleurs au casque.  
* Pour les casques plus anciens qui ne disposent pas de Bluetooth intégré, les contrôleurs doivent être couplés directement :  
    * Sélectionnez Paramètres > appareils > Bluetooth & d’autres appareils sur votre ordinateur et assurez-vous que les contrôleurs sont répertoriés comme couplés.Si ce n’est pas le cas, vous devez les apparier. 
    * Si vous avez d’autres périphériques Bluetooth associés à votre PC, tels que des casques ou des boîtiers, essayez de les supprimer. Sélectionnez **paramètres > appareils > Bluetooth & d’autres appareils** sur votre ordinateur, sélectionnez les appareils, puis sélectionnez **Supprimer l’appareil** .
    * Retirez les écouteurs et les haut-parleurs Bluetooth dans **paramètres > appareils > Bluetooth & d’autres appareils** et éteignez les appareils. 
    * Si vous utilisez une carte Bluetooth USB, assurez-vous qu’elle est connectée à un port USB noir 2,0 et qu’elle est branchée le plus loin possible de tout autre transmetteur sans fil ou disque mémoire flash USB, y compris le connecteur USB pour votre casque. 
    * Si votre PC intègre Bluetooth et que vous rencontrez des problèmes de connexion, essayez d’utiliser une carte Bluetooth USB à la place. (Pour ce faire, vous devez également désactiver votre radio Bluetooth intégrée dans [Device Manager](https://support.microsoft.com/help/4026149), puis coupler vos autres appareils Bluetooth avec la nouvelle carte.)
* Si l’application paramètres est ouverte sur la page Bluetooth & autres appareils, fermez-la.

## <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Je rencontre une gêne quand j’utilise mon casque

Pour obtenir des informations générales sur le confort de Windows Mixed Reality, consultez [intégrité, sécurité et confort du casque Windows Mixed Reality](wmr-health-safety-comfort.md). Pour plus d’informations sur votre casque spécifique, contactez le fabricant du casque.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Mes éléments visuels sont saccadés, se chargent lentement ou ne semblent pas corrects

Si vos visuels de réalité mixte n’ont pas la meilleure apparence, essayez ce qui suit.

* Assurez-vous que votre casque est branché à la bonne carte graphique sur votre PC. Certains PC ont des cartes graphiques intégrées et discrètes. La carte discrète offre généralement les meilleures performances. [En savoir plus sur le matériel PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Fermez les applications inutilisées sur votre bureau.
* Ajustez la taille de votre casque : déplacez-le vers le bas et le haut, ou vers la gauche et la droite, et assurez-vous qu’il est ajusté.
* Réglez les paramètres visuels de votre casque ( **paramètres > la réalité mixte > affichage du casque** ). Lorsque la **qualité visuelle** est définie sur **automatique** , nous allons choisir la meilleure expérience de réalité mixte pour votre PC. Pour obtenir une expérience avec davantage de détails visuels, affectez la valeur **haute** à la **qualité visuelle** . Si vos visuels sont saccadés, vous souhaiterez peut-être sélectionner un paramètre inférieur.
* Essayez de régler l’étalonnage de votre casque. Les lentilles doivent être ajustées pour correspondre à votre distance interpupillary (IPD), la distance entre vos élèves. Si vous ne connaissez pas votre IPD, un Optometrist doit être en mesure de le mesurer pour vous. Il existe également des sites Web conçus pour mesurer l’IPD. Une fois que vous connaissez votre IPD, utilisez le bouton d’étalonnage de votre casque pour effectuer des ajustements. Si le casque n’a pas de bouton d’étalonnage, sélectionnez **paramètres > réalité mixte > l’affichage du casque** et ajustez le contrôle d’étalonnage.

## <a name="i-have-questions-about-my-headset-hardware"></a>J’ai des questions sur mon matériel de casque

Pour plus d’informations sur votre casque, contactez le fabricant. Il peut y avoir un guide produit dans la zone, ou vous pouvez essayer le site Web du fabricant.

## <a name="the-floor-in-mixed-reality-seems-to-be-in-the-wrong-spot"></a>L’étage de la réalité mixte semble se trouver au mauvais endroit

Si le plancher semble inactif (par exemple, vous avez l’impression que vous êtes flottant), sélectionnez **démarrer > ajustement** de la pièce tout en portant votre casque pour apporter des modifications.

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>J’ai reçu un message indiquant qu’il faut brancher et charger mon PC. Pourquoi ?

Si vous utilisez un ordinateur portable, Windows Mixed Reality fonctionne mieux lorsque l’ordinateur est entièrement chargé et branché.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Comment faire désinstaller Windows Mixed Reality ?

Sélectionnez **démarrer > paramètres > réalité mixte** , puis sélectionnez **désinstaller** . Veillez à déconnecter votre casque de votre ordinateur et fermez le portail de réalité mixte avant de désinstaller.

Quand vous êtes prêt à recommencer à utiliser votre casque, connectez-le et le portail de réalité mixte vous guidera tout au long de la configuration.

> [!NOTE]
> Si vous voyez un message indiquant « nous n’avons pas pu terminer la suppression de Windows Mixed Reality », cela signifie que certains fichiers, y compris les informations relatives à votre environnement, peuvent toujours se trouver sur votre ordinateur. Cela peut poser des problèmes si vous décidez de réinstaller Windows Mixed Reality ultérieurement.
> 
> Pour savoir comment supprimer manuellement les informations Windows Mixed Reality restantes de votre PC, consultez **[cet article](installation_errors.md)** .

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Mon Wi-Fi ralentit lorsque j’utilise Windows Mixed Reality

Si vous utilisez une connexion Wi-Fi 2,4 GHz, vos contrôleurs de mouvement peuvent ralentir votre Wi-Fi. Essayez l’une des opérations suivantes :

<!-- TODO: Use Windows Mixed Reality PC hardware guidelines interlink -->
* Basculez vers une connexion Wi-Fi 5 GHz, si celle-ci est disponible. [En savoir plus](https://support.microsoft.com/help/4000461)
* Utilisez un adaptateur Bluetooth distinct pour connecter vos contrôleurs de mouvement à votre PC. [Voir les adaptateurs recommandés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

## <a name="what-is-the-experience-options-setting"></a>Qu’est-ce que le paramètre options d’expérience ?

Le paramètre options d’expérience ( **paramètres > réalité mixte > affichage du casque > options d’expérience** ) vous donne la possibilité de modifier les paramètres de performances de Windows Mixed Reality. Cela vous permet de choisir la meilleure expérience possible pour votre configuration matérielle dans une plage de contenu. L’expérience 90Hz est disponible pour tous les systèmes, mais vous pouvez essayer d’utiliser la fonctionnalité automatique en premier, pour déterminer le paramètre de votre choix.

Voici les options disponibles :

* Automatique ou laisser Windows décider : Windows Mixed Reality déterminera la meilleure expérience de votre configuration matérielle. Pour la plupart des gens, c’est le meilleur choix pour commencer.
* 60Hz : définit la fréquence d’actualisation sur 60 Hz et désactive certaines fonctionnalités, telles que la capture vidéo et la version préliminaire dans le portail de réalité mixte.
* 90Hz : définit la fréquence d’actualisation sur 90Hz si votre casque peut s’exécuter à cette vitesse. Si des problèmes de câble empêchent l’exécution du casque sur 90Hz, vous pouvez voir une erreur au démarrage avec ce mode sélectionné. 

## <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Je vois un message indiquant « placer sur votre casque », même si j’ai mon casque sur

Quand vous placez sur votre casque, Windows Mixed realisation a besoin d’un peu de temps pour recharger votre espace. Cette opération peut prendre quelques secondes. Si ce message ne disparaît pas, assurez-vous que l’autocollant de protection a été retiré du capteur de proximité, situé à l’intérieur du casque, entre les lentilles. Si la vignette a été supprimée et que vous rencontrez toujours des problèmes, contactez le fabricant de votre casque. En appuyant sur **Win + Y** sur votre clavier, vous déclenchez manuellement l’exécution du casque si le capteur de proximité ne se déclenche pas automatiquement. 

Encore besoin d’aide ? Pour un dépannage avancé, consultez [cet article](troubleshooting-windows-mixed-reality.md).

## <a name="see-also"></a>Voir aussi
* [Demander à la communauté](https://answers.microsoft.com)
* [Contactez-nous pour obtenir de l’aide](https://support.microsoft.com/contactus/)