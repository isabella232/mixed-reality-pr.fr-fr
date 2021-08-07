---
title: Envoyer des bogues et des commentaires
description: aidez-nous à améliorer Windows Mixed Reality en remplissant vos commentaires à l’aide des catégories appropriées dans l’application Hub de commentaires.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
appliesto:
- Windows 10
ms.openlocfilehash: b4ba5cf16aec84fa6c34ae2454ebfefa56512a04e4845dee0c3c894c4976cc53
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188946"
---
# <a name="filing-bugs-and-feedback"></a>Envoyer des bogues et des commentaires

## <a name="why-its-important"></a>Pourquoi il est important

L’équipe d’ingénierie utilise le même mécanisme pour le suivi et la résolution des bogues internes. par conséquent, utilisez le hub de commentaires pour signaler tout ce qui est étrange que vous voyez-nous sommes à votre écoute.

## <a name="before-you-file-feedback"></a>Avant de vous envoyer des commentaires

Assurez-vous que votre ordinateur est configuré pour fournir des données complètes pour les commentaires et les Diagnostics. Voici comment vérifier le paramètre sur votre ordinateur avant de vous envoyer des commentaires :

1. ouvrez l’application **Paramètres** Windows.
2. Sélectionnez on **Privacy**.
3. accédez à **commentaires & diagnostics** dans le volet gauche, qui a été renommé pour **diagnostics & commentaires** dans les builds récentes Windows insider de Windows.
4. Sous **Sélectionnez la quantité de données que vous envoyez à Microsoft**, sélectionnez **complète** si elle n’est pas déjà sélectionnée.
5. Veillez à redémarrer votre ordinateur et répétez les étapes pour reproduire votre problème avant de remplir les commentaires.

## <a name="how-to-file-feedback-for-windows-mixed-reality-immersive-headsets-on-pc"></a>comment envoyer des commentaires pour Windows Mixed Reality des casques immersifs sur PC

1. Assurez-vous que le casque immersif est connecté à votre PC.
2. Lancez **Feedback Hub** sur le bureau avec le HMD connecté.
3. Accédez à l' **onglet Commentaires** dans le volet gauche. ![Onglet Commentaires](images/feedback1.png) 
4. Sélectionnez **Ajouter un nouveau** bouton de commentaires pour entrer les commentaires. ![Ajouter un commentaire](images/feedback2.png)
5. Sélectionnez **problème** dans **quel type de commentaire est-ce que c’est ?** pour rendre les commentaires exploitables. ![Détails et étapes de reproduction](images/feedback3.png)
6. Fournissez un titre de commentaires significatif dans la zone **résumer votre problème** .
7. Fournissez des détails et des étapes pour reproduire le problème dans la zone **Donnez-nous plus de détails** .
8. Sélectionnez **réalité mixte** comme catégorie supérieure, puis choisissez une sous-catégorie applicable :

   | Sous-catégorie      | Description                                                                           |
   |------------------|---------------------------------------------------------------------------------------|
   | Applications             | Problèmes avec une application spécifique.                                                   |
   | Développeur        | Problèmes lors de la création ou de l’exécution d’une application pour la réalité mixte.                               |
   | Appareil           | Problèmes avec le HMD lui-même.                                                           |
   | Expérience personnelle  | problèmes avec votre environnement VR : interactions avec le Windows Mixed Reality la page d’hébergement.    |
   | Entrée            | Problèmes liés aux méthodes d’entrée : contrôleurs de mouvement, reconnaissance vocale, manette de la souris et du clavier.|
   | Configurer           | Tout ce qui vous empêche de configurer l’appareil.                           |
   | Tous les autres problèmes | Autre chose.                                                                        |

9. Pour nous aider à identifier et corriger le bogue plus rapidement, il est utile de capturer des traces et des vidéos. Pour démarrer la collecte des traces, sélectionnez **Démarrer la capture**. Cette opération commence à collecter des traces et une capture vidéo de votre scénario de réalité mixte. ![ Démarrer la capture](images/feedback4.png)
10. Laissez l’application de commentaires et exécutez le scénario rompu. Ne fermez pas l’application Hub de commentaires à ce stade.
11. Une fois que vous avez terminé votre scénario, revenez à l’application de commentaires et sélectionnez **arrêter la capture**. Une fois cette opération terminée, vous devez voir qu’un fichier contenant les suivis a été ajouté.
12. Sélectionnez **Envoyer**. ![ Envoyer](images/feedback5.png)

Cela vous amène à la page « remerciement ». À ce stade, vos commentaires ont été envoyés avec succès.

Il est facile de diriger d’autres personnes vers vos commentaires après leur envoi en accédant à vos **commentaires > mes commentaires**, en sélectionnant le problème et en utilisant l’icône de **partage** pour obtenir une URL abrégée. Vous pouvez fournir l’URL aux collègues, au personnel de Microsoft, aux lecteurs de [Forum](https://forums.hololens.com/) , etc., pour voter ou promouvoir.

> [!IMPORTANT]
> Avant de signaler un bogue, vérifiez que vous respectez les contraintes suivantes afin que les journaux soient correctement téléchargés avec les commentaires.
>    * Vous devez disposer d’au moins 3 Go d’espace disque libre sur le lecteur principal de l’appareil.
>    * Assurez-vous qu’un réseau non contrôlé est disponible pour charger les cabines.

## <a name="after-filing-feedback"></a>Après avoir effectué des commentaires

Veillez à consulter régulièrement le hub de commentaires après avoir fait un profilage. Dans la plupart des cas, nous essaierons de répondre dès que possible. Si vous n’êtes pas déjà en contact avec nous lorsque vous envoyez des commentaires, la seule façon dont nous pouvons vous contacter pour obtenir des suggestions de dépannage ou d’autres questions se fait via le système de commentaires dans le hub de commentaires. Malheureusement, à ce stade, les notifications ne vous sont pas envoyées en dehors du Hub de commentaires.

## <a name="see-also"></a>Voir aussi

* [Dépannage](troubleshooting-windows-mixed-reality.md)