---
title: "Relire un seul &#233;v&#233;nement &#224; la fois (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "événements [SQL Server], relecture d’un seul événement à la fois"
  - "traces [SQL Server], relecture"
  - "relecture des traces"
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 21
---
# Relire un seul &#233;v&#233;nement &#224; la fois (SQL Server Profiler)
  Cette rubrique décrit comment relire un événement à la fois dans un fichier ou une table de trace au moyen du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### Pour relire un seul événement à la fois  
  
1.  Ouvrez le fichier de trace ou la table de trace à relire. Pour plus d’informations, consultez [Ouvrir un fichier de trace&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) ou [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Vérifiez que le fichier de trace ou la table de trace que vous ouvrez contient les classes d'événements nécessaires pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  Dans le menu **Relire**, cliquez sur **Étape** et connectez-vous à l’instance du serveur dont vous voulez relire la trace.  
  
3.  Dans la boîte de dialogue **Configuration de la relecture**, vérifiez les paramètres, puis cliquez sur **OK**. Pour plus d’informations sur la spécification des paramètres dans la boîte de dialogue **Configuration de la relecture**, consultez [Relire un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) ou [Relire une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md).  
  
4.  Pour relire le premier événement, cliquez sur **OK** dans la boîte de dialogue **Configuration de la relecture**.  
  
5.  Pour relire des événements ultérieurs, dans le menu **Relire**, cliquez sur **Étape** ou appuyez sur F10. Continuez à cliquer sur **Étape** ou à appuyer sur F10 pour chaque événement.  
  
## Voir aussi  
 [Relire des traces](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  