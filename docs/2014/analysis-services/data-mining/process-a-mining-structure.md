---
title: Traiter une Structure d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 92793adcf2fd04b1dac0c26933c1d5969a31f1a5
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66083110"
---
# <a name="process-a-mining-structure"></a>traiter une structure d'exploration de données
  Pour pouvoir consulter ou utiliser des modèles d'exploration de données associés à une structure d'exploration de données, vous devez déployer le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et traiter la structure d'exploration de données et les modèles d'exploration de données. De plus, si vous modifiez la structure d’exploration de données ou les modèles d’exploration de données, un message vous invite à les redéployer et les retraiter. Le traitement de la structure sous l’onglet **Structure d’exploration de données** du Concepteur d’exploration de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] traite tous les modèles associés.  
  
 Vous pouvez traiter une structure d'exploration de données à l'aide de ces outils :  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   XMLA : commande Process  
  
 Pour plus d’informations sur la façon de traiter les différents modèles, consultez [Traiter un modèle d’exploration de données](process-a-mining-model.md).  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a>Pour traiter une structure d'exploration de données et tous les modèles d'exploration de données associés à l'aide des outils de données SQL Server  
  
1.  Sélectionnez **Traiter la structure d’exploration de données et tous les modèles** dans l’option de menu **Modèle d’exploration de données** de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
     Si vous modifiez la structure, un message vous demande de la redéployer avant de traiter les modèles. Cliquez sur **Oui**.  
  
2.  Cliquez sur **exécuter** dans le **traiter la Structure d’exploration de données - \<structure >** boîte de dialogue.  
  
     La boîte de dialogue **État d’avancement du traitement** s’ouvre avec les informations sur le traitement des modèles.  
  
3.  Cliquez sur **Fermer** dans la boîte de dialogue **État d’avancement du traitement** une fois que les modèles ont été traités.  
  
4.  Cliquez sur **fermer** dans le **traiter la Structure d’exploration de données - \<structure >** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures relatives aux structures d’exploration de données](mining-structure-tasks-and-how-tos.md)  
  
  
