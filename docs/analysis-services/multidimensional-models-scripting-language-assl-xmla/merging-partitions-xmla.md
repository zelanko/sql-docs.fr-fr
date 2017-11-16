---
title: La fusion de Partitions (XMLA) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5528a4392eb5e6554cafc179e0ceedc14b26c0c7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="merging-partitions-xmla"></a>Fusion de partitions (XMLA)
  Si les partitions ont la même conception d’agrégation et la structure, vous pouvez fusionner la partition à l’aide de la [MergePartitions](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md) commande XML for Analysis (XMLA). Dans le cadre de la gestion des partitions, il est important de fusionner les partitions, plus particulièrement les partitions qui contiennent des données historiques partitionnées par date.  
  
 Par exemple, un cube financier peut utiliser deux partitions :  
  
-   une partition qui représente les données financières de l'exercice en cours, utilisant des paramètres de stockage ROLAP (Relational ROLAP) en temps réel pour les performances ;  
  
-   une autre partition qui contient les données financières des exercices précédents, utilisant des paramètres de stockage MOLAP (Multidimensional OLAP) pour le stockage.  
  
 Les deux partitions utilisent des paramètres de stockage différents, mais elles partagent la même conception d'agrégation. Au lieu de traiter le cube plusieurs années de données d’historique à la fin de l’année, vous pouvez utiliser la **MergePartitions** commande pour fusionner la partition pour l’année en cours dans la partition des exercices précédents. Cela préserve les données d'agrégation sans qu'il soit nécessaire de traiter entièrement le cube, une opération qui peut s'avérer fastidieuse.  
  
## <a name="specifying-partitions-to-merge"></a>Spécification des partitions à fusionner  
 Lorsque le **MergePartitions** commande est exécutée, les données d’agrégation stockées dans les partitions sources spécifiées dans le [Source](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md) propriété est ajoutée à la partition cible spécifiée dans le [cible](../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md) propriété.  
  
> [!NOTE]  
>  Le **Source** propriété peut contenir plusieurs références d’objet de partition. Toutefois, le **cible** ne peut pas de propriété.  
  
 Doit être fusionné avec succès, les partitions spécifiées à la fois dans le **Source** et **cible** doit être contenue dans le même groupe de mesures et utiliser la même conception d’agrégation. Sinon, une erreur se produit.  
  
 Les partitions spécifiées dans le **Source** sont supprimées après la **MergePartitions** commande est terminée avec succès.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a> Description  
 L’exemple suivant fusionne toutes les partitions dans le **Customer Counts** groupe de mesures de la **Adventure Works** de cube dans le **Adventure Works DW** exemple [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans la base de données le **Customers_2004** partition.  
  
### <a name="code"></a>Code  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
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
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

