---
title: Modèle d’application
description: Windows Mixed Reality utilise le modèle d’application fourni par l’plateforme Windows universelle, un modèle et un environnement pour les applications Windows modernes.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, modèle d’application, cycle de vie, suspendre, reprendre, vignette, vues, contrats, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, réalité mixte Shared Computer Toolkit
ms.openlocfilehash: 5f15f0a2516a21cd6432e7f09df7950f8d832acc77ac77056f5bf1382500024e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221897"
---
# <a name="app-model"></a>Modèle d’application

Windows Mixed Reality utilise le modèle d’application fourni par le [plateforme Windows universelle](/windows/uwp/get-started/) (UWP), qui est un modèle et un environnement pour les applications Windows modernes. Le modèle d’application UWP définit la manière dont les applications sont installées, mises à jour, gérées et supprimées en toute sécurité. Elle régit également le cycle de vie de l’application : la manière dont les applications s’exécutent, sont en veille et arrêt-et comment elles peuvent préserver l’État. Enfin, le modèle d’application couvre l’intégration et l’interaction avec le système d’exploitation, les fichiers et d’autres applications.

![applications 2d organisées dans le Windows Mixed Reality dans la zone de déjeuner](images/20160112-055908-hololens-500px.jpg)<br>
*applications avec une vue 2d organisée dans la page d’Windows Mixed Reality*

## <a name="app-lifecycle"></a>Cycle de vie de l’application

Le cycle de vie d’une application de réalité mixte implique des concepts d’application standard tels que le placement, le lancement, l’arrêt et la suppression.

### <a name="placement-is-launch"></a>Le placement est lancé

chaque application démarre en réalité mixte en plaçant une vignette d’application (juste un [Windows vignette secondaire](/uwp/api/Windows.UI.StartScreen.SecondaryTile)) dans la [Windows Mixed Reality page d’hébergement](../discover/navigating-the-windows-mixed-reality-home.md). Ces vignettes d’application, au positionnement, commencent à exécuter l’application. Ces vignettes d’application sont conservées et restent à leur emplacement de destination, agissant comme des lanceurs à chaque fois que vous souhaitez revenir à l’application.

![Placement place une vignette secondaire dans le monde](images/slide1-600px.png)<br>
*Placement place une vignette secondaire dans le monde*

