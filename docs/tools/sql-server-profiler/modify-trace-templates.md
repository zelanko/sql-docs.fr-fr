---
title: "Modifier des mod&#232;les de trace | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles [SQL Server], SQL Server Profiler"
  - "profileur [SQL Server Profiler], modèles"
  - "modèles de trace [SQL Server]"
  - "modification des modèles de trace"
  - "SQL Server Profiler, modèles"
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Modifier des mod&#232;les de trace
  Vous pouvez modifier les modèles enregistrés dans un fichier sur l'ordinateur local sur lequel le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] est en cours d'exécution. Vous pouvez également modifier les modèles dérivés de ces fichiers. Quand vous modifiez des modèles existants, vous modifiez leurs propriétés, telles que les classes d’événements et les colonnes de données, en suivant l’ordre de la définition initiale des propriétés, sous l’onglet **Sélection des événements** de la boîte de dialogue **Propriétés de la trace**. Les classes d'événements et les colonnes de données peuvent être ajoutées ou supprimées, et les filtres peuvent être modifiés. Une fois le modèle modifié, un modèle spécifique à l'utilisateur est créé et le modèle système initial demeure intact. Pour plus d’informations, consultez [Enregistrer des traces et des modèles de trace](../../tools/sql-server-profiler/save-traces-and-trace-templates.md).  
  
 Il se peut que vous deviez dériver un modèle d'un fichier de trace existant si vous ne vous rappelez pas (ou si n'avez pas effectué d'enregistrement) du modèle d'origine utilisé pour créer la trace, ou bien si vous voulez exécuter la même trace à une date ultérieure. Lorsque vous utilisez des traces existantes, vous pouvez afficher les propriétés, mais pas les modifier. Pour modifier les propriétés, arrêtez ou suspendez la trace. Pour plus d’informations, consultez [Dériver un modèle à partir d’un fichier de trace ou d’une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) et [Dériver un modèle à partir d’une trace en cours d’exécution &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md).  
  
 **Pour créer un modèle de trace**  
  
 [Créer un modèle de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
 **Pour exécuter une trace à partir d'un modèle de trace**  
  
 [Créer une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 **Pour modifier un modèle de trace**  
  
 [Utilisation de SQL Server Profiler](../../tools/sql-server-profiler/modify-a-trace-template-sql-server-profiler.md)  
  
 [Utilisation de Transact-SQL](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 **Pour ajouter ou supprimer des événements dans un modèle de trace ou un fichier de trace**  
  
 [Utilisation de SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Utilisation de Transact-SQL](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
## Voir aussi  
 [Démarrer une trace](../../tools/sql-server-profiler/start-a-trace.md)  
  
  