---
title: Processus de base de données, la Table ou Partition | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ea2d05c2862445737ea544fdab9c4ca8fc5e6c76
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66066845"
---
# <a name="process-database-table-or-partition"></a>Traiter une base de données, une table ou une partition
  Les tâches de cette rubrique décrivent comment traiter une base de données de modèle tabulaire, table ou des partitions manuellement à l’aide de la **processus \<objet >** boîte de dialogue dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Pour plus d’informations sur le traitement des modèles tabulaires, consultez [Traiter les données &#40;SSAS Tabulaire&#41;](../process-data-ssas-tabular.md).  
  
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
    |**Traiter des données**|Chargez les données dans une partition ou une table sans reconstruire les hiérarchies ou les relations ni recalculer les colonnes calculées et les mesures.|  
    |**Traiter l'effacement**|Supprime toutes les données d'une partition.|  
    |**Traiter l'ajout**|Mise à jour incrémentielle de la partition avec de nouvelles données.|  
  
4.  Dans la colonne de case à cocher **Traiter** , sélectionnez les partitions à traiter avec le mode sélectionné, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions de modèle tabulaire &#40;SSAS Tabulaire&#41;](tabular-model-partitions-ssas-tabular.md)   
 [Créer et gérer des partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
