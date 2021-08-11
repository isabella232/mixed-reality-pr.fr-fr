---
title: HoloLens (1ère génération) et Azure 305 - Fonctions et stockage
description: suivez ce cours pour apprendre à implémenter des stockage Azure et des fonctions dans une application de réalité mixte.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, réalité mixte, academy, unity, didacticiel, api, fonctions, stockage, hololens, immersif, vr, Windows 10, Visual Studio
ms.openlocfilehash: 337b1d3fb23450325805237a6ba975861260760b7d37028b8d717bad99b9d233
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193944"
---
# <a name="hololens-1st-gen-and-azure-305-functions-and-storage"></a>HoloLens (1er génération) et Azure 305 : fonctions et stockage

<br>

>[!NOTE]
>Les tutoriels Mixed Reality Academy ont été conçus pour les appareils HoloLens (1re génération) et les casques immersifs de réalité mixte.  Nous estimons qu’il est important de laisser ces tutoriels à la disposition des développeurs qui recherchent encore des conseils pour développer des applications sur ces appareils.  Notez que ces tutoriels **_ne sont pas_** mis à jour avec les derniers ensembles d’outils ou interactions utilisés pour HoloLens 2.  Ils sont fournis dans le but de fonctionner sur les appareils pris en charge. Une nouvelle série de didacticiels sera publiée à l’avenir qui vous montrera comment développer pour HoloLens 2.  Cet avis sera mis à jour avec un lien vers ces didacticiels lors de leur publication.

<br> 

![produit final-début](images/AzureLabs-Lab5-00.png)

dans ce cours, vous allez apprendre à créer et à utiliser des Azure Functions et à stocker des données avec une ressource de stockage Azure, au sein d’une application de réalité mixte.

*Azure Functions* est un service Microsoft, qui permet aux développeurs d’exécuter de petits morceaux de code, « functions », dans Azure. Cela permet de déléguer le travail au Cloud, plutôt qu’à votre application locale, ce qui peut avoir de nombreux avantages. *Azure Functions* prend en charge plusieurs langages de développement, notamment C \# , F \# , Node.js, Java et php. Pour plus d’informations, consultez l' [article Azure Functions](/azure/azure-functions/functions-overview).

*stockage Azure* est un service cloud de Microsoft, qui permet aux développeurs de stocker des données, avec l’assurance qu’elles seront hautement disponibles, sécurisées, durables, évolutives et redondantes. Cela signifie que Microsoft traitera toutes les tâches de maintenance et les problèmes critiques pour vous. pour plus d’informations, consultez l' [article stockage Azure](/azure/storage/common/storage-introduction).

Une fois ce cours terminé, vous disposerez d’une application de casque immersif en réalité mixte, qui sera en mesure d’effectuer les opérations suivantes :

1.  Permet à l’utilisateur de faire un regard sur une scène.
2.  Déclencher la génération d’objets quand l’utilisateur passe d’un « bouton » en 3D.
3.  Les objets générés sont choisis par une fonction Azure.
4.  à mesure que chaque objet est généré, l’application stocke le type d’objet dans un *fichier Azure*, situé dans *stockage Azure*.
5.  Lors du chargement d’une deuxième fois, les données du *fichier Azure* sont récupérées et utilisées pour relire les actions de génération à partir de l’instance précédente de l’application.

Dans votre application, c’est à vous de savoir comment vous allez intégrer les résultats à votre conception. Ce cours est conçu pour vous apprendre à intégrer un service Azure à votre Project Unity. C’est votre travail d’utiliser les connaissances que vous avez acquises dans ce cours pour améliorer votre application de réalité mixte.

## <a name="device-support"></a>Prise en charge des appareils

<table>
<tr>
<th>Cours</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Casques immersifs</a></th>
</tr><tr>
<td>Réalité mixte - Azure - Cours 305 : Fonctions et stockage</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> bien que ce cours se concentre principalement sur les casques Windows Mixed Reality immersifs, vous pouvez également appliquer ce que vous avez appris dans ce cours à Microsoft HoloLens. À mesure que vous suivez le cours, vous verrez des remarques sur les modifications que vous devrez peut-être utiliser pour prendre en charge HoloLens.

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
- Abonnement à un compte Azure pour la création de ressources Azure
- Accès Internet pour l’installation d’Azure et la récupération de données

## <a name="before-you-start"></a>Avant de commencer

Pour éviter de rencontrer des problèmes lors de la création de ce projet, il est fortement recommandé de créer le projet mentionné dans ce didacticiel dans un dossier racine ou dans un dossier racine (les chemins de dossiers longs peuvent entraîner des problèmes au moment de la génération).

## <a name="chapter-1---the-azure-portal"></a>Chapitre 1-portail Azure

pour utiliser le **Service stockage Azure**, vous devez créer et configurer un **compte Stockage** dans le Portail Azure.

