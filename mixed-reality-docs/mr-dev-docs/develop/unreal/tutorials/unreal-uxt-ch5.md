---
title: 5. Ajout d’un bouton et réinitialisation des positions des pièces
description: Partie 5 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 8e16865e89c06c37f2932f1828bf8ca5551e6fce
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609690"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Ajout d’un bouton et réinitialisation des positions des pièces

Dans le tutoriel précédent, vous avez ajouté des acteurs d’interaction manuelle aux composants Pawn et Manipulator de l’échiquier pour les rendre interactifs. Dans cette section, vous allez continuer à utiliser le plug-in Mixed Reality Toolkit UX Tools pour créer votre application de jeu d’échecs avec de nouvelles fonctions et des références d’acteur dans des blueprints. À la fin de cette section, vous serez prêt à empaqueter et déployer l’application de réalité mixte sur un appareil ou un émulateur.

## <a name="objectives"></a>Objectifs

* Ajouter un bouton interactif
* Créer une fonction pour réinitialiser l’emplacement d’une pièce
* Lier le bouton pour déclencher la fonction quand l’utilisateur appuie dessus

## <a name="creating-a-reset-function"></a>Création d’une fonction de réinitialisation

Votre première tâche consiste à créer un blueprint de fonction qui remet une pièce d’échec à sa position d’origine dans la scène.

1.  Ouvrez **WhiteKing**, sélectionnez l’icône **+** en regard de la section **Functions** de **My Blueprint**, puis nommez-le **Reset Location**.

2.  Faites glisser l’exécution de **Drag and release** vers la grille Blueprint pour créer un nœud **SetActorRelativeTransform**.
    * Cette fonction définit la transformation (position, rotation et échelle) d’un acteur par rapport à son parent. Vous allez utiliser cette fonction pour réinitialiser la position du roi sur l’échiquier, même si celui-ci a été déplacé de sa position d’origine.

3. Cliquez avec le bouton droit dans le graphique d’événements, sélectionnez **Make Transform**, puis déplacez-le en définissant le paramètre **Location** comme suit : **X =-26**, **Y = 4**, **Z = 0**.
    * Connectez sa valeur de retour (**Return Value**) au repère **New Relative Transform** dans **SetActorRelativeTransform**.

![Fonction Reset Location](images/unreal-uxt/5-function.PNG)

**Compilez** et **enregistrez** le projet avant de revenir à la fenêtre principale.


## <a name="adding-a-button"></a>Ajouter un bouton

Maintenant que la fonction est correctement configurée, la tâche suivante consiste à créer un bouton qui la déclenche quand le joueur appuie dessus.

1.  Cliquez sur **Add New > Blueprint Class**, développez la section **All Classes**, puis recherchez **UxtPressableButtonActor**.
    * Nommez ce bouton **ResetButton** et double-cliquez pour ouvrir le blueprint.

![Sous-classe du nouveau Blueprint à partir du bouton de style HoloLens 2](images/unreal-uxt/5-subclass.PNG)

2. Vérifiez que **ResetButton(self)** est sélectionné dans le volet **Components**. Dans le volet **Details**, accédez à la section **Button**. Changez le **Button Label** par défaut en « Reset », développez la section **Button Icon Brush** et appuyez sur le bouton **Open Icon Brush Editor**.

![Définir l’étiquette et l’icône sur le bouton](images/unreal-uxt/5-buttonconfig.PNG)

L’éditeur Icon Brush s’ouvre, que vous pouvez utiliser pour sélectionner une nouvelle icône pour votre bouton.

![Sélectionner une icône pour le bouton](images/unreal-uxt/5-iconbrusheditor.PNG)

Vous pouvez ajuster de nombreux autres paramètres pour configurer votre bouton. Pour en savoir plus sur le composant UXT Pressable Button, consultez la [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).

3. Cliquez sur **ButtonComponent (Inherited)** dans le panneau **Components** et faites défiler le volet **Details** vers le bas jusqu’à la section **Events**.
    * Cliquez sur le bouton vert **+** à côté de **On Button Pressed** pour ajouter un événement au graphique d’événements, qui est appelé quand le joueur appuie sur le bouton.

À partir de là, vous devez appeler la fonction **Reset Location** de **WhiteKing**, qui a besoin d’une référence à l’acteur **WhiteKing** dans le niveau.

4.  Dans le volet **My Blueprint**, accédez à la section **Variables**, cliquez sur le bouton **+** et nommez la variable **WhiteKing**.
    * Dans le volet **Details**, sélectionnez la liste déroulante à côté de **Variable Type**, recherchez **WhiteKing**, puis sélectionnez **Object Reference**.
    * Cochez la case à côté de **Instance Editable**, qui permet de définir la variable à partir du niveau principal.

![Créer une variable](images/unreal-uxt/5-var.PNG)

5.  Faites glisser la variable WhiteKing de **My Blueprint > Variables** vers le graphique d’événements de Reset Button et choisissez **Get WhiteKing**.

## <a name="firing-the-function"></a>Déclenchement de la fonction

Il ne reste plus qu’à déclencher expressément la fonction de réinitialisation dès lors que le joueur appuie sur le bouton.

1.  Faites glisser la broche de sortie WhiteKing et relâchez-la pour placer un nouveau nœud. Sélectionnez la fonction **Reset Location**. Pour finir, faites glisser la broche d’exécution sortante depuis **On Button Pressed** vers la broche d’exécution entrante sur **Reset Location**. **Compilez** et **enregistrez** le Blueprint ResetButton, puis revenez dans la fenêtre principale.

![Appeler la fonction Reset Location à partir de l’événement On Button Pressed](images/unreal-uxt/5-callresetloc.PNG)

2.  Faites glisser **ResetButton** vers la fenêtre Viewport et définissez son emplacement sur **X = 50**, **Y = -25** et **Z = 10**. Définissez sa rotation comme ceci : **Z = 180**. Sous **Default**, attribuez à la variable **WhiteKing** la valeur **WhiteKing**.

![Définir la variable](images/unreal-uxt/5-buttonlevel.PNG)

Exécutez l’application, déplacez la pièce d’échec vers son nouvel emplacement, puis appuyez sur le bouton de style HoloLens 2 pour voir la logique de réinitialisation en action.

Votre application de réalité mixte comporte maintenant un échiquier et une pièce avec laquelle vous pouvez interagir, et un bouton entièrement opérationnel qui réinitialise la position de la pièce. Vous trouverez l’application à ce stade d’avancement dans son dépôt [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp). N’hésitez pas à aller au-delà de ce tutoriel et à configurer les autres pièces du jeu d’échecs en faisant en sorte que l’échiquier se réinitialise entièrement quand vous appuyez sur le bouton de réinitialisation.

![Scène finale dans la fenêtre Viewport](images/unreal-uxt/5-endscene.PNG)

Vous êtes prêt à passer à la dernière section de ce tutoriel, où vous allez découvrir comment empaqueter et déployer l’application sur un appareil ou un émulateur.

> [!IMPORTANT]
> À ce stade, vous devez mettre à jour votre projet avec les **[paramètres de performances Unreal](../performance-recommendations-for-unreal.md)** recommandés avant de déployer votre application sur un appareil ou un émulateur.

[Section suivante : 6. Empaquetage et déploiement sur un appareil ou un émulateur](unreal-uxt-ch6.md)
