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
# <a name="hp-reverb-g2-controllers-in-unity"></a>Contrôleurs de réverbération HP G2 dans Unity

## <a name="getting-started"></a>Prise en main

Aucune configuration supplémentaire n’est requise pour utiliser le contrôleur de réverbération HP G2 si vous développez pour SteamVR ou à l’aide de l’API d’entrée Windows Mixed Reality (XR. WSA. Entrée). Toutefois, les boutons A, B, X, Y et le déclencheur d’utilisation ne sont pas accessibles actuellement via le gestionnaire d’entrée, sauf si vous utilisez SteamVR. La prise en charge des entrées de réverbération G2 supplémentaires sera disponible prochainement. n’hésitez pas à vérifier.

## <a name="porting-existing-applications"></a>Portage d’applications existantes

Si vous disposez déjà d’une application existante que vous développez pour des casques immersifs de Windows Mixed Reality, consultez les sections [Guide de Portage](../porting-apps/porting-guides.md) et [paramètres du projet](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) pour obtenir des suggestions générales.

## <a name="mapping-input"></a>Entrée de mappage

Lorsque vous êtes prêt à faire fonctionner votre mappage d’entrée pour vos nouveaux contrôleurs, commencez par la section [mappage d’entrée](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) du Guide de Portage immersif. Les instructions relatives à la configuration des entrées dans Unity sont détaillées dans les [gestes et les contrôleurs de mouvement](gestures-and-motion-controllers-in-unity.md), ainsi qu’avec un [bouton complet et une table de mappage d’axe](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) pour référence.

## <a name="see-also"></a>Voir aussi
* [Mise à jour pour SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)