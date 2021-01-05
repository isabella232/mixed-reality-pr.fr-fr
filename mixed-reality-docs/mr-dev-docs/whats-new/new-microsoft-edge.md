---
title: Windows Mixed Reality et le nouveau Microsoft Edge
description: Préparez-vous au nouveau Microsoft Edge dans Windows Mixed Reality. Comprend les modifications à attendre, les mises à jour pour rechercher et les problèmes connus.
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: Edge, nouveau, Web immersif, Microsoft Edge, navigateur, VR, 360, 360 vidéo, 360 Viewer, webxr, webvr
ms.openlocfilehash: 341c7e3d53bd7fb0c569a8acffcf56662c8d2c32
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757437"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality et le nouveau Microsoft Edge

Le [nouveau Microsoft Edge est désormais disponible en téléchargement](https://blogs.windows.com/windowsexperience/?p=173496), mais les clients peuvent également [attendre une prochaine mise à jour pour l’installer avec Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), à la suite d’une approche de déploiement mesurée au cours des prochains mois. 

Grâce à ces nouvelles, **nous souhaitons permettre aux clients du casque Windows Mixed Reality VR de savoir ce qu’il faut attendre du nouveau Microsoft Edge et afficher les mises à jour en attente pour une expérience de navigation améliorée dans Windows Mixed Reality**.

## <a name="introducing-the-new-microsoft-edge"></a>Présentation du nouveau Microsoft Edge

Le nouveau Microsoft Edge [adopte le projet open source de chrome](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) sur le bureau afin de créer une meilleure compatibilité pour les clients et une moindre fragmentation du Web pour les développeurs Web. Il prend également en charge WebXR au lancement, la nouvelle norme pour créer des expériences Web immersifs pour les casques VR, à la place de WebVR.

>[!IMPORTANT]
>Lorsque vous installez Microsoft Edge sur un appareil Windows 10 à jour, il remplace la version précédente (héritée) sur votre PC.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Préparation au nouveau Microsoft Edge

Les clients du casque Windows Mixed Reality VR qui veulent utiliser le nouveau Microsoft Edge dans la réalité mixte doivent **effectuer une mise à niveau vers Windows 10 Version 1903 ou ultérieure pour la prise en charge native des applications Win32 (comme le nouveau Microsoft Edge)** dans la page d’hébergement de la réalité mixte. Vérifiez Windows Update ou [Installez manuellement la dernière version de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Pour une expérience Microsoft Edge optimale dans la réalité mixte, nous vous recommandons également d’attendre des **optimisations clés de la réalité de Windows mixte pour le nouveau Microsoft Edge arrivant avec la mise à jour Cumulative 2020-01 pour Windows 10 Version 1903 (ou ultérieure)**, qui doit être disponible en Windows Update à la fin du janvier.

>[!IMPORTANT]
>Si vous choisissez de télécharger le nouveau Microsoft Edge avant de procéder à ces mises à jour, il y aura des problèmes connus avec son comportement dans Windows Mixed Reality (que vous pouvez voir ci-dessous).

## <a name="known-issues"></a>Problèmes connus

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problèmes connus résolus par la mise à jour cumulative 2020-01 pour Windows 10 version 1903 (ou version ultérieure)

- Le lancement d’une application Win32, y compris le nouveau Microsoft Edge, provoque un blocage rapide de l’affichage du casque.
- La vignette Microsoft Edge disparaît du menu Démarrer Windows Mixed Reality (vous pouvez la trouver dans le dossier « applications classiques »).
- Les fenêtres de la version précédente de Microsoft Edge sont toujours placées autour de la réalité mixte, mais elles ne peuvent pas être utilisées. La tentative d’activation de ces fenêtres démarre Edge dans l’application de bureau.
- La sélection d’un lien hypertexte dans la page d’hébergement de la réalité mixte lance un navigateur Web sur le bureau et non sur la réalité mixte.
- L’application WebVR Showcase est présente dans la réalité mixte, en dépit du fait que WebVR n’est plus pris en charge.
- Améliorations générales apportées au lancement et aux visuels du clavier.

### <a name="monitor-and-input-handling-issues"></a>Problèmes de gestion des entrées et des analyses

Après avoir effectué la mise à jour cumulative 2020-01 pour Windows 10 version 1903 (ou ultérieure), les analyses virtuelles s’affichent en tant que moniteurs physiques génériques dans les **paramètres > système > affichent** pendant les sessions Windows Mixed Reality. Certains clients, en particulier avec plusieurs analyses physiques, peuvent remarquer des problèmes de disposition des postes de travail et de gestion des entrées.

**Pourquoi cela se produit**

La prise en charge des applications Win32 classiques dans Windows Mixed Reality a été introduite dans la [mise à jour de Windows 10 mai 2019](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-may-2019). Pour activer cette prise en charge, vous devez créer un moniteur virtuel pour héberger l’application Win32. À chaque fois qu’une nouvelle application Win32 est lancée, une autre analyse virtuelle doit être créée. Malheureusement, la création d’un moniteur virtuel est une tâche intensive qui peut entraîner un blocage rapide de l’affichage du casque. Les clients nous ont proposé des commentaires qui étaient une expérience inconfortable et perturbatrice. En raison des commentaires et de l’augmentation de l’utilisation des applications Win32, nous avons décidé de pré-allouer trois moniteurs virtuels au démarrage de Windows Mixed Reality. Cela empêche toute interruption et permet aux clients de lancer jusqu’à trois applications Win32 simultanées sans avoir à se figer.

**Solution de contournement**

Depuis que nous avons reçu des commentaires que certains clients, en particulier ceux qui disposent de plusieurs moniteurs physiques, préfèrent désactiver cette pré-allocation du moniteur virtuel. Pour permettre aux clients de contrôler, nous avons activé une solution de contournement qui implique la modification d’une valeur de clé de Registre, disponible avec les mises à jour Windows suivantes :

- 2020-07 version préliminaire de la mise à jour cumulative pour Windows 10 version 2004 (KB4568831)
- 2020-10 version préliminaire de la mise à jour cumulative pour Windows 10 version 1909 (KB4580386)
- 2020-10 version préliminaire de la mise à jour cumulative pour Windows 10 version 1903 (KB4580386)

>[!NOTE]
>La modification des valeurs de clé de Registre est destinée aux utilisateurs expérimentés.

>[!WARNING]
>La désactivation de la pré-allocation du moniteur virtuel peut entraîner un blocage court de votre casque quand vous lancez une application Win32 (telle que la vapeur, le nouveau Microsoft Edge ou Google Chrome) dans Windows Mixed Reality.

Pour désactiver la pré-allocation du moniteur virtuel :
1. Consultez **Windows Update** pour l’une des versions d’évaluation de la mise à jour cumulative de Windows 10 indiquée ci-dessus, puis installez la mise à jour quand elle est disponible. La mise à jour peut se trouver sous **mises à jour facultatives** ou **Options avancées** dans la page Paramètres du Windows Update
2. Lancer l' **éditeur du Registre**
3. Accédez à «HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Si le REG_DWORD « PreallocateVirtualMonitors » n’est pas présent, créez-le en sélectionnant **modifier > nouvelle > valeur DWORD (32 bits)** et en entrant PreallocateVirtualMonitors comme nom.
5. Si la REG_DWORD « PreallocateVirtualMonitors » est présente (ou que vous venez de la créer), double-cliquez sur l’entrée et remplacez « Data values » de 1 (valeur par défaut) par 0 (zéro).
    * VRAI-1
    * FALSE-0

Les analyses virtuelles sont désormais allouées lorsque vous tentez de lancer une application Win32 dans Windows Mixed Reality au lieu de la pré-allouer. Pour réinitialiser cette valeur et réactiver la pré-allocation du moniteur virtuel, renvoyez la valeur DWORD « données de la valeur » à 1.

### <a name="other-known-issues"></a>Autres problèmes connus

-   Les sites Web ouverts dans Windows Mixed Reality sont perdus lorsque le portail de la réalité mixte se ferme. Les fenêtres Microsoft Edge seront conservées dans la place de la réalité mixte.
- Les expériences WebXR, y compris l’extension de visionneuse 360, peuvent ne pas démarrer correctement sur les PC avec une configuration GPU hybride. Vous pouvez contourner ce problème en activant une fonctionnalité en version préliminaire dans le nouveau Microsoft Edge. Accédez à `edge://flags` , recherchez « multi-GPU » et activez l’indicateur appelé **WEBXR multi GPU support**.
-   Les données audio des fenêtres Microsoft Edge ne sont pas spatiales.
-   **Correction de la version d’extension de visionneuse 360 2.3.8**: l’ouverture d’une vidéo 360 à partir de YouTube dans Windows Mixed Reality peut entraîner la déformation de la vidéo dans le casque. Le redémarrage de Edge doit mettre à jour l’extension de visionneuse 360 de façon invisible pour résoudre ce problème. Vous pouvez vérifier la version de l’extension que vous avez en entrant `edge://system/` dans la barre d’adresses et en sélectionnant le bouton de **développement** en regard de « extensions ».
