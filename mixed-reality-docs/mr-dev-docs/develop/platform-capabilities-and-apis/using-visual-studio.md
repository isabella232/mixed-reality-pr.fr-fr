---
title: Utilisation de Visual Studio pour le déploiement et le débogage
description: Découvrez comment créer, déboguer et déployer des applications pour HoloLens et Windows Mixed Reality avec Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, déboguer, déployer
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "100496090"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Utilisation de Visual Studio pour le déploiement et le débogage

Que vous utilisiez DirectX ou Unity pour développer votre application de réalité mixte, Visual Studio est votre outil de prédilection pour la déboguer et la déployer. Dans cette section, vous allez découvrir comment :
* Déployer des applications sur votre HoloLens ou un casque immersif Windows Mixed Reality à l’aide de Visual Studio.
* Utiliser l’émulateur HoloLens intégré à Visual Studio.
* Déboguer des applications de réalité mixte.

## <a name="prerequisites"></a>Prérequis

1. Consultez [Installer les outils](../../develop/install-the-tools.md#installation-checklist) pour obtenir des instructions d’installation.
2. Créez un projet d’application Windows universelle dans Visual Studio.  Pour HoloLens (1re génération), utilisez Visual Studio 2017 ou une version plus récente.  Pour HoloLens 2, utilisez Visual Studio 2019 16.2 ou ultérieur. Les langages C# et C++ sont pris en charge. (Ou suivez les instructions pour [créer une application dans Unity](../../develop/unity/tutorials/holograms-100.md).)

## <a name="enabling-developer-mode"></a>Activation du mode développeur

Commencez par activer le **mode développeur** sur votre appareil afin que Visual Studio puisse s’y connecter.

### <a name="hololens"></a>HoloLens

1. Mettez HoloLens sous tension et allumez l’appareil.
2. Utilisez le [mouvement associé au menu Démarrer](../../design/system-gesture.md) pour lancer le menu principal.
3. Sélectionnez la vignette **Settings** pour lancer l’application dans votre environnement.
4. Sélectionnez l’élément de menu **Mettre à jour**.
5. Sélectionnez l’élément de menu **Pour les développeurs**.
6. Activez le **Mode développeur** pour déployer des applications à partir de Visual Studio sur votre HoloLens.
7. Facultatif : Faites défiler et activez également **Portail d’appareil**, ce qui vous permet de vous connecter au [Portail d’appareil Windows](using-the-windows-device-portal.md) sur votre HoloLens à partir d’un navigateur web.

### <a name="windows-pc"></a>PC Windows

Si vous travaillez avec un casque Windows Mixed Reality connecté à votre PC, vous devez activer le **Mode développeur** sur ce PC.
1. Accédez à **Paramètres**
2. Sélectionnez **Mise à jour et sécurité**
3. Sélectionnez **Pour les développeurs**
4. Activez le **Mode développeur**, lisez la clause d’exclusion de responsabilité pour le paramètre que vous avez choisi, puis sélectionnez Oui pour accepter la modification.

## <a name="deploying-a-hololens-app-over-wi-fi"></a>Déploiement d’une application HoloLens via une connexion Wi-Fi 

Configurez votre projet Visual Studio avec les propriétés suivantes :

1. Sélectionner vos options de compilation d’applications
    * Pour les projets Unity, choisissez **Release** ou **Master** 
    * Pour tous les autres projets, choisissez **Release**

> [!NOTE]
> Vous trouverez les définitions complètes de chaque option de compilation dans [Exportation et génération de solutions Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).

2. Sélectionner votre configuration de build en fonction de votre appareil

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Sélectionnez **Machine distante** dans le menu déroulant de la cible de déploiement

![Cible de déploiement de machine distante dans Visual Studio](images/remotemachinesetting_arm64.png)

Ensuite, vous devez définir votre connexion à distance. Pour les projets C++ et JavaScript, accédez à **Projet > Propriétés > Propriétés de configuration > Débogage**. Si vous travaillez sur un projet C#, une boîte de dialogue doit s’afficher automatiquement.

> [!NOTE]
> Si la boîte de dialogue de connexion distante n’apparaît pas dans votre projet C#, vous pouvez l’ouvrir manuellement à partir de **Propriétés > Déboguer**.

1. Entrez l’adresse IP de votre appareil dans le champ **Adresse** ou **Nom de la machine**. 
    * Vous pouvez rechercher l’adresse IP sur votre HoloLens sous **Paramètres > Réseau et Internet > Options avancées**.
    * Nous recommandons toujours d’entrer manuellement votre adresse IP plutôt que de dépendre de la fonctionnalité Détection automatique.

2. Définissez le **Mode d’authentification** sur **Universel (protocole non chiffré)**

  ![Boîte de dialogue Connexion à distance dans Visual Studio](images/remotedeploy.png)

3. Créer, déployer et déboguer votre application en fonction de vos besoins
    * Sélectionnez **Déboguer > Démarrer le débogage** pour déployer votre application et commencer le débogage
    * Sélectionnez **Générer > Déployer** pour générer et déployer sans déboguer

![Démarrer sans débogage dans Visual Studio](images/deploywithdebugging.png)

4. La première fois que vous déployez une application sur votre HoloLens à partir de votre PC, vous êtes invité à entrer un code PIN. Suivez les instructions de la section **Appairer votre appareil**, plus loin dans cet article.

## <a name="deploying-a-hololens-app-over-usb"></a>Déploiement d’une application HoloLens via une connexion USB 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. Sélectionner vos options de compilation d’applications
    * Pour les projets Unity, choisissez **Release** ou **Master** 
    * Pour tous les autres projets, choisissez **Release**

> [!NOTE]
> Vous trouverez les définitions complètes de chaque option de compilation dans [Exportation et génération de solutions Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).

2. Sélectionner votre configuration de build en fonction de votre appareil

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Sélectionnez **Appareil** dans le menu déroulant de la cible de déploiement

![Déploiement d’appareils dans Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. Créer, déployer et déboguer votre application en fonction de vos besoins
    * Sélectionnez **Déboguer > Démarrer le débogage** pour déployer votre application et commencer le débogage
    * Sélectionnez **Générer > Déployer** pour générer et déployer sans déboguer

![Démarrer sans débogage dans Visual Studio](images/deploywithdebugging.png)</br>

5. La première fois que vous déployez une application sur votre HoloLens à partir de votre PC, vous êtes invité à entrer un code PIN. Suivez les instructions de la section **Appairer votre appareil**, plus loin dans cet article.

> [!NOTE]
> Si vous constatez beaucoup de temps d’attente lors du déploiement de vos applications via une connexion USB, nous vous recommandons d’utiliser les [instructions sur la connexion à distance](#deploying-a-hololens-app-over-wi-fi) dans la section précédente.

## <a name="deploying-an-app-to-the-hololens-emulator"></a>Déploiement d’une application sur l’émulateur HoloLens

1. Assurez-vous d’avoir **[installé l’émulateur HoloLens 2 ou HoloLens (1ère génération)](../install-the-tools.md#installation-checklist)**
2. Sélectionner votre configuration de build et l’émulateur en fonction de votre appareil

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Créer, déployer et déboguer votre application en fonction de vos besoins
    * Sélectionnez **Déboguer > Démarrer le débogage** pour déployer votre application et commencer le débogage
    * Sélectionnez **Générer > Déployer** pour générer et déployer sans déboguer

![Démarrer sans débogage dans Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a>Déploiement d’une application VR sur votre PC local 

Pour utiliser un casque immersif Windows Mixed Reality qui se connecte à votre PC ou au [simulateur Mixed Reality](using-the-windows-mixed-reality-simulator.md) :
1. Sélectionnez une configuration de build **x86** ou **x64** pour votre application
2. Sélectionnez **Machine locale** dans le menu déroulant de la cible de déploiement
3. Créer, déployer et déboguer votre application en fonction de vos besoins
    * Sélectionnez **Déboguer > Démarrer le débogage** pour déployer votre application et commencer le débogage
    * Sélectionnez **Générer > Déployer** pour générer et déployer sans déboguer

## <a name="pairing-your-device"></a>Appairage de votre appareil

La première fois que vous déployez une application sur votre HoloLens à partir de Visual Studio, vous êtes invité à entrer un code PIN. Sur votre HoloLens, générez un code PIN. Pour cela, lancez l’application Paramètres, accédez à **Mise à jour > Pour les développeurs**, puis appuyez sur **Coupler**. Tapez le code PIN qui apparaît sur votre HoloLens dans Visual Studio. Une fois l’appairage terminé, appuyez sur **Terminé** sur votre HoloLens pour fermer la boîte de dialogue. Ce PC étant maintenant appairé avec votre HoloLens, vous pouvez y déployer des applications automatiquement. Répétez ces étapes pour chaque PC utilisé pour déployer des applications sur votre HoloLens.

Pour découpler votre HoloLens de tous les ordinateurs appairés :
* Lancez l’application **Paramètres**, accédez à **Mise à jour > Pour les développeurs**, puis appuyez sur **Effacer**.

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Débogueur Graphics pour HoloLens (1re génération)

Les outils Graphics Diagnostics de Visual Studio sont utiles quand vous écrivez et optimisez une application holographique. Pour plus d’informations, consultez [Visual Studio Graphics Diagnostics sur MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics).

**Pour démarrer le débogueur Graphics**
1. Suivez les instructions données plus haut pour cibler un appareil ou un émulateur
2. Accédez à **Déboguer > Graphics > Démarrer les diagnostics**
3. La première fois que vous démarrez les diagnostics avec un HoloLens, vous pouvez obtenir une erreur « Accès refusé ». Redémarrez votre HoloLens pour que les autorisations mises à jour prennent effet, puis réessayez.

## <a name="profiling"></a>Profilage

Les outils de profilage dans Visual Studio vous permettent d’analyser l’utilisation des ressources et les performances de votre application. Ces outils comprennent des outils pour optimiser l’utilisation du processeur, de la mémoire, des graphiques et du réseau. Pour plus d’informations, consultez [Exécuter les outils de diagnostic sans débogage sur MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools).

**Pour démarrer les outils de profilage avec HoloLens**
1. Suivez les instructions données plus haut pour cibler un appareil ou un émulateur
2. Accédez à **Déboguer > Démarrer les outils de diagnostic sans débogage...**
3. Sélectionnez les outils que vous souhaitez utiliser
4. Sélectionnez **Démarrer**
5. La première fois que vous démarrez les diagnostics sans débogage avec un HoloLens, vous pouvez obtenir une erreur « Accès refusé ». Redémarrez votre HoloLens pour que les autorisations mises à jour prennent effet, puis réessayez.

## <a name="debugging-an-installed-or-running-app"></a>Débogage d’une application installée ou en cours d’exécution

Vous pouvez utiliser Visual Studio pour déboguer une application Windows universelle installée sans déploiement à partir d’un projet Visual Studio. Cela est utile si vous souhaitez déboguer un package d’application installé ou une application en cours d’exécution.
1. Accédez à **Déboguer -> Autres cibles de débogage -> Déboguer le package d’application installé**
2. Sélectionnez la cible **Machine distante** pour HoloLens ou **Machine locale** pour les casques immersifs
3. Entrez l’**adresse IP** de votre appareil
4. Choisissez le mode d’authentification **Universel**
5. La fenêtre affiche les applications en cours d’exécution et les applications inactives. Sélectionnez celle que vous voulez déboguer.
6. Choisissez le type de code à déboguer (managé, natif, mixte)
7. Sélectionnez **Attacher** ou **Démarrer**

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de points de contrôle de développement Unreal que nous avons élaboré, vous êtes actuellement au cœur de la phase de déploiement. À partir d’ici, vous pouvez passer au sujet suivant :

> [!div class="nextstepaction"]
> [Déploiement sur l’émulateur HoloLens](using-the-hololens-emulator.md)

Ou accéder directement à l’ajout de services avancés :

> [!div class="nextstepaction"]
> [Services avancés](../../develop/unity/unity-development-overview.md#5-adding-services)

Vous pouvez revenir aux [points de contrôle de développement Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Installer les outils](../install-the-tools.md)
* [Utilisation de l’émulateur HoloLens](using-the-hololens-emulator.md)
* [Déploiement et débogage d’applications de plateforme Windows universelle (UWP)](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [Activer votre appareil pour le développement](/windows/uwp/get-started/enable-your-device-for-development)