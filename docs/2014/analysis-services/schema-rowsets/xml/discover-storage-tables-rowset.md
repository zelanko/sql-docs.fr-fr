---
title: Ensemble de lignes DISCOVER_STORAGE_TABLES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 13df6f10-8efe-4fe9-83a6-96d108809ed1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bcea65e3ada897e1c6bcd72027ee9d533d95a61e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059299"
---
# <a name="discoverstoragetables-rowset"></a>Ensemble de lignes DISCOVER_STORAGE_TABLES
  Permet au client d'identifier les tables incluses dans une base de données Analysis Services qui fonctionne en mode tabulaire ou SharePoint.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_STORAGE_TABLES` ensemble de lignes contient les colonnes suivantes.  
  
|**Nom de colonne**|**Indicateur de type**|**Longueur**|**Description**|  
|---------------------|------------------------|----------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`||Spécifie le nom de la base de données qui contient les tables.<br /><br /> Le `DISCOVER_STORAGE_TABLES` ensemble de lignes peut être restreint à l’aide de cette colonne. Si cette colonne n'est pas utilisée pour restreindre l'ensemble de lignes, la base de données actuelle est utilisée.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Spécifie le cube ou modèle qui contient les tables.<br /><br /> Le `DISCOVER_STORAGE_TABLES` ensemble de lignes peut être restreint à l’aide de cette colonne.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`||Nom du groupe de mesures.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`||Nom de la partition.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nom de la dimension.|  
|`TABLE_ID`|`DBTYPE_WSTR`||ID de la table utilisée pour stocker les attributs de table.|  
|`TABLE_PARTITIONS_COUNT`|`DBTYPE_ WSTR`||Nombre de partitions de la table.|  
|`HINT_TABLE_TYPE`|`DBTYPE_ WSTR`||Conseil pour le type de table.|  
|`ROWS_COUNT`|`DBTYPE_UI4`||Nombre de lignes dans la partition.|  
|`RIVIOLATION_COUNT`|`DBTYPE_UI4`||Nombre de lignes avec des violations d'intégrité référentielle.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_STORAGE_TABLES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|**Nom de colonne**|**Indicateur de type**|**État de la restriction**|  
|---------------------|------------------------|---------------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant retourne une liste de tables de stockages et le nombre de lignes dans chacune, à partir de la base de données par défaut sur la connexion actuelle.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
