---
title: API WinRT avec Unity pour HoloLens
description: plus épurée comment utiliser les api WinRT et l’espace de noms Windows dans vos projets de réalité mixte unity pour les HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, procédure pas à pas, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, API de réalité mixte
ms.openlocfilehash: 158c28d9186269108442226bbfcfc90a3c235a71336fdab9dbf9eadc21a309a1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215605"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>API WinRT avec Unity pour HoloLens

Cette page explique comment utiliser les API WinRT dans votre projet Unity pour HoloLens.

## <a name="mixed-reality-apis"></a>API de réalité mixte

un sous-ensemble axé sur la réalité mixte du SDK Windows a été mis à disposition dans une projection .NET Standard compatible 2,0, que vous pouvez utiliser dans votre projet sans les directives de préprocesseur. La plupart des API du Windows. Perception et Windows. L'. Les espaces de noms Input. spatial sont inclus et peuvent être étendus pour inclure des API supplémentaires à l’avenir. Les API projetées peuvent être utilisées lors de l’exécution dans l’éditeur, ce qui permet l’utilisation du [mode de lecture](/windows/mixed-reality/unity-play-mode). Pour utiliser cette projection, apportez les modifications suivantes à votre projet :

1) Ajoutez une référence à [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package utilisant [NuGet pour unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Préfixez les références à l' `Windows` espace de noms avec `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Remplacez les casts de pointeur natifs par `FromNativePtr` :
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Inclure de manière conditionnelle les appels d’API WinRT

vous pouvez également utiliser les api WinRT dans les projets unity générés pour la plateforme plateforme Windows universelle et Xbox One à l’aide de directives de préprocesseur. Tout code que vous écrivez dans des scripts Unity qui ciblent des API WinRT doit être inclus de manière conditionnelle pour les builds uniquement. 

Pour ce faire, vous pouvez effectuer deux étapes dans Unity :
1) Le niveau de compatibilité de l’API doit être défini sur **.net 4,6** ou **.NET standard 2,0** dans les paramètres du lecteur
    - **Modifier**  >  **Project Paramètres**  >  **Lecteur**  >  **Configuration**  >  de **Niveau de compatibilité** de l’API vers **.net 4,6** ou **.NET standard 2,0**
2) La directive de préprocesseur **ENABLE_WINMD_SUPPORT** doit être entourée de tout code utilisant WinRT

l’extrait de code suivant provient de la page manuelle unity pour [plateforme Windows universelle : API WinRT dans les scripts C#](https://docs.unity3d.com/Manual/windowsstore-scripts.html). dans cet exemple, un ID de publicité est retourné, mais uniquement sur UWP et Xbox One builds :

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Modifier vos scripts dans un projet Unity C#

Lorsque vous double-cliquez sur un script dans l’éditeur Unity, le script est lancé par défaut dans un projet de l’éditeur. les api WinRT semblent être inconnues, car le projet Visual Studio ne fait pas référence à la Windows Runtime. la directive **ENABLE_WINMD_SUPPORT** est non définie et tout code *#if* encapsulé est ignoré jusqu’à ce que vous génériez votre projet dans une solution de Visual Studio UWP.

## <a name="see-also"></a>Voir aussi
* [Exportation et création de solutions Unity Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Unité de prise en charge du Runtime](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)