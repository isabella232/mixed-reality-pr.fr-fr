---
title: Utilisation du portail d’appareil Windows
description: Découvrez comment configurer et gérer à distance votre appareil via une connexion Wi-Fi ou USB en utilisant le Portail d‘appareil Windows.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Portail d’appareil Windows, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 92f8c67297a33c4c8e72de802ceb8a3080d904d9
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905722"
---
# <a name="using-the-windows-device-portal"></a>Utilisation du portail d’appareil Windows

<table>
<tr>
<th>Fonctionnalité</th><th style="width:150px"><a href="/hololens/hololens1-hardware">HoloLens (1ère génération)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px">
</tr><tr>
<td> Portail d’appareil Windows</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Le portail d’appareil Windows pour HoloLens vous permet de configurer et de gérer à distance votre appareil par le biais d’une connexion Wi-Fi ou USB. Le Device Portal est un serveur Web situé sur l'appareil auquel vous pouvez vous connecter depuis un navigateur Web sur votre PC. Le portail d’appareil comprend de nombreux outils qui vous aideront à gérer votre appareil HoloLens, ainsi qu’à déboguer et à optimiser vos applications.

Cette documentation concerne spécifiquement le portail d’appareil Windows pour HoloLens. Si vous souhaitez utiliser le portail d’appareil Windows pour les ordinateurs de bureau (y compris pour Windows Mixed Reality), consultez [Vue d’ensemble du portail d’appareil Windows](/windows/uwp/debug-test-perf/device-portal).

> [NOTE!] Il n’est pas recommandé d’utiliser le portail d’appareil pour les appareils HoloLens que vous déployez dans votre organisation.

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configuration de HoloLens pour l’utilisation du portail d’appareil Windows

