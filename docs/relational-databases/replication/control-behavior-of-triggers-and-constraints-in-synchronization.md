---
title: "Contrôler le comportement des déclencheurs et des contraintes de la synchronisation | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 24825a3c9c016588b4ac3d1a9c8fa29741e609b3
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="control-behavior-of-triggers-and-constraints-in-synchronization"></a>Contrôler le comportement des déclencheurs et des contraintes de la synchronisation
  Au cours de la synchronisation, les agents de réplication exécutent des instructions [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md), [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md) et [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md) sur les tables répliquées, ce qui peut entraîner l’exécution de déclencheurs de langage de manipulation de données (DML) sur ces tables. Dans certains cas, vous pouvez avoir besoin d'empêcher l'exécution de ces déclencheurs ou l'application de contraintes au cours de la synchronisation. Ce comportement dépend de la manière dont le déclencheur ou la contrainte sont créés.  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>Pour empêcher l'exécution de déclencheurs pendant la synchronisation  
  
1.  Quand vous créez un déclencheur, spécifiez l’option NOT FOR REPLICATION de [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
2.  Pour un déclencheur existant, spécifiez l’option NOT FOR REPLICATION d’[ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md).  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>Pour empêcher l'application de contraintes pendant la synchronisation  
  
1.  Quand vous créez une contrainte CHECK ou FOREIGN KEY, spécifiez l’option CHECK NOT FOR REPLICATION dans la définition de contrainte de [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des tables &#40;moteur de base de données&#41;](../../relational-databases/tables/create-tables-database-engine.md)  
  
  
