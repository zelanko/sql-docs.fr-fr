---
title: Traiter les données (SSAS tabulaire) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 605c0b0171eadbab3e2fb7265ed5059ae521d011
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142155"
---
# <a name="process-data-ssas-tabular"></a>Traiter les données (SSAS Tabulaire)
  Lorsque vous importez des données dans un modèle tabulaire, en mode mis en cache, vous capturez un instantané de ces données au moment de l'importation. Dans certains cas, ces données peuvent ne jamais changer et elles n'ont pas besoin d'être mises à jour dans le modèle. Toutefois, il est plus probable que les données que vous importez subissent des modifications régulièrement, et pour que votre modèle reflète les données les plus récentes des sources de données, il est nécessaire de traiter (actualiser) ces données et de recalculer les données calculées. Pour mettre à jour les données dans votre modèle, effectuez une action de traitement sur toutes les tables, sur une table individuelle, par partition ou par connexion de source de données.  
  
 Lors de la création de votre projet de modèle, toutes les actions de traitement doivent être initiées manuellement dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Une fois qu'un modèle a été déployé, les opérations de traitement peuvent être effectuées en utilisant [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou planifiées à l'aide d'un script. Les tâches décrites ici concernent toutes des actions de traitement que vous pouvez effectuer pendant la création de modèles dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour plus d'informations sur les actions de traitement pour un modèle déployé, consultez [Process Database, Table, or Partition](tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Traiter manuellement des données &#40;SSAS tabulaire&#41;](manually-process-data-ssas-tabular.md)|Explique comment traiter manuellement des données de l'espace de travail de modèle.|  
|[Résoudre les problèmes de traitement des données &#40;SSAS tabulaire&#41;](troubleshoot-process-data-ssas-tabular.md)|Explique comment résoudre les problèmes liés aux opérations de traitement.|  
  
  