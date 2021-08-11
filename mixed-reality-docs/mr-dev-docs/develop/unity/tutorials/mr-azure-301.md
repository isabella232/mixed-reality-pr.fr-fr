---
title: HoloLens (1ère génération) et Azure 301 - Traduction de langue
description: suivez ce cours pour apprendre à implémenter le API de traduction de texte Translator Text Azure dans une application de réalité mixte.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, réalité mixte, académie, unity, didacticiel, api, texte de traducteur, hololens, immersif, vr, traduction de langue, Windows 10, Visual Studio
ms.openlocfilehash: 8eeeab45c6e7d93c1b04afa4db811f220b0c2f9c85400fc93a81ac413164a6b7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115229511"
---
# <a name="hololens-1st-gen-and-azure-301-language-translation"></a>HoloLens (1re génération) et Azure 301 : traduction de langue

<br>

>[!NOTE]
>Les tutoriels Mixed Reality Academy ont été conçus pour les appareils HoloLens (1re génération) et les casques immersifs de réalité mixte.  Nous estimons qu’il est important de laisser ces tutoriels à la disposition des développeurs qui recherchent encore des conseils pour développer des applications sur ces appareils.  Notez que ces tutoriels **_ne sont pas_** mis à jour avec les derniers ensembles d’outils ou interactions utilisés pour HoloLens 2.  Ils sont fournis dans le but de fonctionner sur les appareils pris en charge. Une nouvelle série de didacticiels sera publiée à l’avenir qui vous montrera comment développer pour HoloLens 2.  Cet avis sera mis à jour avec un lien vers ces didacticiels lors de leur publication.

<br>

dans ce cours, vous allez apprendre à ajouter des fonctionnalités de traduction à une application de réalité mixte à l’aide d’Azure Cognitive Services, avec la API de traduction de texte Translator Text.

![Produit final](images/AzureLabs-Lab1-00.png)

