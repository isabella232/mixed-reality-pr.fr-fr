---
title: Fonctionnement du suivi intérieur-extérieur
description: Informations sur le système de suivi à l’intérieur de l’appareil photo, utilisé dans les casques de Windows Mixed Reality.
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, Inside-Out, Inside Out, Tracking, Camera
ms.openlocfilehash: a91b5fba399e9bb328fd579811a64aee03b49efd
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174336"
---
# <a name="inside-out-tracking"></a>Suivi interne

## <a name="how-does-inside-out-tracking-work"></a>Comment fonctionne le suivi à l’intérieur de la sortie ?

**Réponse rapide :** le système de suivi utilise deux caméras de faible résolution visibles pour observer les fonctionnalités dans votre environnement, et fusionne ces informations avec les données IMU pour déterminer une position précise de l’appareil dans votre environnement.

**Plus de détails :** Le système de suivi utilise deux caméras noires et blanches de basse résolution pour identifier les fonctionnalités de votre environnement en clair. Le système effectue la triangulation de sa position en fonction des fonctionnalités observées et complète ces informations en fusionnant les données IMU à taux élevé afin de produire une estimation de pose continue pour les HMD dans votre environnement. Les informations de pose sont utilisées par les deux applications pour restituer une scène et le système pour corriger ce rendu pour toute prédiction incorrecte dans le temps et la position. Les informations de votre environnement sont stockées sur votre ordinateur afin que le système de suivi puisse rappeler des données spécifiques à l’environnement, telles que l’emplacement physique de la limite dans votre salle. Si vous utilisez votre appareil dans plusieurs salles, vous pouvez configurer différentes limites dans chaque pièce et le système de suivi pourra rappeler la limite spécifique pour la salle spécifique.

Étant donné que le suivi sur les casques immersifs de la réalité Windows Mixed fonctionne comme le suivi sur [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens), cette vidéo peut vous être utile :

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>De quoi ai-je besoin pour faire fonctionner le suivi ?

Il y a deux préoccupations à prendre en compte pour garantir le bon fonctionnement du suivi :
1. Vérifiez que votre ordinateur répond à la configuration requise pour exécuter Windows Mixed Reality. Si votre ordinateur répond à la configuration minimale requise pour Windows Mixed Reality, le suivi disposera de suffisamment de ressources pour s’exécuter correctement sur votre ordinateur.
2. Assurez-vous que votre environnement est adapté au type de suivi visuel que l’appareil utilise. Vous devez utiliser l’appareil dans un environnement avec suffisamment de lumière. Étant donné que l’appareil fonctionne en observant votre environnement dans une lumière visible, il doit y avoir suffisamment de lumière pour que l’environnement puisse être observé. Il doit également y avoir suffisamment de fonctionnalités visuelles distinctives (en d’autres termes, décorations, points de contraste, etc.) pour que le système de suivi fonctionne.

## <a name="how-much-light-is-enough-light"></a>Quelle est la quantité de lumière suffisante ?

Une bonne règle empirique est que vous puissiez vous déplacer confortablement dans l’environnement sans vous sentir trop obscur. Si vous pouvez observer les fonctionnalités d’une autre personne à travers la pièce, le système de suivi est probablement suffisamment clair.

## <a name="what-is-the-recommended-amount-of-environmental-features"></a>Quelle est la quantité recommandée de fonctionnalités environnementales ?

Le produit a été conçu pour fonctionner dans des environnements normaux. Examinez l’expérience de réflexion suivante : Si vous étiez dans une salle complètement vierge (murs blancs, plafond blanc, plancher blanc), le système de suivi ne trouvera pas de fonctionnalités à suivre et échouait. Si vous étiez dans une salle couverte par le travail artistique et la décoration, le système de suivi trouvera de nombreuses fonctionnalités à suivre et fonctionnerait bien. Pour l’essentiel, en général, les maisons et les bureaux décorés ont été démontrés comme ayant suffisamment de détails pour assurer le suivi.

## <a name="how-fast-can-i-move-with-the-device"></a>Quelle est la vitesse de déplacement de l’appareil ?

L’appareil est conçu pour prendre en charge le mouvement en-delà de ce qui est normalement rencontré par le mouvement de la tête humaine. N’hésitez pas à vous déplacer. Gardez à l’esprit que vous avez réduit la connaissance de votre environnement physique quand vous êtes dans un casque immersif, vous devez donc vous assurer que vous êtes en sécurité dans votre environnement.

## <a name="where-will-tracking-not-work"></a>Où le suivi ne fonctionne-t-il pas ?

Le suivi ne fonctionne pas dans une pièce sombre dans laquelle les caméras ne peuvent pas voir suffisamment de fonctionnalités en raison de la faible luminosité. En général, le suivi ne fonctionne pas correctement (ou parfois du tout) dans le déplacement de véhicules tels que les avions, les bus, les trains, les voitures ou les ascenseurs.

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>Quelle est la différence entre 3DOF et 6DOF ?

