---
title: "Cr&#233;er et g&#233;rer des partitions de mod&#232;les tabulaires (SSAS Tabulaire) | Microsoft Docs"
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
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 8
---
# Cr&#233;er et g&#233;rer des partitions de mod&#232;les tabulaires (SSAS Tabulaire)
  Les partitions divisent une table en sections logiques. Chaque partition peut ensuite être traitée (actualisée) indépendamment d'autres partitions. Les partitions définies pour un modèle au cours de la création de modèles sont dupliquées dans un modèle déployé. Une fois le déploiement terminé, vous pouvez gérer ces partitions à l'aide de la boîte de dialogue **Partitions** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou à l'aide d'un script. Les tâches fournies dans cette rubrique décrivent comment créer et gérer des partitions pour un modèle déployé.  
  
 Cette rubrique inclut les tâches suivantes :  
  
-   [Pour créer une nouvelle partition](#bkmk_create_new)  
  
-   [Pour copier une partition](#bkmk_copy)  
  
-   [Pour fusionner deux ou plusieurs partitions](#bkmk_merge)  
  
-   [Pour supprimer une partition](#bkmk_delete)  
  
## Tâches  
 Pour créer et gérer des partitions d'une base de données de modèle tabulaire déployée, vous utiliserez la boîte de dialogue **Partitions** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour afficher la boîte de dialogue **Partitions**, dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur une table, puis cliquez sur **Partitions**.  
  
###  <a name="bkmk_create_new"></a> Pour créer une nouvelle partition  
  
1.  Dans la boîte de dialogue **Partitions** , cliquez sur le bouton **Nouveau** .  
  
2.  Dans **Nom de la partition**, tapez un nom pour la partition. Par défaut, le nom de la partition par défaut est numéroté de manière incrémentielle pour chaque nouvelle partition.  
  
3.  Dans **Instruction SQL**, tapez ou collez une instruction de requête SQL qui définit les colonnes et toutes les clauses que vous souhaitez inclure à la partition dans la fenêtre de requête.  
  
4.  Pour valider l'instruction, cliquez sur **Vérifier la syntaxe**.  
  
###  <a name="bkmk_copy"></a> Pour copier une partition  
  
1.  Dans la boîte de dialogue **Partitions** , dans la liste **Partitions** , sélectionnez la partition à copier, puis cliquez sur le bouton **Copier** .  
  
2.  Dans **Nom de la partition**, tapez un nouveau nom pour la partition.  
  
3.  Dans **Instruction SQL**, modifiez l'instruction de requête SQL.  
  
###  <a name="bkmk_merge"></a> Pour fusionner deux ou plusieurs partitions  
  
-   Dans la boîte de dialogue **Partitions**, dans la liste **Partitions**, utilisez Ctrl+clic pour sélectionner les partitions à fusionner, puis cliquez sur le bouton **Fusionner**.  
  
> [!IMPORTANT]  
>  Le fait de fusionner les partitions ne met pas à jour les métadonnées des partitions. Les administrateurs doivent modifier l'instruction SQL pour la partition obtenue afin de veiller à ce que les opérations de traitement traitent toutes les données dans la partition fusionnée.  
  
###  <a name="bkmk_delete"></a> Pour supprimer une partition  
  
-   Dans la boîte de dialogue **Partitions** , dans la liste **Partitions** , sélectionnez la partition à supprimer, puis cliquez sur le bouton **Supprimer** .  
  
## Voir aussi  
 [Partitions de modèle tabulaire &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [Traiter les partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/process-tabular-model-partitions-ssas-tabular.md)  
  
  