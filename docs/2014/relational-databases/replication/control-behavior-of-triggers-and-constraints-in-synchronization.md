---
title: Contrôler le comportement des déclencheurs et des contraintes pendant la synchronisation (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 26d9a2431b91c1dc081345a06e7fe5a7533cbaa2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721519"
---
# <a name="control-the-behavior-of-triggers-and-constraints-during-synchronization-replication-transact-sql-programming"></a>Contrôler le comportement de déclencheurs et de contraintes au cours de la synchronisation (programmation Transact-SQL de la réplication)
  Au cours de la synchronisation, les agents de réplication exécutent des instructions [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) et [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) sur les tables répliquées, ce qui peut entraîner l’exécution de déclencheurs de langage de manipulation de données (DML) sur ces tables. Dans certains cas, vous pouvez avoir besoin d'empêcher l'exécution de ces déclencheurs ou l'application de contraintes au cours de la synchronisation. Ce comportement dépend de la manière dont le déclencheur ou la contrainte sont créés.  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>Pour empêcher l'exécution de déclencheurs pendant la synchronisation  
  
1.  Quand vous créez un déclencheur, spécifiez l’option NOT FOR REPLICATION de [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
2.  Pour un déclencheur existant, spécifiez l’option NOT FOR REPLICATION d’[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql).  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>Pour empêcher l'application de contraintes pendant la synchronisation  
  
1.  Quand vous créez une contrainte CHECK ou FOREIGN KEY, spécifiez l’option CHECK NOT FOR REPLICATION dans la définition de contrainte de [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des tables &#40;moteur de base de données&#41;](../tables/create-tables-database-engine.md)  
  
  
