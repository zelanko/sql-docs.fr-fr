---
title: Propriétés communes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- external metadata column properties [Integration Services]
- output properties [Integration Services]
- data types [Integration Services], properties
- input properties [Integration Services]
- component properties [Integration Services]
ms.assetid: 51973502-5cc6-4125-9fce-e60fa1b7b796
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5b20a0d2f47e89070712a4063acba4da0225b85d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66060960"
---
# <a name="common-properties"></a>Propriétés communes
  Les objets de Data Flow dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] le modèle objet ont des propriétés communes et des propriétés personnalisées au niveau du composant, de l’entrée et de la sortie, ainsi que des niveaux de colonne d’entrée et de colonne de sortie. De nombreuses propriétés ont des valeurs en lecture seule qui sont assignées au moment de l'exécution par le moteur de flux de données.  
  
 Cette rubrique répertorie et décrit les propriétés communes des objets de flux de données.  
  
-   [Composants](#components)  
  
-   [Port](#inputs)  
  
-   [Colonnes d’entrée](#inputcolumns)  
  
-   [Sorties](#outputs)  
  
-   [Colonnes de sortie](#outputcolumns)  
  
 Pour plus d'informations sur les propriétés des clients, consultez les rubriques suivantes  
  
-   [Propriétés personnalisées ADO NET](data-flow/ado-net-custom-properties.md)  
  
-   [Propriétés personnalisées de la tâche de contrôle de capture de données modifiées](control-flow/cdc-control-task-custom-properties.md)  
  
-   [Propriétés personnalisées des sources CDC](data-flow/cdc-source-custom-properties.md)  
  
-   [Propriétés personnalisées de la destination d'apprentissage du modèle d'exploration de données](data-flow/data-mining-model-training-destination-custom-properties.md)  
  
-   [Propriétés personnalisées de la destination DataReader](data-flow/datareader-destination-custom-properties.md)  
  
-   [Propriétés personnalisées de la destination de traitement de dimension](data-flow/dimension-processing-destination-custom-properies.md)  
  
-   [Propriétés personnalisées d'Excel](data-flow/excel-custom-properties.md)  
  
-   [Propriétés personnalisées des fichiers plats](data-flow/flat-file-custom-properties.md)  
  
-   [Propriétés personnalisées des destinations ODBC](data-flow/odbc-destination-custom-properties.md)  
  
-   [Propriétés personnalisées des sources ODBC](data-flow/odbc-source-custom-properties.md)  
  
-   [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)Propriétés personnalisées OLE DB  
  
-   [Propriétés personnalisées de la destination de traitement de partition](data-flow/partition-processing-destination-custom-properties.md)  
  
-   [Propriétés personnalisées des fichiers bruts](data-flow/raw-file-custom-properties.md)  
  
-   [Propriétés personnalisées de la destination du jeu d'enregistrements](data-flow/recordset-destination-custom-properties.md)  
  
-   [Propriétés personnalisées de la destination SQL Server Compact Edition](data-flow/sql-server-compact-edition-destination-custom-properties.md)  
  
-   [Propriétés personnalisées de la destination SQL Server](data-flow/sql-server-destination-custom-properties.md)  
  
-   [Propriétés personnalisées des transformations](data-flow/transformations/transformation-custom-properties.md)  
  
-   [Propriétés personnalisées des sources XML](data-flow/xml-source-custom-properties.md)  
  
##  <a name="component-properties"></a><a name="components"></a>Propriétés du composant  
 Dans le modèle objet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], un composant dans le flux de données implémente l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>.  
  
 Le tableau suivant décrit les propriétés des composants dans un flux de données. Certaines propriétés ont des valeurs en lecture seule qui sont assignées au moment de l'exécution par le moteur de flux de données.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|ComponentClassID|String|CLSID du composant.|  
|ContactInfo|String|Informations de contact pour le développeur d'un composant.|  
|Description|String|Description du composant de flux de données. La valeur par défaut de cette propriété est le nom du composant de flux de données.|  
|ID|Integer|Valeur qui identifie de manière unique cette instance du composant.|  
|IdentificationString|String|Identifie le composant.|  
|IsDefaultLocale|Boolean|Indique si le composant utilise les paramètres régionaux de la tâche de flux de données à laquelle il appartient.|  
|LocaleID|Integer|Paramètres régionaux utilisés par le composant de flux de données lors de l'exécution du package. Tous les paramètres régionaux Windows sont disponibles dans les composants de flux de données.|  
|Nom|String|Nom du composant de flux de données.|  
|PipelineVersion|Integer|Version de la tâche de flux de données dans laquelle un composant est destiné à être exécuté.|  
|UsesDispositions|Boolean|Indique si un composant a une sortie d'erreur.|  
|ValidateExternalMetadata|Boolean|Indique si les métadonnées des colonnes externes sont validées. La valeur par défaut de cette propriété est `True`.|  
|Version|Integer|Version d'un composant.|  
  
##  <a name="input-properties"></a><a name="inputs"></a>Propriétés d’entrée  
 Dans le modèle objet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , les transformations et destinations ont des sorties. Une entrée d'un composant dans le flux de données implémente l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>.  
  
 Le tableau suivant décrit les propriétés des entrées de composants dans un flux de données. Certaines propriétés ont des valeurs en lecture seule qui sont assignées au moment de l'exécution par le moteur de flux de données.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|Description|String|Description de l'entrée.|  
|ErrorOrTruncationOperation|String|Chaîne facultative qui spécifie les types d'erreurs ou troncations qui peuvent se produire lors du traitement d'une ligne.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valeur qui spécifie la gestion des erreurs. Ces valeurs sont `Fail component`, `Ignore failure` et `Redirect row`.|  
|HasSideEffects|Boolean|Indique si un composant peut être supprimé du plan d’exécution du workflow lorsqu’il n’est pas attaché à un composant en aval et lorsque `RunInOptimizedMode` a `true`la valeur.|  
|ID|Integer|Valeur qui identifie l'entrée de façon unique.|  
|IdentificationString|String|Chaîne qui identifie l'entrée.|  
|IsSorted|Boolean|Indique si les données dans l'entrée sont triées.|  
|Nom|String|Nom de l'entrée.|  
|SourceLocale|Integer|ID de paramètres régionaux (LCID) des données d'entrée.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valeur qui détermine la façon dont le composant gère les troncations qui se produisent lors du traitement des lignes. . Ces valeurs sont `Fail component`, `Ignore failure` et `Redirect row`.|  
  
 Les destinations et certaines transformations ne prennent pas en charge les sorties d’erreur, et les propriétés ErrorRowDisposition et TruncationRowDisposition de ces composants sont en lecture seule.  
  
###  <a name="input-column-properties"></a><a name="inputcolumns"></a>Propriétés de la colonne d’entrée  
 Dans le modèle objet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , une entrée contient une collection de colonnes d'entrée. Une colonne d'entrée d'un composant dans le flux de données implémente l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInputColumn100>.  
  
 Le tableau suivant décrit les propriétés des colonnes d'entrée de composants dans un flux de données. Certaines propriétés ont des valeurs en lecture seule qui sont assignées au moment de l'exécution par le moteur de flux de données.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|ComparisonFlags|Integer|Ensemble d'indicateurs qui spécifient la comparaison des colonnes ayant un type de données character. Pour plus d'informations, voir [Comparing String Data](data-flow/comparing-string-data.md).|  
|Description|String|Décrit la colonne d'entrée.|  
|ErrorOrTruncationOperation|String|Chaîne facultative qui spécifie les types d'erreurs ou troncations qui peuvent se produire lors du traitement d'une ligne.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valeur qui spécifie la gestion des erreurs. Ces valeurs sont `Fail component`, `Ignore failure` et `Redirect row`.|  
|ExternalMetadataColumnID|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>|ID de la colonne de métadonnées externe assigné à une colonne d'entrée.|  
|ID|Integer|Valeur qui identifie la colonne d'entrée de façon unique.|  
|IdentificationString|String|Chaîne qui identifie la colonne d'entrée.|  
|LineageID|Integer|ID de la colonne en amont.|  
|Nom|String|Nom de la colonne d'entrée.|  
|SortKeyPosition|Integer|Valeur qui indique si une colonne est triée, son ordre de tri et l'ordre dans lequel plusieurs colonnes sont triées. La valeur **0** indique que la colonne n'est pas triée.  Pour plus d’informations, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valeur qui détermine la façon dont le composant gère les troncations qui se produisent lors du traitement des lignes. Ces valeurs sont `Fail component`, `Ignore failure` et `Redirect row`.|  
|UpstreamComponentName|String|Nom du composant en amont.|  
|UsageType|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType>|Valeur qui détermine la façon dont une colonne d'entrée est utilisée par le composant.|  
  
 Les propriétés de type de données des colonnes d'entrée sont également décrites sous « Propriétés du type de données ».  
  
##  <a name="output-properties"></a><a name="outputs"></a>Propriétés de sortie  
 Dans le modèle objet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , les sources et les transformations ont des sorties. Une sortie d'un composant dans le flux de données implémente l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>.  
  
 Le tableau suivant décrit les propriétés des sorties de composants dans un flux de données. Certaines propriétés ont des valeurs en lecture seule qui sont assignées au moment de l'exécution par le moteur de flux de données.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|DeleteOutputOnPathDetached|Boolean|Valeur qui détermine si le moteur de flux de données supprime la sortie lorsqu'elle est détachée d'un chemin d'accès.|  
|Description|String|Décrit la sortie.|  
|ErrorOrTruncationOperation|String|Chaîne facultative qui spécifie les types d'erreurs ou troncations qui peuvent se produire lors du traitement d'une ligne.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valeur qui spécifie la gestion des erreurs. Ces valeurs sont `Fail component`, `Ignore failure` et `Redirect row`.|  
|ExclusionGroup|Integer|Valeur qui identifie un groupe de sorties s'excluant mutuellement.|  
|HasSideEffects|Boolean|Valeur qui indique si un composant peut être supprimé du plan d'exécution du flux de données lorsqu'il n'est pas attaché à un composant en amont et lorsque la propriété `RunInOptimizedMode` a la valeur `true`.|  
|ID|Integer|Valeur qui identifie la sortie de façon unique.|  
|IdentificationString|String|Chaîne qui identifie la sortie.|  
|IsErrorOut|Boolean|Indique si la sortie est une sortie d'erreur.|  
|IsSorted|Boolean|Indique si la sortie est triée. La valeur par défaut est `False`.<br /><br /> ** \* Important \* \* ** La définition de la valeur `IsSorted` de la `True` propriété sur ne trie pas les données. Cette propriété indique uniquement aux composants en aval que les données ont été précédemment triées. Pour plus d’informations, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|Nom|String|Nom de la sortie.|  
|SynchronousInputID|Integer|ID d'une entrée synchrone avec la sortie.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valeur qui détermine la façon dont le composant gère les troncations qui se produisent lors du traitement des lignes. Ces valeurs sont `Fail component`, `Ignore failure` et `Redirect row`.|  
  
###  <a name="output-column-properties"></a><a name="outputcolumns"></a>Propriétés de la colonne de sortie  
 Dans le modèle objet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , une sortie contient une collection de colonnes de sortie. Une colonne de sortie d'un composant dans le flux de données implémente l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100>.  
  
 Le tableau suivant décrit les propriétés des colonnes de sortie de composants dans un flux de données. Certaines propriétés ont des valeurs en lecture seule qui sont assignées au moment de l'exécution par le moteur de flux de données.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|ComparisonFlags|Integer|Ensemble d'indicateurs qui spécifient la comparaison des colonnes ayant un type de données character. Pour plus d'informations, voir [Comparing String Data](data-flow/comparing-string-data.md).|  
|Description|String|Décrit la colonne de sortie.|  
|ErrorOrTruncationOperation|String|Chaîne facultative qui spécifie les types d'erreurs ou troncations qui peuvent se produire lors du traitement d'une ligne.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valeur qui spécifie la gestion des erreurs. Ces valeurs sont `Fail component`, `Ignore failure` et `Redirect row`. La valeur par défaut est `Fail component`.|  
|ExternalMetadataColumnID|Integer|ID de la colonne de métadonnées externe assigné à une colonne d'entrée.|  
|ID|Integer|Valeur qui identifie la colonne de sortie de façon unique.|  
|IdentificationString|String|Chaîne qui identifie la colonne de sortie.|  
|LineageID|Integer|ID de la colonne de sortie. Les composants en aval font référence à la colonne à l'aide de cette valeur.|  
|Nom|String|Nom de la colonne de sortie.|  
|SortKeyPosition|Integer|Valeur qui indique si une colonne est triée, son ordre de tri et l'ordre dans lequel plusieurs colonnes sont triées. La valeur **0** indique que la colonne n'est pas triée. Pour plus d’informations, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|SpecialFlags|Integer|Valeur qui contient les indicateurs spéciaux de la colonne de sortie.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valeur qui détermine la façon dont le composant gère les troncations qui se produisent lors du traitement des lignes. Ces valeurs sont `Fail component`, `Ignore failure` et `Redirect row`. La valeur par défaut est `Fail component`.|  
  
 Les colonnes de sortie incluent également un jeu de propriétés de type de données.  
  
## <a name="external-metadata-column-properties"></a>Propriétés de colonne de métadonnées externe  
 Dans le modèle objet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , les entrées et sorties peuvent contenir une collection de colonnes de métadonnées externes. Une colonne de métadonnées externe d'un composant dans le flux de données implémente l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>.  
  
 Le tableau suivant décrit les propriétés des colonnes de métadonnées externes de composants dans un flux de données. Certaines propriétés ont des valeurs en lecture seule qui sont assignées au moment de l'exécution par le moteur de flux de données.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|Description|String|Décrit la colonne externe.|  
|ID|Integer|Valeur qui identifie la colonne de façon unique.|  
|IdentificationString|String|Chaîne qui identifie la colonne.|  
|Nom|String|Nom de la colonne externe.|  
  
 Les colonnes de métadonnées externes incluent également un jeu de propriétés de type de données.  
  
## <a name="data-type-properties"></a>Propriétés du type de données  
 Les colonnes de sortie et les colonnes de métadonnées externes incluent un jeu de propriétés de type de données. Selon le type de données de la colonne, les propriétés peuvent être en lecture/écriture ou en lecture seule.  
  
 Le tableau suivant décrit les propriétés de type de données des colonnes de sortie et des colonnes de métadonnées externes.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|CodePage|Integer|Spécifie la page de codes pour les données de chaîne qui ne sont pas Unicode.|  
|DataType|Integer (énumération)|Type de données [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] de la colonne. Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).|  
|Longueur|Integer|Longueur d'une colonne en caractères.|  
|Precision|Integer|Précision d'une colonne numérique.|  
|Scale|Integer|Échelle d'une colonne numérique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Transmission de données](data-flow/data-flow.md)   
 [Transformation, propriétés personnalisées](data-flow/transformations/transformation-custom-properties.md)   
 [Propriétés du chemin](../../2014/integration-services/path-properties.md)   
 [Propriétés du flux de données pouvant être définies à l’aide d’expressions](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
