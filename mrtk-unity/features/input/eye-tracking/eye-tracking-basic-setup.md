---
title: Suivi oculaire - Configuration de base
description: Comment configurer le suivi oculaire dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, suivi oculaire,
ms.openlocfilehash: d8b47639729381a41e4fe1e1db86700bf9323860553934a6da4dfa4b15de49eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197454"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>Prise en main du suivi oculaire dans MRTK

Cette page explique comment configurer votre scène Unity MRTK pour utiliser le suivi oculaire dans votre application.
L’exemple suivant suppose que vous commencez avec une nouvelle scène.
Vous pouvez également consulter nos [exemples de suivi des yeux MRTK](../../example-scenes/eye-tracking-examples-overview.md) déjà configurés à l’aide de tonnes d’excellents exemples que vous pouvez créer directement.

## <a name="eye-tracking-requirements-checklist"></a>Liste de vérification des exigences de suivi oculaire

Pour que le suivi des yeux fonctionne correctement, les conditions suivantes doivent être remplies.
si vous débutez avec le suivi visuel sur HoloLens 2 et la configuration du suivi oculaire dans MRTK, ne vous inquiétez pas !
Nous verrons en détail comment les traiter plus en détail ci-dessous.

1. un _« oeil de regard Fournisseur de données »_ doit être ajouté au système d’entrée. Cela permet de fournir des données de suivi visuel à partir de la plateforme.
2. La fonctionnalité _« GazeInput »_ doit être activée dans le manifeste de l’application.
   **cette fonctionnalité peut être définie dans unity 2019, mais dans unity 2018 et versions antérieures, cette fonctionnalité est disponible uniquement dans Visual Studio et via l’outil de génération MRTK**
3. le HoloLens **doit** être étalonné par un œil pour l’utilisateur actuel. Consultez notre [exemple pour détecter si un utilisateur est étalonné ou non](eye-tracking-is-user-calibrated.md).

### <a name="a-note-on-the-gazeinput-capability"></a>Remarque sur la fonctionnalité GazeInput

les outils de génération fournis par MRTK (c.-à-d. Shared Computer Toolkit en réalité mixte > utilitaires-> fenêtre de génération) peuvent automatiquement activer la fonctionnalité GazeInput. Pour ce faire, vous devez vérifier que la « fonctionnalité d’entrée en regard » est cochée sous l’onglet « options de génération AppX » :

