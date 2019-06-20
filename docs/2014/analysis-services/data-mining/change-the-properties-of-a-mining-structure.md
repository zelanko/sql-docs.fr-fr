---
title: Modifier les propriétés d’une Structure d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c9ca227753b8ebbd80d4de0c672fc8cab5c1b56
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66085861"
---
# <a name="change-the-properties-of-a-mining-structure"></a>Modifier les propriétés d'une structure d'exploration de données
  Il existe deux types de propriétés sur une structure d'exploration de données, qui peuvent être modifiées :  
  
-   Propriétés de la structure d'exploration de données qui affectent la structure entière  
  
-   Propriétés sur des colonnes individuelles de la structure  
  
 Notez que certaines propriétés dépendent d'autres paramètres de propriété. Par exemple, vous ne pouvez pas définir les propriétés qui contrôlent le comportement de placement dans un conteneur (notamment <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> ou <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>) jusqu'à ce que vous ayez défini le type de données de la colonne à `Discretized`.  
  
 Pour plus d’informations sur les propriétés de structure d’exploration de données, consultez [Structure d’exploration de données](mining-structure-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>Pour modifier les propriétés d'une structure d'exploration de données  
  
1.  Sous l’onglet **Structure d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit de la souris sur la structure d’exploration de données ou sur une colonne de la structure d’exploration de données, puis sélectionnez **Propriétés**.  
  
     La fenêtre **Propriétés** s’ouvre dans la partie droite de l’écran si elle n’était pas affichée.  
  
2.  Dans la fenêtre **Propriétés** , sélectionnez la valeur qui correspond à la propriété à modifier, puis entrez la nouvelle valeur.  
  
     La nouvelle valeur est appliquée lorsque vous sélectionnez un élément différent dans le concepteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures relatives aux structures d’exploration de données](mining-structure-tasks-and-how-tos.md)  
  
  
