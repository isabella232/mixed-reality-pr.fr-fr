---
title: Vue d’ensemble de la programmation
description: Découvrez comment accéder aux objets et interfaces maquette à l’aide de scripts.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, maquette, prototypage, réalité mixte, réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935406"
---
# <a name="programming-overview"></a>Vue d’ensemble de la programmation

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logo](../images/MaquetteIcon.png) Vue d’ensemble de la programmation

Microsoft maquette utilise JavaScript (ECMAScript 5,1 avec extensions) basé sur l’interpréteur [JINT](https://github.com/sebastienros/jint) . L’extension `.mqjs` est utilisée pour distinguer les fichiers JavaScript maquette du code JavaScript normal.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Les objets et interfaces maquette sont accessibles et peuvent faire l’objet d’un script à l’aide de l' `Maquette` objet. La documentation sur les interfaces et les objets maquette est fournie dans la référence d’API de maquette.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript est un nouvel ajout et dans le flux, les modifications doivent être attendues. Une documentation plus détaillée et des mises à jour sont bientôt disponibles.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>Actualités sur l’écriture de scripts

* TBD-scripts à la une : exemples/didacticiels
  * 2x images/légende – lien vers la page Actualités

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>Prise en main de MaquetteScript

* Mqjs et JS
* Modèle de programmation
  * Modification et exécution
* Lien vers le flux de travail de programmation
* Lien vers le partage des résultats

## <a name="programming-workflow"></a>Flux de travail de programmation

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* Opération de script
* Opération du débogueur
* Boucle de débogage
* Copier/coller du code ?

## <a name="running-mqjs-scripts"></a>Exécution de scripts. mqjs

<!-- TODO(Stefan): Need screenshot -->
Pour exécuter un fichier MaquetteScript. mqjs, accédez aux fenêtres compagnon de maquette et ouvrez l’onglet script pour rechercher les scripts.

> [!NOTE] 
> Certaines options ne fonctionneront pas encore, car nous n’avons pas fourni les scripts.

## <a name="vscode-editor-workflow"></a>Flux de travail de l’éditeur VSCode

Pour évaluer un script dans maquette à partir de VSCode, l’utilisateur doit connaître deux commandes :

   `CTRL-5` évalue le texte sélectionné ou l’intégralité de la ligne où se trouve le curseur. 

   `CTRL-SHIFT-5` évalue l’ensemble du fichier.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
Le texte est envoyé à maquette, évalué dans l’environnement JavaScript, et le résultat est renvoyé à la console de sortie de VSCode. Cela peut être utilisé comme REPL (Read-eval-Print-Loop).

## <a name="example-first-step"></a>Exemple de première étape

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
Copiez le code suivant dans un fichier dans VSCode :

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
Sélectionnez le code ou uniquement les sections, puis appuyez `CTRL-5` sur Exécuter. Cela doit créer un cube, le placer devant vous et modifier sa couleur.

Il existe d’autres exemples de recherche dans l’extension.

## <a name="sharing-results"></a>Partage des résultats

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
Partage entre les utilisateurs et les équipes
* Projet zip dans le répertoire documents
* Copier le projet dans le partage de fichiers
* Ajout de l’emplacement de fichier des envois de partage d’équipe à l’équipe maquette

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* Includes, référence à du code ailleurs avec des chemins d’accès relatifs/absolus, modules
* Bibliotheque?
* Prise en charge du runtime
* Externes non résolus-comportement lorsque des entrées manquent/se bloquent
* Pouvez-vous ajouter/modifier/observer le script associé à des objets spécifiques ?
  * Pouvons-nous copier/coller ce script ailleurs ?
  * Qu’en est-il des propriétés de l’objet ?
  * Vous nommez des objets dans ma scène ? (attribution d’un nouveau nom à un script)
  * Mot clé THIS ou SELF pour le script associé à un objet
  * Si je clique avec le bouton droit sur un objet, puis-je voir le code qui lui est associé (et sa hiérarchie)
  * Puis-je sélectionner dans l’interface utilisateur et être affiché dans le code de VSCode ?
  * Comment conserver le code associé à un objet « ensemble » dans le fichier source du script ?
  * Placer la fenêtre des propriétés d’un objet quand je clique dessus ? Dans VR et dans l’onglet principal ?
* Problèmes de sécurité
* Test : peut être TBD, mais nous pourrions suggérer une vidéo ou une manipulation de trame par script
* Si nous disposons d’un mécanisme de création de rapports de bogues, nous pouvons rendre celui-ci accessible via le script pour les autres ( ?)... ultérieurement
* Déploiement : Comment « partager » le résultat, le package en tant qu’EXE
* Exécution/contrôle d’une démonstration ou d’une spectating/surveillance
* Mode lecteur
* Un segment peut-il vous permettre de créer des « composants » pour le partage ? (peut être TBD)
  * Existe-t-il #include ? Cela gère pure JS que je suppose mais peut avoir des conflits d’espace de noms.
  * Y a-t-il quelque chose que nous pourrions faire pour qu’un maquette incorpore d’autres maquette avec des objets nommés pour correspondre au code JS ?
