---
title: Implémenter des lanceurs d’applications 3D (applications Win32)
description: découvrez comment créer des programmes de lancement et des logos d’applications en 3d pour les applications et les jeux Win32 VR pour le menu Démarrer et l’environnement de bureau.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icône, modélisation, lanceur, lanceur 3D, vignette, cube en direct, Win32, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, manifeste
ms.openlocfilehash: 60eb4f543f287e833033c8e1852e2a85c6040d3c76455aadaca4b37c0a632573
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198765"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Implémenter des lanceurs d’applications 3D (applications Win32)

> [!NOTE]
> cette fonctionnalité n’est disponible que pour les pc qui exécutent les derniers vols [Windows insider](https://insider.windows.com) (RS5), build 17704 et versions ultérieures.

la [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) à la base est le point de départ où les utilisateurs se trouvent avant de lancer des applications. par défaut, vous devez lancer des applications et des jeux Win32 VR en dehors du casque et ne pas apparaître dans la liste « toutes les applications » sur le menu Démarrer Windows Mixed Reality. si vous suivez les instructions de cet article pour implémenter un lanceur d’applications 3d, votre expérience Win32 VR peut être lancée à partir de la Windows Mixed Reality menu Démarrer et de l’environnement d’hébergement.

Cela n’est valable que pour les expériences Win32 VR de l’eau, distribuées en dehors de la vapeur. pour les expériences VR [distribuées par vapeur](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md), nous avons [mis à jour le Windows Mixed Reality pour SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) , ainsi que les Windows derniers vols RS5 insider afin que les titres de SteamVR s’affichent dans le Windows Mixed Reality menu Démarrer dans la liste « toutes les applications » à l’aide d’un lanceur par défaut. en d’autres termes, la méthode décrite dans cet article n’est pas nécessaire pour les titres SteamVR et sera remplacée par le Windows Mixed Reality pour la fonctionnalité bêta SteamVR.

## <a name="3d-app-launcher-creation-process"></a>processus de création du lanceur d’applications 3D

La création d’un lanceur d’applications 3D comporte trois étapes :
1. [Conception et concept](3d-app-launcher-design-guidance.md)
2. [Modélisation et exportation](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Intégration dans votre application (cet article)

les ressources 3d à utiliser comme lanceurs pour votre application doivent être créées à l’aide des [instructions de création de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) pour garantir la compatibilité. les ressources qui ne satisfont pas à cette spécification de création ne seront pas affichées dans la Windows Mixed Reality page d’hébergement.

## <a name="configuring-the-3d-launcher"></a>Configuration du lanceur 3D

les applications Win32 s’affichent dans la liste « toutes les applications » sur le menu Démarrer Windows Mixed Reality si vous créez un lanceur d’application 3d pour eux. pour ce faire, créez un fichier [manifeste d’éléments visuels](/previous-versions/windows/apps/dn393983(v=win.10)) référençant le Lanceur d’application 3d en procédant comme suit :

1. créer un **fichier d’application 3d Lanceur asset GLB** (voir [modélisation et exportation](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Créez un **[manifeste d’éléments visuels](/previous-versions/windows/apps/dn393983(v=win.10))** pour votre application.
    1. Vous pouvez commencer par l' [exemple ci-dessous](#sample-visual-elements-manifest).  Pour plus d’informations, consultez la documentation complète du [manifeste des éléments visuels](/previous-versions/windows/apps/dn393983(v=win.10)) .
    2. Mettez à jour **Square150x150Logo** et **Square70x70Logo** avec un fichier PNG/jpg/gif pour votre application.
        * ils seront utilisés pour le logo 2d de l’application dans la liste Windows Mixed Reality toutes les applications et pour le Menu démarrer sur le bureau.
        * Le chemin d’accès du fichier est basé sur le dossier contenant le manifeste des éléments visuels.
        * Vous devez toujours fournir une icône de menu Démarrer du Bureau pour votre application via les mécanismes standard. Celui-ci peut être directement dans l’exécutable ou dans le raccourci que vous créez. Par exemple, via IShellLink :: SetIconLocation.
        * *Facultatif :* Vous pouvez utiliser un fichier Resources. pri si vous souhaitez que le fichier MRT fournisse plusieurs tailles de ressources pour différentes échelles de résolution et des thèmes à contraste élevé.
    3. mettez à jour le **chemin d’accès MixedRealityModel** pour qu’il pointe vers la GLB pour votre application 3d Lanceur
    4. Enregistrez le fichier sous le même nom que votre fichier exécutable, avec l’extension « .VisualElementsManifest.xml », puis enregistrez-le dans le même répertoire. Par exemple, pour le fichier exécutable « contoso.exe », le fichier XML associé est nommé « contoso.visualelementsmanifest.xml ».
3. **ajoutez un raccourci** à votre application dans le Menu démarrer du Windows de bureau. Consultez l’exemple [ci-dessous](#sample-app-launcher-shortcut-creation) pour obtenir un exemple d’implémentation C++. 
    * créez-le dans%ALLUSERSPROFILE%\Microsoft\ Windows \menu démarrer \, ou%APPDATA%\Microsoft\ Windows \menu démarrer \ \ programme (utilisateur)
    * Si une mise à jour modifie votre manifeste d’éléments visuels ou les ressources référencées par celle-ci, le programme d’installation ou le programme d’installation doit mettre à jour le raccourci de telle sorte que le manifeste soit analysé et que les ressources mises en cache soient mises à jour.
4. *Facultatif :* Si votre raccourci de bureau ne pointe pas directement vers l’exécutable de votre application (par exemple, s’il appelle un gestionnaire de protocole personnalisé comme « myapp:// »), le menu Démarrer ne trouvera pas automatiquement le fichier VisualElementsManifest.xml de l’application. Pour résoudre ce cas, le raccourci doit spécifier le chemin d’accès du fichier manifeste des éléments visuels à l’aide de System. AppUserModel. VisualElementsManifestHintPath (). Cela peut être défini dans le raccourci en utilisant les mêmes techniques que System.AppUserModel.ID. Vous n’êtes pas obligé d’utiliser System.AppUserModel.ID, mais vous pouvez le faire si vous souhaitez que le raccourci corresponde à l’ID de modèle utilisateur d’application explicite de l’application, le cas échéant.  Consultez la section exemple de création d’un [raccourci de lancement d’application](#sample-app-launcher-shortcut-creation) ci-dessous pour obtenir un exemple C++.

### <a name="sample-visual-elements-manifest"></a>Exemple de manifeste d’éléments visuels

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>Exemple de création de raccourci de lancement d’application

L’exemple de code ci-dessous montre comment vous pouvez créer un raccourci en C++, y compris le remplacement du chemin d’accès au fichier XML du manifeste des éléments visuels. Notez que le remplacement n’est nécessaire que dans les cas où votre raccourci ne pointe pas directement vers l’EXE associé au manifeste (par exemple, votre raccourci utilise un gestionnaire de protocole personnalisé comme « myapp:// »).

#### <a name="sample-lnk-shortcut-creation-c"></a>Exemple. LNK création d’un raccourci (C++)

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>Exemple. Raccourci du lanceur d’URL 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>Voir aussi

* [Exemple de modèle de réalité mixte](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenant un lanceur d’application 3D.
* [Guide de conception du lanceur d’applications 3D](3d-app-launcher-design-guidance.md)
* [création de modèles 3d à utiliser dans la Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implémentation de lanceurs d’applications en 3D (applications UWP)](implementing-3d-app-launchers.md)
* [Exploration de la page d’accueil Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)