---
title: Publication sur le Microsoft Store
description: Découvrez comment empaqueter, certifier et publier vos applications de réalité mixte Unreal sur le Microsoft Store.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, documentation, guides, fonctionnalités, casque de réalité mixte, casque de réalité mixte Windows, casque de réalité virtuelle, publication, distribution, Microsoft Store
ms.openlocfilehash: 3a975d9c66e64f56919163e9d3aa65a3126d6379
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583594"
---
# <a name="publishing-to-the-microsoft-store"></a>Publication sur le Microsoft Store

Quand vous êtes prêt à lancer votre application, vous devez mettre à jour quelques paramètres du projet avant de la soumettre au Microsoft Store. Tous ces paramètres ont des valeurs par défaut, que vous devez toutefois changer pour la production afin de mieux représenter l’application.

## <a name="project-settings-for-the-store-packaging"></a>Paramètres du projet pour l’empaquetage du Store

1. Tout d’abord, sélectionnez **Paramètres du projet > Description** et mettez à jour les informations sur le jeu et son éditeur : 
    * Le **nom du jeu** apparaît dans la vignette de l’application sur le HoloLens.
    * Le **nom unique de l’entreprise**  est utilisé lors de la génération du certificat de projet et doit être au format : 
        * **CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName** :

![Capture d’écran de l’éditeur Unreal avec la section de description développée dans les paramètres du projet](images/unreal-publishing-img-01.png)

2. Développez la section **HoloLens** des paramètres du projet et mettez à jour les ressources d’empaquetage.  Ces noms de ressources seront indiquées dans la page du Store de l’application :

![Capture d’écran de l’éditeur Unreal avec la section d’empaquetage développée dans les paramètres du projet](images/unreal-publishing-img-02.png)

3. Développez la section **Images** et mettez à jour les images du Store par défaut avec les textures qui représentent l’application du Store.  Cochez éventuellement la case **Logo 3D** pour charger un fichier glb à utiliser comme cube 3D lors du lancement de l’application :

![Capture d’écran de l’éditeur Unreal avec la section des images développée dans les paramètres du projet](images/unreal-publishing-img-03.png)

4. Enfin, sélectionnez **Générer** pour générer un certificat de signature à partir du nom du projet et du nom unique de l’entreprise.  
    * Définissez une **couleur d’arrière-plan de vignette**, qui va remplacer tous les pixels transparents dans les images du Store.
    * Développez la liste déroulante et activez **Utiliser l’environnement du Windows Store** pour une exécution sur des appareils verrouillés par le Store, non déverrouillés par le développeur.

![Capture d’écran de l’éditeur Unreal avec la section de génération de certificats développée dans les paramètres du projet](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a>Programme d’installation d’application facultatif

Un fichier de programme d’installation d’application peut être créé à partir de **Paramètres du projet > HoloLens**, lequel peut servir à distribuer l’application en dehors du Store.  Cochez la case permettant de **créer un programme d’installation d’application** et définissez une URL ou un chemin réseau où stocker le fichier appxbundle du jeu.  

![Capture d’écran de l’éditeur Unreal avec la section du programme d’installation d’application développée dans les paramètres du projet](images/unreal-publishing-img-05.png)

Quand l’application est empaquetée, les fichiers appxbundle et appinstaller sont générés.  Chargez le fichier appxbundle sur l’URL d’installation, puis lancez le fichier appinstaller pour installer l’application à partir de l’emplacement réseau.

## <a name="windows-app-certification-kit"></a>Kit de certification des applications Windows

Le SDK Windows 10 est fourni avec le kit de certification des applications Windows (WACK) pour valider les problèmes courants susceptibles d’affecter le chargement d’un package dans le Store.  Vous pouvez trouver le WACK dans le répertoire des kits Windows, généralement sous le chemin suivant : 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. Une fois votre fichier appx est empaqueté pour la publication, exécutez **appcertui.exe** et suivez les invites pour analyser le fichier appx :

![Capture d’écran de l’application sélectionnée à des fins de validation dans le kit de certification des applications Windows](images/unreal-publishing-img-06.png)

2. Sélectionnez **Valider l’application du Store** :

![Capture d’écran de la sélection de la validation dans le kit de certification des applications Windows](images/unreal-publishing-img-07.png)

3. Recherchez le fichier appx dans la section supérieure et sélectionnez **Suivant** :

![Capture d’écran de la sélection des tests dans le kit de certification des applications Windows](images/unreal-publishing-img-08.png)

4. Sélectionnez **Suivant** pour exécuter les tests et créer un rapport :
    * Tous les tests disponibles exécutables sur l’ordinateur hôte sont activés par défaut.

![Capture d’écran de la progression de la validation de l’application dans le kit de certification des applications Windows](images/unreal-publishing-img-09.png)

5. Attendez la fin des tests. Une fois l’opération terminée, la fenêtre finale indique une réussite ou un échec, que vous pouvez consulter dans le rapport enregistré.

![Capture d’écran des résultats du rapport final dans le kit de certification des applications Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a>Échec du WACK connu avec la version 4.25

Le plug-in Windows Mixed Reality dans Unreal 4.25 fait échouer le WACK, car certains binaires x64 sont inclus lors de l’empaquetage pour HoloLens. L’échec ressemble à ceci :

![Capture d’écran d’un échec en raison de l’analyseur binaire et des API prises en charge par le kit de certification des applications Windows](images/unreal-publishing-img-11.png)

Pour résoudre le problème :
1. Accédez à la racine de l’installation ou du répertoire source Unreal en ouvrant un projet Unreal et cliquez avec le bouton droit sur l’icône Unreal dans la barre des tâches.
2. Cliquez avec le bouton droit sur UE4Editor, sélectionnez Propriétés, puis accédez au chemin dans l’entrée **Emplacement** :

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. Dans **WindowsMixedRealityHMD.Build.cs**, modifiez la **ligne 32** suivante :

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

to:

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. Fermez Unreal, rouvrez le projet, puis réempaquetez pour HoloLens.  Réexécutez le WACK et l’erreur sera supprimée. 

## <a name="see-also"></a>Voir aussi

* [Envoi d’une application au Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Kit de certification des applications Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [Créer un fichier Programme d’installation d’application manuellement](/windows/msix/app-installer/how-to-create-appinstaller-file)