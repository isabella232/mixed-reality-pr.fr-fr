---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638730"
---
# <a name="all-platforms"></a>[<span data-ttu-id="15665-101">Toutes les plateformes</span><span class="sxs-lookup"><span data-stu-id="15665-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="15665-102">Les mêmes mappages d’action et d’axe dans les paramètres de projet d’entrée du jeu peuvent être utilisés à partir de C++.</span><span class="sxs-lookup"><span data-stu-id="15665-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="15665-103">Créer une nouvelle classe C++ avec fichier/nouvelle classe C++...</span><span class="sxs-lookup"><span data-stu-id="15665-103">Create a new C++ Class with File/New C++ Class...</span></span>

![Création d’une classe C++](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="15665-105">Créer un pion</span><span class="sxs-lookup"><span data-stu-id="15665-105">Create a pawn</span></span>

![Création d’un pion](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="15665-107">Dans la solution Visual Studio du projet, recherchez la nouvelle classe pion et configurez-la pour l’entrée.</span><span class="sxs-lookup"><span data-stu-id="15665-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="15665-108">Tout d’abord, dans le constructeur, définissez AutoPossessPlayer sur le premier joueur pour router l’entrée vers le pion.</span><span class="sxs-lookup"><span data-stu-id="15665-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="15665-109">Ensuite, dans SetupPlayerInputComponent, liez les actions et les événements d’axe aux noms d’action à partir des paramètres d’entrée du projet.</span><span class="sxs-lookup"><span data-stu-id="15665-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="15665-110">Ajoutez les fonctions de rappel à la classe :</span><span class="sxs-lookup"><span data-stu-id="15665-110">Add the callback functions to the class:</span></span>

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

* <span data-ttu-id="15665-111">Mettez à jour l’en-tête du pion avec les définitions de fonction de rappel :</span><span class="sxs-lookup"><span data-stu-id="15665-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="15665-112">Compilez à partir de Visual Studio pour lancer l’éditeur avec le nouveau pion.</span><span class="sxs-lookup"><span data-stu-id="15665-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="15665-113">Glissez-déposez le pion du navigateur de contenu dans le jeu et le pion exécutera maintenant les rappels lorsque l’utilisateur appuie sur l’entrée.</span><span class="sxs-lookup"><span data-stu-id="15665-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="15665-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="15665-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="15665-115">Lors de l’utilisation d’événements d’axe Joystick, le nom de l’événement d’axe doit se terminer par « _X » ou « _Y » correspondant à la clé utilisée.</span><span class="sxs-lookup"><span data-stu-id="15665-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![Utilisation d’événements Stick](../images/reverb-g2-img-09.png)

<span data-ttu-id="15665-117">Enfin, enregistrez les actions dans le jeu avec SteamVR à l’aide des boutons **régénérer le manifeste d’action** et **régénérer les liaisons de contrôleur** dans les paramètres du projet > entrée Steam VR.</span><span class="sxs-lookup"><span data-stu-id="15665-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![Inscription des actions dans les paramètres du projet](../images/reverb-g2-img-10.png)

