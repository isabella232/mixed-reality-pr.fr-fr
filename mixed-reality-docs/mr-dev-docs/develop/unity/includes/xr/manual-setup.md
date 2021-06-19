---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394583"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Installez le plug-in OpenXR avec la nouvelle application outil de la fonctionnalité de réalité mixte. Suivez les [instructions d’installation et d’utilisation](../../welcome-to-mr-feature-tool.md) , puis sélectionnez le package de **plug-in OpenXR de la réalité mixte** dans la catégorie de la réalité mixte Toolkit :

![Fenêtre packages de l’outil de réalité mixte avec plug-in Open XR mis en surbrillance](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Définition de votre cible de génération

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :

1. Sélectionner le **fichier > les paramètres de Build...**
2. Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3. Définissez **Architecture** sur **ARM 64**.
4. Définissez **Target device** sur **HoloLens**.
5. Définissez **Build Type** sur **D3D**.
6. Définissez **UWP SDK** sur **Latest installed**.

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configuration de la gestion des plug-ins XR pour OpenXR

Pour définir OpenXR comme Runtime dans Unity :

1. Dans l’éditeur Unity, accédez à **modifier > paramètres du projet**
2. Dans la liste des paramètres, sélectionnez **gestion des plug-ins XR**
3. Cochez les cases **Initialize XR on Startup** et **OpenXR**
4. Si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez **ensemble de fonctionnalités Microsoft HoloLens** .

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](../../images/openxr-img-05.png)

### <a name="optimization"></a>Optimization

Si vous développez pour HoloLens 2, accédez à la **réalité mixte> OpenXR > appliquer les paramètres de projet recommandés pour HoloLens 2** afin d’obtenir de meilleures performances d’application.

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](../../images/openxr-img-08.png)

> [!IMPORTANT]
> Si vous voyez une icône d’avertissement jaune en regard du **plug-in OpenXR**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer. L’éditeur Unity devra peut-être redémarrer pour que les modifications prennent effet.

![Capture d’écran de la fenêtre de validation du projet OpenXR](../../images/openxr-img-06.png)

Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !  Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Exemples de projets Unity pour OpenXR et HoloLens 2

Consultez les [exemples de référentiel OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) pour les exemples de projets Unity montrant comment créer des applications Unity pour des casques HoloLens 2 ou de réalité mixte à l’aide du plug-in OpenXR de la réalité mixte.

# <a name="windows-xr"></a>[XR Windows](#tab/windowsxr)

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :

1.  Sélectionner le **fichier > les paramètres de Build...**
2.  Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3.  Définissez **Architecture** sur **ARM 64**.
4.  Définissez **Target device** sur **HoloLens**.
5.  Définissez **Build Type** sur **D3D**.
6.  Définissez **UWP SDK** sur **Latest installed**.
7.  Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D quand elle est exportée :

1. Dans l’éditeur Unity, accédez à **modifier > paramètres du projet** , puis sélectionnez **gestion du plug-in XR**

2. Sélectionnez **installer la gestion des plug-ins XR**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](../../images/wmr-config-img-5.png)

3. Sélectionnez **initialiser XR au démarrage** et **Windows Mixed Reality**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](../../images/wmr-config-img-7.png)

4. Développez la section **gestion du plug-in XR** et sélectionnez universels onglet Paramètres de la **plateforme Windows** .
5. Si vous utilisez Unity 2020 ou une version ultérieure, vous verrez les options permettant de vérifier **OpenXR** ou **Windows Mixed Reality**. 
    * Vous pouvez choisir l’un ou l’autre Runtime.  Si vous développez spécifiquement pour HoloLens 2 ou la réverbération HP G2 et que vous décidez d’essayer le **OpenXR**, sélectionnez la zone OpenXR et passez en revue notre guide pour [utiliser le plug-in OpenXR de réalité mixte pour Unity](../../openxr-getting-started.md) afin de vous préparer correctement pour ces appareils avant de revenir à ce didacticiel.

> [!NOTE]
> À partir de Unity 2020 LTS, Microsoft adopte le développement avec OpenXR.  À mesure que nous migrons vers ce chemin, dans Unity 2021,1, le plug-in Windows XR sera déconseillé et supprimé dans 2021,2, OpenXR le seul chemin pris en charge. Vous trouverez plus d’informations dans [utilisation du plug-in OpenXR de la réalité mixte](../../openxr-getting-started.md).

6. Si vous décidez de choisir le plug-in **Windows Mixed Reality** , cochez toutes les cases et définissez le **mode d’envoi de profondeur** sur une profondeur de **16 bits**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section Windows Mixed Reality mise en surbrillance](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[XR antérieur](#tab/legacy)

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :

1.  Sélectionner le **fichier > les paramètres de Build...**
2.  Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3.  Définissez **Architecture** sur **ARM 64**.
4.  Définissez **Target device** sur **HoloLens**.
5.  Définissez **Build Type** sur **D3D**.
6.  Définissez **UWP SDK** sur **Latest installed**.
7.  Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.

> [!CAUTION]
> Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.

1. Ouvrir les **paramètres du lecteur...** à partir des paramètres de **Build... et** développez le groupe de **paramètres XR**
2. Dans la section **paramètres XR** , sélectionnez la **réalité virtuelle prise en charge** pour ajouter la liste des appareils de réalité virtuelle
3. Définir le **format de profondeur** sur **16 bits** et activer le partage de **mémoire tampon de profondeur**
4. Définir le **mode de rendu stéréo** sur **une seule instance de passage**
5. Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser la communication à distance holographique 

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres du lecteur mise en surbrillance](../../images/wmr-config-img-9.png)