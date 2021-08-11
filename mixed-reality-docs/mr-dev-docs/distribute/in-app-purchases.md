---
title: Achats dans l'application
description: apprenez à utiliser des achats dans l’application dans vos applications de réalité mixte avec des vues XAML 2d et une fenêtre contextuelle d’inventaire Windows OS.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: achats dans l’application, hololens, XAML, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: fbb957d1044a5c76c19691b875de8f9513bfc4b49bc4cb0dbb98d045d615f1a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196147"
---
# <a name="in-app-purchases"></a>Achats dans l'application

les achats dans l’application sont pris en charge dans HoloLens, mais il existe un certain travail pour les configurer.

Pour utiliser la fonctionnalité dans l’achat d’applications, vous devez :
* Créer une [vue 2D](../design/app-views.md) XAML pour qu’elle apparaisse en tant que ardoise
* Basculez vers celui-ci pour activer le placement, ce qui laisse la vue immersive
* Appeler l’API : await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

cette API permet d’afficher la fenêtre contextuelle stock Windows OS qui affiche le nom, la description et le prix de l’achat dans l’application. L’utilisateur peut ensuite choisir des options d’achat. Une fois l’action terminée, l’application doit présenter l’interface utilisateur, ce qui permet à l’utilisateur de revenir à sa [vue immersive](../design/app-views.md).

pour les applications ciblant Windows Mixed Reality des casques immersifs basés sur le bureau, il n’est pas nécessaire de basculer manuellement vers une vue XAML avant d’appeler l’API RequestProductPurchaseAsync.