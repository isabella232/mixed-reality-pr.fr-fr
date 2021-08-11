---
title: Scène Understanding SDK
description: Découvrez comment installer et utiliser le kit de développement logiciel (SDK) de scène, y compris les composants, les mailles et les objets dans les applications de réalité mixte.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: compréhension des scènes, mappage Spatial, Windows Mixed Reality, unity
ms.openlocfilehash: 1b93f3137e1ac1309ee56e974a0fa33608114f16dfb65a13e369490f45d6beb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193636"
---
# <a name="scene-understanding-sdk-overview"></a>Présentation du SDK présentation de Scene

La compréhension de la scène transforme les données de capteur d’environnement non structurées que votre appareil de réalité mixte capture et les convertit en une représentation abstraite puissante. Le kit de développement logiciel (SDK) joue le rôle de couche de communication entre votre application et le runtime Understanding. Elle est destinée à reproduire les constructions standard existantes, telles que les graphiques de scène 3D pour les représentations 3D, ainsi que les rectangles et panneaux 2D pour les applications 2D. Tandis que la construction de scènes comprenant les imitations sera mappée aux frameworks concrets, en général SceneUnderstanding est une infrastructure agnostique qui autorise l’interopérabilité entre des infrastructures variées qui interagissent avec elle. À mesure que la compréhension de la scène évolue, le rôle du kit de développement logiciel (SDK) consiste à s’assurer que de nouvelles représentations et fonctionnalités continuent à être exposées au sein d’une infrastructure unifiée. Dans ce document, nous allons commencer par introduire des concepts de haut niveau qui vous aideront à vous familiariser avec l’environnement de développement/l’utilisation, puis à fournir une documentation plus détaillée pour des classes et des constructions spécifiques.

## <a name="where-do-i-get-the-sdk"></a>Où puis-je me procurer le kit de développement logiciel ?

Le kit de développement logiciel (SDK) SceneUnderstanding peut être téléchargé via l’outil de la [fonctionnalité de réalité mixte](../unity/welcome-to-mr-feature-tool.md).

**Remarque :** la version la plus récente dépend des packages de préversion et vous devez activer les packages de préversions pour les afficher.

Pour la version 0.5.2022-RC et les versions ultérieures, Scene Understanding prend en charge les projections de langage pour C# et C++ permettant aux applications de développer des applications pour les plateformes Win32 ou UWP. À compter de cette version, SceneUnderstanding prend en charge Unity dans le cadre de la prise en charge de l’éditeur, qui est utilisée uniquement pour communiquer avec HoloLens2. 

SceneUnderstanding requiert SDK Windows version 18362 ou ultérieure. 

## <a name="conceptual-overview"></a>Vue d'ensemble conceptuelle

### <a name="the-scene"></a>La scène

