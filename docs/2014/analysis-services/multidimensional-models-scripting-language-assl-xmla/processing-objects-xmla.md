---
title: Traitement d’objets (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab38ea9b58e891d813a3ca73f43d20a364275da0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62727595"
---
# <a name="processing-objects-xmla"></a>Traitement d'objets (XMLA)
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le traitement est l’étape ou la série d’étapes qui transforment les données en informations pour l’analyse de l’entreprise. Si le traitement varie selon le type d'objet, le traitement consiste toujours à transformer des données en informations.  
  
 Pour traiter un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objet, vous pouvez utiliser la commande [traiter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) . La commande `Process` peut traiter les objets suivants dans une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :  
  
-   Cubes  
  
-   Bases de données  
  
-   Dimensions  
  
-   les groupes de mesures ;  
  
-   Modèles d'exploration de données  
  
-   Structures d'exploration de données  
  
-   Partitions  
  
 Pour contrôler le traitement des objets, la commande `Process` propose plusieurs propriétés définissables. Les propriétés de la commande `Process` permettent de contrôler les éléments suivants : portée du traitement, types d'objets à traiter, utilisation ou non de liaisons hors ligne, gestion des erreurs et gestion des tables d'écriture différée.  
  
## <a name="specifying-processing-options"></a>Spécification d'options de traitement  
 La propriété [type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) de la `Process` commande spécifie l’option de traitement à utiliser lors du traitement de l’objet. Pour plus d’informations sur les options de traitement, consultez [Options et paramètres de traitement &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
 Le tableau suivant répertorie les constantes associées à la propriété `Type` et les différents objets qui peuvent être traités avec chaque constant.  
  
|`Type`ajoutée|Objets applicables|  
|--------------------|------------------------|  
|*ProcessFull*|Cube, base de données, dimension, groupe de mesures, modèle d'exploration de données, structure d'exploration de données, partition|  
|*ProcessAdd*|Dimension, partition|  
|*ProcessUpdate*|Dimension|  
|*ProcessIndexes*|Dimension, cube, groupe de mesures, partition|  
|*ProcessData*|Dimension, cube, groupe de mesures, partition|  
|*ProcessDefault*|Cube, base de données, dimension, groupe de mesures, modèle d'exploration de données, structure d'exploration de données, partition|  
|*ProcessClear*|Cube, base de données, dimension, groupe de mesures, modèle d'exploration de données, structure d'exploration de données, partition|  
|*ProcessStructure*|Cube, structure d'exploration de données|  
|*ProcessClearStructureOnly*|Structure d'exploration de données|  
|*ProcessScriptCache*|Cube|  
  
 Pour plus d’informations sur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] le traitement des objets, consultez traitement de l' [objet de modèle multidimensionnel](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>Spécification des objets à traiter  
 La propriété [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) de la `Process` commande contient l’identificateur d’objet de l’objet à traiter. Seul un objet peut être spécifié dans une commande `Process`, mais le traitement d'un objet porte également sur les objets enfants. Par exemple, le traitement d'un groupe de mesures dans un cube englobe toutes les partitions de ce groupe de mesures. De même, le traitement d'une base de données porte sur tous ses objets, notamment les cubes, les dimensions et les structures d'exploration de données contenus dans la base de données.  
  
 Si vous définissez l'attribut `ProcessAffectedObjects` de la commande `Process` à true, les objets connexes affectés par le traitement de l'objet spécifié sont égalements traités. Par exemple, si une dimension est mise à jour de façon incrémentielle ** à l’aide de l' `Process` option de traitement ProcessUpdate de la commande, toute partition dont les agrégations sont invalidées en raison de l' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ajout `ProcessAffectedObjects` ou de la suppression de membres est également traitée par si a la valeur true. Dans ce cas, une seule commande `Process` peut traiter plusieurs objets dans une même instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], mais c'est [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui détermine quels sont les objets, outre l'objet unique spécifié dans la commande `Process`, qui doivent également être traités.  
  
 Toutefois, vous pouvez traiter simultanément plusieurs objets, tels que des dimensions, en utilisant plusieurs commandes `Process` au sein d'une commande `Batch`. Lorsqu'il s'agit de traiter les objets d'une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en série ou en parallèle, les opérations de traitement par lot offrent un niveau de contrôle plus fin qu'en utilisant l'attribut `ProcessAffectedObjects`. Elles vous permettent en outre d'affiner votre approche de traitement pour les bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] plus volumineuses. Pour plus d’informations sur l’exécution d’opérations par lots, consultez [exécution d’opérations par lots &#40;&#41;XMLA ](performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>Spécification de liaisons hors ligne  
 Si la `Process` commande n’est pas contenue `Batch` dans une commande, vous pouvez éventuellement spécifier des liaisons hors ligne dans les propriétés [bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)et [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) de la `Process` commande pour les objets à traiter. Les liaisons hors lignes sont des références à des sources de données, des vues de source de données et d'autres objets dans lesquels elles existent seulement le temps de l'exécution de la commande `Process`. Elles remplacent les liaisons existantes associées aux objets traités. Si aucune liaison hors ligne n'est spécifiée, les liaisons actuellement associées aux objets à traiter sont utilisées.  
  
 Les liaisons hors ligne sont utilisées dans les circonstances suivantes :  
  
