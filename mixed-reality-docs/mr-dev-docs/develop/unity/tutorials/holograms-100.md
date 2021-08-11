---
title: HoloLens (1ère génération) - Bases 100 - Bien démarrer avec Unity
description: découvrez comment créer votre première application « hello world » de base de réalité mixte pour les appareils HoloLens et Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: en réalité mixte, Windows Mixed Reality, HoloLens, immersif, vr, mr, prise en main, hologramme, academy, didacticiel, académie de la réalité mixte, unity, casque de réalité mixte, casque Windows mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 518be5642304b6307f0b26f30f37315eba4164448493d928f6effb3027f7d611
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196501"
---
# <a name="hololens-1st-gen-basics-100-getting-started-with-unity"></a>HoloLens (1re génération) notions de base 100 : prise en main d’unity

>[!IMPORTANT]
>les didacticiels d’académie de la réalité mixte ont été conçus avec des HoloLens (1er génération), unity 2017 et des casques immersifs immersifs de la réalité mixte à l’esprit.  Nous estimons qu’il est important de laisser ces tutoriels à la disposition des développeurs qui recherchent encore des conseils pour développer des applications sur ces appareils. ces didacticiels ne seront **_pas_** mis à jour avec les derniers ensembles d’outils ou interactions utilisés pour HoloLens 2 et peuvent ne pas être compatibles avec les versions plus récentes d’unity.  Ils sont fournis dans le but de fonctionner sur les appareils pris en charge. Une [nouvelle série de tutoriels](mrlearning-base.md) a été publiée pour HoloLens 2.

Ce didacticiel vous guide dans la création d’une application de réalité mixte de base créée avec Unity.

## <a name="device-support"></a>Prise en charge des appareils

<table>
<tr>
<th>Cours</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Casques immersifs</a></th>
</tr><tr>
<td>Réalité mixte - Principes fondamentaux - Cours 100 : Bien démarrer avec Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prérequis

* un PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md).

## <a name="chapter-1---create-a-new-project"></a>Chapitre 1-créer un Project

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Pour générer une application avec Unity, vous devez d’abord créer un projet. Ce projet est organisé en quelques dossiers, dont le plus important est votre dossier de ressources. il s’agit du dossier qui contient toutes les ressources que vous importez à partir d’outils de création de contenu numérique tels que Maya, Max Cinema 4d ou Photoshop, tout le code que vous créez avec Visual Studio ou votre éditeur de code favori, et tout autre fichier de contenu créé par unity lorsque vous composez des scènes, animations et autres types de ressources unity dans l’éditeur.

pour générer et déployer des applications UWP, unity peut exporter le projet en tant que solution de Visual Studio qui contient tous les fichiers de ressources et de code nécessaires.

1. Démarrer Unity
2. Sélectionnez **Nouveau**
3. Entrez un nom de projet (par exemple, « MixedRealityIntroduction »)
4. Entrez un emplacement pour enregistrer votre projet
5. Vérifier que le bouton bascule **3D** est sélectionné
6. Sélectionner **créer un projet**

Contentes, vous êtes prêt pour la prise en main de vos personnalisations de réalité mixte.

## <a name="chapter-2---setup-the-camera"></a>Chapitre 2-configurer l’appareil photo

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

La caméra principale Unity gère le suivi des têtes et le rendu stéréoscopique. Il y a quelques modifications à apporter à la caméra principale pour l’utiliser avec la réalité mixte.

1. Sélectionner un fichier > nouvelle scène

Tout d’abord, il sera plus facile de présenter votre application si vous imaginez la position de départ de l’utilisateur comme (**X**: 0, **Y**: 0, **Z**: 0). Étant donné que la caméra principale effectue le suivi du mouvement de la tête de l’utilisateur, la position de départ de l’utilisateur peut être définie en définissant la position de départ de l’appareil photo principal.

1. Sélectionner la **caméra principale** dans le volet de la **hiérarchie**
2. Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et remplacez la **position** (**x**: 0, **y**: 1, **z**:-10) par (**x**: 0, **y**: 0, **z**: 0)

Deuxièmement, l’arrière-plan de la caméra par défaut a besoin d’une pensée.

**pour les applications HoloLens**, le monde réel doit apparaître derrière tout ce que l’appareil photo rend, et non une texture Skybox.

