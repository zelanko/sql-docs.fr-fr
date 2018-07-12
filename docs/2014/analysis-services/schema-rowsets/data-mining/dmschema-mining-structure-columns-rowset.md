---
title: Ensemble de lignes DMSCHEMA_MINING_STRUCTURE_COLUMNS | Microsoft Docs
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
- DMSCHEMA_MINING_STRUCTURE_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURE_COLUMNS rowset
ms.assetid: 81f25502-ac90-42f1-8ddf-7b0f9752ebfd
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c98da6f1e843b08fac4b91baabec79ab0d9c341
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171580"
---
# <a name="dmschemaminingstructurecolumns-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_STRUCTURE_COLUMNS
  Décrit les colonnes de toutes les structures d’exploration de données déployées sur un serveur qui est en cours d’exécution [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DMSCHEMA_MINING_STRUCTURE_COLUMNS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`||Nom de schéma non qualifié. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ne prend pas en charge les schémas, par conséquent, cette colonne est toujours `NULL`.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`||Nom de la structure. Cette colonne ne peut pas contenir un `NULL`.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Nom de la colonne. L'unicité est garantie uniquement au sein des colonnes qui partagent le même modèle. Par exemple, deux colonnes imbriquées peuvent porter le même nom si elles appartiennent à deux tables imbriquées distinctes dans la même structure.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||GUID de la colonne. Les fournisseurs qui n'utilisent pas de GUID pour identifier les colonnes doivent retourner `NULL` dans cette colonne.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||ID de propriété de la colonne. Les fournisseurs qui n'associent aucun ID de propriété aux colonnes doivent retourner `NULL` dans cette colonne. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Retourne `NULL` pour cette colonne.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||Valeur ordinale de la colonne. Les colonnes sont numérotées à partir de 1. `NULL` s'il n'existe aucune valeur ordinale stable pour la colonne.|  
|`COLUMN_HASDEFAULT`|`DBTYPE_BOOL`||Valeur booléenne qui indique si cette colonne possède une valeur par défaut.<br /><br /> `TRUE` lorsque la colonne possède une valeur par défaut.<br /><br /> `FALSE` lorsque la colonne ne possède pas de valeur par défaut ou lorsqu'il est impossible de savoir si elle possède une valeur par défaut.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||La valeur par défaut de la colonne. Un fournisseur peut exposer `DBCOLUMN_DEFAULTVALUE` mais pas `DBCOLUMN_HASDEFAULT` (pour les tables ISO) dans l'ensemble de lignes retourné par `IColumnsRowset::GetColumnsRowset`.<br /><br /> Si la valeur par défaut est `NULL`, `COLUMN_HASDEFAULT` correspond à `TRUE` et la colonne `COLUMN_DEFAULT` est une valeur `NULL`.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||-Masque de bits qui décrit les caractéristiques de la colonne. Le type énuméré `DBCOLUMNFLAGS` spécifie les bits du masque de bits. Cette colonne ne peut pas contenir de valeur `NULL`. Les valeurs valides sont les suivantes :<br />-   **DBCOLUMNFLAGS_ISNULLABLE** (`0x20`)<br />-   **DBCOLUMNFLAGS_MAYBENULL** (`0x40`)<br />-   **DBCOLUMNFLAGS_ISLONG** (`0x80`)|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si cette colonne possède une valeur par défaut.<br /><br /> `TRUE` si la colonne peut contenir `NULL` ; `FALSE` dans le cas contraire.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Indicateur du type de données de la colonne. Exemple :<br /><br /> -   "`TABLE`" = `DBTYPE_HCHAPTER`<br />-   "`TEXT`" = `DBTYPE_WCHAR`<br />-   "`LONG`" = `DBTYPE_I8`<br />-   "`DOUBLE`" = `DBTYPE_R8`<br />-   "`DATE`" = `DBTYPE_DATE`|  
|`TYPE_GUID`|`DBTYPE_GUID`||GUID du type de données de la colonne. Les fournisseurs qui n'utilisent pas de GUID pour identifier les types de données doivent retourner `NULL` dans cette colonne.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Longueur maximale possible pour une valeur de la colonne. Pour les colonnes de type character, binary ou bit, il s'agit de l'une des valeurs suivantes :<br /><br /> -La longueur maximale de la colonne en caractères, octets ou bits, respectivement, si la longueur est définie. Par exemple, la longueur maximale d'une colonne `CHAR(5)` dans une table SQL est 5.<br />-La longueur maximale des données type en caractères, octets ou bits, respectivement, si la colonne n’a pas une longueur définie.<br />-Zéro (0) si le type de données ni de la colonne a une longueur maximale définie.<br />-   `NULL` pour tous les autres types de colonnes.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Longueur maximale en octets de la colonne, si la colonne est de type character ou binary. La valeur zéro (0) signifie que la colonne ne possède pas de longueur maximale. `NULL` pour tous les autres types de colonnes.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Précision maximale de la colonne si son type de données est un type numérique autre que `VARNUMERIC` ; `NULL` si son type de données n'est pas numérique ou est `VARNUMERIC`.<br /><br /> La précision des colonnes dont le type de données est `DBTYPE_DECIMAL` ou `DBTYPE_NUM`ERIC dépend de la définition de la colonne.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Nombre de chiffres situés à droite de la virgule décimale si l'indicateur de type de la colonne est `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC` ou `DBTYPE_VARNUMERIC`. Sinon, il s’agit de `NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Précision DateTime (nombre de chiffres dans la partie des fractions de secondes) de la colonne si cette dernière est de type datetime ou interval. Si le type de données de la colonne n'est pas datetime, la valeur est `NULL`.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue dans lequel le jeu de caractères est défini. `NULL` si le fournisseur ne prend pas en charge les catalogues ou plusieurs jeux de caractères.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Le nom de schéma non qualifié dans lequel le jeu de caractères est défini. `NULL` si le fournisseur ne prend pas en charge les schémas ou plusieurs jeux de caractères.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Nom du jeu de caractères. `NULL` si le fournisseur ne prend pas en charge plusieurs jeux de caractères.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue dans lequel le classement est défini. `NULL` si le fournisseur ne prend pas en charge les catalogues ou plusieurs classements.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Nom de schéma non qualifié dans lequel le classement est défini. `NULL` si le fournisseur ne prend pas en charge les schémas ou plusieurs classements.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Nom du classement. `NULL` si le fournisseur ne prend pas en charge plusieurs classements.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue dans lequel le domaine est défini. `NULL` si le fournisseur ne prend pas en charge les catalogues ou les domaines.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Nom du schéma non qualifié dans lequel le domaine est défini. `NULL` si le fournisseur ne prend pas en charge les schémas ou les domaines.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Le nom de domaine. `NULL` si le fournisseur ne prend pas en charge les domaines.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description explicite de la colonne. `NULL` si aucune description n'est associée à la colonne.|  
|`DISTRIBUTION_FLAG`|`DBTYPE_WSTR`||Distribution de la colonne de structure d'exploration de données :<br /><br /> -   "`NORMAL`"<br />-«`LOG_NORM`AL »<br />-   "`UNIFORM`"|  
|`CONTENT_TYPE`|`DBTYPE_WSTR`||Type de contenu de la colonne de structure d'exploration de données :<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-«`DISCRETIZED(`[args]`)`»<br />-   "`ORDERED`"<br />-   "`SEQUENCE_TIME`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY_VARIANCE`"<br />-   "`PROBABILITY_STDEV`"|  
|`MODELING_FLAG`|`DBTYPE_WSTR`||Liste d'indicateurs de modélisation délimitée par des virgules. Le seul indicateur pris en charge pour une colonne de structure est « `NOT NULL` ».|  
|`IS_RELATED_TO_KEY`|`DBTYPE_BOOL`||Valeur booléenne qui indique si cette colonne est associée à la clé.<br /><br /> `VARIANT_TRUE` si cette colonne est associée à la clé ; `VARIANT_FALSE` dans le cas contraire. Si la clé est une colonne unique, le champ `RELATED_ATTRIBUTE` peut contenir son nom de colonne.|  
|`RELATED_ATTRIBUTE`|`DBTYPE_WSTR`||Nom de la colonne cible à laquelle la colonne actuelle est associée ou pour laquelle elle constitue une propriété spéciale.|  
|`CONTAINING_COLUMN`|`DBTYPE_WSTR`||Nom de la colonne `TABLE` contenant cette colonne. `NULL` si aucune table ne contient la colonne.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Valeur booléenne qui indique si cette colonne a appris un jeu de valeurs possibles.<br /><br /> `TRUE` si la colonne a appris un jeu de valeurs possibles ; `FALSE` dans le cas contraire.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes `DMSCHEMA_MINING_STRUCTURE_COLUMNS` peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`|Facultatif.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`|Facultatif.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
