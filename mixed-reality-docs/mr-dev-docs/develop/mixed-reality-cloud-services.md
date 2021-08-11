---
layout: LandingPage
title: Vue d’ensemble des services cloud de réalité mixte Azure
description: Découvrez tous les services cloud de réalité mixte Azure que vous pouvez intégrer dans vos applications Unity ou Unreal.
author: hferrone
ms.author: v-haferr
ms.date: 12/9/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Réalité mixte, développer, développement, HoloLens, services cloud, Azure, rendu à distance, ancres spatiales, cognitive services, cognition, unity, machine learning, traduction vocale, vision par ordinateur, Microsoft Graph
ms.openlocfilehash: ac4ce3d1bef426682450da69e9c8ffcd9e317e2a7853365e1af082a1913e1ecc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189027"
---
# <a name="azure-mixed-reality-cloud-services-overview"></a>Vue d’ensemble des services cloud de réalité mixte Azure

![ Image Azure Spatial Anchors](../design/images/AzureSpatialAnchors.jpg)

Révélez ce en quoi chaque humain est expert, le monde physique tridimensionnel dans lequel nous vivons, avec les services de réalité mixte Azure. Aidez les gens à créer, à apprendre et à collaborer plus efficacement en capturant et en exposant des informations numériques dans le contexte de leur travail et de leur monde. Introduisez la 3D dans l’utilisation de vos appareils mobiles, casques et autres appareils non attachés. Tirez parti d’Azure afin d’aider à garantir la protection de vos informations les plus sensibles.

## <a name="mixed-reality-services"></a>Services de réalité mixée

Les services cloud de réalité mixte comme **Azure Remote Rendering** et **Azure Spatial Anchors** permettent aux développeurs de créer des expériences immersives attrayantes sur une variété de plateformes. Ces services vous permettent d’intégrer la reconnaissance spatiale à vos projets lorsque vous créez des applications pour la formation 3D, la maintenance prédictive de l’équipement et la révision de la conception, le tout dans le contexte des environnements de vos utilisateurs.

### <a name="azure-remote-rendering"></a>Azure Remote Rendering

[Azure Remote Rendering](/azure/remote-rendering/) (ARR) est un service qui vous permet de rendre des modèles 3D extrêmement complexes en temps réel et de les diffuser en continu sur un appareil. ARR est désormais en disponibilité générale, et peut être ajouté à vos projets Unity ou à vos projets natifs C++ qui ciblent HoloLens 2 ou un poste de travail Windows.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-Azure-Mixed-Reality-Services-Azure-Remote-Rendering/player]

ARR est un composant essentiel de toute application de réalité mixte qui s’exécute sur des appareils non attachés, car ils ont moins de puissance de rendu de calcul. Prenez la comparaison suivante de modèle de moteur en guise d’exemple : le modèle haute fidélité sur la gauche a plus de 18 millions de triangles, tandis que le modèle réduit sur la droite n’en a qu’environ 200 000. Dans les scénarios où chaque détail a son importance : gestion des installations industrielles, contrôle de la conception pour des biens tels que les moteurs de camion, planification de la chirurgie pré-opération, et ainsi de suite, la visualisation en 3D permet de faire vivre chacun de ces détails. C’est ce qui aide les concepteurs, les ingénieurs, les médecins et les étudiants à mieux comprendre des informations complexes et à prendre la bonne décision. Toutefois, cette simplification peut entraîner une perte de détails importants qui sont nécessaires dans les décisions métier et de conception clés.

![Exemple d’application Azure Remote Rendering dans Unity](images/arr-engine.png)

ARR résout ce problème en déplaçant la charge de travail de rendu vers des GPU haut de gamme dans le cloud. Un moteur graphique hébergé dans le cloud prend le relais et effectue le rendu de l’image, l’encode sous la forme d’un flux vidéo et diffuse le modèle directement sur l’appareil cible. 

* Pour les modèles complexes qui ne peuvent pas être gérés par un seul GPU haut de gamme, ARR distribue la charge de travail sur plusieurs GPU et fusionne le résultat en une image unique, un processus entièrement transparent pour l’utilisateur. 

En guise de bonus, ARR ne restreint pas le type d’interface utilisateur que vous pouvez utiliser dans votre application. À la fin d’un frame, votre contenu rendu localement est combiné automatiquement à l’image distante, comme illustré dans l’image ci-dessous :

