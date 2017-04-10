---
title: "supprimer un mod&#232;le d&#39;exploration de donn&#233;es d&#39;une structure d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "structures d’exploration de données [Analysis Services], modèles d’exploration de données"
  - "suppression de modèles d'exploration de données"
  - "retrait de modèles d'exploration de données"
  - "modèles d’exploration de données [Analysis Services], suppression"
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 29
---
# supprimer un mod&#232;le d&#39;exploration de donn&#233;es d&#39;une structure d&#39;exploration de donn&#233;es
  Vous pouvez supprimer les modèles d’exploration de données en utilisant le Concepteur d’exploration de données, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou des instructions DMX.  
  
### Supprimer un modèle d'exploration de données à l'aide de des outils de données SQL Server  
  
1.  Sélectionnez l’onglet **Modèles d’exploration de données** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur le modèle à supprimer, puis sélectionnez **Supprimer**.  
  
     La boîte de dialogue **Supprimer les objets** s’ouvre.  
  
3.  Cliquez sur **OK**.  
  
### Supprimer un modèle d'exploration de données à l'aide de SQL Server Management Studio  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient le modèle.  
  
2.  Développez **Structures d’exploration de données**, puis développez **Modèles d’exploration de données**.  
  
3.  Cliquez avec le bouton droit sur le modèle à supprimer, puis sélectionnez **Supprimer**.  
  
     La suppression du modèle ne supprime pas les données d'apprentissage, seuls les métadonnées et les schémas créés lorsque vous avez formé le modèle sont supprimés.  
  
### Supprimer un modèle d'exploration de données à l'aide de DMX  
  
-   [DROP MINING MODEL &#40;DMX&#41;](../../dmx/drop-mining-model-dmx.md)  
  
## Voir aussi  
 [Tâches du modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  