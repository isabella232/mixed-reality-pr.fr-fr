---
title: Mouvements dans Unity
description: Apprenez à agir sur votre point de regard avec l’entrée de mouvement main à l’aide de XR et des API de bouton et d’axe courantes.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: gestes, unity, point d’entrée, casque de réalité mixte, casque de réalité windows mixte, casque de réalité virtuelle, MRTK, Shared Computer Toolkit de la réalité mixte
ms.openlocfilehash: 8dd6b64dd0bb52e64515a43d69713ecc5dc6bcec203a987568f7c25ac492a864
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214754"
---
# <a name="gestures-in-unity"></a>Mouvements dans Unity

il existe deux façons principales d’agir sur votre point [d'](gaze-in-unity.md)intergression, les [gestes manuels](../../design/gaze-and-commit.md#composite-gestures) et les [contrôleurs de mouvement](../../design/motion-controllers.md) dans HoloLens et les HMDs immersifs. Vous accédez aux données des deux sources d’entrée spatiale via les mêmes API dans Unity.

Unity fournit deux méthodes principales pour accéder aux données d’entrée spatiales pour Windows Mixed Reality. les api *d’entrée. GetButton/input. GetAxis* courantes fonctionnent sur plusieurs kits de développement logiciel (sdk) XR unity, tandis que l’api *InteractionManager/GestureRecognizer* propre à Windows Mixed Reality expose l’ensemble complet des données d’entrée spatiale.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>API de mouvement composite de haut niveau (GestureRecognizer)

**Espace de noms :** *UnityEngine. XR. WSA. Input*<br>
**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

Votre application peut également reconnaître les gestes composites de niveau supérieur pour les sources d’entrée spatiale, le TAP, le maintien, la manipulation et les gestes de navigation. Vous pouvez reconnaître ces gestes composites sur les [mains](../../design/gaze-and-commit.md#composite-gestures) et les [contrôleurs de mouvement](../../design/motion-controllers.md) à l’aide de GestureRecognizer.

Chaque événement de mouvement sur le GestureRecognizer fournit le SourceKind pour l’entrée, ainsi que le rayon de l’en-tête de ciblage au moment de l’événement. Certains événements fournissent des informations supplémentaires spécifiques au contexte.

Seules quelques étapes sont requises pour capturer des mouvements à l’aide d’un module de reconnaissance de mouvement :
1. Créer un module de reconnaissance de mouvement
2. Spécifier les gestes à surveiller
3. S’abonner à des événements pour ces mouvements
4. Démarrer la capture des mouvements

### <a name="create-a-new-gesture-recognizer"></a>Créer un module de reconnaissance de mouvement

Pour utiliser *GestureRecognizer*, vous devez avoir créé un *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Spécifier les gestes à surveiller

Spécifiez les gestes qui vous intéressent via *SetRecognizableGestures ()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>S’abonner à des événements pour ces mouvements

Abonnez-vous aux événements pour les mouvements qui vous intéressent.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>Les mouvements de navigation et de manipulation s’excluent mutuellement sur une instance d’un *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Démarrer la capture des mouvements

Par défaut, un *GestureRecognizer* n’analyse pas l’entrée tant que *StartCapturingGestures ()* n’est pas appelé. Il est possible qu’un événement de mouvement soit généré après l’appel de *StopCapturingGestures ()* si l’entrée a été effectuée avant le frame dans lequel *StopCapturingGestures ()* a été traité. Le *GestureRecognizer* se souvient s’il était activé ou désactivé au cours de la trame précédente dans laquelle le mouvement s’est réellement produit. il est donc fiable pour démarrer et arrêter la surveillance des mouvements en fonction du point de vue du regard de ce frame.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Arrêter la capture des mouvements

Pour arrêter la reconnaissance des mouvements :

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Suppression d’un module de reconnaissance de mouvement

N’oubliez pas de vous désabonner des événements souscrits avant de détruire un objet *GestureRecognizer* .

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Rendu du modèle de contrôleur de mouvement dans Unity

![Modèle de contrôleur de mouvement et téléportage](images/motioncontrollertest-teleport-1000px.png)<br>
*Modèle de contrôleur de mouvement et téléportage*

pour afficher les contrôleurs de mouvement de votre application qui correspondent aux contrôleurs physiques que vos utilisateurs détiennent et qui s’articulent à mesure que les différents boutons sont enfoncés, vous pouvez utiliser le **prefab MotionController** dans la [réalité mixte Shared Computer Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Ce Prefab charge dynamiquement le modèle glTF correct au moment de l’exécution à partir du pilote du contrôleur de mouvement installé du système.  Il est important de charger ces modèles de manière dynamique plutôt que de les importer manuellement dans l’éditeur, afin que votre application affiche des modèles 3D physiquement précis pour tous les contrôleurs actuels et futurs que vos utilisateurs peuvent avoir.

1. suivez les instructions [Prise en main](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) pour télécharger la Shared Computer Toolkit de la réalité mixte et l’ajouter à votre projet unity.
2. Si vous avez remplacé votre appareil photo par le *MixedRealityCameraParent* Prefab dans le cadre des étapes de prise en main, vous êtes en déplacement.  Prefab comprend le rendu du contrôleur de mouvement.  sinon, ajoutez *assets/HoloToolkit/Input/Prefabs/MotionControllers. prefab* à votre scène à partir du volet de Project.  Vous pouvez ajouter ce Prefab en tant qu’enfant de n’importe quel objet parent que vous utilisez pour déplacer la caméra lorsque l’utilisateur téléporte dans votre scène, afin que les contrôleurs soient fournis avec l’utilisateur.  Si votre application n’implique pas de téléportage, ajoutez simplement le Prefab à la racine de votre scène.

## <a name="throwing-objects"></a>Lever des objets

La levée d’objets dans la réalité virtuelle est un problème plus difficile qu’il n’y paraît d’abord. Comme avec la plupart des interactions basées physiquement, lorsque la levée dans le jeu se fait de manière inattendue, elle est immédiatement évidente et s’interrompt. Nous avons passé un peu de temps à réfléchir à la façon de représenter un comportement de levée de manière physique et à rencontrer quelques recommandations, activées par le biais des mises à jour de notre plateforme, que nous aimerions partager avec vous.

Vous trouverez un exemple de la façon dont nous vous recommandons d’implémenter la levée [ici](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Cet exemple suit les quatre instructions suivantes :
* **Utilisez la *vélocité* du contrôleur au lieu de la position**. dans la mise à jour de novembre pour Windows, nous avons introduit un changement de comportement dans l' [état de suivi de position « approximatif](../../design/motion-controllers.md#controller-tracking-state)». Dans cet État, les informations de vélocité sur le contrôleur continuent d’être signalées aussi longtemps que nous pensons qu’il s’agit d’une précision élevée, qui est souvent plus longue que la position demeure une précision élevée.
* **Incorporez la *vélocité angulaire* du contrôleur**. Cette logique est contenue dans le `throwing.cs` fichier de la `GetThrownObjectVelAngVel` méthode statique, dans le package lié ci-dessus :
   1. Comme la vélocité angulaire est conservée, l’objet levé doit conserver la même vélocité angulaire qu’au moment de la levée : `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Comme le centre de la masse de l’objet levé n’est probablement pas à l’origine de la poignée, il a probablement une vitesse différente de celle du contrôleur dans le cadre de la référence de l’utilisateur. La partie de la rapidité de l’objet utilisée de cette façon est la vélocité tangentielle instantanée du centre de la masse de l’objet levé autour de l’origine du contrôleur. Cette vélocité tangentielle est le produit croisé de la vélocité angulaire du contrôleur avec le vecteur représentant la distance entre l’origine du contrôleur et le centre de la masse de l’objet levé.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. La vélocité totale de l’objet levé est la somme de la vélocité du contrôleur et de cette vélocité tangentielle : `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Portez une attention particulière à l' *heure* à laquelle nous appliquons la vélocité**. Quand vous appuyez sur un bouton, il peut falloir jusqu’à 20 ms pour que cet événement se propage à Bluetooth au système d’exploitation. Cela signifie que si vous interrogez une modification de l’état d’un contrôleur en l’appuyant sur non enfoncé ou sur l’autre, le contrôleur vous pose les informations dont vous bénéficiez en effet. En outre, la présentation du contrôleur présentée par notre API d’interrogation est anticipée afin de refléter une situation probable au moment où l’image sera affichée, ce qui peut être supérieur à 20 ms à l’avenir. Cela est idéal pour le *rendu* des objets détenus, mais il compose notre problème de temps pour *cibler* l’objet à mesure que nous calculons la trajectoire pour le moment où l’utilisateur a relâché la levée. Heureusement, avec la mise à jour de novembre, lors de l’envoi d’un événement Unity comme *InteractionSourcePressed* ou *InteractionSourceReleased* , l’état contient les données de la pose de l’historique de retour lorsque le bouton était enfoncé ou relâché.  Pour optimiser le rendu du contrôleur et le ciblage du contrôleur lors des levées, vous devez utiliser correctement l’interrogation et l’événement, selon le cas :
   * Pour le rendu de chaque trame par le **contrôleur** , votre application doit positionner les *gameobject* du contrôleur au niveau du contrôleur avant prédiction pour le temps des photons du frame actuel.  Vous recevez ces données à partir d’API d’interrogation Unity, telles que *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* ou *[XR. WSA. Entrez. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Pour le **ciblage du contrôleur** sur une presse ou une mise en sortie, votre application doit raycast et calculer des trajectoires en fonction de la pose du contrôleur historique pour cet événement Press ou Release.  Vous recevez ces données à partir d’API d’événements Unity, telles que *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Utilisez la poignée**. Angular vélocité et la vélocité sont rapportées par rapport à la pose de la poignée, et non à la pose du pointeur.

la génération continuera à s’améliorer avec les futures mises à jour de Windows et vous pouvez vous attendre à trouver plus d’informations ici.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>Contrôleurs de mouvement et de mouvement dans MRTK

Vous pouvez accéder au contrôleur de mouvement et de mouvement à partir du gestionnaire d’entrée.

* [Mouvement dans MRTK](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [Contrôleur de mouvement dans MRTK](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a>Avancer avec des tutoriels

Des didacticiels pas à pas, avec des exemples de personnalisation plus détaillés, sont disponibles dans Mixed Reality Academy :

- [Réalité mixte - Entrées - Cours 211 : Mouvement](tutorials/holograms-211.md)
- [Réalité mixte - Entrées - Cours 213 : Contrôleurs de mouvement](../../deprecated/mixed-reality-213.md)

[![Entrée MR 213-contrôleur de mouvement](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Entrée MR 213-contrôleur de mouvement*

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction MRTK Core. À partir d’ici, vous pouvez passer au composant suivant :

> [!div class="nextstepaction"]
> [Suivi du regard et des mains](./hand-eye-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi

* [Suivre de la tête et valider](../../design/gaze-and-commit.md)
* [Contrôleurs de mouvement](../../design/motion-controllers.md)