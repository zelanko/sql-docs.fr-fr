---
title: Ensemble de lignes DISCOVER_STORAGE_TABLES | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 13df6f10-8efe-4fe9-83a6-96d108809ed1
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 51b5bd319480be4c7757d4fb642859af54f209a3
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="discoverstoragetables-rowset"></a>Ensemble de lignes DISCOVER_STORAGE_TABLES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Permet au client d'identifier les tables incluses dans une base de données Analysis Services qui fonctionne en mode tabulaire ou SharePoint.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_STORAGE_TABLES** contient les colonnes suivantes.  
  
|**Nom de colonne**|**Indicateur de type**|**Longueur**|**Description**|  
|---------------------|------------------------|----------------|---------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**||Spécifie le nom de la base de données qui contient les tables.<br /><br /> L'ensemble de lignes **DISCOVER_STORAGE_TABLES** peut être restreint à l'aide de cette colonne. Si cette colonne n'est pas utilisée pour restreindre l'ensemble de lignes, la base de données actuelle est utilisée.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Spécifie le cube ou modèle qui contient les tables.<br /><br /> L'ensemble de lignes **DISCOVER_STORAGE_TABLES** peut être restreint à l'aide de cette colonne.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**||Nom du groupe de mesures.|  
|**PARTITION_NAME**|**DBTYPE_WSTR**||Nom de la partition.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Nom de la dimension.|  
|**TABLE_ID**|**DBTYPE_WSTR**||ID de la table utilisée pour stocker les attributs de table.|  
|**TABLE_PARTITIONS_COUNT**|**DBTYPE_ WSTR**||Nombre de partitions de la table.|  
|**HINT_TABLE_TYPE**|**DBTYPE_ WSTR**||Conseil pour le type de table.|  
|**ROWS_COUNT**|**DBTYPE_UI4**||Nombre de lignes dans la partition.|  
|**RIVIOLATION_COUNT**|**DBTYPE_UI4**||Nombre de lignes avec des violations d'intégrité référentielle.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_STORAGE_TABLES** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|**Nom de colonne**|**Indicateur de type**|**État de la restriction**|  
|---------------------|------------------------|---------------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif|  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant retourne une liste de tables de stockages et le nombre de lignes dans chacune, à partir de la base de données par défaut sur la connexion actuelle.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma de Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
