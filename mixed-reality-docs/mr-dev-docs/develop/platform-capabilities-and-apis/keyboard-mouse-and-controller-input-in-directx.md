---
title: Saisie à l’aide de la commande de jeu, du clavier et de la souris dans DirectX
description: Explique comment créer une application pour Windows Mixed Reality qui utilise le clavier, la souris et les contrôleurs de jeu.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, clavier, souris, contrôleur de jeu, contrôleur Xbox, HoloLens, Desktop, procédure pas à pas, exemple de code
ms.openlocfilehash: 3cf35ba195e839332cbedb8b2c3945334a158cbc
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583629"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="727df-104">Saisie à l’aide de la commande de jeu, du clavier et de la souris dans DirectX</span><span class="sxs-lookup"><span data-stu-id="727df-104">Keyboard, mouse, and controller input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="727df-105">Cet article s’applique aux API natives WinRT héritées.</span><span class="sxs-lookup"><span data-stu-id="727df-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="727df-106">Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](../native/openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="727df-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)**.</span></span>

<span data-ttu-id="727df-107">Les claviers, les souris et les contrôleurs de jeu peuvent être des formes d’entrée utiles pour les appareils Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="727df-107">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="727df-108">Les claviers et souris Bluetooth sont pris en charge sur HoloLens, pour être utilisés avec le débogage de votre application ou comme une autre forme d’entrée.</span><span class="sxs-lookup"><span data-stu-id="727df-108">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="727df-109">Windows Mixed Reality prend également en charge les casques immersifs attachés à des PC, où les souris, les claviers et les contrôleurs de jeu étaient traditionnellement la norme.</span><span class="sxs-lookup"><span data-stu-id="727df-109">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="727df-110">Pour utiliser l’entrée au clavier sur HoloLens, couplez un clavier Bluetooth à votre appareil ou utilisez une entrée virtuelle via le portail de périphériques Windows.</span><span class="sxs-lookup"><span data-stu-id="727df-110">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="727df-111">Pour utiliser l’entrée au clavier tout en portant un casque immersif Windows Mixed Reality, affectez le focus d’entrée à la réalité mixte en plaçant sur l’appareil ou en utilisant la combinaison de touches Windows + Y.</span><span class="sxs-lookup"><span data-stu-id="727df-111">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="727df-112">Gardez à l’esprit que les applications destinées à HoloLens doivent fournir des fonctionnalités sans que ces appareils soient attachés.</span><span class="sxs-lookup"><span data-stu-id="727df-112">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="727df-113">Les extraits de code de cet article illustrent actuellement l’utilisation de C++/CX au lieu des/WinRT C++ conformes à C + +17, tels qu’ils sont utilisés dans le [modèle de projet holographique c++](../native/creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="727df-113">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="727df-114">Les concepts sont équivalents pour un projet C++/WinRT, bien que vous deviez traduire le code.</span><span class="sxs-lookup"><span data-stu-id="727df-114">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="727df-115">S’abonner aux événements d’entrée CoreWindow</span><span class="sxs-lookup"><span data-stu-id="727df-115">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="727df-116">Entrée de clavier</span><span class="sxs-lookup"><span data-stu-id="727df-116">Keyboard input</span></span>

<span data-ttu-id="727df-117">Dans le modèle d’application holographique Windows, nous incluons un gestionnaire d’événements pour l’entrée au clavier comme n’importe quelle autre application UWP.</span><span class="sxs-lookup"><span data-stu-id="727df-117">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="727df-118">Votre application utilise les données d’entrée au clavier de la même façon dans Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="727df-118">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="727df-119">À partir de AppView. cpp :</span><span class="sxs-lookup"><span data-stu-id="727df-119">From AppView.cpp:</span></span>

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a><span data-ttu-id="727df-120">Entrée au clavier virtuel</span><span class="sxs-lookup"><span data-stu-id="727df-120">Virtual keyboard input</span></span>
<span data-ttu-id="727df-121">Pour les casques de bureau immersifs, vous pouvez prendre en charge des claviers virtuels rendus par Windows sur votre vue immersif en implémentant **CoreTextEditContext**.</span><span class="sxs-lookup"><span data-stu-id="727df-121">For immersive desktop headsets, you can support virtual keyboards rendered by Windows over your immersive view by implementing **CoreTextEditContext**.</span></span> <span data-ttu-id="727df-122">Cela permet à Windows de comprendre l’état de vos propres zones de texte de rendu d’application, de sorte que le clavier virtuel puisse contribuer correctement au texte.</span><span class="sxs-lookup"><span data-stu-id="727df-122">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="727df-123">Pour plus d’informations sur l’implémentation de la prise en charge de CoreTextEditContext, consultez l' [exemple CoreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="727df-123">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="727df-124">Entrée de la souris</span><span class="sxs-lookup"><span data-stu-id="727df-124">Mouse Input</span></span>

<span data-ttu-id="727df-125">Vous pouvez également utiliser l’entrée de la souris, à nouveau via les gestionnaires d’événements d’entrée UWP CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="727df-125">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="727df-126">Voici comment modifier le modèle d’application holographique Windows pour prendre en charge les clics de souris de la même façon que les gestes appuyés.</span><span class="sxs-lookup"><span data-stu-id="727df-126">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="727df-127">Une fois cette modification effectuée, un clic de souris tout en faisant passer un périphérique de casque immersif repositionne le cube.</span><span class="sxs-lookup"><span data-stu-id="727df-127">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

> [!NOTE]
> <span data-ttu-id="727df-128">Les applications UWP peuvent également obtenir des données brutes XY pour la souris à l’aide de l’API [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) .</span><span class="sxs-lookup"><span data-stu-id="727df-128">UWP apps can also get raw XY data for the mouse by using the [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="727df-129">Commencez par déclarer un nouveau gestionnaire OnPointerPressed dans AppView. h :</span><span class="sxs-lookup"><span data-stu-id="727df-129">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="727df-130">Dans AppView. cpp, ajoutez ce code à SetWindow :</span><span class="sxs-lookup"><span data-stu-id="727df-130">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="727df-131">Placez ensuite cette définition pour OnPointerPressed en bas du fichier :</span><span class="sxs-lookup"><span data-stu-id="727df-131">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

<span data-ttu-id="727df-132">Le gestionnaire d’événements que nous venons d’ajouter est un transfert vers la classe principale du modèle.</span><span class="sxs-lookup"><span data-stu-id="727df-132">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="727df-133">Modifions la classe principale pour prendre en charge ce transfert.</span><span class="sxs-lookup"><span data-stu-id="727df-133">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="727df-134">Ajoutez cette déclaration de méthode publique au fichier d’en-tête :</span><span class="sxs-lookup"><span data-stu-id="727df-134">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="727df-135">Vous aurez également besoin de cette variable de membre privé :</span><span class="sxs-lookup"><span data-stu-id="727df-135">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="727df-136">Enfin, nous allons mettre à jour la classe principale avec la nouvelle logique pour prendre en charge les clics de souris.</span><span class="sxs-lookup"><span data-stu-id="727df-136">Finally, we'll update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="727df-137">Commencez par ajouter ce gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="727df-137">Start by adding this event handler.</span></span> <span data-ttu-id="727df-138">Veillez à mettre à jour le nom de la classe :</span><span class="sxs-lookup"><span data-stu-id="727df-138">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="727df-139">Maintenant, dans la méthode de mise à jour, remplacez la logique existante pour obtenir un pointeur à l’aide de ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="727df-139">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="727df-140">Recompilez et redéployez.</span><span class="sxs-lookup"><span data-stu-id="727df-140">Recompile and redeploy.</span></span> <span data-ttu-id="727df-141">Notez que le clic de souris va à présent repositionner le cube dans votre casque immersif ou HoloLens avec la souris Bluetooth associée.</span><span class="sxs-lookup"><span data-stu-id="727df-141">Notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="727df-142">Prise en charge des contrôleurs de jeu</span><span class="sxs-lookup"><span data-stu-id="727df-142">Game controller support</span></span>

<span data-ttu-id="727df-143">Les contrôleurs de jeu peuvent être un moyen amusant et pratique de permettre à l’utilisateur de contrôler une expérience Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="727df-143">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

 <span data-ttu-id="727df-144">Ajoutez les déclarations de membre privées suivantes à la classe d’en-tête de votre fichier principal :</span><span class="sxs-lookup"><span data-stu-id="727df-144">add the following private member declarations to the header class for your main file:</span></span>

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

<span data-ttu-id="727df-145">Initialisez les événements de manette de main et tous les boîtiers de connexion actuellement attachés dans le constructeur de votre classe principale :</span><span class="sxs-lookup"><span data-stu-id="727df-145">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

<span data-ttu-id="727df-146">Ajoutez ces gestionnaires d’événements à votre classe principale.</span><span class="sxs-lookup"><span data-stu-id="727df-146">Add these event handlers to your main class.</span></span> <span data-ttu-id="727df-147">Veillez à mettre à jour le nom de la classe :</span><span class="sxs-lookup"><span data-stu-id="727df-147">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

<span data-ttu-id="727df-148">Enfin, mettez à jour la logique d’entrée pour reconnaître les modifications de l’état du contrôleur.</span><span class="sxs-lookup"><span data-stu-id="727df-148">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="727df-149">Ici, nous utilisons la même m_pointerPressed variable traitée dans la section ci-dessus pour ajouter des événements de souris.</span><span class="sxs-lookup"><span data-stu-id="727df-149">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="727df-150">Ajoutez-la à la méthode Update, juste avant l’emplacement où elle recherche le SpatialPointerPose :</span><span class="sxs-lookup"><span data-stu-id="727df-150">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="727df-151">N’oubliez pas d’annuler l’inscription des événements lors du nettoyage de la classe principale :</span><span class="sxs-lookup"><span data-stu-id="727df-151">Don't forget to unregister the events when cleaning up the main class:</span></span>

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

<span data-ttu-id="727df-152">Recompilez et redéployez.</span><span class="sxs-lookup"><span data-stu-id="727df-152">Recompile, and redeploy.</span></span> <span data-ttu-id="727df-153">Vous pouvez maintenant attacher un contrôleur de jeu, ou le coupler, et l’utiliser pour repositionner le cube en rotation.</span><span class="sxs-lookup"><span data-stu-id="727df-153">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="727df-154">Indications importantes pour l’entrée au clavier et à la souris</span><span class="sxs-lookup"><span data-stu-id="727df-154">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="727df-155">Il existe quelques différences clés dans la façon dont ce code peut être utilisé sur Microsoft HoloLens, qui est un appareil qui s’appuie principalement sur l’entrée d’utilisateur naturelle, par rapport à ce qui est disponible sur un PC Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="727df-155">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="727df-156">Vous ne pouvez pas vous appuyer sur l’entrée du clavier ou de la souris.</span><span class="sxs-lookup"><span data-stu-id="727df-156">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="727df-157">Toutes les fonctionnalités de votre application doivent fonctionner avec le regard, le geste et l’entrée vocale.</span><span class="sxs-lookup"><span data-stu-id="727df-157">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="727df-158">Lorsqu’un clavier Bluetooth est attaché, il peut être utile d’activer l’entrée au clavier pour tout texte que votre application peut demander.</span><span class="sxs-lookup"><span data-stu-id="727df-158">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="727df-159">Il peut s’agir d’un excellent complément pour la dictée, par exemple.</span><span class="sxs-lookup"><span data-stu-id="727df-159">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="727df-160">Lorsqu’il s’agit de concevoir votre application, ne vous fiez pas (par exemple) aux contrôles WASD et Mouse pour votre jeu.</span><span class="sxs-lookup"><span data-stu-id="727df-160">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="727df-161">HoloLens est conçu pour permettre à l’utilisateur de parcourir la salle.</span><span class="sxs-lookup"><span data-stu-id="727df-161">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="727df-162">Dans ce cas, l’utilisateur contrôle directement l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="727df-162">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="727df-163">Une interface pour la conduite de l’appareil photo autour de la salle avec des contrôles de déplacement/d’apparence n’offre pas la même expérience.</span><span class="sxs-lookup"><span data-stu-id="727df-163">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="727df-164">L’entrée au clavier est un excellent moyen de contrôler le débogage de votre application ou du moteur de jeu, en particulier dans la mesure où l’utilisateur n’est pas obligé d’utiliser le clavier.</span><span class="sxs-lookup"><span data-stu-id="727df-164">Keyboard input is an excellent way to control your app or game engine debugging, especially since the user won't be required to use the keyboard.</span></span> <span data-ttu-id="727df-165">Son câblage est identique à celui que vous utilisez avec les API d’événement CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="727df-165">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="727df-166">Dans ce scénario, vous pouvez choisir d’implémenter un moyen de configurer votre application pour acheminer les événements de clavier vers un mode « en entrée de débogage uniquement » pendant vos sessions de débogage.</span><span class="sxs-lookup"><span data-stu-id="727df-166">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="727df-167">Les contrôleurs Bluetooth fonctionnent également.</span><span class="sxs-lookup"><span data-stu-id="727df-167">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="727df-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="727df-168">See also</span></span>
* [<span data-ttu-id="727df-169">Accessoires matériels</span><span class="sxs-lookup"><span data-stu-id="727df-169">Hardware accessories</span></span>](../../discover/hardware-accessories.md)