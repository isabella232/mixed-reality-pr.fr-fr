---
title: HoloLens (1ère génération) et Azure 308 - Notifications interappareils
description: suivez ce cours pour apprendre à implémenter Azure Notification Hubs, Azure Functions et les Tables stockage Azure et dans une application de réalité mixte.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, réalité mixte, académie, unity, didacticiel, api, notification, fonctions, tables, notification hubs, hololens, immersif, vr, Windows 10, Visual Studio
ms.openlocfilehash: 01d096297a9fbe25d39b2846acd2ee89b50edcfd26456f3f20ccd2c9bc26b514
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205533"
---
# <a name="hololens-1st-gen-and-azure-308-cross-device-notifications"></a>HoloLens (1er génération) et Azure 308 : notifications entre appareils

<br>

>[!NOTE]
>Les tutoriels Mixed Reality Academy ont été conçus pour les appareils HoloLens (1re génération) et les casques immersifs de réalité mixte.  Nous estimons qu’il est important de laisser ces tutoriels à la disposition des développeurs qui recherchent encore des conseils pour développer des applications sur ces appareils.  Notez que ces tutoriels **_ne sont pas_** mis à jour avec les derniers ensembles d’outils ou interactions utilisés pour HoloLens 2.  Ils sont fournis dans le but de fonctionner sur les appareils pris en charge. Une nouvelle série de didacticiels sera publiée à l’avenir qui vous montrera comment développer pour HoloLens 2.  Cet avis sera mis à jour avec un lien vers ces didacticiels lors de leur publication.

<br>

![produit final-début](images/AzureLabs-Lab8-00.png)

Dans ce cours, vous allez apprendre à ajouter des fonctionnalités de Notification Hubs à une application de réalité mixte à l’aide d’Azure Notification Hubs, de tables Azure et d’Azure Functions.

**Azure notification hubs** est un service Microsoft, qui permet aux développeurs d’envoyer des notifications push ciblées et personnalisées à n’importe quelle plateforme, toutes alimentées dans le Cloud. Cela permet aux développeurs de communiquer efficacement avec les utilisateurs finaux, ou même de communiquer entre différentes applications, en fonction du scénario. Pour plus d’informations, consultez la [page](/azure/notification-hubs/notification-hubs-push-notification-overview) **notification hubs Azure** .

**Azure Functions** est un service Microsoft, qui permet aux développeurs d’exécuter de petits morceaux de code, « functions », dans Azure. Cela permet de déléguer le travail au Cloud, plutôt qu’à votre application locale, ce qui peut avoir de nombreux avantages. **Azure Functions** prend en charge plusieurs langages de développement, notamment C \# , F \# , Node.js, Java et php. Pour plus d’informations, consultez la [page](/azure/azure-functions/functions-overview) **Azure Functions** .

**Azure Tables** est un service cloud Microsoft qui permet aux développeurs de stocker des données non SQL structurées dans le cloud, ce qui les rend facilement accessibles en tout lieu. Le service dispose d’une conception sans schéma, ce qui permet l’évolution des tables en fonction des besoins et est donc très flexible. Pour plus d’informations, consultez la [page](/azure/cosmos-db/table-storage-overview) **tables Azure**

Une fois ce cours terminé, vous disposerez d’une application de casque et d’une application de PC de bureau, qui sera en mesure d’effectuer les opérations suivantes :

1. L’application PC Desktop permet à l’utilisateur de déplacer un objet dans l’espace 2D (X et Y) à l’aide de la souris.

2. Le déplacement d’objets dans l’application PC est envoyé au Cloud à l’aide de JSON, qui se présente sous la forme d’une chaîne contenant un ID d’objet, un type et des informations de transformation (coordonnées X et Y). 

3. L’application de réalité mixte, qui a une scène identique à celle de l’application de bureau, recevra des notifications concernant le déplacement d’objets à partir du service Notification Hubs (qui vient d’être mis à jour par l’application du PC de bureau). 

4. Lors de la réception d’une notification, qui contient les informations relatives à l’ID d’objet, au type et à la transformation, l’application de réalité mixte applique les informations reçues à sa propre scène.

Dans votre application, c’est à vous de savoir comment vous allez intégrer les résultats à votre conception. Ce cours est conçu pour vous apprendre à intégrer un service Azure à votre Project Unity. C’est votre travail d’utiliser les connaissances que vous avez acquises dans ce cours pour améliorer votre application de réalité mixte. Ce cours est un didacticiel autonome qui n’implique pas directement d’autres laboratoires de réalité mixte.

## <a name="device-support"></a>Prise en charge des appareils

<table>
<tr>
<th>Cours</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Casques immersifs</a></th>
</tr><tr>
<td> Réalité mixte - Azure - Cours 308 : Notifications inter-appareils</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> bien que ce cours se concentre principalement sur les casques Windows Mixed Reality immersifs, vous pouvez également appliquer ce que vous avez appris dans ce cours à Microsoft HoloLens. À mesure que vous suivez le cours, vous verrez des remarques sur les modifications que vous devrez peut-être utiliser pour prendre en charge HoloLens. lorsque vous utilisez HoloLens, vous remarquerez peut-être un écho pendant la capture vocale.

## <a name="prerequisites"></a>Prérequis

> [!NOTE]
> Ce didacticiel est conçu pour les développeurs qui ont une expérience de base avec Unity et C#. Sachez également que les conditions préalables et les instructions écrites dans ce document représentent les éléments qui ont été testés et vérifiés au moment de l’écriture (mai 2018). Vous êtes libre d’utiliser le logiciel le plus récent, tel qu’indiqué dans l’article [installer les outils](../../install-the-tools.md) , bien qu’il ne soit pas supposé que les informations de ce cours correspondent parfaitement à ce que vous trouverez dans les logiciels plus récents que ceux répertoriés ci-dessous.

Nous vous recommandons d’utiliser le matériel et les logiciels suivants pour ce cours :

