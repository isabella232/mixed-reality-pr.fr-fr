---
ms.openlocfilehash: c205e3b812eeb7a85bfe361d4fd83f9aec7b7999
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244977"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Bannière du logo Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. Télécharger la dernière version

Nous vous recommandons d’utiliser le flux [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) pour les nouveaux projets. Veillez à installer la dernière révision pour bénéficier des derniers correctifs de stabilité.
* La recommandation actuelle est d’utiliser **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)** , qui est la build LTS nécessaire pour MRTK v2 ci-dessous.
* Si vous devez utiliser une autre version de Unity pour des raisons spécifiques, vous pouvez installer différentes versions de Unity côte à côte.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Installer Mixed Reality Feature Tool

[Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) est un nouveau moyen pour les développeurs de découvrir et d’ajouter des packages de fonctionnalités de réalité mixte dans des projets Unity. 

Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation. Une fois que vous avez validé les packages souhaités, Mixed Reality Feature Tool les télécharge dans le projet de votre choix.

#### <a name="importing-the-mixed-reality-toolkit"></a>Importation du Mixed Reality Toolkit

![MRTK](../../design/images/MRTK_UX_Hero.png)

Le [Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) est un kit de développement multiplateforme open source pour les applications de réalité mixte. 

* Installez le package Mixed Reality Toolkit en suivant les [instructions d’installation et d’utilisation](../unity/welcome-to-mr-feature-tool.md#system-requirements) et en sélectionnant le package **Mixed Reality Toolkit Foundation**.

Nous recommandons de suivre la section Bien démarrer de nos parcours de développement [HoloLens](../unity/unity-development-overview.md#1-getting-started) ou [VR](../unity/unity-development-wmr-overview.md#1-getting-started) proposés. Si vous suivez déjà le parcours de développement Unity pour HoloLens, terminez le reste des étapes de configuration ci-dessous et passez aux [tutoriels Bien démarrer avec HoloLens 2](../unity/tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Notez que les instructions d’installation ciblent la dernière combinaison stable des versions de MRTK et d’Unity, qui sont **MRTK 2.5.1** et **Unity 2019.4 LTS**.

> [!NOTE]
> Si vous ne voulez pas utiliser MRTK pour Unity, vous devrez [générer vous-même un script pour toutes les interactions et tous les comportements](../unity/configure-unity-project.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Bannière Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit-Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a>Autres outils [facultatif]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> : bits de code et composants pouvant ne pas s’exécuter directement sur HoloLens ou sur des casques immersifs (réalité virtuelle), mais au lieu de cela, se coupler à eux pour créer des expériences ciblant Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> : collection de scripts et de composants partagés.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurer votre PC pour le développement de réalité mixte

Le SDK Windows 10 fonctionne de manière optimale sur le système d’exploitation Windows 10. Ce SDK est également pris en charge par Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Notez que les systèmes d’exploitation plus anciens ne prennent pas en charge tous les outils.

> [!NOTE]
> Vous pouvez développer et déployer vos applications pour HoloLens, les casques immersifs VR ou les deux. Veillez à répondre aux conditions ci-dessous en fonction de vos besoins.

#### <a name="for-hololens-development"></a>Pour le développement HoloLens

Lorsque vous configurez votre ordinateur de développement pour HoloLens, vérifiez qu’il répond aux exigences de configuration du système pour <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> et <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si vous souhaitez exécuter votre application sur un appareil HoloLens, vous devez suivre les [instructions de configuration du portail d’appareil Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Si vous prévoyez d’utiliser l’[émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), vérifiez également que votre PC répond à la [configuration système requise de l’émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Pour bien démarrer avec l’émulateur HoloLens, consultez [Utilisation de l’émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

Si vous prévoyez de développer des applications pour HoloLens et pour les casques immersifs (VR) Windows Mixed Reality, suivez les recommandations et les exigences système fournies dans la section ci-dessous.

#### <a name="hololens-troubleshooting"></a>Résolution des problèmes concernant HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>Le mode développeur est grisé

Si vous rencontrez des problèmes pour activer le mode développeur sur votre appareil, vous n’êtes peut-être pas le [propriétaire de l’appareil](/hololens/security-adminless-os). En mode multi-utilisateur, la personne qui utilise l’appareil en premier est le propriétaire de l’appareil et les utilisateurs suivants ne disposent pas des autorisations requises pour activer le mode développeur ni effectuer d’autres modifications de configuration. Toutefois, il existe une exception où le premier utilisateur peut ne pas être le propriétaire de l’appareil dans un environnement AutoPilot, ce qui est détaillé dans la [documentation sur la sécurité HoloLens](/hololens/security-adminless-os#device-owner).

Voici les solutions possibles :

* Faire en sorte que le propriétaire de l’appareil active le mode développeur avant de transmettre l’appareil à d’autres utilisateurs ou développeurs.
* Proposer à l’administrateur informatique/MDM d’activer la stratégie CSP [ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) pour l’appareil spécifique ou un groupe d’appareils de développeur. 
    * Cette stratégie peut être définie par des [packages de provisionnement](/hololens/hololens-provisioning) ou via [MDM pour les appareils HoloLens](/hololens/hololens-mdm-configure).
* Utiliser l’application [ARC (Advanced Recovery Companion)](/hololens/hololens-recovery).

> [!NOTE]
> Pour plus d’informations sur la gestion des appareils, consultez la vue d’ensemble de la **[gestion des appareils HoloLens](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>Je ne parviens pas à effectuer le déploiement sur USB

Si vous n’êtes pas en mesure de déployer une application directement sur USB, vérifiez que vous avez rempli toutes les conditions d’installation listées ci-dessus et suivez notre [tutoriel pas à pas](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).

#### <a name="immersive-vr-headset-requirements"></a>Exigences de configuration du casque immersif (VR)

>[!NOTE]
>Les instructions suivantes constituent les spécifications minimales actuellement recommandées qui s’appliquent à votre *ordinateur de développement* pour casques immersifs (VR). Ces instructions font l’objet de mises à jour régulières.

>[!WARNING]
>Vous ne devez pas confondre ces instructions avec les [instructions de compatibilité matérielle minimale](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), qui listent les *spécifications relatives à l’ordinateur personnel* qui est ciblé par votre application ou votre jeu pour casque immersif.

Si votre ordinateur de développement pour casques immersifs n’a pas de ports HDMI et/ou USB 3.0 de taille suffisante, vous aurez besoin d’[adaptateurs](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) pour connecter votre casque.

Il existe actuellement des [problèmes connus](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) avec certaines configurations matérielles, en particulier avec les notebooks à l’affichage hybride.

<table>
<tr>
<th></th><th> Minimum</th><th> Recommandé</th>
</tr><tr>
<td> Processeur</td><td> <b>Notebook :</b> Processeur Intel Mobile Core i5 7e génération, double cœur avec hyper-threading <b>Desktop :</b> Processeur Intel Desktop i5 6e génération, double cœur avec hyper-threading <b>OU</b> AMD FX4350 quadruple cœur 4.2 Ghz</td><td> <b>Desktop :</b> Intel Desktop i7 6e génération (6 cœurs) <b>OU</b> AMD Ryzen 5 1600 (6 noyaux, 12 threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook :</b> NVIDIA GTX 965M, AMD RX 460M (2 Go) ou supérieur, GPU compatible avec DX12 <b>Desktop :</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 Go) ou supérieur, GPU compatible avec DX12</td><td><b>Desktop :</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 Go) ou supérieur, GPU compatible avec DX12</td>
</tr><tr>
<td> Version WDDM du pilote GPU</td><td colspan="2"> Pilote WDDM 2.2</td>
</tr><tr>
<td> Enveloppe thermique</td><td colspan="2"> 15W ou supérieure</td>
</tr><tr>
<td> Ports d’affichage graphique</td><td colspan="2"> 1 port d’affichage graphique disponible pour les&#160;casques (HDMI 1.4 ou DisplayPort 1.2 pour les casques 60Hz, HDMI 2.0 ou DisplayPort 1.2 pour les casques 90Hz)</td>
</tr><tr>
<td> Résolution de l’affichage</td><td colspan="2"> Résolution : SVGA (800x600) ou une plus grande profondeur de couleurs : 32 bits de couleur par pixel</td>
</tr><tr>
<td> Mémoire</td><td> 8 Go de RAM ou plus</td><td> 16 Go de RAM ou plus</td>
</tr><tr>
<td> Stockage</td><td colspan="2"> &gt;10 Go d’espace libre supplémentaire</td>
</tr><tr>
<td> Ports USB</td><td colspan="2"> 1 port USB disponible pour les casques (USB 3.0 type A) <b>Remarque : il doit fournir un minimum de 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (connectivité des accessoires)</td>
</tr>
</table>

Si vous débutez dans le développement MRTK avec Unity, nous vous recommandons de suivre notre parcours de développement Unity :

> [!div class="nextstepaction"]
> [Démarrer votre parcours Unity pour HoloLens](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [Démarrer votre parcours Unity pour VR](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours des points de contrôle de développement Unity pour HoloLens que nous avons élaboré, votre tâche suivante consiste à suivre notre série de tutoriels HoloLens 2.

> [!div class="nextstepaction"]
> [Série de tutoriels HoloLens 2](../unity/tutorials/mr-learning-base-01.md)

Si vous suivez le parcours Unity pour VR, votre tâche suivante consiste à configurer votre projet.

> [!div class="nextstepaction"]
> [Configuration de votre projet pour WMR](../unity/configure-unity-project.md)

Vous pouvez revenir à tout moment aux points de contrôle de développement Unity pour [HoloLens](../unity/unity-development-overview.md#1-getting-started) et [VR](../unity/unity-development-wmr-overview.md#1-getting-started).

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. Télécharger la dernière version

Nous vous recommandons d’installer [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) ou ultérieure pour tirer pleinement parti de la prise en charge intégrée d’HoloLens.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importer le Mixed Reality Toolkit (MRTK)
![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) est un kit de développement multiplateforme open source pour les applications de réalité mixte. MRTK fournit un système d’entrée multiplateforme, des composants fondamentaux, ainsi que des modules communs pour les interactions spatiales. Le toolkit vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.

Pour l’installation, nous vous recommandons de suivre la [section Bien démarrer](../unreal/unreal-development-overview.md#1-getting-started) de notre [parcours de développement Unreal](../unreal/unreal-development-overview.md). Si vous suivez déjà le parcours de développement Unreal, terminez le reste des étapes de configuration ci-dessous et passez aux [tutoriels Bien démarrer avec HoloLens 2](../unreal/tutorials/unreal-uxt-ch1.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Image du logo Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Si vous ne souhaitez pas utiliser le MRTK pour Unreal, vous devrez générer un script pour toutes les interactions et tous les comportements.

#### <a name="other-tools-optional"></a>Autres outils [facultatif]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> : bits de code et composants pouvant ne pas s’exécuter directement sur HoloLens ou sur des casques immersifs (réalité virtuelle), mais au lieu de cela, se coupler à eux pour créer des expériences ciblant Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> : collection de scripts et de composants partagés.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurer votre PC pour le développement de réalité mixte

Le SDK Windows 10 fonctionne de manière optimale sur le système d’exploitation Windows 10. Ce SDK est également pris en charge par Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Notez que les systèmes d’exploitation plus anciens ne prennent pas en charge tous les outils.

> [!NOTE]
> Vous pouvez développer et déployer vos applications pour HoloLens, les casques immersifs VR ou les deux. Veillez à répondre aux conditions ci-dessous en fonction de vos besoins.

#### <a name="for-hololens-development"></a>Pour le développement HoloLens

Quand vous configurez votre PC de développement pour HoloLens, vérifiez qu’il répond à la configuration système requise pour [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) et <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si vous souhaitez exécuter votre application sur un appareil HoloLens, vous devez suivre les [instructions de configuration du portail d’appareil Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Si vous prévoyez d’utiliser l’[émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), vérifiez également que votre PC répond à la [configuration système requise de l’émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Si vous prévoyez de développer des applications pour HoloLens et pour les casques immersifs (VR) Windows Mixed Reality, suivez les recommandations et les exigences système fournies dans la section ci-dessous.

#### <a name="hololens-troubleshooting"></a>Résolution des problèmes concernant HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>Le mode développeur est grisé

Si vous rencontrez des problèmes pour activer le mode développeur sur votre appareil, vous n’êtes peut-être pas le [propriétaire de l’appareil](/hololens/security-adminless-os). En mode multi-utilisateur, la personne qui utilise l’appareil en premier est le propriétaire de l’appareil et les utilisateurs suivants ne disposent pas des autorisations requises pour activer le mode développeur ni effectuer d’autres modifications de configuration. Toutefois, il existe une exception où le premier utilisateur peut ne pas être le propriétaire de l’appareil dans un environnement AutoPilot, ce qui est détaillé dans la [documentation sur la sécurité HoloLens](/hololens/security-adminless-os#device-owner).

Voici les solutions possibles :

* Faire en sorte que le propriétaire de l’appareil active le mode développeur avant de transmettre l’appareil à d’autres utilisateurs ou développeurs.
* Proposer à l’administrateur informatique/MDM d’activer la stratégie CSP [ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) pour l’appareil spécifique ou un groupe d’appareils de développeur. 
    * Cette stratégie peut être définie par des [packages de provisionnement](/hololens/hololens-provisioning) ou via [MDM pour les appareils HoloLens](/hololens/hololens-mdm-configure).
* Utiliser l’application [ARC (Advanced Recovery Companion)](/hololens/hololens-recovery).

> [!NOTE]
> Pour plus d’informations sur la gestion des appareils, consultez la vue d’ensemble de la **[gestion des appareils HoloLens](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>Je ne parviens pas à effectuer le déploiement sur USB

Si vous n’êtes pas en mesure de déployer une application directement sur USB, vérifiez que vous avez rempli toutes les conditions d’installation listées ci-dessus et suivez notre [tutoriel pas à pas](../unreal/tutorials/unreal-uxt-ch6.md).

#### <a name="immersive-vr-headset-requirements"></a>Exigences de configuration du casque immersif (VR)

>[!NOTE]
>Les instructions suivantes constituent les spécifications minimales actuellement recommandées qui s’appliquent à votre *ordinateur de développement* pour casques immersifs (VR). Ces instructions font l’objet de mises à jour régulières.

>[!WARNING]
>Vous ne devez pas confondre ces instructions avec les [instructions de compatibilité matérielle minimale](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), qui listent les *spécifications relatives à l’ordinateur personnel* qui est ciblé par votre application ou votre jeu pour casque immersif.

Si votre ordinateur de développement pour casques immersifs n’a pas de ports HDMI et/ou USB 3.0 de taille suffisante, vous aurez besoin d’[adaptateurs](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) pour connecter votre casque.

Il existe actuellement des [problèmes connus](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) avec certaines configurations matérielles, en particulier avec les notebooks à l’affichage hybride.

<table>
<tr>
<th></th><th> Minimum</th><th> Recommandé</th>
</tr><tr>
<td> Processeur</td><td> <b>Notebook :</b> Processeur Intel Mobile Core i5 7e génération, double cœur avec hyper-threading <b>Desktop :</b> Processeur Intel Desktop i5 6e génération, double cœur avec hyper-threading <b>OU</b> AMD FX4350 quadruple cœur 4.2 Ghz</td><td> <b>Desktop :</b> Intel Desktop i7 6e génération (6 cœurs) <b>OU</b> AMD Ryzen 5 1600 (6 noyaux, 12 threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook :</b> NVIDIA GTX 965M, AMD RX 460M (2 Go) ou supérieur, GPU compatible avec DX12 <b>Desktop :</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 Go) ou supérieur, GPU compatible avec DX12</td><td><b>Desktop :</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 Go) ou supérieur, GPU compatible avec DX12</td>
</tr><tr>
<td> Version WDDM du pilote GPU</td><td colspan="2"> Pilote WDDM 2.2</td>
</tr><tr>
<td> Enveloppe thermique</td><td colspan="2"> 15W ou supérieure</td>
</tr><tr>
<td> Ports d’affichage graphique</td><td colspan="2"> 1 port d’affichage graphique disponible pour les&#160;casques (HDMI 1.4 ou DisplayPort 1.2 pour les casques 60Hz, HDMI 2.0 ou DisplayPort 1.2 pour les casques 90Hz)</td>
</tr><tr>
<td> Résolution de l’affichage</td><td colspan="2"> Résolution : SVGA (800x600) ou une plus grande profondeur de couleurs : 32 bits de couleur par pixel</td>
</tr><tr>
<td> Mémoire</td><td> 8 Go de RAM ou plus</td><td> 16 Go de RAM ou plus</td>
</tr><tr>
<td> Stockage</td><td colspan="2"> &gt;10 Go d’espace libre supplémentaire</td>
</tr><tr>
<td> Ports USB</td><td colspan="2"> 1 port USB disponible pour les casques (USB 3.0 type A) <b>Remarque : il doit fournir un minimum de 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (connectivité des accessoires)</td>
</tr>
</table>

Si vous débutez dans le développement MRTK avec Unreal, nous vous recommandons de suivre notre parcours de développement Unreal :

> [!div class="nextstepaction"]
> [Commencer votre parcours Unreal](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de points de contrôle de développement Unreal que nous avons élaboré, votre tâche suivante consiste à suivre notre série de tutoriels HoloLens 2.

> [!div class="nextstepaction"]
> [Série de tutoriels HoloLens 2](../unreal/tutorials/unreal-uxt-ch1.md)

Vous pouvez revenir aux [points de contrôle de développement Unreal](../unreal/unreal-development-overview.md#1-getting-started) à tout moment.

# <a name="native-openxr"></a>[Natif (OpenXR)](#tab/native)

 ![Développement d’applications en mode natif](../images/native_logo_banner.png)

Le développement OpenXR natif ne propose pas de moteur que vous pouvez télécharger. Vous trouverez tout ce dont vous avez besoin pour commencer le développement dans le document [Bien démarrer avec OpenXR](../native/openxr-getting-started.md).

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. Configurer votre PC pour le développement de réalité mixte

Le SDK Windows 10 fonctionne de manière optimale sur le système d’exploitation Windows 10. Ce SDK est également pris en charge par Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Notez que les systèmes d’exploitation plus anciens ne prennent pas en charge tous les outils.

#### <a name="for-hololens-development"></a>Pour le développement HoloLens

Quand vous configurez votre PC de développement pour HoloLens, vérifiez qu’il répond aux exigences de configuration système pour <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si vous souhaitez exécuter votre application sur un appareil HoloLens, vous devez suivre les [instructions de configuration du portail d’appareil Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Si vous prévoyez d’utiliser l’[émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), vérifiez également que votre PC répond à la [configuration système requise de l’émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Si vous prévoyez de développer des applications pour HoloLens et pour les casques immersifs (VR) Windows Mixed Reality, suivez les recommandations et les exigences système fournies dans la section ci-dessous.

> [!NOTE]
> Vous pouvez développer et déployer vos applications pour HoloLens, les casques immersifs VR ou les deux. Veillez à répondre aux conditions ci-dessous en fonction de vos besoins.

#### <a name="hololens-troubleshooting"></a>Résolution des problèmes concernant HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>Le mode développeur est grisé

Si vous rencontrez des problèmes pour activer le mode développeur sur votre appareil, vous n’êtes peut-être pas le [propriétaire de l’appareil](/hololens/security-adminless-os). En mode multi-utilisateur, la personne qui utilise l’appareil en premier est le propriétaire de l’appareil et les utilisateurs suivants ne disposent pas des autorisations requises pour activer le mode développeur ni effectuer d’autres modifications de configuration. Toutefois, il existe une exception où le premier utilisateur peut ne pas être le propriétaire de l’appareil dans un environnement AutoPilot, ce qui est détaillé dans la [documentation sur la sécurité HoloLens](/hololens/security-adminless-os#device-owner).

Voici les solutions possibles :

* Faire en sorte que le propriétaire de l’appareil active le mode développeur avant de transmettre l’appareil à d’autres utilisateurs ou développeurs.
* Proposer à l’administrateur informatique/MDM d’activer la stratégie CSP [ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) pour l’appareil spécifique ou un groupe d’appareils de développeur. 
    * Cette stratégie peut être définie par des [packages de provisionnement](/hololens/hololens-provisioning) ou via [MDM pour les appareils HoloLens](/hololens/hololens-mdm-configure).
* Utiliser l’application [ARC (Advanced Recovery Companion)](/hololens/hololens-recovery).

> [!NOTE]
> Pour plus d’informations sur la gestion des appareils, consultez la vue d’ensemble de la **[gestion des appareils HoloLens](/hololens/hololens-csp-policy-overview)** .

#### <a name="immersive-vr-headset-requirements"></a>Exigences de configuration du casque immersif (VR)

>[!NOTE]
>Les instructions suivantes constituent les spécifications minimales actuellement recommandées qui s’appliquent à votre *ordinateur de développement* pour casques immersifs (VR). Ces instructions font l’objet de mises à jour régulières.

>[!WARNING]
>Vous ne devez pas confondre ces instructions avec les [instructions de compatibilité matérielle minimale](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), qui listent les *spécifications relatives à l’ordinateur personnel* qui est ciblé par votre application ou votre jeu pour casque immersif.

Si votre ordinateur de développement pour casques immersifs n’a pas de ports HDMI et/ou USB 3.0 de taille suffisante, vous aurez besoin d’[adaptateurs](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) pour connecter votre casque.

Il existe actuellement des [problèmes connus](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) avec certaines configurations matérielles, en particulier avec les notebooks à l’affichage hybride.

<table>
<tr>
<th></th><th> Minimum</th><th> Recommandé</th>
</tr><tr>
<td> Processeur</td><td> <b>Notebook :</b> Processeur Intel Mobile Core i5 7e génération, double cœur avec hyper-threading <b>Desktop :</b> Processeur Intel Desktop i5 6e génération, double cœur avec hyper-threading <b>OU</b> AMD FX4350 quadruple cœur 4.2 Ghz</td><td> <b>Desktop :</b> Intel Desktop i7 6e génération (6 cœurs) <b>OU</b> AMD Ryzen 5 1600 (6 noyaux, 12 threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook :</b> NVIDIA GTX 965M, AMD RX 460M (2 Go) ou supérieur, GPU compatible avec DX12 <b>Desktop :</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 Go) ou supérieur, GPU compatible avec DX12</td><td><b>Desktop :</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 Go) ou supérieur, GPU compatible avec DX12</td>
</tr><tr>
<td> Version WDDM du pilote GPU</td><td colspan="2"> Pilote WDDM 2.2</td>
</tr><tr>
<td> Enveloppe thermique</td><td colspan="2"> 15W ou supérieure</td>
</tr><tr>
<td> Ports d’affichage graphique</td><td colspan="2"> 1 port d’affichage graphique disponible pour les&#160;casques (HDMI 1.4 ou DisplayPort 1.2 pour les casques 60Hz, HDMI 2.0 ou DisplayPort 1.2 pour les casques 90Hz)</td>
</tr><tr>
<td> Résolution de l’affichage</td><td colspan="2"> Résolution : SVGA (800x600) ou une plus grande profondeur de couleurs : 32 bits de couleur par pixel</td>
</tr><tr>
<td> Mémoire</td><td> 8 Go de RAM ou plus</td><td> 16 Go de RAM ou plus</td>
</tr><tr>
<td> Stockage</td><td colspan="2"> &gt;10 Go d’espace libre supplémentaire</td>
</tr><tr>
<td> Ports USB</td><td colspan="2"> 1 port USB disponible pour les casques (USB 3.0 type A) <b>Remarque : il doit fournir un minimum de 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (connectivité des accessoires)</td>
</tr>
</table>

Si vous débutez dans le développement Natif avec MRTK, nous vous recommandons de suivre notre parcours de développement Natif :

> [!div class="nextstepaction"]
> [Commencer votre parcours natif](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de points de contrôle de développement Natif que nous avons élaboré, la tâche suivante consiste à configurer votre environnement de développement pour HoloLens 2.

> [!div class="nextstepaction"]
> [Configurer pour HoloLens 2](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

Vous pouvez revenir aux [points de contrôle de développement Natif](../native/directx-development-overview.md#1-getting-started) à tout moment.