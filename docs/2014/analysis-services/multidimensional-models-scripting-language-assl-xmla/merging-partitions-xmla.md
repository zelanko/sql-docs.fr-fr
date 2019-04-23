---
title: Fusion de Partitions (XMLA) | Microsoft Docs
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
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60156065"
---
# <a name="merging-partitions-xmla"></a>Fusion de partitions (XMLA)
  Si des partitions partagent la même conception d’agrégation et la structure, vous pouvez fusionner la partition à l’aide de la [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) commande XML for Analysis (XMLA). Dans le cadre de la gestion des partitions, il est important de fusionner les partitions, plus particulièrement les partitions qui contiennent des données historiques partitionnées par date.  
  
 Par exemple, un cube financier peut utiliser deux partitions :  
  
-   une partition qui représente les données financières de l'exercice en cours, utilisant des paramètres de stockage ROLAP (Relational ROLAP) en temps réel pour les performances ;  
  
-   une autre partition qui contient les données financières des exercices précédents, utilisant des paramètres de stockage MOLAP (Multidimensional OLAP) pour le stockage.  
  
 Les deux partitions utilisent des paramètres de stockage différents, mais elles partagent la même conception d'agrégation. Au lieu de traiter le cube avec plusieurs années de données historiques à la fin de l'exercice, vous pouvez utiliser la commande `MergePartitions` pour fusionner la partition de l'exercice en cours dans la partition des exercices précédents. Cela préserve les données d'agrégation sans qu'il soit nécessaire de traiter entièrement le cube, une opération qui peut s'avérer fastidieuse.  
  
## <a name="specifying-partitions-to-merge"></a>Spécification des partitions à fusionner  
 Lorsque le `MergePartitions` commande est exécutée, les données d’agrégation stockées dans les partitions sources spécifiées dans le [Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) propriété est ajoutée à la partition cible spécifiée dans le [cible](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) propriété.  
  
> [!NOTE]  
>  La propriété `Source` peut contenir plusieurs références d'objet partition. En revanche, la propriété `Target` ne le peut pas.  
  
 Pour que la fusion aboutisse, les partitions spécifiées à la fois dans `Source` et `Target` doivent être contenues dans le même groupe de mesures et utiliser la même conception d'agrégation. Sinon, une erreur se produit.  
  
 Les partitions spécifiées dans `Source` sont supprimées une fois que la commande `MergePartitions` a abouti.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple suivant fusionne toutes les partitions dans le **Customer Counts** groupe de mesures de la **Adventure Works** de cube dans le **Adventure Works DW** exemple [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données dans le **Customers_2004** partition.  
  
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
  
  
