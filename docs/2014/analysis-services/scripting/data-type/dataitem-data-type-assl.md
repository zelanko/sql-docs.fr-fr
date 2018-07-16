---
title: Type de données DataItem (ASSL) | Microsoft Docs
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
- DataItem Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataItem
helpviewer_keywords:
- DataItem data type
ms.assetid: f4f5155f-9c3d-49a1-a390-a9c734fafbce
caps.latest.revision: 44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2646dcce64672d98d33ecff3575016269379325
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300889"
---
# <a name="dataitem-data-type-assl"></a>Type de données DataItem (ASSL)
  Définit un type de données primitif qui représente les caractéristiques associées aux données d'un élément de données, tel qu'une colonne ou un attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataItem>  
   <DataType>...</DataType>  
   <DataSize>...</DataSize>  
   <MimeType>...</MimeType>  
   <NullProcessing>...</NullProcessing>  
   <Trimming>...</Trimming>  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
      <Collation>...</Collation>  
   <Format>...</Format>  
   <Source>...</Source>  
   <Annotations>...</Annotations>  
</DataItem>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [Collation](../properties/collation-element-assl.md), [DataSize](../properties/datasize-element-assl.md), [DataType](../properties/datatype-element-assl.md), [Format](../properties/format-element-assl.md), [InvalidXmlCharacters](../properties/invalidxmlcharacters-element-assl.md), [MimeType](../properties/mimetype-element-assl.md), [NullProcessing](../properties/nullprocessing-element-assl.md), [Source](../properties/source-element-binding-assl.md), [Trimming](../properties/trimming-element-assl.md)|  
|Éléments dérivés|Voir le tableau dans la section Remarques.|  
  
## <a name="remarks"></a>Notes  
 Le type de données `DataItem` est utilisé pour tous les éléments de données qu'il est possible de lier (par exemple, une mesure, une clé d'attribut et un nom d'attribut). Les détails pertinents, et les valeurs par défaut qui s'appliquent, dépendent de l'utilisation (par exemple, les noms d'attribut doivent être des chaînes).  
  
 Une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] accepte uniquement un certain ensemble de types de données. L'utilisation d'autres résultats de types de données entraîne une erreur plutôt qu'une conversion implicite à l'un des types valides.  
  
 Le tableau suivant répertorie les éléments de type `DataItem`.  
  
|Élément parent|Élément de type `DataItem`|Commentaires|  
|--------------------|----------------------------------|--------------|  
|[AttributeTranslation](../objects/column-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md) ou [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/customrollupcolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md) ou [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/customrolluppropertiescolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md) ou [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/keycolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md), [AttributeBinding](attributebinding-data-type-assl.md) ou [TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/namecolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md) ou [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/skippedlevelscolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md) ou [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/unaryoperatorcolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md) ou [AttributeBinding](attributebinding-data-type-assl.md)|  
|[Mesure](../objects/measure-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|`Source` élément de la `DataItem` doit être de type [RowBinding](rowbinding-data-type-assl.md), [ColumnBinding](binding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), ou [CubeDimensionBinding](dimensionbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[KeyColumn](../objects/keycolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md), [AttributeBinding](attributebinding-data-type-assl.md) ou [InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[KeyColumn](../objects/keycolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[NameColumn](../objects/namecolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/foreignkeycolumn-element-assl.md)|`Source` élément de la `DataItem` doit être de type [ColumnBinding](binding-data-type-assl.md)|  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