- un PC de développement, [compatible avec Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) pour le développement d’écouteurs immersifs (VR)
- [Windows 10 Fall Creators Update (ou version ultérieure) avec le mode développeur activé](../../install-the-tools.md#installation-checklist)
- [le dernier kit de développement logiciel Windows 10](../../install-the-tools.md#installation-checklist)
- [Unity 2017,4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- un [casque Windows Mixed Reality (VR)](../../../discover/immersive-headset-hardware-details.md) ou [Microsoft HoloLens](/hololens/hololens1-hardware) avec le mode développeur activé
- Accès Internet pour l’installation d’Azure et pour accéder Notification Hubs

## <a name="before-you-start"></a>Avant de commencer

- Pour éviter de rencontrer des problèmes lors de la création de ce projet, il est fortement recommandé de créer le projet mentionné dans ce didacticiel dans un dossier racine ou dans un dossier racine (les chemins de dossiers longs peuvent entraîner des problèmes au moment de la génération).
- Vous devez être le propriétaire de votre portail des développeurs Microsoft et du portail d’inscription des applications. sinon, vous n’êtes pas autorisé à accéder à l’application dans le [Chapitre 2](#chapter-2---retrieve-your-new-apps-credentials).

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Chapitre 1-créer une application sur le portail des développeurs Microsoft

Pour utiliser le service **Azure notification hubs** , vous devez créer une application sur le portail des développeurs Microsoft, car votre application doit être inscrite, afin de pouvoir envoyer et recevoir des notifications.

1.  Connectez-vous au [portail des développeurs Microsoft](https://developer.microsoft.com/dashboard).

    > Vous devrez vous connecter à votre compte Microsoft.

2.  Dans le tableau de bord, cliquez sur **créer une application**.

    ![créer une application](images/AzureLabs-Lab8-01.png)

3.  Une fenêtre contextuelle s’affiche, dans laquelle vous devez réserver un nom pour votre nouvelle application. Dans la zone de texte, insérez un nom approprié ; Si le nom choisi est disponible, un cycle s’affiche à droite de la zone de texte. Une fois que vous avez un nom disponible inséré, cliquez sur le bouton **réserver un nom de produit** en bas à gauche de la fenêtre contextuelle.

    ![inverser un nom](images/AzureLabs-Lab8-02.png)

4.  Une fois l’application créée, vous êtes prêt à passer au chapitre suivant.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Chapitre 2-récupération des informations d’identification de vos nouvelles applications

Connectez-vous au portail d’inscription des applications, où votre nouvelle application sera listée et récupérez les informations d’identification qui seront utilisées pour configurer le **Service notification hubs** dans le **portail Azure**.

1.  Accédez au [portail d’inscription des applications](https://apps.dev.microsoft.com).

    ![portail d’inscription des applications](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Vous devrez utiliser votre compte Microsoft pour vous connecter.  
    > il **doit** s’agir du compte Microsoft que vous avez utilisé dans le [chapitre](#chapter-1---create-an-application-on-the-microsoft-developer-portal)précédent, avec le portail des développeurs Windows Store.

2.  Votre application se trouve dans la section **mes applications** . Une fois que vous l’avez trouvé, cliquez dessus pour afficher une nouvelle page qui contient le nom de l’application et l' **inscription**.

    ![votre application nouvellement inscrite](images/AzureLabs-Lab8-04.png)

3.  Faites défiler la page d’inscription pour trouver la section secrets de votre **application** et le **SID du package** pour votre application. Copiez-les pour les utiliser avec la configuration du **service Azure notification hubs** dans le chapitre suivant.

    ![secrets d’application](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Chapitre 3-configurer le portail Azure : créer Notification Hubs service

Une fois les informations d’identification de vos applications récupérées, vous devez accéder au portail Azure, où vous allez créer un service Azure Notification Hubs.

1.  Connectez-vous au [portail Azure](https://portal.azure.com).

    > [!NOTE] 
    > Si vous n’avez pas encore de compte Azure, vous devez en créer un. Si vous suivez ce didacticiel dans une situation de classe ou de laboratoire, demandez à votre formateur ou à l’un des prostructors de vous aider à configurer votre nouveau compte.

2.  Une fois que vous êtes connecté, cliquez sur **nouveau** dans l’angle supérieur gauche et recherchez **notification Hub**, puis cliquez sur **_entrée_**.

    ![Rechercher le hub de notification](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > Le mot ***New** _ peut avoir été remplacé par _ * créer une ressource * *, dans les portails plus récents.

3.  La nouvelle page fournit une description du service *notification hubs* . En bas à gauche de cette invite, sélectionnez le bouton **créer** pour créer une association avec ce service.

    ![créer une instance notification hubs](images/AzureLabs-Lab8-07.png)

4.  Une fois que vous avez cliqué sur ***créer***:

    1.  Insérez le nom de votre choix pour cette instance de service.

    2.  Fournissez un **espace de noms** que vous pourrez associer à cette application.

    3.  Sélectionnez un **emplacement.**

    4.  Choisissez un **groupe de ressources** ou créez-en un. Un groupe de ressources permet de surveiller, de contrôler l’accès, de configurer et de gérer la facturation d’un regroupement de ressources Azure. Il est recommandé de conserver tous les services Azure associés à un seul projet (par exemple, ces laboratoires) sous un groupe de ressources commun).

        > Si vous souhaitez en savoir plus sur les groupes de ressources Azure, cliquez [sur le lien suivant pour gérer un groupe de ressources](/azure/azure-resource-manager/resource-group-portal). 

    5.  Sélectionnez un **abonnement** approprié.

    6.  Vous devrez également confirmer que vous avez compris les conditions générales appliquées à ce service.

    7. Sélectionnez **Créer**.

        ![renseigner les détails du service](images/AzureLabs-Lab8-08.png)

5.  Une fois que vous avez cliqué sur **créer**, vous devez attendre que le service soit créé, cette opération peut prendre une minute.

6.  Une notification s’affichera dans le portail une fois l’instance de service créée.

    ![notification](images/AzureLabs-Lab8-09.png)

7.  Cliquez sur le bouton **atteindre la ressource** dans la notification pour explorer votre nouvelle instance de service. Vous êtes dirigé vers votre nouvelle instance de service **notification Hub** .

    ![accéder à la ressource](images/AzureLabs-Lab8-10.png)
    
8.  Dans la page vue d’ensemble, à mi-chemin de la page, cliquez sur **Windows (WNS).** Le panneau à droite change pour afficher deux champs de texte, qui nécessitent votre **SID de package** et votre **clé de sécurité**, à partir de l’application que vous avez configurée précédemment.

    ![service hubs nouvellement créé](images/AzureLabs-Lab8-11.png)

9. Une fois que vous avez copié les détails dans les champs appropriés, cliquez sur **Enregistrer** pour recevoir une notification lorsque le hub de notification a été correctement mis à jour.

    ![copier les détails de sécurité](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Chapitre 4-configurer le portail Azure : créer un service de table

après avoir créé votre instance de service Notification Hubs, revenez à votre portail azure, où vous allez créer un Service de Tables azure en créant une ressource de Stockage.

1.  Si vous n’êtes pas déjà connecté, connectez-vous au [portail Azure](https://portal.azure.com).

2.  une fois connecté, cliquez sur **nouveau** dans l’angle supérieur gauche et recherchez **Stockage compte**, puis cliquez sur **entrée**.

    > [!NOTE] 
    > Le mot ***New** _ peut avoir été remplacé par _ * créer une ressource * *, dans les portails plus récents.

3.  sélectionnez **Stockage compte-blob, fichier, table, file d’attente** dans la liste.

    ![Rechercher le compte de stockage](images/AzureLabs-Lab8-13.png)

4.  la nouvelle page fournit une description du service de **compte Stockage** . En bas à gauche de cette invite, sélectionnez le bouton **créer** pour créer une instance de ce service.

    ![créer une instance de stockage](images/AzureLabs-Lab8-14.png)

5.  Une fois que vous avez cliqué sur **créer**, un panneau s’affiche :

    1. Insérez le **nom** souhaité pour cette instance de service (doit être tout en minuscules).

    2. Pour **modèle de déploiement**, cliquez sur **Resource Manager**.

    3.  pour **type de compte**, à l’aide du menu déroulant, sélectionnez **Stockage (à usage général v1)**.

    4. Sélectionnez un **emplacement** approprié.
    
    5.  Dans la liste déroulante **réplication** , sélectionnez **stockage avec accès géo-redondant (RA-GRS)**.

    6.  Pour les **performances**, cliquez sur **standard**.

    7.  Dans la section **transfert sécurisé requis** , sélectionnez **désactivé**.

    8.  Dans le menu déroulant **abonnement** , sélectionnez un abonnement approprié.

    9.  Choisissez un **groupe de ressources** ou créez-en un. Un groupe de ressources permet de surveiller, de contrôler l’accès, de configurer et de gérer la facturation d’un regroupement de ressources Azure. Il est recommandé de conserver tous les services Azure associés à un seul projet (par exemple, ces laboratoires) sous un groupe de ressources commun).

        > Si vous souhaitez en savoir plus sur les groupes de ressources Azure, cliquez [sur le lien suivant pour gérer un groupe de ressources](/azure/azure-resource-manager/resource-group-portal).

    10. Laissez les **réseaux virtuels** **désactivés** s’il s’agit d’une option pour vous.

    11. Cliquez sur **Créer**.

        ![renseigner les détails du stockage](images/AzureLabs-Lab8-15.png)

6.  Une fois que vous avez cliqué sur **créer**, vous devez attendre que le service soit créé, cette opération peut prendre une minute.

7.  Une notification s’affichera dans le portail une fois l’instance de service créée. Cliquez sur les notifications pour explorer votre nouvelle instance de service.

    ![nouvelle notification de stockage](images/AzureLabs-Lab8-16.png)

8.  Cliquez sur le bouton **atteindre la ressource** dans la notification pour explorer votre nouvelle instance de service. vous êtes dirigé vers la page vue d’ensemble de votre nouvelle instance de Service Stockage.

    ![accéder à la ressource](images/AzureLabs-Lab8-17.PNG)

9. Dans la page vue d’ensemble, sur le côté droit, cliquez sur **tables**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. Le panneau à droite change pour afficher les informations sur le **service de table** , où vous devez ajouter une nouvelle table. Pour ce faire, cliquez sur le **+** bouton de **table** dans l’angle supérieur gauche.

    ![Tables ouvertes](images/AzureLabs-Lab8-19.png)

11. Une nouvelle page s’affiche, dans laquelle vous devez entrer un nom de **table**. Il s’agit du nom que vous allez utiliser pour faire référence aux données de votre application dans les chapitres ultérieurs. Insérez un nom approprié, puis cliquez sur **OK**.

    ![créer une nouvelle table](images/AzureLabs-Lab8-20.png)    

12. Une fois la nouvelle table créée, vous pouvez la voir dans la page **service de table** (en bas).

    ![nouvelle table créée](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Chapitre 5 : remplissage de la table Azure dans Visual Studio

Maintenant que votre compte de stockage de **service de table** a été configuré, il est temps d’y ajouter des données qui seront utilisées pour stocker et récupérer des informations. La modification de vos tables peut être effectuée via **Visual Studio**.

1.  Ouvrez **Visual Studio**.

2.  Dans le menu, cliquez sur **Afficher** le  >  **Cloud Explorer**.

    ![ouvrir Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  Le **Cloud Explorer** s’ouvre en tant qu’élément ancré (patienter, car le chargement peut prendre du temps).

    > [!NOTE] 
    > si l’abonnement que vous avez utilisé pour créer vos *comptes de Stockage* n’est pas visible, vérifiez que vous disposez des éléments suivants : 
    > - Connectez-vous au même compte que celui que vous avez utilisé pour le portail Azure.
    > - Sélectionnez votre abonnement dans la page de gestion des comptes (vous devrez peut-être appliquer un filtre à partir de vos paramètres de compte) :  
    >
    >   ![Rechercher un abonnement](images/AzureLabs-Lab8-22-5.png)

4.  Vos services Cloud Azure s’affichent. recherchez **Stockage comptes** , puis cliquez sur la flèche à gauche de celle-ci pour développer vos comptes.

    ![ouvrir les comptes de stockage](images/AzureLabs-Lab8-23.png)

5.  une fois développé, le **compte de Stockage** que vous venez de créer doit être disponible. Cliquez sur la flèche à gauche de votre stockage, puis une fois celle-ci développée, recherchez des **tables** , puis cliquez sur la flèche en regard de celle-ci pour afficher la **table** que vous avez créée dans le dernier chapitre. Double-cliquez sur votre **table**.

    ![ouvrir la table d’objets de scène](images/AzureLabs-Lab8-24.png)

6.  votre table s’ouvre au centre de votre fenêtre de Visual Studio. Cliquez sur l’icône de table avec **+** (plus).

    ![Ajouter une nouvelle table](images/AzureLabs-Lab8-25.png)

7.  Une fenêtre s’affiche pour vous inviter à *Ajouter une entité*. Vous allez créer trois entités au total, chacune avec plusieurs propriétés. Vous remarquerez que *PartitionKey* et *RowKey* sont déjà fournis, car ils sont utilisés par la table pour rechercher vos données. 

    ![clé de partition et de ligne](images/AzureLabs-Lab8-26.png)

8. Mettez à jour la *valeur* de **PartitionKey** et **RowKey** comme suit (n’oubliez pas d’effectuer cette opération pour chaque propriété de ligne que vous ajoutez, même si vous incrémentez le RowKey à chaque fois) :

    ![Ajouter les valeurs correctes](images/AzureLabs-Lab8-26-5.png)

9.  Cliquez sur **Ajouter une propriété** pour ajouter des lignes de données supplémentaires. Faites correspondre votre première table vide à la table ci-dessous.

10. Cliquez sur **OK** lorsque vous avez terminé.

    ![Cliquez sur OK lorsque vous avez terminé](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Vérifiez que vous avez modifié le **type** des entrées **X**, **Y** et **Z**, puis **doublez**-les. 

11. Vous remarquerez que votre table contient désormais une ligne de données. Cliquez à **+** nouveau sur l’icône (plus) pour ajouter une autre entité.

    ![première ligne](images/AzureLabs-Lab8-27-5.png)

12. Créez une propriété supplémentaire, puis définissez les valeurs de la nouvelle entité pour qu’elles correspondent à celles indiquées ci-dessous.

    ![Ajouter un cube](images/AzureLabs-Lab8-28.png)

13. Répétez la dernière étape pour ajouter une autre entité. Définissez les valeurs de cette entité sur celles indiquées ci-dessous.

    ![Ajouter un cylindre](images/AzureLabs-Lab8-29.png)

14. Votre table doit maintenant ressembler à celle ci-dessous.

    ![table terminée](images/AzureLabs-Lab8-30.png)

15. Vous avez terminé ce chapitre. Veillez à enregistrer.

## <a name="chapter-6---create-an-azure-function-app"></a>Chapitre 6-créer un Function App Azure

Créez un Function App Azure, qui sera appelé par l’application de bureau pour mettre à jour le service de **table** et envoyer une notification par le biais du **Hub de notification**.

Tout d’abord, vous devez créer un fichier qui permettra à votre fonction Azure de charger les bibliothèques dont vous avez besoin.

1.  ouvrez **Bloc-notes** (appuyez sur Windows clé et tapez Notepad).

    ![ouvrir le bloc-notes](images/AzureLabs-Lab8-31.png)

2.  avec Bloc-notes ouvrir, insérez la structure JSON ci-dessous. Une fois que vous avez terminé, enregistrez-le sur votre bureau en tant que **project.jssur**. Il est important que l’attribution de noms soit correcte : Assurez-vous qu’elle n' **a pas d’extension de fichier .txt** . Ce fichier définit les bibliothèques que votre fonction utilisera, si vous avez utilisé NuGet elle vous semblera familière.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  Connectez-vous au [portail Azure](https://portal.azure.com).

4.  Une fois que vous êtes connecté, cliquez sur **nouveau** dans l’angle supérieur gauche et recherchez **Function App**, appuyez sur **entrée**.

    ![Rechercher une application de fonction](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > Le mot **nouveau** peut avoir été remplacé par **créer une ressource**, dans les portails plus récents.

5.  La nouvelle page fournit une description du service **Function App** . En bas à gauche de cette invite, sélectionnez le bouton **créer** pour créer une association avec ce service.

    ![instance de l’application de fonction](images/AzureLabs-Lab8-33.png)

6.  Une fois que vous avez cliqué sur **créer**, renseignez les éléments suivants :

    1. Pour **nom** de l’application, insérez le nom de votre choix pour cette instance de service.

    2. Sélectionnez un **Abonnement**.

    3. Sélectionnez le niveau tarifaire approprié, s’il s’agit de la première fois que vous créez un **Service Function App**, vous devez disposer d’un niveau gratuit.

    4. Choisissez un **groupe de ressources** ou créez-en un. Un groupe de ressources permet de surveiller, de contrôler l’accès, de configurer et de gérer la facturation d’un regroupement de ressources Azure. Il est recommandé de conserver tous les services Azure associés à un seul projet (par exemple, ces laboratoires) sous un groupe de ressources commun).

        > Si vous souhaitez en savoir plus sur les groupes de ressources Azure, cliquez [sur le lien suivant pour gérer un groupe de ressources](/azure/azure-resource-manager/resource-group-portal).

    5. pour **système d’exploitation**, cliquez sur Windows, car il s’agit de la plateforme prévue.

    6. Sélectionnez un **plan d’hébergement** (ce didacticiel utilise un **plan de consommation**.

    7. Sélectionnez un **emplacement** **(choisissez le même emplacement que celui du stockage que vous avez créé à l’étape précédente)**

    8. pour la section **Stockage** , **vous devez sélectionner le Service Stockage que vous avez créé à l’étape précédente**.

    9. vous n’aurez pas besoin de *Application Insights* dans cette **application. n'** hésitez donc pas à la conserver.

    10. Cliquez sur **Créer**.

        ![créer une nouvelle instance](images/AzureLabs-Lab8-34.png)

7.  Une fois que vous avez cliqué sur **créer** , vous devez attendre que le service soit créé, cette opération peut prendre une minute.

8.  Une notification s’affichera dans le portail une fois l’instance de service créée.

    ![nouvelle notification](images/AzureLabs-Lab8-35.png)

9.  Cliquez sur les notifications pour explorer votre nouvelle instance de service.

10. Cliquez sur le bouton **atteindre la ressource** dans la notification pour explorer votre nouvelle instance de service. 

    ![accéder à la ressource](images/AzureLabs-Lab8-36.png)

11. Cliquez sur l' **+** icône (plus) en regard de *fonctions* pour *créer un nouveau*.

    ![Ajouter une nouvelle fonction](images/AzureLabs-Lab8-37.png)

12. Dans le panneau central, la fenêtre de création de **fonction** s’affiche. Ignorez les informations dans la moitié supérieure du panneau, puis cliquez sur **fonction personnalisée**, située près du bas (dans la zone bleue, comme ci-dessous).

    ![fonction personnalisée](images/AzureLabs-Lab8-38.png)

13. La nouvelle page de la fenêtre affiche différents types de fonction. Faites défiler la liste pour afficher les types violets, puis cliquez sur élément **http put** .

    ![lien http put](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Vous devrez peut-être faire défiler la page vers le bas (et cette image risque de ne pas être exactement la même, si les mises à jour du portail Azure ont eu lieu). Toutefois, vous recherchez un élément appelé *http put*.

14. La fenêtre **http put** s’affiche, dans laquelle vous devez configurer la fonction (Voir l’image ci-dessous).

    1.  Pour **langue,** dans le menu déroulant, sélectionnez C \# .

    2.  Pour **nom,** entrez un nom approprié.

    3.  Dans le menu déroulant **niveau d’authentification** , sélectionnez **fonction**.

    4.  Pour la section nom de la **table** , vous devez utiliser le nom exact que vous avez utilisé pour créer le service de **table** précédemment (y compris la même casse).

    5.  dans la section **connexion au compte Stockage** , utilisez le menu déroulant, puis sélectionnez votre compte de stockage. Si ce n’est pas le cas, cliquez sur **le lien hypertexte** à côté du titre de la section pour afficher un autre panneau, où votre compte de stockage doit être listé.

        ![nouveau stockage](images/AzureLabs-Lab8-40.png)

15. Cliquez sur **créer** . vous recevrez une notification indiquant que vos paramètres ont été correctement mis à jour.

    ![créer une fonction](images/AzureLabs-Lab8-41.png)

16. Après avoir cliqué sur **créer**, vous êtes redirigé vers l’éditeur de fonction.

    ![mettre à jour le code de fonction](images/AzureLabs-Lab8-42.png)

17. Insérez le code suivant dans l’éditeur de fonction (en remplaçant le code dans la fonction) :

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > À l’aide des bibliothèques incluses, la fonction reçoit le nom et l’emplacement de l’objet qui a été déplacé dans la scène Unity (en tant qu’objet C#, appelé **UnityGameObject**). Cet objet est ensuite utilisé pour mettre à jour les paramètres d’objet dans la table créée. Après cela, la fonction effectue un appel à votre service de notification Hub créé, qui avertit toutes les applications abonnées.

18. Avec le code en place, cliquez sur **Enregistrer**.

19. Ensuite, cliquez sur l' **\<** icône (flèche), sur le côté droit de la page.

    ![ouvrir le panneau de chargement](images/AzureLabs-Lab8-43.png)

20. Un panneau s’affiche à partir de la droite. dans ce panneau, cliquez sur **Télécharger** et un explorateur de fichiers s’affiche.

21. accédez à, puis cliquez sur le fichier **project.js** , que vous avez créé dans **Bloc-notes** précédemment, puis cliquez sur le bouton **ouvrir** . Ce fichier définit les bibliothèques que votre fonction utilisera.

    ![Télécharger JSON](images/AzureLabs-Lab8-44.png)

22. Une fois le fichier chargé, il s’affiche dans le volet de droite. Cliquez dessus pour l’ouvrir dans l’éditeur de **fonctions** . Elle doit ressembler **exactement** à l’image suivante (sous l’étape 23).

23. Ensuite, dans le volet de gauche, sous **fonctions**, cliquez sur le lien **intégrer** .

    ![fonction d’intégration](images/AzureLabs-Lab8-45.png)

24. Sur la page suivante, dans le coin supérieur droit, cliquez sur **éditeur avancé** (comme ci-dessous).

    ![ouvrir l’éditeur avancé](images/AzureLabs-Lab8-46.png)

25. Un **function.jssur** le fichier s’ouvre dans le panneau central, qui doit être remplacé par l’extrait de code suivant. Cela définit la fonction que vous générez et les paramètres transmis à la fonction.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. Votre éditeur doit maintenant ressembler à l’image ci-dessous :

    ![Retour à l’éditeur standard](images/AzureLabs-Lab8-47.png)

27. Vous pouvez remarquer que les paramètres d’entrée que vous venez d’insérer ne correspondent pas à votre table et à vos détails de stockage et doivent donc être mis à jour avec vos informations. N' **effectuez pas cette opération ici**, car elle est décrite ci-dessous. Cliquez simplement sur le lien **éditeur standard** , dans le coin supérieur droit de la page, pour revenir en arrière.

28. de retour dans l' **éditeur Standard**, cliquez sur **table Stockage (table) Azure**, sous **entrées**. 
    
    ![Entrées de table](images/AzureLabs-Lab8-47-5.png)

29. Vérifiez que les informations suivantes correspondent à **vos** informations, car elles peuvent être différentes (une image est présente en dessous des étapes suivantes) :

    1.  **nom** de la table : nom de la table que vous avez créée dans votre stockage Azure, service de Tables.

    2.  **Stockage la connexion au compte :** cliquez sur **nouveau**, qui apparaît en regard du menu déroulant, et un panneau s’affiche à droite de la fenêtre.

        ![nouveau stockage](images/AzureLabs-Lab8-48.png)

        1.  sélectionnez votre **compte de Stockage** que vous avez créé précédemment pour héberger les **applications de fonction.**

        2. vous remarquerez que la valeur de la connexion au **compte Stockage** a été créée.

        3. Veillez à cliquer sur **Enregistrer** une fois que vous avez terminé.

    3.  La page **entrées** doit maintenant correspondre aux informations ci-dessous, qui illustrent **vos** informations.

        ![entrées terminées](images/AzureLabs-Lab8-49.png)

30. Ensuite, cliquez sur **Azure notification Hub (notification)** -sous **sorties**. Assurez-vous que les éléments suivants sont mis en correspondance avec **vos** informations, car ils peuvent être différents (une image est présente en dessous des étapes suivantes) :

    1.  **Nom du Hub de notification**: il s’agit du nom de l’instance de service de votre **Hub de notification** que vous avez créée précédemment.

    2.  **Notification hubs la connexion** à l’espace de noms : cliquez sur **nouveau**, qui apparaît en regard du menu déroulant.

        ![vérifier les sorties](images/AzureLabs-Lab8-50.png)

    3. La fenêtre contextuelle de **connexion** s’affiche (Voir l’image ci-dessous), où vous devez sélectionner l' **espace de noms** du **Hub de notification** que vous avez configuré précédemment.

    4. Sélectionnez le nom de votre **Hub de notification** dans le menu déroulant du milieu.

    5.  Définissez le menu déroulant **stratégie** sur **DefaultFullSharedAccessSignature**.

    6. Cliquez sur le bouton **Sélectionner** pour revenir en arrière.

        ![mise à jour de sortie](images/AzureLabs-Lab8-51.png)

31.  La page **sorties** doit maintenant correspondre aux informations ci-dessous, mais avec **vos** informations à la place. Veillez à cliquer sur **Enregistrer**.

> [!WARNING]
> *Ne modifiez pas directement le nom du Hub de notification* (cette opération doit être effectuée à l’aide de la **éditeur avancé**, à condition que vous ayez suivi correctement les étapes précédentes.

![sorties terminées](images/AzureLabs-Lab8-50.png)

32. À ce stade, vous devez tester la fonction pour vous assurer qu’elle fonctionne. Pour ce faire : 

    1. Accédez à la page de fonction une fois de plus :

        ![sorties terminées](images/AzureLabs-Lab8-50-1.png)

    2. De retour dans la page de fonction, cliquez sur l’onglet **test** situé à l’extrême droite de la page pour ouvrir le panneau *test* :

        ![sorties terminées](images/AzureLabs-Lab8-50-2.png)

    3. Dans la zone de texte **requête Body** du panneau, collez le code ci-dessous :

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. Une fois le code de test en place, cliquez sur le bouton **exécuter** en bas à droite pour exécuter le test. Les journaux de sortie du test s’affichent dans la zone de la console, sous le code de votre fonction.

        ![sorties terminées](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Si le test ci-dessus échoue, vous devez vérifier exactement que vous avez suivi les étapes ci-dessus, en particulier les paramètres dans le **panneau intégrer**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Chapitre 7-configurer l’unité de travail Project

> [!IMPORTANT]
> L’application de bureau que vous créez maintenant ne fonctionne **pas** dans l’éditeur Unity. elle doit être exécutée en dehors de l’éditeur, après la génération de l’application, à l’aide de Visual Studio (ou de l’application déployée). 

Voici une configuration standard pour le développement avec Unity et la réalité mixte, et en tant que tel, est un bon modèle pour d’autres projets.

Configurez et testez votre casque immersif en réalité mixte.

> [!NOTE] 
> Vous n’aurez **pas** besoin de contrôleurs de mouvement pour ce cours. Si vous avez besoin de la prise en charge de la configuration du casque immersif, suivez ce [lien pour savoir comment configurer Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Ouvrez **Unity** et cliquez sur **nouveau**.

    ![nouveau projet Unity](images/AzureLabs-Lab8-52.png)

2.  vous devez fournir un nom de Project unity, insérer **UnityDesktopNotifHub**. Assurez-vous que le type de projet est défini sur **3D**. Définissez l' **emplacement** approprié pour vous (n’oubliez pas que les répertoires racine sont mieux adaptés). Ensuite, cliquez sur **créer un projet**.

    ![créer un projet](images/AzureLabs-Lab8-53.png)

3.  Si Unity est ouvert, il est conseillé de vérifier que l' **éditeur de script** par défaut est défini sur **Visual Studio**. Accédez à **modifier**  >  les **Préférences** , puis à partir de la nouvelle fenêtre, accédez à **outils externes**. modifiez l' **éditeur de Script externe** pour **Visual Studio 2017**. Fermez la fenêtre **Préférences** .

    ![définir les outils VS externes](images/AzureLabs-Lab8-54.png)

4.  ensuite, accédez à **fichier**  >  **Build Paramètres** et sélectionnez **plateforme Windows universelle**, puis cliquez sur le bouton **Switch Platform** pour appliquer votre sélection.

    ![changer de plateformes](images/AzureLabs-Lab8-55.png)

5.  pendant la Paramètres de la génération de **fichiers**, assurez-vous  >  que :

    1.  L' **appareil cible** est défini sur **n’importe quel appareil**

        > Cette application sera destinée à votre bureau. doit donc être **n’importe quel appareil**

    2.  Le **type de build** est **D3D**

    3.  Le **SDK** est configuré sur le **dernier installé**

    4.  **Visual Studio Version** est définie sur le **plus récent**

    5.  La **génération et l’exécution** sont définies sur l' **ordinateur local**

    6.  Dans ce cas, il convient d’enregistrer la scène et de l’ajouter à la Build.

        1. Pour ce faire, sélectionnez **Ajouter des scènes ouvertes**. Une fenêtre d’enregistrement s’affiche.

            ![Ajouter des scènes ouvertes](images/AzureLabs-Lab8-56.png)

        2. Créez un dossier pour cela, ainsi que toute nouvelle scène, puis sélectionnez le bouton **nouveau dossier** pour créer un nouveau dossier, puis nommez-le **scenes**.

            ![nouveau dossier scenes](images/AzureLabs-Lab8-57.png)

        3. Ouvrez le dossier **scenes** nouvellement créé, puis dans le champ **nom de fichier :** texte, **tapez \_ NH Desktop \_ Scene**, puis cliquez sur **Enregistrer**.

            ![nouvelle NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  dans les **Paramètres de Build**, les paramètres restants doivent être conservés comme valeurs par défaut pour le moment.

6.  dans la même fenêtre, cliquez sur le bouton **Paramètres du lecteur** pour ouvrir le panneau correspondant dans l’espace où se trouve l' **inspecteur** .

7.  Dans ce volet, quelques paramètres doivent être vérifiés :

    1.  dans l' **autre onglet Paramètres** :

        1.  La **version du runtime de script** doit être **expérimentale (équivalent .net 4,6)**

        2. Le **backend de script** doit être **.net**

        3. Le **niveau de compatibilité** de l’API doit être **.net 4,6**

            ![version .net 4,6](images/AzureLabs-Lab8-59.png)

    2.  dans l’onglet **Paramètres de publication** , sous **fonctionnalités**, vérifiez :

        - **InternetClient**

            ![client Internet Tick](images/AzureLabs-Lab8-60.png)

8.  de retour dans la **génération Paramètres** les *\# projets unity C* ne sont plus grisés. cochez la case en regard de cette option.

9.  Fermez la fenêtre **Build Settings**.

10. enregistrez votre scène et Project **fichier**  >  **enregistrer la séquence** de  >  **Project enregistrer** la scène/le fichier.

    > [!IMPORTANT]
    > Si vous souhaitez ignorer le composant *Unity Set up* pour ce projet (application de bureau) et continuer directement dans le code, n’hésitez pas à [Télécharger ce fichier. pour Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), à l’importer dans votre projet en tant que [**package personnalisé**](https://docs.unity3d.com/Manual/AssetPackages.html), puis à continuer à partir du [chapitre 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  Vous devrez toujours ajouter les composants script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Chapitre 8-importation des dll dans Unity

vous utiliserez stockage Azure pour unity (qui utilise lui-même le kit de développement logiciel (SDK) .net pour Azure). pour plus d’informations, consultez ce [lien à propos de stockage Azure pour unity](/sandbox/gamedev/unity/azure-storage-unity).

Il existe actuellement un problème connu dans Unity qui nécessite que les plug-ins soient reconfigurés après l’importation. Ces étapes (4-7 dans cette section) ne sont plus nécessaires une fois que le bogue a été résolu.

Pour importer le kit de développement logiciel (SDK) dans votre propre projet, assurez-vous d’avoir téléchargé la dernière version de [**pour Unity**](https://aka.ms/azstorage-unitysdk) à partir de github. Ensuite, procédez comme suit :

1.  Ajoutez le fichier **. pour Unity** à Unity à l’aide de l’option de menu **\> \> package personnalisé du package d’importation de ressources** .

2.  dans la zone **importer le Package unity** qui s’affiche, vous pouvez sélectionner tous les éléments sous * *_plug-in_ * \> Stockage * * *.  Décochez tout le reste, car il n’est pas nécessaire pour ce cours.

    ![importer dans le package](images/AzureLabs-Lab8-61.png)

3.  Cliquez sur le bouton ***Importer*** pour ajouter les éléments à votre projet.

4.  accédez au dossier **Stockage** sous **plug-ins** dans la vue Project et sélectionnez les plug-ins suivants *uniquement*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![décocher une plateforme](images/AzureLabs-Lab8-62.png)

5.  Une fois *ces plug-ins spécifiques* sélectionnés, **décochez** **toutes les plateformes** et **décochez** **WSAPlayer** , puis cliquez sur **appliquer**.

    ![appliquer des dll de plateforme](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Nous marqueons ces plug-ins particuliers à utiliser uniquement dans l’éditeur Unity. Cela est dû au fait qu’il existe différentes versions des mêmes plug-ins dans le dossier WSA qui seront utilisées après l’exportation du projet à partir d’Unity.

6.  dans le dossier du plug-in **Stockage** , sélectionnez uniquement :

    -   Microsoft.Data.Services.Client

        ![définir ne pas traiter pour les dll](images/AzureLabs-Lab8-64.png)

7.  cochez la case **ne pas traiter** sous Paramètres de la **plateforme** , puis cliquez sur **_appliquer_**.

    ![ne pas appliquer de traitement](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Nous marquant ce plug-in « ne pas traiter », car l’assembly Unity Patcher a des difficultés à traiter ce plug-in. Le plug-in fonctionne toujours même s’il n’est pas traité.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Chapitre 9-créer la classe TableToScene dans le projet Unity de bureau

Vous devez maintenant créer les scripts contenant le code pour exécuter cette application.

Le premier script que vous devez créer est **TableToScene**, qui est responsable des opérations suivantes :

-   Lecture des entités dans la table Azure.
-   À l’aide des données de la table, déterminez les objets à générer et leur position.

Le deuxième script que vous devez créer est **CloudScene**, qui est responsable des opérations suivantes :

-   Inscription de l’événement de clic gauche pour permettre à l’utilisateur de faire glisser des objets autour de la scène.
-   Sérialisation des données d’objet à partir de cette scène Unity et envoi de celles-ci au Function App Azure.

Pour créer cette classe :

1.  cliquez avec le bouton droit sur le dossier **Asset** situé dans le panneau Project, puis **créez** le  >  **dossier**. Nommez le dossier **scripts**.

    ![créer un dossier de scripts](images/AzureLabs-Lab8-66.png)

    ![créer un dossier de scripts 2](images/AzureLabs-Lab8-67.png)

2.  Double-cliquez sur le dossier que vous venez de créer pour l’ouvrir.

3.  Cliquez avec le bouton droit dans le dossier **scripts** , puis cliquez sur **créer** un  >  **script C#**. Nommez le script **TableToScene**.

    ![nouveau script c# ](images/AzureLabs-Lab8-68.png)
     ![ TableToScene renommer](images/AzureLabs-Lab8-69.png)

4.  Double-cliquez sur le script pour l’ouvrir dans Visual Studio 2017.

5.  Ajoutez les espaces de noms suivants :

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  Dans la classe, insérez les variables suivantes :

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > remplacez la valeur **accountName** par le nom de votre Service stockage Azure et la valeur **accountKey** par la valeur de clé trouvée dans le service stockage Azure, dans le portail Azure (voir l’Image ci-dessous). 
    >
    > ![extraire la clé de compte](images/AzureLabs-Lab8-70.png)

7.  Ajoutez maintenant les méthodes **Start ()** et **éveillé ()** pour initialiser la classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  Dans la classe **TableToScene** , ajoutez la méthode qui permet de récupérer les valeurs de la table Azure et de les utiliser pour générer les primitives appropriées dans la scène.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  En dehors de la classe **TableToScene** , vous devez définir la classe utilisée par l’application pour sérialiser et désérialiser les **entités de table**.

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Veillez à **Enregistrer** avant de revenir à l’éditeur Unity.

11. Cliquez sur la **caméra principale** dans le volet de la **hiérarchie** , afin que ses propriétés s’affichent dans l' **inspecteur**.

12. Le dossier **scripts** étant ouvert, sélectionnez le fichier de script **TableToScene** et faites-le glisser sur l' **appareil photo principal**. Le résultat doit se présenter comme suit :

    ![Ajouter un script à l’appareil photo principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Chapitre 10-créer la classe CloudScene dans le bureau Unity Project

Le deuxième script que vous devez créer est **CloudScene**, qui est responsable des opérations suivantes :

-   Inscription de l’événement de clic gauche pour permettre à l’utilisateur de faire glisser des objets autour de la scène.

-   Sérialisation des données d’objet à partir de cette scène Unity et envoi de celles-ci au Function App Azure.

Pour créer le deuxième script :

1.  Cliquez avec le bouton droit dans le dossier **scripts** , cliquez sur **créer**, puis sur **\# script C**. Nommez le script **CloudScene**
    
    ![nouveau script c#- ](images/AzureLabs-Lab8-72.png)
     ![ Renommer CloudScene](images/AzureLabs-Lab8-73.png)

2.  Ajoutez les espaces de noms suivants :

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Insérez les variables suivantes :

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Remplacez la valeur **azureFunctionEndpoint** par votre URL Azure Function App trouvée dans le Service Azure Function App, dans le portail Azure, comme indiqué dans l’image ci-dessous :

    ![Obtient l’URL de la fonction](images/AzureLabs-Lab8-74.png)

5.  Ajoutez maintenant les méthodes **Start ()** et **éveillé ()** pour initialiser la classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  Dans la méthode **Update ()** , ajoutez le code suivant qui détecte l’entrée de la souris et glissent, ce qui déplace à son tour GameObjects dans la scène. Si l’utilisateur a glissé et supprimé un objet, il passe le nom et les coordonnées de l’objet à la méthode **UpdateCloudScene ()**, qui appelle le service Azure Function App, qui met à jour la table Azure et déclenche la notification.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  Ajoutez maintenant la méthode **UpdateCloudScene ()** , comme indiqué ci-dessous :

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  Enregistrer le code et revenir à Unity

9.  Faites glisser le script **CloudScene** sur l' **appareil photo principal**. 

    1. Cliquez sur la **caméra principale** dans le volet de la **hiérarchie** , afin que ses propriétés s’affichent dans l' **inspecteur**. 

    2. Le dossier **scripts** étant ouvert, sélectionnez le script **CloudScene** et faites-le glisser sur l' **appareil photo principal**. Le résultat doit se présenter comme suit :

        > ![faire glisser le script Cloud sur l’appareil photo principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>chapitre 11-créer le Project de bureau sur UWP

Tout ce qui est nécessaire pour la section Unity de ce projet est maintenant terminé.

1.  accédez à **Paramètres de build** (Paramètres de build de **fichier**  >  ).

2.  dans la fenêtre **Paramètres de build** , cliquez sur **générer**.

    ![générer le projet](images/AzureLabs-Lab8-76.png)

3.  Une fenêtre de l' **Explorateur de fichiers** s’affiche et vous invite à entrer un emplacement à générer. Créez un nouveau dossier (en cliquant sur **nouveau dossier** dans l’angle supérieur gauche), puis nommez-le **Builds**.

    ![nouveau dossier pour la Build](images/AzureLabs-Lab8-77.png)

    1.  Ouvrez le nouveau dossier **Builds** , puis créez un autre dossier (à l’aide d’un **nouveau dossier** ) et nommez-le **NH \_ \_**.

        ![nom du dossier NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Avec l' **\_ \_ application de bureau NH** sélectionnée. Cliquez sur **Sélectionner un dossier**. La génération du projet prendra quelques minutes.

4.  Après la génération, l' **Explorateur de fichiers** s’affiche et vous indique l’emplacement de votre nouveau projet. Toutefois, il n’est pas nécessaire de l’ouvrir, car vous devez d’abord créer l’autre projet Unity, dans les chapitres suivants.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Chapitre 12-configurer une Unity de réalité mixte Project

Ce qui suit est une configuration classique pour le développement avec la réalité mixte, et, par conséquent, est un bon modèle pour d’autres projets.

1.  Ouvrez **Unity** et cliquez sur **nouveau**.

    ![nouveau projet Unity](images/AzureLabs-Lab8-79.png)

2.  vous devez maintenant fournir un nom de Project unity, insert **UnityMRNotifHub**. Assurez-vous que le type de projet est défini sur **3D**. Définissez l' **emplacement** approprié pour vous (n’oubliez pas que les répertoires racine sont mieux adaptés). Ensuite, cliquez sur **créer un projet**.

    ![nom UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Si Unity est ouvert, il est conseillé de vérifier que l' **éditeur de script** par défaut est défini sur **Visual Studio**. Accédez à **modifier**  >  les **Préférences** , puis à partir de la nouvelle fenêtre, accédez à **outils externes**. modifiez l' **éditeur de Script externe** pour **Visual Studio 2017**. Fermez la fenêtre **Préférences** .

    ![définir l’éditeur externe sur VS](images/AzureLabs-Lab8-81.png)

4.  ensuite, accédez à **fichier**  >  **Build Paramètres** et basculez la plateforme sur **plateforme Windows universelle**, en cliquant sur le bouton **changer de plateforme** .

    ![basculer les plateformes sur UWP](images/AzureLabs-Lab8-82.png)

5.  accédez à Paramètres de Build de **fichier** et assurez-vous  >   que :

    1.  L' **appareil cible** est défini sur **n’importe quel appareil**

        > pour le Microsoft HoloLens, définissez **appareil cible** sur *HoloLens*.

    2.  Le **type de build** est **D3D**

    3.  Le **SDK** est configuré sur le **dernier installé**

    4.  **Visual Studio Version** est définie sur le **plus récent**

    5.  La **génération et l’exécution** sont définies sur l' **ordinateur local**

    6.  Dans ce cas, il convient d’enregistrer la scène et de l’ajouter à la Build.

        1. Pour ce faire, sélectionnez **Ajouter des scènes ouvertes**. Une fenêtre d’enregistrement s’affiche.

            ![Ajouter des scènes ouvertes](images/AzureLabs-Lab8-83.png)

        2. Créez un dossier pour cela, ainsi que toute nouvelle scène, puis sélectionnez le bouton **nouveau dossier** pour créer un nouveau dossier, puis nommez-le **scenes**.

            ![nouveau dossier scenes](images/AzureLabs-Lab8-84.png)

        3. Ouvrez le dossier **scenes** nouvellement créé, puis dans le champ **nom de fichier :** texte, **tapez \_ NH Mr \_ Scene**, puis cliquez sur **Enregistrer**.

            ![nouvelle scène-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  dans les **Paramètres de Build**, les paramètres restants doivent être conservés comme valeurs par défaut pour le moment.

6.  dans la même fenêtre, cliquez sur le bouton **Paramètres du lecteur** pour ouvrir le panneau correspondant dans l’espace où se trouve l' **inspecteur** .    

    ![ouvrir les paramètres du lecteur](images/AzureLabs-Lab8-86.png)

7.  Dans ce volet, quelques paramètres doivent être vérifiés :

    1.  dans l' **autre onglet Paramètres** :

        1.  La **version du runtime de script** doit être **expérimentale** (équivalent .net 4,6)
        2.  Le **backend de script** doit être **_.net_**
        3.  Le **niveau de compatibilité** de l’API doit être **.net 4,6**

            ![compatibilité des API](images/AzureLabs-Lab8-87.png)

    2.  plus bas dans le volet, dans **XR Paramètres** (situé sous **publier Paramètres**), cochez **réalité virtuelle prise en charge**, assurez-vous que le kit de **développement logiciel (SDK) Windows Mixed Reality** est ajouté

        ![mettre à jour les paramètres XR](images/AzureLabs-Lab8-88.png)        

    3.  dans l’onglet **Paramètres de publication** , sous **fonctionnalités**, conversez-le :

        - **InternetClient**           

            ![client Internet Tick](images/AzureLabs-Lab8-89.png)

8.  de retour dans le **Paramètres de Build**, les **projets unity C#** ne sont plus grisés : cochez la case en regard de cette option.

9.  une fois ces modifications effectuées, fermez la fenêtre de Paramètres de Build.

10. enregistrez votre scène et Project **fichier**  >  **enregistrer la séquence** de  >  **Project enregistrer** la scène/le fichier.

    > [!IMPORTANT]
    > Si vous souhaitez ignorer le composant *Unity Set up* pour ce projet (application de réalité mixte) et continuer directement dans le code, n’hésitez pas à [Télécharger ce fichier. pour Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), à l’importer dans votre projet en tant que [**package personnalisé**](https://docs.unity3d.com/Manual/AssetPackages.html), puis à continuer à partir du [chapitre 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Vous devrez toujours ajouter les composants script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Chapitre 13-importation des dll dans l’Unity de réalité mixte Project

vous utiliserez stockage Azure pour la bibliothèque unity (qui utilise le kit de développement logiciel (SDK) .net pour Azure). pour plus d' [informations sur l’utilisation de stockage Azure avec unity](/sandbox/gamedev/unity/azure-storage-unity), suivez ce lien.
Il existe actuellement un problème connu dans Unity qui nécessite que les plug-ins soient reconfigurés après l’importation. Ces étapes (4-7 dans cette section) ne sont plus nécessaires une fois que le bogue a été résolu.

Pour importer le kit de développement logiciel (SDK) dans votre propre projet, assurez-vous d’avoir téléchargé la dernière version de [. pour Unity](https://aka.ms/azstorage-unitysdk). Ensuite, procédez comme suit :

1.  Ajoutez le fichier. pour Unity que vous avez téléchargé à partir de la version ci -dessus, à Unity à l’aide de l’option de  >    >  menu **package personnalisé** du package d’importation de ressources.

2.  dans la zone **importer le Package unity** qui s’affiche, vous pouvez sélectionner tout dans le **plug-in**  >  **Stockage**.

    ![importer un package](images/AzureLabs-Lab8-90.png)

3.  Cliquez sur le bouton **Importer** pour ajouter les éléments à votre projet.

4.  accédez au dossier **Stockage** sous **plug-ins** dans la vue Project et sélectionnez les plug-ins suivants *uniquement*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![sélectionner les plug-ins](images/AzureLabs-Lab8-91.png)

5.  Une fois *ces plug-ins spécifiques* sélectionnés, **décochez** **toutes les plateformes** et **décochez** **WSAPlayer** , puis cliquez sur **appliquer**.

    ![appliquer les modifications de la plateforme](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Vous marquez ces plug-ins particuliers à utiliser uniquement dans l’éditeur Unity. Cela est dû au fait qu’il existe différentes versions des mêmes plug-ins dans le dossier WSA qui seront utilisées après l’exportation du projet à partir d’Unity.

6.  dans le dossier du plug-in **Stockage** , sélectionnez uniquement :

    -   Microsoft.Data.Services.Client

        ![sélectionner le client des services de données](images/AzureLabs-Lab8-93.png)

7.  cochez la case **ne pas traiter** sous Paramètres de la **plateforme** , puis cliquez sur **appliquer**.

    ![ne pas traiter](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Vous marquez ce plug-in « ne pas traiter », car l’assembly Unity Patcher a des difficultés à traiter ce plug-in. Le plug-in fonctionne toujours même s’il n’est pas traité.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Chapitre 14-création de la classe TableToScene dans le projet Unity de réalité mixte

La classe **TableToScene** est identique à celle expliquée dans le [chapitre 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project). créez la même classe dans l’unity de réalité mixte Project suivant la même procédure que celle expliquée dans le [chapitre 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).

Une fois que vous aurez terminé ce chapitre, cette classe sera configurée sur l’appareil photo de vos **projets Unity** .

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Chapitre 15-création de la classe NotificationReceiver dans l’Unity de réalité mixte Project

Le deuxième script que vous devez créer est **NotificationReceiver**, qui est responsable des opérations suivantes :

-   Inscription de l’application auprès du Hub de notification lors de l’initialisation.
-   Écoute des notifications provenant du Hub de notification.
-   Désérialisation des données d’objet à partir des notifications reçues.
-   Déplacez le GameObjects dans la scène, en fonction des données désérialisées.

Pour créer le script **NotificationReceiver** :

1.  Cliquez avec le bouton droit dans le dossier **scripts** , cliquez sur **créer**, puis sur **\# script C**. Nommez le script **NotificationReceiver**.

    ![créer un nouveau nom de script c# ](images/AzureLabs-Lab8-95.png)
     ![ NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  Double-cliquez sur le script pour l’ouvrir.

3.  Ajoutez les espaces de noms suivants :

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  Insérez les variables suivantes :

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Remplacez la valeur **hubName** par le nom de votre service de hub de notification et la valeur de **hubListenEndpoint** par la valeur de point de terminaison de l’onglet stratégies d’accès, service Azure notification Hub, dans le portail Azure (Voir l’image ci-dessous).

    ![Insérer un point de terminaison de stratégie notification hubs](images/AzureLabs-Lab8-97.png)

6.  Ajoutez maintenant les méthodes **Start ()** et **éveillé ()** pour initialiser la classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  Ajoutez la méthode **WaitForNotification** pour permettre à l’application de recevoir des notifications de la bibliothèque du Hub de notification sans entrer en conflit avec le thread principal :

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  La méthode suivante, **InitNotificationAsync ()**, inscrit l’application auprès du service de notification Hub lors de l’initialisation. Le code est commenté, car Unity ne sera pas en mesure de générer le projet. Vous allez supprimer les commentaires lorsque vous importez le package NuGet Azure Messaging dans Visual Studio.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  Le gestionnaire suivant, **Channel \_ PushNotificationReceived ()**, est déclenché chaque fois qu’une notification est reçue. Elle désérialisera la notification, qui sera l’entité de table Azure qui a été déplacée sur l’application de bureau, puis déplace le GameObject correspondant dans la scène MR vers la même position. 
    
    > [!IMPORTANT]
    > le code est mis en commentaire, car le code fait référence à la bibliothèque de messagerie Azure, que vous ajouterez après avoir créé le projet unity à l’aide de la Gestionnaire de package Nuget, dans Visual Studio. Par conséquent, le projet Unity ne sera pas en mesure de générer, sauf s’il est mis en commentaire. N’oubliez pas que si vous générez votre projet et que vous souhaitez ensuite revenir à Unity, vous devez ajouter **un nouveau commentaire** à ce code.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. N’oubliez pas d’enregistrer vos modifications avant de revenir à l’éditeur Unity.

11. Cliquez sur la **caméra principale** dans le volet de la **hiérarchie** , afin que ses propriétés s’affichent dans l' **inspecteur**.

12. Le dossier **scripts** étant ouvert, sélectionnez le script **NotificationReceiver** et faites-le glisser sur l' **appareil photo principal**. Le résultat doit se présenter comme suit :

    ![faire glisser le script du récepteur de notification vers l’appareil photo](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > si vous développez ceci pour la Microsoft HoloLens, vous devez mettre à jour le composant *camera* de l' **appareil photo principal**, afin que :
    > - Indicateurs d’effacement : couleur unie
    > - Arrière-plan : Noir

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>chapitre 16 : créer la Project de la réalité mixte sur UWP

Ce chapitre est identique au processus de génération pour le projet précédent. Tout ce qui est nécessaire pour la section Unity de ce projet est maintenant terminé. il est donc temps de la générer à partir d’Unity.

1.  accédez à **Paramètres de build** (Paramètres de build de **fichier**  >   ).

2.  dans le menu **générer Paramètres** , assurez-vous que **unity C# projects*** est coché (ce qui vous permettra de modifier les scripts de ce projet, après la génération).

3.  Une fois cette opération terminée, cliquez sur **générer**.

    ![générer le projet](images/AzureLabs-Lab8-99.png)

4.  Une fenêtre de l' **Explorateur de fichiers** s’affiche et vous invite à entrer un emplacement à générer. Créez un nouveau dossier (en cliquant sur **nouveau dossier** dans l’angle supérieur gauche), puis nommez-le **Builds**.

    ![créer un dossier Builds](images/AzureLabs-Lab8-100.png)

    1.  Ouvrez le nouveau dossier **Builds** , puis créez un autre dossier (à l’aide d’un **nouveau dossier** ) et nommez-le **NH \_ m \_ application**.

        ![créer un dossier NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  L' **application NH \_ Mr \_** est sélectionnée. Cliquez sur **Sélectionner un dossier**. La génération du projet prendra quelques minutes.

5.  Après la génération, une fenêtre de l' **Explorateur de fichiers** s’ouvre à l’emplacement de votre nouveau projet.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>chapitre 17-ajouter des packages de NuGet à la Solution UnityMRNotifHub

> [!WARNING] 
> n’oubliez pas que, une fois que vous avez ajouté les Packages de NuGet suivants (et que vous supprimez les commentaires du code dans le [chapitre](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)suivant), le code, lorsqu’il est rouvert dans l’unity Project, présente des erreurs. Si vous souhaitez revenir en arrière et poursuivre la modification dans l’éditeur Unity, vous avez besoin d’un commentaire qui errosome le code, puis de supprimer les marques de commentaire ultérieurement, une fois que vous êtes à nouveau dans Visual Studio. 

une fois la génération de la réalité mixte terminée, accédez au projet de réalité mixte, que vous avez créé, puis double-cliquez sur le fichier de solution (. sln) dans ce dossier pour ouvrir votre solution avec Visual Studio 2017.
vous devez maintenant ajouter le package de NuGet **WindowsAzure. messaging. managed** . Il s’agit d’une bibliothèque qui est utilisée pour recevoir des notifications du Hub de notification.

pour importer le package de NuGet :

1.  Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur votre solution

2.  cliquez sur **gérer les Packages de NuGet**.

    ![Ouvrez le gestionnaire NuGet](images/AzureLabs-Lab8-102.png)

3.  Sélectionnez l’onglet ***Browse** _ et recherchez _ * WindowsAzure. Messaging. Managed * *.

    ![Rechercher le package de messagerie Windows Azure](images/AzureLabs-Lab8-103.png)

4.  Sélectionnez le résultat (comme indiqué ci-dessous) et, dans la fenêtre de droite, activez la case à cocher en regard de **Project**. cela place une coche dans la case à cocher en regard de **Project**, ainsi que la case à cocher en regard du projet **assembly-CSharp** et **UnityMRNotifHub** .

    ![cocher tous les projets](images/AzureLabs-Lab8-104.png)

5.  La version initialement fournie **n’est peut-être pas** compatible avec ce projet. Par conséquent, cliquez sur le menu déroulant en regard de **version**, puis cliquez sur **version 0.1.7.9**, puis sur **installer**.

6.  vous avez maintenant terminé l’installation du package de NuGet. Recherchez le code commenté que vous avez entré dans la classe **NotificationReceiver** et supprimez les commentaires.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Chapitre 18-modifier l’application UnityMRNotifHub, classe NotificationReceiver

après avoir ajouté les **Packages NuGet**, vous devez supprimer les *marques de commentaire* du code dans la classe **NotificationReceiver** .

notamment :

1. Espace de noms en haut :

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Tout le code dans la méthode **InitNotificationsAsync ()** :

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> Le code ci-dessus contient un commentaire : Assurez-vous que vous n’avez *pas accidentellement supprimé le commentaire de ce* commentaire (car le code ne se compilera pas si vous en avez !).

3. Enfin, l’événement **Channel_PushNotificationReceived** :

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

Avec ces commentaires, veillez à enregistrer, puis passez au chapitre suivant.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Chapitre 19-associer le projet de réalité mixte à l’application du Windows Store

Vous devez maintenant associer le projet de **réalité mixte** à l’application du Windows Store que vous avez créée dans au début du laboratoire.

1.  Ouvrez la solution.

2.  cliquez avec le bouton droit sur l’application UWP Project dans le panneau Explorateur de solutions, accédez à **store** et **associez l’application au store...**.

    ![ouvrir l’Association de magasins](images/AzureLabs-Lab8-105.png)

3.  une nouvelle fenêtre s’affiche, appelée **associer votre application au magasin de Windows**. Cliquez sur **Suivant**.

    ![accéder à l’écran suivant](images/AzureLabs-Lab8-106.png)

4.  Il charge toutes les applications associées au compte que vous avez connecté. Si vous n’êtes pas connecté à votre compte, vous pouvez vous **connecter** à cette page.

5.  Recherchez le **nom** de l’application Windows Store que vous avez créé au début de ce didacticiel et sélectionnez-le. Cliquez ensuite sur **Suivant**.

    ![Recherchez et sélectionnez le nom de votre boutique](images/AzureLabs-Lab8-107.png)

6.  Cliquez sur **Associer**.

    ![associer l’application](images/AzureLabs-Lab8-108.png)

7.  Votre application est maintenant **associée** à l’application du Windows Store. Cela est nécessaire pour activer les notifications.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Chapitre 20 : déployer des applications UnityMRNotifHub et UnityDesktopNotifHub

Ce chapitre peut être plus facile avec deux personnes, car le résultat inclut les applications en cours d’exécution, l’une s’exécutant sur le Bureau de votre ordinateur et l’autre au sein de votre casque immersif.

L’application de casque immersif attend de recevoir les modifications apportées à la scène (modifications de position du GameObjects local) et l’application de bureau apporte des modifications à leur scène locale (modifications de position), qui sont partagées avec l’application RM. Il est logique de déployer l’application RM en premier, puis l’application de bureau, afin que le récepteur puisse commencer à écouter.

Pour déployer l’application **UnityMRNotifHub** sur votre ordinateur local :

1.  ouvrez le fichier solution de votre application **UnityMRNotifHub** dans **Visual Studio 2017**.

2.  Dans la **plateforme** de la solution, sélectionnez **x86, ordinateur local**.

3.  Dans la **configuration** de la solution, sélectionnez **Déboguer**.

    ![définir la configuration du projet](images/AzureLabs-Lab8-109.png)

4.  Accédez au **menu Générer** , puis cliquez sur **déployer la solution** pour chargement l’application sur votre ordinateur.

5.  Votre application doit maintenant apparaître dans la liste des applications installées, prêtes à être lancées.

Pour déployer l’application **UnityDesktopNotifHub** sur l’ordinateur local :

1.  ouvrez le fichier solution de votre application **UnityDesktopNotifHub** dans **Visual Studio 2017**.

2.  Dans la **plateforme** de la solution, sélectionnez **x86, ordinateur local**.

3.  Dans la **configuration** de la solution, sélectionnez **Déboguer**.

    ![définir la configuration du projet](images/AzureLabs-Lab8-110.png)

4.  Accédez au **menu Générer** , puis cliquez sur **déployer la solution** pour chargement l’application sur votre ordinateur.

5.  Votre application doit maintenant apparaître dans la liste des applications installées, prêtes à être lancées.

6.  Lancez l’application de réalité mixte, suivie de l’application de bureau.

Une fois les deux applications en cours d’exécution, déplacez un objet dans la scène du Bureau (à l’aide du bouton gauche de la souris). Ces modifications positionnelles seront effectuées localement, sérialisées et envoyées au service Function App. Le service de Function App met ensuite à jour la table avec le hub de notification. Une fois la mise à jour reçue, le hub de notification envoie les données mises à jour directement à toutes les applications inscrites (dans ce cas, l’application du casque immersif), qui désérialise ensuite les données entrantes et applique les nouvelles données positionnelles aux objets locaux, en les déplaçant dans la scène.


## <a name="your-finished-your-azure-notification-hubs-application"></a>Votre application Azure Notification Hubs terminée
 
Félicitations, vous avez créé une application de réalité mixte qui tire parti du service Azure Notification Hubs et permet la communication entre les applications.
 
![fin du produit final](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Exercices bonus

### <a name="exercise-1"></a>Exercice 1

Pouvez-vous utiliser la modification de la couleur du GameObjects et envoyer cette notification à d’autres applications en affichant la scène ?

### <a name="exercise-2"></a>Exercice 2

Pouvez-vous ajouter le déplacement du GameObjects à votre application RM et voir la scène mise à jour dans votre application de bureau ?