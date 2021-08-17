---
title: Canaux de données de communication à distance holographique personnalisés
description: Les canaux de données personnalisés peuvent être utilisés pour envoyer des données utilisateur sur la connexion de communication à distance holographique déjà établie.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, communication à distance, accès distant holographique, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, canaux de données
ms.openlocfilehash: 1adda10aa7792eaeab0ac32cb37d73dcfd2b58e6
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184710"
---
# <a name="custom-holographic-remoting-data-channels-c"></a>Canaux de données de communication à distance holographiques personnalisés (C++)

>[!NOTE]
>Ce guide est spécifique à la communication à distance holographique sur HoloLens 2.

Utilisez des canaux de données personnalisés pour envoyer des données personnalisées via une connexion de communication à distance établie.

>[!IMPORTANT]
>Les canaux de données personnalisés requièrent une application distante personnalisée et une application de lecteur personnalisée, car elle permet la communication entre les deux applications personnalisées.

>[!TIP]
>Un simple exemple de ping-pong se trouve dans les exemples Remote et Player à l’intérieur du [référentiel GitHub des exemples de communication](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)à distance holographique. Supprimez ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` les marques de commentaire dans les fichiers SampleRemoteMain. h/SamplePlayerMain. h pour activer l’exemple de code.


## <a name="create-a-custom-data-channel"></a>Créer un canal de données personnalisé


Pour créer un canal de données personnalisé, les champs suivants sont requis :
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Une fois la connexion établie, vous pouvez créer des canaux de données à partir du côté distant, du côté joueur ou des deux. RemoteContext et PlayerContext fournissent toutes les deux une ```CreateDataChannel()``` méthode pour créer des canaux de données. Le premier paramètre est l’ID de canal, qui est utilisé pour identifier le canal de données dans les opérations suivantes. Le deuxième paramètre est la priorité, qui spécifie la priorité avec laquelle les données de ce canal sont transférées de l’autre côté. Les ID de canal valides côté distant sont compris entre 0 et 63, et 64 jusqu’à 127 inclus pour le côté joueur. Les priorités valides sont ```Low``` , ```Medium``` ou ```High``` (des deux côtés).

Pour démarrer la création d’un canal de données côté **distant** :
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Pour démarrer la création d’un canal de données côté **joueur** :
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Pour créer un canal de données personnalisé, un seul côté (distant ou lecteur) doit appeler la ```CreateDataChannel``` méthode.

## <a name="handling-custom-data-channel-events"></a>Gestion des événements de canal de données personnalisé

Pour établir un canal de données personnalisé, l' ```OnDataChannelCreated``` événement doit être géré (à la fois sur le joueur et le côté distant). Il se déclenche lorsqu’un canal de données utilisateur a été créé par chaque côté et fournit un ```IDataChannel``` objet, qui peut être utilisé pour envoyer et recevoir des données sur ce canal.

Pour inscrire un écouteur sur l' ```OnDataChannelCreated``` événement :
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Pour être informé de la réception des données, inscrivez-vous à l' ```OnDataReceived``` événement sur l' ```IDataChannel``` objet fourni par le ```OnDataChannelCreated``` Gestionnaire. Inscrivez-vous à l' ```OnClosed``` événement pour être informé de la fermeture du canal de données.

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>Envoi de données

Pour envoyer des données sur un canal de données personnalisé, utilisez la ```IDataChannel::SendData()``` méthode. Le premier paramètre est un ```winrt::array_view<const uint8_t>``` pour les données qui doivent être envoyées. Le deuxième paramètre spécifie l’emplacement où les données doivent être renvoyées, jusqu’à ce que l’autre côté accuse réception de la réception. 

>[!IMPORTANT]
>En cas de mauvaises conditions de réseau, le même paquet de données peut arriver plusieurs fois. Le code de réception doit être en mesure de gérer cette situation.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Fermeture d’un canal de données personnalisé

Pour fermer un canal de données personnalisé, utilisez la ```IDataChannel::Close()``` méthode. Les deux côtés sont avertis par l' ```OnClosed``` événement une fois que le canal de données personnalisé a été fermé.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Voir aussi
* [Vue d’ensemble de la communication à distance holographique](holographic-remoting-overview.md)
* [écriture d’une application distante de communication à distance holographique à l’aide d’api Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Écriture d’une application distante de communication à distance holographique à l’aide d’API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Écriture d’une application de lecteur de communication à distance holographique personnalisée](holographic-remoting-create-player.md)
* [Résolution des problèmes et limitations de la communication à distance holographique](holographic-remoting-troubleshooting.md)
* [Termes du contrat de licence de la communication à distance holographique](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)