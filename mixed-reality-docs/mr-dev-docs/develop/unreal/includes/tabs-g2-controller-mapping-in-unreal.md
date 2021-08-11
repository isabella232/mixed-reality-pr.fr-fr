---
ms.openlocfilehash: 4dde9dcb34553e1ad39d9c732f32f9d0ef174eaf2a6b6fbe7b59b8fdc9facf8d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204196"
---
# <a name="all-platforms"></a>[Toutes les plateformes](#tab/all)

Les mêmes mappages d’action et d’axe dans les paramètres de projet d’entrée du jeu peuvent être utilisés à partir de C++.

1. Créer une nouvelle classe C++ avec fichier/nouvelle classe C++...

![Création d’une classe C++](../images/reverb-g2-img-11.png)

2. Créer un pion

![Création d’un pion](../images/reverb-g2-img-12.png)

3. dans la solution Visual Studio du projet, recherchez la nouvelle classe pion et configurez-la pour l’entrée.
* Tout d’abord, dans le constructeur, définissez AutoPossessPlayer sur le premier joueur pour router l’entrée vers le pion.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* Ensuite, dans SetupPlayerInputComponent, liez les actions et les événements d’axe aux noms d’action à partir des paramètres d’entrée du projet.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* Ajoutez les fonctions de rappel à la classe :

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* Mettez à jour l’en-tête du pion avec les définitions de fonction de rappel :

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. compilez à partir de Visual Studio pour lancer l’éditeur avec le nouveau pion. Glissez-déposez le pion du navigateur de contenu dans le jeu et le pion exécutera maintenant les rappels lorsque l’utilisateur appuie sur l’entrée.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

Lors de l’utilisation d’événements d’axe Joystick, le nom de l’événement d’axe doit se terminer par « _X » ou « _Y » correspondant à la clé utilisée.

![Utilisation d’événements Stick](../images/reverb-g2-img-09.png)

enfin, enregistrez les actions dans le jeu avec SteamVR à l’aide des boutons **régénérer le manifeste d’Action** et **régénérer les liaisons de contrôleur** dans Project Paramètres > entrée Steam.

![Inscription des actions dans les paramètres du projet](../images/reverb-g2-img-10.png)

