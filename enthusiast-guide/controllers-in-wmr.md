---
title: Contrôleurs dans Windows Mixed Reality
description: Découvrez comment configurer, associer, utiliser et résoudre les problèmes courants liés aux contrôleurs dans Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
appliesto:
- Windows 10
ms.openlocfilehash: 960b26d16e9edd387eb94c469d45b0c669fadc10
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580541"
---
# <a name="motion-controllers-in-windows-mixed-reality"></a>Contrôleurs de mouvement dans Windows Mixed Reality

Les contrôleurs de mouvement sont des accessoires matériels qui permettent aux utilisateurs d’interagir en réalité mixte. L’un des avantages des contrôleurs de mouvement par rapport aux gestes est que les contrôleurs ont une position précise dans l’espace, ce qui permet une interaction fine avec les objets numériques. Pour les casques immersifs Windows Mixed Reality, les contrôleurs de mouvement constituent la principale façon dont les utilisateurs effectuent des actions dans leur environnement.

Les contrôleurs de mouvement Windows Mixed Reality effectuent un suivi des mouvements précis et réactifs dans votre champ de vue via les capteurs du casque immersif. Il n’est pas nécessaire d’installer le matériel sur les murs de votre espace. Ces contrôleurs de mouvement offriront la même facilité de configuration et de portabilité que les casques immersifs immersifs de Windows Mixed Reality.

Vous pouvez également utiliser un contrôleur Xbox, une souris, un clavier ou une solution en [utilisant uniquement votre voix](using-speech-in-wmr.md).

## <a name="motion-controller-setup"></a>Configuration du contrôleur de mouvement

La plupart des casques sont précouplés directement sur le casque, mais certains casques précoces nécessitent que les contrôleurs de mouvement soient couplés à votre PC avec Bluetooth 4,0. Lorsque vous connectez votre casque immersif pour la première fois, vous allez passer à l’activation de vos contrôleurs de mouvement au cours de l’installation. Mais si vous devez les recoupler ultérieurement, voici comment procéder :

