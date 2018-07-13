---
title: Procédures stockées compilées en mode natif et options SET d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
caps.latest.revision: 5
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 274f389a1d15c998177d5ab7895122de3200dec4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201469"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>Procédures stockées compilées en mode natif et options SET d'exécution
  Les options de session sont fixes dans les blocs Atomic. L'exécution d'une procédure stockée n'est pas affectée par les options SET d'une session. Toutefois, certaines options SET, telles que SET NOEXEC et SET SHOWPLAN_XML, empêchent l'exécution des procédures stockées (y compris des procédures stockées compilées en mode natif).  
  
 Lorsqu'une procédure stockée compilée en mode natif est exécutée avec une option STATISTICS activée, les statistiques sont collectées pour la procédure dans son ensemble, et non par instruction. Pour plus d’informations, consultez [SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql), [SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql) et [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql). Pour obtenir les statistiques d'exécution au niveau d'une instruction dans des procédures stockées compilées en mode natif, utilisez une session d'événements étendus dans l'événement sp_statement_completed, qui commence à l'issue de chaque requête individuelle exécutée dans les procédures stockées. Pour plus d’informations sur la création de sessions d’événements étendus, consultez [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).  
  
 `SHOWPLAN_XML` est pris en charge pour les procédures stockées compilées en mode natif. `SHOWPLAN_ALL` et `SHOWPLAN_TEXT` ne sont pas prises en charge dans les procédures stockées compilées en mode natif.  
  
 `SET FMTONLY` n'est pas prise en charge dans les procédures stockées compilées en mode natif. Utilisez plutôt [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)  
  
  
