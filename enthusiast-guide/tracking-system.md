---
title: Fonctionnement du suivi intérieur-extérieur
description: informations sur le système de suivi à l’intérieur de l’appareil photo, utilisé dans Windows Mixed Reality casques.
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, inside-out, inside out, suivi, appareil photo
ms.openlocfilehash: 579ef23c1eca2c184d07878c4e71ce298c5ad9922255b5e43643458a256b61bf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197863"
---
# <a name="inside-out-tracking"></a>Suivi intérieur-extérieur

## <a name="how-does-inside-out-tracking-work"></a>Comment fonctionne le suivi à l’intérieur de la sortie ?

**Réponse rapide :** le système de suivi utilise deux caméras de faible résolution visibles pour observer les fonctionnalités de votre environnement. Les appareils photo fusionne ensuite les informations avec les données IMU pour déterminer une position précise de l’appareil dans votre environnement.

**Plus de détails :** Le système de suivi utilise deux caméras noires et blanches de basse résolution pour identifier les fonctionnalités de votre environnement en clair. Le système effectue la triangulation de sa position en fonction des fonctionnalités observées, qui complètent ensuite les informations en fusionnant les données IMU à taux élevé afin de produire une estimation de pose continue pour le HMD dans votre environnement. Les informations de pose sont utilisées par les deux applications pour restituer une scène et le système pour corriger ce rendu pour toute prédiction incorrecte dans le temps et la position. Votre PC stocke les informations d’environnement afin que le système de suivi puisse rappeler des données spécifiques à l’environnement, comme l’emplacement physique des limites de la salle. Si vous utilisez votre appareil dans plusieurs pièces, vous pouvez configurer différentes limites dans chaque pièce et le système de suivi peut rappeler la limite spécifique pour la salle spécifique.

étant donné que le suivi sur Windows Mixed Reality des casques immersifs fonctionne comme le suivi sur [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens), cette vidéo peut vous être utile :

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>De quoi ai-je besoin pour faire fonctionner le suivi ?

Il y a deux préoccupations à prendre en compte pour garantir le bon fonctionnement du suivi :
1. Vérifiez que votre ordinateur répond à la configuration requise pour exécuter Windows Mixed Reality. si votre ordinateur répond à la configuration minimale requise pour Windows Mixed Reality, le suivi disposera de suffisamment de ressources pour s’exécuter correctement sur votre ordinateur.
2. Assurez-vous que votre environnement est adapté au type de suivi visuel que l’appareil utilise. Vous devez utiliser l’appareil dans un environnement avec suffisamment de lumière. Étant donné que l’appareil fonctionne en observant votre environnement dans une lumière visible, il doit y avoir suffisamment de lumière pour que l’environnement puisse être observé. Il doit également y avoir suffisamment de fonctionnalités visuelles distinctives (en d’autres termes, décorations, points de contraste, etc.) pour que le système de suivi fonctionne.

## <a name="how-much-light-is-enough-light"></a>Quelle est la quantité de lumière suffisante ?

Si vous pouvez vous déplacer confortablement dans l’environnement sans vous sentir trop sombre, et si vous pouvez observer les fonctionnalités d’une autre personne à travers la pièce, le système de suivi est probablement suffisamment clair. Gardez à l’esprit qu’il y a trop de lumière, si vous regardez directement le soleil, les caméras peuvent être saturées et ne suivent pas de fiabilité. 

## <a name="what-is-the-recommended-number-of-environmental-features"></a>Quel est le nombre recommandé de fonctionnalités environnementales ?

Le produit a été conçu pour fonctionner dans des environnements normaux. Envisagez l’expérience de pensée suivante : Si vous étiez dans une salle vide avec des murs blancs, un plafond blanc et un plancher blanc, le système de suivi ne trouvera aucune fonctionnalité à suivre et échouait. Si vous étiez dans une salle couverte par le travail artistique et la décoration, le système de suivi trouvera de nombreuses fonctionnalités à suivre et fonctionnerait bien. Généralement, les maisons et les bureaux décorés sont généralement démontrés comme ayant suffisamment de détails pour assurer le suivi.

## <a name="how-fast-can-i-move-with-the-device"></a>Quelle est la vitesse de déplacement de l’appareil ?

L’appareil est conçu pour prendre en charge le mouvement en-delà de ce qui est normalement rencontré par le mouvement de la tête humaine. N’hésitez pas à vous déplacer. Gardez à l’esprit que vous avez réduit la connaissance de votre environnement physique quand vous êtes dans un casque immersif, vous devez donc vous assurer que vous vous déplacez en toute sécurité dans votre environnement.

## <a name="where-will-tracking-not-work"></a>Où le suivi ne fonctionne-t-il pas ?

Le suivi ne fonctionne pas dans une pièce sombre où les caméras ne peuvent pas voir suffisamment de fonctionnalités en raison d’une faible luminosité. Le suivi ne fonctionnera pas correctement (ou parfois du tout) dans le déplacement de véhicules tels que les avions, les bus, les trains, les voitures ou les ascenseurs. Le suivi peut également échouer dans des situations où la légère ou la légère différence est importante. Par exemple, s’il existe un flux direct de soleil dans une pièce, les caméras peuvent réduire l’exposition pour réduire la saturation et ne voient pas les fonctionnalités naturelles normales. Il est recommandé d’utiliser un éclairage relativement même, et si vous devez plisser ou trouver des choses peu de confort, le système de suivi peut ne pas s’avérer très efficace. 

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>Quelle est la différence entre 3DOF et 6DOF ?

