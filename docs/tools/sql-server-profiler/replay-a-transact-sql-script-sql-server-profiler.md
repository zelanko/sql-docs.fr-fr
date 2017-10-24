---
title: Relire un Script Transact-SQL (SQL Server Profiler) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: eed8da389f0c2422b3aee7ec947e5f34958f190d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>Relire un script Transact-SQL (SQL Server Profiler)
  Lorsque vous testez d'éventuelles solutions à un problème de performances, utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour lire des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)], et comparer les performances avant et après les modifications.  
  
### <a name="to-replay-a-transact-sql-script"></a>Relecture d'un script Transact-SQL  
  
1.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Fichier de script**.  
  
2.  Sélectionnez le fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)] que vous souhaitez ouvrir. Vérifiez que le script [!INCLUDE[tsql](../../includes/tsql-md.md)] contient les événements nécessaires pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](../../tools/sql-server-profiler/replay-requirements.md).  
  
3.  Dans le menu **Relire** , cliquez sur **Démarrer**, puis connectez-vous au serveur où vous souhaitez relire le script.  
  
4.  Dans la boîte de dialogue **Configuration de relecture** , vérifiez les paramètres, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Relire des Traces](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

