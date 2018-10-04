---
title: Traiter les données (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c3f47ddcfab5df43104d3998822fdaf8bd504946
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048429"
---
# <a name="process-data-ssas-tabular"></a>Traiter les données (SSAS Tabulaire)
  Lorsque vous importez des données dans un modèle tabulaire, en mode mis en cache, vous capturez un instantané de ces données au moment de l'importation. Dans certains cas, ces données peuvent ne jamais changer et elles n'ont pas besoin d'être mises à jour dans le modèle. Toutefois, il est plus probable que les données que vous importez subissent des modifications régulièrement, et pour que votre modèle reflète les données les plus récentes des sources de données, il est nécessaire de traiter (actualiser) ces données et de recalculer les données calculées. Pour mettre à jour les données dans votre modèle, effectuez une action de traitement sur toutes les tables, sur une table individuelle, par partition ou par connexion de source de données.  
  
 Lors de la création de votre projet de modèle, toutes les actions de traitement doivent être initiées manuellement dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Une fois qu'un modèle a été déployé, les opérations de traitement peuvent être effectuées en utilisant [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou planifiées à l'aide d'un script. Les tâches décrites ici concernent toutes des actions de traitement que vous pouvez effectuer pendant la création de modèles dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour plus d'informations sur les actions de traitement pour un modèle déployé, consultez [Process Database, Table, or Partition](tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Traiter manuellement les données &#40;SSAS tabulaire&#41;](manually-process-data-ssas-tabular.md)|Explique comment traiter manuellement des données de l'espace de travail de modèle.|  
|[Résoudre les problèmes de traitement des données &#40;SSAS tabulaire&#41;](troubleshoot-process-data-ssas-tabular.md)|Explique comment résoudre les problèmes liés aux opérations de traitement.|  
  
  
