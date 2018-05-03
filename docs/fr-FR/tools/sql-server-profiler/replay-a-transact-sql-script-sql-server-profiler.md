---
title: Relire un script Transact-SQL (SQL Server Profiler) | Microsoft Docs
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
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 56c8590e3eacdc4f20fda834b5f2d8533ff61e68
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>Relire un script Transact-SQL (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Lorsque vous testez d'éventuelles solutions à un problème de performances, utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour lire des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] , et comparer les performances avant et après les modifications.  
  
### <a name="to-replay-a-transact-sql-script"></a>Relecture d'un script Transact-SQL  
  
1.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Fichier de script**.  
  
2.  Sélectionnez le fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)] que vous souhaitez ouvrir. Vérifiez que le script [!INCLUDE[tsql](../../includes/tsql-md.md)] contient les événements nécessaires pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](../../tools/sql-server-profiler/replay-requirements.md).  
  
3.  Dans le menu **Relire** , cliquez sur **Démarrer**, puis connectez-vous au serveur où vous souhaitez relire le script.  
  
4.  Dans la boîte de dialogue **Configuration de la relecture** , vérifiez les paramètres, puis cliquez sur **OK**.  
  
## <a name="see-also"></a> Voir aussi  
 [Relire des traces](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
