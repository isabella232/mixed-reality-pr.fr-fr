---
title: WinRT dans Unreal
description: Découvrez comment écrire et gérer des fonctionnalités WinRT personnalisées dans des applications de réalité mixte non réelles pour les appareils HoloLens.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, streaming, communication à distance, réalité mixte, développement, prise en main, fonctionnalités, nouveau projet, émulateur, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité Windows mixte, casque de réalité virtuelle, WinRT, DLL
ms.openlocfilehash: f32b5b3ddbee2e24e61d08b0a1b887b7b06e6da4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580400"
---
# <a name="winrt-in-unreal"></a>WinRT dans Unreal

Au cours de votre développement HoloLens, vous devrez peut-être écrire une fonctionnalité à l’aide de WinRT. Par exemple, l’ouverture d’une boîte de dialogue de fichier dans une application HoloLens nécessiterait FileSavePicker dans le fichier d’en-tête WinRT/Windows. Storage. Pickrs. h. WinRT est pris en charge dans le système de génération inréel à partir de la version 4,26 et versions ultérieures.

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous explorez actuellement les API et les fonctionnalités de la plateforme Mixed Reality. À partir de là, vous pouvez accéder à n’importe quelle [rubrique](unreal-development-overview.md#3-advanced-features) ou passer directement au déploiement de votre application sur un appareil ou un émulateur.

> [!div class="nextstepaction"]
> [Déploiement sur un appareil](unreal-deploying.md)

## <a name="see-also"></a>Voir aussi

* [API C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)
* [FileSavePicker, classe](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Bibliothèques tierces non réelles](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)