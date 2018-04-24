---
title: Broker:Activation, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: event-classes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 469e626013bb764ea61e954c03857b37ea74ebd5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="brokeractivation-event-class"></a>Broker:Activation, classe d'événement
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement **Broker:Activation** quand un moniteur de file d’attente démarre une procédure stockée d’activation, envoie une notification QUEUE_ACTIVATION, ou quand une procédure stockée d’activation démarrée par un moniteur de file d’attente se termine.  
  
## <a name="brokeractivation-event-class-data-columns"></a>Colonnes de données de la classe d'événement Broker:Activation  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ClientProcessID**|**Int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|**Int**|ID de la base de données spécifiée par l’instruction USE *base_de_données* ou celui de la base de données par défaut si aucune instruction USE *base_de_données*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**EventClass**|**Int**|Type de classe d'événements capturée. Toujours **163** pour **Broker:Activation**.|27|non|  
|**EventSequence**|**Int**|Numéro de séquence de cet événement.|51|non|  
|**EventSubClass**|**nvarchar**|Action spécifique que cet événement signale. Une des valeurs suivantes :<br /><br /> **démarré**:   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a démarré une procédure stockée d’activation.<br /><br /> **terminé**:  la procédure stockée d’activation s’est terminée normalement.<br /><br /> **abandon**:   la procédure stockée d’activation a été interrompue suite à une erreur.|21|non|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IntegerData**|**Int**|Nombre de tâches actives dans cette file d'attente.|25|non|  
|**IsSystem**|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|non|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**ObjectID**|**Int**|File d'attente associée à cet événement.|22|non|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|**SPID**|**Int**|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|**StartTime**|**datetime**|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**TransactionID**|**bigint**|ID affecté à la transaction par le système.|4|non|  
  
  
