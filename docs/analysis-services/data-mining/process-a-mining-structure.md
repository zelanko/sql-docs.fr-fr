---
title: "Traiter une Structure d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2e9c6f31a8701571b2d9be03eecd34050757e7a7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="process-a-mining-structure"></a>traiter une structure d'exploration de données
  Pour pouvoir consulter ou utiliser des modèles d'exploration de données associés à une structure d'exploration de données, vous devez déployer le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et traiter la structure d'exploration de données et les modèles d'exploration de données. De plus, si vous modifiez la structure d’exploration de données ou les modèles d’exploration de données, un message vous invite à les redéployer et les retraiter. Le traitement de la structure sous l’onglet **Structure d’exploration de données** du Concepteur d’exploration de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] traite tous les modèles associés.  
  
 Vous pouvez traiter une structure d'exploration de données à l'aide de ces outils :  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   XMLA : commande Process  
  
 Pour plus d’informations sur la façon de traiter les différents modèles, consultez [Traiter un modèle d’exploration de données](../../analysis-services/data-mining/process-a-mining-model.md).  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a>Pour traiter une structure d'exploration de données et tous les modèles d'exploration de données associés à l'aide des outils de données SQL Server  
  
1.  Sélectionnez **Traiter la structure d’exploration de données et tous les modèles** dans l’option de menu **Modèle d’exploration de données** de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
     Si vous modifiez la structure, un message vous demande de la redéployer avant de traiter les modèles. Cliquez sur **Oui**.  
  
2.  Cliquez sur **exécuter** dans les **traiter la Structure d’exploration de données - \<structure >** boîte de dialogue.  
  
     La boîte de dialogue **État d’avancement du traitement** s’ouvre avec les informations sur le traitement des modèles.  
  
3.  Cliquez sur **Fermer** dans la boîte de dialogue **État d’avancement du traitement** une fois que les modèles ont été traités.  
  
4.  Cliquez sur **fermer** dans les **traiter la Structure d’exploration de données - \<structure >** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la structure d'exploration de données et procédures](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  

