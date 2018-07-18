---
title: Ensemble de lignes DISCOVER_XML_METADATA | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_XML_METADATA
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_XML_METADATA rowset
ms.assetid: 0befd026-db1b-43ac-b0e6-734abb56a4b1
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 616e7c06087fff3d2c2e0388ba44a3e30b200e5f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37214009"
---
# <a name="discoverxmlmetadata-rowset"></a>Ensemble de lignes DISCOVER_XML_METADATA
  Retourne un document XML qui décrit un objet demandé. L'ensemble de lignes qui est retourné se compose toujours d'une ligne et d'une colonne.  
  
 Si vous appelez le [Discover](../../xmla/xml-elements-methods-discover.md) méthode avec le `DISCOVER_XML_METATDATA` valeur d’énumération dans le [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) élément, le `Discover` méthode retourne la `DISCOVER_XML_METATDATA` ensemble de lignes.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes `DISCOVER_XML_METADATA` contient la colonne suivante.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`METADATA`|`DBTYPE_WSTR`||Document XML qui décrit l'objet demandé par la restriction.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
> [!IMPORTANT]  
>  L'ensemble de lignes `DISCOVER_XML_METADATA` ne peut pas être interrogé à l'aide de la syntaxe de commande SELECT. Toutefois, l'ensemble de lignes `DISCOVER_XML_METADATA` peut être interrogé à l'aide de la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_XML_METADATA` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`DatabaseID`|`DBTYPE_WSTR`|Facultatif.|  
|`DimensionID`|`DBTYPE_WSTR`|Facultatif.|  
|`CubeID`|`DBTYPE_WSTR`|Facultatif.|  
|`MeasureGroupID`|`DBTYPE_WSTR`|Facultatif.|  
|`PartitionID`|`DBTYPE_WSTR`|Facultatif.|  
|`PerspectiveID`|`DBTYPE_WSTR`|Facultatif.|  
|`DimensionPermissionID`|`DBTYPE_WSTR`|Facultatif.|  
|`RoleID`|`DBTYPE_WSTR`|Facultatif.|  
|`DatabasePermissionID`|`DBTYPE_WSTR`|Facultatif.|  
|`MiningModelID`|`DBTYPE_WSTR`|Facultatif.|  
|`MiningModelPermissionID`|`DBTYPE_WSTR`|Facultatif.|  
|`DataSourceID`|`DBTYPE_WSTR`|Facultatif.|  
|`MiningStructureID`|`DBTYPE_WSTR`|Facultatif.|  
|`AggregationDesignID`|`DBTYPE_WSTR`|Facultatif.|  
|`TraceID`|`DBTYPE_WSTR`|Facultatif.|  
|`MiningStructurePermissionID`|`DBTYPE_WSTR`|Facultatif.|  
|`CubePermissionID`|`DBTYPE_WSTR`|Facultatif.|  
|`AssemblyID`|`DBTYPE_WSTR`|Facultatif.|  
|`MdxScriptID`|`DBTYPE_WSTR`|Facultatif.|  
|`DataSourceViewID`|`DBTYPE_WSTR`|Facultatif.|  
|`DataSourcePermissionID`|`DBTYPE_WSTR`|Facultatif.|  
|`ObjectExpansion`|`DBTYPE_WSTR`|Facultatif.|  
  
 La restriction, `ObjectExpansion`, est disponible pour chaque objet principal de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Le client utilise généralement des restrictions pour décrire les objets OLAP pour lesquels la DDL doit être retournée, et il utilise la restriction `ObjectExpansion` pour définir le degré d'expansion dans la DDL retournée. Le tableau suivant indique si la valeur d’énumération est autorisée pour [élément Alter &#40;XMLA&#41; ](../../xmla/xml-elements-commands/alter-element-xmla.md) commandes.  
  
|Valeur d'énumération|Description|  
|-----------------------|-----------------|  
|`ReferenceOnly`|Retourne uniquement le nom/ID/horodatage/état demandé pour les objets demandés et tous les objets principaux descendants.|  
|`ObjectProperties`|Développe l'objet demandé sans référence aux objets qu'il contient (inclut les objets secondaires contenus développés).|  
|`ExpandObject`|Identique à *ObjectProperties*, mais retourne également le nom, l'ID et l'horodateur pour les objets principaux contenus.|  
|`ExpandFull`|Développe entièrement l'objet demandé de manière récursive jusqu'au bas de chaque objet qu'il contient.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  
