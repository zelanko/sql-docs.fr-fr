---
title: Fusion de partitions (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f09255372478bdb9956b64283c8b94477598239
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62702042"
---
# <a name="merging-partitions-xmla"></a>Fusion de partitions (XMLA)
  Si les partitions ont la même conception d’agrégation et la même structure, vous pouvez fusionner la partition à l’aide de la commande [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) dans XML for Analysis (XMLA). Dans le cadre de la gestion des partitions, il est important de fusionner les partitions, plus particulièrement les partitions qui contiennent des données historiques partitionnées par date.  
  
 Par exemple, un cube financier peut utiliser deux partitions :  
  
-   une partition qui représente les données financières de l'exercice en cours, utilisant des paramètres de stockage ROLAP (Relational ROLAP) en temps réel pour les performances ;  
  
-   une autre partition qui contient les données financières des exercices précédents, utilisant des paramètres de stockage MOLAP (Multidimensional OLAP) pour le stockage.  
  
 Les deux partitions utilisent des paramètres de stockage différents, mais elles partagent la même conception d'agrégation. Au lieu de traiter le cube avec plusieurs années de données historiques à la fin de l'exercice, vous pouvez utiliser la commande `MergePartitions` pour fusionner la partition de l'exercice en cours dans la partition des exercices précédents. Cela préserve les données d'agrégation sans qu'il soit nécessaire de traiter entièrement le cube, une opération qui peut s'avérer fastidieuse.  
  
## <a name="specifying-partitions-to-merge"></a>Spécification des partitions à fusionner  
 Lorsque la `MergePartitions` commande s’exécute, les données d’agrégation stockées dans les partitions sources spécifiées dans la propriété [source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) sont ajoutées à la partition cible spécifiée dans la propriété [cible](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) .  
  
> [!NOTE]  
>  La propriété `Source` peut contenir plusieurs références d'objet partition. En revanche, la propriété `Target` ne le peut pas.  
  
 Pour que la fusion aboutisse, les partitions spécifiées à la fois dans `Source` et `Target` doivent être contenues dans le même groupe de mesures et utiliser la même conception d'agrégation. Sinon, une erreur se produit.  
  
 Les partitions spécifiées dans `Source` sont supprimées une fois que la commande `MergePartitions` a abouti.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple suivant fusionne toutes les partitions du groupe de **mesures Customer Counts** du **cube Adventure Works** de l’exemple [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de base de données **Adventure Works DW** dans la partition **Customers_2004** .  
  
### <a name="code"></a>Code  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
