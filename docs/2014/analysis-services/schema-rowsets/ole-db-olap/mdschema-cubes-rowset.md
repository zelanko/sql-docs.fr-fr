---
title: Ensemble de lignes MDSCHEMA_CUBES | Documents Microsoft
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
- MDSCHEMA_CUBES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_CUBES rowset
ms.assetid: 5f1b63d4-aa3f-48c6-b866-7ffd91675044
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0044c9943b2f2819ea216c735f298b7e30de7a3a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142802"
---
# <a name="mdschemacubes-rowset"></a>Ensemble de lignes MDSCHEMA_CUBES
  Décrit la structure des cubes d'une base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_CUBES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom de la base de données.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube ou de la dimension. Les noms de dimension sont précédés d'un symbole dollar ($). **Remarque :** uniquement les administrateurs de serveur et base de données disposent des autorisations pour voir les cubes créés à partir d’une dimension.|  
|`CUBE_TYPE`|`DBTYPE_WSTR`||Type du cube. Les valeurs valides sont :<br /><br /> -   `CUBE`<br />-   `DIMENSION`|  
|`CUBE_GUID`|`DBTYPE_GUID`||Non pris en charge.|  
|`CREATED_ON`|`DBTYPE_DBTIMESTAMP`||Non pris en charge.|  
|`LAST_SCHEMA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Heure du dernier traitement du cube.|  
|`SCHEMA_UPDATED_BY`|`DBTYPE_WSTR`||Non pris en charge.|  
|`LAST_DATA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Heure du dernier traitement du cube.|  
|`DATA_UPDATED_BY`|`DBTYPE_WSTR`||Non pris en charge.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description conviviale du cube.|  
|`IS_DRILLTHROUGH_ENABLED`|`DBTYPE_BOOL`||Valeur booléenne qui retourne toujours True.|  
|`IS_LINKABLE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si un cube peut être utilisé dans un cube lié.|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||Valeur booléenne indiquant si un cube est activé en écriture.|  
|`IS_SQL_ENABLED`|`DBTYPE_BOOL`||Valeur booléenne qui indique si SQL peut être utilisé sur le un cube.|  
|`CUBE_CAPTION`|`DBTYPE_WSTR`||Légende du cube.|  
|`BASE_CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube source s'il s'agit d'un cube de perspective.|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||(Facultatif) Jeu de notes, au format XML.|  
  
 L'ensemble de lignes est trié selon `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_CUBES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -CUBE 1<br />-DIMENSION DE 2<br /><br /> La restriction par défaut est la valeur 1.|  
|`Base Cube_Name`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  