-   traitement incrémentiel d'une partition dans laquelle une table de faits alternative ou un filtre appliqué à la table de faits existante doit être spécifié pour éviter que les lignes ne soient comptées deux fois ;  
  
-   Utilisation d’une tâche de workflow [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans pour fournir des données lors du traitement d’une dimension, d’un modèle d’exploration de données ou d’une partition.  
  
 Les liaisons hors ligne sont décrites dans le cadre d'ASSL (Analysis Services Scripting Language). Pour plus d’informations sur les liaisons hors ligne dans ASSL, consultez sources de [données et liaisons &#40;&#41;multidimensionnel SSAS ](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>Mise à jour incrémentielle des partitions  
 La mise à jour incrémentielle d'une partition déjà traitée fait généralement appel à une liaison hors ligne, car la liaison spécifiée pour la partition fait référence à des données de table de faits déjà agrégées dans la partition. Lors de la mise à jour incrémentielle d'une partition déjà traitée par le biais de la commande `Process`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] effectue les actions suivantes :  
  
-   création d'une partition temporaire avec une structure identique à celle de la partition devant faire l'objet d'une mise à jour incrémentielle ;  
  
-   traitement de la partition temporaire en utilisant la liaison hors ligne spécifiée dans la commande `Process` ;  
  
-   fusion de la partition temporaire avec la partition sélectionnée existante.  
  
 Pour plus d’informations sur la fusion de partitions à l’aide d’XML for Analysis (XMLA), consultez [fusion de partitions &#40;&#41;XMLA ](merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>Gestion des erreurs de traitement  
 La propriété [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) de la `Process` commande vous permet de spécifier comment gérer les erreurs rencontrées lors du traitement d’un objet. Par exemple, lors du traitement d'une dimension, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rencontre une valeur en double dans la colonne clé de l'attribut de clé. Du fait que les clés d'attribut doivent être uniques, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ignore les enregistrements en double. Basée sur la propriété [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) de `ErrorConfiguration`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut :  
  
-   ignorer l'erreur et poursuivre le traitement de la dimension ;  
  
-   retourner un message qui indique qu'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a rencontré une clé en double et poursuivre le traitement.  
  
 Pendant l'exécution d'une commande `ErrorConfiguration`, `Process` peut proposer des options dans de nombreuses conditions similaires.  
  
## <a name="managing-writeback-tables"></a>Gestion des tables d'écriture différée  
 Si la commande `Process` rencontre une partition activée en écriture (ou un cube ou un groupe de mesures pour une partition de ce type) qui n'est pas déjà traitée en intégralité, il se peut qu'il n'existe pas encore de table d'écriture différée pour cette partition. La propriété [WriteBackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) de la `Process` commande détermine si [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] doit créer une table d’écriture différée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L'exemple suivant traite entièrement la base de données [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
### <a name="code"></a>Code  
  
```  
<Process xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>Description  
 L’exemple suivant traite de façon incrémentielle la partition **Internet_Sales_2004** dans le groupe de mesures **Internet Sales** du cube **Adventure Works DW** de [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] l' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] exemple de base de données. La `Process` commande ajoute des agrégations pour les dates de commande ultérieures au 31 décembre 2006 à la partition à l’aide d’une liaison de requête hors ligne `Bindings` dans la propriété `Process` de la commande pour récupérer les lignes de la table de faits à partir desquelles générer des agrégations à ajouter à la partition.  
  
### <a name="code"></a>Code  
  
```  
<Process ProcessAffectedObjects="true" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  
