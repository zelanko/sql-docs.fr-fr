---
title: Filtrer le cube source d’une structure d’exploration de données | Microsoft Docs
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081148"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a>Filtrer le cube source d'une structure d'exploration de données
  Lorsque vous créez une structure d’exploration de données basée sur des données dans un modèle multidimensionnel (un cube OLAP), vous pouvez *découper* le cube sur lequel la structure d’exploration de données est basée. Le découpage vous permet de créer des sous-ensembles de données, comme un genre de filtre sur les données utilisées pour l'apprentissage du modèle d'exploration de données.  
  
### <a name="to-slice-a-cube"></a>Pour découper un cube  
  
1.  Dans le concepteur d’exploration [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]de données de, sélectionnez l’onglet **structure d’exploration** de données ou l’onglet **modèles d’exploration** de données.  
  
2.  Dans le menu **modèle d’exploration de données** , sélectionnez définir la structure d’exploration de **données tranche de cube**.  
  
     La boîte de dialogue **découper le cube** s’ouvre.  
  
3.  Dans la colonne **dimension** de la boîte de dialogue **découper le cube** , sélectionnez la dimension que vous souhaitez filtrer.  
  
4.  Sélectionnez un niveau d’une hiérarchie à l’aide de la liste dans la colonne **hiérarchie** .  
  
5.  Sélectionnez un opérateur dans la liste de la colonne **opérateur** , à utiliser lors de la création de la condition de filtre.  
  
6.  Cliquez sur la zone dans la colonne **filtre** .  
  
     Une boîte de dialogue s'ouvre avec tous les membres au niveau spécifié de la hiérarchie.  
  
7.  Sélectionnez le membre ou les membres à filtrer.  
  
8.  Cliquez sur **OK** dans la boîte de dialogue membre.  
  
9. Cliquez sur **OK** dans la boîte de dialogue **découper le cube** .  
  
     Le cube source est filtré comme défini par la coupe de cube.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la structure d’exploration de données et procédures](data-mining/mining-structure-tasks-and-how-tos.md)   
 [Créer une structure d’exploration de données OLAP](data-mining/create-a-new-olap-mining-structure.md)  
  
  
