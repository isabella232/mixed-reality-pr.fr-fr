---
title: Activation de la sécurité de connexion pour la communication à distance holographique
description: Cette page explique comment configurer la communication à distance holographique pour utiliser des connexions chiffrées et authentifiées entre le lecteur et les applications distantes.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, communication à distance, accès distant holographique, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, sécurité, authentification, serveur à client
ms.openlocfilehash: 6ac5284bdf9e5984fcf091b6502fb62a494e4fe8
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184646"
---
# <a name="enabling-connection-security-for-holographic-remoting-c"></a>Activation de la sécurité de connexion pour la communication à distance holographique (C++)

>[!IMPORTANT]
>Ce guide est spécifique à la communication à distance holographique sur HoloLens 2.

Cette page vous donne une vue d’ensemble de la sécurité réseau pour la communication à distance holographique. Vous trouverez des informations sur

* la sécurité dans le contexte de la communication à distance holographique et la raison pour laquelle vous pouvez en avoir besoin
* mesures recommandées en fonction de différents cas d’utilisation
* implémentation de la sécurité dans votre solution de communication à distance holographique

## <a name="holographic-remoting-security"></a>Sécurité de la communication à distance holographique

La communication à distance holographique échange des informations sur un réseau. Si aucune mesure de sécurité n’est en place, les adversaires sur le même réseau peuvent compromettre l’intégrité de la communication ou accéder aux informations confidentielles.

la sécurité est désactivée pour les exemples d’applications et le lecteur de communication à distance holographique dans le magasin de Windows. Cela rend les exemples plus faciles à comprendre. Il vous aide également à commencer plus rapidement avec le développement.

Pour les tests de champ ou la production, nous vous recommandons vivement d’activer la sécurité dans votre solution de communication à distance holographique.

La sécurité dans la communication à distance holographique, lorsqu’elle est configurée correctement pour votre cas d’utilisation, vous offre les garanties suivantes :

* **Authenticité :** le joueur et l’application distante peuvent vérifier que l’autre côté est bien celui qu’ils revendiquent
* **Confidentialité :** aucun tiers ne peut lire les informations échangées entre le joueur et l’application distante
* **Intégrité :** Player et Remote peuvent détecter toute modification en transit de leur communication

>[!IMPORTANT]
>pour pouvoir utiliser les fonctionnalités de sécurité, vous devez implémenter à la fois un [lecteur personnalisé](holographic-remoting-create-player.md) et une application distante personnalisée à l’aide des api [Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) ou [OpenXR](holographic-remoting-create-remote-openxr.md) .

