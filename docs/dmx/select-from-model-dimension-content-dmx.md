---
description: Sélectionnez à partir du &lt; modèle &gt; . DIMENSION_CONTENT (DMX)
title: Sélectionnez à partir du &lt; modèle &gt; . DIMENSION_CONTENT (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e3d7bbfcce023ce994f71a5897a1cbf4b0095419
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471997"
---
# <a name="select-from-ltmodelgtdimension_content-dmx"></a>Sélectionnez à partir du &lt; modèle &gt; . DIMENSION_CONTENT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Un modèle d'exploration de données peut être utilisé comme dimension dans un cube OLAP, où chaque nœud du modèle est représenté en tant que membre de la dimension. **Select from \<model> . Dimension_CONTENT** instruction retourne le contenu du modèle qui se rapporte à son utilisation en tant que dimension.  
  
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
  
 *expression*  
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
 [SÉLECTIONNER &#40;&#41;DMX ](../dmx/select-dmx.md)   
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
