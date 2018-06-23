---
title: Ensemble de lignes DBSCHEMA_COLUMNS | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DBSCHEMA_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_COLUMNS rowset
ms.assetid: 653bdd07-a533-4a99-8b6a-6e5c7322e1f3
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 413e86e156db59e7621c94bdc1c99cd0087a987f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139678"
---
# <a name="dbschemacolumns-rowset"></a>Ensemble de lignes DBSCHEMA_COLUMNS
  Fournit des informations de colonne pour toutes les colonnes qui répondent aux critères de restriction indiqués.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DBSCHEMA_COLUMNS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`||Nom de la base de données.|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`||Non pris en charge.|  
|`TABLE_NAME`|`DBTYPE_WSTR`||Nom du cube.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Nom de la mesure ou de la hiérarchie d'attribut.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||Non pris en charge.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||Non pris en charge.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||Position de la colonne, à partir de 1.|  
|`COLUMN_HAS_DEFAULT`|`DBTYPE_BOOL`||Non pris en charge.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||Non pris en charge.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||Masque de bits `DBCOLUMNFLAGS` indiquant les propriétés de la colonne Consultez « Type d’énuméré DBCOLUMNFLAGS » dans [IColumnsInfo::GetColumnInfo](http://msdn2.microsoft.com/library/ms722704.aspx)|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Retourne toujours `false`.|  
|`DATA_TYPE`|`DBTYPE_WSTR`<br /><br /> `DBTYPE_VARIANT`||Type de données de la colonne. Retourne une chaîne pour les colonnes de dimension et une variante pour les mesures.|  
|`TYPE_GUID`|`DBTYPE_GUID`||Non pris en charge.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Longueur maximale possible d'une valeur de la colonne.<br /><br /> Cette valeur est extraite de la propriété `DataSize` dans l'objet `DataItem`.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Longueur maximale possible d'une valeur de la colonne, en octets, pour les colonnes de type character ou binary.<br /><br /> Une valeur de zéro (0) indique que la colonne ne possède pas de longueur maximale.<br /><br /> La valeur `NULL` est retournée pour les colonnes qui ne retournent pas de type de données binary ou character.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Précision maximale de la colonne pour les types de données numériques autres que `DBTYPE_VARNUMERIC`.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Nombre de chiffres à droite de la virgule décimale pour `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC`, `DBTYPE_VARNUMERIC`. Sinon, c’est `NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Non pris en charge.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Non pris en charge.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Non pris en charge.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Non pris en charge.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Non pris en charge.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Non pris en charge.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Non pris en charge.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Non pris en charge.|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`||Type OLAP de l'objet.<br /><br /> `MEASURE` indique que l'objet est une mesure.<br /><br /> `ATTRIBUTE` indique que l'objet est un attribut de dimension.<br /><br /> `SCHEMA` indique que l'objet est une colonne dans un schéma.|  
  
 L'ensemble de lignes est trié selon `TABLE_CATALOG`, `TABLE_SCHEMA`, `TABLE_NAME`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DBSCHEMA_COLUMNS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`TABLE_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB](ole-db-schema-rowsets.md)  
  
  