---
title: Extraire un script d’une trace (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e94dd6e91814a70366f41dd7ee6f788c63e5455d
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67731355"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>Extraire un script d'une trace (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment extraire des événements [!INCLUDE[tsql](../../includes/tsql-md.md)] d'un fichier ou d'une table de trace et comment les enregistrer sous forme de fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)] , dans le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>Pour extraire un script Transact-SQL à partir d'un fichier ou d'une table de trace  
  
1.  Ouvrez un fichier ou une table de trace contenant les événements [!INCLUDE[tsql](../../includes/tsql-md.md)] que vous voulez enregistrer sous forme de fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour plus d’informations, consultez [Ouvrir un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) ou l'Assistant Paramétrage du [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
2.  Dans le menu **Fichier**, pointez sur **Exporter**, sur **Extraire les événements SQL Server**, puis cliquez sur **Extraire les événements Transact-SQL**.  
  
3.  Dans la boîte de dialogue **Enregistrer sous** , attribuez un nom au fichier [!INCLUDE[tsql](../../includes/tsql-md.md)] , puis cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
