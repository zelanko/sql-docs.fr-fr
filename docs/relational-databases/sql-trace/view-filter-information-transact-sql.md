---
description: Afficher des informations de filtrage (Transact-SQL)
title: Afficher des informations de filtrage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2876e99401b050e165713da583192fbc7fa0c4be
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88324980"
---
# <a name="view-filter-information-transact-sql"></a>Afficher des informations de filtrage (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette rubrique explique comment utiliser les fonctions intégrées pour afficher les informations de filtrage de traces.  
  
### <a name="to-view-filter-information"></a>Pour afficher les informations de filtrage  
  
1.  Exécutez **fn_trace_getfilterinfo** en spécifiant l’ID de la trace sur laquelle vous souhaitez des informations de filtrage. Cette fonction renvoie une table de filtres, les colonnes auxquelles les filtres sont appliqués et les valeurs auxquelles les filtres sont appliqués.  
  
     Appelez la fonction comme suit :  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de SQL Server Profiler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
