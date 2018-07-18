---
title: Broker:Forwarded Message Sent, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Forwarded Message Sent event class
ms.assetid: d0ef74d9-a4ef-4918-aa21-6b267e85569f
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1e6db9afb690f2819be36f9308ecf9de2ae81999
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37217409"
---
# <a name="brokerforwarded-message-sent-event-class"></a>Broker:Forwarded Message Sent, classe d'événements
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement Broker:Forwarded Message Sent quand Service Broker transmet un message.  
  
## <a name="brokerforwarded-message-sent-event-class-data-columns"></a>Colonnes de données de la classe d'événements Broker:Forwarded Message Sent  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|BigintData1|`bigint`|Numéro de séquence du message.|52|non|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l’instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DBUserName|`nvarchar`|ID d'instance de broker pour le service dont provient le message.|40|non|  
|EventClass|`int`|Type de classe d'événements capturée. Toujours 139 pour Broker:Forwarded Message Sent.|27|non|  
|EventSequence|`int`|Numéro de séquence de cet événement.|51|non|  
|FileName|`nvarchar`|Nom du service auquel le message est destiné.|36|non|  
|GUID|`uniqueidentifier`|ID de conversation du dialogue. Cet identifiant est transmis en tant que partie intégrante du message et est partagé par les deux intervenants de la conversation.|54|non|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IndexID|`int`|Nombre de sauts restants au message transféré.|24|non|  
|IntegerData|`int`|Nombre de fragments du message transféré.|25|non|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|non|  
|LoginSid|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|ObjectId|`int`|Valeur de durée de vie du message transmis au moment de sa transmission.|22|non|  
|ObjectName|`nvarchar`|ID du message transféré.|34|non|  
|OwnerName|`nvarchar`|Identificateur de Service Broker vers lequel le message est dirigé.|37|non|  
|RoleName|`nvarchar`|Rôle du descripteur de conversation. Une des valeurs suivantes :<br /><br /> Initiateur. Cette instance de Service Broker a lancé la conversation.<br /><br /> Cible. Cette instance de Service Broker correspond à la cible de la conversation.|38|non|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|SPID|`int`|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|StartTime|`datetime`|Heure de début de l'événement, le cas échéant.|14|Oui|  
|Réussi|`int`|Temps consommé durant le processus de transfert.|23|non|  
|TargetLoginName|`nvarchar`|Adresse réseau à laquelle cette instance a envoyé le message. Notez que celle-ci peut différer de la destination finale du message.|42|non|  
|TargetUserName|`nvarchar`|Nom du service initiateur du message.|39|non|  
|TransactionID|`bigint`|ID affecté à la transaction par le système.|4|non|  
  
  
