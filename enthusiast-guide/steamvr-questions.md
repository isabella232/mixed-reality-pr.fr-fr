---
title: FAQ SteamVR
description: SteamVR le dépannage de Windows Mixed realisation qui va au-delà de notre documentation de support technique standard.
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, SteamVR
ms.openlocfilehash: f1eafa303d0f2ee4c289f9acf337d8c512a7915c
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132133"
---
# <a name="steamvr-faqs"></a>FAQ SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Comment jouer à des jeux SteamVR dans mon casque Windows Mixed Reality

1. [Téléchargez et installez SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe). Le didacticiel SteamVR doit démarrer automatiquement lorsque vous démarrez SteamVR.
2. Connectez votre casque à votre ordinateur et allumez vos contrôleurs de mouvement.
3. Une fois que Windows Mixed Reality a été chargé et que vos contrôleurs sont visibles, ouvrez l’application Steam sur votre bureau.
4. Utilisez l’application Steam pour lancer un jeu SteamVR à partir de votre bibliothèque de vapeur. Pour lancer des jeux SteamVR sans sortir votre casque, recherchez-les et lancez-les sous **démarrer > toutes les applications** de Windows Mixed Reality.

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Un message indique que « pour utiliser SteamVR avec Windows Mixed Reality, vous devez installer le dernier Windows Update » ou « mode développeur Windows requis ».

1. Assurez-vous que votre ordinateur exécute la dernière version de Windows 10. Accédez à **paramètres > système > à propos** de et, sous « spécifications Windows », assurez-vous que « version du système d’exploitation » est 16299,64 ou supérieur.
2. Assurez-vous que vous n’avez pas de mise à jour en attente de téléchargement ou d’installation. Accédez à **paramètres > mettre à jour & sécurité > Windows Update** et sélectionnez « Rechercher les mises à jour ». Vous devrez peut-être vérifier plusieurs fois jusqu’à ce qu’aucune mise à jour supplémentaire ne soit disponible, puis redémarrez votre PC.

## <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR se bloque après la mise à jour de Windows

Certaines versions antérieures de Windows Mixed Reality pour SteamVR ne sont plus compatibles avec Windows. Pour vous assurer que votre version de Windows Mixed Reality pour SteamVR est à jour :

1. Dans votre bibliothèque de vapeur, accédez à **logiciel > Windows Mixed Reality for SteamVR** .
2. Cliquez dessus avec le bouton droit et accédez à « propriétés ».
3. Sélectionnez l’onglet « mettre à jour » et « toujours conserver cette application à jour ».
4. Forcez la mise à jour en accédant à l’onglet « fichiers locaux » et en sélectionnant « vérifier l’intégrité des fichiers d’application ».
5. Redémarrez Steam et SteamVR.

Si SteamVR continue de se bloquer après la mise à jour, vous pouvez avoir deux installations de Windows Mixed Reality pour SteamVR sur votre ordinateur. Pour confirmer si c’est le cas :

1. Localisez ```%localappdata%\openvr\openvrpaths.vrpath``` et ouvrez-le dans le bloc-notes.
2. Dans les sections « pilotes externes », recherchez plusieurs entrées pour « MixedRealityVRDriver »
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Si vous voyez plusieurs entrées, supprimez l’ancienne des deux entrées. Une fois que vous avez une seule entrée, il ne doit plus y avoir de virgule à la fin de la ligne. Exemple :
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Enregistrez le fichier et fermez-le.
5. Redémarrez Steam et SteamVR.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Mes contrôleurs ne fonctionnent pas comme prévu dans SteamVR

1. Fermez SteamVR.
2. Revenez à la page d’hébergement Windows Mixed Reality et vérifiez que vos contrôleurs fonctionnent correctement.
3. Lancez à nouveau l’expérience SteamVR et vos contrôleurs doivent revenir à la normale.
4. Si les problèmes persistent, envoyez des commentaires sur les fichiers à l’aide du [Hub de commentaires Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) sous la catégorie de réalité mixte et incluez SteamVR dans le résumé.

Notez que vous utiliserez vos contrôleurs de mouvement différemment dans différents jeux. Voici quelques notions de base pour vous aider à démarrer :
* Pour ouvrir le tableau de bord de la vapeur, appuyez sur le joystick de gauche.
* Pour quitter un jeu SteamVR et revenir à la page d’hébergement Windows Mixed Reality, appuyez sur le bouton Windows. Sélectionnez ensuite le bouton d’accueil de la réalité mixte qui apparaît à l’écran.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Mes contrôleurs de gauche et de droite sont inversés dans SteamVR

Démarrez le jeu en désactivant vos contrôleurs, puis activez le contrôleur de gauche, suivi de celui qui convient.

## <a name="my-games-are-running-slowly"></a>Mes jeux s’exécutent lentement

1. Assurez-vous que votre ordinateur répond aux spécifications de SteamVR dans Windows Mixed Reality et pour le jeu SteamVR que vous jouez.
2. Dans le portail de réalité mixte sur votre bureau, sélectionnez « Pause » pour arrêter la version préliminaire du bureau.
3. Accédez à **paramètres > > système à propos** de et sous « spécifications Windows », vérifiez que « version du système d’exploitation » est 16299,64 ou une version ultérieure.
4. Assurez-vous que votre ordinateur dispose des derniers pilotes graphiques (« Rechercher des mises à jour » dans Windows Update).
5. Cochez « gestionnaire des tâches » pour connaître les autres processus qui peuvent consommer des ressources sur votre PC.
6. Vérifiez si la vapeur télécharge un jeu en arrière-plan. Cela peut consommer des ressources et compliquer l’exécution des jeux.
7. Une petite classe d’applications qui n’ont pas de fenêtre visible (par exemple, SteamVR à la racine) présentent un problème de performance connu. La grande majorité des applications ne rentrent pas dans cette catégorie et un correctif sera disponible dans une prochaine mise à jour.

Si vous rencontrez toujours des problèmes de performances inattendus, envoyez-nous vos commentaires à l’aide du [Hub de commentaires Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Veillez à suivre les instructions pour [inclure un suivi des performances SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr).

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR affiche une erreur de compositeur (par exemple, « échec de la connexion au compositeur Shared IPC (400) »).

Cela peut se produire si votre casque et votre moniteur principal se trouvent sur deux cartes vidéo différentes. Connectez votre moniteur à la même carte que votre casque et configurez cette analyse comme moniteur principal dans **paramètres application > système > afficher** .

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Le contenu SteamVR s’affiche au mauvais endroit, par exemple sous le plancher ou au-dessus de mon en-tête

Réinitialisez votre position :

1. Cliquez sur le stick analogique du contrôleur de gauche pour afficher le « tableau de bord SteamVR ».
2. Sélectionnez le bouton « Paramètres ».
3. Sélectionnez « Réinitialiser la position assise ».

## <a name="my-steam-app-closed-unexpectedly"></a>Mon application à vapeur fermée de manière inattendue

L’application de vapeur se ferme si vous verrouillez l’écran de votre PC, si vous retirez votre casque, si vous changez d’utilisateur ou si votre ordinateur passe en mode veille.
