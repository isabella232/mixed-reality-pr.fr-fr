---
ms.openlocfilehash: c9ce068adc3b4b550ecaf1b1c106d9b12f363ac0
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443510"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

Si vous avez une application HoloLens, choisissez votre [option de distribution](../distribute-overview.md#distribution-options) préférée dans le tableau ci-dessous. Si vous publiez sur le Microsoft Store, vous avez la possibilité d’ajouter des [achats dans l’application](../in-app-purchases.md) pour monétiser votre contenu.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Si vous utilisez une application immersif qui cible un casque Windows Mixed Reality, créez un lanceur d’application 3D, puis choisissez votre [option de distribution](../distribute-overview.md#distribution-options) préférée dans le tableau ci-dessous. Si vous publiez sur le Microsoft Store, vous avez la possibilité d’ajouter des [achats dans l’application](../in-app-purchases.md) pour monétiser votre contenu.

### <a name="designing-3d-app-launchers-for-vr"></a>Conception des lanceurs d’applications 3D pour VR 

les lanceurs d’applications 3D apparaissent en tant qu’objets dans l’environnement d’hébergement Windows Mixed Reality qui s’affiche chaque fois qu’un utilisateur place sur un casque immersif. Ces objets sont les vôtres pour la création et la personnalisation, mais il est recommandé de commencer par notre article de [conseils de conception](../3d-app-launcher-design-guidance.md) pour obtenir le blocage de bonnes pratiques de conception, notamment la mise à l’échelle, le type, le choix de couleurs, la texturation et les autres éléments qui font partie de l’environnement virtuel.

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modélisation et exportation des lanceurs d’applications 3D

Une fois que vous avez défini l’idée de votre lanceur d’applications 3D, vous devez vous assurer qu’il répond aux exigences de Microsoft Store, y compris le format de fichier de ressources, le nombre de triangles, les tailles de texture, la longueur d’animation et l’optimisation des ressources. Ce processus peut être très technique. nous vous recommandons donc d’utiliser notre article de [création de modèle 3D](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) pour cocher toutes les cases. Les ressources qui ne répondent pas à cette spécification de création ne seront pas affichées dans la page d’hébergement de Windows Mixed Reality.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Ajout de lanceurs d’applications 3D dans vos applications

Une fois que vous avez vérifié que votre lanceur d’applications 3D répond aux instructions de création de Windows Mixed Reality, il peut être utilisé pour remplacer le lanceur 2D par défaut de votre application dans l’environnement d’hébergement Windows Mixed Reality. Le processus d’intégration d’un lanceur d’application 3D dans votre application dépend du type d’application que vous développez :

* [Applications UWP](../implementing-3d-app-launchers.md)
* [Applications Win32](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>Facultatif Placer des modèles 3D dans la page d’hébergement Windows Mixed Reality

En guise de bonus supplémentaire, certaines applications 2D vous permettent de placer des modèles 3D directement dans l’espace de réalité Windows mixed en tant que décorations ou pour une inspection supplémentaire en 3D complet. Le protocole Add Model vous permet d’envoyer un modèle 3D à partir de votre site Web ou de votre application vers la page d’hébergement Windows Mixed Reality, où il sera conservé comme les lanceurs d’applications 3D, les applications 2D et les hologrammes. Découvrez [Comment placer des modèles 3D dans la page d’hébergement Windows Mixed Reality](../enable-placement-of-3d-models-in-the-home.md) pour obtenir des détails supplémentaires et des instructions sur la façon d’animer vos propres applications.