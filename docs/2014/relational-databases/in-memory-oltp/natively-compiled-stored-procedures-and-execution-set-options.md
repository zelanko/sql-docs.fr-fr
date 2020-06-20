---
title: Procédures stockées compilées en mode natif et options SET d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 264a2b3ab1e6f3f0bda97bfe89a4438aa641577d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025845"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>Procédures stockées compilées en mode natif et options SET d'exécution
  Les options de session sont fixes dans les blocs Atomic. L'exécution d'une procédure stockée n'est pas affectée par les options SET d'une session. Toutefois, certaines options SET, telles que SET NOEXEC et SET SHOWPLAN_XML, empêchent l'exécution des procédures stockées (y compris des procédures stockées compilées en mode natif).  
  
 Lorsqu'une procédure stockée compilée en mode natif est exécutée avec une option STATISTICS activée, les statistiques sont collectées pour la procédure dans son ensemble, et non par instruction. Pour plus d’informations, consultez [SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql), [SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql) et [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql). Pour obtenir les statistiques d'exécution au niveau d'une instruction dans des procédures stockées compilées en mode natif, utilisez une session d'événements étendus dans l'événement sp_statement_completed, qui commence à l'issue de chaque requête individuelle exécutée dans les procédures stockées. Pour plus d’informations sur la création de sessions d’événements étendus, consultez [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).  
  
 `SHOWPLAN_XML` est pris en charge pour les procédures stockées compilées en mode natif. `SHOWPLAN_ALL` et `SHOWPLAN_TEXT` ne sont pas prises en charge dans les procédures stockées compilées en mode natif.  
  
 `SET FMTONLY` n'est pas prise en charge dans les procédures stockées compilées en mode natif. Utilisez plutôt [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)  
  
  
