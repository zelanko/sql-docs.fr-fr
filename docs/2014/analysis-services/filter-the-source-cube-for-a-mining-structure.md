---
title: Filtrer le Cube Source pour une Structure d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74220f2385e27484c5cc511c84be5625290a28db
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66081148"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a>Filtrer le cube source d'une structure d'exploration de données
  Lorsque vous créez une structure d’exploration de données qui est basée sur les données dans un modèle multidimensionnel (cube OLAP), vous pouvez *tranche* le cube basé sur la structure d’exploration de données. Le découpage vous permet de créer des sous-ensembles de données, comme un genre de filtre sur les données utilisées pour l'apprentissage du modèle d'exploration de données.  
  
### <a name="to-slice-a-cube"></a>Pour découper un cube  
  
1.  Dans le Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], sélectionnez le **Structure d’exploration de données** onglet ou la **des modèles d’exploration de données** onglet.  
  
2.  Sur le **Mining Model** menu, sélectionnez **définir une coupe de Cube Structure d’exploration de données**.  
  
     Le **découper un Cube** boîte de dialogue s’ouvre.  
  
3.  Dans le **Dimension** colonne de la **découper un Cube** boîte de dialogue, sélectionnez la dimension que vous souhaitez filtrer.  
  
4.  Sélectionnez un niveau d’une hiérarchie, à l’aide de la liste dans le **hiérarchie** colonne.  
  
5.  Sélectionnez un opérateur dans la liste dans le **opérateur** colonne, à utiliser lors de la création de la condition de filtre.  
  
6.  Cliquez sur la zone dans le **filtre** colonne.  
  
     Une boîte de dialogue s'ouvre avec tous les membres au niveau spécifié de la hiérarchie.  
  
7.  Sélectionnez le membre ou les membres à filtrer.  
  
8.  Cliquez sur **OK** dans la boîte de dialogue de membre.  
  
9. Cliquez sur **OK** dans le **découper un Cube** boîte de dialogue.  
  
     Le cube source est filtré comme défini par la coupe de cube.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la structure d'exploration de données et procédures](data-mining/mining-structure-tasks-and-how-tos.md)   
 [Créer une structure d’exploration de données OLAP](data-mining/create-a-new-olap-mining-structure.md)  
  
  