1. Avec la **caméra principale** toujours sélectionnée dans le **panneau hiérarchie** , recherchez le composant **Camera** dans le panneau **inspecteur** et remplacez la liste déroulante **Clear Flags** de **skybox** par **couleur unie**.
2. Sélectionnez le sélecteur de couleur d' **arrière-plan** et modifiez les valeurs **RVBA** en (0, 0, 0, 0)

**Pour les applications de réalité mixte ciblant des casques immersifs**, nous pouvons utiliser la texture skybox par défaut fournie par Unity.

1. Avec la **caméra principale** toujours sélectionnée dans le panneau **hiérarchie** , recherchez le composant **Camera** dans le panneau **inspecteur** et conservez la liste déroulante **indicateurs clairs** pour **skybox**.

Troisièmement, examinons le plan near clip dans Unity et empêchez les objets d’être rendus trop près des yeux des utilisateurs, car un utilisateur approche un objet ou un objet s’approche d’un utilisateur.

**pour les applications HoloLens**, le plan near clip peut être défini sur la [HoloLens mètres recommandés](../camera-in-unity.md#using-clipping-planes) 0,85.

1. avec la **caméra principale** toujours sélectionnée dans le **panneau hiérarchie** , recherchez le **composant camera** dans le panneau **inspecteur** , puis remplacez le champ du **plan Near Clip** par la valeur par défaut **0,3** par le HoloLens **0,85** recommandé.

**Pour les applications de réalité mixte ciblant des casques immersifs**, nous pouvons utiliser le paramètre par défaut fourni par Unity.

1. Avec la **caméra principale** toujours sélectionnée dans le panneau **hiérarchie** , recherchez le composant **Camera** dans le panneau **inspecteur** , puis conservez le champ du **plan near clip** à la valeur par défaut **0,3**.

Enfin, laissez-nous enregistrer notre progression jusqu’à présent. Pour enregistrer les modifications de la scène, sélectionnez **fichier > enregistrer la scène sous**, nommez la scène **main**, puis sélectionnez **Enregistrer**.

## <a name="chapter-3---setup-the-project-settings"></a>chapitre 3 : configurer le Project Paramètres

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

dans ce chapitre, nous allons définir des paramètres de projet unity qui nous aident à cibler le kit de développement logiciel (SDK) Windows holographique pour le développement. Nous allons également définir des paramètres de qualité pour notre application. enfin, nous nous assurons que nos cibles de génération sont définies sur plateforme Windows universelle.

### <a name="unity-performance-and-quality-settings"></a>Paramètres de performance et de qualité Unity

**Paramètres de qualité Unity pour HoloLens**

![Paramètres de qualité Unity pour HoloLens](images/qualitysettings.png)

étant donné que la gestion de la fréquence élevée sur les HoloLens est si importante, nous souhaitons que les paramètres de qualité soient réglés pour des performances plus rapides. Pour plus d’informations sur les performances, sur [les recommandations en matière de performances pour Unity](../performance-recommendations-for-unity.md).

1. sélectionnez **modifier > Project Paramètres > qualité**
2. sélectionnez la **liste déroulante** sous le logo de **plateforme Windows universelle** et sélectionnez **très faible**. Vous savez que le paramètre est correctement appliqué lorsque la zone dans la colonne Plateforme Windows universelle et la ligne **Très faible** est verte.

**Pour les applications de réalité mixte ciblant bloqués**, vous pouvez conserver les valeurs par défaut des paramètres de qualité.

### <a name="target-windows-10-sdk"></a>kit de développement logiciel (SDK) Windows 10 cible

**kit de développement logiciel (SDK) holographique Target Windows**

![kit de développement logiciel (SDK) holographique Target Windows](../images/xrsettings.png)

Nous devons permettre à Unity de savoir que l’application que nous essayons d’exporter doit créer une [vue immersive](../../../design/app-views.md) au lieu d’une vue 2D. pour ce faire, nous allons activer la prise en charge de la réalité virtuelle sur unity ciblant le kit de développement logiciel Windows 10.

1. accédez à **modifier > Project Paramètres > Player**.
2. dans le **panneau** de l’inspecteur pour Paramètres de lecteur, sélectionnez l’icône **plateforme Windows universelle** .
3. Développez le groupe **XR Settings**.
4. Dans la section **Rendering** (Rendu), cochez la case **Virtual Reality Supported** (Réalité virtuelle prise en charge) pour ajouter une nouvelle liste **Virtual Reality SDKs** (SDK de réalité virtuelle).
5. Vérifiez que **Windows Mixed Reality** apparaît dans la liste. Dans le cas contraire, sélectionnez le bouton **+** en bas de la liste et choisissez **Windows Mixed Reality**.

>[!NOTE]
>si vous ne voyez pas l’icône **plateforme Windows universelle** , vérifiez que vous avez sélectionné plateforme Windows universelle prise en charge de la génération pendant l’installation. Si ce n’est pas le cas, vous devrez peut-être réinstaller Unity avec l’installation de Windows appropriée.

Travail étonnant d’obtenir tous les paramètres de projet appliqués. Nous allons ensuite ajouter un hologramme !

## <a name="chapter-4---create-a-cube"></a>Chapitre 4-créer un cube

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

La création d’un cube dans votre projet Unity est identique à la création d’un autre objet dans Unity. Le fait de placer un cube devant l’utilisateur est simple, car le système de coordonnées de Unity est mis en correspondance avec le monde réel, où un compteur dans Unity est approximativement un compteur dans le monde réel.

1. Dans le coin supérieur gauche du panneau de **hiérarchie** , sélectionnez la liste déroulante **créer** , puis choisissez **objet 3D > cube**.
2. Sélectionner le **cube** nouvellement créé dans le volet de **hiérarchie**
3. Dans l' **inspecteur** , recherchez le composant **transformer** et changez **position** en (**X**: 0, **Y**: 0, **Z**: 2). *Cela positionne le cube 2 mètres devant la position de départ de l’utilisateur.*
4. Dans le composant **transformer** , remplacez **rotation** par (**x**: 45, **Y**: 45, **z**: 45) et remplacez **adapter** par (**x**: 0,25, **y**: 0,25, **z**: 0,25). *Le cube est mis à l’échelle sur 0,25 mètres.*
5. Pour enregistrer les modifications de la scène, sélectionnez **fichier > enregistrer la scène**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Chapitre 5-vérification sur l’appareil à partir de l’éditeur Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Maintenant que nous avons créé notre cube, il est temps d’effectuer une vérification rapide de l’appareil. Vous pouvez le faire directement à partir de l’éditeur Unity.

### <a name="initial-setup"></a>Configuration initiale

1. sur votre PC de développement, dans unity, ouvrez le **fichier >** la fenêtre de Paramètres de Build.
2. remplacez **platform** par **plateforme Windows universelle** , puis cliquez sur **Switch platform** .

### <a name="for-hololens-use-unity-remoting"></a>pour HoloLens utiliser la communication à distance unity

1. sur votre HoloLens, installez et exécutez le [lecteur de communication à distance holographique](../../platform-capabilities-and-apis/holographic-remoting-player.md), disponible dans le Windows Store. Lancez l’application sur l’appareil. elle entrera en état d’attente et affichera l’adresse IP de l’appareil. Notez l’adresse IP.
2. Ouvrez **windows > XR > émulation holographique**.
3. Remplacez le **mode** d’émulation **aucun** par **distant par appareil**.
4. dans **ordinateur distant**, entrez l’adresse IP de votre HoloLens notée plus haut.
5. Cliquez sur **Connexion**.
6. Vérifiez que l’état de la **connexion** devient vert **connecté**.
7. Vous pouvez maintenant cliquer sur **lire** dans l’éditeur Unity.

Vous pouvez maintenant voir le cube dans l’appareil et dans l’éditeur. Vous pouvez suspendre, inspecter des objets et effectuer un débogage comme s’il s’agissait d’une application dans l’éditeur, car c’est essentiellement ce qui se passe, mais avec les données vidéo, audio et d’appareil transmises sur le réseau entre l’ordinateur hôte et l’appareil.

### <a name="for-other-mixed-reality-supported-headsets"></a>Pour les autres casques pris en charge par la réalité mixte

1. Connecter le casque sur votre PC de développement à l’aide du câble USB et du câble HDMI ou display port.
2. Lancez le **portail de réalité mixte** et assurez-vous que vous avez effectué la première expérience d’exécution.
3. À partir de Unity, vous pouvez maintenant appuyer sur le bouton de lecture.

Vous pouvez maintenant voir le rendu du cube dans votre casque de réalité mixte et dans l’éditeur.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Chapitre 6 : générer et déployer sur un appareil à partir de Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

nous sommes maintenant prêts à compiler notre projet pour Visual Studio et le déployer sur notre appareil cible.

### <a name="export-to-the-visual-studio-solution"></a>exporter vers la solution Visual Studio

1. ouvrez le **fichier >** la fenêtre de Paramètres de Build.
1. Cliquez sur **Ajouter des scènes ouvertes** pour ajouter la scène.
1. remplacez **platform** par **plateforme Windows universelle** , puis cliquez sur **Switch platform**.
1. dans **plateforme Windows universelle** paramètres, assurez-vous que le **kit SDK** est **Universal 10**.
1. Pour appareil cible, laissez **un appareil** pour bloqués afficher ou basculer vers **HoloLens**.
1. Le **type de build UWP** doit être **D3D**.
1. Le **Kit de développement logiciel (SDK) UWP** peut être laissé sur le **dernier installé**.
1. Cliquez sur **Générer**.
1. Dans l’Explorateur de fichiers, cliquez sur **nouveau dossier** et nommez le dossier **« app »**.
1. Après avoir sélectionné le dossier de l' **application** , cliquez sur le bouton **Sélectionner un dossier** .
1. une fois la création d’unity terminée, une fenêtre d’explorateur de fichiers Windows s’affiche.
1. Ouvrez le dossier de l' **application** dans l’Explorateur de fichiers.
1. ouvrez la solution de Visual Studio générée (MixedRealityIntroduction. sln dans cet exemple).

### <a name="compile-the-visual-studio-solution"></a>compiler la solution Visual Studio

enfin, nous allons compiler la solution Visual Studio exportée, la déployer et l’essayer sur l’appareil.

1. à l’aide de la barre d’outils supérieure de Visual Studio, remplacez la cible **Debug** par **Release** et de **ARM** par **X86**.

Les instructions diffèrent pour le déploiement sur un appareil et sur l’émulateur. Suivez les instructions qui correspondent à votre configuration.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Déployer sur un appareil de réalité mixte sur Wi-Fi

1. Cliquez sur la flèche en regard du bouton **ordinateur local** , puis remplacez la cible de déploiement par **ordinateur distant**.
2. entrez l’adresse IP de votre appareil de réalité mixte et changez le **Mode d’authentification** en protocole universel (protocole non chiffré) pour HoloLens et **Windows** pour d’autres appareils.
3. Cliquez sur **Déboguer > exécuter sans débogage**.

**par HoloLens**, s’il s’agit de la première fois que vous déployez sur votre appareil, vous devez effectuer un jumelage [à l’aide de Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Déployer sur un appareil de réalité mixte sur USB

Assurez-vous que l’appareil est branché via le câble USB.

1. **pour HoloLens**, cliquez sur la flèche en regard du bouton **ordinateur Local** , puis remplacez la cible de déploiement par **appareil**.
2. **Pour cibler des appareils bloqués connectés à votre PC**, conservez le paramètre sur la machine locale. Assurez-vous que le portail de la **réalité mixte** est en cours d’exécution.
3. Cliquez sur **Déboguer > exécuter sans débogage**.

### <a name="deploy-to-emulator"></a>Déployer sur Emulator

1. cliquez sur la flèche en regard du bouton **périphérique** , puis dans la liste déroulante, sélectionnez **HoloLens Emulator**.
2. Cliquez sur **Déboguer > exécuter sans débogage**.

### <a name="try-out-your-app"></a>Essayer votre application

Maintenant que votre application est déployée, essayez de déplacer tout autour du cube et observez qu’il reste dans le monde.

## <a name="see-also"></a>Voir aussi

* [Vue d’ensemble du développement Unity](../unity-development-overview.md)
* [Bonnes pratiques sur l’utilisation d’Unity et de Visual Studio](../best-practices-for-working-with-unity-and-visual-studio.md)
* [Réalité mixte - Principes fondamentaux - Cours 101](holograms-101.md)
* [Réalité mixte - Principes fondamentaux - Cours 101E](holograms-101e.md)