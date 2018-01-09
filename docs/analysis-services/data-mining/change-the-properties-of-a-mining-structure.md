---
title: "Modifier les propriétés d’une Structure d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2f97c94a1c594a341c1e03326c975a080d9033cf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="change-the-properties-of-a-mining-structure"></a>Modifier les propriétés d'une structure d'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Il existe deux types de propriétés sur une structure d’exploration de données, qui peuvent être modifiées :  
  
-   Propriétés de la structure d'exploration de données qui affectent la structure entière  
  
-   Propriétés sur des colonnes individuelles de la structure  
  
 Notez que certaines propriétés dépendent d'autres paramètres de propriété. Par exemple, vous ne pouvez pas définir les propriétés qui contrôlent le comportement de placement dans un conteneur (notamment <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> ou <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>) jusqu’à ce que vous ayez défini le type de données de la colonne sur **Discretized**.  
  
 Pour plus d’informations sur les propriétés de structure d’exploration de données, consultez [Structure d’exploration de données](../../analysis-services/data-mining/mining-structure-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>Pour modifier les propriétés d'une structure d'exploration de données  
  
1.  Sous l’onglet **Structure d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit de la souris sur la structure d’exploration de données ou sur une colonne de la structure d’exploration de données, puis sélectionnez **Propriétés**.  
  
     La fenêtre **Propriétés** s’ouvre dans la partie droite de l’écran si elle n’était pas affichée.  
  
2.  Dans la fenêtre **Propriétés** , sélectionnez la valeur qui correspond à la propriété à modifier, puis entrez la nouvelle valeur.  
  
     La nouvelle valeur est appliquée lorsque vous sélectionnez un élément différent dans le concepteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures relatives aux structures d’exploration de données](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
