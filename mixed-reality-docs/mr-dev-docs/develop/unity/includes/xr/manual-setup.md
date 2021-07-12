---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603712"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Installez le plug-in OpenXR avec la nouvelle application outil de la fonctionnalité de réalité mixte. Suivez les [instructions d’installation et d’utilisation](../../welcome-to-mr-feature-tool.md) , puis sélectionnez le package de **plug-in OpenXR de réalité mixte** dans la catégorie **prise en charge** de la plateforme :

![Fenêtre packages de l’outil de réalité mixte avec plug-in Open XR mis en surbrillance](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Définition de votre cible de génération

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

si vous ciblez HoloLens 2, vous devez basculer vers le plateforme Windows universelle :

1. sélectionner le **fichier > la Paramètres de Build...**
2. sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3. Définissez **Architecture** sur **ARM64**.
4. Définissez **Target device** sur **HoloLens**.
5. Définissez **Build Type** sur **D3D Project**.
6. Définir la **version du SDK cible** sur le **dernier installé**

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configuration de la gestion des plug-ins XR pour OpenXR

Pour définir OpenXR comme Runtime dans Unity :

1. dans l’éditeur unity, accédez à **modifier > Project Paramètres**
2. dans la liste des Paramètres, sélectionnez **gestion des plug-ins XR** (doit déjà être installé si vous avez installé le plug-in OpenXR de réalité mixte à l’aide de MRFT)
3. Cochez la case **Initialize XR on Startup** .
4. si vous ciblez Desktop VR, restez sur l’onglet autonome du PC (le moniteur) et cochez les cases **OpenXR** et **Windows Mixed Reality ensemble de fonctionnalités** .
5. si vous ciblez HoloLens 2, basculez vers l’onglet plateforme Windows universelle (le logo Windows) et sélectionnez les zones de **jeu de fonctionnalités** **OpenXR** et Microsoft HoloLens

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](../../images/openxr-img-05.png)

> [!IMPORTANT]
> Si vous voyez une icône d’avertissement jaune en regard du **plug-in OpenXR**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer. L’éditeur Unity devra peut-être redémarrer pour que les modifications prennent effet.

![Capture d’écran de la fenêtre de validation du projet OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

si vous développez pour HoloLens 2, sélectionnez l’élément de menu **> de réalité mixte Project > appliquer les paramètres de projet recommandés pour HoloLens 2** pour obtenir de meilleures performances d’application.

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](../../images/openxr-img-08.png)

Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !  Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Exemples de projets Unity pour OpenXR et HoloLens 2

consultez les [exemples de référentiel OpenXR Mixed reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) pour obtenir des exemples de projets unity montrant comment créer des applications unity pour HoloLens 2 ou des casques de réalité mixtes à l’aide du plug-in OpenXR de réalité mixte.

Ou, si vous êtes prêt à commencer par vous-même à partir d’un projet vide, passez à l’article Configuration de l' [appareil photo](../../camera-in-unity.md) .

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

> [!CAUTION]
> le plug-in Windows XR est déconseillé dans unity 2021,1 et sera supprimé dans unity 2021,2.  Pour le développement Unity 2020, Microsoft recommande le plug-in OpenXR à la place.

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

si vous ciblez HoloLens 2, vous devez basculer vers le plateforme Windows universelle :

1.  sélectionner le **fichier > la Paramètres de Build...**
2.  sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3.  Définissez **Architecture** sur **ARM64**.
4.  Définissez **Target device** sur **HoloLens**.
5.  Définissez **Build Type** sur **D3D Project**.
6.  Définir la **version du SDK cible** sur le **dernier installé**
7.  Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D quand elle est exportée :

1. dans l’éditeur unity, accédez à **modifier > paramètres Project** et sélectionnez **gestion du plug-in XR**

2. Sélectionnez **installer la gestion des plug-ins XR** si elle apparaît

![capture d’écran de la fenêtre de Paramètres Project ouverte dans l’éditeur unity avec la gestion du plug-in XR mise en évidence](../../images/wmr-config-img-5.png)

3. sélectionnez **initialize XR au démarrage** et **Windows Mixed Reality**

![capture d’écran de la fenêtre paramètres Project ouverte dans l’éditeur unity avec la gestion du plug-in XR mise en évidence](../../images/wmr-config-img-7.png)

4. sélectionnez la section Windows Mixed Reality **de la gestion du Plug-in XR**  >   , cochez toutes les cases et définissez le Format de la **mémoire tampon** de profondeur sur le **tampon de profondeur 16 bits**

![capture d’écran de la fenêtre paramètres Project ouverte dans l’éditeur unity avec la section Windows Mixed Reality mise en surbrillance](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[XR antérieur](#tab/legacy)

> [!CAUTION]
> Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

si vous ciblez HoloLens 2, vous devez basculer vers le plateforme Windows universelle :

1.  sélectionner le **fichier > la Paramètres de Build...**
2.  sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3.  Définissez **Architecture** sur **ARM64**.
4.  Définissez **Target device** sur **HoloLens**.
5.  Définissez **Build Type** sur **D3D Project**.
6.  Définir la **version du SDK cible** sur le **dernier installé**
7.  Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.

1. ouvrir le **Paramètres du lecteur...** à partir de la **Paramètres de Build... et** développez le groupe de **Paramètres XR**
2. dans la section **Paramètres XR** , sélectionnez **virtual reality pris en charge** pour ajouter la liste des appareils de réalité virtuelle
3. Définissez le **format de profondeur** sur **16 bits** et cochez **activer le partage du tampon de profondeur**
4. Définissez **Stereo Rendering Mode** (Mode de rendu stéréo) sur **Single Pass Instanced** (Instance à passe unique).
5. Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser l’accès distant en mode de lecture holographique

![capture d’écran de la fenêtre paramètres Project ouverte dans l’éditeur unity avec la section paramètres du lecteur mise en surbrillance](../../images/wmr-config-img-9.png)