>[!NOTE]
> À partir de la version [2.4.0](holographic-remoting-version-history.md#v2.4.0) , vous pouvez créer des applications distantes à l’aide de l' [API OpenXR](../native/openxr.md) . Vous trouverez [ci-dessous](#secure-connection-using-the-openxr-api)une vue d’ensemble de l’établissement d’une connexion sécurisée dans un environnement OpenXR.

## <a name="planning-the-security-implementation"></a>Planification de l’implémentation de la sécurité

Lorsque vous activez la sécurité dans la communication à distance holographique, la bibliothèque de communication à distance active automatiquement le chiffrement et les contrôles d’intégrité de toutes les données échangées sur le réseau.

Le fait de garantir une authentification appropriée nécessite néanmoins des tâches supplémentaires. Ce que vous devez faire exactement dépend de votre cas d’utilisation, et le reste de cette section concerne la procédure à suivre.

>[!IMPORTANT]
> Cet article ne peut fournir que des conseils généraux. Si vous n’êtes pas sûr, pensez à consulter un expert en sécurité qui peut vous fournir des conseils spécifiques à votre cas d’utilisation.

Tout d’abord : lorsque vous décrivez des connexions réseau, les termes _client_ et _serveur_ sont utilisés. Le serveur est le côté qui écoute les connexions entrantes sur une adresse de point de terminaison connue et le client est celui qui se connecte au point de terminaison du serveur.

>[!NOTE]
> Les rôles client et serveur ne sont pas liés au fait qu’une application joue le rôle d’un lecteur ou d’un serveur distant. Tandis que les exemples ont le joueur dans le rôle de serveur, il est facile d’inverser les rôles si cela s’avère mieux adapté à votre cas d’utilisation.

### <a name="planning-the-server-to-client-authentication"></a>Planification de l’authentification de serveur à client

Le serveur utilise des certificats numériques pour prouver son identité au client. Le client valide le certificat du serveur au cours de la phase de négociation de connexion. Si le client n’approuve pas le serveur, il met fin à la connexion à ce stade.

La manière dont le client valide le certificat de serveur, ainsi que les types de certificats de serveur qui peuvent être utilisés, dépendent de votre cas d’utilisation.

**Cas d’utilisation 1 :** Le nom d’hôte du serveur n’est pas fixe, ou le serveur n’est pas traité par le nom d’hôte.

Dans ce cas d’utilisation, il n’est pas pratique (voire possible) d’émettre un certificat pour le nom d’hôte du serveur. Nous vous recommandons de valider l’empreinte numérique du certificat à la place. Comme pour une empreinte humaine, l’empreinte numérique identifie de façon unique un certificat.

Il est important de communiquer l’empreinte numérique au client hors bande. Cela signifie que vous ne pouvez pas l’envoyer sur la même connexion réseau que celle utilisée pour la communication à distance. Au lieu de cela, vous pouvez l’entrer manuellement dans la configuration du client ou demander au client d’analyser un code QR.

**Cas d’utilisation 2 :** Le serveur peut être atteint sur un nom d’hôte stable.

Dans ce cas d’utilisation, le serveur a un nom d’hôte spécifique, et vous savez que ce nom n’est pas susceptible de changer. Vous pouvez ensuite utiliser un certificat émis pour le nom d’hôte du serveur. L’approbation est établie en fonction du nom d’hôte et de la chaîne d’approbation du certificat.

Si vous choisissez cette option, le client doit connaître le nom d’hôte du serveur et le certificat racine à l’avance.

### <a name="planning-the-client-to-server-authentication"></a>Planification de l’authentification client à serveur

Les clients s’authentifient auprès du serveur à l’aide d’un jeton de forme libre. Ce que ce jeton doit contenir dépend à nouveau de votre cas d’utilisation :

**Cas d’utilisation 1 :** Il vous suffit de vérifier l’identité de l’application cliente.

Dans ce cas d’utilisation, un secret partagé peut suffire. Ce secret doit être suffisamment complexe pour qu’il ne puisse pas être deviné.

Un secret partagé correct est un GUID aléatoire, qui est entré manuellement à la fois dans la configuration du serveur et du client. Pour en créer un, vous pouvez, par exemple, utiliser la `New-Guid` commande dans PowerShell.

Assurez-vous que ce secret partagé n’est jamais communiqué via des canaux non sécurisés. La bibliothèque de communication à distance garantit que le secret partagé est toujours envoyé chiffré et uniquement aux homologues approuvés.

**Cas d’utilisation 2 :** Vous devez également vérifier l’identité de l’utilisateur de l’application cliente.

Un secret partagé ne sera pas suffisant pour couvrir ce cas d’utilisation. Au lieu de cela, vous pouvez utiliser des jetons créés par un fournisseur d’identité. Un flux de travail d’authentification à l’aide d’un fournisseur d’identité ressemble à ceci :

* Le client autorise le fournisseur d’identité et demande un jeton
* Le fournisseur d’identité génère un jeton et l’envoie au client.
* Le client envoie ce jeton au serveur via la communication à distance holographique
* Le serveur valide le jeton du client par rapport au fournisseur d’identité

le [Plateforme d’identités Microsoft](/azure/active-directory/develop/)est un exemple de fournisseur d’identité.

Comme dans le cas d’usage précédent, assurez-vous que ces jetons ne sont pas envoyés via des canaux non sécurisés ou qu’ils sont exposés autrement.

## <a name="implementing-holographic-remoting-security"></a>Implémentation de la sécurité de la communication à distance holographique

N’oubliez pas que vous devez implémenter des applications à distance et de lecteur personnalisées si vous souhaitez activer la sécurité de la connexion. Vous pouvez utiliser les exemples fournis comme points de départ pour vos propres applications.

Pour activer la sécurité, appelez `ListenSecure()` au lieu de `Listen()` , et `ConnectSecure()` au lieu de `Connect()` pour établir la connexion de communication à distance.

Ces appels nécessitent que vous fournissiez des implémentations de certaines interfaces pour fournir et valider des informations relatives à la sécurité :

* Le serveur doit implémenter un fournisseur de certificats et un validateur d’authentification
* Le client doit implémenter un fournisseur d’authentification et un validateur de certificat.

Toutes les interfaces ont une fonction qui vous demande d’agir, qui reçoit un objet de rappel comme paramètre. À l’aide de cet objet, vous pouvez facilement implémenter la gestion asynchrone de la requête. Conservez une référence à cet objet et appelez la fonction d’achèvement lorsque l’action asynchrone est terminée. La fonction d’achèvement peut être appelée à partir de n’importe quel thread.

>[!TIP]
>L’implémentation d’interfaces WinRT peut facilement être effectuée à l’aide de C++/WinRT. Le chapitre [créer des API avec C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis) décrit cela en détail.

>[!IMPORTANT]
>l' `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` intérieur du package NuGet contient une documentation détaillée sur l’API liée aux connexions sécurisées.

### <a name="implementing-a-certificate-provider"></a>Implémentation d’un fournisseur de certificats

Les fournisseurs de certificats fournissent à l’application serveur le certificat à utiliser. L’implémentation se compose de deux parties :

1) Objet de certificat qui implémente l' `ICertificate` interface :

    * `GetCertificatePfx()` doit retourner le contenu binaire d’un `PKCS#12` magasin de certificats. Un `.pfx` fichier contenant `PKCS#12` des données, son contenu peut être utilisé directement ici.
    * `GetSubjectName()` doit retourner le nom convivial qui identifie le certificat à utiliser. Si aucun nom convivial n’est assigné au certificat, cette fonction doit retourner le nom du sujet du certificat.
    * `GetPfxPassword()` doit retourner le mot de passe requis pour ouvrir le magasin de certificats (ou une chaîne vide si aucun mot de passe n’est requis).

