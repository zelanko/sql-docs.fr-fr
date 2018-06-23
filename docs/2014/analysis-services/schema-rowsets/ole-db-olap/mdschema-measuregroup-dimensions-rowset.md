---
title: Ensemble de lignes MDSCHEMA_MEASUREGROUP_DIMENSIONS | Documents Microsoft
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
- MDSCHEMA_MEASUREGROUP_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUP_DIMENSIONS rowset
ms.assetid: c731c06a-7382-4e50-ba0e-d8cee3ab4f28
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f607b966099f71acee460a5a343c557e2a81857e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042310"
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>Ensemble de lignes MDSCHEMA_MEASUREGROUP_DIMENSIONS
  Énumère les dimensions des groupes de mesures.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_MEASUREGROUP_DIMENSIONS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom du catalogue auquel appartient ce groupe de mesures. Valeur `NULL` si le fournisseur ne prend pas en charge les catalogues.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube auquel appartient ce groupe de mesures.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Nom du groupe de mesures.|  
|`MEASUREGROUP_CARDINALITY`|`DBTYPE_WSTR`||Nombre d'instances qu'une mesure dans le groupe de mesures peut avoir pour un membre de dimension unique. Les valeurs possibles sont :<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique de la dimension.|  
|`DIMENSION_CARDINALITY`|`DBTYPE_WSTR`||Nombre d'instances qu'un membre de dimension peut avoir pour une instance unique d'une mesure de groupe de mesures.<br /><br /> Les valeurs possibles sont :<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si les hiérarchies de la dimension sont visibles.<br /><br /> Retourne `TRUE` si une ou plusieurs hiérarchies de la dimension sont visibles ; sinon, `FALSE`.|  
|`DIMENSION_IS_FACT_DIMENSION`|`DBTYPE_BOOL`||Valeur booléenne indiquant si la dimension est une dimension de fait.<br /><br /> Retourne `TRUE` si la dimennsion est une dimension de fait ; sinon, `FALSE`.|  
|`DIMENSION_PATH`|`DBTYPE_HCHAPTER`||Liste de dimensions pour la dimension de référence.|  
|`DIMENSION_GRANULARITY`|`DBTYPE_WSTR`||Nom unique de la hiérarchie de granularité.|  
  
 L'ensemble de lignes prend en charge le tri sur `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `MEASUREGROUP_NAME`, `DIMENSION_UNIQUE_NAME`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_MEASUREGROUP_DIMENSIONS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -1 Visible<br />-2 non visible<br />-Restriction par défaut est une valeur de 1.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  