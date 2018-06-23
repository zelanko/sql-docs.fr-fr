---
title: Extraire un script d’une trace (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 035df37fccf2507195e6576e062b7ce254dd1dba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042340"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>Extraire un script d'une trace (SQL Server Profiler)
  Cette rubrique explique comment extraire des événements [!INCLUDE[tsql](../../includes/tsql-md.md)] d'un fichier ou d'une table de trace et comment les enregistrer sous forme de fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)] , dans le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>Pour extraire un script Transact-SQL à partir d'un fichier ou d'une table de trace  
  
1.  Ouvrez un fichier ou une table de trace contenant les événements [!INCLUDE[tsql](../../includes/tsql-md.md)] que vous voulez enregistrer sous forme de fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour plus d’informations, consultez [Ouvrir un fichier de trace&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) ou [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).  
  
2.  Dans le menu **Fichier**, pointez sur **Exporter**, sur **Extraire les événements SQL Server**, puis cliquez sur **Extraire les événements Transact-SQL**.  
  
3.  Dans la boîte de dialogue **Enregistrer sous** , attribuez un nom au fichier [!INCLUDE[tsql](../../includes/tsql-md.md)] , puis cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  