![Exemple d’application Azure Remote Rendering dans Unity](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

[Azure Spatial Anchors](/azure/spatial-anchors/) (ASA) est un service multiplateforme qui vous permet de créer des applications de réalité mixte avec reconnaissance spatiale. Avec Azure Spatial Anchors, vous pouvez mapper, conserver et partager du contenu holographique sur plusieurs appareils à l’échelle du monde réel. AOA étant désormais en préversion publique, vous pouvez l’essayer dans vos applications.

Azure Spatial Anchors est une solution personnalisée unique pour les cas d’usage courants en réalité mixte, notamment :
* **Orientation** : où deux ancres spatiales (ou plus) peuvent être connectées afin de créer une liste de tâches ou des points d’intérêt avec lesquels un utilisateur doit interagir.
* **Expériences multi-utilisateur** : où les utilisateurs peuvent transmettre des déplacements en interagissant avec des objets dans le même espace virtuel.
* **Persistance du contenu virtuel dans le monde réel** : où les utilisateurs peuvent placer des objets virtuels dans le monde réel, qui sont visibles à partir d’autres appareils pris en charge.

![Exemple Azure Spatial Anchors](images/persistence.gif)

Le service peut être développé dans un hôte d’environnements et être déployé sur un grand groupe d’appareils et de plateformes. Cela leur donne une dispense spéciale pour leur propre liste de plateformes disponibles :
* Unity pour HoloLens
* Unity pour iOS
* Unity pour Android
* iOS natif
* Android natif
* C++/WinRT et DirectX pour HoloLens
* Xamarin pour iOS
* Xamarin pour Android

### <a name="azure-object-anchors"></a>Azure Object Anchors

[Azure Object Anchors](/azure/object-anchors/) (AOA) est un service de réalité mixte qui vous permet de créer des expériences riches et immersives en alignant automatiquement du contenu 3D sur des objets physiques. Vous bénéficiez d’une compréhension contextuelle des objets sans avoir besoin de marqueurs ou d’alignement manuel. En créant des applications de réalité mixte avec Object Anchors, vous pouvez réaliser des économies importantes en termes de travail manuel, réduire les erreurs d’alignement et améliorer l’expérience utilisateur.

Azure Object Anchors est particulièrement adapté aux cas d’utilisation courants de la réalité mixte, notamment :
* **Formation** : créez des expériences de formation mixte pour vos employés, sans avoir à placer de marqueurs ou passer du temps à ajuster manuellement l’alignement des hologrammes.
* **Aide relative aux tâches** : la réalité mixte peut simplifier considérablement le guidage des employés dans un ensemble de tâches.
* **Recherche de ressources** : si vous disposez déjà d’un modèle 3D d’un objet dans votre espace physique, Azure Object Anchors peut vous aider à localiser et à suivre les instances de cet objet dans votre environnement physique.

![Superposition virtuelle d’ancres d’objets Azure sur un moteur de voiture ouvert](images/aoa-img-01.png)

## <a name="cognitive-services"></a>Cognitive Services

:::row:::
    :::column:::
       [![Voix](../whats-new/images/speech.jpg)](/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Speech](/azure/cognitive-services/speech-service/)
        Découvrez comment Speech permet l’intégration de fonctionnalités de traitement vocal dans n’importe quelle application ou service. Convertit la langue parlée en texte ou produit une parole naturelle à partir de texte à l’aide de polices de la voix standard (ou personnalisables). Essayez gratuitement n’importe quel service et créez rapidement des applications et des services compatibles avec la reconnaissance vocale avec les fonctionnalités suivantes.
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![Vision](../whats-new/images/vision.jpg)](/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Vision](/azure/cognitive-services/computer-vision/)
        Reconnaissez, identifiez, légendez, indexez et modérez vos images, vidéos et contenus d’encre numérique. Découvrez comment Vision permet aux applications et aux services d’identifier et d’analyser avec précision le contenu des images, des vidéos et de l’encre numérique.
    :::column-end:::
:::row-end:::


## <a name="standalone-unity-services"></a>Services Unity autonomes

Les services autonomes listés ci-dessous ne s’appliquent pas à la réalité mixte, mais peuvent être utiles dans un large éventail de contextes de développement. Si vous développez des applications dans Unity, chacun de ces services peut être intégré à vos projets nouveaux ou existants.

### <a name="device-support"></a>Prise en charge des appareils
<table>
    <tr>
        <td><strong>Service cloud Azure</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></td>
    </tr>
     <tr>
        <td><a href="unity/tutorials/mr-azure-301.md">Traduction</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302.md">Vision par ordinateur</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302b.md">Vision personnalisée</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-303.md">Notifications inter-appareils</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-304.md">Reconnaissance faciale</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-305.md">Fonctions et stockage</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-306.md">Streaming de vidéos</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-307.md">Apprentissage machine</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-308.md"mr-azure-308.md">Fonctions et stockage</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-309.md">Application Insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-310.md">Détection d’objets</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-312.md">Intégration de bots</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="see-also"></a>Voir aussi

* Tutoriels Azure Spatial Anchors pour HoloLens 2 – [Bien démarrer avec Azure Spatial Anchors (1 sur 3)](./unity/tutorials/mr-learning-asa-02.md)
* Tutoriels sur les services de reconnaissance vocale Azure pour HoloLens 2 - [Intégration et utilisation de la reconnaissance vocale et de la transcription (1 sur 4)](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)