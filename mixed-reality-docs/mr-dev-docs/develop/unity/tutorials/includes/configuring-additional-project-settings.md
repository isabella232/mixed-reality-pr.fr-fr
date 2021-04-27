---
ms.openlocfilehash: d8d46da1a1a095074f059b53ebd997e1b6f89961
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984428"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in Windows XR](#tab/winxr)

Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :

![Unity - Project Settings... Chemin du menu](../images/mr-learning-base/base-02-section5-step2-1.png)

Dans la fenêtre Project Settings, sélectionnez **XR Plug-in Managemen** > **Install XR Plug-in Management** pour installer XR Plug-in Management :

![Paramètres XR d’Unity](../images/mr-learning-base/base-02-section5-step2-2.png)

quand Unity a terminé l’installation de XR Plug-in Management. Vérifiez que vous êtes dans les paramètres Universal Windows Platform, puis cochez les cases **Initialize XR on Startup** et **Windows Mixed Reality**.

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Une fois que Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre MRTK Project Configurator doit réapparaître. Si ce n’est pas le cas, utilisez le menu Unity pour l’ouvrir.

Dans la fenêtre MRTK Project Configurator, utilisez la liste déroulante **Audio Spatializer** pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Apply** pour appliquer le paramètre :

![Paramètres XR d’Unity avec l’option SDK Windows Mixed Reality sélectionnée](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet. Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée. Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.

Dans la fenêtre Project, sélectionnez **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, puis utilisez la liste déroulante **Depth Buffer Format** pour sélectionner **16-bit depth** :

![Fenêtre Publishing Settings d’Unity avec le nom du package mis en évidence](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet. Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> de la documentation sur les <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">performances</a> de MRTK.

Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :

![Fenêtre Publishing Settings d’Unity avec le nom du package](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Le « Package name » est l’identificateur unique de l’application. Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.

> [!TIP]
> « Product Name » est le nom affiché dans le menu Démarrer de HoloLens. Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :

![Unity - Project Settings... Chemin du menu](../images/mr-learning-base/base-02-section5-step2-1.png)

Dans la fenêtre Project Settings, sélectionnez **XR Plug-in Managemen** > **Install XR Plug-in Management** pour installer XR Plug-in Management :

![Paramètres XR d’Unity avec l’option Install XR Plug-in Management sélectionnée](../images/mr-learning-base/base-02-section5-step2-2.png)

quand Unity a terminé l’installation de XR Plug-in Management. Vérifiez que vous êtes dans les paramètres Universal Windows Platform, puis cochez les cases **Initialize XR on Startup**, **OpenXR** et **Microsoft HoloLens feature set**.

![Paramètres XR d’Unity avec les options OpenXR et Microsoft HoloLens feature set sélectionnées](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

>[!Important]
>Si une icône d’avertissement rouge apparaît à côté d’OpenXR Plugin (Preview), cliquez dessus et sélectionnez Fix all avant de continuer. L’éditeur Unity devra peut-être redémarrer pour que les modifications prennent effet.
>![Menu de validation du projet OpenXR avec tous les problèmes à corriger sélectionnés.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)

Dans la barre de menus en haut de l’écran, accédez à **Mixed Reality > OpenXR > Apply recommended project settings for HoloLens 2** pour optimiser les performances de l’application.

![Menu Mixed Reality avec les options OpenXR et Apply recommended project settings for HoloLens 2 sélectionnées](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

Une fois qu’Unity a fini d’importer les fichiers nécessaires, la fenêtre MRTK Project Configurator doit réapparaître. Si ce n’est pas le cas, utilisez le menu Unity pour l’ouvrir.

Dans la fenêtre MRTK Project Configurator, utilisez la liste déroulante **Audio Spatializer** pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Apply** pour appliquer le paramètre :

![Fenêtre de configuration de MRTK avec les options par défaut sélectionnées](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet. Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée. Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.


Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :

![Paramètres de publication Unity](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Le « Package name » est l’identificateur unique de l’application. Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.

> [!TIP]
> « Product Name » est le nom affiché dans le menu Démarrer de HoloLens. Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :

Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, cochez la case **Virtual Reality Supported**, cliquez sur l’icône **+** et sélectionnez Windows Mixed Reality pour ajouter le SDK Windows Mixed Reality :

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality sélectionnée](../images/mr-learning-base/base-02-section5-step2-4.png)

Une fois que Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre MRTK Project Configurator doit réapparaître. Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement dans le menu Unity en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**.

Dans la fenêtre MRTK Project Configurator, utilisez la liste déroulante **Audio Spatializer** pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Apply** pour appliquer le paramètre :

![Fenêtre de configuration de MRTK](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet. Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée. Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.

Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, puis utilisez la liste déroulante **Depth Format** pour sélectionner **16-bit depth** :

![Unity - 16 Depth activé](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet. Pour plus d’informations à ce sujet, reportez-vous à la section <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Partage de mémoire tampon de profondeur (HoloLens)</a> de la documentation sur les performances de MRTK.

Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :

![Paramètres de publication Unity. Nom de package configuré](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Le « Package name » est l’identificateur unique de l’application. Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.

> [!TIP]
> « Product Name » est le nom affiché dans le menu Démarrer de HoloLens. Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.
