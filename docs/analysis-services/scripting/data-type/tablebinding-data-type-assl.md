---
title: "Type de données TableBinding (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TableBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TableBinding
helpviewer_keywords:
- TableBinding data type
ms.assetid: 3195dca4-82bf-46b7-a31f-5383586e3573
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 680587b7bd9154cf8f32ecbebe34e68c39e4c04a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="tablebinding-data-type-assl"></a>Type de données TableBinding (ASSL)
  Définit un type de données dérivé représentant une liaison à une table.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<TableBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceID>...</DataSourceID>  
   <DbTableName>...</DbTableName>  
   <DbSchemaName>...</DbSchemaName>  
</TableBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md), [DbSchemaName](../../../analysis-services/scripting/properties/dbschemaname-element-assl.md), [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)|  
|Éléments dérivés|Consultez [de liaison](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Notez que le référencement d'autres tables à l'aide d'une sous-sélection dans l'expression de filtre risque de nuire aux performances dans certaines sources de données. Toutefois, le concepteur peut contrôler totalement l'expression SQL en définissant une requête nommée dans la vue de source de données, puis en faisant référence à cette requête.  
  
 La méthode employée pour définir les liaisons d'une partition est indépendante de l'utilisation de tables partitionnées dans la vue de source de données.  
  
 En guise d'exemple, considérons un groupe de mesures dont la table par défaut, « Sales », contient les colonnes « Date », « Product ID », « Qty », « Price » et « Amount » (montant calculé dans la vue de source de données). Supposons ensuite que la partition « Sales97 » utilise la table « Sales97 » avec le filtre « Year(Sales.Date) = 97 ».  
  
 La requête efficace est la suivante :  
  
```  
SELECT Date, Product ID, Qty, Price, Qty * Price AS Amount   
   FROM Sales97 As Sales  
   WHERE Year(Sales.Date) = 97  
```  
  
 L'expression calculée s'applique encore, même si l'expression a utilisé des noms de table qualifiés (par exemple Sales.Qty). La même règle s’applique si au lieu de cela, la table a été remplacée par une quelconque requête « SELECT... » La clause FROM ci-dessus deviendrait alors « FROM SELECT... Ventes."  
  
 Pour plus d’informations sur la **liaison** type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de type **liaison** et la hiérarchie d’héritage de **liaison** types, consultez [Type de liaison de données &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et liaisons &#40; SSAS multidimensionnel &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de liaison de données &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Sources de données et liaisons &#40; SSAS multidimensionnel &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

