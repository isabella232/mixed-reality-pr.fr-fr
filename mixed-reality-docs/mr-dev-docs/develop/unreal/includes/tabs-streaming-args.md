---
ms.openlocfilehash: 283ef0bedc96a63d34a66fa0d88dee97420957c7744ad3702c6ac3bc34c14310
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218855"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| Option | Description |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | Prend l’adresse IP (et le port facultatif) de l’appareil HoloLens 2 auquel se connecter. Si aucun port n’est fourni, la valeur par défaut est 8265. |
| `-RemotingBitrate=<bitrate>` | (facultative) Valeur par défaut 8000. Taux de transfert réseau maximal (Ko/s). |
| `-HoloLensRemotingListen` | (facultative) Démarre un serveur d’écoute. |
| `-HoloLensRemotingListenPort=<port>` | (facultative) Prend le port d’écoute. Utilisée pour la connexion à un PC ou à une machine virtuelle à partir d’un appareil HoloLens. |
| `-HoloLens1Remoting=<IP address>` | (dépréciée dans 4.26) Prend l’adresse IP de l’appareil HoloLens 1 auquel se connecter. |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| Option | Description |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | Prend l’adresse IP (et le port facultatif, dont la valeur par défaut est 8265) de l’appareil HoloLens 2 auquel se connecter, ou le port sur lequel l’application doit écouter les connexions. |
| `-EnableAudio` | (facultative) Utilise l’audio du PC lors de la communication à distance.  |
| `-Listen` | (facultative) Démarre un serveur d’écoute. |
| `-RemotingBitrate=<bitrate>` | (facultative) Valeur par défaut 8000. Taux de transfert réseau maximal (Ko/s). |
| `-RemotingCodec=<codec>` | (facultative) Codec de connexion  |