---
title: Relire un script Transact-SQL (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b85c31fcaad26d6cc8604764e37d8aa32d58610
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62712352"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>Relire un script Transact-SQL (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Lorsque vous testez d'éventuelles solutions à un problème de performances, utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour lire des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] , et comparer les performances avant et après les modifications.  
  
### <a name="to-replay-a-transact-sql-script"></a>Relecture d'un script Transact-SQL  
  
1.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Fichier de script**.  
  
2.  Sélectionnez le fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)] que vous souhaitez ouvrir. Vérifiez que le script [!INCLUDE[tsql](../../includes/tsql-md.md)] contient les événements nécessaires pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](../../tools/sql-server-profiler/replay-requirements.md).  
  
3.  Dans le menu **Relire** , cliquez sur **Démarrer**, puis connectez-vous au serveur où vous souhaitez relire le script.  
  
4.  Dans la boîte de dialogue **Configuration de la relecture** , vérifiez les paramètres, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Relire des traces](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
