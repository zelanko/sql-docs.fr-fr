---
title: Utiliser SQL Server Profiler pour surveiller Analysis Services | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 338f49e4ee261ff1f17e25e4781f717a86418363
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a>Utiliser SQL Server Profiler pour contrôler Analysis Services
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Le assure le suivi des événements de processus du moteur, notamment le début d’un lot ou d’une transaction, et capture des données à propos de ces événements, ce qui vous permet de surveiller l’activité des serveurs et des bases de données (par exemple, les requêtes des utilisateurs ou les connexions). Vous pouvez capturer les données du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] dans une table ou un fichier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , en vue d'une analyse ultérieure, et relire les événements capturés sur la même instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou sur une autre instance pour voir exactement ce qui s'est passé. Vous pouvez relire les événements en temps réel ou pas à pas. Il est également très utile d'exécuter sur la même machine les événements de trace et les compteurs de performances. SQL Profiler peut corréler les deux en fonction de l'heure et les afficher ensemble sur une même chronologie. Les événements de trace vous donneront plus de détails, tandis que les compteurs de performances vous fourniront une vue agrégée. Pour plus d’informations sur la création et l’exécution de traces, consultez [Créer des traces de SQL Server Profiler pour la relecture &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md).  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Introduction à la surveillance de Analysis Services à l'aide de SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|Explique comment utiliser le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour contrôler une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Créer des traces de SQL Server Profiler pour la relecture &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)|Indique les conditions requises pour créer une trace afin d'effectuer une relecture en utilisant le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Événements de trace Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)|Décrit les classes d'événements [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Ces classes d'événements sont associées aux actions générées par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et utilisées pour les relectures de traces.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser une instance Analysis Services](../../analysis-services/instances/monitor-an-analysis-services-instance.md)  
  
  

