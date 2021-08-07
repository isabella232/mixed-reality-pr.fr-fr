---
title: Accessoires matériels
description: décrit les types d’accessoires disponibles à utiliser avec Windows Mixed Reality, et comment les configurer.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: Guide pratique, accessoires, Bluetooth, BT, contrôleur, boîtier de commande, clic, Xbox, matériel, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, contrôleur de mouvement
ms.openlocfilehash: a6776df9374fce3f1399de944be06c93ff6fdcb3e6f4a38dcc92453556857376
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188452"
---
# <a name="hardware-accessories"></a>Accessoires matériels

les appareils Windows Mixed Reality prennent en charge les accessoires. vous pouvez utiliser des Bluetooth ou des ports USB pour coupler des accessoires pris en charge à un casque immersif de votre PC.

pour plus d’informations sur l’utilisation de Bluetooth accessoires avec HoloLens, consultez [Connecter pour Bluetooth et les périphériques USB-C](/hololens/hololens-connect-devices).

Windows Mixed Reality les casques immersifs nécessitent des accessoires pour les entrées au-delà du point de vue [et de la](../design/gaze-and-commit.md) [voix](../design/voice-input.md). Les accessoires pris en charge incluent le **clavier et la souris**, le **boîtier de soumanette** et les **[contrôleurs de mouvement](../design/motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>association des accessoires Bluetooth

le couplage d’un Bluetooth périphérique à l’aide d’un casque immersif est semblable au couplage d’un périphérique Bluetooth à un ordinateur de bureau Windows 10 ou à un appareil mobile :

1. dans le Menu démarrer, ouvrez l’application **Paramètres**
2. Accéder aux **appareils**
3. activer la radio Bluetooth si elle est désactivée à l’aide du commutateur slider
4. placez votre appareil Bluetooth en mode d’appairage. ce processus varie d’un appareil à l’autre, mais sur la plupart des appareils Bluetooth appuyez et maintenez un ou plusieurs boutons enfoncés.
5. attendez que le nom de l’appareil apparaisse dans la liste des appareils Bluetooth. Dans ce cas, sélectionnez l’appareil, puis sélectionnez le bouton de **paire** . si vous avez de nombreux Bluetooth périphériques à proximité, vous devrez peut-être faire défiler le curseur vers le bas de la liste des appareils Bluetooth pour voir l’appareil que vous essayez de coupler.
6. lorsque vous associez Bluetooth périphériques à une capacité d’entrée (par exemple : Bluetooth claviers), un code pin à 6 ou 8 chiffres peut s’afficher. Veillez à taper cette broche sur le périphérique, puis appuyez sur entrée pour terminer le jumelage avec le casque.

## <a name="motion-controllers"></a>Contrôleurs de mouvement

les [contrôleurs de mouvement](../design/motion-controllers.md) Windows Mixed Reality sont pris en charge par les casques immersifs, mais pas HoloLens. Ces contrôleurs offrent un suivi des mouvements précis et réactif dans votre champ de vue. Les capteurs du casque immersif effectuent le suivi, ce qui signifie qu’il n’est pas nécessaire d’installer le matériel sur les murs de votre espace. Chaque contrôleur est doté de plusieurs méthodes d’entrée.

![contrôleurs de mouvement Windows Mixed Reality](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>claviers Bluetooth

les claviers de Bluetooth en anglais Qwerty peuvent être couplés et utilisés partout où vous pouvez utiliser le clavier holographique. l’obtention d’un clavier de qualité fait une différence. nous vous recommandons donc d’utiliser le [clavier pliable universel microsoft](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) ou le [concepteur microsoft Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>boîtiers de Bluetooth

Vous pouvez utiliser un contrôleur avec des applications et des jeux qui activent spécifiquement la prise en charge du boîtier de commande. les boîtiers de commande ne peuvent pas être utilisés pour contrôler l’interface utilisateur HoloLens.

les contrôleurs de réseau sans fil Xbox fournis avec la Xbox One S ou vendus comme accessoires pour la fonctionnalité de Xbox One S Bluetooth connectivité, vous pouvez les utiliser avec des HoloLens et des casques immersifs. Le contrôleur sans fil Xbox [doit être mis à jour](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) avant de pouvoir être utilisé avec HoloLens.

d’autres marques de Bluetooth peuvent fonctionner avec des appareils Windows Mixed Reality, mais la prise en charge varie selon l’application.

## <a name="other-bluetooth-accessories"></a>autres accessoires Bluetooth

tant que le périphérique prend en charge les profils Bluetooth HID ou GATT, il peut être associé à HoloLens. d’autres Bluetooth les appareils HID et GATT, en plus du clavier, de la souris et du clic HoloLens, peuvent nécessiter une application auxiliaire sur Microsoft HoloLens pour être entièrement fonctionnelle.

Les périphériques non pris en charge sont les suivants :

* les périphériques dans les profils audio Bluetooth ne sont pas pris en charge.
* Bluetooth les périphériques audio, tels que les haut-parleurs et les casques, peuvent être disponibles dans l’application Paramètres, mais ne sont pas pris en charge avec Microsoft HoloLens comme point de terminaison audio.
* les téléphones et les pc compatibles Bluetooth ne sont pas pris en charge pour le jumelage et les transferts de fichiers.

## <a name="unpairing-a-bluetooth-peripheral"></a>découplage d’un périphérique Bluetooth

1. dans le Menu démarrer, ouvrez l’application **Paramètres**
2. Accéder aux **appareils**
3. activer la radio Bluetooth si elle est désactivée
4. rechercher votre appareil dans la liste des appareils Bluetooth disponibles
5. Sélectionnez votre appareil dans la liste, puis cliquez sur le bouton **supprimer** .