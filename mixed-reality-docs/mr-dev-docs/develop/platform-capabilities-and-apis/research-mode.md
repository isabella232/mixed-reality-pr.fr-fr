---
title: Mode de recherche HoloLens
description: En utilisant le mode de recherche sur HoloLens, une application peut accéder aux flux de capteur de périphérique clé (profondeur, suivi de l’environnement et réflectivité de l’IR).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Mode de recherche, CV, RS4, vision par ordinateur, recherche, HoloLens, HoloLens 2
ms.openlocfilehash: c8e626969f87eda8b686ba759a167a2bf48e3277
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583135"
---
# <a name="hololens-research-mode"></a>Mode de recherche HoloLens

Le mode de recherche a été introduit sur les appareils HoloLens (1er génération) pour permettre l’accès aux capteurs de clé, en particulier pour les applications de recherche qui ne sont pas destinées au déploiement.  Le mode de recherche pour HoloLens 2 conserve les fonctionnalités de HoloLens 1, mais ajoute l’accès aux flux suivants :

* **Caméras de suivi de l’environnement clair visibles** -caméras de nuances de gris utilisées par le système pour le suivi des têtes et la génération de cartes.
* **Appareil photo de profondeur** : fonctionne en deux modes :  
    + Détection presque-profondeur AHAT, à fréquence élevée (45 FPS) utilisée pour le suivi des handles. Différemment du mode de levée de la première version, AHAT offre une Pseudo-profondeur avec un retour à la ligne au-delà de 1 mètre. 
    + Détection de longueurs longues, à faible fréquence (1-5 FPS), utilisée par le [mappage spatial](../../design/spatial-mapping.md)

* **Deux versions du flux de réflectivité IR** -utilisées par le HoloLens pour calculer la profondeur. Ces images sont éclairées par infrarouge et ne sont pas affectées par la lumière visible ambiante.

Si vous utilisez un HoloLens 2, vous avez également accès aux entrées supplémentaires ci-dessous :

* **Accéléromètre** : utilisé par le système pour déterminer l’accélération linéaire le long des axes X, Y et Z et la gravité.
* **Gyroscope** : utilisé par le système pour déterminer les rotations.
* **Magnétomètre** : utilisé par le système pour estimer l’orientation absolue.

> [!IMPORTANT]
> Le mode de recherche est actuellement en version préliminaire publique. 

![Capture d’écran de l’application en mode recherche](images/sensor-stream-viewer.jpg)<br>
*Capture de réalité mixte d’une application de test qui affiche les huit flux de capteurs disponibles en mode de recherche*

## <a name="usage"></a>Usage

Le mode de recherche est conçu pour les chercheurs universitaires et industriels qui explorent de nouvelles idées dans les domaines de la Vision par ordinateur et de la robotique.  Elle n’est pas destinée aux applications déployées dans des environnements d’entreprise ou disponibles via le Microsoft Store ou d’autres canaux de distribution.

En outre, Microsoft ne garantit pas que le mode de recherche ou les fonctionnalités équivalentes seront pris en charge dans les futures mises à jour du matériel ou du système d’exploitation. Toutefois, ne vous laissez pas vous empêcher de l’utiliser pour développer et tester de nouvelles idées !

## <a name="security-and-performance"></a>Sécurité et performances

L’activation du mode de recherche utilise davantage de batterie que l’utilisation du HoloLens 2 dans des conditions normales, même si l’application qui utilise les fonctionnalités du mode de recherche n’est pas en cours d’exécution.  L’activation de ce mode peut également réduire la sécurité globale de votre appareil, car les applications peuvent avoir recours à des données de capteur.  Vous trouverez plus d’informations sur la sécurité des appareils dans le [Forum aux questions sur la sécurité HoloLens](/hololens/hololens-faq-security).  

## <a name="device-support"></a>Prise en charge des appareils
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>Fonctionnalité</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens première génération</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>Caméras de suivi des têtes</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Caméra de profondeur & IR</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Accéléromètre</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Gyroscope</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Magnétomètre</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>Activation du mode de recherche (HoloLens First GEN et HoloLens 2)

Le mode de recherche est une extension du mode développeur. Avant de commencer, les fonctionnalités de développement de l’appareil doivent être activées pour accéder aux paramètres du mode de recherche : 

* Ouvrez le **menu démarrer > paramètres** , puis sélectionnez **mises à jour**.
* Sélectionnez **pour les développeurs** et activer le **mode développeur**.
* Faites défiler la liste et activez le **portail d’appareil**.

Une fois les fonctionnalités du développeur activées, [Connectez-vous au portail de l’appareil](/windows/uwp/debug-test-perf/device-portal-hololens) pour activer les fonctionnalités du mode de recherche :

* Accédez à **système > le mode de recherche** dans le portail de l' **appareil**.
* Sélectionnez **autoriser l’accès au flux de capteur**.
* Redémarrez l’appareil à partir de l’élément de menu **Power** situé en haut de la page.

Une fois que vous avez redémarré l’appareil, les applications chargées via le portail de l' **appareil** peuvent accéder aux flux en mode de recherche.

![Onglet mode de recherche du portail de l’appareil HoloLens](images/ResearchModeDevPortal.png)<br>
*Fenêtre du mode de recherche dans le portail d’appareils HoloLens*

> [!IMPORTANT]
> Le mode de recherche pour HoloLens 2 est disponible à partir de la build 19041,1356. Si vous avez besoin d’accéder à une version antérieure, inscrivez-vous à notre programme [Insider Preview](/hololens/hololens-insider) .

### <a name="using-sensor-data-in-your-apps"></a>Utilisation des données de capteur dans vos applications

Les applications peuvent accéder aux données de flux de capteur de la même façon que [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) accède à des flux de photo et de vidéo. 

Toutes les API qui fonctionnent pour le développement HoloLens sont également disponibles en mode de recherche. En particulier, l’application sait précisément où HoloLens se trouve dans l’espace 6DoF à chaque fois que la capture de l’image du capteur est terminée.

Nous avons des exemples d’applications qui illustrent l’accès aux flux en mode de recherche, à l’aide des [fonctions intrinsèques et extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)et de l’enregistrement des flux :
* [HoloLens (première génération)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>Support

Pour HoloLens (First Gen), utilisez le [suivi des problèmes](https://github.com/Microsoft/HololensForCV/issues) dans le référentiel HoloLensForCV pour publier des commentaires et effectuer le suivi des problèmes connus.

Pour HoloLens 2, utilisez le [suivi des problèmes](https://github.com/microsoft/HoloLens2ForCV/issues) dans le référentiel HoloLens2ForCV pour publier des commentaires et effectuer le suivi des problèmes connus.

## <a name="see-also"></a>Voir aussi

* [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [HoloLensForCV GitHub référentiel](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens2ForCV GitHub référentiel](https://github.com/microsoft/HoloLens2ForCV)
* [Utilisation du portail d’appareil Windows](using-the-windows-device-portal.md)