---
title: Persistance dans Unity
description: La persistance permet à vos utilisateurs d’épingler des hologrammes individuels ou un espace de travail où qu’ils le souhaitent, puis de les trouver plus tard là où ils s’attendent à plusieurs utilisations de votre application.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistance, Unity
ms.openlocfilehash: bb1a9b0544f9325a60c86c7424b7b451b6b4335b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91682459"
---
# <a name="persistence-in-unity"></a>Persistance dans Unity

**Espace de noms :** *UnityEngine. XR. WSA. persistance*<br>
**Classe :** *WorldAnchorStore*

Le WorldAnchorStore est la clé de la création d’expériences holographiques dans lesquelles les hologrammes restent dans des positions réelles spécifiques entre les instances de l’application. Cela permet à vos utilisateurs d’épingler des hologrammes individuels ou un espace de travail où qu’ils le souhaitent, puis de les trouver plus tard là où ils s’attendent à plusieurs utilisations de votre application.

## <a name="how-to-persist-holograms-across-sessions"></a>Comment conserver des hologrammes entre les sessions

Le WorldAnchorStore vous permet de conserver l’emplacement des WorldAnchor entre les sessions. Pour conserver les hologrammes entre les sessions, vous devez effectuer un suivi séparé de vos GameObjects qui utilisent une ancre mondiale particulière. Il est souvent judicieux de créer une racine GameObject avec une ancre mondiale et de faire en sorte que les hologrammes enfants soient ancrés avec un décalage de position local.

Pour charger des hologrammes à partir de sessions précédentes :
1. Obtient le WorldAnchorStore
2. Charger les données d’application relatives à l’ancre mondiale qui vous donne l’ID de l’ancre mondiale
3. Charger une ancre universelle à partir de son ID

Pour enregistrer des hologrammes pour les sessions à venir :
1. Obtient le WorldAnchorStore
2. Enregistrer une ancre mondiale en spécifiant un ID
3. Enregistrer les données d’application relatives à l’ancre mondiale avec un ID

### <a name="getting-the-worldanchorstore"></a>Obtention du WorldAnchorStore

Nous souhaitons conserver une référence à WorldAnchorStore pour nous assurer que nous sommes prêts à travailler lorsque nous souhaitons effectuer une opération. Étant donné qu’il s’agit d’un appel asynchrone, éventuellement dès le démarrage, nous souhaitons appeler

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

Dans ce cas, StoreLoaded est notre gestionnaire pour la fin du chargement du WorldAnchorStore :

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Nous disposons maintenant d’une référence au WorldAnchorStore que nous allons utiliser pour enregistrer et charger des ancres universelles spécifiques.

### <a name="saving-a-worldanchor"></a>Enregistrement d’un WorldAnchor

Pour ce faire, nous devons simplement nommer ce que nous enregistrons et le transférer dans le WorldAnchor que nous avons reçu avant l’enregistrement. Remarque : la tentative d’enregistrement de deux ancres dans la même chaîne échoue (Store. L’enregistrement retourne la valeur false). Vous devez supprimer le précédent enregistrement avant d’enregistrer le nouveau fichier :

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>Chargement d’un WorldAnchor

Et pour charger :

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

Nous pouvons également utiliser le Store. Delete () pour supprimer une ancre précédemment enregistrée et stockée. Clear () pour supprimer toutes les données précédemment enregistrées.

### <a name="enumerating-existing-anchors"></a>Énumération des ancres existantes

Pour découvrir les ancres précédemment stockées, appelez GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistance des hologrammes pour plusieurs appareils

Vous pouvez utiliser des <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer une ancre Cloud durable à partir d’un WorldAnchor local, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android, même si ces appareils ne sont pas présents simultanément.  Étant donné que les ancres Cloud sont persistantes, plusieurs périphériques peuvent voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.

Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.

Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours du point de contrôle de développement Unity que nous avons mis en place, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte. À partir de là, vous pouvez passer au bloc de construction suivant :

> [!div class="nextstepaction"]
> [Mappage spatial](spatial-mapping-in-unity.md)

Ou accédez aux API et fonctionnalités de la plateforme de réalité mixte :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez toujours revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Persistance d’ancrage spatial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity</a>
