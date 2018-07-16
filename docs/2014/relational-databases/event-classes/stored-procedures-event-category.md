---
title: Procédures stockées, catégorie d’événements | Microsoft Docs
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
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10b7991639dc3e6e029d78db432764b2decd0bee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37307196"
---
# <a name="stored-procedures-event-category"></a>Catégorie d'événements Procédures stockées
  La catégorie d’événements **Procédures stockées** contient des événements de procédure stockée généraux.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Classe d'événements RPC:Completed](rpc-completed-event-class.md)|Indique qu'un appel de procédure distante (RPC) s'est terminé.|  
|[PreConnect:Completed, classe d’événements](preconnect-completed-event-class.md)|Indique quand la fonction classifieur de Resource Governor termine de s'exécuter.|  
|[PreConnect:Starting, classe d'événements](preconnect-starting-event-class.md)|Indique quand la fonction classifieur de Resource Governor commence à s'exécuter.|  
|[Classe d'événements RPC Output Parameter](rpc-output-parameter-event-class.md)|Trace les valeurs de paramètres de sortie des appels de procédure distante après l'exécution.|  
|[Classe d'événements RPC:Starting](rpc-starting-event-class.md)|Indique le démarrage d'un appel de procédure distante.|  
|[Classe d'événements SP:CacheHit](sp-cachehit-event-class.md)|Indique que la procédure stockée se trouve dans le cache.|  
|[Classe d'événements SP:CacheInsert](sp-cacheinsert-event-class.md)|Indique que la procédure stockée a été placée dans le cache.|  
|[Classe d'événements SP:CacheMiss](sp-cachemiss-event-class.md)|Indique que la procédure stockée est introuvable dans le cache.|  
|[Classe d'événements SP:CacheRemove](sp-cacheremove-event-class.md)|Indique que la procédure stockée a été supprimée du cache.|  
|[Classe d'événements SP:Completed](sp-completed-event-class.md)|Indique que l'exécution de la procédure stockée s'est terminée.|  
|[Classe d'événements SP:Recompile](sp-recompile-event-class.md)|Indique que la procédure stockée a été recompilée.|  
|[Classe d'événements SP:Starting](sp-starting-event-class.md)|Indique que l'exécution de la procédure stockée démarre.|  
|[Classe d'événements SP:StmtCompleted](sp-stmtcompleted-event-class.md)|Indique qu'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] d'une procédure stockée s'est terminée.|  
|[SP:StmtStarting, classe d’événements](sp-stmtstarting-event-class.md)|Indique qu'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] d'une procédure stockée a commencé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
