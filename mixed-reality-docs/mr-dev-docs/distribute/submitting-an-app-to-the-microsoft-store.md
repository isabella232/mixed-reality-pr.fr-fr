---
title: Envoi d’une application au Microsoft Store
description: Explore le processus d’empaquetage, de test et d’envoi de vos applications de réalité mixte au Microsoft Store.
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, HoloLens, casques immersifs, app, uwp, envoyer, envoyer, filtres, métadonnées, configuration système requise, mots clés, wack, certification, package, appx, merchandising, casque de réalité mixte, casque windows mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 5ea0d48b96ff91f51ff565c652d5ec294e994692dcc7881e626ea7817b05d876
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197720"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Envoi d’une application au Microsoft Store

> [!IMPORTANT]
> Si vous envoyez une application inréelle, veillez à suivre les **[instructions de publication](../develop/unreal/unreal-publishing-to-store.md)** avant de continuer.

## <a name="prerequisites"></a>Prérequis

les [HoloLens](/hololens/hololens1-hardware) et le Windows 10 PC qui alimentent votre [casque immersif](../discover/immersive-headset-hardware-details.md) s’exécutent plateforme Windows universelle applications. que vous soumettez une application qui prend en charge HoloLens, le PC, ou les deux, l’envoi d’applications passe par l' [espace partenaires](https://partner.microsoft.com/dashboard).

Si vous n’avez pas encore de compte de développeur de l’espace partenaires, inscrivez-vous à un compte avant de passer à l' [installation](https://developer.microsoft.com/store/register) . Vous trouverez plus d’informations sur les instructions et les listes de vérification de l’envoi dans cet article sur les [envois d’application](/windows/uwp/publish/app-submissions).

> [!IMPORTANT]
> vous ne serez pas en mesure de soumettre des applications au Microsoft Store si votre compte de développeur de l’espace partenaires ne parvient pas à effectuer la vérification de l’emploi. Pour plus d’informations, contactez l' [équipe de support](https://developer.microsoft.com/windows/support) de l’espace partenaires.

## <a name="packaging-a-mixed-reality-app"></a>Empaquetage d’une application de réalité mixte

Il existe plusieurs étapes pour empaqueter une application de réalité mixte, y compris :

* Préparation correcte de toutes les ressources d’image
* sélection de l’image de vignette affichée dans le HoloLens menu Démarrer
* définition de la version cible et minimale de Windows pour l’application
* Définition des familles d’appareils cibles dans les dépendances de l’application
* Ajout de métadonnées pour associer l’application au Microsoft Store
* Création d’un package de téléchargement

Chacune de ces étapes de soumission est traitée dans sa propre section ci-dessous. nous vous recommandons de les passer en revue de manière séquentielle.

### <a name="prepare-image-assets-included-in-the-appx"></a>Préparer les ressources d’image incluses dans le AppX

Les ressources d’image suivantes sont requises pour que les outils de génération AppX créent votre application dans un package AppX, qui est requis pour l’envoi au Microsoft Store. Vous pouvez en savoir plus sur [les instructions relatives aux ressources de vignettes et d’icônes](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) sur MSDN.

| Élément multimédia requis | Mise à l’échelle recommandée | Format d'image | Où l’élément multimédia est-il affiché ? | 
|----------|----------|----------|------------------|
| Logo carré 71 x 71 | Quelconque |  PNG | N/A | 
| Logo carré 150 x 150 | 150 x 150 (échelle de 100%) ou 225x225 (échelle de 150%) | PNG | Démarrer les codes confidentiels et toutes les applications (si 310 x 310 n’est pas fourni), stocker les suggestions de recherche, la page de liste des boutiques, Store Browse, Store Search | 
|  Logo 310 étendu |  Quelconque  |  PNG  |  N/A | 
|  Logo du Windows Store |  75x75 (échelle de 150%)  |  PNG  |  Espace partenaires, application de rapport, rédiger un avis, ma bibliothèque | 
|  Écran de démarrage |  930x450 (échelle de 150%)  |  PNG  |  lanceur d’applications 2D (ardoise) | 

si vous développez pour HoloLens, il existe d’autres ressources recommandées que vous pouvez tirer parti des éléments suivants :

