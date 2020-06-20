---
title: Assembly Load, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Assembly Load event class
ms.assetid: cfb0b69d-4ce0-4067-a3df-d82775e57886
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b1a628035fa7469441c670e20dbbf98cdbf8f8a7
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937310"
---
# <a name="assembly-load-event-class"></a>Classe d'événements Assembly Load
  La classe d'événements **Assembly Load** se produit lorsqu'une demande de chargement d'un assembly est exécutée.  
  
 Pour contrôler des chargements d'assemblys, incluez la classe d'événements **Assembly Load** dans des traces. Ceci peut être utile lors du dépannage d'une requête qui utilise CLR, lors du dépannage d'un serveur à exécution lente qui exécute des requêtes CLR, ou lors de la surveillance d'un serveur pour réunir des informations sur les utilisateurs, les bases de données, les opérations réussies ou d'autres informations sur les chargements d'assemblys.  
  
## <a name="assembly-load-event-class-data-columns"></a>Colonnes de données de la classe d'événements Assembly Load  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application qui a demandé le chargement.|10|Yes|  
|**ClientProcessID**|**int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Yes|  
|**DatabaseID**|**int**|ID de la base de données spécifiée par l'instruction de base de données USE ou celui de la base de données par défaut si aucune instruction de base de données USE n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Yes|  
|**DatabaseName**|**nvarchar**|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Yes|  
|**EventSequence**|**int**|Séquence d'un événement donné au sein de la demande.|51|No|  
|**GroupID**|**int**|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Yes|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel le client est exécuté. La colonne de données est remplie si le client fournit le nom de l'hôte. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Yes|  
|**LoginName**|**nvarchar**|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Yes|  
|**LoginSID**|**image**|Identificateur de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l’affichage catalogue **sys.server_principals** . Chaque connexion possède un SID unique au niveau du serveur.|41|Yes|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Yes|  
|**NTUserName**|**nvarchar**|Nom d'utilisateur Windows.|6|Yes|  
|**Arguments**|**int**|ID d'assembly.|22|Oui|  
|**ObjectName**|**nvarchar**|Nom complet de l'assembly.|34|Yes|  
|**Identifi**|**int**|ID de la demande contenant l'instruction.|49|Yes|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en utilisant Login1 et que vous exécutez une instruction sous le nom de Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et Windows.|64|Yes|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Yes|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Yes|  
|**Succès**|**int**|Indique si le chargement de l'assembly a réussi (1) ou échoué (0).|23|Oui|  
|**TextData**|**ntext**|« Chargement d'assembly réussi » si le chargement a réussi ; sinon  « Échec du chargement d'assembly ».|1|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../relational-databases/extended-events/extended-events.md)   
 [Assemblys &#40;moteur de base de données&#41;](../relational-databases/clr-integration/assemblies-database-engine.md)  
  
  
