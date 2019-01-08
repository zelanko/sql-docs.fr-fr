---
title: Background Job Error, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Background Job Error event class
ms.assetid: 9e6d2a0e-919d-4fe2-a306-b20b8d41c197
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b95db663ea56f8dd43ed1091169f8117292033c4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52797091"
---
# <a name="background-job-error-event-class"></a>Background Job Error (classe d'événements)
  La classe d’événements **Background Job Error** intervient quand un travail en arrière-plan s’est arrêté anormalement. Cette condition peut nécessiter l'intervention d'un administrateur système.  
  
## <a name="background-job-error-event-class-data-columns"></a>Colonnes de la classe d'événements Background Job Error  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**Int**|ID de la base de données spécifiée par le travail. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|**nvarchar**|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|**Erreur**|**Int**|Numéro d’erreur de la dernière tentative (**EventSubClass** 1 uniquement).|31|Oui|  
|**EventClass**|**Int**|Type d’événement = 193.|27|Non|  
|**EventSequence**|**Int**|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**EventSubClass**|**Int**|Type de sous-classe d'événements.<br /><br /> 1 = Travail en arrière-plan abandonné après la défaillance.<br /><br /> 2 = Travail en arrière-plan supprimé - la fille d'attente est pleine.<br /><br /> 3 = Le travail en arrière-plan a retourné une erreur.|21|Oui|  
|**IndexID**|**Int**|ID de l'index de l'objet affecté par l'événement. Pour déterminer l’ID d’index d’un objet, utilisez la colonne **indid** de la table système **sysindexes** .|24|Oui|  
|**IntegerData**|**Int**|Nombre de tentatives effectuées par le travail (**EventSubClass** 1 uniquement).|25|Oui|  
|**IntegerData2**|**Int**|Numéro de séquence du travail.|55|Oui|  
|**ObjectID**|**Int**|ID affecté à l'objet par le système.|22|Oui|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|64|Oui|  
|**Severity**|**Int**|Niveau de gravité de l’erreur lors de la dernière tentative (**EventSubClass** 1 uniquement).|20|Oui|  
|**StartTime**|**datetime**|Heure à laquelle le travail a été créé.|14|Oui|  
|**État**|**Int**|État de l’erreur lors de la dernière tentative (**EventSubClass** 1 uniquement).|30|Oui|  
|**TextData**|**ntext**|Description texte de la valeur de la sous-classe d'événements.|1|Oui|  
|**Type**|**Int**|Type du travail.|57|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Classe d'événements Auto Stats](auto-stats-event-class.md)  
  
  
