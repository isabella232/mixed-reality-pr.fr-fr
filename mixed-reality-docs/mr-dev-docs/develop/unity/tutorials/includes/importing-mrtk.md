---
ms.openlocfilehash: 7fd590713322c296cbbb14e133b1085aa27bb0197b70d1feca1ecb59ed61a3c7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201404"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Une fois **MixedRealityFeatureTool** ouvert, cliquez sur **Démarrer** pour commencer à utiliser Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

La première étape consiste à faire pointer Mixed Reality Feature Tool sur votre **Chemin d’accès du projet** à l’aide du bouton représentant des **points de suspension**. Cliquez ensuite sur le bouton représentant des points de suspension à côté du chemin d’accès du projet et accédez à votre dossier de projet dans l’Explorateur. Par exemple : _D:\MixedRealityLearning\Tutoriels MRTK_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Une fois le dossier de votre projet localisé, cliquez sur le bouton Ouvrir pour revenir à Mixed Reality Feature Tool. Cliquez ensuite sur **Découvrir les fonctionnalités**.

> [!NOTE]
> La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier. Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.

> [!Important]
> Mixed Reality Feature Tool effectue la validation pour s’assurer qu’il a été dirigé vers un dossier de projet Unity. Le dossier doit contenir des dossiers Ressources, Packages et Paramètres du projet.

Les fonctionnalités sont regroupées par catégorie afin de faciliter leur recherche, cliquez sur la liste déroulante **Mixed Reality Toolkit** pour rechercher les packages relatifs à Mixed Reality Toolkit et cliquez sur la liste déroulante **Prise en charge de plateformes** pour rechercher des packages associant différentes plateformes de prise en charge.

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

Vérifiez la **Mixed Reality Toolkit Foundation** et cliquez sur la liste déroulante en regard de celle-ci afin de sélectionner **MRTK 2.7.2**, consultez également le **Plug-in Mixed Reality OpenXR 1.0.0**, puis cliquez sur la liste déroulante en regard de celui-ci pour sélectionner la version la plus récente disponible et cliquez ensuite sur le bouton **Obtenir des fonctionnalités** pour télécharger les packages sélectionnés.

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

Cliquez ensuite sur le bouton **Validate** pour valider le package sélectionné. Vous voyez une fenêtre contextuelle avec le message **No validation issues were detected** (Aucun problème de validation détecté). Cliquez sur **OK** pour fermer la fenêtre contextuelle, puis cliquez sur le bouton **Import**.

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


Cliquez sur le bouton **Approve** pour ajouter **Mixed Reality Toolkit** au projet.

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>Configuration du projet Unity

Une fois qu’Unity a fini d’importer le package à partir de la section précédente, un message d’avertissement s’affiche pour redémarrer l’éditeur Unity afin d’activer les backends pour le nouveau système de plug-in, cliquez sur **Oui**

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

Une fois qu’Unity redémarre, la fenêtre MRTK Project Configurator doit s’afficher. Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement en accédant à **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer projet pour MRTK** :

