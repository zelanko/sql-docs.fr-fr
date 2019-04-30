---
title: Élément de colonne pour les Index (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef7972014dff498172b9c016b3a7debb79a054fa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149847"
---
# <a name="column-element-for-index-dta"></a>Column, élément pour les index (Assistant Paramétrage de base de données)
  Spécifie les colonnes sur lesquelles l'index est créé pour une configuration spécifiée par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribut de colonne|Description|  
|----------------------|-----------------|  
|`Type`|Facultatif. Spécifie le type de colonne d'index. Utilisez un type de données **string** pour spécifier cet attribut avec l'une des valeurs autorisées suivantes :<br /><br /> `KeyColumn`:<br />                  Spécifie que la colonne est référencée par une clé d'index. Utilisez la syntaxe suivante pour définir cet attribut :<br />`<Column Type="KeyColumn">`<br />Pour plus d’informations sur les colonnes clés, consultez [Description des index cluster et non-cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).<br /><br /> `IncludedColumn`: Spécifie que la colonne est une colonne non clé (au lieu d'une colonne clé). Utilisez la syntaxe suivante pour définir cet attribut :<br />`<Column Type="IncludedColumn">`<br />Pour plus d’informations sur les colonnes incluses, consultez [Créer des index avec colonnes incluses](../../relational-databases/indexes/create-indexes-with-included-columns.md).|  
|`SortOrder`|Facultatif. Spécifie l'ordre de tri de la colonne. Utilisez un type de données **string** pour spécifier un ordre de tri **"Ascending"** ou **"Descending"** comme suit :<br /><br /> `<Column SortOrder="Ascending">`|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Peut spécifié jusqu'à 1 024 colonnes pour l'élément `Index`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Index, élément &#40;Assistant Paramétrage de base de données&#41;](index-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour les colonnes &#40;Assistant Paramétrage de base de données&#41;](name-element-for-column-dta.md)|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
