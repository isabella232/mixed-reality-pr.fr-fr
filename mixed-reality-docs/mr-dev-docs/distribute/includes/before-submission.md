---
ms.openlocfilehash: d811df7f0dbd7c44a5135ed82c9061e19c1335e3e23dda6398562317f7ee8861
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198782"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

si vous disposez d’une application HoloLens, choisissez votre [option de distribution](../distribute-overview.md#distribution-options) préférée dans le tableau ci-dessous. si vous publiez sur le Microsoft Store, vous avez la possibilité d’ajouter des [achats dans l’application](../in-app-purchases.md) pour monétiser votre contenu.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

si vous utilisez une application immersive qui cible un Windows Mixed Reality casque, créez un lanceur d’application 3d, puis choisissez votre option de [distribution](../distribute-overview.md#distribution-options) préférée dans le tableau ci-dessous. si vous publiez sur le Microsoft Store, vous avez la possibilité d’ajouter des [achats dans l’application](../in-app-purchases.md) pour monétiser votre contenu.

### <a name="designing-3d-app-launchers-for-vr"></a>Conception des lanceurs d’applications 3D pour VR 

les lanceurs d’applications 3d apparaissent en tant qu’objets dans le Windows Mixed Reality environnement d’hébergement qui apparaît chaque fois qu’un utilisateur place sur un casque immersif. Ces objets sont les vôtres pour la création et la personnalisation, mais il est recommandé de commencer par notre article de [conseils de conception](../3d-app-launcher-design-guidance.md) pour obtenir le blocage de bonnes pratiques de conception, notamment la mise à l’échelle, le type, le choix de couleurs, la texturation et les autres éléments qui font partie de l’environnement virtuel.

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modélisation et exportation des lanceurs d’applications 3D

une fois que vous avez défini l’idée de votre lanceur d’applications 3d, vous devez vous assurer qu’il répond aux exigences de Microsoft Store, y compris le format de fichier de ressources, le nombre de triangles, les tailles de texture, la longueur d’animation et l’optimisation des ressources. Ce processus peut être très technique. nous vous recommandons donc d’utiliser notre article de [création de modèle 3D](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) pour cocher toutes les cases. les ressources qui ne répondent pas à cette spécification de création ne sont pas rendues dans la Windows Mixed Reality page d’hébergement.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Ajout de lanceurs d’applications 3D dans vos applications

une fois que vous avez vérifié que votre lanceur d’applications 3d respecte les instructions de création de Windows Mixed Reality, il peut être utilisé pour remplacer le lanceur 2d par défaut de votre application dans le Windows Mixed Reality environnement d’hébergement. Le processus d’intégration d’un lanceur d’application 3D dans votre application dépend du type d’application que vous développez :

* [Applications UWP](../implementing-3d-app-launchers.md)
* [Applications Win32](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>Facultatif placement de modèles 3d dans le Windows Mixed Reality

en guise de bonus supplémentaire, certaines applications 2d vous permettent de placer des modèles 3d directement dans le Windows Mixed Reality origine comme décorations ou pour une inspection supplémentaire en 3d complet. le protocole add model vous permet d’envoyer un modèle 3d à partir de votre site web ou de votre application vers la page d’hébergement Windows Mixed Reality, où il sera conservé comme les lanceurs d’applications 3d, les applications 2d et les hologrammes. découvrez [comment placer des modèles 3d dans la Windows Mixed Reality page d’hébergement](../enable-placement-of-3d-models-in-the-home.md) pour trouver plus de détails et d’instructions sur la façon d’animer vos propres applications.