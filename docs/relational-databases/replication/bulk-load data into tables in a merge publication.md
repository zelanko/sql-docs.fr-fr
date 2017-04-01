---
title: "Charger en masse des donn&#233;es dans les tables d&#39;une publication de fusion (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "chargement en masse [réplication SQL Server]"
  - "chargement en masse de la réplications de fusion [réplication SQL Server]"
  - "sp_addtabletocontents"
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Charger en masse des donn&#233;es dans les tables d&#39;une publication de fusion (programmation Transact-SQL de la r&#233;plication)
  Lorsque les données sont chargées dans les tables à l’aide de la [utilitaire bcp](../../tools/bcp-utility.md) ou le [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) commande, par défaut, les déclencheurs de réplication de fusion qui conservent les données de suivi dans le [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) (table système) ne sont pas déclenchés. Vous avez le choix entre forcer les déclencheurs de réplication de fusion à se déclencher au chargement des données et insérer par programmation les métadonnées de réplication générées après l'opération de copie en bloc à l'aide de procédures stockées de réplication.  
  
### Pour charger en masse les données dans les tables publiées par la réplication de fusion à l'aide de l'utilitaire bcp  
  
1.  Sur le serveur de publication ou sur l'Abonné, exécutez l' [bcp Utility](../../tools/bcp-utility.md) ou [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) pour insérer des données dans une table a publié à l'aide de la réplication de fusion.  
  
2.  Utilisez l'une des méthodes suivantes pour garantir que les métadonnées de réplication sont générées pour les données insérées.  
  
    -   Exécutez la copie en bloc à l'aide de l'option FIRE_TRIGGERS.  
  
    -   Sur la base de données dans laquelle les données ont été insérées, exécutez [sp_addtabletocontents & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql.md). Spécifiez le nom de la table dans laquelle les données ont été insérées pour **@table_name**.  
  
  