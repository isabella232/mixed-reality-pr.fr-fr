---
title: Instructions de contribution
description: découvrez les étapes et les instructions de base pour contribuer au Guide du passionné de Windows Mixed Reality. Nous apprécions vos commentaires, modifications, ajouts et aide.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
appliesto:
- Windows 10
ms.openlocfilehash: fd47e806a1ac14d85f503d7d4f799b232cbd3e102c3d4494d5704082bf0e08ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188101"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Contribution au Guide du passionné de réalité mixte

Nous vous remercions de votre intérêt dans le Guide du passionné. Nous apprécions vos commentaires, modifications, ajouts et aide à l’amélioration de nos documents. Cette page décrit les étapes de base et les instructions à suivre pour contribuer.

> [!IMPORTANT]
> Tous les dépôts qui publient sur docs.microsoft.com ont adopté le [Code de conduite Open Source Microsoft](https://opensource.microsoft.com/codeofconduct/). Pour plus d’informations, consultez la [FAQ sur le code de conduite](https://opensource.microsoft.com/codeofconduct/faq/) ou envoyez vos questions ou vos commentaires à [opencode@microsoft.com](mailto:opencode@microsoft.com).<br>
>
> Les corrections mineures ou les clarifications pour la documentation, ainsi que les exemples de code dans les référentiels publics, sont couverts par les [Conditions d’utilisation du site web docs.microsoft.com](/legal/termsofuse). Les nouveautés et modifications significatives généreront un commentaire dans la requête de tirage pour vous inviter à signer un contrat de licence de contribution en ligne si vous n’êtes pas un employé de Microsoft. Vous devrez remplir le formulaire en ligne pour que nous puissions accepter votre demande de tirage (pull request).

## <a name="before-you-start"></a>Avant de commencer

si vous n’en avez pas déjà un, vous devez [créer un compte GitHub](https://github.com/join).

>[!NOTE]
>si vous êtes un employé de microsoft, liez votre compte GitHub à votre alias microsoft sur le [portail Open Source de microsoft](https://repos.opensource.microsoft.com/). Rejoignez les organisations **« Microsoft »** et **« MicrosoftDocs »** .

quand vous configurez votre compte GitHub, nous vous recommandons également les précautions de sécurité suivantes :
- Créez un [mot de passe fort pour votre compte GitHub](https://github.com/settings/admin).
- Activez [l’authentification à deux facteurs](https://github.com/settings/two_factor_authentication/configure).
- Enregistrez vos [codes de récupération](https://github.com/settings/auth/recovery-codes) dans un endroit sûr.
- Mettez à jour vos [paramètres de profil public](https://github.com/settings/profile).
   - Définissez votre nom et envisagez de configurer votre adresse de messagerie *publique* pour *ne pas afficher mon adresse de messagerie*.
   - Nous vous recommandons de télécharger une image de profil, car une miniature est affichée sur les pages docs auxquelles vous contribuez.
- Si vous envisagez d’utiliser la ligne de commande, vous pouvez configurer [git Credential Manager pour Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). De cette façon, vous n’aurez pas à entrer votre mot de passe chaque fois que vous effectuerez une contribution.

le système de publication étant lié à GitHub, ces étapes sont importantes. vous êtes alors inscrit comme auteur ou contributeur à chaque article à l’aide de votre alias de GitHub.

## <a name="how-to-make-a-change"></a>Comment apporter une modification

| Pour suggérer une modification de la documentation, procédez comme suit : | Captures d’écran. |
| :------------------- | :--------: |
| 1. Si vous affichez une page Docs.microsoft.com, cliquez sur le bouton **modifier** en haut à droite de la page.  Vous êtes redirigé vers le fichier source Markdown correspondant dans le [dépôt GitHub](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide). | ![Bouton modifier](images/edit_button.jpg) |
| 2. si vous n’avez pas encore de compte GitHub, cliquez sur s' **inscrire** dans le coin supérieur droit et créez un nouveau compte. | ![Bouton d’inscription](images/signup-for-github-button.png)|
| 3. dans la page GitHub correspondante qui s’ouvre, cliquez sur modifier (l’icône représentant un crayon). | ![Bouton crayon](images/pencil_button.jpg)|
| 4. dans le volet modifier le fichier, [Mettez à jour les métadonnées des fichiers](#updating-metadata) et utilisez la langue démarque pour modifier le contenu. ([Procédure d’écriture de la démarque.](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![Modifier le fichier](images/edit-in-github.png)|
| 5. cliquez sur Aperçu des modifications pour vérifier que la mise en forme se présente comme prévu. | ![Prévisualiser les modifications](images/edit-in-github.png)|
| 6. quand vous avez terminé, faites défiler la page vers le bas et cliquez sur « proposer un changement de fichier ». une page de comparaison des modifications s’affiche, vous permettant de vérifier vos modifications. Cliquez ensuite sur le bouton « créer une requête de tirage » pour soumettre vos modifications. Et vous avez terminé ! | ![Proposer une modification](images/propose.jpg)|

Une fois que vous avez envoyé des modifications (via une requête de tirage), elles sont examinées par un membre de l’équipe de documentation. Si votre demande est acceptée, les mises à jour sont publiées dans [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](/windows/mixed-reality/enthusiast-guide) .

* Pour la révision interne uniquement, vous pouvez voir vos modifications sur [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

### <a name="updating-metadata"></a>Mise à jour des métadonnées

Mettez à jour les métadonnées en haut de chaque article :
   * **titre**: titre de la page qui s’affiche sous l’onglet navigateur lorsque l’article est affiché. Les titres de page sont utilisés pour le SEO et l’indexation. par conséquent, ne modifiez pas le titre, sauf si cela est nécessaire (bien que cela soit moins critique avant que la documentation ne soit publique).
   * **Description**: rédigez une brève description du contenu de l’article, qui améliore le SEO et la découverte.
   * **auteur**: si vous êtes le propriétaire principal de la page, ajoutez votre alias de GitHub ici.
   * **ms. Author**: Si vous êtes le propriétaire principal de la page, ajoutez votre alias Microsoft ici (vous n’en avez pas besoin @microsoft.com , juste l’alias).
   * **ms. date**: mettez à jour la date si vous ajoutez du contenu majeur à la page, mais pas pour des correctifs tels que la clarification, la mise en forme, la grammaire ou l’orthographe.
   * **Mots clés**: aide sur les mots clés dans SEO (optimisation du moteur de recherche). Ajoutez des mots clés, séparés par une virgule et un espace, qui sont spécifiques à votre article, mais pas de ponctuation après le dernier mot clé de votre liste. Vous n’avez pas besoin d’ajouter des mots clés globaux qui s’appliquent à tous les articles, car ceux-ci sont gérés ailleurs. 

### <a name="renaming-or-deleting-an-existing-article"></a>Attribution d’un nouveau nom ou suppression d’un article existant

Si votre modification renomme ou supprime un article existant, veillez à ajouter une redirection. De cette façon, toute personne disposant d’un lien vers l’article existant continuera de se retrouver au bon endroit. Les redirections sont gérées par l' .openpublishing.redirection.jssur le fichier à la racine du référentiel.

Pour ajouter une redirection à .openpublishing.redirection.jssur, ajoutez une entrée au `redirections` tableau :

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- `source_path`Est le chemin d’accès relatif au référentiel relatif à l’ancien article que vous supprimez. Assurez-vous que le chemin commence par `mixed-reality-docs/enthusiast-guide` et se termine par `.md` .
- `redirect_url`Est l’URL publique relative de l’ancien article vers le nouvel article. Assurez-vous que cette URL **ne** contient `mixed-reality-docs/enthusiast-guide` `.md` pas ou, car elle fait référence à l’URL publique et non au chemin d’accès au référentiel. La liaison à une section dans le nouvel article à l’aide de `#section` est autorisée. Vous pouvez également utiliser un chemin d’accès absolu à un autre site, si nécessaire.
- `redirect_document_id` indique si vous souhaitez conserver l’ID du document dans le fichier précédent. Par défaut, il s’agit de `false`. Utilisez `true` si vous souhaitez conserver la `ms.documentid` valeur d’attribut de l’article Redirigé. Si vous conservez l’ID de document, les données, telles que les affichages de page et les classements, seront transférées vers l’article cible. Procédez ainsi si la redirection est principalement un changement de nom, et non un pointeur vers un autre article qui ne couvre qu’une partie du même contenu.

Si vous ajoutez une redirection, veillez à supprimer également l’ancien fichier.

### <a name="creating-a-new-article"></a>Création d’un article

utilisez le flux de travail suivant pour *créer de nouveaux articles* dans la documentation référentiel via GitHub dans un navigateur web :

1. Créez une fourche à partir de la branche « master » MicrosoftDocs/Mixed-Real/Tree/docs/passionné-Guide (à l’aide du bouton de **branchement** dans le coin supérieur droit).

   ![Dupliquez la branche principale.](images/forkbranch.png)
2. Dans le dossier « Mixed-Reality/passionné-guide », sélectionnez **Create New file (créer un fichier** ) dans le coin supérieur droit.
3. Créer un nom de page pour l’article (utilisez des traits d’Union à la place d’espaces et n’utilisez pas de ponctuation ou d’apostrophes) et ajoutez « . MD »

   ![Nommez votre nouvelle page.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Veillez à créer le nouvel article dans le dossier « Mixed-Real-docs/passionné ». Vous pouvez le vérifier en recherchant « /Mixed-Reality-docs/Enthusiast-guide » dans la ligne du nouveau nom de fichier.

4. En haut de votre nouvelle page, ajoutez le bloc de métadonnées suivant :

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. Renseignez les champs de métadonnées pertinents conformément aux instructions de la [section ci-dessus](#updating-metadata).
6. Écrivez le contenu de l’article à l’aide des [principes fondamentaux](#markdown-basics).
7. Ajoutez une `## See also` section au bas de l’article avec des liens vers d’autres articles pertinents.
8. Lorsque vous avez terminé, sélectionnez **valider le nouveau fichier**.
9. Sélectionnez **nouvelle demande de tirage (pull Request** ) et fusionnez la branche « master » de votre branche dans MicrosoftDocs/Mixed-Reality/passionné-Guide’Master' (Assurez-vous que la flèche pointe vers la bonne voie).

   ![Créer une requête de tirage (pull request) à partir de votre fourche dans MicrosoftDocs/Mixed-Reality/passionné-Guide](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>Utilisation des branches

le [Guide du passionné de la réalité mixte GitHub référentiel](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) utilise deux branches parentes principales [: Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), ce contenu peut être consulté sur le [site intermédiaire](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)et en [direct](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live), pour le contenu qui s’affiche sur le [site en ligne](/windows/mixed-reality/enthusiast-guide).

Lorsque vous faites des contributions, soumettez votre demande de tirage (PR) à la branche **principale** . Cette branche qui peut être visualisée sur le site intermédiaire ne doit contenir que des contributions prêtes pour publication sur le site actif. Vous pouvez également créer et soumettre une branche avec votre propre nom de branche unique, qui peut être sélectionné et affiché dans le site intermédiaire. (La branche **active** est uniquement autorisée à être utilisée par les administrateurs de contenu.)

## <a name="markdown-basics"></a>Les bases de Markdown

Les ressources suivantes vous permettront d’apprendre à modifier la documentation à l’aide du langage de démarque :

- [Principes de base de Markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Affiche de référence de démarque-en un clin d’œil](images/MarkdownPoster.pdf)
- [Ressources supplémentaires pour l’écriture de la démarque pour docs.microsoft.com](/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Ajout de tables

En raison de la façon dont les tableaux de styles docs.microsoft.com, ils n’ont pas de bordures ou de styles personnalisés, même si vous essayez le style CSS en ligne. Il semblera fonctionner pendant une période de temps limitée, mais la plateforme finira par supprimer le style de la table. Vous devez donc anticiper et garder vos tables simples. [Voici un site qui simplifie les tableaux de démarques](https://www.tablesgenerator.com/markdown_tables).

l' [Extension Docs de démarque pour Visual Studio Code](/teamblog/docs-extension) facilite également la génération de table si vous utilisez [Visual Studio Code (voir ci-dessous)](#using-visual-studio-code) pour modifier la documentation.

### <a name="adding-images"></a>Ajout d’images

Vous devez charger vos images dans le dossier « Mixed-Real-docs/images » dans référentiel, puis les référencer de manière appropriée dans l’article. Les images s’affichent automatiquement à la taille maximale, ce qui signifie que les images volumineuses remplissent toute la largeur de l’article. Nous vous recommandons de prédimensionner vos images avant de les charger. La largeur recommandée est comprise entre 600 et 700 pixels, même si vous devez monter ou diminuer la taille s’il s’agit d’une capture d’écran dense ou d’une fraction d’une capture d’écran, respectivement.

>[!IMPORTANT]
>Vous pouvez uniquement charger des images sur vos référentiel dupliqués avant la fusion. par conséquent, si vous envisagez d’ajouter des images à un article, vous devez [utiliser Visual Studio Code](#using-visual-studio-code) pour ajouter d’abord les images au dossier « images » de votre branche, ou vous assurer que vous avez effectué les opérations suivantes dans un navigateur web :
>
>1. A fait la duplication du référentiel MicrosoftDocs/Mixed-Reality.
>2. Modification de l’article dans votre fourche.
>3. Téléchargez les images que vous référencez dans votre article dans le dossier « Mixed-Real-docs/images » de votre fourche.
>4. Création d’une **requête de tirage** pour fusionner votre fourche dans la branche « master » MicrosoftDocs/de la réalité mixte.
>
>Pour savoir comment configurer vos propres référentiel dupliqués, suivez les instructions de création d' [un nouvel article](#creating-a-new-article).

## <a name="previewing-your-work"></a>Aperçu de votre travail

pendant la modification de GitHub via un navigateur web, vous pouvez sélectionner l’onglet d' **aperçu** près du haut de la page pour afficher un aperçu de votre travail avant de le valider. 

>[!NOTE]
>L’aperçu de vos modifications sur review.docs.microsoft.com est uniquement disponible pour les employés de Microsoft

Employés de Microsoft : une fois vos contributions fusionnées dans la branche principale, vous pouvez passer en revue le contenu avant qu’il ne soit public à l’adresse https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master . Recherchez votre article à l’aide de la table des matières de la colonne de gauche.

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Modification dans le navigateur et modification avec un client Desktop

La modification dans le navigateur est le moyen le plus simple pour apporter des modifications rapides, toutefois, il existe quelques inconvénients :

- Vous n’avez pas de vérification orthographique.
- Vous n’avez pas de lien intelligent vers d’autres articles (vous devez taper manuellement le nom de fichier de l’article).
- Il peut être laborieux de charger et de référencer des images.

si vous préférez ne pas traiter ces problèmes, utilisez un client de bureau comme [Visual Studio Code](https://code.visualstudio.com/) avec quelques [extensions utiles](#useful-extensions) pour contribuer.

## <a name="using-visual-studio-code"></a>Utilisation de Visual Studio Code

Pour les raisons mentionnées [ci-dessus](#editing-in-the-browser-vs-editing-with-a-desktop-client), vous préférerez peut-être utiliser un client de bureau pour modifier la documentation au lieu d’un navigateur Web. Nous vous recommandons d’utiliser [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Installation

procédez comme suit pour configurer Visual Studio Code pour qu’il fonctionne avec ce référentiel :

1. Dans un navigateur Web :
    1. Installez [git pour votre PC](https://git-scm.com/downloads).
    2. Installez [Visual Studio Code](https://code.visualstudio.com/).
    3. [Duplication de MicrosoftDocs/Mixed-realisation](#creating-a-new-article) si vous ne l’avez pas déjà fait.
    4. Dans votre fourche, sélectionnez **cloner ou télécharger** et copiez l’URL.
2. Créez un clone local de votre fourche dans Visual Studio Code :
    1. Dans le menu **affichage** , sélectionnez **palette de commandes**.
    2. Tapez « git : Clone ».
    3. Collez l’URL que vous avez copiée.
    4. Choisissez l’emplacement où enregistrer le clone sur votre PC.
    5. Sélectionnez **ouvrir référentiel** dans la fenêtre contextuelle.

### <a name="editing-documentation"></a>Modification de la documentation

Utilisez le flux de travail suivant pour apporter des modifications à la documentation avec Visual Studio Code :

>[!NOTE]
>toutes les instructions relatives à la [modification](#how-to-make-a-change) et à la [création](#creating-a-new-article) d’articles, ainsi que les [principes fondamentaux de la modification de la démarque](#markdown-basics), ci-dessus s’appliquent également à l’utilisation de Visual Studio Code.

1. Assurez-vous que votre fourche cloné est à jour avec la référentiel officielle.
   1. Dans un navigateur Web, créez une requête de tirage pour synchroniser les modifications récentes des autres contributeurs de MicrosoftDocs/Mixed-Reality’Master’sur votre fourche (Assurez-vous que la flèche pointe vers la bonne voie).
      
      ![Synchroniser les modifications de MicrosoftDocs/Mixed-Reality avec votre fourche](images/sync_repos.PNG)
   2. dans Visual Studio Code, sélectionnez le bouton synchroniser pour synchroniser votre branche fraîchement mise à jour sur le clone local.
      
      ![Cliquer sur l’image du bouton de synchronisation](images/sync_clone.png)
2. Créez ou modifiez des articles dans votre référentiel cloné à l’aide de Visual Studio Code.
   1. Modifiez un ou plusieurs articles (ajoutez des images au dossier « images » si nécessaire).
   2. **Enregistrer** les modifications dans l' **Explorateur**.
      
      ![Choisissez « Enregistrer tout » dans l’Explorateur](images/explorer_save.png)
   3. **Valide toutes les** modifications dans **le contrôle de code source** (message de validation en écriture quand vous y êtes invité).
      
      ![Choisissez « valider tout » dans le contrôle de code source](images/source_control_commit.png)
   4. Sélectionnez le bouton **synchroniser** pour resynchroniser vos modifications avec l’origine (votre fourche sur GitHub).
      
      ![Cliquez sur le bouton synchroniser.](images/sync_back.png)
3. Dans un navigateur Web, créez une requête de tirage pour synchroniser les modifications apportées à votre fourche en MicrosoftDocs/Mixed-Reality’Master' (Assurez-vous que la flèche pointe vers la bonne voie).

   ![Créer une requête de tirage (pull request) à partir de votre fourche dans MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Extensions utiles

les extensions de Visual Studio Code suivantes sont utiles lors de la modification de la documentation :

- [Extension docs de la marque pour Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -utilisez **Alt + M** pour afficher un menu d’options de création de documents, comme :
   - Recherchez et référencez des images que vous avez téléchargées.
   - Ajoutez une mise en forme comme des listes, des tables et des appels spécifiques aux documents, comme `>[!NOTE]` .
   - Recherchez et référencez des liens et des signets internes (liens vers des sections spécifiques dans une page).
   - Les erreurs de mise en forme sont mises en surbrillance (pointez votre souris sur l’erreur pour en savoir plus).
- [Vérificateur orthographique de code](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) : les mots mal orthographiés sont soulignés. Cliquez avec le bouton droit sur un mot mal orthographié pour le modifier ou enregistrez-le dans le dictionnaire.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>utilisation de problèmes pour fournir des commentaires sur Windows Mixed Reality Guide du passionné

Pour fournir des commentaires, ou pour indiquer un problème, plutôt que de modifier directement les pages de documentation, [créez un problème](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) et les propriétaires de contenu feront de leur mieux pour résoudre le problème en temps opportun.

Veillez à inclure le titre de la rubrique et l’URL si vous créez un problème concernant une page spécifique.

Nous vous remercions d’avoir pris en charge ce contenu.