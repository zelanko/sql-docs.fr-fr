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
ms.openlocfilehash: 47d797c84a05f50da026280f6e197f965d804426
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067507"
---
# <a name="set-a-trace-filter-transact-sql"></a>Définir un filtre de trace (Transact-SQL)
  Cette rubrique explique comment utiliser des procédures stockées pour créer un filtre qui n'extrait que les informations requises lors d'un événement en cours de traçage.  
  
### <a name="to-set-a-trace-filter"></a>Pour définir un filtre de trace  
  
1.  Si la trace est déjà en cours d’exécution, exécutez **sp_trace_setstatus** en spécifiant **\@status = 0**  pour l’arrêter.  
  
2.  Exécutez **sp_trace_setfilter** pour configurer le type d’informations extraites pour l’événement dont vous voulez suivre la trace.  
  
> [!IMPORTANT]
>  Contrairement aux procédures stockées standard, les paramètres de toutes les procédures stockées [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] (<strong>sp_trace_*xx*</strong>) sont strictement typés et ne prennent pas en charge la conversion automatique des types de données. Si ces paramètres ne sont pas appelés avec des types de données appropriés pour les paramètres d'entrée tels qu'ils sont spécifiés dans la description de l'argument, la procédure stockée renvoie une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer une trace](../../relational-databases/sql-trace/filter-a-trace.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [Procédures stockées système &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Procédures stockées de SQL Server Profiler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
