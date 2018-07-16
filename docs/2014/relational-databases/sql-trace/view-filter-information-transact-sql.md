---
title: Afficher des informations de filtrage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7bf6a65f047141be467aee5c8c4eda63887a78bb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327669"
---
# <a name="view-filter-information-transact-sql"></a>Afficher des informations de filtrage (Transact-SQL)
  Cette rubrique explique comment utiliser les fonctions intégrées pour afficher les informations de filtrage de traces.  
  
### <a name="to-view-filter-information"></a>Pour afficher les informations de filtrage  
  
1.  Exécutez **fn_trace_getfilterinfo** en spécifiant l’ID de la trace sur laquelle vous souhaitez des informations de filtrage. Cette fonction renvoie une table de filtres, les colonnes auxquelles les filtres sont appliqués et les valeurs auxquelles les filtres sont appliqués.  
  
     Appelez la fonction comme suit :  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)   
 [Procédures stockées système &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Procédures stockées de SQL Server Profiler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
