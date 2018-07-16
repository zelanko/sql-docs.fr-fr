---
title: Broker:Message Classify, classe d’événements | Microsoft Docs
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
- Broker:Message Classify event class
ms.assetid: e51f3351-1239-4c41-b87c-1dd86968e027
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6097a06f1a239dc6e3af181ba983c5575567cbbc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225610"
---
# <a name="brokermessage-classify-event-class"></a>Broker:Message Classify, classe d'événements
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement **Broker:Message Classify** quand Service Broker détermine le routage d’un message.  
  
## <a name="brokermessage-classify-event-class-data-columns"></a>Colonnes de données de la classe d'événements Broker:Message Classify  
  
|Colonne de données|Type de données|Description|Numéro de colonne|Filtrable|  
|-----------------|---------------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|**ClientProcessID**|**Int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|**Int**|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**EventClass**|**Int**|Type de classe d'événements capturée. Renvoie toujours **141** pour **Broker:Message Classify**.|27|non|  
|**EventSequence**|**Int**|Numéro de séquence de cet événement.|51|non|  
|**EventSubClass**|**nvarchar**|Type de sous-classe d’événements, qui fournit des informations complémentaires concernant chaque classe d’événements. Cette colonne peut contenir les valeurs suivantes :<br /><br /> **Local**: la route choisie possède l’adresse LOCAL.<br /><br /> **À distance**: la route choisie possède une adresse autre que LOCAL.<br /><br /> **Retardé**: le message est retardé, soit parce que le transfert est désactivé, car il n’existe aucun itinéraire correspondant présent.|21|Oui|  
|**FileName**|**nvarchar**|Nom du service vers lequel le message est dirigé.|36|non|  
|**GUID**|**uniqueidentifier**|ID de conversation du dialogue. Cet identifiant est transmis en tant que partie intégrante du message et est partagé par les deux intervenants de la conversation.|54|non|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IsSystem**|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|non|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**OwnerName**|**nvarchar**|Identificateur de Service Broker vers lequel le message est dirigé.|37|non|  
|**RoleName**|**nvarchar**|Indique si le message a été reçu du réseau ou provient de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|38|non|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|**SPID**|**Int**|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|**Start Time**|**datetime**|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**TargetUserName**|**nvarchar**|Adresse réseau du Service Broker du saut suivant.|39|non|  
|**TransactionID**|**bigint**|ID affecté à la transaction par le système.|4|non|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