1. Mettez HoloLens sous tension et allumez l’appareil.
2. Pour lancer le menu principal, utilisez le [mouvement associé au menu Démarrer](/hololens/hololens2-basic-usage#start-gesture) sur un HoloLens 2 ou [écartez les doigts paume vers le haut](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) sur un HoloLens (1re génération). 
3. Pointez du regard la vignette **Paramètres** et effectuez un [clic aérien](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) sur un HoloLens (1re génération). Vous pouvez également la sélectionner sur un HoloLens 2 [en la touchant ou en utilisant un rayon émanant de la main](/hololens/hololens2-basic-usage). 
4. Sélectionnez l’élément de menu **Mettre à jour**.
5. Sélectionnez l’élément de menu **Pour les développeurs**.
6. Activez **Mode développeur**.

> [!IMPORTANT]
> Si vous êtes dans un environnement multi-utilisateur et que vous n’êtes pas administrateur, la capacité à entrer en mode Développeur peut être grisée. Vérifiez que vous êtes **[administrateur sur l’appareil](/hololens/security-adminless-os)** .

7. [Faites défiler](../../design/gaze-and-commit.md#composite-gestures) la liste et activez le **portail d’appareil**.
8. Si vous configurez le portail d’appareil Windows afin de pouvoir déployer des applications sur cet HoloLens par le biais d’une connexion USB ou Wi-Fi, sélectionnez **Coupler** pour [générer un code PIN d’appairage](using-visual-studio.md). Dans l’application Paramètres, laissez le menu contextuel Code confidentiel ouvert jusqu’à ce que vous entriez le code confidentiel dans Visual Studio lors du premier déploiement.

![Activation du mode Développeur dans l’application Paramètres pour Windows Holographique](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a>Connexion Wi-Fi

1. [Connectez votre appareil HoloLens au Wi-Fi](/hololens/hololens-network).
2. Recherchez l’adresse IP de votre appareil en effectuant l’une des opérations suivantes :
  * Accédez à **Paramètres > Réseau et Internet > Wi-Fi > Options avancées**.
  * Accédez à **Paramètres > Réseau et Internet** et sélectionnez **Propriétés matérielles**.
  * Utilisation de la commande vocale « Quelle est mon adresse IP ? ».

![Paramètres HoloLens 2](images/using-windows-portal-img-02.jpg)

3. Sur votre PC, dans un navigateur web, accédez à https://<ADRESSE_IP_DE_VOTRE_APPAREIL_HOLOLENS>
   * Le navigateur affichera le message suivant : « Le certificat de sécurité de ce site web présente un problème ». Cela se produit car le certificat émis au portail d’appareil est un certificat de test. Vous pouvez ignorer cette erreur de certificat pour le moment et continuer.

## <a name="connecting-over-usb"></a>Connexion USB

> [!IMPORTANT]
> IpOverUsb n’est plus recommandé par les nouvelles normes de navigateur, car il requiert l’utilisation du port 10080. Si vous souhaitez toujours utiliser IpOverUsb, cochez la case « Connectivité des périphériques USB » pendant l’installation de Visual Studio, qui n’est pas cochée par défaut. Au lieu de cela, nous vous recommandons de vous connecter avec UsbNcm, qui est pris en charge par défaut sur HoloLens 2. Si vous utilisez un HoloLens 1, nous vous recommandons de vous connecter à votre PC à l’aide du Wi-Fi.

1. Si votre HoloLens 2 exécute Windows Holographique version 21H1 ou supérieure, accédez à « Pour les développeurs » dans l’application Paramètres et assurez-vous que l’option « Découverte d’appareils » est ACTIVÉE. 
2. Branchez votre HoloLens 2 à votre PC à l’aide d’un câble USB-C.
3. Recherchez votre adresse IP UsbNcm. Il existe deux façons de procéder :
  * Dans l’application Paramètres sur l’appareil (cette méthode ne fonctionne que pour les HoloLens exécutant Windows Holographique version 21H1 ou supérieure pour lesquels que l’option « Découverte d’appareils » est ACTIVÉE.)
    1. Accédez à l’application Paramètres sur l’appareil.
    2. Accédez à « Mise à jour et sécurité » > « Pour les développeurs ». Il s’agit du même emplacement que celui sur lequel vous avez activé le portail d'appareil.
    3. En bas de la page, copiez votre adresse IP **Ethernet**. Il s’agit de votre adresse IP UsbNcm. 
    ![Paramètres de HoloLens 2 - Adresse IP UsbNcm](images/deviceportal_usbncm_ipaddress.jpg)

  * Dans le portail d'appareil 
    1. Sur votre appareil, ouvrez le portail d’appareil à l’aide de l’adresse Wi-Fi de votre HoloLens. Si vous ne connaissez pas l’adresse Wi-Fi de votre HoloLens, vous pouvez utiliser la commande vocale « Quelle est mon adresse IP ? »
    2. Accédez à Système > Réseaux
    3. À l’extrême droite de la page, dans le panneau « Configuration IP », recherchez la section qui commence par « Description : fonction UsbNcm ».
    4. Votre adresse IP UsbNcm figure sur la ligne « Adresse IPv4 ». Vous pouvez copier l’adresse ou simplement cliquer dessus. Il s’agit d’un lien hypertexte qui rouvre le portail d’appareil à l’aide de l’adresse IP UsbNcm.
  
  * Dans une invite de commandes
    1. Dans une invite de commandes, accédez au dossier bin\<SDK version>\x86 où est installé votre kit de développement logiciel (SDK) Windows 10, par exemple, C:\Program Files (x86)\Windows Kits\10\bin\10.0.19041.0\x86.
    2. Tapez « appareils winappdeploycmd » et appuyez sur Entrée.
    3. Dans la sortie, recherchez l’entrée où la colonne Modèle/nom correspond au nom de votre appareil HoloLens, par exemple HOLOLENS-xxxxxx. L’adresse IP UsbNcm se trouve au début de cette ligne et sera une adresse IP privée automatique sous la forme 169.254.x.x. Copiez cette adresse. 
 
4. Si vous avez copié votre adresse IP UsbNcm à partir d’un navigateur web sur votre PC, accédez à https://, suivi de votre adresse IP UsbNcm.

### <a name="moving-files-over-usb"></a>Déplacement de fichiers par USB

Vous pouvez déplacer des fichiers de votre PC vers votre HoloLens sans configurer d’autres paramètres.
1. Connectez votre PC à votre HoloLens à l’aide d’un câble USB.
2. Faites glisser vos fichiers dans **PC\\[nom_de_votre_appareil_HoloLens]\Internal Storage** sur votre bureau.
3. Ouvrez le **menu Démarrer** et sélectionnez **Toutes les applications > Explorateur de fichiers** sur votre HoloLens.

> [!NOTE]
> Vous devrez peut-être sélectionner **Cet appareil** sur le côté gauche du panneau pour quitter l’emplacement « Fichiers récents » afin de localiser vos fichiers. 

## <a name="connecting-to-an-emulator"></a>Connexion à un émulateur

Vous pouvez également utiliser Device Portal avec votre émulateur. Pour vous connecter au portail d’appareil, utilisez la [barre d’outils](using-the-hololens-emulator.md). Sélectionnez cette icône : ![Icône Ouvrir le portail d’appareil](images/emulator-deviceportal.png) **Ouvrir le portail d’appareil** : ouvre le Portail d’appareil Windows pour le système d’exploitation HoloLens dans l’émulateur.

## <a name="creating-a-username-and-password"></a>Création d’un nom d’utilisateur et d’un mot de passe

![Configurer l’accès au portail d’appareil Windows](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configurer l’accès au portail d’appareil Windows*

La première fois que vous vous connectez au portail d’appareil sur votre HoloLens, vous devez créer un nom d’utilisateur et un mot de passe.
1. Dans un navigateur web sur votre PC, entrez l’adresse IP de l’HoloLens. La page d’accès à la configuration s’affiche.
2. Sélectionnez **Demander un code PIN** ou appuyez dessus et regardez l’écran HoLolens pour obtenir le code PIN généré.
3. Entrez le code confidentiel dans la **zone de texte prévue à cet effet de votre appareil**.
4. Entrez le nom d’utilisateur que vous utiliserez pour vous connecter au portail d’appareil. Il n’est pas nécessaire qu’il s’agisse d’un nom de compte Microsoft (MSA) ou de domaine.
5. Entrez un mot de passe et confirmez-le. Le mot de passe doit comporter au moins sept caractères. Il n’est pas nécessaire qu’il s’agisse d’un mot de passe de compte Microsoft (MSA) ou de domaine.
6. Cliquez sur **Appairer** pour vous connecter au portail d’appareil Windows sur l’appareil HoloLens.

Si vous souhaitez modifier ce nom d’utilisateur ou ce mot de passe, vous pouvez à tout moment répéter ce processus en accédant à la page de sécurité de l’appareil : https://<ADRESSE_IP_DE_VOTRE_APPAREIL_HOLOLENS>/devicepair.htm.

## <a name="security-certificate"></a>Certificat de sécurité

Si une « erreur de certificat » s’affiche dans votre navigateur, vous pouvez la résoudre en créant une relation d’approbation avec l’appareil.

Chaque HoloLens génère un certificat auto-signé pour sa connexion SSL. Par défaut, ce certificat n’est pas approuvé par le navigateur web de votre PC, c’est la raison pour laquelle vous obtiendrez peut-être une « erreur de certificat ». Pour vous connecter en toute sécurité à votre appareil, téléchargez ce certificat à partir de votre HoloLens (par le biais d’une connexion USB ou Wi-Fi approuvée) et approuvez-le sur votre PC.
1. **Vérifiez que vous vous trouvez sur un réseau sécurisé (USB ou réseau Wi-Fi approuvé)** .
2. Téléchargez le certificat de cet appareil à partir de la page « Sécurité » sur le portail de l’appareil.
   * Accédez à : https://<ADRESSE_IP_DE_VOTRE_APPAREIL_HOLOLENS>/devicepair.htm
   * Ouvrez le nœud Système > Préférences. 
   * Faites défiler jusqu’à Sécurité des appareils, puis sélectionnez le bouton « Télécharger le certificat de cet appareil ».
3. Installez le certificat dans le magasin de « Autorités de certification racines de confiance » de votre PC.
   * Dans le menu Windows, tapez : gérer les certificats d’ordinateur et démarrer l’applet.
   * Développez le dossier **Trusted Root Certification Authority**.
   * Sélectionnez le dossier **Certificats**.
   * Dans le menu Action, sélectionnez : Toutes les tâches > Importer...
   * Terminez l’Assistant Importation de certificat en utilisant le fichier de certificat que vous avez téléchargé à partir de Device Portal.
4. Redémarrez le navigateur.

>[!NOTE]
> Ce certificat sera uniquement approuvé pour l’appareil et l’utilisateur devra recommencer le processus si l’appareil est flashé.

## <a name="sideloading-applications"></a>Chargement de version test des applications

### <a name="installing-a-certificate"></a>Installation d’un certificat

1. Dans le portail d’appareil Windows, accédez à la page **Gestionnaire d’applications**
2. Dans la section Déployer des applications, sélectionnez **Installer un certificat**
3. Sous Sélectionnez le fichier de certificat (.cer) utilisé pour signer un package d’application, sélectionnez Choisir un fichier et accédez au certificat associé au package d’application dont vous souhaitez charger une version test
4. Sélectionnez **Installer** pour commencer l’installation

![Capture d’écran de la page Gestionnaire d’applications ouverte dans le portail d’appareil Windows](images/sideloading-1.png)

### <a name="installing-an-app"></a>Installation d’une application

> [!NOTE]
> Pour qu’une application puisse être correctement installée via le portail d’appareil, elle doit être signée par un certificat qui doit être installé sur l’appareil avant d’essayer d’installer l’application. Pour obtenir des instructions, consultez la [section précédente](#installing-a-certificate).

1. Lorsque vous avez [créé un package d’application depuis Visual Studio](using-visual-studio.md), vous pouvez l’installer à distance sur votre appareil à partir des fichiers générés :

![Capture d’écran du contenu du fichier de package d’application](images/sideloading-2.png)

2. Dans le portail d’appareil Windows, accédez à la page **Gestionnaire d’applications**
3. Dans la section **Déployer des applications**, sélectionnez **Stockage local**
4. Sous Sélectionner le package d’application, sélectionnez Choisir un fichier et accédez au package d’application dont vous souhaitez charger une version test
5. Cochez les cases respectives si vous souhaitez installer des packages facultatifs ou de framework en même temps que l’application, puis sélectionnez **Suivant** :

![Capture d’écran de la page Gestionnaire d’applications ouverte dans le portail d’appareil Windows avec l’onglet Stockage local en surbrillance](images/sideloading-3.png)

6. Sélectionnez **Installer** pour commencer l’installation
 
![Capture d’écran de la page Gestionnaire d’applications ouverte dans le portail d’appareil Windows avec l’installation terminée](images/sideloading-4.png) 

Une fois l’installation terminée, revenez à la page **All apps** dans HoloLens et lancez votre application nouvellement installée.

## <a name="device-portal-pages"></a>Pages de Device Portal

### <a name="home"></a>page d'accueil

![Page d’accueil du portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-04.png)<br>
*Page d’accueil du portail d’appareil Windows sur Microsoft HoloLens*

> [NOTE] Les paramètres configurés dans le portail d’appareil s’appliquent à tout l’appareil et persistent à la suite de redémarrages. Il est recommandé d’utiliser le portail d’appareil uniquement lors du développement, et non sur des appareils déployés.

Votre session Device Portal démarre sur la page d’accueil. Accédez à d’autres pages à partir de la barre de navigation située sur le côté gauche de la page d’accueil.

La barre d’outils se trouvant en haut de la page permet d’accéder aux fonctionnalités et aux états couramment utilisés.
* **En ligne** : indique si l’appareil est connecté au Wi-Fi.
* **Arrêt** : éteint l’appareil.
* **Redémarrer** : mise sous tension de l’appareil par cycle.
* **Sécurité** : ouvre la page de sécurité de l’appareil.
* **Froid** : indique la température de l’appareil.
* **Secteur** : indique si l’appareil est branché sur le secteur et en cours de chargement.
* **Aide** : ouvre la page relative à la documentation de l’interface REST.

La page d’accueil affiche les informations suivantes :
* **État de l’appareil** : supervise l’état de votre appareil et signale les erreurs critiques.
* **Informations Windows** : affiche le nom du casque HoloLens et la version de Windows installée.
* La section **Préférences** comprend les paramètres suivants :
   * **IPD** : définit l’écart pupillaire correspondant à la distance, exprimée en millimètres, séparant le centre des pupilles de l’utilisateur lorsqu’il regarde droit devant lui. Le paramètre prend immédiatement effet. La valeur par défaut a été calculée automatiquement lors de la configuration de votre appareil.
   * **Nom de l’appareil** : attribuez un nom au casque HoloLens. redémarrez l’appareil après avoir modifié cette valeur pour qu’elle soit prise en compte. Après avoir cliqué sur **Enregistrer**, une boîte de dialogue vous demande si vous voulez redémarrer l’appareil immédiatement ou ultérieurement.
   * **Paramètres de la veille** : définit le délai d’attente avant la mise en veille de l’appareil lorsque celui-ci est branché ou sur batterie.

### <a name="3d-view"></a>Vue 3D

![Page Vue 3D dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-05.png)<br>
*Page Vue 3D dans le portail d’appareil Windows sur Microsoft HoloLens*

Utilisez la page Vue 3D pour voir comment HoloLens interprète votre environnement. Naviguez dans la vue à l’aide de la souris :
* Pivoter : clic gauche + souris
* Mouvement panoramique : clic droit + souris
* Zoom : défilement à l’aide de la souris.
* **Options de suivi** :
   * activez le suivi visuel en continu en cochant **Forcer le suivi visuel**. 
   * **Suspendre** arrête le suivi visuel.
* **Options d’affichage** : définissez les options de l’affichage 3D :
  * **Suivi** : indique si le suivi visuel est actif.
  * **Afficher le sol** : affiche un plan de sol en damier.
  * **Afficher le tronc de cône** : affiche le tronc de cône.
  * **Afficher le plan de stabilisation** : affiche le plan utilisé par HoloLens pour stabiliser le mouvement.
  * **Afficher le maillage** : affiche le maillage de mappage de surface qui représente votre environnement.
  * **Afficher les ancres spatiales** : affiche les ancres spatiales de l’application active. Sélectionnez le bouton Mettre à jour pour récupérer et actualiser les ancres.
  * **Afficher les détails** : affiche la position des mains, les quaternions de rotation de la tête et le vecteur d’origine à mesure de leur changement en temps réel.
  * **Bouton plein écran** : affiche la vue 3D en mode plein écran. Appuyez sur la touche ÉCHAP pour quitter le mode plein écran.
* **Reconstruction de surface** : sélectionnez **Mettre à jour** ou appuyez dessus pour afficher le tout dernier maillage de mappage spatial de l’appareil. Un passage complet peut nécessiter un certain temps (pouvant aller jusqu’à quelques secondes). Le maillage ne se met pas à jour automatiquement dans la vue 3D. Vous devez sélectionner **Mettre à jour** pour obtenir le tout dernier maillage à partir de l’appareil. Sélectionnez **Enregistrer** pour enregistrer le maillage de mappage spatial actuel en tant que fichier obj sur votre PC.
* **Ancres spatiales** : sélectionnez Mettre à jour pour afficher ou mettre à jour les ancres spatiales de l’application active.

### <a name="map-manager"></a>Map Manager

Map Manager vous permet de partager des cartes entre des appareils, qui peuvent être utilisées afin de configurer des expériences partagées pour les clients de Divertissement en fonction de la localisation. L’outil vous permet d’importer et d’exporter des cartes système et des ancres.  

Pour accéder à Map Manager, connectez-vous au Portail d’appareil et sélectionnez **Réalité mixte -> Map Manager** : 

![Page Map Manager dans le Portail d’appareil Windows](images/using-windows-portal-img-06.png)
*Page Map Manager dans le Portail d’appareil Windows sur Microsoft HoloLens*

#### <a name="exporting-and-importing-maps"></a>Exportation et importation de cartes

Pour exporter des cartes, sélectionnez **Exporter la carte système et les ancres**. Cela peut prendre un certain temps ; soyez donc prêt à patienter 30 à 60 secondes pendant l’exportation de la carte. Une fois l’opération terminée, le fichier est téléchargé dans votre navigateur.  

Pour importer des cartes et des ancres, sélectionnez respectivement **Charger un fichier de carte** et **Charger un fichier d’ancre**, puis sélectionnez un fichier de carte ou d’ancre que vous avez déjà exporté. Le fichier de carte ou d’ancre chargé peut provenir de n’importe quel autre appareil HoloLens. 

> [!NOTE]
> Sur HoloLens, il est également possible d’importer et d’exporter la base de données de mappage spatial. Toutefois, cela ne fonctionne pas sur les appareils non-HoloLens.  


### <a name="mixed-reality-capture"></a>MRC (Mixed Reality Capture)

![Page Capture de Réalité Mixte dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-07.png)<br>
*Page Capture de Réalité Mixte dans le portail d’appareil Windows sur Microsoft HoloLens*

> [IMPORTANT] Les paramètres configurés dans le portail d’appareil s’appliquent à tout l’appareil et persistent à la suite de redémarrages. Tous les paramètres modifiés dans le portail d’appareil s’appliquent aux captures et aux applications de réalité mixte. Ces paramètres étant persistants, il est recommandé d’utiliser le portail d’appareil uniquement lors du développement, et non sur des appareils déployés.

Utilisez la page MRC pour enregistrer les flux multimédias issus du casque HoloLens.
* **Paramètres de capture** : contrôle les flux multimédias capturés en vérifiant les paramètres suivants :
  * **Hologrammes** : capture le contenu holographique du flux vidéo. Les hologrammes font l’objet d’un rendu en mono et non en stéréo.
  * **Caméra PV** : capture le flux vidéo à partir de l’appareil photo ou de la caméra vidéo.
  * **Son du micro** : capture les données audio à partir du réseau de microphones.
  * **Son de l’application** : capture les données audio à partir de l’application en cours d’exécution.
  * **Afficher à partir de la caméra** : aligne la capture sur le point de vue de l’appareil photo ou de la caméra vidéo, si cela est [pris en charge par l’application en cours d’exécution](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 uniquement).
  * **Qualité de l’aperçu instantané** : sélectionnez la résolution d’écran, la fréquence d’images et la vitesse de streaming de l’aperçu instantané.
* **Paramètres audio** (HoloLens 2 uniquement) :
  * **Catégorie de média audio** : sélectionnez la catégorie utilisée lors du traitement du microphone. La valeur **Par défaut** permet d’inclure une partie de l’environnement, tandis que **Communications** applique une annulation du bruit de fond.
  * **Gain audio de l’application** : gain appliqué au volume de l’audio de l’application.
  * **Gain audio du micro** : gain appliqué au volume de l’audio du microphone.
* **Paramètres photo et vidéo** (HoloLens 2, version 2004 ou ultérieure) :
  * **Profil de capture** : sélectionnez le profil utilisé lors de la prise de photos et de vidéos. Ce profil détermine les résolutions et fréquences d’images disponibles.
  * **Résolution photo** : résolution à laquelle la photo sera prise.
  * **Résolution vidéo et fréquence d’images** : résolution et fréquence d’images auxquelles la vidéo sera prise.
  * **Tampon de stabilisation vidéo** : taille du tampon utilisé lors de la prise d’une vidéo. Plus la valeur est élevée, plus les mouvements rapides peuvent être compensés.
* Sélectionnez le bouton **Aperçu instantané** ou appuyez dessus pour afficher le flux de capture. **Arrêter l’aperçu instantané** arrête le flux de capture.
* Sélectionnez **Enregistrer** ou appuyez dessus pour commencer à enregistrer le flux de réalité mixte à l’aide des paramètres spécifiés. **Arrêter l’enregistrement** arrête l’enregistrement et le sauvegarde.
* Sélectionnez **Prendre une photo** ou appuyez dessus pour prendre une image fixe à partir du flux de capture.
* Sélectionnez **Restaurer les paramètres par défaut** ou appuyez dessus pour restaurer les paramètres audio, photo et vidéo par défaut.
* **Photos et vidéos** : affiche une liste des captures photo et vidéo prises sur l’appareil.

Tous les paramètres de cette page s’appliquent aux captures effectuées à l’aide du portail d’appareil Windows. D’autres s’appliquent également à la MRC système, notamment le menu Démarrer, les boutons matériels, les commandes vocales globales, Miracast et les enregistreurs MRC personnalisés.

|  Paramètre  |  S’applique à System MRC  |  S’applique aux enregistreurs MRC personnalisés |
|----------|----------|----------|
|  Hologrammes  |  Non  |  Non |
|  Caméra PV  |  Non  |  Non |
|  Son du micro  |  Non  |  Non |
|  Son de l’application  |  Non  |  Non |
|  Afficher à partir de la caméra  |  Oui    |  Oui (peut être substitué) |
|  Qualité de l’aperçu instantané  |  Non  |  Non |
|  Catégorie de média audio  |  Oui  |  Non |
|  Gain audio de l’application  |  Oui  |  Oui (peut être substitué) |
|  Gain audio du micro  |  Oui  |  Oui (peut être substitué) |
|  Profil de capture  |  Oui  |  Non |
|  Résolution photo  |  Oui  |  Non |
|  Résolution vidéo et fréquence d’images  |  Oui  |  Non |
|  Tampon de stabilisation vidéo  |  Oui  |  Oui (peut être substitué) |

> [!NOTE]
> Il existe des [limites concernant les captures de Réalité Mixte simultanées](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations) :
> * Si une application tente d’accéder à l’appareil photo ou à la caméra vidéo alors que le portail de d’appareil Windows est en train d’enregistrer une vidéo, l’enregistrement vidéo s’arrête.
>   * HoloLens 2 n’arrête pas l’enregistrement vidéo si l’application accède à l’appareil photo ou à la caméra vidéo en mode SharedReadOnly.
> * Si une application utilise activement l’appareil photo ou la caméra vidéo, le portail d’appareil Windows peut prendre une photo ou enregistrer une vidéo.
> * Streaming en direct :
>   * HoloLens (1re génération) empêche une application d’accéder à l’appareil photo ou à la caméra vidéo pendant le streaming en direct à partir du portail d’appareil Windows.
>   * HoloLens (1ère génération) ne parviendra pas à effectuer un streaming en direct si une application utilise activement l’appareil photo ou la caméra vidéo.
>   * HoloLens 2 arrête automatiquement le streaming en direct quand une application tente d’accéder à l’appareil photo ou à la caméra vidéo en mode ExclusiveControl.
>   * HoloLens 2 peut démarrer un flux en direct pendant qu’une application utilise activement la caméra PV.

### <a name="performance-tracing"></a>Suivi des performances

![Page Suivi des performances dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-08.png)<br>
*Page Suivi des performances dans le portail d’appareil Windows sur Microsoft HoloLens*

Capturez les suivis de l’[Enregistreur de performance Windows](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR) à partir de votre appareil HoloLens.
* **Profils disponibles** : sélectionnez le profil WPR dans la liste déroulante, puis sélectionnez **Démarrer** ou appuyez dessus pour commencer le suivi.
* **Profils personnalisés** : sélectionnez **Parcourir** ou appuyez dessus pour choisir un profil WPR sur votre PC. Sélectionnez **Charger et démarrer** ou appuyez dessus pour commencer le suivi.

Pour arrêter le suivi, sélectionnez le lien Arrêter. Restez dans cette page jusqu’à ce que le fichier de suivi ait terminé le téléchargement.

Les fichiers ETL capturés peuvent être ouverts pour analyse dans [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)).

### <a name="processes"></a>Processus

![Page Processus dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-09.png)<br>
*Page Processus dans le portail d’appareil Windows sur Microsoft HoloLens*

Affiche les détails concernant les processus en cours d’exécution. Cela comprend les processus relatifs aux applications au système.

### <a name="system-performance"></a>Performances du système

![Page Performances du système dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-10.png)<br>
*Page Performances du système dans le portail d’appareil Windows sur Microsoft HoloLens*

Présente des graphiques en temps réel des informations de diagnostic système, telles que la consommation d’énergie, la fréquence d’images et la charge du processeur.

Voici les mesures disponibles :
* **Alimentation SOC** : utilisation de l’alimentation système sur puce instantanée, moyenne par minute
* **Alimentation système** : utilisation de l’alimentation système instantanée, moyenne par minute
* **Fréquence d’images** : images par seconde, VBlanks manqués par seconde et VBlanks manqués successifs
* **GPU** : utilisation du moteur GPU, pourcentage du total disponible
* **Processeur** : pourcentage du total disponible
* **E/S** : lectures et écritures
* **Réseau** : réceptions et envois
* **Mémoire** : totale, en cours d’utilisation, disponible validée, paginée et non paginée

### <a name="apps"></a>Applications

![Page Applications dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-11.png)<br>
*Page Applications dans le portail d’appareil Windows sur Microsoft HoloLens*

Gère les applications qui sont installées sur l’appareil HoloLens.
* **Applications installées** : supprime et démarre des applications.
* **Applications en cours d’exécution** : liste les applications en cours d’exécution.
* **Installer l’application** : sélectionne les packages d’application à installer à partir d’un dossier de votre ordinateur ou de votre réseau.
* **Dépendance** : ajoute des dépendances à l’application que vous souhaitez installer.
* **Déployer** : déploie l’application et les dépendances sélectionnées sur l’appareil HoloLens.

### <a name="app-crash-dumps"></a>Vidages sur incident des applications

![Page Vidages sur incident des applications dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-12.png)<br>
*Page Vidages sur incident des applications dans le portail d’appareil Windows sur Microsoft HoloLens*

Cette page vous permet de recueillir les vidages sur incident de vos applications chargées de manière indépendante. Cochez la case **Activation des vidages sur incident** pour chaque application pour laquelle vous souhaitez recueillir des vidages sur incident. Revenez à cette page pour recueillir les vidages sur incident. Les fichiers de vidage peuvent être [ouverts dans Visual Studio pour le débogage](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files).

### <a name="file-explorer"></a>Explorateur de fichiers

![Page Explorateur de fichiers dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-13.png)<br>
*Page Explorateur de fichiers dans le portail d’appareil Windows sur Microsoft HoloLens*

Utilisez l’Explorateur de fichiers pour parcourir, charger et télécharger des fichiers. Vous pouvez utiliser les fichiers du dossier Documents, du dossier Images et des dossiers de stockage local des applications que vous avez déployées à partir de Visual Studio ou du portail d’appareil.

### <a name="kiosk-mode"></a>Mode plein écran

>[!NOTE]
>Le mode plein écran est disponible uniquement avec la suite [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features).

![Page Mode kiosque dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-14.png)

Pour obtenir des instructions à jour sur l’activation du mode plein écran via le portail d’appareil Windows, consultez l’article [Configurer HoloLens en mode plein écran](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) sur Windows IT Pro Center.

### <a name="logging"></a>Journalisation

![Page Journalisation dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-15.png)<br>
*Page Journalisation dans le portail d’appareil Windows sur Microsoft HoloLens*

Gère en temps réel le suivi d’événements pour Windows (ETW) sur l’appareil HoloLens.

Cochez la case **Masquer les fournisseurs** pour n’afficher que la liste **Événements**.
* **Fournisseurs inscrits** : sélectionnez le fournisseur ETW et le niveau de suivi. Le niveau de suivi est l’une des valeurs suivantes :
   1. Sortie ou arrêt anormal
   2. Erreurs graves
   3. Avertissements
   4. Avertissements sans erreur

Sélectionnez **Activer** ou appuyez dessus pour démarrer le suivi. Le fournisseur est ajouté à la liste déroulante **Fournisseurs activés**.
* **Fournisseurs personnalisés** : sélectionnez un fournisseur ETW personnalisé et le niveau de suivi. Identifiez le fournisseur par son GUID. N’insérez pas de crochets dans le GUID.
* **Fournisseurs activés** : liste les fournisseurs activés. Sélectionnez un fournisseur dans la liste déroulante, puis cliquez sur ou appuyez sur **Désactiver** pour arrêter le suivi. Cliquez ou appuyez sur **Arrêter tout** pour suspendre tout le suivi.
* **Historique des fournisseurs** : affiche les fournisseurs ETW activés pendant la session active. Cliquez ou appuyez sur **Activer** pour activer un fournisseur qui a été désactivé. Cliquez ou appuyez sur **Effacer** pour supprimer l’historique.
* **Événements** : liste les événements ETW des fournisseurs sélectionnés sous forme de tableau. Le tableau suivant est mis à jour en temps réel. En dessous du tableau, cliquez sur le bouton **Effacer** pour supprimer tous les événements ETW du tableau. Cela ne désactive pas les fournisseurs. Vous pouvez cliquer sur **Enregistrer dans le fichier** pour exporter vers un fichier CSV en local les événements ETW actuellement collectés.
* **Filtres** : permettent de filtrer les événements ETW collectés par ID, mot clé, niveau, nom du fournisseur, nom de la tâche ou texte. Vous pouvez combiner plusieurs critères :
   1. Pour les critères qui sont appliqués à une même propriété, les événements qui peuvent satisfaire l’un de ces critères sont affichés.
   2. Pour les critères qui sont appliqués à une propriété différente, les événements doivent satisfaire à tous les critères.

Par exemple, vous pouvez spécifier les critères *(Le nom de la tâche contient 'Foo' ou 'Bar') AND (Le texte contient 'erreur' ou 'avertissement')*

### <a name="simulation"></a>Simulation

![Page Simulation dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-16.png)<br>
*Page Simulation dans le portail d’appareil Windows sur Microsoft HoloLens*

Vous permet d’enregistrer et de lire des données d’entrée pour le test.
* **Capturer la salle** : permet de télécharger un fichier de simulation de pièce contenant le maillage de mappage spatial de l’environnement de l’utilisateur. Nommez la pièce, puis cliquez sur **Capturer** pour enregistrer les données sous forme de fichier .xef sur votre PC. Ce fichier de pièce peut être chargé dans l’émulateur HoloLens.
* **Enregistrement** : cochez les flux à enregistrer, nommez l’enregistrement, puis cliquez ou appuyez sur **Enregistrer** pour démarrer l’enregistrement. Effectuez des actions avec votre HoloLens, puis cliquez sur **Arrêter** pour enregistrer les données sous forme de fichier .xef sur votre PC. Ce fichier peut être chargé dans l’émulateur ou l’appareil HoloLens.
  >[!NOTE]
  >La fonctionnalité d’enregistrement est actuellement disponible uniquement sur le HoloLens 1re génération. L’enregistrement n’est pas encore pris en charge sur HoloLens 2, mais la lecture des enregistrements existants est prise en charge.
* **Lecture** : cliquez ou appuyez sur **Charger l’enregistrement** pour sélectionner un fichier xef à partir de votre PC et envoyer les données à HoloLens.
* **Mode contrôle** : sélectionnez **Par défaut** ou **Simulation** dans la liste déroulante, puis cliquez ou appuyez sur le bouton **Définir** pour sélectionner le mode sur le casque HoloLens. Choisissez Simulation pour désactiver les capteurs réels de votre casque HoloLens et utiliser les données simulées à la place. Si vous passez à « Simulation », votre HoloLens ne répondra pas à l’utilisateur réel tant que vous ne serez pas revenu à l’utilisateur « Par défaut ».

### <a name="networking"></a>Mise en réseau

![Page Réseaux dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-17.png)<br>
*Page Réseaux dans le portail d’appareil Windows sur Microsoft HoloLens*

Gère les connexions Wi-Fi sur l’appareil HoloLens.
* **Adaptateurs Wi-Fi** : sélectionnez un adaptateur Wi-Fi et un profil à l’aide des contrôles de la liste déroulante. Cliquez ou appuyez sur **Se connecter** pour utiliser l’adaptateur sélectionné.
* **Réseaux disponibles** : liste les réseaux Wi-Fi auxquels l’appareil HoloLens peut se connecter. Cliquez ou appuyez sur **Actualiser** pour mettre à jour la liste.
* **Configuration IP** : affiche l’adresse IP et d’autres informations concernant la connexion réseau.

### <a name="virtual-input"></a>Entrée virtuelle

![Page Entrée virtuelle dans le portail d’appareil Windows sur Microsoft HoloLens](images/using-windows-portal-img-18.png)<br>
*Page Entrée virtuelle dans le portail d’appareil Windows sur Microsoft HoloLens*

Envoie la saisie au clavier de l’ordinateur distant au casque HoloLens.

Cliquez ou appuyez sur la zone située sous le **clavier virtuel** pour permettre l’envoi de séquences de touches au casque HoloLens. Saisissez du texte dans la **zone de saisie de texte**, puis cliquez ou appuyez sur **Envoyer** pour envoyer les séquences de touches à l’application active.

## <a name="device-portal-rest-apis"></a>API REST du portail d’appareil

Dans le portail d’appareil, tout repose sur les [API REST](device-portal-api-reference.md) que vous pouvez utiliser pour accéder aux données et contrôler votre appareil par programmation, si vous le souhaitez.

## <a name="troubleshooting"></a>Dépannage

### <a name="how-to-fix-the-its-lonely-here-message"></a>Comment résoudre le message « Nous n’avons aucun élément à vous proposer ici »

> [!NOTE]
> En passant de HoloLens 2 à HoloLens (1ère génération), les pages peuvent se retrouver vides si elles ont été utilisées sur HoloLens 2 avant d’être utilisées sur HoloLens (1ère génération).

![Message « Nous n’avons aucun élément à vous proposer ici » dans la page du portail d’appareil](images/using-windows-portal-img-19.png)

1. Sélectionnez **Réinitialiser la disposition** dans le menu en haut à gauche :

![Sélection de Réinitialiser la disposition dans le menu du portail d’appareil](images/using-windows-portal-img-20.png)

2. Cliquez sur **Réinitialiser la disposition** sous le titre **Réinitialiser l’espace de travail**. La page du portail s’actualise automatiquement et affiche votre contenu.

![Sélection de Réinitialiser la disposition dans la page Réinitialiser l’espace de travail](images/using-windows-portal-img-21.png)