Dès que l’emplacement est terminé (sauf si l’emplacement a été démarré par une [application au lancement de l’application](app-model.md#protocols) ), l’application démarre le lancement. Windows Mixed Reality pouvez exécuter un nombre limité d’applications en même temps. Dès que vous placez et lancez une application, d’autres applications actives peuvent s’interrompre. Les applications suspendues laissent une capture d’écran du dernier état de l’application sur sa vignette d’application où vous l’avez placée. pour plus d’informations sur la gestion de la reprise et d’autres événements de cycle de vie, consultez [Windows 10 cycle de vie des applications UWP](/windows/uwp/launch-resume/app-lifecycle).

![Après avoir placé une vignette, l’application démarre le ](images/slide2-500px.png) ![ diagramme d’État en cours d’exécution pour l’application en cours d’exécution, suspendue ou non exécutée](images/ic576232-500px.png)<br>
*Left : après avoir placé une vignette, l’application commence à s’exécuter. Right : diagramme d’état de l’application en cours d’exécution, suspendue ou non exécutée.*

### <a name="remove-is-closeterminate-process"></a>Le processus de suppression est fermer/terminer

Lorsque vous supprimez une vignette d’application placée du monde entier, les processus sous-jacents se ferment. Cela peut être utile pour s’assurer que votre application est arrêtée ou redémarrer une application problématique.

### <a name="app-suspensiontermination"></a>Interruption/arrêt de l’application

dans la [Windows Mixed Reality page d’hébergement](../discover/navigating-the-windows-mixed-reality-home.md), l’utilisateur peut créer plusieurs points d’entrée pour une application en lançant votre application à partir du menu Démarrer et en plaçant la vignette de l’application dans le monde entier. Chaque vignette d’application se comporte comme un point d’entrée différent et a une instance de vignette distincte dans le système. Une requête pour [SecondaryTile. FindAllAsync](/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) entraîne un **SecondaryTile** pour chaque instance d’application.

Quand une application UWP s’interrompt, une capture d’écran est prise de l’état actuel.

![Des captures d’écran s’affichent pour les applications suspendues](images/slide9-800px.png)<br>
*Des captures d’écran s’affichent pour les applications suspendues*

l’une des principales différences par rapport aux autres interpréteurs de Windows 10 est la façon dont l’application est informée de l’activation d’une instance d’application via les événements [CoreApplication.](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) reforming et [CoreWindow. activated](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) .

|  Scénario |  Reprise  |  Activé | 
|----------|----------|----------|
|  lancer une nouvelle instance de l’application à partir de la menu Démarrer  |   |  **Activé** avec un nouveau [TileId](/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  lancer la deuxième instance de l’application à partir de la menu Démarrer  |   |  **Activé** avec un nouveau **TileId** | 
|  Sélectionnez l’instance de l’application qui n’est pas actuellement active  |   |  **Activé** avec le **TileId** associé à l’instance | 
|  Sélectionnez une autre application, puis sélectionnez l’instance précédemment active  |  **Reprise** déclenchée  |  | 
|  Sélectionnez une autre application, puis sélectionnez l’instance qui était précédemment inactive  |  **Reprise** déclenchée  |  Ensuite **activé** avec le **TileId** associé à l’instance | 

### <a name="extended-execution"></a>Exécution étendue

Parfois, votre application doit continuer à travailler en arrière-plan ou à exécuter des données audio. Les [tâches en arrière-plan](/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) sont disponibles sur HoloLens.

![Les applications peuvent s’exécuter en arrière-plan](images/slide10-800px.png)<br>
*Les applications peuvent s’exécuter en arrière-plan*

## <a name="app-views"></a>Vues d’applications

Lorsque votre application est activée, vous pouvez choisir le type de vue que vous souhaitez afficher. Pour le **CoreApplication** d’une application, il y a toujours une [vue d’application](/uwp/api/Windows.UI.ViewManagement.ApplicationView) principale et un nombre quelconque d’autres affichages d’application que vous souhaitez créer. Sur le bureau, vous pouvez considérer une vue d’application comme une fenêtre. Nos modèles d’application de réalité mixte créent un projet Unity dans lequel la vue d’application principale est [immersive](app-views.md). 

votre application peut créer une vue d’application 2d supplémentaire à l’aide de technologies telles que XAML, pour utiliser des fonctionnalités de Windows 10 telles que l’achat dans l’application. si votre application a démarré en tant qu’application UWP pour d’autres appareils Windows 10, votre vue principale est 2d. Toutefois, vous pouvez « allumer » en réalité mixte en ajoutant une autre vue d’application qui est immersive pour afficher une expérience de façon volumétrique. Imagine la création d’une application de visionneuse de photos en XAML où le bouton de diaporama bascule vers une vue d’application immersif qui flew des photos à partir de l’application dans le monde entier et des surfaces.

![L’application en cours d’exécution peut avoir une vue 2D ou une vue immersive](images/slide3-800px.png)<br>
*L’application en cours d’exécution peut avoir une vue 2D ou une vue immersive*

### <a name="creating-an-immersive-view"></a>Création d’une vue immersive

Les applications de réalité mixte créent une vue immersive, qui est obtenue avec le type [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace) .

Une application qui est purement immersive doit toujours créer une vue immersive au lancement, même si elle est lancée à partir du bureau. Les vues immersives s’affichent toujours dans le casque, quel que soit l’emplacement à partir duquel elles ont été créées. L’activation d’une vue immersive permet d’afficher le portail de réalité mixte et de guider l’utilisateur sur son casque.

Une application qui commence par une vue 2D sur le moniteur de bureau peut créer une vue immersive secondaire pour afficher le contenu du casque. C’est le cas, par exemple, d’une fenêtre de périphérie 2D sur le moniteur affichant une vidéo de 360 degrés dans le casque.

![Les applications qui s’exécutent en mode immersif sont les seules visibles](images/slide4-800px.png)<br>
*Une application en cours d’exécution dans une vue immersive est la seule visible*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>vue 2d dans la page d’Windows Mixed Reality

Tout autre chose qu’une vue immersive est rendue sous la forme d’une vue 2D dans votre monde.

Une application peut avoir des vues 2D à la fois sur le moniteur de bureau et dans le casque. Une nouvelle vue 2D sera placée dans le même Shell que la vue qui l’a créée, soit sur le moniteur, soit dans le casque. Il n’est pas actuellement possible pour une application ou un utilisateur de déplacer une vue 2D entre la réalité mixte et le moniteur.

![Les applications qui s’exécutent dans la vue 2D partagent l’espace dans le monde mixte avec d’autres applications](images/slide5-800px.png)<br>
*Les applications qui s’exécutent dans une vue 2D partagent l’espace avec d’autres applications*

### <a name="placement-of-additional-app-tiles"></a>Positionnement des vignettes d’application supplémentaires

Vous pouvez placer autant d’applications avec une vue 2D dans votre monde que vous le souhaitez avec les [API de vignette secondaires](/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Ces vignettes « épinglées » s’affichent sous forme d’écrans d’accueil que les utilisateurs doivent placer et peuvent ensuite utiliser pour lancer votre application. Windows Mixed Reality ne prend actuellement pas en charge le rendu d’un contenu de vignette 2d sous forme de vignettes dynamiques.

![Les applications peuvent avoir plusieurs placements à l’aide de vignettes secondaires](images/slide6-800px.png)<br>
*Les applications peuvent avoir plusieurs placements à l’aide de vignettes secondaires*

### <a name="switching-views"></a>Basculement des vues

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Passage de la vue XAML 2D à la vue immersif

Si l’application utilise du code XAML, le [IFRAMEWORKVIEWSOURCE](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) XAML contrôle la première vue de l’application. L’application devra basculer vers la vue immersive avant d’activer le **CoreWindow** pour s’assurer que l’application démarre directement dans l’expérience immersive.

Utilisez [CoreApplication. CreateNewView](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) et [ApplicationViewSwitcher. SwitchAsync](/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) pour en faire la vue active.

> [!NOTE]
>* Ne spécifiez pas l’indicateur [ApplicationViewSwitchingOptions. ConsolidateViews](/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) à **SwitchAsync** lors du passage de la vue XAML à la vue immersif, ou la ardoise qui a lancé l’application sera supprimée du monde entier.
>* **SwitchAsync** doit être appelé à l’aide du [répartiteur](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) associé à l’affichage dans lequel vous passez.
>* Vous devrez **SwitchAsync** la vue XAML si vous devez lancer un clavier virtuel ou si vous souhaitez activer une autre application.

![Les applications peuvent basculer entre les vues 2D et les vues immersives ](images/slide7-600px.png) ![ quand une application passe dans une vue immersive, le monde mixte et d’autres applications disparaissent](images/slide8-600px.png)<br>
*Gauche : les applications peuvent basculer entre la vue 2D et l’affichage immersif. Right : quand une application passe dans une vue immersive, le Windows Mixed Reality page d’hébergement et d’autres applications disparaissent.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Basculement de la vue immersive vers une vue XAML de clavier

Une raison courante du basculement entre les vues est l’affichage d’un clavier dans une application de réalité mixte. L’interpréteur de commandes ne peut afficher le clavier système que si l’application affiche une vue 2D. Si l’application doit obtenir une entrée de texte, elle peut fournir une vue XAML personnalisée avec un champ d’entrée de texte, basculer vers celle-ci, puis revenir en arrière une fois l’entrée terminée.

Comme dans la section précédente, vous pouvez utiliser **ApplicationViewSwitcher. SwitchAsync** pour basculer vers une vue XAML à partir de votre vue immersif.

## <a name="app-size"></a>Taille de l’application

les vues d’application 2D s’affichent toujours dans une ardoise virtuelle fixe. Ainsi, toutes les vues 2D affichent exactement la même quantité de contenu. Voici des informations supplémentaires sur la taille de la vue 2D de votre application :
* Les proportions de l’application sont conservées pendant le redimensionnement.
* La [résolution et le facteur d’échelle](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) de l’application ne sont pas modifiés par le redimensionnement.
* Les applications ne sont pas en mesure d’interroger leur taille réelle dans le monde.

![les applications 2D s’affichent avec des tailles de fenêtre fixes](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Les applications avec une vue 2D apparaissent avec des tailles de fenêtre fixes*

## <a name="app-tiles"></a>Vignettes d’application

l’menu Démarrer utilise la mosaïque standard de petite vignette et moyenne pour les codes confidentiels et la liste **toutes les applications** en réalité mixte. 

![menu Démarrer pour Windows Mixed Reality](images/start-500px.png)<br>
*menu Démarrer pour Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>Interactions entre l’application et l’application

Lorsque vous créez des applications, vous avez accès aux mécanismes de communication de l’application riche aux applications disponibles sur Windows 10. la plupart des nouvelles api de protocole et des inscriptions de fichiers fonctionnent parfaitement sur HoloLens pour permettre le lancement et la communication de l’application. 

Pour les casques de bureau, l’application associée à une extension de fichier ou un protocole donné peut être une application Win32 qui peut uniquement apparaître sur le moniteur de bureau ou dans la tablette de bureau.

### <a name="protocols"></a>Protocoles

HoloLens prend en charge l’application pour le lancement d’applications via les [apiWindows.System. Lanceur](/uwp/api/Windows.System.Launcher).

Voici quelques éléments à prendre en compte lors du lancement d’une autre application :

* Quand vous procédez à un lancement non modal, tel que [LaunchUriAsync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), l’utilisateur doit placer l’application avant d’interagir avec elle.

* Quand vous exécutez un lancement modal, par exemple par le biais de [LaunchUriForResultsAsync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), l’application modale est placée en haut de la fenêtre.

* Windows Mixed Reality ne pouvez pas superposer des applications par-dessus des vues exclusives. pour afficher l’application lancée, Windows ramène l’utilisateur au monde entier pour afficher l’application.

### <a name="file-pickers"></a>Sélecteurs de fichiers

HoloLens prend en charge les contrats [FileOpenPicker](/uwp/api/Windows.Storage.Pickers.FileOpenPicker) et [FileSavePicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) . Toutefois, aucune application n’est préinstallée et ne respecte pas les contrats de sélecteur de fichiers. ces applications, par exemple, OneDrive peuvent être installées à partir du Microsoft Store.

Si plusieurs applications de sélecteur de fichiers sont installées, vous ne verrez aucune interface utilisateur de désambiguïsation pour choisir l’application à lancer. Au lieu de cela, le premier sélecteur de fichiers installé est choisi. Lors de l’enregistrement d’un fichier, le nom de fichier est généré, ce qui comprend l’horodateur. Cette image ne peut pas être modifiée par l'utilisateur.

Par défaut, les extensions suivantes sont prises en charge localement :

|  Application  |  Extensions | 
|----------|----------|
|  Photo  |  BMP, GIF, jpg, png, AVI, MOV, MP4, WMV | 
|  Microsoft Edge  |  htm, html, PDF, SVG, XML | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>contrats d’application et extensions de Windows Mixed Reality

Les contrats d’application et les points d’extension vous permettent d’inscrire votre application pour tirer parti des fonctionnalités plus profondes du système d’exploitation, telles que la gestion d’une extension de fichier ou l’utilisation de tâches en arrière-plan. Il s’agit de la liste des contrats et des points d’extension pris en charge et non pris en charge sur HoloLens.

|  Contrat ou extension  |  Pris en charge ? | 
|----------|----------|
| [Fournisseur d’images de compte (extension)](/previous-versions/windows/apps/hh464906(v=win.10)#account_picture_provider) | Non pris en charge | 
| [Alarme](/previous-versions/windows/apps/hh464906(v=win.10)#alarm) | Non pris en charge | 
| [App Service](/previous-versions/windows/apps/hh464906(v=win.10)#app_service) | Pris en charge, mais pas entièrement fonctionnel | 
| [Fournisseur de rendez-vous](/previous-versions/windows/apps/hh464906(v=win.10)#appointmnets_provider) | Non pris en charge | 
| [Lecture automatique (extension)](/previous-versions/windows/apps/hh464906(v=win.10)#autoplay) | Non pris en charge | 
| [Tâches en arrière-plan (extension)](/previous-versions/windows/apps/hh464906(v=win.10)#background_tasts) | Partiellement pris en charge (tous les déclencheurs ne fonctionnent pas) | 
| [Tâche de mise à jour (extension)](/previous-versions/windows/apps/hh464906(v=win.10)#update_task) | Pris en charge | 
| [Contrat de mise à jour de fichier mis en cache](/previous-versions/windows/apps/hh464906(v=win.10)#cached_file_updater) | Pris en charge | 
| [Paramètres de l’appareil photo (extension)](/previous-versions/windows/apps/hh464906(v=win.10)#camera_settings) | Non pris en charge | 
| [Protocole de numérotation](/previous-versions/windows/apps/hh464906(v=win.10)#dial_protocol) | Non pris en charge | 
| [Activation de fichier (extension)](/previous-versions/windows/apps/hh464906(v=win.10)#file_activation) | Pris en charge | 
| [Contrat de sélecteur de fichier ouvert](/previous-versions/windows/apps/hh464906(v=win.10)#file_open_picker_contract) | Pris en charge | 
| [Contrat de sélecteur d’enregistrement de fichier](/previous-versions/windows/apps/hh464906(v=win.10)#file_save_picker_contract) | Pris en charge | 
| [Appel de l’écran de verrouillage](/previous-versions/windows/apps/hh464906(v=win.10)#lock_screen_call) | Non pris en charge | 
| [Lecture de contenu multimédia](/previous-versions/windows/apps/hh464906(v=win.10)#media_playback) | Non pris en charge | 
| [Lire le contrat](/previous-versions/windows/apps/hh464906(v=win.10)#playto_contract) | Non pris en charge | 
| [Tâche de configuration préinstallée](/previous-versions/windows/apps/hh464906(v=win.10)#preinstalled_config_task) | Non pris en charge | 
| [Imprimer un flux de travail 3D](/previous-versions/windows/apps/hh464906(v=win.10)#print_3d_workflow) | Pris en charge | 
| [Imprimer les paramètres de tâche (extension)](/previous-versions/windows/apps/hh464906(v=win.10)#print_task_settings) | Non pris en charge | 
| [Activation d’URI (extension)](/previous-versions/windows/apps/hh464906(v=win.10)#protocol_activation) | Pris en charge | 
| [Lancement restreint](/previous-versions/windows/apps/hh464906(v=win.10)#restricted_launch) | Non pris en charge | 
| [Rechercher un contrat](/previous-versions/windows/apps/hh464906(v=win.10)#search_contract) | Non pris en charge | 
| [contrat de Paramètres](/previous-versions/windows/apps/hh464906(v=win.10)#settings_contract) | Non pris en charge | 
| [Partager le contrat](/previous-versions/windows/apps/hh464906(v=win.10)#share_contract) | Non pris en charge | 
| [SSL/certificats (extension)](/previous-versions/windows/apps/hh464906(v=win.10)#ssl_certificates) | Pris en charge | 
| [Fournisseur de comptes Web](/previous-versions/windows/apps/hh464906(v=win.10)#web_account_provider) | Pris en charge | 

## <a name="app-file-storage"></a>Stockage de fichiers d’application

tout le stockage se fait via l' [espace de noms Windows. Stockage](/uwp/api/Windows.Storage). HoloLens ne prend pas en charge la synchronisation/l’itinérance du stockage d’application. Pour plus d’informations, consultez la documentation ci-dessous :

* [Fichiers, dossiers et bibliothèques](/windows/uwp/files/index)
* [Stocker et récupérer des paramètres et autres données d’application](/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Dossiers connus

Pour plus d’informations sur les applications UWP, consultez [fichier KnownFolders](/uwp/api/Windows.Storage.KnownFolders) .

<table>
<tr>
<th> Propriété</th><th> Pris en charge sur HoloLens</th><th> Pris en charge sur les casques immersifs</th><th> Description</th>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtient le dossier de captures de l’application.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtient le dossier du rouleau de l’appareil photo.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtient la bibliothèque de documents. La bibliothèque de documents n’est pas destinée à une utilisation générale.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>obtient la bibliothèque de Musique.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtient le dossier 3D d’objets.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtient la bibliothèque d’images.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Sélections</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtient le dossier de listes de lecture.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtient le dossier images enregistrées.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtient la bibliothèque de vidéos.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">HomeGroup</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtient le dossier du groupe résidentiel.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtient le dossier des appareils Media Server (Digital vivant Network Alliance (DLNA)).</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtient le dossier des appels enregistrés.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtient le dossier des appareils amovibles.</td>
</tr>
</table>

## <a name="app-package"></a>Package d’application

avec Windows 10, vous ne ciblez plus un système d’exploitation, mais vous [ciblez votre application sur une ou plusieurs familles d’appareils](/windows/uwp/get-started/universal-application-platform-guide#device-families). Une famille d’appareils identifie les API, les caractéristiques système et les comportements que vous pouvez attendre sur les différents appareils de cette famille. Il détermine également l’ensemble des appareils sur lesquels votre application peut être installée à partir de l' [Microsoft Store](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* pour cibler à la fois les casques et les HoloLens de bureau, ciblez votre application sur le **Windows.** Famille d’appareils universelle.
* Pour cibler uniquement des casques de bureau, ciblez votre application sur le **Windows.** Famille d’appareils de bureau.
* pour cibler uniquement HoloLens, ciblez votre application sur le **Windows.** Famille d’appareils holographiques.

## <a name="see-also"></a>Voir aussi

* [Vues d’applications](app-views.md)
* [Mise à jour des applications UWP 2D pour la réalité mixte](../develop/porting-apps/building-2d-apps.md)
* [Guide de conception du lanceur d’applications 3D](../distribute/3d-app-launcher-design-guidance.md)
* [Implémentation des lanceurs d’applications 3D](../distribute/implementing-3d-app-launchers.md)