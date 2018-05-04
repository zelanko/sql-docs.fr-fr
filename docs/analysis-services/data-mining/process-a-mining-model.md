---
title: Traiter un modèle d’exploration de données | Documents Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], processing
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ed7f670a46c49cc31b576b68ae1b2c7a5edd46d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="process-a-mining-model"></a>Traiter un modèle d'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dans l'onglet Modèles d'exploration de données du Concepteur d'exploration de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous pouvez traiter un modèle d'exploration de données associé à une structure d'exploration de données, ou traiter tous les modèles associés à la structure.  
  
 Vous pouvez traiter un modèle d'exploration de données à l'aide des outils suivants :  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 Vous pouvez également utiliser une commande de traitement XMLA. Pour plus d’informations, consultez [Outils et approches de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/tools-and-approaches-for-processing-analysis-services.md).  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a>Traiter un seul modèle d'exploration de données à l'aide des outils de données SQL Server  
  
1.  Sous l'onglet **Modèles d'exploration de données** du Concepteur d'exploration de données, sélectionnez un modèle d'exploration de données dans une ou plusieurs colonnes des modèles de la grille.  
  
2.  Dans le menu **Modèle d'exploration de données** , sélectionnez **Traiter le modèle**.  
  
     Si vous avez modifié la structure d'exploration de données, un message vous demande de la redéployer avant de traiter le modèle. Cliquez sur **Oui**.  
  
3.  Dans le **traiter le modèle d’exploration de données - \<modèle >** boîte de dialogue, cliquez sur **exécuter**.  
  
     La boîte de dialogue **État d'avancement du traitement** s'ouvre avec les informations de traitement du modèle.  
  
4.  Une fois le modèle traité, cliquez sur **Fermer** dans la boîte de dialogue **État d'avancement du traitement** .  
  
5.  Cliquez sur **fermer** dans les **traiter le modèle d’exploration de données - \<modèle >** boîte de dialogue.  
  
 Seuls la structure d'exploration de données et le modèle d'exploration de données sélectionné ont été traités.  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a>Traiter tous les modèles d'exploration de données associés à une structure d'exploration de données  
  
1.  Dans l'onglet **Modèles d'exploration de données** du Concepteur d'exploration de données, sélectionnez **Traiter l'exploration de données et tous les modèles** dans le menu **Modèle d'exploration de données** .  
  
2.  Si vous avez modifié la structure d'exploration de données, un message vous demande de la redéployer avant de traiter les modèles. Cliquez sur **Oui**.  
  
3.  Dans le **traiter la Structure d’exploration de données - \<structure >** boîte de dialogue, cliquez sur **exécuter**.  
  
4.  La boîte de dialogue **État d'avancement du traitement** s'ouvre avec les informations de traitement du modèle.  
  
5.  Une fois les modèles traités, cliquez sur **Fermer** dans la boîte de dialogue **État d'avancement du traitement** .  
  
6.  Cliquez sur **fermer** dans les **traitement \<modèle >** boîte de dialogue.  
  
 La structure d'exploration de données et tous les modèles d'exploration de données associés ont été traités.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches liées aux modèles d’exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