Tout d’abord, le DDL est concis pour les « degrés de liberté ». En ce qui concerne les systèmes de suivi, cela signifie les degrés ou les types de mouvement qui peuvent être détectés. Ces mouvements sont divisés en deux catégories principales : « rotation » et « rotation avec translation ». 3DOF fait référence à 3 degrés de liberté et représente des rotations sur chaque axe. En d’autres termes, le suivi 3DOF vous permet de regarder à gauche/à droite, vers le haut/vers le haut et de faire pivoter le côté de votre tête (Roll). Vous ne pouvez pas traduire ou avancer/reculer dans 3DOF. 6DOF est limité à 6 degrés de liberté. Il s’appuie sur les rotations de 3DOF et les ajoute aux traductions informatiques. Cela signifie que vous pouvez avancer/reculer, Strafe gauche/droite et Crouch. 3 le suivi des DDL est le type de suivi que vous trouverez généralement sur un téléphone ou un produit VR mobile, tandis que 6DOF se trouvera sur des plateformes plus puissantes VR. Certaines expériences sont adaptées à 3DOF et n’autorisent que le mouvement 3DOF (rotations), même si l’appareil prend en charge le suivi 6DOF. Un exemple de cela serait de regarder une vidéo 360 dans Windows Mixed Reality. La vidéo vous permettra de vous faire une recherche, mais ne vous permettra pas de vous familiariser avec votre environnement.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>Les choses sont instables ou saccadées dans mon casque. Mon suivi ne fonctionne-t-il pas ?

Il existe deux sources de ce type d’erreur. Il est important de pouvoir attribuer ce que vous observez à la bonne cause afin qu’il puisse être traité. Consultez la section [résolution des problèmes](tracking.md) pour mieux comprendre pourquoi cela peut se produire.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>Puis-je apporter ma propre technologie de suivi à Windows Mixed Reality ?

Cela n’est actuellement pas pris en charge.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>Pourquoi est-ce que je vois une interface utilisateur indiquant « impossible de trouver votre limite ? »

Étant donné que la limite de sécurité est spécifique à un emplacement physique, si vous utilisez l’appareil dans un autre emplacement, le système ne pourra pas trouver les limites. En outre, une fois que vous avez configuré votre limite, le système le recherchera toujours, même si vous utilisez l’appareil dans un emplacement physique différent. Vous verrez cette interface utilisateur chaque fois que vous utilisez l’appareil dans un emplacement différent et que vous n’avez pas encore configuré de limite dans cet emplacement. Vous pouvez configurer des limites dans chaque emplacement où vous utilisez l’appareil, et l’appareil rappellera vos limites d’emplacement spécifiques.

Si vous utilisez l’appareil dans un emplacement où vous avez déjà configuré une limite et que l’appareil ne peut pas le trouver, vous pouvez configurer une nouvelle limite ou effacer toutes les données d’environnement pour supprimer toutes les limites de l’appareil. Consultez la section [résolution des problèmes](tracking.md) pour comprendre pourquoi le système ne trouve pas vos limites et les étapes à suivre pour le corriger.

## <a name="how-do-i-set-up-tracking"></a>Comment faire configurer le suivi ?

Le suivi dans Windows Mixed Reality est simple à utiliser. Aucune infrastructure ou configuration n’est requise et l’appareil est prêt à l’emploi. Si vous avez choisi, vous pouvez configurer une limite virtuelle à utiliser. Pour plus d’informations, consultez la section relative à la [configuration de vos limites](set-up-windows-mixed-reality.md#set-up-your-room-boundary) .

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Comment faire effacer les données de suivi et d’environnement ?

Le système de suivi stocke des données d’environnement afin qu’il puisse rappeler l’emplacement physique réel des choses comme vos limites de sécurité. Ces informations, y compris vos limites de sécurité, peuvent être supprimées à tout moment. Si ces informations sont supprimées, le système ne reconnaîtra plus votre espace ou pourra vous rappeler vos limites de sécurité. Si vous souhaitez utiliser des limites de sécurité après avoir effacé les données de l’environnement, vous devrez les reconfigurer. Consultez la section relative à la [configuration de votre limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) pour configurer une nouvelle limite. Pour supprimer toutes ces données, ouvrez paramètres, accédez à « réalité mixte », puis sélectionnez la section environnement du menu de gauche. Cliquez sur le bouton intitulé « effacer les données d’environnement » pour supprimer tous les environnements et données de suivi.

## <a name="see-also"></a>Voir aussi
* [Résolution des problèmes liés au système de suivi](tracking.md)
* [Fonctionnement des contrôleurs de mouvement](controller-in-wmr.md)
* [Votre accueil Windows Mixed Reality](your-mixed-reality-home.md)
* [Utilisation de jeux et d’applications dans Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
