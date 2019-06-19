---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 419b45c688f755d6e5f7cf86154ce6cc527fc6ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048241"
---
# <a name="mssqlserver10509"></a>MSSQLSERVER_10509
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10509|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_INVALID_STMT|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car l’instruction spécifiée par **@stmt** ou **@statement_start_offset** contient une erreur de syntaxe ou n’est pas éligible pour le repère de plan. Fournissez une seule instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] valide ou une position de départ de l'instruction valide dans le lot. Pour obtenir une position de départ valide, interrogez la colonne statement_start_offset de la fonction de gestion dynamique sys.dm_exec_query_stats.|  
  
## <a name="explanation"></a>Explication  
L’instruction spécifiée par **@stmt** ou **@statement_start_offset** contient une erreur de syntaxe ou n’est pas éligible pour une utilisation dans un repère de plan.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Fournissez une seule instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] valide ou une position de départ de l'instruction valide dans le lot. Pour obtenir une position de départ valide, interrogez la colonne statement_start_offset de la fonction de gestion dynamique sys.dm_exec_query_stats.  
  
## <a name="see-also"></a>Voir aussi  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
