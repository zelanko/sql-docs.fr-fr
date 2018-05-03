---
title: Extraire un script d’une trace (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: df61dbca7fd73aa35b3b90ca0e682b3c9581d182
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>Extraire un script d'une trace (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment extraire des événements [!INCLUDE[tsql](../../includes/tsql-md.md)] d'un fichier ou d'une table de trace et comment les enregistrer sous forme de fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)] , dans le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>Pour extraire un script Transact-SQL à partir d'un fichier ou d'une table de trace  
  
1.  Ouvrez un fichier ou une table de trace contenant les événements [!INCLUDE[tsql](../../includes/tsql-md.md)] que vous voulez enregistrer sous forme de fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour plus d’informations, consultez [Ouvrir un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) ou l'Assistant Paramétrage du [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
2.  Dans le menu **Fichier**, pointez sur **Exporter**, sur **Extraire les événements SQL Server**, puis cliquez sur **Extraire les événements Transact-SQL**.  
  
3.  Dans la boîte de dialogue **Enregistrer sous** , attribuez un nom au fichier [!INCLUDE[tsql](../../includes/tsql-md.md)] , puis cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a> Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
