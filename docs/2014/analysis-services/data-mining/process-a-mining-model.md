---
title: Traiter un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], processing
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fd2506e835f634937d5bf135ed7eec7cfa259b5f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66083095"
---
# <a name="process-a-mining-model"></a>Traiter un modèle d'exploration de données
  Dans l'onglet Modèles d'exploration de données du Concepteur d'exploration de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous pouvez traiter un modèle d'exploration de données associé à une structure d'exploration de données, ou traiter tous les modèles associés à la structure.  
  
 Vous pouvez traiter un modèle d'exploration de données à l'aide des outils suivants :  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 Vous pouvez également utiliser une commande de traitement XMLA. Pour plus d’informations, consultez [Outils et approches pour le traitement des &#40;Analysis Services&#41;](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md).  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a>Traiter un seul modèle d'exploration de données à l'aide des outils de données SQL Server  
  
1.  Sous l'onglet **Modèles d'exploration de données** du Concepteur d'exploration de données, sélectionnez un modèle d'exploration de données dans une ou plusieurs colonnes des modèles de la grille.  
  
2.  Dans le menu **Modèle d'exploration de données** , sélectionnez **Traiter le modèle**.  
  
     Si vous avez modifié la structure d'exploration de données, un message vous demande de la redéployer avant de traiter le modèle. Cliquez sur **Oui**.  
  
3.  Dans la boîte de dialogue **traitement \<du modèle d’exploration de données model>** , cliquez sur **exécuter**.  
  
     La boîte de dialogue **État d'avancement du traitement** s'ouvre avec les informations de traitement du modèle.  
  
4.  Une fois le modèle traité, cliquez sur **Fermer** dans la boîte de dialogue **État d'avancement du traitement** .  
  
5.  Cliquez sur **Fermer** dans la boîte de dialogue **traitement de modèles d’exploration de \<données>** .  
  
 Seuls la structure d'exploration de données et le modèle d'exploration de données sélectionné ont été traités.  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a>Traiter tous les modèles d'exploration de données associés à une structure d'exploration de données  
  
1.  Dans l'onglet **Modèles d'exploration de données** du Concepteur d'exploration de données, sélectionnez **Traiter l'exploration de données et tous les modèles** dans le menu **Modèle d'exploration de données** .  
  
2.  Si vous avez modifié la structure d'exploration de données, un message vous demande de la redéployer avant de traiter les modèles. Cliquez sur **Oui**.  
  
3.  Dans la boîte de dialogue traitement de la structure d' **exploration de données- \<structure>** , cliquez sur **exécuter**.  
  
4.  La boîte de dialogue **État d'avancement du traitement** s'ouvre avec les informations de traitement du modèle.  
  
5.  Une fois les modèles traités, cliquez sur **Fermer** dans la boîte de dialogue **État d'avancement du traitement** .  
  
6.  Cliquez sur **Fermer** dans la boîte de dialogue **>du modèle de traitement \<** .  
  
 La structure d'exploration de données et tous les modèles d'exploration de données associés ont été traités.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches du modèle d'exploration de données et procédures](mining-model-tasks-and-how-tos.md)  
  
  
