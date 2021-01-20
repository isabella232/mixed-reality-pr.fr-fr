---
title: Portage d’applications VR sur Windows Mixed Reality
description: Une procédure pas à pas expliquant comment porter une application immersive existante vers Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: port, Unity, inreal, middleware, Engine, UWP, Win32, Portage, HoloLens 1ère génération, casque de réalité mixte, casque Windows Mixed realisation, migration, Windows 10, mappage d’entrée,
ms.openlocfilehash: dd09c6479bfcf3659b3e9355be898d77bccc6dc6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580585"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Portage d’applications VR sur Windows Mixed Reality

Windows 10 prend en charge les casques immersifs et holographiques. Si vous avez créé du contenu pour d’autres appareils tels que le Rift ou le HTC Oculus, ils ont des dépendances avec les bibliothèques qui existent au-dessus de l’API de plateforme du système d’exploitation. L’intégration des applications Win32 Unity en cours à Windows Mixed Reality implique le reciblage de l’utilisation des kits de développement logiciel (SDK) de VR spécifiques au fournisseur pour les API VR inter-fournisseurs.

## <a name="porting-requirements"></a>Conditions requises pour le portage

À un niveau élevé, les étapes suivantes sont impliquées dans le portage du contenu existant :
1. **Assurez-vous que votre ordinateur exécute la mise à jour des créateurs de automne Windows 10 (16299).** Nous vous déconseillons de recevoir des builds préliminaires à partir de la sonnerie d’inversion anticipée, car ces builds ne sont pas les plus stables pour le développement de la réalité mixte.
2. **Effectuez une mise à niveau vers la dernière version de votre graphique ou de votre moteur de jeux.** Les moteurs de jeu doivent prendre en charge la version 10.0.15063.0 du kit de développement logiciel (SDK) Windows 10 (publiée en avril 2017) ou une version ultérieure.
3. **Mettez à niveau les intergiciel, les plug-ins ou les composants.** Si votre application contient des composants, il est judicieux de procéder à une mise à niveau vers la dernière version.
4. **Supprimer les dépendances sur les kits de développement logiciel en double**. En fonction de l’appareil ciblé par votre contenu, vous devez supprimer ou compiler de façon conditionnelle ce kit de développement logiciel pour pouvoir cibler les API Windows à la place. SteamVR est un exemple de ce scénario.
5. **Résoudre les problèmes de génération.** À ce stade, l’exercice de Portage est spécifique à votre application, à votre moteur et aux dépendances de composants dont vous disposez.

## <a name="common-porting-steps"></a>Étapes de Portage courantes

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Assurez-vous de disposer du bon matériel de développement

La page [installer les outils](../install-the-tools.md#immersive-vr-headset-requirements) répertorie le matériel de développement recommandé.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. effectuez une mise à niveau vers le dernier vol de Windows 10

La plateforme Windows Mixed Reality est toujours en cours de développement. Nous vous recommandons de [rejoindre le programme Windows Insider](https://insider.windows.com/) pour accéder au vol « Windows Insider Fast ».
1. Installer [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Participez](https://insider.windows.com/) au programme Windows Insider.
3. Activer le [mode développeur](/windows/uwp/get-started/enable-your-device-for-development)
4. Basculer vers les [vols rapides Windows Insider](/archive/blogs/uktechnet/joining-insider-preview) via les **paramètres > section mettre à jour la sécurité &**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. effectuez une mise à niveau vers la version la plus récente de Visual Studio
* Si vous utilisez Visual Studio, effectuez une mise à niveau vers la build la plus récente
* Consultez [installer la page outils](../install-the-tools.md#installation-checklist) sous Visual Studio 2019

### <a name="4-choose-the-correct-adapter"></a>4. Choisissez l’adaptateur approprié
* Dans les systèmes tels que les blocs-notes avec deux GPU, [Ciblez l’adaptateur approprié](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Cela s’applique aux applications d’Unity et DirectX natives où un ID3D11Device est créé, explicitement ou implicitement (Media Foundation), pour ses fonctionnalités.

## <a name="unity-porting-guidance"></a>Guide de Portage Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Instructions sur le portage inréel

> [!IMPORTANT]
> Si vous utilisez des contrôleurs de reréverbérations HP G2, reportez-vous à [cet article](../unreal/unreal-reverb-g2-controllers.md) pour obtenir des instructions supplémentaires sur le mappage d’entrée.

## <a name="see-also"></a>Voir aussi
* [Instructions de compatibilité matérielle PC minimale pour Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Comprendre les performances de la réalité mixte](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recommandations en matière de performances pour Unity](../unity/performance-recommendations-for-unity.md)
* [Contrôleurs de mouvement](../../design/motion-controllers.md)
* [Contrôleurs de mouvement dans Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guides de portage](porting-guides.md)