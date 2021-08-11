---
title: Langage principal
description: En savoir plus sur les détails du langage de base de maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototypage, réalité mixte, réalité virtuelle, VR, MR, commentaires, Hub de commentaires, bogues
ms.openlocfilehash: 290b1442c3cc7fed10b315f4beeebfe2eab4a775d4909d5411c651362e24d94e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197399"
---
# <a name="maquettescript-core-language-details"></a>Détails du langage de base MaquetteScript

<!-- TODO(Harrison): Need consolidated logo with text -->
![Maquette logo ](../images/MaquetteIcon.png) MaquetteScript Core Language Details

## <a name="accessing-maquette-object-and-namespace"></a>Accès à l' `Maquette` objet et à l’espace de noms

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette expose les interfaces et les objets internes dans JavaScript par le biais de l' `Maquette` objet et de ses enfants. Cette fonctionnalité est décrite dans la documentation relative à l' [objet maquette et](https://www.maquette.ms/doc_staging/objects/Maquette.html) à l’espace de noms. 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
L' `Maquette` objet a des fonctions de niveau supérieur pour faciliter l’interaction avec maquette lui-même et faciliter la résolution des problèmes. Cela est décrit dans la documentation de [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).

## <a name="maquette-startup-and-loading"></a>Démarrage et chargement de maquette

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette charge et évalue des fichiers JavaScript spécifiques pour activer la configuration, l’installation et l’initialisation aux moments suivants :

Lors du démarrage de maquette :
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

Chaque fois qu’un projet est chargé :
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

Les projets chargent leurs scripts de projet respectifs :
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>Implémentation JavaScript

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
L’interpréteur JavaScript utilisé dans maquette est basé sur [JINT](https://github.com/sebastienros/jint). JINT est compatible ECMAScript 5,1 et prend en charge des [extensions supplémentaires d’ECMAScript 6](https://github.com/sebastienros/jint/issues/343). 

L’extension `.mqjs` est utilisée pour distinguer les fichiers JavaScript maquette du code JavaScript normal.

## <a name="see-also"></a>Voir aussi 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->