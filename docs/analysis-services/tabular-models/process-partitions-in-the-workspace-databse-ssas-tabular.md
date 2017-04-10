---
title: "Traiter des partitions dans la base de donn&#233;es de l&#39;espace de travail (SSAS Tabulaire) | Microsoft Docs"
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
ms.assetid: 3a369705-43fa-4961-9045-32e06fbdde33
caps.latest.revision: 12
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 12
---
# Traiter des partitions dans la base de donn&#233;es de l&#39;espace de travail (SSAS Tabulaire)
  Les partitions divisent une table en sections logiques. Chaque partition peut ensuite être traitée (actualisée) indépendamment d'autres partitions. Les tâches de cette rubrique décrivent comment traiter les partitions dans la base de données model de l’espace de travail à l’aide de la boîte de dialogue **Traiter les partitions** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Une fois que le modèle a été déployé sur une autre instance Analysis Services, les administrateurs de bases de données peuvent créer et gérer des partitions dans le modèle (déployé) à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], par script ou à l'aide d'un package IS. Pour plus d’informations, consultez [Créer et gérer des partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
###  <a name="bkmk_create_new"></a> Pour traiter une partition  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle**, puis sur **Traiter** (Actualiser) et sur **Traiter les partitions**.  
  
2.  Dans la zone de liste **Mode**, sélectionnez l’un des modes de traitement suivants :  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Traiter par défaut**|Détecte l'état de traitement d'un objet de partition et effectue le traitement nécessaire pour faire passer les objets de partition non traités ou traités partiellement dans un état de traitement complet. Les données des partitions et des tables vides sont chargées ; les hiérarchies, les colonnes calculées et les relations sont créées ou reconstruites.|  
    |**Traiter entièrement**|Traite un objet de partition et tous les objets qu'il contient. Lorsque la commande Traiter entièrement est exécutée pour un objet qui a déjà été traité, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supprime toutes les données de l'objet, puis traite l'objet. Ce type de traitement est obligatoire lorsqu'une modification structurelle a été apportée à un objet.|  
    |**Traiter les données**|Chargez les données dans une partition ou une table sans reconstruire les hiérarchies ou les relations ni recalculer les colonnes calculées et les mesures.|  
    |**Traiter l'effacement**|Supprime toutes les données d'une partition.|  
    |**Traiter l'ajout**|Mise à jour incrémentielle de la partition avec de nouvelles données.|  
  
3.  Dans la colonne de case à cocher **Traiter** , sélectionnez les partitions à traiter avec le mode sélectionné, puis cliquez sur **OK**.  
  
## Voir aussi  
 [Partitions &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/partitions-ssas-tabular.md)   
 [Créer et gérer des partitions dans la base de données de l’espace de travail &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  