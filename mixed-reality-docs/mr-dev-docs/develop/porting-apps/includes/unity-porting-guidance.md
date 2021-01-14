---
ms.openlocfilehash: 0ef22142ac2efc3ef47ece2619d31dbeddcff8fe
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192660"
---
# <a name="project-settings"></a>[Paramètres du projet](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. passez en revue les étapes de Portage courantes indiquées ci-dessus.

Passez en revue les étapes courantes indiquées ci-dessus pour vous assurer que votre environnement de développement est correctement configuré. À l’étape #3, si vous utilisez Visual Studio, vous devez sélectionner la charge **de travail développement de jeux avec Unity** . Vous pouvez désélectionner le composant « éditeur Unity facultatif », car vous installerez une version plus récente d’Unity à l’étape suivante.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. effectuez une mise à niveau vers la dernière version publique d’Unity avec la prise en charge de Windows MR
1. Téléchargez la dernière [version publique recommandée d’Unity](../../install-the-tools.md) avec prise en charge de la réalité mixte.
2. Enregistrez une copie de votre projet avant de commencer
3. Consultez la [documentation](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponible à partir de Unity sur la mise à niveau si votre projet a été généré sur une version antérieure d’Unity.
4. Suivez les [instructions](https://docs.unity3d.com/Manual/APIUpdater.html) sur le site de Unity pour utiliser son programme de mise à jour d’API automatique
5. Vérifiez s’il existe des modifications supplémentaires que vous devez apporter pour que votre projet s’exécute et pour traiter les erreurs et avertissements restants. 

> [!Note] 
> Si vous avez des intergiciels (middleware) dont vous dépendez, vérifiez que vous utilisez la dernière version (plus de détails à l’étape 3 ci-dessous).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. Mettez à niveau votre intergiciel vers les dernières versions

Avec toute mise à jour Unity, il y a de bonnes chances que vous deviez mettre à jour un ou plusieurs packages middleware dont dépend votre jeu ou votre application. En outre, la mise à jour du middleware le plus récent augmente la probabilité de réussite tout au long du processus de Portage.

### <a name="4-target-your-application-to-run-on-win32"></a>4. cibler votre application pour qu’elle s’exécute sur Win32

À l’intérieur de votre application Unity :

* Accéder aux paramètres de génération de > de fichiers
* Sélectionnez « PC, Mac, Linux standalone »
* Définir la plateforme cible sur « Windows »
* Définissez architecture sur « x86 », puis sélectionnez « changer la plateforme »

> [!NOTE] 
> Si votre application a des dépendances sur des services spécifiques à l’appareil, tels que la mise en correspondance à partir de la vapeur, vous devez les désactiver à cette étape. Vous pouvez vous connecter aux services équivalents fournis par Windows plus tard.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. configurer votre matériel Windows Mixed Reality
1. Passer en revue les étapes de [configuration du casque immersif](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. En savoir plus sur l' [utilisation du simulateur Windows Mixed Reality](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) et [la navigation dans la page d’informations Windows Mixed Reality](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. cibler votre application pour qu’elle s’exécute sur Windows Mixed Reality
1. Tout d’abord, vous devez supprimer ou compiler de façon conditionnelle toute autre prise en charge de bibliothèque spécifique à un kit de développement logiciel (SDK) VR particulier. Ces ressources changent fréquemment les paramètres et les propriétés de votre projet de manière incompatible avec d’autres kits de développement logiciel (SDK) VR, tels que Windows Mixed Reality.
    * Par exemple, si votre projet fait référence au kit de développement logiciel (SDK) SteamVR, vous devez mettre à jour votre projet pour utiliser à la place les API de VR courantes d’Unity qui prennent en charge Windows Mixed Reality et SteamVR.
    * Les étapes spécifiques pour l’exclusion conditionnelle d’autres kits de développement logiciel VR sont bientôt disponibles.
2. Dans votre projet Unity, [Ciblez le kit de développement logiciel (SDK) Windows 10](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. Pour chaque scène, [configurer l’appareil photo](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. utiliser la phase pour placer le contenu à l’étage

Vous pouvez créer des expériences de réalité mixte sur une large gamme [d’expériences.](../../../design/coordinate-systems.md)

Si vous déployez une expérience à l' **échelle assise**, vous devez vérifier que Unity est défini sur le type d’espace de suivi **fixe** :

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Le code ci-dessus définit le système de coordonnées universel de Unity pour suivre le [cadre stationnaire de référence](../../../design/coordinate-systems.md#spatial-coordinate-systems). Dans le mode de suivi fixe, le contenu placé dans l’éditeur juste devant l’emplacement par défaut de l’appareil photo (Forward is-Z) apparaît devant l’utilisateur au lancement de l’application. Pour recentrer l’origine assise de l’utilisateur, vous pouvez appeler XR de l’unité [. Méthode InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) .

Si vous effectuez une mise à l' **échelle permanente** ou une **expérience** de mise à l’échelle de l’espace, vous allez placer du contenu par rapport à l’étage. Vous avez raison de l’étage de l’utilisateur à l’aide de la **[Phase spatiale](../../../design/coordinate-systems.md#spatial-coordinate-systems)**, qui représente l’origine de l’utilisateur et la limite facultative de l’espace, configurées lors de la première exécution. Pour ces expériences, vous devez vous assurer que Unity est défini sur le type d’espace de suivi **RoomScale** . Alors que RoomScale est la valeur par défaut, vous pouvez le définir explicitement et vous assurer que vous obtenez la valeur true, afin d’intercepter les situations où l’utilisateur a déplacé son ordinateur hors de la salle qu’il a étalonnée :

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

Une fois que votre application a correctement défini le type d’espace de suivi RoomScale, le contenu placé sur le plan y = 0 s’affiche sur le plancher. L’origine à (0, 0, 0) sera l’emplacement spécifique sur le plancher où l’utilisateur a pris la main pendant la configuration de la salle, avec-Z représentant la direction vers l’avant au cours de l’installation.

Dans le code de script, vous pouvez ensuite appeler la méthode TryGetGeometry sur vous êtes le type UnityEngine. expérimental. XR. Boundary pour obtenir un polygone de limite, en spécifiant un type de limite de TrackedArea. Si l’utilisateur a défini une limite (vous récupérez une liste de vertex), il est possible de fournir une expérience de mise à l’échelle de l' **espace** à l’utilisateur, où il peut se déplacer dans la scène que vous créez.

Le système affiche automatiquement la limite lorsque l’utilisateur l’approche. Votre application n’a pas besoin d’utiliser ce polygone pour restituer la limite elle-même.

Pour plus d’informations, consultez la page [systèmes de coordonnées dans Unity](../../unity/coordinate-systems-in-unity.md) .

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

Exemple de résultats :

![Exemple de résultats](../../porting-apps/images/largestrectangle-400px.jpg)

L’algorithme est basé sur un blog de Daniel Smilkov : le [plus grand rectangle dans un polygone](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. utiliser votre modèle d’entrée

Chaque jeu ou application ciblant un HMD existant aura un ensemble d’entrées qu’il gère, les types d’entrées dont il a besoin pour l’expérience et les API spécifiques qu’il appelle pour obtenir ces entrées. Nous avons investi pour essayer de le rendre aussi simple et simple que possible pour tirer parti des entrées disponibles dans Windows Mixed Reality.

Lisez le [Guide de Portage d’entrée pour Unity](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input) dans l’onglet adjacent pour plus d’informations sur la façon dont Windows Mixed Reality expose les entrées et sur la façon dont elles sont mappées à ce que votre application peut faire aujourd’hui.

### <a name="9-performance-testing-and-tuning"></a>9. test et réglage des performances

Windows Mixed Reality sera disponible sur une vaste gamme d’appareils, allant des PC de jeux haut de gamme aux PC grand public. Selon le marché que vous ciblez, il existe une différence significative dans les budgets de calcul et graphiques disponibles pour votre application. Au cours de cet exercice de Portage, vous utilisez probablement un PC Premium et avez des budgets de calcul et graphiques importants disponibles pour votre application. Si vous souhaitez que votre application soit disponible pour un public plus large, vous devez tester et profiler votre application sur [le matériel représentatif que vous souhaitez cibler](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

[Unity](https://docs.unity3d.com/Manual/Profiler.html) et [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) incluent des profileurs de performances, et [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) et [Intel](https://software.intel.com/articles/vr-content-developer-guide) publient des instructions sur le profilage et l’optimisation des performances. Une discussion complète sur les performances est disponible [pour comprendre les performances de la réalité mixte](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md). En outre, il existe des détails spécifiques pour Unity sous [recommandations de performances pour Unity](../../unity/performance-recommendations-for-unity.md).

# <a name="input-mapping"></a>[Mappage d’entrées](#tab/input)

Vous pouvez porter votre logique d’entrée vers Windows Mixed Reality à l’aide de l’une des deux approches, les API d’entrée générales d’Unity. GetButton/GetAxis qui s’étendent sur plusieurs plateformes ou sur le XR spécifique à Windows. WSA. API d’entrée qui offrent des données plus riches pour les contrôleurs de mouvement et les mains de HoloLens.

> [!IMPORTANT]
> Si vous utilisez des contrôleurs de reréverbérations HP G2, reportez-vous à [cet article](../../unity/unity-reverb-g2-controllers.md) pour obtenir des instructions supplémentaires sur le mappage d’entrée.

## <a name="unity-xr-input-apis"></a>API d’entrée Unity XR

Pour les nouveaux projets, nous vous recommandons d’utiliser les nouvelles API d’entrée XR dès le début. 

Vous trouverez plus d’informations sur les [API XR ici](https://docs.unity3d.com/Manual/xr_input.html).

## <a name="inputgetbuttongetaxis-apis"></a>API Input. GetButton/GetAxis

Unity utilise actuellement ses API d’entrée. GetButton/Input. GetAxis pour exposer l’entrée pour [le kit de développement logiciel (SDK) Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) et [le kit de développement logiciel (SDK) OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Si vos applications utilisent déjà ces API pour l’entrée, il s’agit du chemin le plus simple pour la prise en charge des contrôleurs de mouvement dans Windows Mixed Reality : vous devez simplement remapper les boutons et les axes dans le gestionnaire d’entrée.

Pour plus d’informations, consultez le [tableau des mappages bouton Unity/AXIS](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) et [vue d’ensemble des API Unity courantes](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR spécifique à Windows. WSA. API d’entrée

> [!CAUTION]
> Si votre projet utilise l’un des XR. Les API WSA, elles sont en passe en faveur du kit de développement logiciel (SDK) XR dans les futures versions Unity. Pour les nouveaux projets, nous vous recommandons d’utiliser le kit de développement logiciel (SDK) XR dès le début. Vous trouverez plus d’informations sur le [système d’entrée XR et les API ici](https://docs.unity3d.com/Manual/xr_input.html).

Si votre application crée déjà une logique d’entrée personnalisée pour chaque plateforme, vous pouvez choisir d’utiliser les API d’entrée spatiale spécifiques à Windows sous l’espace de noms **UnityEngine. XR. WSA. Input** . Cela vous permet d’accéder à des informations supplémentaires, telles que la précision de la position ou le genre de source, vous permettant de distinguer les mains et les contrôleurs de HoloLens.

> [!NOTE]
> Si vous utilisez des contrôleurs de réverbération HP G2, toutes les API d’entrée continuent de fonctionner, à l’exception de **InteractionSource. supportsTouchpad**, qui retourne false sans les données du pavé tactile.

Pour plus d’informations, consultez la [vue d’ensemble des API UnityEngine. XR. WSA. Input](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Poignée de pose et pose de pointage

Windows Mixed Reality prend en charge les contrôleurs de mouvement dans un large éventail de facteurs de forme, la conception de chaque contrôleur étant différente dans sa relation entre la position de l’utilisateur et la direction « avant » naturelle que les applications doivent utiliser pour pointer lors du rendu du contrôleur.

Pour mieux représenter ces contrôleurs, il existe deux types de poses que vous pouvez examiner pour chaque source d’interaction :

* La **poignée pose**, représentant l’emplacement de la paume d’une main détectée par un HoloLens, ou la paume contenant un contrôleur de mouvement.
    * Sur les casques immersifs, cette pose est idéale pour afficher **la main de l’utilisateur** ou **un objet détenu par l’utilisateur**, tel qu’un arme ou un pistolet.
    * Position de la **poignée**: le centre de la poche quand il maintient le contrôleur naturellement, ajusté à gauche ou à droite pour centrer la position au sein de la poignée.
    * **Axe droit de l’orientation de la poignée**: lorsque vous ouvrez complètement votre main pour former une pose plate à 5 doigts, le rayon normal à votre paume (en avant à partir de la poche de gauche, en arrière depuis la paume de droite)
    * **Axe avant de l’orientation de la poignée**: quand vous fermez partiellement votre main (comme si vous détenir le contrôleur), le rayon qui pointe vers l’avant dans le tube formé par vos doigts non thumbs.
    * **Axe vers le haut de l’orientation**: l’axe vers le haut, impliqué dans les définitions Right et Forward.
    * Vous pouvez accéder à la poignée à l’aide de l’API d’entrée entre fournisseurs de l’unité Unity (**[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/rotation**) ou par le biais de l’API spécifique à Windows (**SourceState. SourcePose. TryGetPosition/rotation**, demandant la poignée pose).
* Le **pointeur se pose**, représentant l’extrémité du contrôleur pointant vers l’avant.
    * Ce modèle est mieux utilisé pour raycast quand vous **pointez sur l’interface utilisateur** lorsque vous rendez le modèle de contrôleur lui-même.
    * Actuellement, le pointeur pose est disponible uniquement par le biais de l’API spécifique à Windows (**sourceState. sourcePose. TryGetPosition/rotation**, demandant le pointeur pose).

Ces coordonnées de pose sont toutes exprimées en coordonnées universelles Unity.
