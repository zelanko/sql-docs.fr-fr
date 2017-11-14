---
title: "Processus de base de données, la Table ou Partition (Analysis Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 89e7f6904f4e47fc6f2047acec2b7bbc02c68c20
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="process-database-table-or-partition-analysis-services"></a>Processus de base de données, table ou partition (Analysis Services)
  Les tâches de cette rubrique décrivent comment traiter manuellement les partitions, table ou une base de données de modèle tabulaire à l’aide de la **processus \<objet >** boîte de dialogue de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Pour plus d’informations sur le traitement des modèles tabulaires, consultez [Traiter les données &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/process-data-ssas-tabular.md).  
  
##  <a name="bkmk_process_tasks"></a> Tâches  
  
###  <a name="bkmk_process_db"></a> Pour traiter une base de données  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur la base de données à traiter, puis cliquez sur **Traiter la base de données**.  
  
2.  Dans la boîte de dialogue **Traiter la base de données** , dans la zone de liste **Mode** , sélectionnez l’un des modes de traitement suivants :  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Traiter par défaut**|Détecte l'état de traitement des objets de base de données et effectue le traitement nécessaire pour faire passer les objets non traités ou traités partiellement dans un état de traitement complet. Les données des partitions et des tables vides sont chargées ; les hiérarchies, les colonnes calculées et les relations sont créées ou reconstruites (recalculées).|  
    |**Traiter entièrement**|Traite une base de données et tous les objets qu'elle contient. Lorsque la commande Traiter entièrement est exécutée pour un objet qui a déjà été traité, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supprime toutes les données de l'objet, puis traite l'objet. Ce type de traitement est obligatoire lorsqu'une modification structurelle a été apportée à un objet. Cette option nécessite le plus de ressources.|  
    |**Traiter l'effacement**|Supprime toutes les données des objets de base de données.|  
    |**Traiter le recalcul**|Met à jour et recalcule les hiérarchies, les relations et les colonnes calculées.|  
  
3.  Dans la colonne de case à cocher **Traiter** , sélectionnez les partitions à traiter avec le mode sélectionné, puis cliquez sur **OK**.  
  
###  <a name="bkmk_process_table"></a> Pour traiter une table  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans la base de données model tabulaire qui contient la table à traiter, développez le nœud **Tables** , cliquez avec le bouton droit sur la table à traiter et sélectionnez **Traiter la table**.  
  
2.  Dans la boîte de dialogue **Traiter la table** , dans la zone de liste **Mode** , sélectionnez l’un des modes de traitement suivants :  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Traiter par défaut**|Détecte l'état de traitement d'un objet de table et effectue le traitement nécessaire pour faire passer les objets non traités ou traités partiellement dans un état de traitement complet. Les données des partitions et des tables vides sont chargées ; les hiérarchies, les colonnes calculées et les relations sont créées ou reconstruites (recalculées).|  
    |**Traiter entièrement**|Traite un objet de table et tous les objets qu'il contient. Lorsque la commande Traiter entièrement est exécutée pour un objet qui a déjà été traité, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supprime toutes les données de l'objet, puis traite l'objet. Ce type de traitement est obligatoire lorsqu'une modification structurelle a été apportée à un objet. Cette option nécessite le plus de ressources.|  
    |**Traiter les données**|Chargez les données dans une table sans reconstruire les hiérarchies ou les relations ni recalculer les colonnes calculées et les mesures.|  
    |**Traiter l'effacement**|Supprime toutes les données d'une table et de toutes les partitions de table.|  
    |**Traiter la défragmentation**|Défragmente les index de table auxiliaire.|  
  
3.  Dans la colonne de cases à cocher de la table, vérifiez la table et sélectionnez éventuellement toutes les tables supplémentaires à traiter, puis cliquez sur **OK**.  
  
###  <a name="bkmk_process_partition"></a> Pour traiter une ou plusieurs partitions  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur la table qui contient les partitions à traiter, puis sélectionnez **Partitions**.  
  
2.  Dans la boîte de dialogue **Partitions** , dans **Partitions**, cliquez sur le bouton Traiter.  
  
3.  Dans la boîte de dialogue **Traiter la partition** , dans la zone de liste **Mode** , sélectionnez l’un des modes de traitement suivants :  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Traiter par défaut**|Détecte l'état de traitement d'un objet de partition et effectue le traitement nécessaire pour faire passer les objets de partition non traités ou traités partiellement dans un état de traitement complet. Les données des partitions et des tables vides sont chargées ; les hiérarchies, les colonnes calculées et les relations sont créées ou reconstruites (recalculées).|  
    |**Traiter entièrement**|Traite un objet de partition et tous les objets qu'il contient. Lorsque la commande Traiter entièrement est exécutée pour un objet qui a déjà été traité, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supprime toutes les données de l'objet, puis traite l'objet. Ce type de traitement est obligatoire lorsqu'une modification structurelle a été apportée à un objet.|  
    |**Traiter les données**|Chargez les données dans une partition ou une table sans reconstruire les hiérarchies ou les relations ni recalculer les colonnes calculées et les mesures.|  
    |**Traiter l'effacement**|Supprime toutes les données d'une partition.|  
    |**Traiter l'ajout**|Mise à jour incrémentielle de la partition avec de nouvelles données.|  
  
4.  Dans la colonne de case à cocher **Traiter** , sélectionnez les partitions à traiter avec le mode sélectionné, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions de modèle tabulaire &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [Créer et gérer des partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  

