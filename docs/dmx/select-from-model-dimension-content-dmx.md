---
title: SELECT FROM &lt;modèle&gt;. DIMENSION_CONTENT (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 29f730f0bdff985ffceb849c429e5d1b02f70d5f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992623"
---
# <a name="select-from-ltmodelgtdimensioncontent-dmx"></a>SELECT FROM &lt;modèle&gt;. DIMENSION_CONTENT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Un modèle d'exploration de données peut être utilisé comme dimension dans un cube OLAP, où chaque nœud du modèle est représenté en tant que membre de la dimension. **SELECT FROM \<modèle >. Dimension_CONTENT** instruction retourne le contenu du modèle qui se rapporte à son utilisation en tant que dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste séparée par des virgules des identificateurs des colonnes associées dérivés de l'ensemble de lignes de schéma de contenu.  
  
 *model*  
 Identificateur du modèle  
  
 *expression de condition*  
 Facultatif. Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Les fournisseurs des algorithmes définissent le contenu à retourner et son mode d'organisation. Par exemple, le fournisseur peut limiter le nombre de nœuds décrits dans le contenu de la dimension.  
  
 Le tableau ci-dessous répertorie les colonnes dont le contenu de dimension peut être interrogé, et la fonction que chaque colonne effectue en tant que dimension d'exploration de données.  
  
|Colonne de l'ensemble de lignes CONTENT|Fonction dans la dimension d'exploration de données|  
|---------------------------|---------------------------------------|  
|ATTRIBUTE_NAME|Propriété de membre|  
|NODE_NAME|Propriété de membre|  
|NODE_UNIQUE_NAME|Attribut de clé.|  
|NODE_TYPE|Propriété de membre|  
|NODE_CAPTION|CaptionColumn de **clé** attribut.|  
|CHILDREN_CARDINALITY|Propriété de membre|  
|PARENT_UNIQUE_NAME|Relatedattribut de le **clé** attribut (ParentAttribute dans la hiérarchie parent-enfant).|  
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
 [SÉLECTIONNEZ &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
