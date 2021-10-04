---
title: FAQ SteamVR
description: SteamVR Windows Mixed Reality la résolution des problèmes qui vont au-delà de notre documentation de support technique standard.
author: qianwen
ms.author: v-qianwen
ms.date: 09/24/2021
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, dépannage, erreurs, aide, Support, SteamVR
ms.openlocfilehash: 17ab1709e8a2fc7e3eee70082aef64f0dc23d318
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436798"
---
# <a name="steamvr-faqs"></a>FAQ SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>comment jouer à des jeux SteamVR dans mon casque Windows Mixed Reality

1. [Téléchargez et installez SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe). Le didacticiel SteamVR doit démarrer automatiquement lorsque vous démarrez SteamVR.
2. Connecter votre casque sur votre ordinateur et allumez vos contrôleurs de mouvement.
3. une fois que Windows Mixed Reality page d’hébergement a été chargée et que vos contrôleurs sont visibles, ouvrez l’application à vapeur sur votre bureau.
4. Utilisez l’application Steam pour lancer un jeu SteamVR à partir de votre bibliothèque de vapeur. pour lancer des jeux SteamVR sans sortir votre casque, recherchez-les et lancez-les sous Windows Mixed Reality **démarrer > toutes les applications**.

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>un message indique « pour utiliser SteamVR avec Windows Mixed Reality, vous devez installer le dernier Windows Update » ou « Windows Mode développeur requis ».

1. assurez-vous que votre ordinateur exécute la dernière version de Windows 10 ou Windows 11. accédez à **Paramètres > système > sur** et, sous « spécifications de Windows », vérifiez que « version du système d’exploitation » est 16299,64 ou supérieure.
2. Assurez-vous que vous n’avez pas de mise à jour en attente de téléchargement ou d’installation. accédez à **Paramètres > mettre à jour & sécurité > Windows Update** et sélectionnez « rechercher les mises à jour ». Vous devrez peut-être vérifier plusieurs fois jusqu’à ce qu’aucune mise à jour supplémentaire ne soit disponible, puis redémarrez votre PC.

## <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR se bloque après la mise à jour de Windows

certaines versions antérieures de Windows Mixed Reality pour SteamVR ne sont plus compatibles avec Windows. pour vous assurer que votre version de Windows Mixed Reality pour SteamVR est à jour :

1. dans votre bibliothèque de vapeur, accédez à **logiciels > Windows Mixed Reality pour SteamVR**.
2. Cliquez dessus avec le bouton droit et accédez à « propriétés ».
3. Sélectionnez l’onglet « mettre à jour » et « toujours conserver cette application à jour ».
4. Forcez la mise à jour en accédant à l’onglet « fichiers locaux » et en sélectionnant « vérifier l’intégrité des fichiers d’application ».
5. Redémarrez Steam et SteamVR.

si SteamVR continue de se bloquer après la mise à jour, vous pouvez avoir deux installations de Windows Mixed Reality pour SteamVR sur votre ordinateur. Pour confirmer :

1. localisez ```%localappdata%\openvr\openvrpaths.vrpath``` et ouvrez-le dans Bloc-notes.
2. Consultez les sections « pilotes externes » pour rechercher plusieurs entrées pour « MixedRealityVRDriver »
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Si vous voyez plusieurs entrées, supprimez l’ancienne des deux entrées. Une fois que vous avez une seule entrée, il ne doit plus y avoir de virgule à la fin de la ligne. Par exemple :
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Enregistrez le fichier et fermez-le.
5. Redémarrez Steam et SteamVR.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Mes contrôleurs ne fonctionnent pas comme prévu dans SteamVR

1. Fermez SteamVR.
2. revenez à Windows Mixed Reality page d’hébergement et vérifiez que vos contrôleurs fonctionnent.
3. Lancez à nouveau l’expérience SteamVR et vos contrôleurs doivent revenir à la normale.
4. si les problèmes persistent, envoyez un commentaire de fichier à l’aide de la [Hub de commentaires Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) dans la catégorie de réalité mixte et incluez SteamVR dans le résumé.

Vous utiliserez vos contrôleurs de mouvement différemment dans différents jeux. Voici quelques notions de base pour vous aider à démarrer :
* Pour ouvrir le tableau de bord de la vapeur, appuyez sur le joystick de gauche.
* pour quitter un jeu SteamVR et revenir à la page d’hébergement Windows Mixed Reality, appuyez sur le bouton Windows. Sélectionnez ensuite le bouton d’accueil de la réalité mixte qui s’affiche à l’écran.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Mes contrôleurs de gauche et de droite sont inversés dans SteamVR

Démarrez le jeu en désactivant vos contrôleurs, puis activez le contrôleur de gauche, suivi de celui qui convient.

## <a name="my-games-are-running-slowly"></a>Mes jeux s’exécutent lentement

1. assurez-vous que votre ordinateur répond aux spécifications de SteamVR dans Windows Mixed Reality et le jeu que vous jouez.
2. Dans le portail de réalité mixte sur votre bureau, sélectionnez « Pause » pour arrêter la version préliminaire du bureau.
3. accédez à **Paramètres > système > sur** et sous « spécifications de Windows », vérifiez que « version du système d’exploitation » est 16299,64 ou une version ultérieure.
4. assurez-vous que votre ordinateur dispose des derniers pilotes graphiques (« rechercher des mises à jour » dans Windows Update).
5. Cochez « gestionnaire des tâches » pour connaître les autres processus qui peuvent consommer des ressources sur votre PC.
6. Vérifiez si la vapeur télécharge un jeu en arrière-plan, qui consomme des ressources et complique le fonctionnement des jeux.
7. Une petite classe d’applications qui n’ont pas de fenêtre visible (par exemple, SteamVR à la racine) présentent un problème de performance connu. La plupart des applications ne font pas partie de cette catégorie et un correctif sera disponible dans une prochaine mise à jour.

si vous rencontrez toujours des problèmes de performances inattendus, envoyez-nous vos commentaires à l’aide de la [Hub de commentaires Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Veillez à suivre les instructions pour [inclure un suivi des performances SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr).

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR affiche une erreur compository (par exemple, « shared IPC share Connecter failed (400) »).

Cela peut se produire si votre casque et votre moniteur principal se trouvent sur deux cartes vidéo différentes. connectez votre moniteur à la même carte que votre casque et configurez-le comme moniteur principal dans **Paramètres application > système > afficher**.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Le contenu SteamVR s’affiche au mauvais endroit, par exemple sous le plancher ou au-dessus de mon en-tête

Réinitialisez votre position :

1. Sélectionnez le stick analogique du contrôleur de gauche pour afficher le « tableau de bord SteamVR ».
2. sélectionnez le bouton « Paramètres ».
3. Sélectionnez « Réinitialiser la position assise ».

## <a name="my-steam-app-closed-unexpectedly"></a>Mon application à vapeur fermée de manière inattendue

L’application de vapeur se ferme si :

* Verrouillage de l’écran de votre ordinateur
* Supprimer votre casque
* Changer d’utilisateur
* Votre ordinateur passe en mode veille
