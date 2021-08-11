---
title: Entrée vocale en non réel
description: découvrez comment configurer et utiliser les entrées vocales, les mappages vocaux et la reconnaissance dans des applications de réalité mixte non réelles pour les appareils HoloLens 2.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, le moteur UE4, les HoloLens 2, les voix, les entrées vocales, la reconnaissance vocale, la réalité mixte, le développement, les fonctionnalités, la documentation, les guides, les hologrammes, le développement de jeux, le casque de réalité mixte, le casque de realisation de réalité Windows, le casque de réalité virtuelle
ms.openlocfilehash: 12d0c595b5319da50e119f4a2463e2ca3e07ce449f11d6fd266c5f988d180465
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221004"
---
# <a name="voice-input-in-unreal"></a>Entrée vocale en non réel

Les entrées vocales en temps réel vous permettent d’interagir avec un hologramme sans avoir à utiliser des mouvements manuels et n’est pris en charge que HoloLens 2. l’entrée vocale sur HoloLens 2 est alimentée par le même moteur qui prend en charge la reconnaissance vocale dans toutes les autres applications universelles Windows, mais inréelles utilise un moteur plus limité pour traiter l’entrée vocale. Cela limite les fonctionnalités d’entrée vocale dans les mappages de reconnaissance vocale prédéfinis, qui sont traités dans les sections suivantes. 

## <a name="enabling-speech-recognition"></a>Activation de la reconnaissance vocale

si vous utilisez Windows Mixed Reality plug-in, l’entrée vocale ne nécessite aucune api de Windows Mixed Reality spéciale ; Il repose sur l’API existante de mappage [d’entrée](https://docs.unrealengine.com/Gameplay/Input/index.html) de moteur non réel. Si vous utilisez OpenXR, vous devez également installer le [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal). 

Pour activer la reconnaissance vocale sur HoloLens :
1. sélectionnez **Project Paramètres > > HoloLens fonctionnalités >** et activer le **Microphone**. 
2. activez la reconnaissance vocale dans **Paramètres > confidentialité > discours** et sélectionnez **anglais**.

> [!NOTE]
> la reconnaissance vocale fonctionne toujours dans le Windows langue d’affichage configurée dans l’application **Paramètres** . Il est recommandé d’activer également la **reconnaissance vocale en ligne** pour une qualité de service optimale.

![Windows Paramètres de reconnaissance vocale](images/unreal/speech-recognition-settings.png)

3. Une boîte de dialogue s’affiche lorsque l’application commence par vous demander si vous souhaitez activer le microphone. Si vous sélectionnez **Oui** , l’entrée vocale démarre dans l’application.

## <a name="adding-speech-mappings"></a>Ajout de mappages vocaux

La connexion vocale à l’action est une étape importante lors de l’utilisation de l’entrée vocale. Ces mappages surveillent l’application pour les mots clés vocaux qu’un utilisateur peut prononcer, puis déclenchent une action liée. Vous pouvez trouver des mappages de reconnaissance vocale en procédant comme suit :
1. sélectionnez **modifier > Project Paramètres**, en faisant défiler jusqu’à la section **moteur** , puis en cliquant sur **entrée**.

Pour ajouter un nouveau mappage de reconnaissance vocale pour une commande de saut :
1. Sélectionnez l' **+** icône en regard d' **éléments de tableau** et remplissez les valeurs suivantes :
    * **jumpWord** pour le nom de l' **action**
    * **raccourci** pour le **mot clé Speech**

> [!NOTE]
> Vous pouvez utiliser n’importe quel mot ou phrase (s) en anglais comme mot clé. 

![Paramètres d’entrée du moteur UE4](images/unreal/engine-input.png)

Les mappages vocaux peuvent être utilisés en tant que composants d’entrée comme les mappages d’action ou d’axe ou en tant que nœuds de plan dans l’événement Graph. Par exemple, vous pouvez lier la commande Jump pour imprimer deux journaux différents selon le moment où le mot est parlé :

1. Double-cliquez sur un plan pour l’ouvrir dans le **Graph d’événements**.
2. **Cliquez avec le bouton droit** et recherchez le **nom d’action** de votre mappage de reconnaissance vocale (dans le cas présent **jumpWord**), puis appuyez sur **entrée** pour ajouter un nœud **d’action d’entrée** au graphique.
3. Faites glisser et déposez le code PIN **appuyé** pour imprimer le nœud de **chaîne** comme indiqué dans l’image ci-dessous. Vous pouvez faire en sorte que le code confidentiel **libéré** soit vide. il n’exécutera rien pour les mappages vocaux.
 
![Action simple pour la voix](images/unreal/voice-input-img-03.png)

4. Lisez l’application, disons le mot **Jump** et regardez la console pour imprimer les journaux !

c’est tout ce dont vous avez besoin pour commencer à ajouter des entrées vocales à vos applications de HoloLens en toute situation. Vous trouverez plus d’informations sur la reconnaissance vocale et l’interactivité dans les liens ci-dessous, et veillez à réfléchir à l’expérience que vous créez pour vos utilisateurs.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement inréel que nous avons mis à disposition, vous êtes ensuite en train d’explorer les fonctionnalités de la plateforme de réalité mixte et les API : 

> [!div class="nextstepaction"]
> [Caméra HoloLens](unreal-hololens-camera.md)

Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Entrée vocale](../../design/voice-input.md)
* [Pointer et valider](../../design/gaze-and-commit.md)
* [Interactions instinctuelles](../../design/interaction-fundamentals.md)

