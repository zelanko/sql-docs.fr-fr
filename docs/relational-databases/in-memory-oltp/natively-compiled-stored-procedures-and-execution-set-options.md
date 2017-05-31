---
title: "Procédures stockées compilées en mode natif et options SET d’exécution | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 02a1683278d0f64ac41893a9cdb8e97a634002b5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>Procédures stockées compilées en mode natif et options SET d'exécution
  Les options de session sont fixes dans les blocs Atomic. L'exécution d'une procédure stockée n'est pas affectée par les options SET d'une session. Toutefois, certaines options SET, telles que SET NOEXEC et SET SHOWPLAN_XML, empêchent l'exécution des procédures stockées (y compris des procédures stockées compilées en mode natif).  
  
 Lorsqu'une procédure stockée compilée en mode natif est exécutée avec une option STATISTICS activée, les statistiques sont collectées pour la procédure dans son ensemble, et non par instruction. Pour plus d’informations, consultez [SET STATISTICS IO &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-io-transact-sql.md), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-profile-transact-sql.md), [SET STATISTICS TIME &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-time-transact-sql.md) et [SET STATISTICS XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-xml-transact-sql.md). Pour obtenir les statistiques d'exécution au niveau d'une instruction dans des procédures stockées compilées en mode natif, utilisez une session d'événements étendus dans l'événement sp_statement_completed, qui commence à l'issue de chaque requête individuelle exécutée dans les procédures stockées. Pour plus d’informations sur la création de sessions d’événements étendus, consultez [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md).  
  
 **SHOWPLAN_XML** est pris en charge pour les procédures stockées compilées en mode natif. **SHOWPLAN_ALL** et **SHOWPLAN_TEXT** ne sont pas pris en charge avec les procédures stockées compilées en mode natif.  
  
 **SET FMTONLY** n'est pas prise en charge dans les procédures stockées compilées en mode natif. Utilisez plutôt [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