Tout d’abord, le DDL est concis pour les « degrés de liberté ». En ce qui concerne les systèmes de suivi, cela signifie les degrés ou les types de mouvement qui peuvent être détectés. Ces mouvements sont divisés en deux catégories principales : « rotation » et « rotation avec translation ». 3DOF fait référence à 3 degrés de liberté et représente des rotations sur chaque axe. En d’autres termes, le suivi 3DOF vous permet de regarder à gauche/à droite, vers le haut/vers le haut et de faire pivoter le côté de votre tête (Roll). Vous ne pouvez pas traduire ou avancer/reculer dans 3DOF. 6DOF est limité à 6 degrés de liberté. Il s’appuie sur les rotations de 3DOF et les ajoute aux traductions informatiques. Cela signifie que vous pouvez avancer/reculer, Strafe vers la gauche/droite et Crouch. Le suivi de trois DDL est le type de suivi que vous trouverez généralement sur un téléphone ou un produit VR mobile, tandis que 6DOF se trouve sur des plateformes plus puissantes VR. Certaines expériences sont adaptées à 3DOF et n’autorisent que le mouvement 3DOF (rotations), même si l’appareil prend en charge le suivi 6DOF. Un exemple de ce qui suit serait de regarder une vidéo 360 dans Windows Mixed Reality. La vidéo vous permettra de vous faire une recherche, mais ne vous permettra pas de vous familiariser avec votre environnement.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>Les choses sont instables ou saccadées dans mon casque. Mon suivi ne fonctionne-t-il pas ?

Il existe deux sources de ce type d’erreur. Il est important d’attribuer ce que vous observez à la bonne cause pour qu’elle puisse être traitée. Consultez la section [résolution des problèmes](tracking.md) pour mieux comprendre pourquoi cela peut se produire.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>Puis-je mettre en Windows Mixed Reality ma propre technologie de suivi ?

Cette fonctionnalité n’est pas prise en charge actuellement.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>Pourquoi est-ce que je vois une interface utilisateur indiquant « impossible de trouver votre limite ? »

Étant donné que la limite de sécurité est spécifique à un emplacement physique, si vous utilisez l’appareil dans un emplacement différent, le système ne peut pas trouver les limites. En outre, une fois que vous avez configuré votre limite, le système le recherchera toujours, même si vous utilisez l’appareil dans un emplacement physique différent. Vous verrez cette interface utilisateur chaque fois que vous utilisez l’appareil dans un emplacement différent et que vous n’avez pas encore configuré de limite à cet emplacement. Vous pouvez configurer des limites dans chaque emplacement où vous utilisez l’appareil, et l’appareil rappellera vos limites spécifiques à l’emplacement.

Si vous utilisez l’appareil dans un emplacement où vous avez déjà configuré une limite et que l’appareil ne peut toujours pas le trouver, vous pouvez configurer une nouvelle limite ou effacer toutes les données d’environnement pour supprimer toutes les limites de l’appareil. Consultez la section [résolution des problèmes](tracking.md) pour comprendre pourquoi le système ne peut pas trouver vos limites et les étapes à suivre pour le corriger.

## <a name="how-do-i-set-up-tracking"></a>Comment faire configurer le suivi ?

le suivi dans Windows Mixed Reality est simple à utiliser, aucune infrastructure ou configuration n’est requise. Si vous avez choisi, vous pouvez configurer une limite virtuelle à utiliser. Pour plus d’informations, consultez la section relative à la [configuration de vos limites](set-up-windows-mixed-reality.md#set-up-your-room-boundary) .

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Comment faire effacer les données de suivi et d’environnement ?

Le système de suivi stocke des données d’environnement afin qu’il puisse rappeler l’emplacement physique réel des choses comme vos limites de sécurité. Ces informations, y compris vos limites de sécurité, peuvent être supprimées à tout moment. Si ces informations sont supprimées, le système ne reconnaîtra plus votre espace ou n’aurez plus à vous rappeler vos limites de sécurité. Si vous souhaitez utiliser des limites de sécurité après avoir effacé les données de l’environnement, vous devrez les reconfigurer. Consultez la section relative à la [configuration de votre limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) pour configurer une nouvelle limite. pour supprimer toutes ces données, ouvrez Paramètres, accédez à « réalité mixte », puis sélectionnez la section environnement du menu de gauche. Sélectionnez le bouton intitulé « effacer les données d’environnement » pour supprimer tous les environnements et données de suivi.

## <a name="see-also"></a>Voir aussi
* [Résolution des problèmes liés au système de suivi](tracking.md)
* [Contrôleurs de mouvement](controllers-in-wmr.md)
* [Votre accueil Windows Mixed Reality](your-mixed-reality-home.md)
* [Utilisation de jeux et d’applications dans Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
