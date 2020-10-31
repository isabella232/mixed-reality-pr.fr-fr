---
title: Envoyer des bogues et des commentaires
description: Aidez-nous à améliorer Windows Mixed Reality en remplissant les commentaires à l’aide des catégories appropriées dans l’application Hub de commentaires.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
appliesto:
- Windows 10
ms.openlocfilehash: c0e2da59e64973c954cc880504a021a2835ed204
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132123"
---
# <a name="filing-bugs-and-feedback"></a>Envoyer des bogues et des commentaires

## <a name="why-its-important"></a>Pourquoi il est important

L’équipe d’ingénierie utilise le même mécanisme en interne pour le suivi et la résolution des bogues. par conséquent, veuillez nous faire part de vos commentaires et signaler les bogues que vous rencontrez. Nous sommes à l’écoute !

## <a name="before-you-file-feedback"></a>Avant de vous envoyer des commentaires

Assurez-vous que votre ordinateur est configuré pour fournir des données complètes pour les commentaires et les Diagnostics. Voici comment vérifier le paramètre sur votre ordinateur avant de vous envoyer des commentaires :

1. Ouvrez l’application **paramètres** Windows.
2. Cliquez sur **confidentialité** .
3. Accédez à **commentaires & Diagnostics** dans le volet gauche (Notez que cela a été renommé **diagnotics & Feedback** dans les versions récentes de Windows Insider.
4. Sous **Sélectionnez la quantité de données que vous envoyez à Microsoft** , sélectionnez **complète** si elle n’est pas déjà sélectionnée.
5. Veillez à redémarrer votre ordinateur et répétez les étapes pour reproduire votre problème avant de remplir les commentaires.

## <a name="how-to-file-feedback-for-windows-mixed-reality-immersive-headsets-on-pc"></a>Comment envoyer des commentaires sur des casques immersifs Windows Mixed Reality sur PC

1. Assurez-vous que le casque immersif est connecté à votre PC.
2. Lancez **Feedback Hub** sur le bureau avec le HMD connecté.
3. Accédez à l' **onglet Commentaires** dans le volet gauche. ![Onglet Commentaires](images/feedback1.png) 
4. Cliquez sur le bouton **Ajouter un nouveau commentaire** pour entrer les commentaires. ![Ajouter un commentaire](images/feedback2.png)
5. Sélectionnez **problème** dans **quel type de commentaire est-ce que c’est ?** pour rendre les commentaires exploitables. ![Détails et étapes de reproduction](images/feedback3.png)
6. Fournissez un titre de commentaires significatif dans la zone **résumer votre problème** .
7. Fournissez des détails et des étapes pour reproduire le problème dans la zone **Donnez-nous plus de détails** .
8. Sélectionnez **réalité mixte** comme catégorie supérieure, puis choisissez une sous-catégorie applicable :

   | Sous-catégorie      | Description                                                                           |
   |------------------|---------------------------------------------------------------------------------------|
   | Applications             | Problèmes avec une application spécifique.                                                   |
   | Développeur        | Problèmes lors de la création ou de l’exécution d’une application pour la réalité mixte.                               |
   | Appareil           | Problèmes avec le HMD lui-même.                                                           |
   | Expérience personnelle  | Problèmes avec votre environnement VR : interactions avec la page d’hébergement de Windows Mixed Reality.    |
   | Entrée            | Problèmes liés aux méthodes d’entrée : contrôleurs de mouvement, reconnaissance vocale, manette de la souris et du clavier.|
   | Configurer           | Tout ce qui vous empêche de configurer l’appareil.                           |
   | Tous les autres problèmes | Autre chose.                                                                        |

9. Pour nous aider à identifier et corriger le bogue plus rapidement, la capture de traces et de vidéos est très utile. Pour démarrer la collecte des traces, cliquez sur **Démarrer la capture** . Cette opération commence à collecter des traces et une capture vidéo de votre scénario de réalité mixte. ![ Démarrer la capture](images/feedback4.png)
10. Laissez l’application de commentaires et exécutez le scénario rompu. Ne fermez pas l’application Hub de commentaires à ce stade.
11. Une fois que vous avez terminé votre scénario, revenez à l’application de commentaires, puis cliquez sur **arrêter la capture** . Une fois cette opération terminée, vous devez voir qu’un fichier contenant les suivis a été ajouté.
12. Cliquez sur **Envoyer** . ![ Envoyer](images/feedback5.png)

Cela vous amène à la page « remerciement ». À ce stade, vos commentaires ont été envoyés avec succès.

Une fois que vous avez envoyé des commentaires, pour diriger facilement d’autres personnes (par exemple, des collègues, du personnel Microsoft, des lecteurs de [Forum](https://forums.hololens.com/) , etc.) vers le problème, accédez à **Commentaires > mes commentaires** , cliquez sur le problème et utilisez l’icône **partager** pour obtenir une URL abrégée que vous pouvez accorder à d’autres personnes pour le vote ou le faire remonter.

> [!IMPORTANT]
> Avant de signaler un bogue, vérifiez que vous respectez les contraintes suivantes afin que les journaux soient correctement téléchargés avec les commentaires.
>    * Vous devez disposer d’au moins 3 Go d’espace disque libre sur le lecteur principal de l’appareil.
>    * Assurez-vous qu’un réseau non contrôlé est disponible pour charger les cabines.

## <a name="after-filing-feedback"></a>Après avoir effectué des commentaires

Veillez à consulter régulièrement le hub de commentaires après avoir fait un profilage. Dans la plupart des cas, nous essaierons de répondre dès que possible. Si vous n’êtes pas déjà en contact avec nous lorsque vous envoyez des commentaires, la seule façon dont nous pouvons vous contacter pour obtenir des suggestions de dépannage ou d’autres questions se fait via le système de commentaires dans le hub de commentaires. Malheureusement, à ce stade, les notifications ne vous sont pas envoyées en dehors du Hub de commentaires.

## <a name="see-also"></a>Voir aussi

* [Dépannage](troubleshooting-windows-mixed-reality.md)