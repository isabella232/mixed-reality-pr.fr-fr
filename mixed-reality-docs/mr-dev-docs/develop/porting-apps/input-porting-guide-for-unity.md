---
title: Guide de portage des entrées pour Unity
description: Apprenez à gérer les entrées pour Windows Mixed Reality dans Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: entrée, Unity, Portage
ms.openlocfilehash: 97280ff260729bfc2042f7760fa3950e949e27a4
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613263"
---
# <a name="input-porting-guide-for-unity"></a>Guide de portage des entrées pour Unity

Vous pouvez porter votre logique d’entrée vers Windows Mixed Reality à l’aide de l’une des deux approches. La première consiste à utiliser les API d’entrée générale d’Unity. GetButton/GetAxis qui s’étendent sur plusieurs plateformes. La seconde est la XR spécifique à Windows. WSA. API d’entrée, qui offrent des données plus riches pour les contrôleurs de mouvement et les mains de HoloLens.

## <a name="general-inputgetbuttongetaxis-apis"></a>Entrées générales. GetButton/GetAxis API

Unity utilise actuellement ses API d’entrée. GetButton/Input. GetAxis pour exposer l’entrée pour [le kit de développement logiciel (SDK) Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) et [le kit de développement logiciel (SDK) OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Si vos applications utilisent déjà ces API pour l’entrée, les API Input. GetButton/Input. GetAxis sont les chemins les plus simples pour la prise en charge des contrôleurs de mouvement dans Windows Mixed Reality. Il vous suffit de remapper les boutons et les axes dans le gestionnaire d’entrée.

Pour plus d’informations, consultez le [tableau des mappages bouton Unity/AXIS](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) et [vue d’ensemble des API Unity courantes](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR spécifique à Windows. WSA. API d’entrée

Si votre application crée déjà une logique d’entrée personnalisée pour chaque plateforme, vous pouvez utiliser les API d’entrée spatiale spécifiques à Windows dans l’espace de noms **UnityEngine. XR. WSA. Input** . À partir de là, vous accédez à des informations supplémentaires, telles que la précision de la position ou le genre source, qui vous permettent de distinguer les mains et les contrôleurs de HoloLens.

Pour plus d’informations, consultez la [vue d’ensemble des API UnityEngine. XR. WSA. Input](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Poignée de pose et pose de pointage

Windows Mixed Reality prend en charge les contrôleurs de mouvement dans différents facteurs de forme. La conception de chaque contrôleur diffère dans sa relation entre la position de l’utilisateur et la direction « avant » naturelle que les applications doivent utiliser pour pointer lors du rendu du contrôleur.

Pour mieux représenter ces contrôleurs, il existe deux types de poses que vous pouvez examiner pour chaque source d’interaction :

* La **poignée pose**, qui représente l’emplacement de la paume d’une main détectée par un HoloLens ou la poche qui détient un contrôleur de mouvement.
    * Sur les casques immersifs, cette pose est idéale pour afficher **la main de l’utilisateur** ou **un objet détenu par l’utilisateur**, tel qu’un arme ou un pistolet.
    * Position de la **poignée**: le centre de la poche quand il maintient le contrôleur naturellement, ajusté à gauche ou à droite pour centrer la position au sein de la poignée.
    * **Axe droit de l’orientation de la poignée**: lorsque vous ouvrez complètement votre main pour former une pose plate à 5 doigts, le rayon normal à votre paume (en avant à partir de la poche de gauche, en arrière depuis la paume de droite)
    * **Axe avant de l’orientation de la poignée**: quand vous fermez partiellement la main, comme si vous détenir le contrôleur, le rayon qui pointe vers l’avant dans le tube formé par vos doigts non thumbs.
    * **Axe vers le haut de l’orientation**: l’axe vers le haut, impliqué dans les définitions Right et Forward.
    * Vous pouvez accéder à la poignée à l’aide de l’API d’entrée entre fournisseurs de l’unité Unity (**[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/rotation**) ou par le biais de l’API spécifique à Windows (**SourceState. SourcePose. TryGetPosition/rotation**, demandant la poignée pose).
* Le **pointeur se pose**, représentant l’extrémité du contrôleur pointant vers l’avant.
    * Cette solution est la mieux utilisée pour raycast quand vous **pointez sur l’interface utilisateur** lorsque vous affichez le modèle de contrôleur lui-même.
    * Actuellement, le pointeur pose est disponible uniquement par le biais de l’API spécifique à Windows (**sourceState. sourcePose. TryGetPosition/rotation**, demandant le pointeur pose).

Ces coordonnées de pose sont toutes exprimées en coordonnées universelles Unity.

## <a name="see-also"></a>Voir aussi
* [Contrôleurs de mouvement]().. /.. /design/motion-controllers.md)
* [Mouvements et contrôleurs de mouvement dans Unity](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guides de portage](porting-guides.md)
