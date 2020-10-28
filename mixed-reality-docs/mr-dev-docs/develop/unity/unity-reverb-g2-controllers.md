---
title: Contrôleurs de réverbération HP G2 dans Unity
description: Instructions sur l’utilisation des contrôleurs de réverbération HP G2 dans SteamVR et Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, réverbération, réverbération G2, réverbération HP G2, réalité mixte, développement, contrôleurs de mouvement, entrée d’utilisateur, fonctionnalités, nouveau projet, émulateur, documentation, guides, fonctionnalités, hologrammes, développement de jeux
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638386"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="8f8ad-104">Contrôleurs de réverbération HP G2 dans Unity</span><span class="sxs-lookup"><span data-stu-id="8f8ad-104">HP Reverb G2 Controllers in Unity</span></span>

## <a name="getting-started"></a><span data-ttu-id="8f8ad-105">Prise en main</span><span class="sxs-lookup"><span data-stu-id="8f8ad-105">Getting started</span></span>

<span data-ttu-id="8f8ad-106">Aucune configuration supplémentaire n’est requise pour utiliser le contrôleur de réverbération HP G2 si vous développez pour SteamVR ou à l’aide de l’API d’entrée Windows Mixed Reality (XR. WSA. Entrée).</span><span class="sxs-lookup"><span data-stu-id="8f8ad-106">There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input).</span></span> <span data-ttu-id="8f8ad-107">Toutefois, les boutons A, B, X, Y et le déclencheur d’utilisation ne sont pas accessibles actuellement via le gestionnaire d’entrée, sauf si vous utilisez SteamVR.</span><span class="sxs-lookup"><span data-stu-id="8f8ad-107">However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR.</span></span> <span data-ttu-id="8f8ad-108">La prise en charge des entrées de réverbération G2 supplémentaires sera disponible prochainement. n’hésitez pas à vérifier.</span><span class="sxs-lookup"><span data-stu-id="8f8ad-108">Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!</span></span>

## <a name="porting-existing-applications"></a><span data-ttu-id="8f8ad-109">Portage d’applications existantes</span><span class="sxs-lookup"><span data-stu-id="8f8ad-109">Porting existing applications</span></span>

<span data-ttu-id="8f8ad-110">Si vous disposez déjà d’une application existante que vous développez pour des casques immersifs de Windows Mixed Reality, consultez les sections [Guide de Portage](../porting-apps/porting-guides.md) et [paramètres du projet](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) pour obtenir des suggestions générales.</span><span class="sxs-lookup"><span data-stu-id="8f8ad-110">If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.</span></span>

## <a name="mapping-input"></a><span data-ttu-id="8f8ad-111">Entrée de mappage</span><span class="sxs-lookup"><span data-stu-id="8f8ad-111">Mapping input</span></span>

<span data-ttu-id="8f8ad-112">Lorsque vous êtes prêt à faire fonctionner votre mappage d’entrée pour vos nouveaux contrôleurs, commencez par la section [mappage d’entrée](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) du Guide de Portage immersif.</span><span class="sxs-lookup"><span data-stu-id="8f8ad-112">When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide.</span></span> <span data-ttu-id="8f8ad-113">Les instructions relatives à la configuration des entrées dans Unity sont détaillées dans les [gestes et les contrôleurs de mouvement](gestures-and-motion-controllers-in-unity.md), ainsi qu’avec un [bouton complet et une table de mappage d’axe](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) pour référence.</span><span class="sxs-lookup"><span data-stu-id="8f8ad-113">Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f8ad-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f8ad-114">See also</span></span>
* [<span data-ttu-id="8f8ad-115">Mise à jour pour SteamVR</span><span class="sxs-lookup"><span data-stu-id="8f8ad-115">Updating for SteamVR</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)