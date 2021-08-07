---
title: Test de votre application dans HoloLens
description: en savoir plus sur les conseils généraux et les suggestions relatives aux tests et à l’optimisation des performances de votre HoloLens applications de réalité mixte.
author: jonmlyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, test
ms.openlocfilehash: 2f423560191fea8b516db80d533898b5a1f15973442e7bb6cd8878d486e0ffba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212093"
---
# <a name="testing-your-app-on-hololens"></a>Test de votre application dans HoloLens

le test d’applications HoloLens est semblable au test d’applications Windows. Vous devez toujours tenir compte des fonctionnalités, de l’interopérabilité, des performances, de la sécurité, de la fiabilité, etc. Toutefois, certaines zones qui ne s’affichent pas dans les applications de téléphone ou de PC nécessitent un traitement spécial. Les applications holographiques doivent s’exécuter sans heurts dans un ensemble diversifié d’environnements. Ils doivent également conserver les performances et le confort de l’utilisateur à tout moment. Ce guide est ici pour vous aider à tester ces domaines.

## <a name="performance"></a>Performances

Les applications holographiques doivent s’exécuter sans heurts dans un ensemble diversifié d’environnements. Ils doivent également conserver les performances et le confort de l’utilisateur à tout moment. Les performances sont si importantes pour l’expérience de l’utilisateur avec une application holographique dans laquelle nous avons une rubrique entière consacrée. Veillez à lire et à suivre la [Description des performances pour la réalité mixte](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Test de 3D en 3D

1. **Testez votre application dans autant d’espaces que possible.** Essayez dans les grandes salles, les petites salles, les salles de bain, les cuisines, les chambres, les bureaux, etc. Prenez également en compte les chambres avec des fonctionnalités non standard, telles que les murs non verticaux, les murs incurvés et les limites non horizontales. Fonctionne-t-il bien lors de la transition entre des salles, des planchers, en passant par des couloirs ou des escaliers ?
2. **Testez votre application dans des conditions d’éclairage différentes.** Répond-il correctement à différentes conditions environnementales, telles que l’éclairage, les surfaces noires et les surfaces transparentes ou réfléchissantes comme les miroirs et les murs.
3. **Testez votre application dans différentes conditions de mouvement.** Mettez sur l’appareil et essayez vos scénarios dans différents États de mouvement. Répond-il correctement à un mouvement ou à un état stable différent ?
4. **Testez le fonctionnement de votre application à partir de différents angles.** Si vous avez un hologramme universel, que se passe-t-il si votre utilisateur s’en sert ? Que se passe-t-il si un élément est présent entre l’utilisateur et l’hologramme ? Que se passe-t-il si l’utilisateur regarde l’hologramme ci-dessus ou en dessous ?
5. **Utilisez des signaux spatial et audio.** Assurez-vous que votre application utilise des indications spatiales et audio pour empêcher l’utilisateur de se perdre.
6. **Testez votre application à différents niveaux de bruit ambiant.** Si vous avez implémenté des commandes vocales, essayez de les appeler avec différents niveaux de bruit ambiant.
7. **Testez votre application en place et debout**. Veillez à tester à partir des sièges et des positions debout.
8. **Testez votre application à partir de différentes distances**. Les éléments d’interface utilisateur peuvent-ils être lus et interagis à partir de loin ? Votre application réagit-elle aux utilisateurs qui se trouvent trop près de vos hologrammes ?
9. **Testez votre application en fonction des interactions courantes de la barre d’application**. Toutes les vignettes d’application et les applications universelles 2D ont une [barre d’application](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) qui vous permet de contrôler la position des applications dans le monde mixte. Assurez-vous que le fait de cliquer sur supprimer met fin au processus de l’application normalement et que le bouton précédent est pris en charge dans le contexte de votre application universelle 2D. Essayez de mettre à l’échelle et de déplacer votre application en [mode d’ajustement](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) , tant qu’elle est active et qu’il s’agit d’une vignette d’application interrompue.

### <a name="environmental-test-matrix"></a>Matrice de test environnemental

![matrice de Test de l’environnement pour le développement d’applications HoloLens](images/environment-matrix-600px.png)

## <a name="comfort"></a>Confort

1. **Plans de clip.** Soyez précis à l’endroit où [les hologrammes sont rendus](hologram-stability.md#hologram-render-distances).
2. **Évitez les mouvements virtuels incohérents avec le mouvement de la tête réelle.** Évitez de déplacer l’appareil photo d’une façon qui n’est pas représentative du mouvement réel de l’utilisateur. Si votre application nécessite de déplacer l’utilisateur via une scène, rendez le mouvement prévisible, réduisez l’accélération et laissez l’utilisateur contrôler le mouvement.
3. **Suivez les instructions de qualité de l’hologramme.** Les applications performantes qui implémentent les recommandations en matière de [qualité des hologrammes](hologram-stability.md) sont moins susceptibles d’entraîner une gêne pour l’utilisateur.
4. **Distribuez les hologrammes horizontalement plutôt que verticalement.** Forcer l’utilisateur à consacrer de longues périodes de temps à la recherche ou à la baisse peut entraîner une fatigue dans le cou.

## <a name="input"></a>Entrée

### <a name="interaction-models"></a>Modèles d’interaction

Assurez-vous que les interactions d’hologramme fonctionnent avec le [modèle d’interaction](../../design/interaction-fundamentals.md)que vous avez choisi.
Il est également judicieux de valider avec différents accessoires, tels que la souris et le clavier, s’ils sont nécessaires pour prendre en charge l’accessibilité.

**Validez le moment où votre application a un comportement différent avec la souris et le toucher.** Identifie les incohérences et aide à prendre des décisions de conception pour rendre l’expérience plus naturelle pour les utilisateurs. Par exemple, le déclenchement d’une action basée sur le pointage.


### <a name="custom-voice-commands"></a>Commandes vocales personnalisées

L' [entrée vocale](../../design/voice-input.md) est une forme naturelle d’interaction. L’expérience utilisateur peut être magique ou confuse en fonction de votre choix de commandes et de la façon dont vous les exposez. en règle générale, vous ne devez pas utiliser de commandes vocales système telles que « Select » ou « Hey Cortana » comme commandes personnalisées. Voici quelques points à prendre en compte :
1. **Évitez d’utiliser des commandes similaires.** Peut potentiellement déclencher une commande incorrecte.
2. **Choisissez des mots phonétiquement enrichis lorsque cela est possible.** Minimise et/ou évite les fausses activations.

### <a name="peripherals"></a>Périphériques

Les utilisateurs peuvent interagir avec votre application via des [périphériques](../../discover/hardware-accessories.md). Les applications n’ont rien à faire pour tirer parti de cette fonctionnalité. Toutefois, il y a deux choses qui méritent d’être vérifiées.
1. **Validez les interactions personnalisées.** Des raccourcis clavier personnalisés pour votre application.
2. **Validez le basculement des types d’entrée.** Tentative d’utilisation de plusieurs méthodes d’entrée pour effectuer une tâche, telle que la voix, le mouvement, la souris et le clavier dans le même scénario.

## <a name="system-integration"></a>Intégration du système

### <a name="battery"></a>Batterie

Testez votre application sans une source d’alimentation connectée pour comprendre la vitesse à laquelle elle draine la batterie. L’un peut facilement comprendre l’état de la batterie en examinant les lectures de LED d’alimentation. 

![États LED qui indiquent la puissance de la batterie](images/batterypowerledindication-500px.png)<br>

*États LED qui indiquent la puissance de la batterie*

### <a name="power-state-transitions"></a>Transitions d’état d’alimentation

Les scénarios de validation de clé fonctionnent comme prévu lors de la transition entre les États d’alimentation. Par exemple, l’application reste-t-elle à sa position d’origine ? Conserve-t-il son état correctement ? Continue-t-elle à fonctionner comme prévu ?
1. **Veille/reprise.** Pour entrer en mode veille, vous pouvez appuyer sur le bouton d’alimentation et le relâcher immédiatement. L’appareil entrera également en veille automatiquement après 3 minutes d’inactivité. Pour reprendre en mode veille, vous pouvez appuyer sur le bouton d’alimentation et le relâcher immédiatement. L’appareil reprend également si vous le connectez ou le déconnectez d’une source d’alimentation.
2. **Arrêt/redémarrage.** Pour arrêter, appuyez sur le bouton d’alimentation et maintenez-le enfoncé pendant 6 secondes. Pour redémarrer, appuyez sur le bouton d’alimentation.

### <a name="multi-app-scenarios"></a>Scénarios à plusieurs applications

Validez les fonctionnalités principales de l’application lors du basculement entre les applications, en particulier si vous avez implémenté une tâche en arrière-plan. le copier/coller et l’intégration de Cortana méritent également de vérifier le cas échéant.

## <a name="telemetry"></a>Télémétrie

Utilisez les données de télémétrie et les analyses pour vous guider. L’intégration de Analytics à votre application vous aide à obtenir des informations sur votre application auprès de vos testeurs et utilisateurs finaux. Ces données peuvent être utilisées pour optimiser votre application avant son envoi au Windows Store et pour les futures mises à jour. Il existe de nombreuses options d’analyse. si vous n’êtes pas sûr de l’emplacement de départ, consultez [Informations d’application](https://www.visualstudio.com/products/application-insights-vs.aspx).

Questions à prendre en compte :
1. Comment les utilisateurs utilisent-ils l’espace ?
2. Comment l’application place-t-elle des objets dans le monde-peut-il détecter des problèmes ?
3. Combien de temps consacrez-vous aux différentes étapes de l’application ?
4. Combien de temps consacrez-vous à l’application ?
5. Quels sont les chemins d’utilisation les plus courants que les utilisateurs essaient ?
6. Les utilisateurs atteignent-ils des États ou des erreurs inattendus ?

## <a name="emulator-and-simulated-input"></a>Emulator et une entrée simulée

l' [émulateur HoloLens](using-the-hololens-emulator.md) est un excellent moyen de tester efficacement votre application holographique avec différents types de caractéristiques et d’espaces simulés de l’utilisateur. Voici quelques suggestions pour utiliser efficacement l’émulateur pour tester votre application :
1. **Utilisez les salles virtuelles de l’émulateur pour développer vos tests.** L’émulateur est fourni avec un ensemble de salles virtuelles que vous pouvez utiliser pour tester votre application dans encore plus d’environnements.
2. **Utilisez l’émulateur pour examiner votre application à partir de tous les angles.** Les clés PageUp/PageDn rendent votre utilisateur simulé plus grand ou plus petit.
3. **Testez votre application avec un HoloLens réel.** l’HoloLens Emulator est un excellent outil pour vous aider à itérer rapidement sur une application et à détecter de nouveaux bogues, mais veillez également à effectuer des tests sur un HoloLens physique avant de l’envoyer au magasin de Windows. Il est important de s’assurer que les performances et l’expérience sont importantes sur du matériel réel.

## <a name="automated-testing-with-perception-simulation"></a>Tests automatisés avec simulation de perception

Certains développeurs d’applications peuvent souhaiter automatiser les tests de leurs applications. au-delà des tests unitaires simples, vous pouvez utiliser la pile de [simulation de perception](perception-simulation.md) dans HoloLens pour automatiser l’entrée humaine et mondiale dans votre application. l’API de simulation de perception peut envoyer une entrée simulée à l’émulateur HoloLens ou à un HoloLens physique.

## <a name="windows-app-certification-kit"></a>Kit de certification des applications Windows

pour permettre à votre application d’être [publiée dans le magasin de Windows](../../distribute/submitting-an-app-to-the-microsoft-store.md), validez-la et testez-la localement avant de la soumettre à la certification. Si votre application cible le Windows. famille d’appareils holographiques, le [Kit de Certification des applications Windows](/windows/uwp/debug-test-perf/windows-app-certification-kit) n’exécute que les tests d’analyse statique locaux sur votre PC. Aucun test ne sera exécuté sur votre HoloLens.

## <a name="see-also"></a>Voir aussi

* [envoi d’une application au magasin de Windows](../../distribute/submitting-an-app-to-the-microsoft-store.md)