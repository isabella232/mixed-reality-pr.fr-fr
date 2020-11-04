---
ms.openlocfilehash: ad8f4a5ea9bda7915731f879da96cf7e007c58fb
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92755802"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Bannière du logo Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. Télécharger la dernière version

Nous vous recommandons d’utiliser le flux [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) pour les nouveaux projets. Veillez à installer la dernière révision pour bénéficier des derniers correctifs de stabilité.
* Nous recommandons actuellement d’utiliser **Unity 2019** , qui est la version LTS nécessaire à MRTK v2.
* Si vous devez utiliser une autre version de Unity pour des raisons spécifiques, vous pouvez installer différentes versions de Unity côte à côte.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importer le Mixed Reality Toolkit (MRTK)
![MRTK](../../design/images/MRTK_UX_Hero.png)

Le [Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) est un kit de développement multiplateforme open source pour les applications de réalité mixte. MRTK fournit un système d’entrée multiplateforme, des composants fondamentaux, ainsi que des modules communs pour les interactions spatiales. Le toolkit vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.

Pour l’installation, nous vous recommandons de suivre la [section Bien démarrer](../unity/unity-development-overview.md#1-getting-started) de notre [parcours de développement Unity](../unity/unity-development-overview.md). Si vous suivez déjà le parcours de développement Unity, terminez le reste des étapes de configuration ci-dessous et passez aux [tutoriels Bien démarrer avec HoloLens 2](../unity/tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Notez que les instructions d’installation ciblent la dernière combinaison stable des versions MRTK et Unity, **MRTK 2.4.0** et **Unity 2019.3.15**.

> [!NOTE]
> Si vous ne souhaitez pas utiliser le MRTK pour Unity, vous devrez générer un script pour toutes les interactions et tous les comportements.

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

Lorsque vous configurez votre ordinateur de développement pour HoloLens, vérifiez qu’il répond aux exigences de configuration du système pour <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> et <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si vous prévoyez d’utiliser l’[émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), vérifiez également que votre PC répond à la [configuration système requise de l’émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Pour bien démarrer avec l’émulateur HoloLens, consultez [Utilisation de l’émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

Si vous prévoyez de développer des applications pour HoloLens et pour les casques immersifs (VR) Windows Mixed Reality, suivez les recommandations et les exigences système fournies dans la section ci-dessous.

#### <a name="immersive-vr-headset-requirements"></a>Exigences de configuration du casque immersif (VR)

>[!NOTE]
>Les instructions suivantes constituent les spécifications minimales actuellement recommandées qui s’appliquent à votre *ordinateur de développement* pour casques immersifs (VR). Ces instructions font l’objet de mises à jour régulières.

>[!WARNING]
>Vous ne devez pas confondre ces instructions avec les [instructions de compatibilité matérielle minimale](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), qui listent les *spécifications relatives à l’ordinateur personnel* qui est ciblé par votre application ou votre jeu pour casque immersif.

Si vous utilisez un casque **Reverb G2** , téléchargez le plug-in **Microsoft-Valve OpenXR** (TODO: // Need link).

Si votre ordinateur de développement pour casques immersifs n’a pas de ports HDMI et/ou USB 3.0 de taille suffisante, vous aurez besoin d’[adaptateurs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) pour connecter votre casque.

Il existe actuellement des [problèmes connus](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) avec certaines configurations matérielles, en particulier avec les notebooks à l’affichage hybride.

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
> [Commencer votre parcours Unity](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de points de contrôle de développement Unity que nous avons élaboré, votre tâche suivante consiste à suivre notre série de tutoriels HoloLens 2.

> [!div class="nextstepaction"]
> [Série de tutoriels HoloLens 2](../unity/tutorials/mr-learning-base-01.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](../unity/unity-development-overview.md#1-getting-started) à tout moment.

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

Quand vous configurez votre PC de développement pour HoloLens, vérifiez qu’il répond à la configuration système requise pour [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) et <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si vous prévoyez d’utiliser l’[émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), vérifiez également que votre PC répond à la [configuration système requise de l’émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Si vous prévoyez de développer des applications pour HoloLens et pour les casques immersifs (VR) Windows Mixed Reality, suivez les recommandations et les exigences système fournies dans la section ci-dessous.

#### <a name="immersive-vr-headset-requirements"></a>Exigences de configuration du casque immersif (VR)

>[!NOTE]
>Les instructions suivantes constituent les spécifications minimales actuellement recommandées qui s’appliquent à votre *ordinateur de développement* pour casques immersifs (VR). Ces instructions font l’objet de mises à jour régulières.

>[!WARNING]
>Vous ne devez pas confondre ces instructions avec les [instructions de compatibilité matérielle minimale](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), qui listent les *spécifications relatives à l’ordinateur personnel* qui est ciblé par votre application ou votre jeu pour casque immersif.

Si vous utilisez un casque **Reverb G2** , téléchargez le plug-in **Microsoft-Valve OpenXR** (TODO: // Need link).

Si votre ordinateur de développement pour casques immersifs n’a pas de ports HDMI et/ou USB 3.0 de taille suffisante, vous aurez besoin d’[adaptateurs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) pour connecter votre casque.

Il existe actuellement des [problèmes connus](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) avec certaines configurations matérielles, en particulier avec les notebooks à l’affichage hybride.

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

Quand vous configurez votre PC de développement pour HoloLens, vérifiez qu’il répond aux exigences de configuration système pour <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si vous prévoyez d’utiliser l’[émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), vérifiez également que votre PC répond à la [configuration système requise de l’émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Si vous prévoyez de développer des applications pour HoloLens et pour les casques immersifs (VR) Windows Mixed Reality, suivez les recommandations et les exigences système fournies dans la section ci-dessous.

> [!NOTE]
> Vous pouvez développer et déployer vos applications pour HoloLens, les casques immersifs VR ou les deux. Veillez à répondre aux conditions ci-dessous en fonction de vos besoins.

#### <a name="immersive-vr-headset-requirements"></a>Exigences de configuration du casque immersif (VR)

>[!NOTE]
>Les instructions suivantes constituent les spécifications minimales actuellement recommandées qui s’appliquent à votre *ordinateur de développement* pour casques immersifs (VR). Ces instructions font l’objet de mises à jour régulières.

>[!WARNING]
>Vous ne devez pas confondre ces instructions avec les [instructions de compatibilité matérielle minimale](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), qui listent les *spécifications relatives à l’ordinateur personnel* qui est ciblé par votre application ou votre jeu pour casque immersif.

Si votre ordinateur de développement pour casques immersifs n’a pas de ports HDMI et/ou USB 3.0 de taille suffisante, vous aurez besoin d’[adaptateurs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) pour connecter votre casque.

Il existe actuellement des [problèmes connus](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) avec certaines configurations matérielles, en particulier avec les notebooks à l’affichage hybride.

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
