---
title: "Background Job Error, classe d’événements | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Background Job Error event class
ms.assetid: 9e6d2a0e-919d-4fe2-a306-b20b8d41c197
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bae056c3dd2b646bf7e4ec88e7c5d2e8d11bc7f8
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="background-job-error-event-class"></a>Background Job Error (classe d'événements)
  La classe d’événements **Background Job Error** intervient quand un travail en arrière-plan s’est arrêté anormalement. Cette condition peut nécessiter l'intervention d'un administrateur système.  
  
## <a name="background-job-error-event-class-data-columns"></a>Colonnes de la classe d'événements Background Job Error  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID de la base de données spécifiée par le travail. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|**nvarchar**|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|**Erreur**|**int**|Numéro d’erreur de la dernière tentative (**EventSubClass** 1 uniquement).|31|Oui|  
|**EventClass**|**int**|Type d’événement = 193.|27|Non|  
|**EventSequence**|**int**|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**EventSubClass**|**int**|Type de sous-classe d'événements.<br /><br /> 1 = Travail en arrière-plan abandonné après la défaillance.<br /><br /> 2 = Travail en arrière-plan supprimé - la fille d'attente est pleine.<br /><br /> 3 = Le travail en arrière-plan a retourné une erreur.|21|Oui|  
|**IndexID**|**int**|ID de l'index de l'objet affecté par l'événement. Pour déterminer l’ID d’index d’un objet, utilisez la colonne **indid** de la table système **sysindexes** .|24|Oui|  
|**IntegerData**|**int**|Nombre de tentatives effectuées par le travail (**EventSubClass** 1 uniquement).|25|Oui|  
|**IntegerData2**|**int**|Numéro de séquence du travail.|55|Oui|  
|**ObjectID**|**int**|ID affecté à l'objet par le système.|22|Oui|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|64|Oui|  
|**Severity**|**int**|Niveau de gravité de l’erreur lors de la dernière tentative (**EventSubClass** 1 uniquement).|20|Oui|  
|**StartTime**|**datetime**|Heure à laquelle le travail a été créé.|14|Oui|  
|**État**|**int**|État de l’erreur lors de la dernière tentative (**EventSubClass** 1 uniquement).|30|Oui|  
|**TextData**|**ntext**|Description texte de la valeur de la sous-classe d'événements.|1|Oui|  
|**Type**|**int**|Type du travail.|57|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Classe d'événements Auto Stats](../../relational-databases/event-classes/auto-stats-event-class.md)  
  
  
