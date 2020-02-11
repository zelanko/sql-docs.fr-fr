---
title: Sélectionnez à &lt;partir&gt;du modèle. DIMENSION_CONTENT (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7fac89454cd31c1334e41d4c2367143f31476e20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928366"
---
# <a name="select-from-ltmodelgtdimension_content-dmx"></a>Sélectionnez à &lt;partir&gt;du modèle. DIMENSION_CONTENT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Un modèle d'exploration de données peut être utilisé comme dimension dans un cube OLAP, où chaque nœud du modèle est représenté en tant que membre de la dimension. **> de modèle \<Select from Model. Dimension_CONTENT** instruction retourne le contenu du modèle qui se rapporte à son utilisation en tant que dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste séparée par des virgules des identificateurs des colonnes associées dérivés de l'ensemble de lignes de schéma de contenu.  
  
 *model*  
 Identificateur du modèle  
  
 *expression de condition*  
 facultatif. Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *formule*  
 facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Les fournisseurs des algorithmes définissent le contenu à retourner et son mode d'organisation. Par exemple, le fournisseur peut limiter le nombre de nœuds décrits dans le contenu de la dimension.  
  
 Le tableau ci-dessous répertorie les colonnes dont le contenu de dimension peut être interrogé, et la fonction que chaque colonne effectue en tant que dimension d'exploration de données.  
  
|Colonne de l'ensemble de lignes CONTENT|Fonction dans la dimension d'exploration de données|  
|---------------------------|---------------------------------------|  
|ATTRIBUTE_NAME|Propriété de membre|  
|NODE_NAME|Propriété de membre|  
|NODE_UNIQUE_NAME|Attribut de clé.|  
|NODE_TYPE|Propriété de membre|  
|NODE_CAPTION|CaptionColumn pour l’attribut de **clé** .|  
|CHILDREN_CARDINALITY|Propriété de membre|  
|PARENT_UNIQUE_NAME|RelatedAttribut pour l’attribut de **clé** (ParentAttribute dans la hiérarchie parent-enfant).|  
|NODE_DESCRIPTION|Propriété de membre|  
|NODE_RULE|Propriété de membre|  
|MARGINAL_RULE|Propriété de membre|  
|NODE_PROBABILITY|Propriété de membre|  
|MARGINAL_PROBABILITY|Propriété de membre|  
|NODE_SUPPORT|Propriété de membre|  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L'exemple sélectionne toutes les colonnes du contenu du modèle `[TM Decision Tree]` qui se rapportent à l'utilisation du modèle en tant que dimension.  
  
### <a name="code"></a>Code  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNER &#40;&#41;DMX](../dmx/select-dmx.md)   
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
