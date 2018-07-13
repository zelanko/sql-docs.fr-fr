---
title: Classe d’événements Broker:Message Undeliverable | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
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
- Broker:Message Drop event class
- Broker:Message Undeliverable event class
ms.assetid: f532b7c9-ca34-4bac-8dc3-53f9895fd6af
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 75838c8eb38e21eb82f6a57278ebe13310a3f53a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37168670"
---
# <a name="brokermessage-undeliverable-event-class"></a>Classe d’événements Broker:Message Undeliverable
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement **Broker:Message Undeliverable** si le Service Broker ne peut pas conserver un message reçu censé avoir été livré à un service de cette instance. Dans le cas de messages censés avoir été transmis, consultez [Classe d’événements Broker:Forwarded Message Dropped](broker-forwarded-message-dropped-event-class.md).  
  
## <a name="brokermessage-undeliverable-event-class-data-columns"></a>Colonnes de données de la classe d’événements Broker:Message Undeliverable  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**Application Name**|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|**BigintData1**|`bigint`|Numéro de séquence du message non remis.|52|non|  
|**BigintData2**|`bigint`|Numéro de séquence du dernier message ayant été pris en considération.|53|non|  
|**ClientProcessID**|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|`int`|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**Erreur**|`int`|ID du message dans **sys.messages** destiné au texte de l’événement.|31|non|  
|**EventClass**|`int`|Type de classe d'événements capturée. Renvoie toujours **160** pour **Broker:MessageUndeliverable**.|27|non|  
|**EventSequence**|`int`|Numéro de séquence de cet événement.|51|non|  
|**EventSubClass**|`nvarchar`|Indique si le message non remis correspondait à un message en séquence. Prend l'une des deux valeurs :<br /><br /> **Message en séquence**. Le message non remis correspondait à un message en séquence.<br /><br /> **Message sans séquence**. Le message non remis ne correspondait pas à un message en séquence.|21|Oui|  
|**GUID**|`uniqueidentifier`|ID de la conversation à laquelle le message non remis appartient. Cet identifiant est transmis en tant que partie intégrante du message et est partagé par les deux intervenants de la conversation.|54|non|  
|**HostName**|`nvarchar`|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IntegerData**|`int`|Numéro de fragment du message non remis.|25|non|  
|**IntegerData2**|`int`|Numéro du fragment de message que le message non remis était en train de prendre en compte.|55|non|  
|**IsSystem**|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|non|  
|**LoginName**|`nvarchar`|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion Windows au format DOMAINE\nom_utilisateur).|11|non|  
|**LoginSid**|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|`nvarchar`|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**ObjectName**|`nvarchar`|Descripteur de conversation du dialogue.|34|non|  
|**RoleName**|`nvarchar`|Rôle du descripteur de conversation. Il peut prendre la valeur **initiator** ou la valeur **target**.|38|non|  
|**ServerName**|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|**Severity**|`int`|Numéro de gravité du texte de l'événement.|29|non|  
|**SPID**|`int`|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|**StartTime**|`datetime`|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**État**|`int`|Indique l'emplacement dans le code source [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui a produit l'événement. Chaque emplacement susceptible de générer cet événement possède un code d'état spécifique. Un spécialiste de l'assistance technique Microsoft peut se servir de ce code d'état afin de déterminer où l'événement s'est produit.|30|non|  
|**TextData**|`ntext`|Raison pour laquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas pu remettre le message.| 1|Oui|  
|**TransactionID**|`bigint`|ID affecté à la transaction par le système.|4|non|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
