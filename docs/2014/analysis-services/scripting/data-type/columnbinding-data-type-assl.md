---
title: Type de données ColumnBinding (ASSL) | Documents Microsoft
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
- ColumnBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ColumnBinding
helpviewer_keywords:
- ColumnBinding data type
ms.assetid: 3ab1bac1-6716-4b17-a107-d5f9c744c5e6
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1ad7cea5041f8d65964b85e36a0b992f9f5afdae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140623"
---
# <a name="columnbinding-data-type-assl"></a>Type de données ColumnBinding (ASSL)
  Définit un type de données dérivé qui représente la liaison d’une colonne dans une vue de source de données à un [DataItem](dataitem-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ColumnBinding>  
   <!-- The following elements extend Binding -->  
   <TableID>...</TableID>  
      <ColumnID>...</ColumnID>  
</ColumnBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Liaison](binding-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[ColumnID](../properties/columnid-element-eventcolumn-assl.md), [TableID](../properties/id-element-assl.md)|  
|Éléments dérivés|Consultez [de liaison](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Pour créer des noms d’élément XML valides, [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] `DataSet` objets encoder les noms de table pendant la sérialisation vers XML XSD (Schema Definition) ; par exemple, le nom « Order Details » devient « Order_x0020_Details ». De même, les éléments `ColumnID` et `TableID` que contient l'élément `ColumnBinding` et qui font référence à des objets dans la vue de source de données doivent aussi encoder les noms pendant la sérialisation, afin de garantir que les noms correspondent directement au texte figurant dans la vue de source de données. L'instance Analysis Services décodera ces noms, exactement comme le fait le modèle objet `DataSet`.  
  
 Un élément `TableDefinitions` contenu dans un élément employant le type de données `TableBinding` et faisant référence aux tables dans la vue de source de données doit lui aussi encoder les noms lors de leur sérialisation au format XSD. Toutefois, les noms de table figurant dans les liaisons `Partition` ne doivent pas être encodés parce que ces noms sont simplement des noms de tables qui existent dans la base de données et ne doivent pas être dans la vue de source de données. Le fait de ne pas encoder les noms de table dans les liaisons `Partition` a par ailleurs les conséquences suivantes :  
  
-   Ceci permet de simplifier la bibliothèque de définition de données (DDL) des partitions.  
  
-   Il en résulte une cohérence accrue dans la mesure où les partitions peuvent avoir soit un nom de table, soit une instruction SELECT, et l'instruction SELECT ne doit pas être encodée.  
  
 Les noms de table et de colonne n'incluent pas de séparateurs (par exemple « [ » pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [Type de liaison de données &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'élément correspondant dans le modèle objet AMO est <xref:Microsoft.AnalysisServices.ColumnBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  