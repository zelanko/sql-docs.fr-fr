---
title: Fusion de Partitions (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 419ebd0d67b65213fde7393430aedec14249b2ae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63261643"
---
# <a name="merging-partitions-xmla"></a>Fusion de partitions (XMLA)
  Si des partitions partagent la même conception d’agrégation et la structure, vous pouvez fusionner la partition à l’aide de la [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) commande XML for Analysis (XMLA). Dans le cadre de la gestion des partitions, il est important de fusionner les partitions, plus particulièrement les partitions qui contiennent des données historiques partitionnées par date.  
  
 Par exemple, un cube financier peut utiliser deux partitions :  
  
-   une partition qui représente les données financières de l'exercice en cours, utilisant des paramètres de stockage ROLAP (Relational ROLAP) en temps réel pour les performances ;  
  
-   une autre partition qui contient les données financières des exercices précédents, utilisant des paramètres de stockage MOLAP (Multidimensional OLAP) pour le stockage.  
  
 Les deux partitions utilisent des paramètres de stockage différents, mais elles partagent la même conception d'agrégation. Au lieu de traiter le cube avec plusieurs années de données d’historique à la fin de l’année, vous pouvez utiliser la **MergePartitions** commande pour fusionner la partition pour l’année en cours dans la partition des exercices précédents. Cela préserve les données d'agrégation sans qu'il soit nécessaire de traiter entièrement le cube, une opération qui peut s'avérer fastidieuse.  
  
## <a name="specifying-partitions-to-merge"></a>Spécification des partitions à fusionner  
 Lorsque le **MergePartitions** commande est exécutée, les données d’agrégation stockées dans les partitions sources spécifiées dans le [Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) propriété est ajoutée à la partition cible spécifiée dans le [cible ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) propriété.  
  
> [!NOTE]  
>  Le **Source** propriété peut contenir plusieurs références d’objet de partition. Toutefois, le **cible** ne peut pas de propriété.  
  
 Devant être fusionnées avec succès, les partitions spécifiées à la fois dans le **Source** et **cible** doit être contenue dans le même groupe de mesures et utiliser la même conception d’agrégation. Sinon, une erreur se produit.  
  
 Les partitions spécifiées dans le **Source** sont supprimés après la **MergePartitions** commande est terminée avec succès.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple suivant fusionne toutes les partitions dans le **Customer Counts** groupe de mesures de la **Adventure Works** de cube dans le **Adventure Works DW** exemple [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données dans le **Customers_2004** partition.  
  
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
  
  
