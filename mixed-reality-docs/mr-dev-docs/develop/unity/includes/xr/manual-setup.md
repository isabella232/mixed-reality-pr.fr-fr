---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112536160"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Installez le plug-in OpenXR avec la nouvelle application outil de la fonctionnalité de réalité mixte. Suivez les [instructions d’installation et d’utilisation](../../welcome-to-mr-feature-tool.md) , puis sélectionnez le package de **plug-in OpenXR de réalité mixte** dans la catégorie **prise en charge** de la plateforme :

![Fenêtre packages de l’outil de réalité mixte avec plug-in Open XR mis en surbrillance](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Définition de votre cible de génération

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :

1. Sélectionner le **fichier > les paramètres de Build...**
2. Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3. Définissez **Architecture** sur **ARM64**.
4. Définissez **Target device** sur **HoloLens**.
5. Définissez **Build Type** sur **D3D Project**.
6. Définir la **version du SDK cible** sur le **dernier installé**

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configuration de la gestion des plug-ins XR pour OpenXR

Pour définir OpenXR comme Runtime dans Unity :

1. Dans l’éditeur Unity, accédez à **modifier > paramètres du projet**
2. Dans la liste des paramètres, sélectionnez **gestion des plug-ins XR**
3. Sélectionnez **installer la gestion des plug-ins XR** s’il s’agit ![ d’une capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in](../../images/wmr-config-img-5.png)
4. Cochez la case **Initialize XR on Startup** .
5. Si vous ciblez Desktop VR, restez sur l’onglet autonome du PC (le moniteur) et cochez les cases de l’ensemble de fonctionnalités **OpenXR** et **Windows Mixed Reality** .
6. Si vous ciblez HoloLens 2, basculez vers l’onglet plateforme Windows universelle (le logo Windows), puis sélectionnez les zones ensemble de fonctionnalités **OpenXR** et **Microsoft HoloLens** .

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](../../images/openxr-img-05.png)

> [!IMPORTANT]
> Si vous voyez une icône d’avertissement jaune en regard du **plug-in OpenXR**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer. L’éditeur Unity devra peut-être redémarrer pour que les modifications prennent effet.

![Capture d’écran de la fenêtre de validation du projet OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

Si vous développez pour HoloLens 2, sélectionnez le **projet > de la réalité mixte > appliquer les paramètres de projet recommandés pour** l’élément de menu HoloLens 2 afin d’obtenir de meilleures performances d’application.

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](../../images/openxr-img-08.png)

Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !  Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Exemples de projets Unity pour OpenXR et HoloLens 2

Consultez les [exemples de référentiel OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) pour les exemples de projets Unity montrant comment créer des applications Unity pour des casques HoloLens 2 ou de réalité mixte à l’aide du plug-in OpenXR de la réalité mixte.

Ou, si vous êtes prêt à commencer par vous-même à partir d’un projet vide, passez à l’article Configuration de l' [appareil photo](../../camera-in-unity.md) .

# <a name="windows-xr"></a>[XR Windows](#tab/windowsxr)

> [!CAUTION]
> Le plug-in XR Windows est déconseillé dans Unity 2021,1 et sera supprimé dans Unity 2021,2.  Pour le développement Unity 2020, Microsoft recommande le plug-in OpenXR à la place.

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :

1.  Sélectionner le **fichier > les paramètres de Build...**
2.  Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3.  Définissez **Architecture** sur **ARM64**.
4.  Définissez **Target device** sur **HoloLens**.
5.  Définissez **Build Type** sur **D3D Project**.
6.  Définir la **version du SDK cible** sur le **dernier installé**
7.  Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D quand elle est exportée :

1. Dans l’éditeur Unity, accédez à **modifier > paramètres du projet** , puis sélectionnez **gestion du plug-in XR**

2. Sélectionnez **installer la gestion des plug-ins XR** si elle apparaît

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](../../images/wmr-config-img-5.png)

3. Sélectionnez **initialiser XR au démarrage** et **Windows Mixed Reality**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](../../images/wmr-config-img-7.png)

4. Sélectionnez la section **gestion du plug-in XR**  >  **Windows Mixed Reality** , cochez toutes les cases et définissez le format de la **mémoire tampon** de profondeur sur le **tampon de profondeur 16 bits**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section Windows Mixed Reality mise en surbrillance](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[XR antérieur](#tab/legacy)

> [!CAUTION]
> Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :

1.  Sélectionner le **fichier > les paramètres de Build...**
2.  Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3.  Définissez **Architecture** sur **ARM64**.
4.  Définissez **Target device** sur **HoloLens**.
5.  Définissez **Build Type** sur **D3D Project**.
6.  Définir la **version du SDK cible** sur le **dernier installé**
7.  Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.

1. Ouvrir les **paramètres du lecteur...** à partir des paramètres de **Build... et** développez le groupe de **paramètres XR**
2. Dans la section **paramètres XR** , sélectionnez la **réalité virtuelle prise en charge** pour ajouter la liste des appareils de réalité virtuelle
3. Définissez le **format de profondeur** sur **16 bits** et cochez **activer le partage du tampon de profondeur**
4. Définissez **Stereo Rendering Mode** (Mode de rendu stéréo) sur **Single Pass Instanced** (Instance à passe unique).
5. Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser l’accès distant en mode de lecture holographique

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres du lecteur mise en surbrillance](../../images/wmr-config-img-9.png)