Votre appareil de réalité mixte intègre constamment des informations sur ce qu’il voit dans votre environnement. La compréhension de la scène entonnoir toutes ces sources de données et produit une seule abstraction cohésive. La compréhension des scènes génère des scènes, qui constituent une composition de [SceneObjects](scene-understanding-SDK.md#sceneobjects) représentant une instance d’une seule chose, (par exemple, un mur/un plafond/étage). Les objets de scène sont eux-mêmes une composition de [SceneComponents, qui représentent des éléments plus granulaires qui composent ce SceneObject. Les exemples de composants sont les Quad et les maillages, mais à l’avenir, ils pourraient représenter des zones englobantes, des maillages de collision, des métadonnées, etc.

Le processus de conversion des données de capteur brutes en scène est une opération potentiellement coûteuse qui peut prendre des secondes pour les espaces moyens (~ 10x10m) à minutes pour les espaces de grande taille (~ 50x50m). par conséquent, il ne s’agit pas d’un calcul effectué par l’appareil sans demande d’application. Au lieu de cela, la génération de scènes est déclenchée par votre application à la demande. La classe SceneObserver a des méthodes statiques qui peuvent calculer ou désérialiser une scène, que vous pouvez ensuite énumérer/interagir avec. L’action « Compute » est exécutée à la demande et s’exécute sur l’UC, mais dans un processus séparé (le pilote de réalité mixte). Toutefois, pendant que nous effectuons le calcul dans un autre processus, les données de scène obtenues sont stockées et conservées dans votre application dans l’objet de scène. 

Vous trouverez ci-dessous un diagramme qui illustre ce processus et montre des exemples de deux applications interagissant avec le runtime de la vision de la scène. 

![Diagramme de processus](images/SU-ProcessFlow.png)

Sur le côté gauche figure un diagramme du runtime de la réalité mixte, qui est toujours actif et s’exécute dans son propre processus. Ce Runtime est chargé d’effectuer le suivi des appareils, le mappage spatial et d’autres opérations que la présentation de Scene utilise pour comprendre et expliquer le monde autour de vous. Sur le côté droit du diagramme, nous présentons deux applications théoriques qui utilisent la compréhension des scènes. La première application interface avec MRTK, qui utilise le kit de développement logiciel (SDK) de scène en interne, la deuxième application calcule et utilise deux instances de scène distinctes. Les trois scènes de ce diagramme génèrent des instances distinctes des scènes, le pilote n’effectue pas le suivi de l’état global partagé entre les applications et les objets de scène dans une scène introuvable dans une autre. La compréhension de la scène fournit un mécanisme de suivi au fil du temps, mais cette opération s’effectue à l’aide du kit de développement logiciel (SDK). Le code de suivi est déjà en cours d’exécution dans le kit de développement logiciel (SDK) dans le processus de votre application.

Étant donné que chaque scène stocke ses données dans l’espace mémoire de votre application, vous pouvez supposer que toutes les fonctions de l’objet de la scène ou de ses données internes sont toujours exécutées dans le processus de votre application.

### <a name="layout"></a>Layout

Pour travailler avec la compréhension des scènes, il peut être utile de savoir et de comprendre comment le runtime représente des composants logiquement et physiquement. La scène représente des données avec une disposition spécifique qui a été choisie comme simple tout en conservant une structure sous-jacente qui est pliable pour répondre aux exigences futures sans avoir besoin de révisions majeures. Pour ce faire, la scène stocke tous les composants (blocs de construction pour tous les objets de scène) dans une liste plate et définit la hiérarchie et la composition par le biais de références où des composants spécifiques référencent d’autres.

Ci-dessous, nous présentons un exemple de structure dans sa forme plate et logique.

<table>
<tr><th>Disposition logique</th><th>Disposition physique</th></tr>
<tr>
<td>
<ul>
  Scene
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

Cette illustration met en évidence la différence entre la disposition physique et logique de la scène. Sur la gauche, nous voyons la disposition hiérarchique des données que votre application voit lors de l’énumération de la scène. À droite, nous voyons que la scène est composée de 12 composants distincts qui sont accessibles individuellement si nécessaire. Lors du traitement d’une nouvelle scène, nous pensons que les applications parcourent cette hiérarchie logiquement, toutefois, lors du suivi entre les mises à jour de la scène, certaines applications peuvent uniquement être intéressées à cibler des composants spécifiques qui sont partagés entre deux scènes.

## <a name="api-overview"></a>Présentation de l’API

La section suivante fournit une vue d’ensemble des constructions de la présentation des scènes. La lecture de cette section vous donne une idée de la façon dont les scènes sont représentées, ainsi que de l’utilisation des différents composants. La section suivante fournit des exemples de code concrets et des détails supplémentaires qui sont brillants dans cette vue d’ensemble.

Tous les types décrits ci-dessous résident dans l' `Microsoft.MixedReality.SceneUnderstanding` espace de noms.

### <a name="scenecomponents"></a>SceneComponents

Maintenant que vous comprenez la disposition logique des scènes, nous pouvons maintenant présenter le concept de SceneComponents et la façon dont ils sont utilisés pour composer la hiérarchie. Les SceneComponents sont les décompositions les plus granulaires de SceneUnderstanding qui représentent un seul élément fondamental, par exemple, une maille ou un quadruple-Box ou un cadre englobant. Les SceneComponents sont des éléments qui peuvent être mis à jour de manière indépendante et peuvent être référencés par d’autres SceneComponents, de sorte qu’ils disposent d’un ID unique de propriété globale unique, qui autorise ce type de mécanisme de suivi/référencement. Les ID sont utilisés pour la composition logique de la hiérarchie des scènes, ainsi que pour la persistance des objets (opération consistant à mettre à jour une scène par rapport à une autre.) 

Si vous traitez toutes les scènes nouvellement calculées comme étant distinctes et que vous énumérez simplement toutes les données qu’elle contient, les ID sont en grande partie transparents pour vous. Toutefois, si vous envisagez de suivre des composants sur plusieurs mises à jour, vous utiliserez les ID pour indexer et Rechercher des SceneComponents entre les objets de scène.

### <a name="sceneobjects"></a>SceneObjects

Un SceneObject est un SceneComponent qui représente une instance d’un « élément » (par exemple, un mur, un étage, un plafond, etc.). exprimé par leur propriété Kind. Les SceneObjects sont géométriques et, par conséquent, ont des fonctions et des propriétés qui représentent leur emplacement dans l’espace, mais elles ne contiennent pas de structure géométrique ou logique. Au lieu de cela, SceneObjects référence d’autres SceneComponents, en particulier SceneQuads et SceneMeshes, qui fournissent les représentations variées prises en charge par le système. Quand une nouvelle scène est calculée, votre application va probablement énumérer le SceneObjects de la scène pour traiter ce qui l’intéresse.

SceneObjects peut avoir l’un des éléments suivants :

<table>
<tr>
<th>SceneObjectKind</th> <th>Description</th>
</tr>
<tr><td>Contexte</td><td>Le SceneObject est connu pour <b>ne pas</b> être l’un des autres types d’objets de scène reconnus. Cette classe ne doit pas être confondue avec Unknown, où l’arrière-plan est connu comme étant un mur/plancher/plafond, etc... alors que inconnu n’est pas encore catégorisé.</b></td></tr>
<tr><td>Mur</td><td>Un mur physique. Les murs sont supposés être des structures environnementales immobilières.</td></tr>
<tr><td>Floor</td><td>Les étages sont des surfaces sur lesquelles il est possible de parcourir. Remarque : les escaliers ne sont pas des étages. Notez également que les étages supposent une surface pouvant être guidée et qu’il n’y a donc pas d’hypothèse explicite d’un étage singulier. Structures à plusieurs niveaux, rampes, etc... doit tous être classifiés en tant que plancher.</td></tr>
<tr><td>Ceiling</td><td>Surface supérieure d’une salle.</td></tr>
<tr><td>Plateforme</td><td>Grande surface plate sur laquelle vous pouvez placer des hologrammes. Elles ont tendance à représenter des tables, des plans de plan et d’autres grandes surfaces horizontales.</td></tr>
<tr><td>World (Monde)</td><td>Étiquette réservée pour les données géométriques indépendantes de l’étiquetage. La maille générée par la définition de l’indicateur de mise à jour EnableWorldMesh est classée comme monde.</td></tr>
<tr><td>Unknown</td><td>Cet objet de scène n’a pas encore été classé et affecté un genre. Cette opération ne doit pas être confondue avec l’arrière-plan, car cet objet peut être n’importe quoi, le système n’a pas encore pu trouver une classification suffisamment importante pour cela.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

Un SceneMesh est un SceneComponent qui se rapproche de la géométrie des objets géométriques arbitraires à l’aide d’une liste de triangles. Les SceneMeshes sont utilisés dans plusieurs contextes différents, ils peuvent représenter des composants de la structure de cellules étanches ou en tant que WorldMesh, qui représente le maillage de mappage spatial non lié à la scène. Les données d’index et de vertex fournies avec chaque maille utilisent la même disposition familière que les [mémoires tampons de vertex et d’index](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) utilisées pour le rendu des maillages de triangle dans toutes les API de rendu modernes. Dans la compréhension de la scène, les maillages utilisent des index 32 bits et peuvent avoir besoin d’être décomposés en segments pour certains moteurs de rendu.

#### <a name="winding-order-and-coordinate-systems"></a>Ordre d’enroulement et systèmes de coordonnées

Tous les maillages produits par la compréhension des scènes sont censés retourner des maillages dans un système de coordonnées Right-Handed à l’aide de l’ordre de séquencement des aiguilles d’une montre. 

Remarque : les builds de système d’exploitation antérieures à. 191105 peuvent avoir un bogue connu dans lequel les mailles « World » renvoient dans Counter-Clockwise ordre d’enroulement, qui a été résolu par la suite.

### <a name="scenequad"></a>SceneQuad

Un SceneQuad est un SceneComponent qui représente des surfaces 2D qui occupent le monde 3D. SceneQuads peut être utilisé de la même façon que les plans ARKit ARPlaneAnchor ou ARCore, mais ils offrent des fonctionnalités de haut niveau en tant que canevas 2D à utiliser par les applications plates, ou une expérience utilisateur améliorée. des API spécifiques 2D sont fournies pour les quatre cœurs qui facilitent l’utilisation de l’emplacement et de la disposition, et le développement (à l’exception du rendu) avec quatre cœurs doit avoir un sens plus semblable à l’utilisation de canevas 2D que les maillages 3D.

#### <a name="scenequad-shape"></a>Forme SceneQuad

SceneQuads définit une surface rectangulaire délimitée en 2D. Toutefois, les SceneQuads représentent des surfaces avec des formes arbitraires et potentiellement complexes (par exemple, une table en forme de bouée). Pour représenter la forme complexe de la surface d’un quadruple, vous pouvez utiliser l’API GetSurfaceMask pour afficher la forme de la surface dans une mémoire tampon d’image que vous fournissez. Si le SceneObject qui a le quad a également une maille, les triangles de maillage doivent être équivalents à cette image rendue, ils représentent tous les deux une géométrie réelle de la surface, soit en coordonnées 2D, soit en coordonnées 3D.

## <a name="scene-understanding-sdk-details-and-reference"></a>Description et informations de référence du SDK

> [!NOTE] 
> Lorsque vous utilisez MRTK, Notez que vous interagissez avec MRTK [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) et que vous pouvez donc ignorer cette section dans la plupart des cas. Pour plus d’informations, reportez-vous à la [documentation de MRTK Scene](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) .

La section suivante vous aidera à vous familiariser avec les principes fondamentaux de SceneUnderstanding. Cette section doit vous fournir les principes de base, à partir desquels vous devez disposer d’un contexte suffisant pour parcourir les exemples d’applications et voir comment SceneUnderstanding est utilisé de manière holistique.

### <a name="initialization"></a>Initialisation

La première étape de l’utilisation de SceneUnderstanding est de permettre à votre application d’obtenir une référence à un objet de scène. Cette opération peut être effectuée de deux manières : une scène peut être calculée par le pilote, ou une scène existante qui a été calculée dans le passé peut être désérialisée. Ce dernier est utile pour travailler avec SceneUnderstanding pendant le développement, où les applications et les expériences peuvent être rapidement prototypées sans appareil de réalité mixte.

Les scènes sont calculées à l’aide d’un SceneObserver. Avant de créer une scène, votre application doit interroger votre appareil pour s’assurer qu’il prend en charge SceneUnderstanding, ainsi que pour demander l’accès utilisateur aux informations dont SceneUnderstanding a besoin.

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Si RequestAccessAsync () n’est pas appelé, le calcul d’une nouvelle scène échoue. Ensuite, nous allons calculer une nouvelle scène enracinée autour du casque de la réalité mixte et ayant un rayon de 10 mètres.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>Initialisation à partir des données (également appelée. le chemin d’accès du PC)

Si les scènes peuvent être calculées pour une consommation directe, elles peuvent également être calculées sous forme sérialisée pour une utilisation ultérieure. Cela s’est avéré utile pour le développement car il permet aux développeurs de travailler dans et de tester la compréhension des scènes sans avoir besoin d’un appareil. L’acte de sérialisation d’une scène est quasiment identique à son calcul, les données sont retournées à votre application au lieu d’être désérialisées localement par le kit de développement logiciel (SDK). Vous pouvez ensuite le désérialiser vous-même ou l’enregistrer pour une utilisation ultérieure.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a>Énumération SceneObject

Maintenant que votre application a une scène, votre application va regarder et interagir avec SceneObjects. Pour ce faire, accédez à la propriété **SceneObjects** :

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a>Mise à jour des composants et rerecherche de composants

Il existe une autre fonction qui récupère les composants de la scène appelée ***FindComponent***. Cette fonction est utile lors de la mise à jour des objets de suivi et leur recherche dans des scènes ultérieures. Le code suivant calcule une nouvelle scène par rapport à une scène précédente, puis trouve le plancher dans la nouvelle scène.

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Accès aux maillages et aux quads à partir d’objets de scène

Une fois les SceneObjects trouvés, votre application souhaitera probablement accéder aux données contenues dans les quadruples/les maillages dont elle est composée. Ces données sont accessibles avec les propriétés ***quads** _ et _ *_meshes_**. Le code suivant énumère tous les Quad et les maillages de notre objet Floor.

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Notez qu’il s’agit de la SceneObject qui a la transformation par rapport à l’origine de la scène. Cela est dû au fait que SceneObject représente une instance d’un « élément » et qu’il est localisable dans l’espace, les Quad et les maillages représentent la géométrie transformée par rapport à leur parent. Il est possible pour des SceneObjects distincts de référencer le même SceneComponents SceneMesh/SceneQuad, et il est également possible qu’un SceneObject ait plus d’un SceneMesh/SceneQuad.

### <a name="dealing-with-transforms"></a>Traitement des transformations

La compréhension des scènes a fait une tentative délibérée d’alignement avec les représentations de scène 3D traditionnelles lors du traitement des transformations. Chaque scène est donc confinée à un système de coordonnées unique, à l’instar des représentations environnementales 3D les plus courantes. Les SceneObjects fournissent chacun leur emplacement par rapport à ce système de coordonnées. Si votre application traite des scènes qui étendent la limite de ce qu’une origine unique fournit peut ancrer SceneObjects à SpatialAnchors, ou générer plusieurs scènes et les fusionner, mais pour des raisons de simplicité, nous supposons que des scènes étanches existent dans leur propre origine et sont localisées par un NodeId défini par Scene. OriginSpatialGraphNodeId.

le code unity suivant, par exemple, montre comment utiliser les api Windows Perception et unity pour aligner les systèmes de coordonnées ensemble. pour plus d’informations sur l’obtention d’un SpatialCoordinateSystem qui correspond à l’origine universelle d’unity, consultez [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) et [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) . pour plus d’informations sur les api de Perception de la Windows et les [objets natifs de réalité mixte dans unity](/windows/mixed-reality/unity-xrdevice-advanced) .

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

Chaque `SceneObject` a une transformation, qui est ensuite appliquée à cet objet. Dans Unity, nous convertissons les coordonnées vers la droite et assignerons des transformations locales comme suit :

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a>Quadruple

Les Quad sont conçus pour aider les scénarios de placement 2D et doivent être considérés comme des extensions aux éléments d’expérience utilisateur 2D Canvas. Alors que les Quad sont des composants de SceneObjects et peuvent être rendus en 3D, les API Quad elles-mêmes partent du principe que les quatre cœurs sont des structures 2D. Elles offrent des informations telles que l’étendue, la forme et fournissent des API pour le positionnement.

Les Quad présentent des étendues rectangulaires, mais elles représentent des surfaces 2D de forme arbitraire. Pour activer la position sur ces surfaces 2D qui interagissent avec les utilitaires de l’environnement 3D quads, vous pouvez faire en sorte que cette interaction soit possible. Actuellement, la compréhension des scènes fournit deux fonctions telles que **FindCentermostPlacement** et **GetSurfaceMask**. FindCentermostPlacement est une API de haut niveau qui localise une position sur le quadruple dans laquelle un objet peut être placé et tente de trouver le meilleur emplacement pour votre objet, garantissant ainsi que le cadre englobant que vous fournissez reste sur la surface sous-jacente.

> [!NOTE]
> Les coordonnées de la sortie sont relatives au Quad dans « espace quadruple » avec le coin supérieur gauche (x = 0, y = 0), comme c’est le cas avec d’autres types de fenêtres Rect. Veillez à prendre cela en compte lorsque vous travaillez avec les origines de vos propres objets. 

L’exemple suivant montre comment Rechercher l’emplacement positionnable centermost et ancrer un hologramme au quadruple.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

Les étapes 1-4 sont fortement dépendantes de votre infrastructure/implémentation particulière, mais les thèmes doivent être similaires. Il est important de noter que le quad représente simplement un plan 2D limité qui est localisé dans l’espace. En faisant savoir à votre moteur/infrastructure où se trouve le quad et la racine de vos objets par rapport au Quad, vos hologrammes se trouveront correctement en ce qui concerne le monde réel. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>Maillage

Les maillages représentent les représentations géométriques des objets ou des environnements. À l’instar du [mappage spatial](../../design/spatial-mapping.md), les données de vertex et d’index de maillage fournies avec chaque maillage de surface spatiale utilisent la même disposition familière que les mémoires tampons de vertex et d’index utilisées pour le rendu des maillages de triangle dans toutes les API de rendu modernes. Les positions de vertex sont fournies dans le système de coordonnées de `Scene` . Les API spécifiques utilisées pour référencer ces données sont les suivantes :

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

Le code suivant fournit un exemple de génération d’une liste de triangles à partir de la structure de maillage :

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

Les mémoires tampons d’index/vertex doivent être >= nombre d’index/vertex, mais peuvent être de taille arbitraire, ce qui permet une réutilisation efficace de la mémoire.

### <a name="collidermesh"></a>ColliderMesh

Les objets de scène fournissent l’accès aux données de maillage et de mailleur par le biais des propriétés MESHS et ColliderMeshes. Ces maillages correspondent toujours, ce qui signifie que l’index IE de la propriété meshes représente la même géométrie que l’index IE de la propriété ColliderMeshes. Si le runtime/objet prend en charge les maillages de collisions, vous êtes assuré d’avoir le polygone le plus bas, la meilleure approximation d’ordre et il est conseillé d’utiliser ColliderMeshes partout où votre application utilise des conflits. Si le système ne prend pas en charge les conflits, l’objet de maillage retourné dans ColliderMeshes sera le même objet que le maillage pour réduire les contraintes de mémoire.

## <a name="developing-with-scene-understanding"></a>Développement avec la compréhension de la scène

À ce stade, vous devez comprendre les principaux blocs de construction de la scène présentation du runtime et du kit de développement logiciel (SDK). La majeure partie de la puissance et de la complexité se trouve dans les modèles d’accès, l’interaction avec les frameworks 3D et les outils qui peuvent être écrits sur ces API pour effectuer des tâches plus avancées telles que la planification spatiale, l’analyse de la salle, la navigation, la physique, etc. Nous espérons capturer ces exemples dans des exemples qui devraient vous guider dans la bonne direction pour que vos scénarios brillent. S’il existe des exemples ou des scénarios que nous n’adressons pas, faites-le nous savoir et nous essaierons de documenter/prototyper ce dont vous avez besoin.

### <a name="where-can-i-get-sample-code"></a>Où puis-je recevoir un exemple de code ?

Vous trouverez des exemples de code pour Unity dans notre page d' [exemple Unity](https://github.com/sceneunderstanding-microsoft/unitysample) . Cette application vous permet de communiquer avec votre appareil et de restituer les différents objets de scène, ou vous permet de charger une scène sérialisée sur votre ordinateur et de vous permettre de découvrir la scène sans appareil.

### <a name="where-can-i-get-sample-scenes"></a>Où puis-je me procurer des exemples de scènes ?

Si vous avez un HoloLens2, vous pouvez enregistrer toute scène que vous avez capturée en enregistrant la sortie de ComputeSerializedAsync dans un fichier et en la désérialisant à votre convenance. 

Si vous n’avez pas d’appareil HoloLens2 mais que vous souhaitez jouer avec la compréhension des scènes, vous devez télécharger une scène précapturée. L’exemple Scene Understanding est actuellement fourni avec des scènes sérialisées qui peuvent être téléchargées et utilisées à votre convenance. Vous pouvez les trouver ici :

[Exemples de scènes de vision](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>Voir aussi

* [Mappage spatial](../../design/spatial-mapping.md)
* [Compréhension des scènes](../../design/scene-understanding.md)
* [Exemple Unity](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)