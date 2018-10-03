---
title: CursorPrepare, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- CursorPrepare event class
ms.assetid: 990e50fb-b3ee-4366-8613-2c40d4a456f7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c40d64bceec4c05929b808a85908b882705dbbe6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145389"
---
# <a name="cursorprepare-event-class"></a>CursorPrepare (classe d'événements)
  La classe d’événements **CursorPrepare** décrit les événements de préparation des curseurs qui se produisent dans les curseurs d’API. Les événements de préparation de curseurs se produisent lorsque [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] compile une instruction SELECT associée à un curseur dans un plan d’exécution, mais ne crée pas le curseur.  
  
 Incluez la classe d’événements **CursorPrepare** dans les traces qui enregistrent les performances des curseurs. Lorsque la classe d’événements **CursorPrepare** est incluse dans une trace, la charge générée varie selon la fréquence d’utilisation des curseurs sur la base de données pendant la trace. Si les curseurs sont fortement utilisés, la trace peut dégrader notablement les performances.  
  
## <a name="cursorprepare-event-class-data-columns"></a>Colonnes de données de la classe d'événements CursorPrepare  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|**ClientProcessID**|**Int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|**Int**|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|**nvarchar**|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|**EventClass**|**Int**|Type d’événement enregistré = 70|27|non|  
|**EventSequence**|**Int**|Séquence de la classe d’événements **CursorPrepare** dans un traitement.|51|non|  
|**GroupID**|**Int**|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|**Handle**|**Int**|Descripteur de la classe d'événements.|33|Oui|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IsSystem**|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**LoginName**|**nvarchar**|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification Windows sous la forme DOMAINE\Nomutilisateur).|11|Oui|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l’affichage catalogue **sys.server_principals** . Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|non|  
|**NTUserName**|**nvarchar**|Nom d'utilisateur Windows.|6|Oui|  
|**RequestID**|**Int**|Identification de la demande qui a préparé le curseur.|49|Oui|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**Int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si disponible.|14|Oui|  
|**TransactionID**|**bigint**|ID affecté par le système à la transaction.|4|Oui|  
|**XactSequence**|**bigint**|Jeton utilisé pour décrire la transaction en cours.|50|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Curseurs](../cursors.md)  
  
  
