---
title: "Traiter les donn&#233;es (SSAS Tabulaire) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Traiter les donn&#233;es (SSAS Tabulaire)
  Lorsque vous importez des données dans un modèle tabulaire, en mode mis en cache, vous capturez un instantané de ces données au moment de l'importation. Dans certains cas, ces données peuvent ne jamais changer et elles n'ont pas besoin d'être mises à jour dans le modèle. Toutefois, il est plus probable que les données que vous importez subissent des modifications régulièrement, et pour que votre modèle reflète les données les plus récentes des sources de données, il est nécessaire de traiter (actualiser) ces données et de recalculer les données calculées. Pour mettre à jour les données dans votre modèle, effectuez une action de traitement sur toutes les tables, sur une table individuelle, par partition ou par connexion de source de données.  
  
 Lors de la création de votre projet de modèle, toutes les actions de traitement doivent être initiées manuellement dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Une fois qu'un modèle a été déployé, les opérations de traitement peuvent être effectuées en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou planifiées à l'aide d'un script. Les tâches décrites ici concernent toutes des actions de traitement que vous pouvez effectuer pendant la création de modèles dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations sur les actions de traitement pour un modèle déployé, consultez [Traiter une base de données, une table ou une partition &#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## Tâches associées  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Traiter manuellement les données &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/manually-process-data-ssas-tabular.md)|Explique comment traiter manuellement des données de l'espace de travail de modèle.|  
|[Dépanner le traitement des données &#40;SSAS Tabulaire&#41;](../../analysis-services/troubleshoot-process-data-ssas-tabular.md)|Explique comment résoudre les problèmes liés aux opérations de traitement.|  
  
  