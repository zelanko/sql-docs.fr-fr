---
title: "Contr&#244;ler le comportement de d&#233;clencheurs et de contraintes au cours de la synchronisation (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/29/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "identités [réplication SQL Server]"
  - "contraintes [réplication SQL Server], réplication"
  - "déclencheurs [réplication SQL Server], réplication"
  - "déclencheurs [réplication SQL Server]"
  - "contraintes [réplication SQL Server]"
  - "NOT FOR REPLICATION, option"
  - "NFR, option"
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Contr&#244;ler le comportement de d&#233;clencheurs et de contraintes au cours de la synchronisation (programmation Transact-SQL de la r&#233;plication)
  Lors de la synchronisation, les agents de réplication exécutent [Insertion & #40 ; Transact-SQL & #41 ;](../../t-sql/statements/insert-transact-sql.md), [mise à jour & #40 ; Transact-SQL & #41 ;](../../t-sql/queries/update-transact-sql.md), et [Supprimer & #40 ; Transact-SQL & #41 ;](../../t-sql/statements/delete-transact-sql.md) instructions sur les tables répliquées, ce qui peuvent entraîner la manipulation de données les déclencheurs DML (langage) sur ces tables doit être exécuté. Dans certains cas, vous pouvez avoir besoin d'empêcher l'exécution de ces déclencheurs ou l'application de contraintes au cours de la synchronisation. Ce comportement dépend de la manière dont le déclencheur ou la contrainte sont créés.  
  
### Pour empêcher l'exécution de déclencheurs pendant la synchronisation  
  
1.  Lorsque vous créez un nouveau déclencheur, spécifiez l’option NOT FOR REPLICATION de [CREATE TRIGGER & #40 ; Transact-SQL & #41 ;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
2.  Pour un déclencheur existant, spécifiez l’option NOT FOR REPLICATION de [ALTER TRIGGER & #40 ; Transact-SQL & #41 ;](../../t-sql/statements/alter-trigger-transact-sql.md).  
  
### Pour empêcher l'application de contraintes pendant la synchronisation  
  
1.  Lorsque vous créez une nouvelle contrainte CHECK ou FOREIGN KEY, spécifiez l’option CHECK NOT FOR REPLICATION dans la définition de contrainte de [CREATE TABLE & #40 ; Transact-SQL & #41 ;](../../t-sql/statements/create-table-transact-sql.md).  
  
## Voir aussi  
 [Créez des Tables & #40 ; le moteur de base de données & #41 ;](../../relational-databases/tables/create-tables-database-engine.md)  
  
  