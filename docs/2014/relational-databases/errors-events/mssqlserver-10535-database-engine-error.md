---
title: MSSQLSERVER_10535 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ff4797fdd9d206ca459bc84facccfc588aafba00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143044"
---
# <a name="mssqlserver10535"></a>MSSQLSERVER_10535
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10535|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_NO_PLAN|  
|Texte du message|Impossible de créer le repère de plan '%.*ls', car aucun plan n'a été trouvé dans le cache du plan qui correspond au handle de plan spécifié. Indiquez un handle de plan mis en cache. Pour obtenir la liste des handles de plan mis en cache, interrogez la vue de gestion dynamique sys.dm_exec_query_stats.|  
  
## <a name="explanation"></a>Explication  
 Aucun plan correspondant au handle de plan spécifié n'a été trouvé dans le cache du plan.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Indiquez un handle de plan mis en cache. Pour obtenir la liste des handles de plan mis en cache, interrogez la vue de gestion dynamique sys.dm_exec_query_stats.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)  
  
  
