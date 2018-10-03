---
title: Type de données TableBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- TableBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableBinding
helpviewer_keywords:
- TableBinding data type
ms.assetid: 3195dca4-82bf-46b7-a31f-5383586e3573
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab697a42fa489152801a98fb9791fcd657bc5762
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059513"
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
|Types de données de base|[TabularBinding](binding-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[DataSourceID](../properties/id-element-assl.md), [DbSchemaName](../properties/name-element-assl.md), [DbTableName](../properties/dbtablename-element-assl.md)|  
|Éléments dérivés|Consultez [de liaison](binding-data-type-assl.md)|  
  
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
  
 L'expression calculée s'applique encore, même si l'expression a utilisé des noms de table qualifiés (par exemple Sales.Qty). Il en irait de même si, à la place, la table était remplacée par une quelconque requête « SELECT... » : la clause FROM ci-dessus deviendrait alors « FROM SELECT ... Ventes."  
  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de type `Binding` et la hiérarchie d’héritage de `Binding` types, consultez [Type de données de liaison &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données de liaison &#40;ASSL&#41;](binding-data-type-assl.md)   
 [Sources de données et liaisons &#40;SSAS multidimensionnel&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