1. Lancez le **portail de réalité mixte** avec votre casque connecté.  
2. Dans le coin inférieur gauche, sélectionnez **... > configurer les contrôleurs**.
3. Insérez deux piles AA dans chaque contrôleur et mettez votre contrôleur en mode d’appariement (consultez les instructions dans la [section contrôleurs de mouvement de paire](controllers-in-wmr.md#pair-motion-controllers)
4. Suivez les instructions affichées à l’écran.

> [!NOTE]
> * Pour les contrôleurs qui se couplent directement à votre PC, vous devez les mettre en mode de jumelage en les mettant sous tension, puis en appuyant sur le bouton d’appariement dans le compartiment de la batterie jusqu’à ce que les lumières commencent à clignoter.
> * Les contrôleurs de mouvement ne prennent en charge que l’appariement à un seul PC à la fois. Si vous devez les utiliser avec un autre casque, vous devez passer par le processus d’appariement. Consultez [configurer la réalité mixte Windows](set-up-windows-mixed-reality.md)

[Obtenir de l’aide pour la connexion](wmr-setup-faq.md#my-motion-controllers-arent-working)

> [!IMPORTANT]
> **Vous avez un contrôleur Xbox ?**
> 
> Si vous avez un contrôleur Xbox Bluetooth, associez-le à votre PC pour l’utiliser avec votre casque.
> 
> Si vous avez un contrôleur Xbox câblé, connectez-le à votre PC.
> 
> Certains jeux et applications utilisent le contrôleur Xbox différemment de la façon dont il est utilisé dans la réalité mixte. Pour utiliser le contrôleur pour un jeu ou une application, sélectionnez **utiliser comme boîtier** de commande dans la barre de l’application ou dites « utiliser en tant que boîtier ». Pour rétablir la réalité mixte du contrôleur, sélectionnez **utiliser comme boîtier** d’emboîter, à nouveau ou par exemple, « utiliser avec le point de regard ».  

## <a name="pair-motion-controllers"></a>Contrôleurs de mouvement de paire

Si vous utilisez un casque qui comprend un contrôleur Bluetooth intégré, tel que le reverbe Samsung Odyssey + ou HP, vos contrôleurs doivent déjà être couplés. Toutefois, vous pouvez toujours coupler vos contrôleurs à l’aide de l’application d’installation (il doit être déjà installé au cours de la configuration de HMD. Vous pouvez également l’extraire à partir du Microsoft Store).

### <a name="pair-motion-controllers-to-hmd"></a>Associer les contrôleurs de mouvement à HMD

Mettez les contrôleurs sous tension en appuyant sur le bouton Windows pendant 2 secondes jusqu’à ce que les voyants soient allumés.

Retirez la couverture de la batterie de vos contrôleurs et recherchez le petit bouton d’appariement à la périphérie du contrôleur. Maintenez ce bouton enfoncé pour le coupler à votre PC.
    ![Appariement du contrôleur de mouvement](images/connect_controller.png)

Lancez le **portail de réalité mixte** avec votre casque connecté.  
Dans le coin inférieur gauche, sélectionnez **... > configurer les contrôleurs**.
Suivez les instructions à l'écran.

### <a name="pair-motion-controllers-to-pc"></a>Associer les contrôleurs de mouvement au PC

Vous pouvez associer votre contrôleur à un PC en ajoutant un autre appareil Bluetooth.

Alimentez les contrôleurs et placez-les en mode de jumelage comme décrit ci-dessus.

* Accéder aux paramètres de l’ordinateur
* Appareil/ajouter Bluetooth ou un autre périphérique.

Une fois le couplage terminé, les LED sont solides et brillants.

### <a name="common-issues"></a>Problèmes courants

* Vérifiez que vous n’avez qu’une seule radio Bluetooth active sur votre PC. Si vous disposez de plusieurs radios Bluetooth, vous devez désactiver les autres radios dans Device Manager.
* Placez votre dongle Bluetooth dans un port disposant d’un éclairage clair sur vos contrôleurs, et loin de brancher des appareils USB 3,0. USB 3,0 est connu pour avoir des interférences RF avec Bluetooth (lisez [ce document](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/usb3-frequency-interference-paper.pdf) d’Intel pour plus d’informations). Les ports USB 2,0 peuvent fonctionner mieux pour votre dongle Bluetooth.
* Assurez-vous que votre dongle Bluetooth n’est pas branché sur un port USB à côté du câble USB de votre HMD. Le câble du casque a été connu pour causer des interférences avec les dongles Bluetooth également. Branchez le dongle sur le port USB avant de votre ordinateur pour obtenir des résultats optimaux.
* Pour les Notebooks, assurez-vous que le Wi-Fi est connecté à une bande de 5 GHz pour une expérience optimale. Sélectionnez l’icône de réseau sans fil en bas à droite de la barre d’État et sélectionnez les propriétés du réseau que vous utilisez. Les blocs-notes conçus pour partager une antenne 2,4 GHz pour la connectivité Bluetooth et WiFi voient la congestion des données en cas de lenteur des vitesses de réseau ou de performances de suivi du contrôleur de mouvement médiocre.
* Vos contrôleurs Motion recevront régulièrement de nouvelles mises à jour logicielles de Microsoft. Les contrôleurs présentent un modèle alternatif de voyants clignotants lorsqu’ils reçoivent ces nouvelles mises à jour logicielles. C’est normal. Attendez la fin de la mise à niveau du logiciel avant d’utiliser les contrôleurs. Les contrôleurs vibreront et une lumière constante remplacera le modèle de mémoire flash alternatif lorsqu’il sera terminé.
* Vous pouvez être invité à « placer sur le casque et à utiliser le stick analogique pour vous téléporter » avant que les contrôleurs terminent le processus de mise à jour. Les contrôleurs ne seront pas visibles ou utilisables tant que la mise à jour n’est pas terminée. La plupart des mises à jour se produisent dans un délai de deux minutes, mais les mises à jour peuvent prendre jusqu’à 10 minutes. Attendez la fin de la mise à jour avant de passer à l’étape suivante.

## <a name="using-controllers"></a>Utilisation de contrôleurs

Voici comment contourner la réalité mixte avec les contrôleurs de mouvement, un manette de main Xbox ou une souris et un clavier.

> [!TIP]
> Pour basculer entre la réalité mixte et votre bureau, appuyez sur la **touche Windows + Y** sur le clavier de votre PC.

![Mappage du bouton de contrôleur de mouvement](images/get_to_know_controllers.png)

|  Pour  |  Contrôleurs de mouvement  | Boîtier de commande | Souris et clavier |
| --- | --- | --- | --- |
| Porte | Appuyez sur le stick analogique, puis pointez le contrôleur à l’endroit où vous souhaitez aller. Relâchez le stick analogique. | Appuyez sur le stick analogique gauche vers l’avant, puis recherchez l’emplacement où vous souhaitez aller. Relâchez le stick analogique. | Sélectionnez et maintenez le bouton droit, puis pointez la souris à l’endroit où vous souhaitez aller. Relâchez le bouton. |
| Sélectionnez | Pointez sur le contrôleur, puis tirez le déclencheur ou utilisez le pavé tactile. | Pointez avec le regard sur la cible, puis appuyez sur A. | Pointez la souris, puis cliquez sur le bouton gauche. |
| Ouverture du menu Démarrer | Appuyez sur le bouton **Windows** . | Appuyez sur le bouton **Xbox** . | Appuyez sur la **touche du logo Windows**. |
| Conserver une application immersif | Appuyez sur le bouton **Windows** . Ensuite, dans le menu actions rapides, sélectionnez page d’hébergement de la **réalité mixte** . | Appuyez sur le bouton **Xbox** . Sélectionnez ensuite le bouton de démarrage de la **réalité mixte** dans le menu actions rapides. | Appuyez sur la touche * * du logo Windows. Sélectionnez ensuite le bouton de démarrage de la **réalité mixte** dans le menu actions rapides qui s’affiche. |
| Faire pivoter | Déplacer le stick analogique vers la gauche ou vers la droite. | Déplacez le levier droit vers la gauche ou la droite. | Non disponible. |
| Sauvegarder | Déplacez le stick analogique vers l’arrière. | Déplacez le levier gauche vers l’arrière. | Non disponible. |
| Marcher | Poussez le stick analogique vers le bas, puis appuyez dessus dans la direction que vous souhaitez parcourir. | Poussez le levier gauche vers le bas, puis appuyez dessus dans la direction que vous souhaitez parcourir. | Non disponible. |
| Déplacer une fenêtre d’application | Pointez sur la barre de l’application. Tirez et maintenez enfoncé le déclencheur pour saisir la fenêtre, puis utilisez le contrôleur pour le déplacer dans n’importe quelle direction. Libère le déclencheur. | Pointez le curseur sur la barre de l’application, puis appuyez sur la touche et maintenez-la enfoncée pour récupérer la fenêtre. Utilisez le levier gauche pour déplacer la fenêtre côte à côte ou vers le haut ou vers le haut. Utilisez les déclencheurs pour le rapprocher et l’éloigner. Puis, Libérez un. | Pointez la souris sur la barre de l’application. Cliquez avec le bouton gauche et maintenez la touche enfoncée pour saisir la fenêtre, puis utilisez la souris pour la déplacer côte à côte ou vers le haut ou vers le haut. Utilisez la roulette de défilement pour déplacer la fenêtre plus près ou plus loin. Relâchez le bouton de la souris. |
| Déplacer un objet 3D | Pointez sur l’objet, puis tirez et maintenez le déclencheur pour le récupérer. Déplacez-le dans n’importe quelle direction avec le contrôleur, puis libérez le déclencheur. | Pointez avec le regard de l’objet, puis appuyez et maintenez une touche enfoncée pour le récupérer. Utilisez le levier gauche pour déplacer la fenêtre côte à côte ou vers le haut ou vers le haut. Utilisez les déclencheurs pour le rapprocher et l’éloigner. Puis, Libérez un. | Pointez la souris sur l’objet. Cliquez avec le bouton gauche et maintenez la touche enfoncée pour la récupérer, puis utilisez la souris pour la déplacer côte à côte ou vers le haut ou vers le haut.  Pour le rapprocher ou le éloigner, utilisez la roulette de défilement. Relâchez le bouton de la souris. |
| Faire pivoter ou redimensionner une fenêtre d’application | Pointez un contrôleur dans la barre de l’application et l’autre contrôleur n’importe où dans la fenêtre. Maintenez les deux déclencheurs enfoncé, puis redimensionnez les contrôleurs ou séparez-les.  Pour faire pivoter, déplacez un contrôleur vers vous et l’autre vous-même. Libérez les déclencheurs. | Sélectionnez **ajuster** dans la barre de l’application. Pointez le regard sur un coin du frame de réglage, puis appuyez sur A pour le sélectionner. Utilisez le levier gauche pour redimensionner la fenêtre.  | Sélectionnez **ajuster** dans la barre de l’application. Sélectionnez un coin du frame de réglage et maintenez-le enfoncé, puis utilisez la souris pour redimensionner la fenêtre. |
| Faire pivoter ou redimensionner un objet 3D | Pointez les deux contrôleurs au niveau de l’objet. Maintenez les deux déclencheurs enfoncé, puis redimensionnez les contrôleurs ou séparez-les.  Pour faire pivoter, déplacez un contrôleur vers vous et l’autre vous-même. | Sélectionnez **ajuster** dans la barre de l’application, puis déplacez l’objet à l’aide du stick gauche. | Sélectionnez **ajuster** dans la barre de l’application, puis sélectionnez et maintenez l’objet et utilisez la souris pour le déplacer. |
| Faire défiler la fenêtre d’une application | Tirez et maintenez enfoncé le déclencheur, puis déplacez le contrôleur vers le haut ou vers le haut.  | Utilisez le pavé numérique. | Utilisez la roulette de défilement de la souris. |
| Zoom avant ou arrière dans la fenêtre d’application | Tirez les deux déclencheurs, puis rapprochez les contrôleurs ou éloignez-les. | Tirez le déclencheur droit pour effectuer un zoom avant et le déclencheur gauche pour effectuer un zoom arrière. | Utilisez la roulette de défilement de la souris tout en maintenant la touche CTRL enfoncée sur le clavier. |
| Ouvrir un menu | Appuyez sur le bouton de **menu** . | Appuyez sur le bouton de **menu** . | Cliquez avec le bouton droit. |

## <a name="what-do-the-vibrations-and-lights-mean"></a>Signification des vibrations et des lumières

Votre contrôleur vous communique ce qu’il fait en vibrant et en faisant clignoter ses lumières LED.

|  En cas de fonctionnement de votre contrôleur  |  Cela signifie que cela |
| --- | --- |
| Les LED allument et le contrôleur vibre une fois | **Activation** |  
| Les LED éteignent et le contrôleur vibre deux fois | **Désactivation** |
| Clignotement de LED toutes les 3 secondes | **En état de veille** |
| Clignotement clignotant et le contrôleur vibre une fois | **Entrée en mode de jumelage** |
| Le contrôleur vibre une fois | **Connexion ou déconnexion de votre PC** |
| Les LED sont éclairées | **Contrôleurs suivis par le casque** |
| Les LED sont dimly allumés | **Contrôleurs non suivis par le casque** |
| Le contrôleur vibre trois fois, puis éteint | **Niveau de batterie critique** |
| Les anneaux externes et internes des LED clignotent dans un modèle de remplacement | **Mise à jour** |

## <a name="updating-motion-controllers-firmware"></a>Mise à jour du microprogramme des contrôleurs de mouvement

* Si un casque immersif est connecté à votre PC et que le nouveau microprogramme du contrôleur est disponible, le microprogramme est automatiquement envoyé à vos contrôleurs de mouvement la prochaine fois qu’ils sont allumés.
* Les mises à jour du microprogramme du contrôleur sont affichées avec un modèle de quadrants lumineux lumineux dans un mouvement circulaire et prennent 1-2 minutes. Les mises à jour de microprogramme peuvent parfois prendre plus de temps, jusqu’à 10 minutes, ce qui peut indiquer une mauvaise connectivité Bluetooth ou des interférences radio.
* En cas d’interruption de la mise à jour du microprogramme (contrôle hors tension ou batterie), une nouvelle tentative est effectuée lors de la prochaine mise sous tension.
* Une fois la mise à jour du microprogramme terminée, les contrôleurs redémarrent et se reconnectent.
* Les deux contrôleurs doivent être connectés maintenant. Accédez au portail de réalité mixte pour vérifier l’état de vos contrôleurs.
* Vérifiez que vos contrôleurs fonctionnent correctement :
  * Lancez le **portail de réalité mixte** et entrez votre page d’hébergement de la réalité mixte.
  * Déplacez vos contrôleurs et vérifiez le suivi, les boutons de test et vérifiez que la téléportage fonctionne. Si ce n’est pas le cas, consultez [la section résolution des problèmes du contrôleur de mouvement](motion-controller-problems.md)

## <a name="faq"></a>Questions fréquentes (FAQ)

### <a name="how-can-i-check-battery-level"></a>Comment puis-je vérifier le niveau de la batterie ?

*R : le niveau de la batterie est à l’inverse du modèle virtuel, il n’y a pas d’indicateur de niveau de batterie physique. Après la mise sous tension du contrôleur, attendez quelques secondes pour laisser la lecture se stabiliser.*

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Pouvez-vous utiliser ces contrôleurs sans casque ? Uniquement pour la manette de jeu/déclencheur/etc.

*R : pas pour les applications Windows universelles*

## <a name="filing-motion-controller-feedbackbugs"></a>Profilage de commentaires/bogues du contrôleur de mouvement

Faites-nous part de vos commentaires dans le hub de commentaires à l’aide de la catégorie « > d’entrée de réalité mixte ».

## <a name="see-also"></a>Voir aussi

- [Contrôleurs HP dans Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
- [Contrôleurs HP inréel](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
- [Demander à la communauté](https://answers.microsoft.com)
- [Contactez-nous pour obtenir de l’aide](https://support.microsoft.com/contactus/)
- [Dépannage](troubleshooting-windows-mixed-reality.md)

Vous rencontrez des problèmes avec vos contrôleurs de mouvement ? [Obtenir de l’aide](motion-controller-problems.md)