le API de traduction de texte Translator Text est un Service de traduction qui fonctionne quasiment en temps réel. Le service est basé sur le Cloud et, à l’aide d’un appel d’API REST, une application peut utiliser la technologie de traduction d’ordinateur neuronal pour traduire du texte dans une autre langue. pour plus d’informations, consultez la [page API de traduction de texte Translator Text Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

À la fin de ce cours, vous disposerez d’une application de réalité mixte qui sera en mesure d’effectuer les opérations suivantes :

1.  L’utilisateur se prononcera dans un microphone connecté à un casque immersif (ou le microphone intégré de HoloLens).
2.  l’application capture la dictée et l’envoie au API de traduction de texte Translator Text Azure.
3.  Le résultat de la traduction s’affiche dans un groupe d’interface utilisateur simple dans la scène Unity.

ce cours vous apprend à obtenir les résultats du Service Traducteur dans un exemple d’application basée sur unity. Il vous faudra appliquer ces concepts à une application personnalisée que vous pouvez générer.

## <a name="device-support"></a>Prise en charge des appareils

<table>
<tr>
<th>Cours</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Casques immersifs</a></th>
</tr><tr>
<td> Réalité mixte - Azure - Cours 301 : Traduction</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Un jeu de casque avec un microphone intégré (si le casque n’a pas de MIC et de haut-parleurs intégrés)
- Accès à Internet pour la configuration d’Azure et la récupération des traductions

## <a name="before-you-start"></a>Avant de commencer

- Pour éviter de rencontrer des problèmes lors de la création de ce projet, il est fortement recommandé de créer le projet mentionné dans ce didacticiel dans un dossier racine ou dans un dossier racine (les chemins de dossiers longs peuvent entraîner des problèmes au moment de la génération).
- Le code de ce didacticiel vous permet d’enregistrer à partir du périphérique microphone par défaut connecté à votre PC. Assurez-vous que le périphérique microphone par défaut est défini sur l’appareil que vous prévoyez d’utiliser pour capturer votre voix.
- pour permettre à votre PC d’activer la dictée, accédez à **Paramètres > Privacy > Speech, entrée manuscrite & typage** , puis sélectionnez le bouton **activer les services vocaux et les suggestions de saisie**.
- si vous utilisez un microphone et un casque connectés à votre casque (ou intégrés à celui-ci), assurez-vous que l’option « lors de l’usure du casque, basculez vers la mic du casque » est activée dans **Paramètres > réalité mixte > l’Audio et la parole**.

   ![Paramètres de réalité mixte](images/AzureLabs-Lab1-00-5.png)

   ![Paramètre de microphone](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Sachez que si vous développez pour un casque immersif pour ce laboratoire, vous risquez de rencontrer des problèmes de périphérique de sortie audio. Cela est dû à un problème avec Unity, qui est résolu dans les versions ultérieures de Unity (Unity 2018,2). Le problème empêche Unity de modifier le périphérique de sortie audio par défaut au moment de l’exécution. Pour contourner ce problème, assurez-vous que vous avez effectué les étapes ci-dessus et fermez et rouvrez l’éditeur, lorsque ce problème se présente lui-même.

## <a name="chapter-1--the-azure-portal"></a>Chapitre 1 – portail Azure

pour utiliser l’API Azure Traducteur, vous devez configurer une instance du Service qui sera mise à la disposition de votre application.

1.  Connectez-vous au  [portail Azure](https://portal.azure.com).

    > [!NOTE]
    > Si vous n’avez pas encore de compte Azure, vous devez en créer un. Si vous suivez ce didacticiel dans une situation de classe ou de laboratoire, demandez à votre formateur ou à l’un des prostructors de vous aider à configurer votre nouveau compte.

2.  une fois que vous êtes connecté, cliquez sur **nouveau** dans l’angle supérieur gauche et recherchez « API de traduction de texte Translator Text ». Sélectionnez **Enter** (Entrer).

    ![Nouvelle ressource](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > Le mot **nouveau** peut avoir été remplacé par **créer une ressource**, dans les portails plus récents.

3.  la nouvelle page fournit une description du Service *API de traduction de texte Translator Text* . En bas à gauche de cette page, cliquez sur le bouton **créer** pour créer une association avec ce service.

    ![créer un Service API de traduction de texte Translator Text](images/AzureLabs-Lab1-03.png)

4.  Une fois que vous avez cliqué sur **créer**:

    1. Insérez le **nom** de votre choix pour cette instance de service.
    2. Sélectionnez un **abonnement** approprié.
    3. sélectionnez le **niveau tarifaire** approprié, s’il s’agit de la première fois que vous créez un *Service Traduction de texte Translator Text*, vous devez disposer d’un niveau gratuit (nommé F0).
    4. Choisissez un **groupe de ressources** ou créez-en un. Un groupe de ressources permet de surveiller, de contrôler l’accès, de configurer et de gérer la facturation d’un regroupement de ressources Azure. Il est recommandé de conserver tous les services Azure associés à un seul projet (par exemple, ces laboratoires) sous un groupe de ressources commun).

        > Si vous souhaitez en savoir plus sur les groupes de ressources Azure, consultez [l’article du groupe de ressources](/azure/azure-resource-manager/resource-group-portal).

    5. Déterminez l' **emplacement** de votre groupe de ressources (si vous créez un groupe de ressources). L’emplacement devrait idéalement se trouver dans la région où l’application s’exécutait. Certaines ressources Azure sont uniquement disponibles dans certaines régions.
    6. Vous devrez également confirmer que vous avez compris les conditions générales appliquées à ce service.
    7. Sélectionnez **Créer**.

        ![Sélectionnez le bouton créer.](images/AzureLabs-Lab1-04.png)

5.  Une fois que vous avez cliqué sur **créer**, vous devez attendre que le service soit créé, cette opération peut prendre une minute.
6.  Une notification s’affichera dans le portail une fois l’instance de service créée. 

    ![Notification de création de service Azure](images/AzureLabs-Lab1-05.png)

7.  Cliquez sur la notification pour explorer votre nouvelle instance de service. 

    ![Accédez à la fenêtre contextuelle de la ressource.](images/AzureLabs-Lab1-06.png)

8.  Cliquez sur le bouton **atteindre la ressource** dans la notification pour explorer votre nouvelle instance de service. vous êtes dirigé vers votre nouvelle instance de Service API de traduction de texte Translator Text. 

    ![Traducteur Page de service de l’API texte](images/AzureLabs-Lab1-07.png)

9.  Dans ce didacticiel, votre application doit effectuer des appels à votre service, à l’aide de la clé d’abonnement de votre service. 
10. à partir de la page *démarrage rapide* de votre Service *Traduction de texte Translator Text* , accédez à la première étape, *saisissez vos clés*, puis cliquez sur **clés** (vous pouvez également y parvenir en cliquant sur les touches de lien bleu, situées dans le menu de navigation Services, indiqué par l’icône de clé). Cela permet de révéler vos *clés* de service.
11. Prenez une copie de l’une des clés affichées, car vous en aurez besoin plus tard dans votre projet. 

## <a name="chapter-2--set-up-the-unity-project"></a>Chapitre 2 : configurer le projet Unity

Configurez et testez votre casque immersif en réalité mixte.

> [!NOTE]
> Vous n’aurez pas besoin de contrôleurs de mouvement pour ce cours. Si vous avez besoin de la prise en charge de la configuration d’un casque immersif, [procédez comme suit](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

Voici une configuration standard pour le développement avec une réalité mixte et, par conséquent, est un bon modèle pour d’autres projets :

1.  Ouvrez *Unity* et cliquez sur **nouveau**. 

    ![Démarrez le nouveau projet Unity.](images/AzureLabs-Lab1-08.png)

2.  vous devez maintenant fournir un nom de Project unity. Insérez **MR_Translation**. Assurez-vous que le type de projet est défini sur **3D**. Définissez l' *emplacement* approprié pour vous (n’oubliez pas que les répertoires racine sont mieux adaptés). Ensuite, cliquez sur **créer un projet**.

    ![Fournissez des détails pour le nouveau projet Unity.](images/AzureLabs-Lab1-09.png)

3.  Si Unity est ouvert, il est conseillé de vérifier que l' **éditeur de script** par défaut est défini sur **Visual Studio**. Accédez à **modifier > préférences** puis, dans la nouvelle fenêtre, accédez à **outils externes**. modifiez l' **éditeur de Script externe** pour **Visual Studio 2017**. Fermez la fenêtre **Préférences** .

    ![Mettre à jour la préférence éditeur de script.](images/AzureLabs-Lab1-10.png)

4.  accédez ensuite à **fichier > générer Paramètres** et basculez la plateforme sur **plateforme Windows universelle**, en cliquant sur le bouton **changer de plateforme** .

    ![générez Paramètres fenêtre, basculez la plateforme sur UWP.](images/AzureLabs-Lab1-11.png)

5.  accédez à **fichier > générer Paramètres** et assurez-vous que :

    1. L' **appareil cible** est défini sur **n’importe quel appareil**.

        > pour Microsoft HoloLens, définissez **appareil cible** sur *HoloLens*.

    2. Le **type de build** est **D3D**
    3. Le **SDK** est configuré sur le **dernier installé**
    4. **Visual Studio Version** est définie sur le **plus récent**
    5. La **génération et l’exécution** sont définies sur l' **ordinateur local**
    6. Enregistrez la scène et ajoutez-la à la Build.

        1. Pour ce faire, sélectionnez **Ajouter des scènes ouvertes**. Une fenêtre d’enregistrement s’affiche.

            ![Cliquez sur le bouton Ajouter des scènes ouvertes](images/AzureLabs-Lab1-12.png)

        2. Créez un dossier pour cela, ainsi que toute nouvelle scène, puis sélectionnez le bouton **nouveau dossier** pour créer un nouveau dossier, puis nommez-le **scenes**.

            ![Créer un dossier de scripts](images/AzureLabs-Lab1-13.png)

        3. Ouvrez le dossier **scenes** nouvellement créé, puis dans le champ *nom de fichier*:, tapez **MR_TranslationScene**, puis cliquez sur **Enregistrer**.

            ![Donnez un nom à la nouvelle scène.](images/AzureLabs-Lab1-14.png)

            > N’oubliez pas que vous devez enregistrer vos scènes Unity dans le dossier *ressources* , car elles doivent être associées à la Project Unity. La création du dossier scenes (et d’autres dossiers similaires) est un moyen classique de structurer un projet Unity.

    7. dans les *Paramètres de Build*, les paramètres restants doivent être conservés comme valeurs par défaut pour le moment.

6. dans la fenêtre *Paramètres de Build* , cliquez sur le bouton Paramètres du **lecteur** pour ouvrir le panneau correspondant dans l’espace où se trouve l' *inspecteur* . 

    ![Ouvrez les paramètres du lecteur.](images/AzureLabs-Lab1-15.png)

7. Dans ce volet, quelques paramètres doivent être vérifiés :

    1. dans l' **autre onglet Paramètres** :

        1. La **version du runtime de script** doit être **stable** (équivalent .net 3,5).
        2. Le **backend de script** doit être **.net**
        3. Le **niveau de compatibilité** de l’API doit être **.net 4,6**

            ![Mettez à jour d’autres paramètres.](images/AzureLabs-Lab1-16.png)
      
    2. dans l’onglet **Paramètres de publication** , sous **fonctionnalités**, vérifiez :

        1. **InternetClient**
        2. **Microphone**

            ![Mise à jour des paramètres de publication.](images/AzureLabs-Lab1-17.png)

    3. plus bas dans le volet, dans **XR Paramètres** (situé sous **publier Paramètres**), cochez la **réalité virtuelle prise en charge**, assurez-vous que le **kit de développement logiciel (SDK) Windows Mixed Reality** est ajouté.

        ![mettez à jour le Paramètres X R.](images/AzureLabs-Lab1-18.png)

8.  de retour dans le **Paramètres de Build**, les *projets C# unity* ne sont plus grisés. Cochez la case en regard de cette option. 
9.  Fermez la fenêtre Build Settings.
10. enregistrez votre scène et Project (**fichier > enregistrer la scène/le fichier > enregistrer le projet**).

## <a name="chapter-3--main-camera-setup"></a>Chapitre 3 – Configuration de l’appareil photo principal

> [!IMPORTANT]
> Si vous souhaitez ignorer le composant *Unity Set up* de ce cours et continuer directement dans le code, n’hésitez pas à [Télécharger ce fichier. pour Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), à l’importer dans votre projet en tant que [*package personnalisé*](https://docs.unity3d.com/Manual/AssetPackages.html), puis à passer au [Chapitre 5](#chapter-5--create-the-results-class). Vous devrez toujours créer un Project Unity.

1.  Dans le *volet hiérarchie*, vous trouverez un objet appelé **caméra principale**, cet objet représente le point de vue « Head » une fois que vous êtes « dans » votre application.
2.  Avec le tableau de bord Unity devant vous, sélectionnez la **caméra principale gameobject**. Vous remarquerez que le *panneau Inspecteur* (généralement situé à droite dans le tableau de bord) affichera les différents composants de ce *gameobject*, avec la *transformation* en haut, suivi de l' *appareil photo* et d’autres composants. Vous devez réinitialiser la transformation de la caméra principale, afin qu’elle soit positionnée correctement.
3.  Pour ce faire, sélectionnez l’icône d' **engrenage** en regard du composant *transformer* de l’appareil photo, puis sélectionnez **Réinitialiser**. 

    ![Réinitialisez la transformation principale de l’appareil photo.](images/AzureLabs-Lab1-19.png)
 
4.  Le composant *transformer* doit alors ressembler à ceci :

    1. La *position* est définie sur **0, 0,** 0
    2. La *rotation* est définie sur **0, 0,** 0
    3. Et *Scale* est défini sur **1, 1, 1**

        ![Informations de transformation pour l’appareil photo](images/AzureLabs-Lab1-20.png)

5.  Ensuite, avec l’objet **caméra principal** sélectionné, consultez le bouton **Ajouter un composant** situé en bas du panneau de l' *inspecteur*. 
6.  Sélectionnez ce bouton et effectuez une recherche (en tapant *source audio* dans le champ de recherche ou en parcourant les sections) du composant appelé **source audio** , comme indiqué ci-dessous, puis sélectionnez-le (en appuyant sur entrée).
7.  Un composant *source audio* est ajouté à la **caméra principale**, comme illustré ci-dessous.

    ![Ajoutez un composant source audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > par Microsoft HoloLens, vous devrez également modifier les éléments suivants, qui font partie du composant **camera** sur votre **caméra principale**:
    > - **Indicateurs d’effacement :** Couleur unie.
    > - **Arrière-plan** 'Black, alpha 0 ' – couleur hexadécimale : #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Chapitre 4-zone de travail de débogage d’installation

Pour afficher l’entrée et la sortie de la traduction, vous devez créer une interface utilisateur de base. Pour ce cours, vous allez créer un objet d’interface utilisateur Canvas, avec plusieurs objets « Text » pour afficher les données.

1.  Cliquez avec le bouton droit dans une zone vide du *panneau de hiérarchie*, sous **UI**, ajoutez une zone de **dessin**.

    ![Ajoutez un nouvel objet d’interface utilisateur Canvas.](images/AzureLabs-Lab1-22.png)

2.  Lorsque l’objet canevas est sélectionné, dans le *panneau Inspecteur* (dans le composant « Canvas »), changez le **mode de rendu** en **espace universel**. 
3.  Ensuite, modifiez les paramètres suivants dans la *transformation Rect du panneau Inspecteur*:

    1. *Pos*  -   **X** 0 **Y** 0 **Z** 40
    2. *Largeur* -500
    3. *Hauteur* -300
    4. Mise à l' *échelle*  -  **X** 0,13 **Y** 0,13 **Z** 0,13

        ![Mettez à jour la transformation Rect pour la zone de dessin.](images/AzureLabs-Lab1-23.png)
 
4.  Cliquez avec le bouton droit sur le **canevas** dans le *panneau hiérarchie*, sous **interface utilisateur**, puis ajoutez un **panneau**. Ce **panneau** fournit un arrière-plan du texte que vous afficherez dans la scène.
5.  Cliquez avec le bouton droit sur le **panneau** dans le *volet hiérarchie*, sous **interface utilisateur**, puis ajoutez un **objet texte**. Répétez le même processus jusqu’à ce que vous ayez créé quatre objets de texte d’interface utilisateur au total (Conseil : si le premier objet « texte » est sélectionné, vous pouvez simplement appuyer sur **« Ctrl + d »** pour le dupliquer, jusqu’à ce que vous en ayez quatre au total). 
6.  Pour chaque **objet texte**, sélectionnez-le et utilisez les tableaux ci-dessous pour définir les paramètres dans le *panneau Inspecteur*.

    1. Pour le composant de *transformation Rect* :

        | Name                   | Transformation- *position*             | Largeur      | Hauteur    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Pour le composant **texte (script)** :


        | Nom                   | Texte               | Taille de police    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | État du microphone : | 20           |
        | AzureResponseLabel     | Réponse Web Azure | 20           |
        | DictationLabel         |   Vous avez dit :   | 20           |
        | TranslationResultLabel |    Traduction :    | 20           |

        ![Entrez les valeurs correspondantes pour les étiquettes de l’interface utilisateur.](images/AzureLabs-Lab1-24.png)

    3. En outre, définissez le style de police en **gras**. Cela rend le texte plus facile à lire.

        ![Police en gras.](images/AzureLabs-Lab1-25.png)

7.  Pour chaque *objet texte de l’interface utilisateur* créé au [Chapitre 5](#chapter-5--create-the-results-class), créez un nouvel **objet texte de l’interface utilisateur** *enfant* . Ces enfants affichent la sortie de l’application. Pour créer des objets *enfants* , cliquez avec le bouton droit sur le parent souhaité (par exemple, *MicrophoneStatusLabel*), puis sélectionnez **interface utilisateur** et **texte**.
8.  Pour chacun de ces enfants, sélectionnez-les et utilisez les tableaux ci-dessous pour définir les paramètres dans le panneau de l’inspecteur.

    1. Pour le composant de **transformation Rect** :

        | Name                  | Transformation- *position* | Largeur      | Hauteur    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y-30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y-30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y-30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y-30 Z 0          | 300        | 30        |

    2. Pour le composant **texte (script)** :

        | Nom                  | Texte          | Taille de police    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. Ensuite, sélectionnez l’option d’alignement « Centre » pour chaque composant de texte :

    ![aligner le texte.](images/AzureLabs-Lab1-26.png)

10. Pour vous assurer que les objets texte de l' **interface utilisateur enfant** sont facilement lisibles, modifiez leur *couleur*. Pour ce faire, cliquez sur la barre (« noire » actuellement) en regard de la *couleur*. 

    ![Entrez les valeurs correspondantes pour les sorties de texte de l’interface utilisateur.](images/AzureLabs-Lab1-27.png)
 
11. Puis, dans la fenêtre nouvelle *couleur* , remplacez la *couleur hex* par : **0032EAFF**

    ![Mettez à jour la couleur en bleu.](images/AzureLabs-Lab1-28.png)
 
12. Vous trouverez ci-dessous l’aspect de l' **interface utilisateur** .
    1.  Dans le *volet hiérarchie*:

        ![Avoir une hiérarchie dans la structure fournie.](images/AzureLabs-Lab1-29.png)

    2.  Dans les vues *scène* et *jeu*:

        ![Avoir les vues scène et jeu dans la même structure.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Chapitre 5 : créer la classe Results

Le premier script que vous devez créer est la classe *results* , qui est chargée de fournir un moyen de voir les résultats de la traduction. La classe stocke et affiche les éléments suivants : 

- Résultat de la réponse d’Azure.
- État du microphone. 
- Résultat de la dictée (voix au texte).
- Résultat de la traduction.

Pour créer cette classe : 

1.  cliquez avec le bouton droit dans le *panneau Project*, puis **créez > dossier**. Nommez le dossier **scripts**. 
 
    ![Créer un dossier de scripts.](images/AzureLabs-Lab1-31.png)

    ![Ouvrez le dossier scripts.](images/AzureLabs-Lab1-32.png)
 
2.  Avec le dossier **scripts** créer, double-cliquez dessus pour l’ouvrir. Ensuite, dans ce dossier, cliquez avec le bouton droit, puis sélectionnez **créer >** **script C#**. Nommez les *résultats* du script. 

    ![Créez le premier script.](images/AzureLabs-Lab1-33.png)
 
3.  Double-cliquez sur le nouveau script *results* pour l’ouvrir avec **Visual Studio**.
4.  Insérez les espaces de noms suivants :

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  À l’intérieur de la classe, insérez les variables suivantes :

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  Ajoutez ensuite la méthode *éveillé ()* , qui sera appelée lors de l’initialisation de la classe. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Enfin, ajoutez les méthodes qui sont chargées de sortir les différentes informations de résultats à l’interface utilisateur. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  veillez à enregistrer les modifications apportées à *Visual Studio* avant de revenir à *unity*.

## <a name="chapter-6--create-the-microphonemanager-class"></a>Chapitre 6 : créer la classe *MicrophoneManager*

La deuxième classe que vous allez créer est *MicrophoneManager*.

Cette classe est chargée des opérations suivantes :

- Détection du périphérique d’enregistrement attaché au casque ou à l’ordinateur (selon la valeur par défaut).
- Capturez l’audio (voix) et utilisez la dictée pour le stocker en tant que chaîne.
- une fois que la voix a été suspendue, soumettez la dictée à la classe Traducteur.
- Hébergez une méthode qui peut arrêter la capture de la voix si vous le souhaitez.

Pour créer cette classe : 
1.  Double-cliquez sur le dossier **scripts** pour l’ouvrir. 
2.  Cliquez avec le bouton droit dans le dossier **scripts** , puis cliquez sur **créer > script C#**. Nommez le script *MicrophoneManager*. 
3.  Double-cliquez sur le nouveau script pour l’ouvrir avec Visual Studio.
4.  Mettez à jour les espaces de noms pour qu’ils soient identiques à ce qui suit, en haut de la classe *MicrophoneManager* :

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Ensuite, ajoutez les variables suivantes à l’intérieur de la classe *MicrophoneManager* :

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  Vous devez maintenant ajouter du code pour les méthodes *éveillé ()* et *Start ()* . Ils sont appelés lorsque la classe est initialisée :

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  Vous pouvez *supprimer* la méthode *Update ()* puisque cette classe ne l’utilise pas.
8.  à présent, vous avez besoin des méthodes que l’application utilise pour démarrer et arrêter la capture vocale, et la passer à la classe *Traducteur* , que vous allez bientôt créer. Copiez le code suivant et collez-le sous la méthode *Start ()* .

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > Bien que cette application ne l’utilise pas, la méthode *StopCapturingAudio ()* a également été fournie ici, si vous souhaitez implémenter la possibilité d’arrêter la capture de l’audio dans votre application.

9.  Vous devez maintenant ajouter un gestionnaire de dictée qui sera appelé lorsque la voix s’arrêtera. cette méthode passera ensuite le texte dicté à la classe *Traducteur* .

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. veillez à enregistrer les modifications apportées à Visual Studio avant de revenir à unity.

> [!WARNING]  
> à ce stade, vous remarquerez qu’une erreur s’affiche dans le panneau de la Console de l' *éditeur unity* (« le nom’Traducteur’n’existe pas... »). cela est dû au fait que le code fait référence à la classe *Traducteur* , que vous allez créer dans le chapitre suivant.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Chapitre 7 – appel à Azure et au service de traduction

le dernier script que vous devez créer est la classe *Traducteur* . 

Cette classe est chargée des opérations suivantes :

-   Authentification de l’application avec *Azure*, en échange d’un **jeton d’authentification**.
-   Utilisez le **jeton d’authentification** pour envoyer du texte (reçu à partir de la classe *MicrophoneManager* ) à traduire.
-   Recevoir le résultat traduit et le passer à la classe *results* pour le visualiser dans l’interface utilisateur.

Pour créer cette classe : 
1.  Accédez au dossier **scripts** que vous avez créé précédemment. 
2.  cliquez avec le bouton droit dans le **panneau Project**, puis **créez > Script C#**. appelez le script *Traducteur*.
3.  Double-cliquez sur le nouveau *Traducteur* script pour l’ouvrir **avec Visual Studio**.
4.  Ajoutez les espaces de noms suivants au début du fichier :

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  ajoutez ensuite les variables suivantes à l’intérieur de la classe *Traducteur* :

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - Les langages insérés dans l' **énumération** Languages sont simplement des exemples. N’hésitez pas à en ajouter d’autres si vous le souhaitez. l' [API prend en charge plus de 60 langues](/azure/cognitive-services/translator/languages) (y compris Klingon) !
    > - Il existe une [page plus interactive couvrant les langues disponibles](https://www.microsoft.com/translator/business/languages/). Toutefois, sachez que la page semble fonctionner uniquement lorsque la langue du site est définie sur «» (et que le site Microsoft est susceptible de rediriger vers votre langue native). Vous pouvez modifier la langue du site en bas de la page ou en modifiant l’URL.
    > - la valeur **authorizationKey** , dans l’extrait de code ci-dessus, doit être la **clé** que vous avez reçue lorsque vous vous êtes abonné au *API de traduction de texte Translator Text Azure*. Ce sujet a été abordé dans le [Chapitre 1](#chapter-1--the-azure-portal).

6.  Vous devez maintenant ajouter du code pour les méthodes *éveillé ()* et *Start ()* . 
7.  Dans ce cas, le code fait un appel à *Azure* à l’aide de la clé d’autorisation pour obtenir un *jeton*.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > Le jeton expire au bout de 10 minutes. Selon le scénario de votre application, vous devrez peut-être effectuer plusieurs fois le même appel de Coroutine.

8.  La Coroutine permettant d’obtenir le jeton est la suivante :

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > Si vous modifiez le nom de la méthode IEnumerator **GetTokenCoroutine ()**, vous devez mettre à jour les valeurs de chaîne d’appel *StartCoroutine* et *StopCoroutine* dans le code ci-dessus. En fonction de la [documentation Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), pour arrêter une *Coroutine* spécifique, vous devez utiliser la méthode de valeur de chaîne.

9.  Ensuite, ajoutez la Coroutine (avec une méthode de flux « support » juste en dessous) pour obtenir la traduction du texte reçu par la classe *MicrophoneManager* . ce code crée une chaîne de requête à envoyer à l' *API de traduction de texte Translator Text Azure*, puis utilise la classe UnityWebRequest unity interne pour effectuer un appel’obtenir’au point de terminaison avec la chaîne de requête. Le résultat est ensuite utilisé pour définir la traduction dans votre objet de résultats. Le code ci-dessous illustre l’implémentation :

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. veillez à enregistrer les modifications apportées à *Visual Studio* avant de revenir à *unity*.

## <a name="chapter-8--configure-the-unity-scene"></a>Chapitre 8 – configurer la scène Unity

1.  De retour dans l’éditeur Unity, cliquez et faites glisser la classe *results* *du* dossier **scripts** vers l’objet **Camera principal** dans le *panneau hiérarchie*.
2.  Cliquez sur l' **appareil photo principal** et observez le panneau de l' *inspecteur*. Vous remarquerez que dans le composant *script* nouvellement ajouté, il y a quatre champs avec des valeurs vides. Il s’agit des références de sortie des propriétés dans le code. 
3.  Faites glisser les objets de **texte** appropriés du volet de la *hiérarchie* vers ces quatre emplacements, comme indiqué dans l’image ci-dessous.

    ![Met à jour les références cibles avec les valeurs spécifiées.](images/AzureLabs-Lab1-34.png)
  
4.  ensuite, cliquez et faites glisser la classe *Traducteur* du dossier **Scripts** vers l’objet **Camera principal** dans le *panneau hiérarchie*. 
5.  Ensuite, cliquez et faites glisser la classe *MicrophoneManager* du dossier **scripts** vers l’objet **Camera principal** dans le *panneau hiérarchie*. 
6.  Enfin, cliquez sur l' **appareil photo principal** et observez le panneau de l' *inspecteur*. Vous remarquerez que dans le script que vous avez glissé, il existe deux zones de liste déroulante qui vous permettent de définir les langues.
 
    ![Vérifiez que les langues de traduction prévues sont entrées.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Chapitre 9 – test en réalité mixte

À ce stade, vous devez vérifier que la scène a été correctement implémentée.

Assurez-vous que :

- Tous les paramètres mentionnés dans le [Chapitre 1](#chapter-1--the-azure-portal) sont correctement définis. 
- les *résultats*, *Traducteur* et *MicrophoneManager*, les scripts sont attachés à l’objet **Camera principal** . 
- vous avez placé votre **clé** de Service *Azure API de traduction de texte Translator Text* dans la variable **authorizationKey** dans le Script *Traducteur* .  
- Tous les champs du volet principal de l’inspecteur de l' *appareil photo* sont correctement affectés.
- Votre microphone fonctionne lors de l’exécution de votre scène (dans le cas contraire, vérifiez que votre microphone attaché est l’appareil *par défaut* et que vous l’avez [configuré correctement dans Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

Vous pouvez tester le casque immersif en appuyant sur le bouton **lecture** dans l' *éditeur Unity*.
L’application doit fonctionner par le biais du casque immersif attaché.

> [!WARNING]  
> Si une erreur s’affiche dans la console Unity à propos du changement de périphérique audio par défaut, la scène peut ne pas fonctionner comme prévu. Cela est dû à la façon dont le portail de réalité mixte traite les microphones intégrés pour les casques. Si vous voyez cette erreur, arrêtez simplement la scène et redémarrez-la et les choses devraient fonctionner comme prévu.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Chapitre 10 : créer la solution UWP et chargement sur l’ordinateur local

Tout ce qui est nécessaire pour la section Unity de ce projet est maintenant terminé. il est donc temps de la générer à partir d’Unity.

1.  accédez à **build Paramètres**: **fichier > build Paramètres...**
2.  dans la fenêtre **Paramètres de build** , cliquez sur **générer**.

    ![Générez la scène Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Si ce n’est pas déjà le cas, Tick **Unity C# Projects**.
4.  Cliquez sur **Générer**. Unity lance une fenêtre de l' *Explorateur de fichiers* , dans laquelle vous devez créer, puis sélectionner un dossier dans lequel générer l’application. Créez ce dossier maintenant, puis nommez-le *application*. Ensuite, avec le dossier d' *application* sélectionné, appuyez sur **Sélectionner un dossier**. 
5.  Unity commence à générer votre projet dans le dossier de l' *application* . 
6.  Une fois la génération de Unity terminée (cela peut prendre un certain temps), une fenêtre de l' *Explorateur de fichiers* s’ouvre à l’emplacement de votre Build (Vérifiez la barre des tâches, car elle ne s’affiche pas toujours au-dessus de votre Windows, mais vous informera de l’ajout d’une nouvelle fenêtre).

## <a name="chapter-11--deploy-your-application"></a>Chapitre 11 – déployer votre application

Pour déployer votre application :

1.  Accédez à votre nouvelle build Unity (le dossier de l' *application* ) et ouvrez le fichier solution avec *Visual Studio*.
2.  Dans la configuration de la solution, sélectionnez **Déboguer**.
3.  Dans la plateforme de la solution, sélectionnez **x86**, **ordinateur local**. 

    > pour le Microsoft HoloLens, il peut s’avérer plus facile de définir cette valeur sur *Machine distante*, de sorte que vous n’êtes pas attaché à votre ordinateur. Toutefois, vous devez également effectuer les opérations suivantes :
    > - identifiez l' **adresse IP** de votre HoloLens, qui se trouve dans le *Paramètres > réseau & Internet > Wi-Fi > options avancées*. IPv4 est l’adresse que vous devez utiliser. 
    > - Assurez-vous que le *mode développeur* est **activé**; trouvé dans *Paramètres > mettre à jour & > de sécurité pour les développeurs*.

    ![Déployez la solution à partir de Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Accédez au **menu Générer** , puis cliquez sur **déployer la solution** pour chargement l’application sur votre PC.
5.  Votre application doit maintenant apparaître dans la liste des applications installées, prêtes à être lancées.
6.  Une fois lancé, l’application vous invite à autoriser l’accès au microphone. Veillez à cliquer sur le bouton **Oui** .
7.  Vous êtes maintenant prêt à commencer la traduction.

## <a name="your-finished-translation-text-api-application"></a>Votre application API de texte de traduction terminé

Félicitations, vous avez créé une application de réalité mixte qui tire parti de l’API de traduction de texte Azure pour convertir la parole en texte traduit.

![Produit final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Exercices bonus

### <a name="exercise-1"></a>Exercice 1

Pouvez-vous ajouter la fonctionnalité de conversion de texte par synthèse vocale à l’application, afin que le texte retourné soit parlé ?

### <a name="exercise-2"></a>Exercice 2

Permet à l’utilisateur de modifier les langues source et de sortie (« from » et « to ») au sein de l’application elle-même, de sorte que l’application n’a pas besoin d’être reconstruite chaque fois que vous souhaitez modifier des langues.