![Ouvrir la fenêtre MRTK Project Configurator](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

Cliquez sur le **plug-in OpenXR Unity** pour activer la gestion des plug-ins XR et ajouter les packages requis dans votre projet.

![Ajouter un plug-in OpenXR Unity ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

Cela permet d’importer les packages Unity requis pour la Gestion de plug-in XR. Lorsque vous avez terminé, cliquez sur **Afficher les paramètres de gestion de plug-in XR** dans MRTK Project Configurator.

![Afficher les paramètres de gestion de plug-in XR ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

La **fenêtre Paramètres du projet** s’ouvre. Dans la fenêtre Paramètres du projet, sous **Gestion de plug-in XR**, vérifiez que vous êtes dans les paramètres de la plateforme Windows universelle (onglet Logo de Windows). Assurez-vous également que l’option **Initialiser XR au démarrage** est cochée, puis cochez les cases **OpenXR** et **Ensemble de fonctionnalités Microsoft HoloLens** pour les activer.

![Activer Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

Une fois la case OpenXR cochée, la fenêtre MRTK Project Configurator affiche le message mis à jour avec le bouton **Appliquer les paramètres**. Cliquez sur le bouton **Appliquer les paramètres**. 

![Fenêtre Paramètres du projet 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

Lorsque vous cliquez sur Appliquer les paramètres, ce message d’erreur peut s’afficher dans la console. Vous pouvez poursuivre s’il s’agit de la seule erreur ou s’il n’y a aucune erreur.

![Message d’erreur de communication à distance OpenXR](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

Pour valider la configuration d’OpenXR, cliquez sur **OpenXR** sous **Gestion de plug-in XR** et vérifiez les éléments suivants :
* Mode d’envoi en profondeur : **Profondeur de 16 bits**
* Profils d’interaction : **Profil d’interaction manuelle Microsoft**

![Fenêtre Paramètres du projet 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> La réduction du format de profondeur à 16 bits est facultative, mais peut contribuer à améliorer les performances graphiques dans votre projet. Pour plus d’informations à ce sujet, reportez-vous à la section <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Partage de mémoire tampon de profondeur (HoloLens)</a> de la documentation sur les performances de MRTK.


Dans la fenêtre **MRTK Project Configurator**, cliquez sur **Suivant**, puis cliquez sur le bouton **Appliquer** pour appliquer les paramètres. (Si vous avez fermé la fenêtre, vous pouvez l’ouvrir manuellement en accédant à **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer un projet pour MRTK**)

![Fenêtre Paramètres du projet 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Fenêtre Paramètres du projet 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

Une fois que vous avez cliqué sur Appliquer, Unity tente de redémarrer pour que le système d’entrée prenne effet, cliquez sur **Appliquer** pour redémarrer l’éditeur Unity

### <a name="configure-additional-project-settings"></a>Configurer des paramètres de projet supplémentaires

Dans le menu Unity, sélectionnez **Edit (Modifier)** > **Project Settings (Paramètres du projet)...** pour ouvrir la fenêtre Project Settings (Paramètres du projet).

Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :

![Paramètres de publication Unity. Nom de package configuré](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Le « Package name » est l’identificateur unique de l’application. Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.

> [!TIP]
> « Product Name » est le nom affiché dans le menu Démarrer de HoloLens. Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in Windows XR](#tab/winxr)

Une fois **MixedRealityFeatureTool** ouvert, cliquez sur **Démarrer** pour commencer à utiliser Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

La première étape consiste à faire pointer Mixed Reality Feature Tool sur votre **Chemin d’accès du projet** à l’aide du bouton représentant des **points de suspension**. Cliquez ensuite sur le bouton représentant des points de suspension à côté du chemin d’accès du projet et accédez à votre dossier de projet dans l’Explorateur. Par exemple : _D:\MixedRealityLearning\Tutoriels MRTK_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


Une fois le dossier de votre projet localisé, cliquez sur le bouton Ouvrir pour revenir à Mixed Reality Feature Tool. Cliquez ensuite sur **Découvrir les fonctionnalités**.

> [!NOTE]
> La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier. Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.

> [!Important]
> Mixed Reality Feature Tool effectue la validation pour s’assurer qu’il a été dirigé vers un dossier de projet Unity. Le dossier doit contenir des dossiers Ressources, Packages et Paramètres du projet.

Les fonctionnalités sont regroupées par catégorie pour faciliter leur recherche. Cliquez sur la liste déroulante **Mixed Reality Toolkit** pour trouver les packages qui lui sont associés.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Cochez la case **Mixed Reality Toolkit Foundation** et cliquez sur la liste déroulante en regard de celle-ci pour sélectionner **MRTK 2.7.0**, puis cliquez sur le bouton **Obtenir des fonctionnalités** pour télécharger les packages sélectionnés.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Cliquez ensuite sur le bouton **Validate** pour valider le package sélectionné. Vous voyez une fenêtre contextuelle avec le message **No validation issues were detected** (Aucun problème de validation détecté). Cliquez sur **OK** pour fermer la fenêtre contextuelle, puis cliquez sur le bouton **Import**.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


Cliquez sur le bouton **Approve** pour ajouter **Mixed Reality Toolkit** au projet.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Configuration du projet Unity

Une fois que Unity a fini d’importer le package de la section précédente, la fenêtre MRTK Project Configurator doit s’afficher. Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement en accédant à **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer projet pour MRTK** :

![ouverture de l’outil de configuration MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

Cliquez sur le **plug-in Unity intégré (non-OpenXR)** pour activer la gestion de plug-in XR et ajouter les packages requis dans votre projet.

![ outil de configuration MRTK](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> La capture d’écran ci-dessus provient d’Unity 2020. Si vous utilisez Unity 2019, sélectionnez **Gestion XR SDK/XR**

Cela permet d’importer les packages Unity requis pour la gestion de plug-in XR. Une fois que vous avez terminé, cliquez sur **Afficher les paramètres** dans MRTK Project Configurator.

![Fenêtre Paramètres du lecteur](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

La **fenêtre Paramètres du projet** s’ouvre. Dans la fenêtre Paramètres du projet sous **Gestion de plug-in XR**, assurez-vous que vous êtes dans les paramètres de la plateforme Windows universelle et que l’option **Initialiser XR au démarrage** est cochée, puis cochez la case **Windows Mixed Reality**.

![Fenêtre Paramètres du lecteur - Activer la réalité mixte-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Une fois que Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre MRTK Project Configurator doit réapparaître. Si ce n’est pas le cas, utilisez le menu Unity pour l’ouvrir.

Dans la fenêtre MRTK Project Configurator, cliquez sur **Suivant**, puis utilisez la liste déroulante Spatializer audio pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Appliquer** pour appliquer le paramètre :

![MRTK project configurator-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :

> * Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin. Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de la documentation sur les [performances](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de MRTK.
> * Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale. Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.

> [!TIP]
> La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet. Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée. Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.

Cliquez sur **Suivant**, puis sur **Terminé** dans la fenêtre MRTK Project Configurator pour terminer la configuration du projet Unity pour XRSDK.

### <a name="configure-additional-project-settings"></a>Configurer des paramètres de projet supplémentaires

Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :

Dans la fenêtre Paramètres du projet, sélectionnez **Gestion de plug-in XR** > **Windows Mixed Reality** > **Paramètres du runtime**, puis utilisez la liste déroulante **Format de mémoire tampon de profondeur** pour sélectionner **16 bits de profondeur** :

![Unity - 16 Depth activé](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet. Pour plus d’informations à ce sujet, reportez-vous à la section <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Partage de mémoire tampon de profondeur (HoloLens)</a> de la documentation sur les performances de MRTK.

Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :

![Paramètres de publication Unity. Nom de package configuré](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Le « Package name » est l’identificateur unique de l’application. Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.

> [!TIP]
> « Product Name » est le nom affiché dans le menu Démarrer de HoloLens. Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

Une fois **MixedRealityFeatureTool** ouvert, cliquez sur **Démarrer** pour commencer à utiliser Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

La première étape consiste à faire pointer Mixed Reality Feature Tool sur votre **Chemin d’accès du projet** à l’aide du bouton représentant des **points de suspension**. Cliquez ensuite sur le bouton représentant des points de suspension à côté du chemin d’accès du projet et accédez à votre dossier de projet dans l’Explorateur. Par exemple : _D:\MixedRealityLearning\Tutoriels MRTK_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Une fois le dossier de votre projet localisé, cliquez sur le bouton Ouvrir pour revenir à Mixed Reality Feature Tool. Cliquez ensuite sur **Découvrir les fonctionnalités**.

> [!NOTE]
> La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier. Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.

> [!Important]
> Mixed Reality Feature Tool effectue la validation pour s’assurer qu’il a été dirigé vers un dossier de projet Unity. Le dossier doit contenir des dossiers Ressources, Packages et Paramètres du projet.

Les fonctionnalités sont regroupées par catégorie pour faciliter leur recherche. Cliquez sur la liste déroulante **Mixed Reality Toolkit** pour trouver les packages qui lui sont associés.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Cochez la case **Mixed Reality Toolkit Foundation** et cliquez sur la liste déroulante en regard de celle-ci pour sélectionner **MRTK 2.7.0**, puis cliquez sur le bouton **Obtenir des fonctionnalités** pour télécharger les packages sélectionnés.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Cliquez ensuite sur le bouton **Validate** pour valider le package sélectionné. Vous voyez une fenêtre contextuelle avec le message **No validation issues were detected** (Aucun problème de validation détecté). Cliquez sur **OK** pour fermer la fenêtre contextuelle, puis cliquez sur le bouton **Import**.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

Cliquez sur le bouton **Approve** pour ajouter **Mixed Reality Toolkit** au projet.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Configuration du projet Unity

Une fois que Unity a fini d’importer le package de la section précédente, la fenêtre MRTK Project Configurator doit s’afficher. Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement en accédant à **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer projet pour MRTK** :

![Chemin du menu Configure Unity Project d’Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

Cliquez sur **XR antérieur** pour activer XR antérieur et ajouter les packages requis dans votre projet.

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

Cliquez sur le bouton Suivant pour activer les paramètres de pipeline XR pour XR antérieur.

![Fenêtre Configuration de MRTK Unity](../images/mr-learning-base/base-02-section5-step1-3.PNG)

Dans la fenêtre MRTK Project Configurator, assurez-vous que toutes les options sont cochées et utilisez également la liste déroulante **Spatializer audio** pour sélectionner le **Spatializer MS HRTF**, puis cliquez sur le bouton **Appliquer** pour appliquer le paramètre :

![Fenêtre de configuration de MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :

> * Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin. Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de la documentation sur les [performances](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de MRTK.
> * Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale. Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.

> [!TIP]
> La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet. Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée. Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.

Cliquez sur **Suivant**, puis sur le bouton **Terminé** dans la fenêtre MRTK Project Configurator pour terminer la configuration du projet Unity pour XR antérieur.

### <a name="configure-additional-project-settings"></a>Configurer des paramètres de projet supplémentaires

Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :

Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, puis utilisez la liste déroulante **Depth Format** pour sélectionner **16-bit depth** :

![Unity - 16 Depth activé](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet. Pour plus d’informations à ce sujet, reportez-vous à la section <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Partage de mémoire tampon de profondeur (HoloLens)</a> de la documentation sur les performances de MRTK.

Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :

![Paramètres de publication Unity. Nom de package configuré](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Le « Package name » est l’identificateur unique de l’application. Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.

> [!TIP]
> « Product Name » est le nom affiché dans le menu Démarrer de HoloLens. Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.
