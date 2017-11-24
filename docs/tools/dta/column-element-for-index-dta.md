---
title: "Élément de colonne pour les Index (DTA) | Documents Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 557befbb53d96bd0d1b5f862b6df5eeb63670b17
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
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
  
 **Type**: facultatif. Spécifie le type de colonne d'index. Utilisez un type de données **string** pour spécifier cet attribut avec l'une des valeurs autorisées suivantes :  
  
-   **KeyColumn**  
  
     Spécifie que la colonne est référencée par une clé d'index. Utilisez la syntaxe suivante pour définir cet attribut :  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     Pour plus d’informations sur les colonnes clés, consultez [Description des index cluster et non-cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).  
  
-   **IncludedColumn**  
  
     Spécifie que la colonne est une colonne non clé (au lieu d'une colonne clé). Utilisez la syntaxe suivante pour définir cet attribut :  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     Pour plus d’informations sur les colonnes incluses, consultez [Créer des index avec colonnes incluses](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
 **SortOrder**: facultatif. Spécifie l'ordre de tri de la colonne. Utilisez un type de données **string** pour spécifier un ordre de tri **"Ascending"** ou **"Descending"** comme suit :  
  
```  
<Column SortOrder="Ascending">  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Peut spécifié jusqu’à 1 024 colonnes pour l’élément **Index** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Index, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/index-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour les colonnes &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/name-element-for-column-dta.md)|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
