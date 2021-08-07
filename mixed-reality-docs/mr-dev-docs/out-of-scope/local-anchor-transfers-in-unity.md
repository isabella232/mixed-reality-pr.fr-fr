---
title: Transferts d’ancrage locaux dans Unity
description: découvrez comment transférer des points d’ancrage entre plusieurs HoloLens appareils dans une application unity de réalité mixte.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Partage, ancrer, WorldAnchor, m partage 250, WorldAnchorTransferBatch, SpatialPerception, transfert, transfert d’ancrage local, exportation d’ancrage, importation d’ancrage
ms.openlocfilehash: eaf25edbae39aab628277aa29f975f3d4d9d7374c796fd1b7b159053d4a46b95
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189126"
---
# <a name="local-anchor-transfers-in-unity"></a>Transferts d’ancrage locaux dans Unity

dans les situations où vous ne pouvez pas utiliser les <a href="/azure/spatial-anchors" target="_blank">ancres spatiales Azure</a>, les transferts d’ancrage locaux permettent à un appareil HoloLens d’exporter une ancre pour qu’elle soit importée par un deuxième HoloLens appareil.

>[!NOTE]
>Les transferts d’ancrage locaux fournissent un rappel d’ancrage moins fiable que les <a href="/azure/spatial-anchors" target="_blank">ancres spatiales Azure</a>, et les appareils iOS et Android ne sont pas pris en charge par cette approche.

### <a name="setting-the-spatialperception-capability"></a>Définition de la fonctionnalité SpatialPerception

Pour qu’une application puisse transférer des ancres spatiales, la capacité *SpatialPerception* doit être activée.

Comment activer la fonctionnalité *SpatialPerception* :
1. dans l’éditeur unity, ouvrez le volet **« Paramètres player »** (modifier > Project Paramètres player >)
2. cliquez sur l’onglet **« Store de Windows »**
3. développez **« publication Paramètres »** , puis vérifiez la fonctionnalité **« SpatialPerception »** dans la liste **« fonctionnalités »** .

>[!NOTE]
>si vous avez déjà exporté votre projet unity vers une solution Visual Studio, vous devez l’exporter vers un nouveau dossier ou définir manuellement [cette fonctionnalité dans le AppxManifest de Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Transfert d’ancrage

**Espace de noms :** *UnityEngine. XR. WSA. Sharing*<br>
**Type**: *WorldAnchorTransferBatch*

Pour transférer un [WorldAnchor](../develop/unity/coordinate-systems-in-unity.md), vous devez établir l’ancre à transférer. l’utilisateur d’un HoloLens analyse son environnement et choisit manuellement ou par programme un point dans l’espace pour être l’ancre de l’expérience partagée. Les données qui représentent ce point peuvent ensuite être sérialisées et transmises aux autres périphériques qui partagent l’expérience. Chaque appareil désérialise ensuite les données d’ancrage et tente de localiser ce point dans l’espace. Pour que le transfert d’ancrage fonctionne, chaque appareil doit avoir effectué une analyse suffisante de l’environnement, de telle sorte que le point représenté par l’ancre puisse être identifié.

### <a name="setup"></a>Installation

L’exemple de code sur cette page contient quelques champs qui devront être initialisés :
1. *Gameobject rootGameObject* est un *gameobject* dans Unity qui contient un composant *WorldAnchor* . Un utilisateur de l’expérience partagée placera ce *gameobject* et exportera les données vers les autres utilisateurs.
2. *WorldAnchor gameRootAnchor* est le *UnityEngine. XR. WSA. WorldAnchor* qui est sur *rootGameObject*.
3. *Byte [] importedData* est un tableau d’octets pour l’ancre sérialisée que chaque client reçoit sur le réseau.

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>Exportation

Pour exporter, nous avons juste besoin d’un *WorldAnchor* et de savoir ce que nous appelons pour l’application réceptrice. Un client de l’expérience partagée effectue les étapes suivantes pour exporter l’ancre partagée :
1. Créer un *WorldAnchorTransferBatch*
2. Ajouter le *WorldAnchors* à transférer
3. Commencer l’exportation
4. Gérer l’événement *OnExportDataAvailable* à mesure que les données deviennent disponibles
5. Gérer l’événement *OnExportComplete*

Nous créons un *WorldAnchorTransferBatch* pour encapsuler ce que nous allons transférer, puis l’exporter dans octets :

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

À mesure que les données deviennent disponibles, envoyez les octets au client ou à la mémoire tampon sous forme de segments de données disponibles et envoyés par n’importe quel moyen souhaité :

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Une fois l’exportation terminée, si nous avons transféré des données et que la sérialisation a échoué, demandez au client d’ignorer les données. Si la sérialisation a réussi, indiquez au client que toutes les données ont été transférées et que l’importation peut commencer :

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>Importation en cours

Après avoir reçu tous les octets de l’expéditeur, nous pouvons réimporter les données dans un *WorldAnchorTransferBatch* et verrouiller notre objet de jeu racine dans le même emplacement physique. Remarque : l’importation peut échouer momentanément et doit être retentée :

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

Une fois qu’un *gameobject* est verrouillé via l’appel *lockobject* , il aura un *WorldAnchor* qui le conservera dans la même position physique dans le monde, mais il peut se trouver à un emplacement différent dans l’espace de coordonnées Unity que d’autres utilisateurs.