2) Un fournisseur de certificats qui implémente l' `ICertificateProvider` interface :
    * `GetCertificate()` doit construire un objet de certificat et le retourner en appelant `CertificateReceived()` sur l’objet de rappel.

### <a name="implementing-an-authentication-validator"></a>Implémentation d’un validateur d’authentification

Les validateurs d’authentification reçoivent le jeton d’authentification envoyé par le client et répondent avec le résultat de la validation.

Implémentez l' `IAuthenticationReceiver` interface comme suit :

* `GetRealm()` doit retourner le nom du domaine d’authentification (un domaine HTTP utilisé pendant l’établissement de la connexion à distance).
* `ValidateToken()` doit valider le jeton d’authentification du client et appeler `ValidationCompleted()` sur l’objet de rappel avec le résultat de la validation.

### <a name="implementing-an-authentication-provider"></a>Implémentation d’un fournisseur d’authentification

Les fournisseurs d’authentification génèrent ou récupèrent le jeton d’authentification à envoyer au serveur.

Implémentez l' `IAuthenticationProvider` interface comme suit :

* `GetToken()` doit générer ou récupérer le jeton d’authentification à envoyer. Une fois que le jeton est prêt, appelez la `TokenReceived()` méthode sur l’objet de rappel.

### <a name="implementing-a-certificate-validator"></a>Implémentation d’un validateur de certificat

Les validateurs de certificats reçoivent la chaîne de certificats envoyée par le serveur et déterminent si le serveur peut être approuvé.

Pour valider des certificats, vous pouvez utiliser la logique de validation du système sous-jacent. Cette validation du système peut soit prendre en charge votre propre logique de validation, soit la remplacer entièrement. Si vous ne transmettez pas votre propre validateur de certificat lors de la demande d’une connexion sécurisée, la validation du système sera automatiquement utilisée.

