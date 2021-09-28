---
title: Windows Mixed Reality et le nouveau Microsoft Edge
description: découvrez les nouvelles Microsoft Edge pour la réalité mixte, y compris les éléments à attendre, les mises à jour à consulter et les problèmes connus.
author: mattzmsft
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: Edge, nouveau, Web immersif, Microsoft Edge, navigateur, VR, 360, 360 vidéo, 360 Viewer, webxr, webvr
ms.openlocfilehash: ca849f63d2a755639bedba68c47e419528006a6d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148647"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>nouvelle Microsoft Edge pour Windows Mixed Reality

le [nouveau Microsoft Edge est désormais disponible en téléchargement](https://blogs.windows.com/windowsexperience/?p=173496), mais les clients peuvent également [attendre une prochaine mise à jour pour l’installer avec Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), à la suite d’une approche de déploiement mesurée au cours des prochains mois. 

grâce à cette actualité, **nous souhaitons permettre aux clients Windows Mixed Reality VR de recevoir des informations sur les nouveaux Microsoft Edge et d’afficher les mises à jour en attente pour une expérience de navigation améliorée dans Windows Mixed Reality**.

## <a name="introducing-the-new-microsoft-edge"></a>Présentation du nouveau Microsoft Edge

le nouveau Microsoft Edge [adopte le Chromium projet open source](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) sur le bureau afin de créer une meilleure compatibilité pour les clients et une moindre fragmentation du web pour les développeurs web. Il prend également en charge WebXR au lancement, la nouvelle norme pour créer des expériences Web immersifs pour les casques VR, à la place de WebVR.

>[!IMPORTANT]
>lorsque vous installez Microsoft Edge sur un appareil Windows 10 à jour, il remplace la version précédente (héritée) sur votre PC.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Préparez-vous à la nouvelle Microsoft Edge

Windows Mixed Reality les clients du casque VR qui veulent utiliser le nouveau Microsoft Edge dans la réalité mixte doivent **effectuer la mise à niveau vers Windows 10 Version 1903 ou ultérieure pour la prise en charge native des applications Win32 (comme le nouveau Microsoft Edge)** dans la page d’hébergement de la réalité mixte. vérifiez Windows Update ou [installez manuellement la dernière version de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

pour une expérience de Microsoft Edge optimale dans la réalité mixte, nous vous recommandons également d’attendre des **optimisations de clé Windows Mixed Reality pour le nouveau Microsoft Edge arrivant avec la mise à jour Cumulative 2020-01 pour Windows 10 Version 1903 (ou ultérieure)**, qui doit être disponible dans Windows Update à la fin du janvier.

>[!IMPORTANT]
>si vous choisissez de télécharger le nouveau Microsoft Edge avant d’effectuer ces mises à jour, il y aura des problèmes connus avec son comportement dans Windows Mixed Reality (ce que vous pouvez voir ci-dessous).

## <a name="known-issues"></a>Problèmes connus

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>problèmes connus résolus par la mise à jour Cumulative 2020-01 pour Windows 10 Version 1903 (ou version ultérieure)

- le lancement d’une application Win32, y compris la nouvelle Microsoft Edge, provoque un blocage rapide de l’affichage du casque.
- la vignette Microsoft Edge disparaît du menu Démarrer de Windows Mixed Reality (vous pouvez la trouver dans le dossier « applications classiques »).
- les Windows des Microsoft Edge précédentes sont toujours placées autour de la réalité mixte, mais elles ne peuvent pas être utilisées. La tentative d’activation de ces fenêtres démarre Edge dans l’application de bureau.
- La sélection d’un lien hypertexte dans la page d’hébergement de la réalité mixte lance un navigateur Web sur le bureau et non sur la réalité mixte.
- L’application WebVR Showcase est présente dans la réalité mixte, en dépit du fait que WebVR n’est plus pris en charge.
- Améliorations générales apportées au lancement et aux visuels du clavier.

### <a name="monitor-and-input-handling-issues"></a>Problèmes de gestion des entrées et des analyses

après avoir effectué la mise à jour Cumulative 2020-01 pour Windows 10 Version 1903 (ou ultérieure), les analyses virtuelles s’affichent en tant que moniteurs physiques génériques dans **Paramètres > système > s’afficher** pendant les sessions de Windows Mixed Reality. Certains clients, en particulier avec plusieurs analyses physiques, peuvent remarquer des problèmes de disposition des postes de travail et de gestion des entrées.

**Pourquoi cela se produit**

la prise en charge des applications Win32 classiques dans Windows Mixed Reality a été introduite avec le [Mise à jour de mai 2019 de Windows 10](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019). Pour activer cette prise en charge, vous devez créer un moniteur virtuel pour héberger l’application Win32. À chaque fois qu’une nouvelle application Win32 est lancée, une autre analyse virtuelle doit être créée. Malheureusement, la création d’un moniteur virtuel est une tâche intensive qui peut entraîner un blocage rapide de l’affichage du casque. Les clients nous ont proposé des commentaires qui étaient une expérience inconfortable et perturbatrice. En raison des commentaires et de l’augmentation de l’utilisation des applications Win32, nous avons décidé de préallouer trois analyses virtuelles au cours du démarrage de Windows Mixed Reality. Cela empêche toute interruption et permet aux clients de lancer jusqu’à trois applications Win32 simultanées sans avoir à se figer.

**Solution de contournement**

Depuis que nous avons reçu des commentaires que certains clients, en particulier ceux qui disposent de plusieurs moniteurs physiques, préfèrent désactiver cette pré-allocation du moniteur virtuel. pour permettre aux clients de contrôler, nous avons activé une solution de contournement qui implique la modification d’une valeur de clé de registre, disponible avec les mises à jour de Windows suivantes :

- 2020-07 Version préliminaire de la mise à jour Cumulative pour Windows 10 Version 2004 (KB4568831)
- 2020-10 Version préliminaire de la mise à jour Cumulative pour Windows 10 Version 1909 (KB4580386)
- 2020-10 Version préliminaire de la mise à jour Cumulative pour Windows 10 Version 1903 (KB4580386)

>[!NOTE]
>La modification des valeurs de clé de Registre est destinée aux utilisateurs expérimentés.

>[!WARNING]
>la désactivation de la pré-allocation du moniteur virtuel peut entraîner un blocage court de votre casque quand vous lancez une application Win32 (telle que la vapeur, la nouvelle Microsoft Edge ou Google Chrome) dans Windows Mixed Reality.

Pour désactiver la pré-allocation du moniteur virtuel :
1. vérifiez **Windows Update** pour l’une des Windows 10 versions préliminaires de mise à jour Cumulative mentionnées ci-dessus et installez la mise à jour quand elle est disponible. la mise à jour peut se trouver sous **mises à jour facultatives** ou **options avancées** dans la page paramètres du Windows Update
2. Lancer l' **éditeur du Registre**
3. Accédez à «HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Si le REG_DWORD « PreallocateVirtualMonitors » n’est pas présent, créez-le en sélectionnant **modifier > nouvelle > valeur DWORD (32 bits)** et en entrant PreallocateVirtualMonitors comme nom.
5. Si la REG_DWORD « PreallocateVirtualMonitors » est présente (ou que vous venez de la créer), double-cliquez sur l’entrée et remplacez « Data values » de 1 (valeur par défaut) par 0 (zéro).
    * VRAI-1
    * FALSE-0

les analyses virtuelles sont désormais allouées lorsque vous tentez de lancer une application Win32 dans Windows Mixed Reality au lieu de procéder à la pré-allocation. Pour réinitialiser cette valeur et réactiver la pré-allocation du moniteur virtuel, renvoyez la valeur DWORD « données de la valeur » à 1.

### <a name="other-known-issues"></a>Autres problèmes connus

-   l’Audio de Microsoft Edge windows n’est pas spatial.

## <a name="see-also"></a>Voir aussi

* [Présentation de WebXR](../develop/javascript/webxr-overview.md)