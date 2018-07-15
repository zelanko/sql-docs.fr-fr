---
title: Classe d’événements assembly Load | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
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
- Assembly Load event class
ms.assetid: cfb0b69d-4ce0-4067-a3df-d82775e57886
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1464f59c227577bc0c81f5f89ac84430c5b59497
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207619"
---
# <a name="assembly-load-event-class"></a>Classe d'événements Assembly Load
  La classe d'événements **Assembly Load** se produit lorsqu'une demande de chargement d'un assembly est exécutée.  
  
 Pour contrôler des chargements d'assemblys, incluez la classe d'événements **Assembly Load** dans des traces. Ceci peut être utile lors du dépannage d'une requête qui utilise CLR, lors du dépannage d'un serveur à exécution lente qui exécute des requêtes CLR, ou lors de la surveillance d'un serveur pour réunir des informations sur les utilisateurs, les bases de données, les opérations réussies ou d'autres informations sur les chargements d'assemblys.  
  
## <a name="assembly-load-event-class-data-columns"></a>Colonnes de données de la classe d'événements Assembly Load  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application qui a demandé le chargement.|10|Oui|  
|**ClientProcessID**|**Int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Oui|  
|**DatabaseID**|**Int**|ID de la base de données spécifiée par l'instruction de base de données USE ou celui de la base de données par défaut si aucune instruction de base de données USE n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|**nvarchar**|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|**EventSequence**|**Int**|Séquence d'un événement donné au sein de la demande.|51|non|  
|**GroupID**|**Int**|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel le client est exécuté. La colonne de données est remplie si le client fournit le nom de l'hôte. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**LoginName**|**nvarchar**|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|**LoginSID**|**image**|Identificateur de sécurité (SID) de l'utilisateur connecté. Vous trouverez ces informations dans l’affichage catalogue **sys.server_principals** . Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom d'utilisateur Windows.|6|Oui|  
|**ObjectID**|**Int**|ID d'assembly.|22|Oui|  
|**ObjectName**|**nvarchar**|Nom complet de l'assembly.|34|Oui|  
|**RequestID**|**Int**|ID de la demande contenant l'instruction.|49|Oui|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tracée.|26|non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**Int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**Réussi**|**Int**|Indique si le chargement de l'assembly a réussi (1) ou échoué (0).|23|Oui|  
|**TextData**|**ntext**|« Chargement d'assembly réussi » si le chargement a réussi ; sinon  « Échec du chargement d'assembly ».| 1|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../relational-databases/extended-events/extended-events.md)   
 [Assemblys &#40;moteur de base de données&#41;](../relational-databases/clr-integration/assemblies-database-engine.md)  
  
  