![Outils de génération MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

Cet outil trouvera le manifeste AppX une fois la build Unity terminée et ajoutera manuellement la fonctionnalité GazeInput.
**avant unity 2019, cet outil n’est pas actif lors de l’utilisation de la fenêtre de génération intégrée d’unity** (c’est-à-dire Paramètres de build de fichier >).

Avant Unity 2019, lors de l’utilisation de la fenêtre de génération d’Unity, la capacité devra être ajoutée manuellement après la génération Unity, comme suit :

1. ouvrez votre projet de Visual Studio compilé, puis ouvrez le _Package. appxmanifest_ dans votre solution.
2. Veillez à cocher la case _'GazeInput'_ sous _capacités_. si vous ne voyez pas de fonctionnalité _« GazeInput »_ , vérifiez que votre système répond [à la configuration requise pour l’utilisation de MRTK](/windows/mixed-reality/develop/install-the-tools) (en particulier la version SDK Windows).

_Remarque :_ Vous ne devez effectuer cette opération que si vous effectuez une génération dans un nouveau dossier de Build.
Cela signifie que si vous avez déjà créé votre projet Unity et que vous avez configuré le appxmanifest avant et que vous ciblez à présent le même dossier, vous n’aurez pas besoin de réappliquer vos modifications.

## <a name="setting-up-eye-tracking-step-by-step"></a>Configuration du suivi des yeux pas à pas

### <a name="setting-up-the-scene"></a>Configuration de la scène

configurez _MixedRealityToolkit_ en cliquant simplement sur _« Mixed reality Shared Computer Toolkit-> configure... »_ dans la barre de menus.

![MRTK configurer](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>Configuration des profils MRTK requis pour le suivi oculaire

Après avoir configuré votre scène MRTK, vous êtes invité à choisir un profil pour MRTK.
Vous pouvez simplement sélectionner _DefaultMixedRealityToolkitConfigurationProfile_ , puis sélectionner l’option _« copier & personnaliser »_ .

![Profil MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>Créer un « fournisseur de données de regard pour les yeux »

- Cliquez sur l’onglet _« entrée »_ dans votre profil MRTK.
- Pour modifier la valeur par défaut ( _« DefaultMixedRealityInputSystemProfile »_ ), cliquez sur le bouton _« cloner »_ en regard de celle-ci. Un menu _« cloner un profil »_ s’affiche. Cliquez simplement sur _cloner_ en bas de ce menu.
- Double-cliquez sur votre nouveau profil d’entrée, développez _'input Data providers'_ et sélectionnez _' + Add Fournisseur de données'_.
- Créer un nouveau fournisseur de données :
  - sous **Type** _, sélectionnez «Microsoft. MixedReality. Shared Computer Toolkit. WindowsMixedReality. Input'_  ->  _'WindowsMixedRealityEyeGazeDataProvider'_
  - pour la **ou les plateformes,** sélectionnez _« Windows universel »_.

![Fournisseur de données MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Simulation du suivi oculaire dans l’éditeur Unity

Vous pouvez simuler l’entrée de suivi oculaire dans l’éditeur Unity pour vous assurer que les événements sont correctement déclenchés avant de déployer l’application sur votre HoloLens 2.
Le signal de point de regard de l’œil est simulé en utilisant simplement l’emplacement de la caméra comme point de regard de l’œil oculaire et le vecteur d’avance de la caméra comme point de regard de l’œil.
Bien que cela soit parfait pour les tests initiaux, veuillez noter qu’il ne s’agit pas d’une bonne imitation pour des mouvements d’œil rapides.
Pour ce faire, il est préférable de garantir des tests fréquents de vos interactions oculaires sur le HoloLens 2.

1. **Activer le suivi oculaire simulé**:
    - Cliquez sur l’onglet _« entrée »_ dans votre profil de configuration MRTK.
    - À partir de là, accédez au _« fournisseur de données d’entrée »_«  ->  _service de simulation d’entrée_».
    - Clonez le _« DefaultMixedRealityInputSimpulationProfile »_ pour y apporter des modifications.
    - Cochez la case _« simuler la position oculaire »_ .

    ![MRTK yeux simuler](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **Désactiver le curseur en regard de l’en-tête par défaut**: en général, il est recommandé d’éviter d’afficher un curseur en regard de l’œil ou, si nécessaire, de le rendre _très_ subtil.
Nous vous recommandons de masquer par défaut le curseur de pointage en forme d’en-tête par défaut attaché au profil de pointeur en regard de MRTK.
    - Accédez à votre profil de configuration MRTK-> _«_  ->  _pointeurs_ d’entrée »
    - Clonez le _« DefaultMixedRealityInputPointerProfile »_ pour y apporter des modifications.
    - en haut du _pointeur Paramètres_, vous devez assigner un curseur prefab à _« GazeCursor »_. Pour ce faire, vous pouvez sélectionner le Prefab _« EyeGazeCursor »_ dans MRTK Foundation.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Activation du point d’interdépendance oculaire dans le fournisseur de regard

dans HoloLens v1, le point de regard de l’en-tête était utilisé comme technique de pointage principal.
Tandis que le point de vue est toujours disponible via le _GazeProvider_ dans MRTK, qui est attaché à votre [appareil photo](https://docs.unity3d.com/ScriptReference/Camera.html), vous pouvez cocher la case _« IsEyeTrackingEnabled »_ dans les paramètres de pointage du profil du pointeur d’entrée.

>[!NOTE]
>Les développeurs peuvent basculer entre le code de regard basé sur les yeux et le point d’arrêt en regard de l’œil en modifiant la propriété _« IsEyeTrackingEnabled »_ de _« GazeProvider »_.  

>[!IMPORTANT]
>Si l’une des exigences de suivi oculaire n’est pas satisfaite, l’application repasse automatiquement au point de vue de la tête.

### <a name="accessing-eye-gaze-data"></a>Accès aux données de regard visuel

Maintenant que votre scène est configurée pour utiliser le suivi oculaire, voyons comment y accéder dans vos scripts : [accès aux données de suivi visuel via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) et [sélections de cibles prises en charge](eye-tracking-target-selection.md)par l’œil.

### <a name="testing-your-unity-app-on-a-hololens-2"></a>Test de votre application Unity sur un HoloLens 2

la génération de votre application avec le suivi oculaire doit être similaire à la façon dont vous compilez d’autres applications HoloLens 2 MRTK. Assurez-vous que vous avez activé la fonctionnalité *« entrée en regard »* , comme décrit ci-dessus dans la section, [*une remarque sur la capacité GazeInput*](#a-note-on-the-gazeinput-capability).

#### <a name="eye-calibration"></a>Étalonnage oculaire

Enfin, n’oubliez pas d’exécuter l’étalonnage oculaire sur votre HoloLens 2.
Le système de suivi oculaire ne retourne aucune entrée si l’utilisateur n’est pas étalonné.
Le moyen le plus simple d’atteindre l’étalonnage consiste à retourner le visière et à revenir en arrière.
Une notification système doit vous accueillir comme un nouvel utilisateur et vous demander de passer par l’étalonnage oculaire.
vous pouvez également trouver l’étalonnage des yeux dans les paramètres système : Paramètres > système > étalonnage > l’étalonnage des yeux.

#### <a name="eye-tracking-permission"></a>Autorisation de suivi oculaire

quand vous démarrez l’application sur votre HoloLens 2 pour la première fois, une invite s’affiche pour demander à l’utilisateur l’autorisation d’utiliser le suivi oculaire.
S’il n’est pas visible, cela indique généralement que la fonctionnalité _« GazeInput »_ n’a pas été définie.

Une fois l’invite d’autorisation affichée une fois, elle n’apparaît plus automatiquement.
si vous _« avez refusé l’autorisation de suivi oculaire »_, vous pouvez la réinitialiser dans les applications de Paramètres > Privacy->.

---

Vous devez commencer par utiliser le suivi oculaire dans votre application MRTK Unity.
N’oubliez pas de consulter [nos didacticiels de suivi des yeux MRTK et des exemples](../../example-scenes/eye-tracking-examples-overview.md) montrant comment utiliser l’entrée de suivi oculaire et fournir facilement des scripts que vous pouvez réutiliser dans vos projets.

---
[Retour à « suivi oculaire dans le MixedRealityToolkit »](eye-tracking-main.md)