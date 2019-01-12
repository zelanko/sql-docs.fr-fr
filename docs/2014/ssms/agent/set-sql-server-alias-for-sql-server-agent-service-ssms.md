---
title: Définir un filtre de trace (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6e3ecc4b125d226fc2cdf6dbe241e0ce017eae6
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54126689"
---
# <a name="set-a-trace-filter-transact-sql"></a>Définir un filtre de trace (Transact-SQL)
  Cette rubrique explique comment utiliser des procédures stockées pour créer un filtre qui n'extrait que les informations requises lors d'un événement en cours de traçage.  
  
### <a name="to-set-a-trace-filter"></a>Pour définir un filtre de trace  
  
1.  Si la trace est déjà en cours d’exécution, exécutez **sp_trace_setstatus** en spécifiant **@status = 0** pour l’arrêter.  
  
2.  Exécutez **sp_trace_setfilter** pour configurer le type d’informations extraites pour l’événement dont vous voulez suivre la trace.  
  
> [!IMPORTANT]
>  Contrairement aux procédures stockées standard, les paramètres de tous les [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] des procédures stockées (<strong>sp_trace_*xx*</strong>) sont strictement typés et ne prennent pas en charge la conversion automatique. Si ces paramètres ne sont pas appelés avec des types de données appropriés pour les paramètres d'entrée tels qu'ils sont spécifiés dans la description de l'argument, la procédure stockée renvoie une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer une trace](../../relational-databases/sql-trace/filter-a-trace.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [Procédures stockées système &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Procédures stockées de SQL Server Profiler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
