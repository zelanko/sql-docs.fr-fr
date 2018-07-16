---
title: Relire un seul événement à la fois (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5424a91d2672710a593555c937157a4501469e4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299349"
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a>Relire un seul événement à la fois (SQL Server Profiler)
  Cette rubrique décrit comment relire un événement à la fois dans un fichier ou une table de trace au moyen du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-replay-a-single-event-at-a-time"></a>Pour relire un seul événement à la fois  
  
1.  Ouvrez le fichier de trace ou la table de trace à relire. Pour plus d’informations, consultez [Ouvrir un fichier de trace&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) ou [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).  
  
     Vérifiez que le fichier de trace ou la table de trace que vous ouvrez contient les classes d'événements nécessaires pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](replay-requirements.md).  
  
2.  Dans le menu **Relire** , cliquez sur **Étape**et connectez-vous à l’instance du serveur dont vous voulez relire la trace.  
  
3.  Dans la boîte de dialogue **Configuration de la relecture**, vérifiez les paramètres, puis cliquez sur **OK**. Pour plus d’informations sur la spécification des paramètres dans la boîte de dialogue **Configuration de la relecture**, consultez [Relire un fichier de trace &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) ou [Relire une table de trace &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md).  
  
4.  Pour relire le premier événement, cliquez sur **OK** dans la boîte de dialogue **Configuration de la relecture**.  
  
5.  Pour relire des événements ultérieurs, dans le menu **Relire** , cliquez sur **Étape**ou appuyez sur F10. Continuez à cliquer sur **Étape** ou à appuyer sur F10 pour chaque événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Relire des Traces](replay-traces.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
