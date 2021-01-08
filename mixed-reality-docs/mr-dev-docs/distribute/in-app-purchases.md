---
title: Achats dans l'application
description: Apprenez à utiliser des achats dans l’application dans vos applications de réalité mixte avec des vues XAML 2D et une fenêtre contextuelle du système d’exploitation Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: achats dans l’application, hololens, XAML, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: a87cc68f67def1d46a3a6ba352e723d356f51fa2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008669"
---
# <a name="in-app-purchases"></a>Achats dans l'application

Les achats dans l’application sont pris en charge dans HoloLens, mais il existe un certain travail pour les configurer.

Pour utiliser la fonctionnalité dans l’achat d’applications, vous devez :
* Créer une [vue 2D](../design/app-views.md) XAML pour qu’elle apparaisse en tant que ardoise
* Basculez vers celui-ci pour activer le placement, ce qui laisse la vue immersive
* Appeler l’API : await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Cette API affiche la fenêtre contextuelle du système d’exploitation Windows qui affiche le nom, la description et le prix de l’achat dans l’application. L’utilisateur peut ensuite choisir des options d’achat. Une fois l’action terminée, l’application doit présenter l’interface utilisateur, ce qui permet à l’utilisateur de revenir à sa [vue immersive](../design/app-views.md).

Pour les applications ciblant des casques immersifs de la réalité Windows mixte basés sur le bureau, il n’est pas nécessaire de basculer manuellement vers une vue XAML avant d’appeler l’API RequestProductPurchaseAsync.
