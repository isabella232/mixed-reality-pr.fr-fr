---
title: Portage d’applications VR sur Windows Mixed Reality
description: Une procédure pas à pas explique comment porter une application immersif existante vers Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: port, unity, inreal, middleware, engine, UWP, Win32, portage, HoloLens 1ère génération, casque de réalité mixte, casque de réalité windows mixte, migration, Windows 10, mappage d’entrée,
ms.openlocfilehash: c8f0ed76fc7288ed406e2044eb2f3edb8982865b5c956f460d2bc1b815e503df
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213509"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Portage d’applications VR sur Windows Mixed Reality

Windows 10 prend en charge les casques immersifs et holographiques. Si vous avez créé du contenu pour d’autres appareils tels que le Rift ou le HTC Oculus, ils ont des dépendances avec les bibliothèques qui existent au-dessus de l’API de plateforme du système d’exploitation. la réintégration des applications Win32 unity en cours à Windows Mixed Reality implique le reciblage de l’utilisation des kits de développement logiciel (sdk) de vr spécifiques au fournisseur pour les api vr inter-fournisseurs de unity.

## <a name="porting-requirements"></a>Conditions requises pour le portage

À un niveau élevé, les étapes suivantes sont impliquées dans le portage du contenu existant :
1. **assurez-vous que votre ordinateur exécute le Windows 10 Fall Creators Update (16299).** Nous vous déconseillons de recevoir des builds préliminaires à partir de la sonnerie d’inversion anticipée, car ces builds ne sont pas les plus stables pour le développement de la réalité mixte.
2. **Effectuez une mise à niveau vers la dernière version de votre graphique ou de votre moteur de jeux.** les moteurs de jeu devront prendre en charge le kit de développement logiciel (SDK) Windows 10 version 10.0.15063.0 (publiée en avril 2017) ou une version ultérieure.
3. **Mettez à niveau les intergiciel, les plug-ins ou les composants.** Si votre application contient des composants, il est judicieux de procéder à une mise à niveau vers la dernière version.
4. **Supprimer les dépendances sur les kits de développement logiciel en double**. en fonction de l’appareil ciblé par votre contenu, vous devez supprimer ou compiler de façon conditionnelle ce kit de développement logiciel pour pouvoir cibler les api Windows à la place. SteamVR est un exemple de ce scénario.
5. **Résoudre les problèmes de génération.** À ce stade, l’exercice de Portage est spécifique à votre application, à votre moteur et aux dépendances de composants dont vous disposez.

## <a name="common-porting-steps"></a>Étapes de Portage courantes

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Assurez-vous de disposer du bon matériel de développement

La page du [Guide du passionné de VR](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) répertorie le matériel de développement recommandé.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. effectuez une mise à niveau vers le dernier vol de Windows 10

la plateforme Windows Mixed Reality est toujours en cours de développement actif. nous vous recommandons de [rejoindre le programme Windows insider](https://insider.windows.com/) pour accéder au vol « Windows insider Fast ».
1. installer le [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [rejoignez](https://insider.windows.com/) le programme Windows insider.
3. Activer le [mode développeur](/windows/uwp/get-started/enable-your-device-for-development)
4. basculez vers le [Windows vols rapides](/archive/blogs/uktechnet/joining-insider-preview) à l’intérieur de **Paramètres > Section sécurité de & de la mise à jour**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. effectuez une mise à niveau vers la build la plus récente de Visual Studio
* si vous utilisez Visual Studio, effectuez une mise à niveau vers la build la plus récente
* consultez [la page installer les outils](../install-the-tools.md#installation-checklist) sous Visual Studio 2019

### <a name="4-choose-the-correct-adapter"></a>4. Choisissez l’adaptateur approprié
* Dans les systèmes tels que les blocs-notes avec deux GPU, [Ciblez l’adaptateur approprié](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Cela s’applique aux applications d’Unity et DirectX natives où un ID3D11Device est créé, explicitement ou implicitement (Media Foundation), pour ses fonctionnalités.

## <a name="unity-porting-guidance"></a>Guide de Portage Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Instructions sur le portage inréel

> [!IMPORTANT]
> Si vous utilisez des contrôleurs de reréverbérations HP G2, reportez-vous à [cet article](../unreal/unreal-reverb-g2-controllers.md) pour obtenir des instructions supplémentaires sur le mappage d’entrée.

## <a name="see-also"></a>Voir aussi
* [instructions relatives à la compatibilité minimale du matériel PC Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Comprendre les performances de la réalité mixte](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recommandations de performances pour unity](../unity/performance-recommendations-for-unity.md)
* [Contrôleurs de mouvement](../../design/motion-controllers.md)
* [Contrôleurs de mouvement dans Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guides de portage](porting-guides.md)