| Ressources recommandées | Mise à l’échelle recommandée | Où l’élément multimédia est-il affiché ? | 
|----------|----------|----------|
|  Logo carré 310 x 310 |  310 x 310 (échelle de 150%) |  Démarrer les épingles et toutes les applications | 

### <a name="live-tile-requirements"></a>Exigences relatives aux vignettes dynamiques

la menu Démarrer sur HoloLens utilisera par défaut l’image de vignette carré la plus grande incluse. Les applications publiées par Microsoft comportent un lanceur 3D facultatif, que vous pouvez ajouter à votre application en suivant les instructions d' [implémentation du lanceur d’applications 3D](implementing-3d-app-launchers.md) .

### <a name="specifying-target-and-minimum-version-of-windows"></a>Spécification de la version cible et minimale de Windows

si votre application de réalité mixte comprend des fonctionnalités spécifiques à une version de Windows, il est important de spécifier les versions de plateforme minimale et cible prises en charge.

**portez une attention particulière aux applications ciblant [Windows Mixed Reality des casques immersifs](../discover/immersive-headset-hardware-details.md), qui nécessitent au moins la Windows 10 Fall Creators Update (10,0 ; Build 16299) pour fonctionner correctement.**

vous êtes invité à définir la version cible et la version minimale de Windows lorsque vous créez un Project de Windows universel dans Visual Studio. pour les projets existants, vous pouvez modifier ce paramètre dans le menu **Project** en sélectionnant le **<propriétés du> de votre nom d’application** en bas du menu déroulant.