1.  Connectez-vous au  [portail Azure](https://portal.azure.com).

    > [!NOTE]
    > Si vous n’avez pas encore de compte Azure, vous devez en créer un. Si vous suivez ce didacticiel dans une situation de classe ou de laboratoire, demandez à votre formateur ou à l’un des prostructors de vous aider à configurer votre nouveau compte.

2.  une fois que vous êtes connecté, cliquez sur **nouveau** dans l’angle supérieur gauche et recherchez *Stockage compte*, puis cliquez sur **entrée**.

    ![recherche Azure Storage](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > Le mot **nouveau** peut avoir été remplacé par **créer une ressource**, dans les portails plus récents.

3.  la nouvelle page fournit une description du service de *compte stockage Azure* . En bas à gauche de cette invite, sélectionnez le bouton **créer** pour créer une association avec ce service.

    ![créer un service](images/AzureLabs-Lab5-02.png)

4.  Une fois que vous avez cliqué sur **créer**:

    1.  Insérez un *nom* pour votre compte. n’oubliez pas que ce champ accepte uniquement des chiffres et des lettres minuscules.

    2.  Pour *modèle de déploiement*, sélectionnez **Resource Manager**.

    3.  pour *type de compte*, sélectionnez **Stockage (à usage général v1)**.

    4.  Déterminez l' *emplacement* de votre groupe de ressources (si vous créez un groupe de ressources). L’emplacement devrait idéalement se trouver dans la région où l’application s’exécutait. Certaines ressources Azure sont uniquement disponibles dans certaines régions.

    5.  Pour *la réplication* , sélectionnez **Read-Access-géo-redondant Storage (RA-GRS)**.

    6.  Pour *Performances*, sélectionnez **Standard**.

    7.  Laissez le *transfert sécurisé requis* comme **désactivé**.

    8.  Sélectionnez un *Abonnement*.

    9. Choisissez un *groupe de ressources* ou créez-en un. Un groupe de ressources permet de surveiller, de contrôler l’accès, de configurer et de gérer la facturation d’un regroupement de ressources Azure. Il est recommandé de conserver tous les services Azure associés à un seul projet (par exemple, ces laboratoires) sous un groupe de ressources commun). 

        > Si vous souhaitez en savoir plus sur les groupes de ressources Azure, consultez [l’article du groupe de ressources](/azure/azure-resource-manager/resource-group-portal).

    10. Vous devrez également confirmer que vous avez compris les conditions générales appliquées à ce service.

    11. Sélectionnez **Créer**.

        ![informations sur le service d’entrée](images/AzureLabs-Lab5-03.png)

5.  Une fois que vous avez cliqué sur **créer**, vous devez attendre que le service soit créé, cette opération peut prendre une minute.

6.  Une notification s’affichera dans le portail une fois l’instance de service créée.

    ![nouvelle notification dans le portail Azure](images/AzureLabs-Lab5-04.png)

7.  Cliquez sur les notifications pour explorer votre nouvelle instance de service.

    ![accéder à la ressource](images/AzureLabs-Lab5-05.png)

8.  Cliquez sur le bouton **atteindre la ressource** dans la notification pour explorer votre nouvelle instance de service. vous êtes dirigé vers votre nouvelle instance de service de *compte Stockage* .

    ![clés d'accès](images/AzureLabs-Lab5-06.png)

9.  Cliquez sur *clés d’accès* pour afficher les points de terminaison de ce service Cloud. utilisez *Bloc-notes* ou similaire pour copier l’une de vos clés pour une utilisation ultérieure. Notez également la valeur de la *chaîne de connexion* , car elle sera utilisée dans la classe *AzureServices* , que vous allez créer ultérieurement.

    ![copier la chaîne de connexion](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Chapitre 2-Configuration d’une fonction Azure

Vous allez maintenant écrire une  **fonction** Azure dans le service Azure.

Vous pouvez utiliser une **fonction Azure** pour effectuer presque tout ce que vous feriez avec une fonction classique dans votre code, à la différence que cette fonction est accessible par n’importe quelle application disposant d’informations d’identification pour accéder à votre compte Azure.

Pour créer une fonction Azure :

1.  À partir de votre *portail Azure*, cliquez sur **nouveau** dans l’angle supérieur gauche, recherchez *Function App*, puis cliquez sur **entrée**.

    ![créer une application de fonction](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > Le mot **nouveau** peut avoir été remplacé par **créer une ressource**, dans les portails plus récents.

2.  La nouvelle page fournit une description du service *Azure Function App* . En bas à gauche de cette invite, sélectionnez le bouton **créer** pour créer une association avec ce service.

    ![informations sur l’application de fonction](images/AzureLabs-Lab5-09.png)

3.  Une fois que vous avez cliqué sur **créer**:

    1.  Fournissez un *nom d’application*. Seuls des lettres et des chiffres peuvent être utilisés ici (majuscules ou minuscules).

    2.  Sélectionnez votre *abonnement* préféré.

    3. Choisissez un *groupe de ressources* ou créez-en un. Un groupe de ressources permet de surveiller, de contrôler l’accès, de configurer et de gérer la facturation d’un regroupement de ressources Azure. Il est recommandé de conserver tous les services Azure associés à un seul projet (par exemple, ces laboratoires) sous un groupe de ressources commun). 

        > Si vous souhaitez en savoir plus sur les groupes de ressources Azure, consultez [l’article du groupe de ressources](/azure/azure-resource-manager/resource-group-portal).

    4.  pour cet exercice, sélectionnez *Windows* comme **système d’exploitation** choisi.

    5.  Sélectionnez le *plan de consommation* pour le plan d' **hébergement**.

    6.  Déterminez l' *emplacement* de votre groupe de ressources (si vous créez un groupe de ressources). L’emplacement devrait idéalement se trouver dans la région où l’application s’exécutait. Certaines ressources Azure sont uniquement disponibles dans certaines régions. Pour des performances optimales, sélectionnez la même région que le compte de stockage.

    7.  pour *Stockage*, sélectionnez **utiliser l’existant**, puis dans le menu déroulant, recherchez votre stockage créé précédemment.

    8.  laissez *Application Insights* désactivés pour cet exercice.

        ![Détails de l’application de fonction d’entrée](images/AzureLabs-Lab5-10.png)

4.  Cliquez sur le bouton **Créer**.

5.  Une fois que vous avez cliqué sur **créer**, vous devez attendre que le service soit créé, cette opération peut prendre une minute.

6.  Une notification s’affichera dans le portail une fois l’instance de service créée.

    ![nouvelle notification du portail Azure](images/AzureLabs-Lab5-11.png)

7.  Cliquez sur les notifications pour explorer votre nouvelle instance de service. 

    ![accéder à l’application de fonction de ressource](images/AzureLabs-Lab5-12.png)

8.  Cliquez sur le bouton **atteindre la ressource** dans la notification pour explorer votre nouvelle instance de service. Vous êtes dirigé vers votre nouvelle instance de service *Function App* .

9.  Dans le tableau de bord *Function App* , pointez avec la souris sur *fonctions*, situées dans le panneau de gauche, puis cliquez sur le symbole **+ (plus)** .

    ![créer une nouvelle fonction](images/AzureLabs-Lab5-13.png)

10. Dans la page suivante, vérifiez que **webhook + API** est sélectionné, et pour *choisir une langue,* sélectionnez **CSharp**, car il s’agit de la langue utilisée pour ce didacticiel. Enfin, cliquez sur le bouton **créer cette fonction** .

    ![sélectionner le Web Hook CSharp](images/AzureLabs-Lab5-14.png)

11. Vous devez être dirigé vers la page de codes (Run. CSX). si ce n’est pas le cas, cliquez sur la fonction nouvellement créée dans la liste fonctions du volet de gauche.

    ![ouvrir une nouvelle fonction](images/AzureLabs-Lab5-15.png)

12. Copiez le code suivant dans votre fonction. Cette fonction retourne simplement un entier aléatoire compris entre 0 et 2 lorsqu’elle est appelée. Ne vous inquiétez pas du code existant, n’hésitez pas à le coller en haut de celui-ci.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. Sélectionnez **Enregistrer**.

14. Le résultat doit ressembler à l’image ci-dessous.

15. Cliquez sur l’URL de la **fonction d’extraction** et prenez note du point de *terminaison* affiché. Vous devez l’insérer dans la classe *AzureServices* que vous allez créer plus loin dans ce cours.

    ![Obtient le point de terminaison de fonction](images/AzureLabs-Lab5-16.png)

    ![Insérer un point de terminaison de fonction](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Chapitre 3-Configuration du projet Unity

Ce qui suit est une configuration classique pour le développement avec une réalité mixte, et, par conséquent, est un bon modèle pour d’autres projets.

Configurez et testez votre casque immersif en réalité mixte.

> [!NOTE]
> Vous n’aurez **pas** besoin de contrôleurs de mouvement pour ce cours. Si vous avez besoin de la prise en charge de la configuration du casque immersif, consultez [l’article Configuration de la réalité mixte](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Ouvrez Unity et cliquez sur **nouveau**.

    ![Créer un projet Unity](images/AzureLabs-Lab5-17.png)

2.  vous devez maintenant fournir un nom de Project unity. Insérez **MR_Azure_Functions**. Assurez-vous que le type de projet est défini sur **3D**. Définissez l' *emplacement* approprié pour vous (n’oubliez pas que les répertoires racine sont mieux adaptés). Ensuite, cliquez sur **créer un projet**.

    ![Donnez un nom au nouveau projet Unity](images/AzureLabs-Lab5-18.png)

3.  Si Unity est ouvert, il est conseillé de vérifier que l' **éditeur de script** par défaut est défini sur **Visual Studio**. Accédez à **modifier**  >  les **Préférences** , puis à partir de la nouvelle fenêtre, accédez à **outils externes**. modifiez l' **éditeur de Script externe** pour **Visual Studio 2017**. Fermez la fenêtre **Préférences** .

    ![définir Visual Studio comme éditeur de script](images/AzureLabs-Lab5-19.png)

4.  ensuite, accédez à **fichier**  >  **Build Paramètres** et basculez la plateforme sur **plateforme Windows universelle**, en cliquant sur le bouton **changer de plateforme** .

    ![basculer la plateforme sur UWP](images/AzureLabs-Lab5-20.png)

5.  accédez à Paramètres de Build de **fichier** et assurez-vous  >   que :

    1. L' **appareil cible** est défini sur **n’importe quel appareil**.

        > pour Microsoft HoloLens, définissez **appareil cible** sur *HoloLens*.

    2. Le **type de build** est **D3D**

    3. Le **SDK** est configuré sur le **dernier installé**

    4. **Visual Studio Version** est définie sur le **plus récent**

    5. La **génération et l’exécution** sont définies sur l' **ordinateur local**

    6. Enregistrez la scène et ajoutez-la à la Build.

        1.  Pour ce faire, sélectionnez **Ajouter des scènes ouvertes**. Une fenêtre d’enregistrement s’affiche.

            ![Ajouter des scènes ouvertes](images/AzureLabs-Lab5-21.png)

        2.  Créez un dossier pour cela, ainsi que toute nouvelle scène, puis sélectionnez le bouton **nouveau dossier** pour créer un nouveau dossier, puis nommez-le **scenes**.

            ![créer un dossier de scènes](images/AzureLabs-Lab5-22.png)

        3.  Ouvrez le dossier **scenes** nouvellement créé, puis dans le champ **nom de fichier :** , tapez **FunctionsScene**, puis cliquez sur **Enregistrer**.

            ![Enregistrer les fonctions, scène](images/AzureLabs-Lab5-23.png)

6.  dans les **Paramètres de Build**, les paramètres restants doivent être conservés comme valeurs par défaut pour le moment.

    ![Conserver les paramètres de build par défaut](images/AzureLabs-Lab5-24.png)

7.  dans la fenêtre *Paramètres de Build* , cliquez sur le bouton Paramètres du **lecteur** pour ouvrir le panneau correspondant dans l’espace où se trouve l' *inspecteur* .

    ![paramètres du lecteur dans Inspector](images/AzureLabs-Lab5-25.png)

8.  Dans ce volet, quelques paramètres doivent être vérifiés :

    1.  dans l' **autre onglet Paramètres** :

        1.  La **version du runtime de script** doit être **expérimentale** (.net 4,6 équivalent), ce qui déclenche la nécessité de redémarrer l’éditeur.
        2.  Le **backend de script** doit être **.net**
        3.  Le **niveau de compatibilité** de l’API doit être **.net 4,6**

    2.  dans l’onglet **Paramètres de publication** , sous **fonctionnalités**, vérifiez :
        
        -  **InternetClient**

            ![définir les fonctionnalités](images/AzureLabs-Lab5-26.png)

    3.  plus bas dans le volet, dans **XR Paramètres** (situé sous **publication Paramètres**), cochez la **réalité virtuelle prise en charge**, assurez-vous que le **kit de développement logiciel (SDK) Windows Mixed Reality** est ajouté.

        ![définir les paramètres XR](images/AzureLabs-Lab5-27.png)

9.  de retour dans la *Build Paramètres* les *projets C# unity* ne sont plus grisés. Cochez la case en regard de cette option.

    ![Tick (projets c#)](images/AzureLabs-Lab5-28.png)

10.  Fermez la fenêtre Build Settings.

11. enregistrez votre scène et Project (**fichier**  >  **save scene/file**  >  **save Project**).

## <a name="chapter-4---setup-main-camera"></a>Chapitre 4-configurer l’appareil photo principal

> [!IMPORTANT]
> Si vous souhaitez ignorer les composants de la *configuration Unity* de ce cours et continuer directement dans le code, n’hésitez pas à [Télécharger ce fichier. pour Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)et à l’importer dans votre projet en tant que [package personnalisé](https://docs.unity3d.com/Manual/AssetPackages.html). Elle contient également les dll du chapitre suivant. Après l’importation, passez [au chapitre 7](#chapter-7---create-the-azureservices-class). 

1.  Dans le *volet hiérarchie*, vous trouverez un objet appelé **caméra principale**, cet objet représente le point de vue « Head » une fois que vous êtes « dans » votre application.

2.  Avec le tableau de bord Unity devant vous, sélectionnez la **caméra principale gameobject**. Vous remarquerez que le *panneau Inspecteur* (généralement situé à droite dans le tableau de bord) affichera les différents composants de ce *gameobject*, avec la *transformation* en haut, suivi de l' *appareil photo* et d’autres composants. Vous devez réinitialiser la transformation de la caméra principale, afin qu’elle soit positionnée correctement.

3.  Pour ce faire, sélectionnez l’icône d' **engrenage** en regard du composant *transformer* de l’appareil photo, puis sélectionnez **Réinitialiser**.

    ![réinitialiser la transformation](images/AzureLabs-Lab5-29.png)

4.  Ensuite, mettez à jour le composant **transformer** pour qu’il ressemble à ce qui suit :

    |         |    TRANSFORMATION-POSITION   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **O**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRANSFORMATION-ROTATION |       |
    | :---: | :------------------: | :----:|
    | **X** | **O**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORMATION-METTRE À L’ÉCHELLE |       |
    | :---: | :---------------: | :---: |
    | **X** | **O**             | **Z** |
    | 1     | 1                 | 1     |

    ![définir la transformation de l’appareil photo](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Chapitre 5-Configuration de la scène Unity

1.  Cliquez avec le bouton droit dans une zone vide du *panneau hiérarchie*, sous **objet 3D**, ajoutez un **plan**.

    ![créer un plan](images/AzureLabs-Lab5-31.png)

2.  Une fois l’objet **plan** sélectionné, modifiez les paramètres suivants dans le *panneau Inspecteur*:

    |       | TRANSFORMATION-POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **O**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORMATION-METTRE À L’ÉCHELLE |       |
    | :---: | :---------------: | :---: |
    | **X** | **O**             | **Z** |
    | 10    | 1                 | 10    |

    ![définir la position et l’échelle du plan](images/AzureLabs-Lab5-32.png)

    ![vue scène du plan](images/AzureLabs-Lab5-33.png)

3.  Cliquez avec le bouton droit dans une zone vide du *panneau hiérarchie*, sous **objet 3D**, ajoutez un **cube**.

    1.  Renommez le cube en **GazeButton** (avec le cube sélectionné, appuyez sur F2).

    2.  Modifiez les paramètres suivants dans le *panneau Inspecteur*:

        |       | TRANSFORMATION-POSITION |       |
        | :---: | :------------------: |:-----:|
        | **X** | **O**                | **Z** |
        | 0     | 3                    | 5     |


        ![définir la transformation du bouton de pointage](images/AzureLabs-Lab5-34.png)

        ![mode scène de bouton en regard](images/AzureLabs-Lab5-35.png)

    3.  Cliquez sur le bouton de liste déroulante **des balises** et cliquez sur **Ajouter une étiquette** pour ouvrir le *volet balises & couches*.

        ![Ajouter une nouvelle balise](images/AzureLabs-Lab5-36.png)

        ![sélectionner plus](images/AzureLabs-Lab5-37.png)

    4.  Sélectionnez le bouton **+ (plus)** et, dans le champ nom de la *nouvelle balise* , entrez **GazeButton**, puis cliquez sur **Enregistrer**.

        ![nom de la nouvelle balise](images/AzureLabs-Lab5-38.png)

    5.  Cliquez sur l’objet **GazeButton** dans le *volet hiérarchie*, puis, dans le *panneau Inspecteur*, affectez la balise **GazeButton** nouvellement créée.

        ![assigner un bouton de pointage à la nouvelle balise](images/AzureLabs-Lab5-39.png)

4.  Cliquez avec le bouton droit sur l’objet **GazeButton** , dans le *panneau hiérarchie*, puis ajoutez un **gameobject vide** (qui sera ajouté en tant qu’objet *enfant* ).

5.  Sélectionnez le nouvel objet et renommez-le **ShapeSpawnPoint**.

    1.  Modifiez les paramètres suivants dans le *panneau Inspecteur*:

        |       | TRANSFORMATION-POSITION |       |
        | :---: | :------------------: |:----: |
        | **X** |**O**                 | **Z** |
        | 0     | -1                   | 0     |

        ![mettre à jour la transformation de point de génération de forme](images/AzureLabs-Lab5-40.png)

        ![vue scène du point de génération de forme](images/AzureLabs-Lab5-41.png)

6.  Vous allez ensuite créer un objet **texte 3D** pour fournir des commentaires sur l’état du service Azure.

    Cliquez à nouveau avec le bouton droit sur **GazeButton** dans le panneau hiérarchie et ajoutez un objet **3D 3D Object**  >   en tant qu' *enfant*.

    ![créer un objet texte 3D](images/AzureLabs-Lab5-42.png)

7.  Renommez l’objet **3D Text** en **AzureStatusText**.

8.  Modifiez la transformation de l’objet **AzureStatusText** comme suit :

    |       | TRANSFORMATION-POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **O**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | TRANSFORMATION-METTRE À L’ÉCHELLE |       |
    | :---: | :---------------: | :---: |
    | **X** | **O**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > Ne vous inquiétez pas si elle semble être décentrée, car cela sera résolu lorsque le composant de maillage de texte ci-dessous sera mis à jour.

9.  Modifiez le composant de **maillage de texte** pour qu’il corresponde à ce qui suit :

    ![définir le composant de maillage de texte](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > La couleur sélectionnée ici est la couleur hexadécimale : **000000FF**, bien que vous ne soyez pas libre de choisir la vôtre, assurez-vous qu’elle est lisible.

10. La structure de votre volet de hiérarchie doit maintenant ressembler à ceci :

    ![Maillage de texte dans la hiérarchie](images/AzureLabs-Lab5-43b.png)

10. Votre scène doit maintenant ressembler à ceci :

    ![Maillage de texte en mode scène](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>chapitre 6-importer des stockage Azure pour unity

vous utiliserez stockage Azure pour unity (qui utilise lui-même le kit de développement logiciel (SDK) .net pour Azure). pour plus d’informations à ce sujet, consultez l' [article stockage Azure pour unity](/sandbox/gamedev/unity/azure-storage-unity).

Il existe actuellement un problème connu dans Unity qui nécessite que les plug-ins soient reconfigurés après l’importation. Ces étapes (4-7 dans cette section) ne sont plus nécessaires une fois que le bogue a été résolu.

Pour importer le kit de développement logiciel (SDK) dans votre propre projet, assurez-vous d’avoir téléchargé la dernière version [de « . pour Unity » à partir de GitHub](https://aka.ms/azstorage-unitysdk). Ensuite, procédez comme suit :

1.  Ajoutez le fichier **. pour Unity** à Unity à l' aide de l’option de  >    >  menu **package personnalisé** du package d’importation de ressources.

2.  dans la zone **importer le Package unity** qui s’affiche, vous pouvez sélectionner tout dans le **plug-in**  >  **Stockage**. Décochez tout le reste, car il n’est pas nécessaire pour ce cours.

    ![importer dans le package](images/AzureLabs-Lab5-45.png)

3.  Cliquez sur le bouton **Importer** pour ajouter les éléments à votre projet.

4.  accédez au dossier *Stockage* sous *plug-ins*, dans la vue Project, puis sélectionnez les plug-ins suivants *uniquement*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![décocher une plateforme](images/AzureLabs-Lab5-46.png)

5.  Une fois *ces plug-ins spécifiques* sélectionnés, **décochez** *toutes les plateformes* et **décochez** *WSAPlayer* , puis cliquez sur **appliquer**.

    ![appliquer des dll de plateforme](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Nous marqueons ces plug-ins particuliers à utiliser uniquement dans l’éditeur Unity. Cela est dû au fait qu’il existe différentes versions des mêmes plug-ins dans le dossier WSA qui seront utilisées après l’exportation du projet à partir d’Unity.

6.  dans le dossier du plug-in *Stockage* , sélectionnez uniquement :

    -   Microsoft.Data.Services.Client

        ![définir ne pas traiter pour les dll](images/AzureLabs-Lab5-48.png)

7.  cochez la case **ne pas traiter** sous Paramètres de la *plateforme* , puis cliquez sur **appliquer**.

    ![ne pas appliquer de traitement](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Nous marquant ce plug-in « ne pas traiter », car l’assembly Unity Patcher a des difficultés à traiter ce plug-in. Le plug-in fonctionne toujours même s’il n’est pas traité.

## <a name="chapter-7---create-the-azureservices-class"></a>Chapitre 7-créer la classe AzureServices

La première classe que vous allez créer est la classe *AzureServices* .

La classe *AzureServices* est chargée des opérations suivantes :

-   Stockage des informations d’identification du compte Azure.

-   Appel de votre fonction Azure App.

-   le chargement et le téléchargement du fichier de données dans votre Stockage Cloud Azure.

Pour créer cette classe :

1.  cliquez avec le bouton droit dans le dossier *Asset* , situé dans le volet Project, **créez** le  >  **dossier**. Nommez le dossier **scripts**.

    ![créer un dossier](images/AzureLabs-Lab5-50.png)

    ![dossier d’appel-scripts](images/AzureLabs-Lab5-51.png)

2.  Double-cliquez sur le dossier que vous venez de créer pour l’ouvrir.

3.  Cliquez avec le bouton droit dans le dossier, **créez** un  >  **script C#**. Appelez le script *AzureServices*.

4.  Double-cliquez sur la nouvelle classe *AzureServices* pour l’ouvrir avec *Visual Studio*.

5.  Ajoutez les espaces de noms suivants en haut de *AzureServices*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Ajoutez les champs Inspector suivants à l’intérieur de la classe *AzureServices* :

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  Ajoutez ensuite les variables de membre suivantes à l’intérieur de la classe *AzureServices* :

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > Veillez à remplacer les valeurs de *point de terminaison* et de *chaîne de connexion* par les valeurs de votre stockage Azure, qui se trouvent dans le portail Azure.

8.  Vous devez maintenant ajouter le code des méthodes *éveillés ()* et *Start ()* . Ces méthodes sont appelées lorsque la classe est initialisée :

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > Nous remplirons le code pour *CallAzureFunctionForNextShape ()* dans un [chapitre ultérieur](#chapter-10---completing-the-azureservices-class).

9.  Supprimez la méthode *Update ()* puisque cette classe ne l’utilisera pas.

10. enregistrez les modifications apportées à Visual Studio, puis revenez à unity.

11. Cliquez et faites glisser la classe *AzureServices* du dossier scripts vers l’objet Camera principal dans le *panneau hiérarchie*.

12. Sélectionnez l’appareil photo principal, puis saisissez l’objet enfant **AzureStatusText** sous l’objet **GazeButton** , et placez-le dans le champ cible de la référence **AzureStatusText** , dans l' *inspecteur*, pour fournir la référence au script *AzureServices* .

    ![affecter une cible de référence de texte d’État Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Chapitre 8-créer la classe ShapeFactory

Le prochain script à créer est la classe *ShapeFactory* . Le rôle de cette classe est de créer une nouvelle forme, lorsqu’elle est demandée, et de conserver un historique des formes créées dans une *liste d’historique des formes*. chaque fois qu’une forme est créée, la liste de l' *historique des formes* est mise à jour dans la classe *AzureService* , puis stockée dans votre *stockage Azure*. lorsque l’application démarre, si un fichier stocké est trouvé dans votre *stockage Azure*, la liste de l' *historique des formes* est récupérée et relue, avec l’objet **texte 3d** qui indique si la forme générée provient du stockage ou de la nouvelle.

Pour créer cette classe :

1.  Accédez au dossier **scripts** que vous avez créé précédemment.

2.  Cliquez avec le bouton droit dans le dossier, **créez** un  >  **script C#**. Appelez le script *ShapeFactory*.

3.  Double-cliquez sur le nouveau script *ShapeFactory* pour l’ouvrir avec *Visual Studio*.

4.  Vérifiez que la classe *ShapeFactory* comprend les espaces de noms suivants :

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Ajoutez les variables ci-dessous à la classe *ShapeFactory* , puis remplacez les fonctions *Start ()* et *éveillé ()* par celles ci-dessous :

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  La méthode *createShape ()* génère les formes primitives, en fonction du paramètre *entier* fourni. Le paramètre booléen est utilisé pour spécifier si la forme actuellement créée provient d’un stockage ou d’une nouvelle. Placez le code suivant dans votre classe *ShapeFactory* , sous les méthodes précédentes :

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  veillez à enregistrer les modifications apportées à Visual Studio avant de revenir à unity.

8.  De retour dans l’éditeur Unity, cliquez et faites glisser la classe *ShapeFactory* du dossier **scripts** vers l’objet **Camera principal** dans le *panneau hiérarchie*.

9. Une fois l’appareil photo sélectionné, vous remarquerez que le composant script *ShapeFactory* ne contient pas la référence du *point de génération* . Pour résoudre ce problème, faites glisser l’objet **ShapeSpawnPoint** du volet de la *hiérarchie* vers la cible de référence de **point de génération** .

    ![définir la cible de référence de fabrique de forme](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Chapitre 9-créer la classe en regard

Le dernier script que vous devez créer est la classe de *regard* .

Cette classe est chargée de créer un **Raycast** qui sera projeté à l’avance de la caméra principale, pour détecter l’objet que l’utilisateur examine. Dans ce cas, le Raycast doit déterminer si l’utilisateur regarde l’objet **GazeButton** dans la scène et déclencher un comportement.

Pour créer cette classe :

1.  Accédez au dossier **scripts** que vous avez créé précédemment.

2.  cliquez avec le bouton droit dans le panneau Project, **créez** un  >  **Script C#**. Appelez le point de *regard* du script.

3.  Double-cliquez sur le nouveau script de *regard* pour l’ouvrir avec *Visual Studio.*

4.  Assurez-vous que l’espace de noms suivant est inclus en haut du script :

    ```csharp
        using UnityEngine;
    ```

5.  Ajoutez ensuite les variables suivantes à l’intérieur de la classe *regard* :

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> Certaines de ces variables pourront être modifiées dans l' *éditeur*.

6.  Vous devez maintenant ajouter du code pour les méthodes *éveillé ()* et *Start ()* .

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Ajoutez le code suivant, qui créera un objet curseur au démarrage, avec la méthode *Update ()* , qui exécutera la méthode Raycast, ainsi que l’emplacement où la valeur booléenne GazeEnabled est basculée :

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. Ensuite, ajoutez la méthode *UpdateRaycast ()* , qui projetera un Raycast et détectera la cible d’accès.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. Enfin, ajoutez la méthode *ResetFocusedObject ()* , qui va basculer la couleur active des objets GazeButton, en indiquant si elle crée ou non une nouvelle forme.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  enregistrez les modifications apportées à Visual Studio avant de revenir à unity.

11.  Cliquez et faites glisser *la classe pointage du dossier* scripts vers l’objet **caméra principal** dans le *panneau hiérarchie*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Chapitre 10-réalisation de la classe AzureServices

Avec les autres scripts en place, il est désormais possible d' *effectuer* la classe *AzureServices* . Pour ce faire, procédez comme suit :

1.  Ajout d’une nouvelle méthode nommée *CreateCloudIdentityAsync ()*, pour configurer les variables d’authentification nécessaires à la communication avec Azure.

    > Cette méthode vérifie également l’existence d’un fichier précédemment stocké contenant la liste de formes.
    >
    > **si le fichier est trouvé**, il désactive le point d’interdépendance de *l’utilisateur et* déclenche la création de la forme, en fonction du modèle de formes, tel qu’il est stocké dans le **fichier stockage Azure**. l’utilisateur peut voir cela, car la **maille de texte** fournira l’affichage « Stockage » ou « nouveau », en fonction de l’origine des formes.
    >
    > **Si aucun fichier n’est trouvé**, il active le point de *regard*, ce qui permet à l’utilisateur de créer des formes lors de la recherche de l’objet **GazeButton** dans la scène.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  L’extrait de code suivant se trouve dans la méthode *Start ()* ; où un appel sera effectué à la méthode *CreateCloudIdentityAsync ()* . N’hésitez pas à effectuer une copie sur votre méthode *Start ()* actuelle, avec les éléments suivants :

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  Renseignez le code de la méthode *CallAzureFunctionForNextShape ()*. Vous allez utiliser la *Function App Azure* précédemment créée pour demander un index de forme. Une fois la nouvelle forme reçue, cette méthode envoie la forme à la classe *ShapeFactory* pour créer la nouvelle forme dans la scène. Utilisez le code ci-dessous pour terminer le corps de *CallAzureFunctionForNextShape ()*.

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  ajoutez une méthode pour créer une chaîne en concaténant les entiers stockés dans la liste de l’historique des formes et en l’enregistrant dans votre *fichier stockage Azure*.

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  ajoutez une méthode pour récupérer le texte stocké dans le fichier situé dans votre *fichier stockage Azure* et le *désérialiser* dans une liste.

6.  Une fois ce processus terminé, la méthode réactive le point de regard pour permettre à l’utilisateur d’ajouter des formes à la scène.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  enregistrez les modifications apportées à Visual Studio avant de revenir à unity.

## <a name="chapter-11---build-the-uwp-solution"></a>Chapitre 11-créer la solution UWP

Pour commencer le processus de génération :

1.  accédez à   >  **Paramètres de Build** de fichier.

    ![générer l’application](images/AzureLabs-Lab5-54.png)

2.  Cliquez sur **Générer**. Unity lance une fenêtre de l' *Explorateur de fichiers* , dans laquelle vous devez créer, puis sélectionner un dossier dans lequel générer l’application. Créez ce dossier maintenant, puis nommez-le *application*. Ensuite, avec le dossier d' *application* sélectionné, appuyez sur **Sélectionner un dossier**.

3.  Unity commence à générer votre projet dans le dossier de l' *application* .

4.  Une fois la génération de Unity terminée (cela peut prendre un certain temps), une fenêtre de l' *Explorateur de fichiers* s’ouvre à l’emplacement de votre Build (Vérifiez la barre des tâches, car elle ne s’affiche pas toujours au-dessus de votre Windows, mais vous informera de l’ajout d’une nouvelle fenêtre).

## <a name="chapter-12---deploying-your-application"></a>Chapitre 12 : déploiement de votre application

Pour déployer votre application :

1.  Accédez au dossier de l' *application* qui a été créé dans le [dernier chapitre](#chapter-11---build-the-uwp-solution). Vous verrez un fichier avec le nom de votre application, avec l’extension « . sln », que vous devez double-cliquer, afin de l’ouvrir dans *Visual Studio*.

2.  Dans la **plateforme** de la solution, sélectionnez **x86, ordinateur local**.

3.  Dans la **configuration** de la solution, sélectionnez **Déboguer**.

    > pour le Microsoft HoloLens, il peut s’avérer plus facile de définir cette valeur sur *Machine distante*, de sorte que vous n’êtes pas attaché à votre ordinateur. Toutefois, vous devez également effectuer les opérations suivantes :
    > - identifiez l' **adresse IP** de votre HoloLens, qui se trouve dans le   >  **réseau Paramètres &**  >  Options avancées de **Wi-Fi** Internet.  >  l’adresse IPv4 est celle que vous devez utiliser. 
    > - Assurez-vous que le **mode développeur** est **activé**; trouvé dans **Paramètres**  >  **mise à jour & sécurité**  >  **pour les développeurs**.

    ![déployer la solution](images/AzureLabs-Lab5-55.png)

4.  Accédez au menu **générer** , puis cliquez sur **déployer la solution** pour chargement l’application sur votre ordinateur.

5.  Votre application doit maintenant apparaître dans la liste des applications installées, prêtes à être lancées et testées.

## <a name="your-finished-azure-functions-and-storage-application"></a>votre Azure Functions et votre Application Stockage terminée

félicitations, vous avez créé une application de réalité mixte qui tire parti des services Azure Functions et stockage Azure. Votre application sera en mesure de dessiner sur des données stockées et de fournir une action basée sur ces données.

![fin du produit final](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Exercices bonus

### <a name="exercise-1"></a>Exercice 1

Créez un deuxième point de lancement et un autre enregistrement à partir duquel un objet a été créé. Lorsque vous chargez le fichier de données, relisez les formes générées à partir de l’emplacement où elles ont été créées à l’origine.

### <a name="exercise-2"></a>Exercice 2

Créez un moyen de redémarrer l’application, au lieu de la rouvrir à chaque fois. Le **chargement des scènes** est un bon point de départ. après cela, créez un moyen d’effacer la liste stockée dans *stockage Azure*, afin qu’elle puisse être facilement réinitialisée à partir de votre application.