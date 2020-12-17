---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855879"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="e6adb-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e6adb-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="e6adb-102">Option</span><span class="sxs-lookup"><span data-stu-id="e6adb-102">Option</span></span> | <span data-ttu-id="e6adb-103">Description</span><span class="sxs-lookup"><span data-stu-id="e6adb-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="e6adb-104">Prend l’adresse IP (et le port facultatif) de l’appareil HoloLens 2 auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e6adb-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="e6adb-105">Si aucun port n’est fourni, la valeur par défaut est 8265.</span><span class="sxs-lookup"><span data-stu-id="e6adb-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="e6adb-106">(facultative) Valeur par défaut 8000.</span><span class="sxs-lookup"><span data-stu-id="e6adb-106">(optional) Default 8000.</span></span> <span data-ttu-id="e6adb-107">Taux de transfert réseau maximal (Ko/s).</span><span class="sxs-lookup"><span data-stu-id="e6adb-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="e6adb-108">(facultative) Démarre un serveur d’écoute.</span><span class="sxs-lookup"><span data-stu-id="e6adb-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="e6adb-109">(facultative) Prend le port d’écoute.</span><span class="sxs-lookup"><span data-stu-id="e6adb-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="e6adb-110">Utilisée pour la connexion à un PC ou à une machine virtuelle à partir d’un appareil HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e6adb-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="e6adb-111">(dépréciée dans 4.26) Prend l’adresse IP de l’appareil HoloLens 1 auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e6adb-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="e6adb-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="e6adb-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="e6adb-113">Option</span><span class="sxs-lookup"><span data-stu-id="e6adb-113">Option</span></span> | <span data-ttu-id="e6adb-114">Description</span><span class="sxs-lookup"><span data-stu-id="e6adb-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="e6adb-115">Prend l’adresse IP (et le port facultatif, dont la valeur par défaut est 8265) de l’appareil HoloLens 2 auquel se connecter, ou le port sur lequel l’application doit écouter les connexions.</span><span class="sxs-lookup"><span data-stu-id="e6adb-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="e6adb-116">(facultative) Utilise l’audio du PC lors de la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="e6adb-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="e6adb-117">(facultative) Démarre un serveur d’écoute.</span><span class="sxs-lookup"><span data-stu-id="e6adb-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="e6adb-118">(facultative) Valeur par défaut 8000.</span><span class="sxs-lookup"><span data-stu-id="e6adb-118">(optional) Default 8000.</span></span> <span data-ttu-id="e6adb-119">Taux de transfert réseau maximal (Ko/s).</span><span class="sxs-lookup"><span data-stu-id="e6adb-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="e6adb-120">(facultative) Codec de connexion</span><span class="sxs-lookup"><span data-stu-id="e6adb-120">(optional) Connection codec</span></span>  |