![définition des versions de plateforme minimale et cible dans Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
*Définition des versions de plateforme minimale et cible dans Visual Studio*

### <a name="specifying-target-device-families"></a>Spécification des familles d’appareils cibles

les applications de Windows Mixed Reality (pour les [HoloLens](/hololens/hololens1-hardware) et les [casques immersifs](../discover/immersive-headset-hardware-details.md)) font partie du plateforme Windows universelle, donc tout package d’application avec un **Windows.** la [famille d’appareils cibles](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) universels peut s’exécuter sur des pc HoloLens ou Windows 10 avec des casques immersifs. si vous ne spécifiez pas de famille d’appareils cibles dans votre manifeste d’application, vous pouvez ouvrir par inadvertance votre application sur des appareils Windows 10 indésirables. suivez les étapes ci-dessous pour spécifier la famille de périphériques Windows 10 prévue, puis [double-vérifiez que vous avez défini les familles d’appareils appropriées lorsque vous téléchargez votre package d’application dans l’espace partenaires pour la soumission des Microsoft Store.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* pour définir ce champ dans Visual Studio, cliquez avec le bouton droit sur **Package. appxmanifest** et sélectionnez **afficher le Code**, puis recherchez le champ nom du **TargetDeviceFamily** . Par défaut, elle doit ressembler à l’entrée suivante :

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* si vous créez une application **HoloLens** , vous pouvez vous assurer qu’elle est installée uniquement sur HoloLens en affectant à la famille d’appareils cibles la valeur **Windows. Holographique**: 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* si votre application requiert des fonctionnalités de **HoloLens 2** , telles que l’oeil ou le suivi de la main, vous pouvez vous assurer qu’elle est ciblée pour Windows versions 18362 ou ultérieures en définissant la famille de l’appareil cible sur **Windows. Holographique** avec un **MinVersion** de 10.0.18362.0 :

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* si votre application est créée pour **Windows Mixed Reality des casques immersifs**, vous pouvez vous assurer qu’elle est installée uniquement sur Windows 10 pc avec la Windows 10 Fall Creators Update (nécessaire pour Windows Mixed Reality) en affectant à la famille d’appareils cibles la valeur **Windows. Desktop** avec un **MinVersion** de 10.0.16299.0 :

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* enfin, si votre application est destinée à s’exécuter sur **HoloLens** et **Windows Mixed Reality des casques immersifs**, vous pouvez vous assurer que l’application n’est disponible que pour ces deux familles d’appareils et garantir que chaque cible a la version minimale Windows correcte en incluant une ligne pour chaque famille d’appareils cibles avec son MinVersion respectif :

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Vous pouvez en savoir plus sur le ciblage des familles d’appareils en lisant la [documentation TARGETDEVICEFAMILY UWP](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Associer l’application au Windows Store

lorsque vous associez votre application au Microsoft Store, les valeurs suivantes sont téléchargées dans le fichier manifeste de l’application locale des projets en cours :

* Nom complet du package
* Nom du package
* ID de l’éditeur
* Nom complet de l'éditeur
* Version

Si vous remplacez le fichier Package. appxmanifest par défaut par votre propre fichier de .xml personnalisé, vous ne pouvez pas associer votre application au Microsoft Store. L’Association d’un fichier manifeste personnalisé à la Banque génère un message d’erreur.

vous pouvez également tester les scénarios d’achat et de notification en accédant à votre solution Visual Studio et en sélectionnant **Project > store > associer l’application** au windows store.

### <a name="creating-an-upload-package"></a>Création d’un package de téléchargement

suivez les instructions indiquées dans [empaquetage d’applications Universal Windows pour Windows 10](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2).

la dernière étape de la création d’un package de téléchargement consiste à valider le package à l’aide du [Kit de Certification des applications Windows](#windows-app-certification-kit).

si vous ajoutez un package spécifique à HoloLens à un produit existant qui est disponible sur d’autres familles d’appareils Windows 10, prêtez attention aux éléments suivants : 

* [Comment les numéros de version peuvent avoir un impact sur les packages livrés à des clients spécifiques](/windows/uwp/publish/package-version-numbering)
* [Distribution des packages sur différents systèmes d’exploitation](/windows/uwp/publish/guidance-for-app-package-management)

L’aide générale est que le package avec le numéro de version le plus élevé pour un périphérique est celui distribué par le magasin.

Dans un scénario où il y a un **Windows.** Le package universel et un **Windows.** Le package holographique et le Windows. le numéro de version du package universel est plus élevé, un utilisateur HoloLens télécharge le numéro de version supérieur Windows. Package universel au lieu du Windows. Package holographique. 

Dans les cas où le scénario ci-dessus n’est pas le résultat que vous recherchez, il existe plusieurs solutions disponibles :

* Vérifiez vos packages spécifiques à la plateforme, par exemple Windows. Holographique, utilisez toujours un numéro de version plus élevé que vos packages agnostiques de plateforme, comme Windows. Universelle
* Ne pas empaqueter les applications comme Windows. Universel si vous avez également des packages spécifiques à la plateforme, empaquetez plutôt le Windows. Package universel pour les plateformes spécifiques pour lesquelles vous souhaitez qu’il soit disponible
* Créez un Windows unique. Package universel qui fonctionne sur toutes les plateformes. La prise en charge de cette option n’est pas idéale pour l’instant. les solutions ci-dessus sont donc recommandées.

>[!NOTE]
> pour prendre en charge votre application sur les deux HoloLens (1er génération) et HoloLen 2, vous devez télécharger deux packages d’application. l’une contenant x86 pour HoloLens (1re génération) et l’autre contenant ARM ou ARM64 pour HoloLens 2. 
> 
> Si vous incluez à la fois ARM et ARM64 dans votre package, la version de ARM64 est celle qui est utilisée sur HoloLens 2. 

>[!NOTE]
> Vous pouvez déclarer un package unique pour qu’il s’applique à plusieurs familles d’appareils cibles.

## <a name="testing-your-app"></a>Test de votre application

### <a name="windows-app-certification-kit"></a>Kit de certification des applications Windows

lorsque vous créez des packages d’application à envoyer à l’espace partenaires via Visual Studio, l’assistant créer des packages d’application vous invite à exécuter le Windows Kit de Certification des applications sur les packages créés. pour avoir un processus de soumission fluide au magasin, il est préférable de vérifier que la copie locale de votre application transmet les [tests du Kit de Certification de l’application Windows](/previous-versions/windows/apps/jj657973(v=win.10)) avant de les soumettre au windows store. l’exécution du Kit de Certification des applications Windows sur un HoloLens distant n’est pas prise en charge actuellement.

### <a name="run-on-all-targeted-device-families"></a>Exécuter sur toutes les familles d’appareils ciblées

la plateforme Windows universelle vous permet de créer une application unique qui s’exécute sur toutes les familles d’appareils Windows 10. toutefois, cela ne garantit pas que les applications de Windows universelles fonctionnent uniquement sur toutes les familles d’appareils. Il est important de [tester votre application](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) sur chacune des familles d’appareils choisies pour garantir une bonne expérience.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Envoi de votre application de réalité mixte au Store

Si vous soumettez une application de réalité mixte basée sur un projet Unity, reportez-vous à cette [vidéo](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) .

en général, l’envoi d’une application Windows Mixed Reality qui fonctionne sur HoloLens ou des casques immersifs revient à envoyer une application UWP au Microsoft Store. Une fois que vous avez [créé votre application en réservant son nom](/windows/uwp/publish/create-your-app-by-reserving-a-name), suivez la [liste de vérification de soumission UWP](/windows/uwp/publish/app-submissions).

L’une des premières choses à faire est de [Sélectionner une catégorie et une sous-catégorie](/windows/uwp/publish/category-and-subcategory-table) pour votre expérience de réalité mixte. Il est important de **choisir la catégorie la plus précise pour votre application**. Les catégories vous aident à trouver votre application dans les catégories de magasins appropriées et à s’assurer qu’elle s’affiche à l’aide de requêtes de recherche pertinentes. **Le fait de répertorier votre titre en VR en tant que jeu n’entraîne pas une meilleure exposition pour votre application** et peut l’empêcher de s’afficher dans des catégories qui sont plus adaptées et moins encombrées.

Toutefois, il existe quatre domaines clés dans le processus de soumission où vous souhaiterez effectuer des sélections spécifiques à la réalité mixte :
1. Dans la section **[déclarations de produit](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** , sous [Propriétés](/windows/uwp/publish/enter-app-properties).
2. Dans la section **[System Requirements](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** sous [Properties (propriétés](/windows/uwp/publish/enter-app-properties)).
3. Dans la section disponibilité de la **[famille d’appareils](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** , sous [packages](/windows/uwp/publish/upload-app-packages).
4. Dans plusieurs champs de la **[page de liste des boutiques](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** .

### <a name="mixed-reality-product-declarations"></a>Déclarations de produit de réalité mixte

Sur la page **[Propriétés](/windows/uwp/publish/enter-app-properties)** du processus d’envoi de l’application, vous trouverez plusieurs options relatives à la réalité mixte dans la section **[déclarations de produit](/windows/uwp/publish/app-declarations)** .

![Déclarations de produit de réalité mixte](images/product-declarations-900px.png)<br>
Déclarations de produit de réalité mixte

Tout d’abord, vous devez identifier les types d’appareils pour lesquels votre application offre une expérience de réalité mixte. l’identification des types d’appareils garantit que votre application est incluse dans Windows Mixed Reality regroupements dans le magasin.

en regard de « cette expérience a été conçue pour Windows Mixed Reality le : »
* Cochez la case **PC** si votre application offre une expérience VR lorsqu’un casque immersif est connecté au PC de l’utilisateur. Nous vous recommandons de cocher cette case si votre application est configurée pour s’exécuter exclusivement sur un casque immersif ou s’il s’agit d’un jeu de PC standard ou d’une application offrant un mode de réalité mixte ou du contenu bonus quand un casque est connecté.
* activez la case à cocher **HoloLens** uniquement si votre application offre une expérience holographique lorsqu’elle est exécutée sur HoloLens.
* Cochez **les deux** cases si votre application offre une expérience de réalité mixte sur les deux types d’appareils.

Si vous avez sélectionné « PC » ci-dessus, vous devez définir la « configuration de la réalité mixte » (niveau d’activité). cela s’applique uniquement aux expériences de réalité mixte qui s’exécutent sur des pc connectés à des casques immersifs, car les applications de réalité mixte sur HoloLens sont à l’échelle mondiale et l’utilisateur ne définit pas de limite lors de l’installation.
* Choisissez **assis + debout** si vous avez conçu votre application pour que l’utilisateur reste à une position. Par exemple, dans un jeu où vous êtes en mesure de contrôler un cockpit d’avion.
* Choisissez **toutes les expériences** si votre application est conçue avec l’intention pour l’utilisateur de se déplacer dans une limite définie au cours de l’installation. Par exemple, il peut s’agir d’un jeu dans lequel vous allez effectuer des étapes et des canards pour une exposition plus rapide.

### <a name="mixed-reality-system-requirements"></a>Configuration système requise pour la réalité mixte

Sur la page **[Propriétés](/windows/uwp/publish/enter-app-properties)** du processus d’envoi de l’application, vous trouverez plusieurs options relatives à la réalité mixte dans la section **[Configuration système requise](/windows/uwp/publish/enter-app-properties#system-requirements)** .

![Configuration système requise](images/system-reqs-800px.png)<br>
Configuration requise

Dans cette section, vous allez identifier le matériel minimal (obligatoire) et le matériel recommandé (facultatif) pour votre application de réalité mixte.

**Matériel d’entrée :**

utilisez les cases à cocher pour indiquer aux clients potentiels si votre **application prend en charge les** [entrées vocales](../design/voice-input.md), les contrôleurs **[Xbox ou](../discover/hardware-accessories.md#bluetooth-gamepads)** les **[contrôleurs de mouvement Windows Mixed Reality](../design/motion-controllers.md)**. Ces informations seront exposées dans la page de détails du produit de votre application dans le Store et vous aideront à faire figurer votre application dans les collections d’applications/jeux appropriées. Par exemple, une collection peut exister pour tous les jeux qui prennent en charge les contrôleurs de mouvement.

Veillez à sélectionner des cases à cocher pour « matériel minimum » ou « matériel recommandé » pour les types d’entrée. 

Par exemple : 
* si votre jeu nécessite des contrôleurs de mouvement, mais accepte les entrées vocales via le microphone, activez la case à cocher « matériel minimal » en regard de « contrôleurs de mouvement Windows Mixed Reality », mais la case à cocher « matériel recommandé » en regard de « microphone ». 
* si votre jeu peut être lu à l’aide d’un contrôleur xbox, d’un boîtier d’accès ou de contrôleurs de mouvement, vous pouvez activer la case à cocher « matériel minimal » en regard de « contrôleur xbox ou boîtier de commande », puis activer la case à cocher « matériel recommandé » en regard de « contrôleurs de mouvement Windows Mixed Reality », car les contrôleurs de mouvement offriront

**Windows Mixed Reality casque immersif :**

Le fait d’indiquer si un casque immersif est nécessaire pour utiliser votre application ou est facultatif, est essentiel à la satisfaction des clients et à l’éducation.

si votre application ne peut être utilisée *qu'* avec un casque immersif, activez la case à cocher « matériel minimal » en regard de « Windows Mixed Reality le casque immersif ». Elle sera exposée dans la page des détails du produit de votre application dans le Store sous la forme d’un avertissement au-dessus du bouton d’achat, de sorte que les clients ne pensent pas qu’ils achètent une application qui fonctionnera sur leur ordinateur comme une application de bureau traditionnelle.

si votre application s’exécute sur le bureau comme une application PC traditionnelle, mais offre une expérience de VR quand un casque immersif est connecté (que le contenu complet de votre application soit disponible ou seulement une partie), activez la case à cocher « matériel recommandé » en regard de « Windows Mixed Reality le casque immersif ». Aucun avertissement ne sera présenté au-dessus du bouton acheter sur la page de détails du produit de votre application si votre application fonctionne comme une application de bureau traditionnelle sans un casque immersif connecté.

**Spécifications du PC :**

si vous souhaitez que votre application atteigne autant de Windows Mixed Reality utilisateurs de casques immersifs que possible, [ciblez](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) les spécifications du pc pour [Windows Mixed Reality pc avec des graphiques intégrés](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

que votre application de réalité mixte cible la configuration minimale requise Windows Mixed Reality pc, ou qu’elle ait besoin d’une configuration de pc spécifique comme le GPU dédié d’un [Windows Mixed Reality Ultra PC] ( https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines , vous devez ajouter les spécifications de pc appropriées dans la colonne « matériel minimal ».

Si votre application de réalité mixte est conçue pour offrir de meilleures performances ou propose des graphiques de haute résolution sur une configuration de PC ou une carte graphique en particulier, vous devez inclure les spécifications de PC appropriées dans la colonne « matériel recommandé ».

Cela s’applique uniquement si votre application de réalité mixte utilise un casque immersif connecté à un PC. si votre application de réalité mixte s’exécute uniquement sur HoloLens, vous n’avez pas besoin d’indiquer les spécifications du PC, car HoloLens n’a qu’une seule configuration matérielle.

### <a name="device-family-availability"></a>Disponibilité de la famille d’appareils

si vous avez [empaqueté votre application correctement](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) dans Visual Studio, son chargement sur la page Packages doit générer une table avec les familles d’appareils disponibles.

![Tableau de disponibilité des familles d’appareils](images/device-family-table-900px.png)<br>
Tableau de disponibilité des familles d’appareils

si votre application de réalité mixte fonctionne sur des casques immersifs, au moins « Windows 10 Desktop » doit être sélectionné dans le tableau. si votre application de réalité mixte fonctionne sur HoloLens, vous devez sélectionner au moins « Windows 10 Holographique ». si votre application s’exécute sur les deux Windows Mixed Reality types de casque, vous devez sélectionner « Windows 10 Desktop » et « Windows 10 Holographique ».

>[!TIP]
>De nombreux développeurs peuvent rencontrer des erreurs lors du chargement du package de leur application liée à des incompatibilités entre le manifeste du package et les informations de votre compte d’application/éditeur dans l’espace partenaires. ces erreurs peuvent souvent être évitées en se connectant à Visual Studio avec le même compte que celui associé à votre compte de développeur Windows (celui que vous utilisez pour vous connecter à l’espace partenaires). si vous utilisez le même compte, vous pouvez associer votre application à son identité dans le Microsoft Store avant de l’empaqueter.

![Associer votre application au Microsoft Store](images/associate-your-app-700px.png)<br>
associer votre application au Microsoft Store dans Visual Studio

### <a name="store-listing-page"></a>Page de la liste des boutiques

Sur la page [Store Listing](/windows/uwp/publish/create-app-store-listings) du processus d’envoi d’applications, vous pouvez ajouter des informations utiles sur votre application de réalité mixte à plusieurs endroits.

>[!IMPORTANT]
>pour vous assurer que votre application est correctement catégorisée par le magasin et rendue détectable pour Windows Mixed Reality clients, vous devez ajouter **« Windows Mixed Reality »** comme l’un de vos « termes de recherche » pour l’application (vous pouvez rechercher des termes de recherche en développant la section « champs partagés »).

![ajouter Windows Mixed Reality aux termes de recherche](images/search-terms-800px.png)<br>
ajouter « Windows Mixed Reality » aux termes de recherche

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Offre d’essai gratuit pour votre jeu ou votre application

dans de nombreux cas, vos consommateurs n’auront aucune expérience de la réalité virtuelle avant d’acheter un Windows Mixed Reality casque immersif. Ils peuvent ne pas savoir ce qu’il faut attendre des jeux intenses ou se familiariser avec leur propre seuil de confort dans des expériences immersifs. de nombreux clients peuvent également essayer un Windows Mixed Reality casque immersif sur les pc qui ne sont pas badges en tant que [Windows Mixed Reality pc](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). En raison de ces considérations, nous vous recommandons vivement de proposer une [version d’évaluation gratuite](/windows/uwp/publish/set-app-pricing-and-availability#free-trial) pour votre application ou votre jeu de réalité mixte payant.

## <a name="see-also"></a>Voir aussi
* [Qu’est-ce que la réalité mixte ?](../discover/mixed-reality.md)
* [Vue d’ensemble du développement](../develop/development.md)
* [Vues d’applications](../design/app-views.md)
* [Comprendre les performances de la réalité mixte](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recommandations de performances pour unity](../develop/unity/performance-recommendations-for-unity.md)
* [Test de votre application dans HoloLens](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [instructions relatives à la compatibilité minimale du matériel PC Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)