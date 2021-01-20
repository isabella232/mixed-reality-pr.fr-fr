---
title: Utilisation de Microsoft Edge dans Windows Mixed Reality
description: Préparez-vous au nouveau Microsoft Edge dans Windows Mixed Reality. Comprend les modifications à attendre, les mises à jour pour rechercher et les problèmes connus.
author: mattzmsft
ms.author: mazeller
ms.date: 11/11/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, famille, naviguer, découvrir, applications, jeux, Microsoft Edge, chrome, Edge, 360, 360 vidéo, 360 Viewer
ms.openlocfilehash: 26691dd3cf1b8e620373ef150de61cd2c7f461db
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581304"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality et le nouveau Microsoft Edge

Le [nouveau Microsoft Edge](https://www.microsoft.com/edge) est disponible au téléchargement et a commencé à être déployé automatiquement pour les clients via Windows Update. 

Le nouveau Microsoft Edge [adopte le projet open source de chrome](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) sur le bureau. Cela permet de créer une meilleure compatibilité pour les clients et de réduire la fragmentation pour les développeurs Web. Il prend également en charge WebXR au lancement, qui est la nouvelle norme pour créer des expériences Web immersifs pour les casques VR, à la place de WebVR.

>[!IMPORTANT]
>Lorsque vous installez Microsoft Edge sur un appareil Windows 10 à jour, il remplace la version précédente (héritée) sur votre PC.

## <a name="installing-the-new-microsoft-edge"></a>Installation du nouveau Microsoft Edge 

Avant d’installer le nouveau Microsoft Edge, **effectuez une mise à niveau vers Windows 10 Version 1903 ou ultérieure pour la prise en charge d’applications Win32 natives comme le nouveau Microsoft Edge** dans Windows Mixed Reality. Vérifiez Windows Update ou [Installez manuellement la dernière version de Windows 10](https://www.microsoft.com/software-download/windows10).

Une fois que vous avez Windows 10 version 1903 ou ultérieure, vous êtes prêt pour le nouveau Microsoft Edge ! Le nouveau Microsoft Edge est déployé via Windows Update, mais vous pouvez installer manuellement le nouveau Microsoft Edge à partir du [site Web Microsoft Edge](https://www.microsoft.com/edge) si vous le souhaitez.

>[!IMPORTANT]
>Le nouveau Microsoft Edge démarre avec la prise en charge de WebXR, la nouvelle norme pour créer des expériences Web immersifs pour les casques VR. Lorsque vous installez le nouveau Microsoft Edge, vous ne pourrez plus lire les expériences WebVR dans Microsoft Edge. 

## <a name="known-issues"></a>Problèmes connus

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problèmes connus résolus par la mise à jour cumulative 2020-01 pour Windows 10 version 1903 (ou version ultérieure)

- Le lancement d’une application Win32, y compris le nouveau Microsoft Edge, provoque un blocage rapide de l’affichage du casque.
- La vignette Microsoft Edge disparaît du menu Démarrer Windows Mixed Reality (vous pouvez la trouver dans le dossier « applications classiques »).
- Les fenêtres de la version précédente de Microsoft Edge sont toujours placées autour de la réalité mixte, mais elles ne peuvent pas être utilisées. La tentative d’activation de ces fenêtres démarre Edge dans l’application de bureau.
- La sélection d’un lien hypertexte dans la page d’hébergement de la réalité mixte lance un navigateur Web sur le bureau et non sur la réalité mixte.
- L’application WebVR Showcase est présente dans la réalité mixte, en dépit du fait que WebVR n’est plus pris en charge.
- Améliorations générales apportées au lancement et aux visuels du clavier.

### <a name="monitor-and-input-handling-issues"></a>Problèmes de gestion des entrées et des analyses

Après avoir effectué la mise à jour cumulative 2020-01 pour Windows 10 version 1903 ou ultérieure, les analyses virtuelles s’affichent sous la forme de moniteurs physiques génériques dans les **paramètres > système > affichent** pendant les sessions Windows Mixed Reality. Certains clients, en particulier ceux qui disposent de plusieurs moniteurs physiques, peuvent remarquer des problèmes de disposition des postes de travail et de gestion des entrées.

**Pourquoi cela se produit**

La prise en charge des applications Win32 classiques dans Windows Mixed Reality a été introduite dans la [mise à jour de Windows 10 mai 2019](/windows/mixed-reality/release-notes-may-2019). Pour activer cette prise en charge, vous devez créer un moniteur virtuel pour héberger l’application Win32. À chaque fois qu’une nouvelle application Win32 est lancée, une autre analyse virtuelle doit être créée. Malheureusement, la création d’un moniteur virtuel est une tâche intensive qui peut entraîner un blocage rapide de l’affichage du casque. Les clients ont proposé des commentaires que l’expérience était inconfortable et perturbatrice. En raison de ces commentaires, en plus de l’utilisation accrue des applications Win32, nous avons décidé de pré-allouer trois analyses virtuelles au démarrage de Windows Mixed Reality pour éviter cette interruption et permettre aux clients de lancer jusqu’à trois applications Win32 simultanées sans avoir à se figer.

**Solution de contournement**

Depuis que nous avons reçu des commentaires que certains clients, en particulier ceux qui disposent de plusieurs moniteurs physiques, préfèrent désactiver cette pré-allocation du moniteur virtuel. Pour offrir davantage de contrôle aux clients, nous avons activé une solution de contournement qui implique la modification d’une valeur de clé de Registre, disponible avec les mises à jour Windows suivantes :

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

-   Les sites Web ouverts dans Windows Mixed Reality sont perdus lorsque le portail de réalité mixte se ferme, bien que les fenêtres Microsoft Edge restent là où elles ont été placées dans la page d’hébergement de la réalité mixte.
- Les expériences WebXR, y compris l’extension de visionneuse 360, peuvent ne pas démarrer correctement sur les PC avec une configuration GPU hybride. Vous pouvez contourner ce problème en activant une fonctionnalité en version préliminaire dans le nouveau Microsoft Edge. Accédez à `edge://flags` , recherchez « multi-GPU » et activez l’indicateur appelé **WEBXR multi GPU support**.
-   Les données audio des fenêtres Microsoft Edge ne sont pas spatiales.
-   **Correction de la version d’extension de visionneuse 360 2.3.8**: l’ouverture d’une vidéo 360 à partir de YouTube dans Windows Mixed Reality peut entraîner la déformation de la vidéo dans le casque. Le redémarrage de Edge doit mettre à jour l’extension de visionneuse 360 de façon invisible pour résoudre ce problème. Vous pouvez vérifier la version de l’extension que vous avez en entrant `edge://system/` dans la barre d’adresses et en sélectionnant le bouton de **développement** en regard de « extensions ».