sur Windows, la validation du système recherche les éléments suivants :

* Intégrité de la chaîne de certificats : les certificats forment une chaîne cohérente qui se termine au niveau d’un certificat racine approuvé
* Validité du certificat : le certificat du serveur est dans son intervalle de validité et est émis pour l’authentification du serveur
* Révocation : le certificat n’a pas été révoqué
* Nom correspondance : le nom d’hôte du serveur correspond à l’un des noms d’hôte pour lequel le certificat a été émis

Implémentez l' `ICertificateValidator` interface comme suit :

 * `PerformSystemValidation()` doit retourner `true` si une validation système telle que décrite ci-dessus doit être effectuée. Dans ce cas, le résultat de la validation du système est passé en tant qu’entrée à la `ValidateCertificate()` méthode.
* `ValidateCertificate()` doit valider la chaîne de certificats, puis appeler `CertificateValidated()` sur le rappel passé avec le résultat final de la validation. Cette méthode accepte la chaîne de certificats, le nom du serveur avec lequel la connexion est établie, et indique si un contrôle de révocation doit être forcé. Si la chaîne de certificats contient plusieurs certificats, le premier est le certificat du sujet.

>[!NOTE]
>Si votre cas d’utilisation requiert une autre forme de validation (voir le cas d’utilisation de certificat #1 ci-dessus), ignorez entièrement la validation du système. Utilisez plutôt une API ou une bibliothèque qui peut gérer des certificats X. 509 encodés DER pour décoder la chaîne de certificats et effectuer les vérifications nécessaires à votre cas d’usage.

## <a name="secure-connection-using-the-openxr-api"></a>Connexion sécurisée à l’aide de l’API OpenXR

Lors de l’utilisation de l' [API OpenXR](../native/openxr.md) , toutes les API liées à la connexion sécurisée sont disponibles dans le cadre de l' `XR_MSFT_holographic_remoting` extension OpenXR.

>[!IMPORTANT]
>Pour en savoir plus sur l’API d’extension OpenXR de communication à distance holographique, consultez la [spécification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) qui se trouve dans le [référentiel GitHub des exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Les éléments clés pour la connexion sécurisée à l’aide de l' `XR_MSFT_holographic_remoting` extension OpenXR sont les rappels suivants.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`, génère ou récupère le jeton d’authentification à envoyer.
- `xrRemotingValidateServerCertificateCallbackMSFT`, valide la chaîne de certificats.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`, valide le jeton d’authentification du client.
- `xrRemotingRequestServerCertificateCallbackMSFT`, fournissez à l’application serveur le certificat à utiliser.

Ces rappels peuvent être fournis au runtime OpenXR de communication à distance via `xrRemotingSetSecureConnectionClientCallbacksMSFT` et `xrRemotingSetSecureConnectionServerCallbacksMSFT` . En outre, la connexion sécurisée doit être activée via le paramètre secureConnection sur la `XrRemotingConnectInfoMSFT` structure ou la `XrRemotingListenInfoMSFT` structure selon que vous utilisez `xrRemotingConnectMSFT` ou `xrRemotingListenMSFT` .

Cette API est similaire à l’API basée sur IDL décrite dans implémentation de la sécurité de l' [accès à distance holographique](#implementing-holographic-remoting-security). Toutefois, au lieu d’implémenter des interfaces, vous êtes censé fournir des implémentations de rappel. Vous trouverez un exemple détaillé dans l’exemple d' [application OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="see-also"></a>Voir aussi
* [Vue d’ensemble de la communication à distance holographique](holographic-remoting-overview.md)
* [écriture d’une application distante de communication à distance holographique à l’aide d’api Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Écriture d’une application distante de communication à distance holographique à l’aide d’API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Écriture d’une application de lecteur de communication à distance holographique personnalisée](holographic-remoting-create-player.md)
* [Résolution des problèmes et limitations de la communication à distance holographique](holographic-remoting-troubleshooting.md)
* [Termes du contrat de licence de la communication à distance holographique](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)