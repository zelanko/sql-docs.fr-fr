---
title: Ensemble de lignes MDSCHEMA_PROPERTIES | Documents Microsoft
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
- MDSCHEMA_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_PROPERTIES rowset
ms.assetid: 95c480f7-c525-44ba-a59b-cd36f5855a4f
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7c0e0506be8f531018285bba9145a587448e743e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041899"
---
# <a name="mdschemaproperties-rowset"></a>Ensemble de lignes MDSCHEMA_PROPERTIES
  Décrit les propriétés des membres d'une base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_PROPERTIES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom de la base de données.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Nom du schéma auquel appartient cette propriété. `NULL` si le fournisseur ne prend pas en charge les schémas.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Le nom unique de la dimension. Pour les fournisseurs qui produisent des noms uniques par qualification, chaque composant du nom est délimité.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique de la hiérarchie. Pour les fournisseurs qui produisent des noms uniques par qualification, chaque composant du nom est délimité.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique du niveau auquel appartient cette propriété. Si le fournisseur ne prend pas en charge les niveaux nommés, il doit retourner la valeur `DIMENSION_UNIQUE_NAME` pour ce champ. Pour les fournisseurs qui produisent des noms uniques par qualification, chaque composant du nom est délimité.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique du membre auquel appartient cette propriété. Utilisé pour les magasins de données qui ne prennent pas en charge les niveaux nommés ou qui ont des propriétés sur une base membre-par-membre. Si la propriété s'applique à tous les membres d'un niveau, cette colonne a la valeur `NULL`. Pour les fournisseurs qui produisent des noms uniques par qualification, chaque composant du nom est délimité.|  
|`PROPERTY_TYPE`|`DBTYPE_I2`||Bitmap qui spécifie le type de la propriété :<br /><br /> -   `MDPROP_MEMBER` (`1`) identifie une propriété d’un membre. Cette propriété peut être utilisée dans la clause DIMENSION PROPERTIES de l'instruction SELECT.<br />-   `MDPROP_CELL` (`2`) identifie une propriété d’une cellule. Cette propriété peut être utilisée dans la clause CELL PROPERTIES qui apparaît à la fin de l'instruction SELECT.<br />-   `MDPROP_SYSTEM` (`4`) identifie une propriété interne.<br />-   `MDPROP_BLOB` (`8`) identifie une propriété qui contient un objet binaire volumineux (blob).|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`||Nom de la propriété. Si la clé de la propriété est identique au nom la propriété, `PROPERTY_NAME` reste vide.|  
|`PROPERTY_CAPTION`|`DBTYPE_WSTR`||Étiquette ou légende associée à la propriété, essentiellement à des fins d’affichage. En l'absence de légende, la valeur `PROPERTY_NAME` est retournée.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Type de données de la propriété.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Longueur maximale possible de la propriété, s'il s'agit d'un caractère, d'une donnée binaire ou de type bit.<br /><br /> Zéro indique qu'il n'existe pas de longueur maximale définie.<br /><br /> Retourne `NULL` pour tous les autres types de données.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Longueur maximale possible (en octets) de la propriété, s'il s'agit d'un caractère ou d'une donnée binaire.<br /><br /> Zéro indique qu'il n'existe pas de longueur maximale définie.<br /><br /> Retourne `NULL` pour tous les autres types de données.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Précision maximale de la propriété, s'il s'agit d'un type de données numérique.<br /><br /> Retourne `NULL` pour tous les autres types de données.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Nombre de chiffres situés à droite de la virgule décimale, s'il s'agit d'un type `DBTYPE_NUMERIC` ou `DBTYPE_DECIMAL`.<br /><br /> Retourne `NULL` pour tous les autres types de données.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description explicite de la propriété. `NULL` si aucune description n'existe.|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`||Le type de la propriété. Il peut s'agir de l'une des énumérations suivantes :<br /><br /> -   **MD_PROPTYPE_REGULAR** (`0x00`)<br />-   **MD_PROPTYPE_ID** (`0x01`)<br />-   **MD_PROPTYPE_RELATION_TO_PARENT** (`0x02`)<br />-   **MD_PROPTYPE_ROLLUP_OPERATOR** (`0x03`)<br />-   **MD_PROPTYPE_ORG_TITLE** (`0x11`)<br />-   **MD_PROPTYPE_CAPTION** (`0x21`)<br />-   **MD_PROPTYPE_CAPTION_SHORT** (`0x22`)<br />-   **MD_PROPTYPE_CAPTION_DESCRIPTION** (`0x23`)<br />-   **MD_PROPTYPE_CAPTION_ABREVIATION** (`0x24`)<br />-   **MD_PROPTYPE_WEB_URL** (`0x31`)<br />-   **MD_PROPTYPE_WEB_HTML** (`0x32`)<br />-   **MD_PROPTYPE_WEB_XML_OR_XSL** (`0x33`)<br />-   **MD_PROPTYPE_WEB_MAIL_ALIAS** (`0x34`)<br />-   **MD_PROPTYPE_ADDRESS** (`0x41`)<br />-   **MD_PROPTYPE_ADDRESS_STREET** (`0x42`)<br />-   **MD_PROPTYPE_ADDRESS_HOUSE** (`0x43`)<br />-   **MD_PROPTYPE_ADDRESS_CITY** (`0x44`)<br />-   **MD_PROPTYPE_ADDRESS_STATE_OR_PROVINCE** (`0x45`)<br />-   **MD_PROPTYPE_ADDRESS_ZIP** (`0x46`)<br />-   **MD_PROPTYPE_ADDRESS_QUARTER** (`0x47`)<br />-   **MD_PROPTYPE_ADDRESS_COUNTRY** (`0x48`)<br />-   **MD_PROPTYPE_ADDRESS_BUILDING** (`0x49`)<br />-   **MD_PROPTYPE_ADDRESS_ROOM** (`0x4A`)<br />-   **MD_PROPTYPE_ADDRESS_FLOOR** (`0x4B`)<br />-   **MD_PROPTYPE_ADDRESS_FAX** (`0x4C`)<br />-   **MD_PROPTYPE_ADDRESS_PHONE** (`0x4D`)<br />-   **MD_PROPTYPE_GEO_CENTROID_X** (`0x61`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Y** (`0x62`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Z** (`0x63`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_TOP** (`0x64`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_LEFT** (`0x65`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_BOTTOM** (`0x66`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_RIGHT** (`0x67`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_FRONT** (`0x68`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_REAR** (`0x69`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_POLYGON** (`0x6A`)<br />-   **MD_PROPTYPE_PHYSICAL_SIZE** (`0x71`)<br />-   **MD_PROPTYPE_PHYSICAL_COLOR** (`0x72`)<br />-   **MD_PROPTYPE_PHYSICAL_WEIGHT** (`0x73`)<br />-   **MD_PROPTYPE_PHYSICAL_HEIGHT** (`0x74`)<br />-   **MD_PROPTYPE_PHYSICAL_WIDTH** (`0x75`)<br />-   **MD_PROPTYPE_PHYSICAL_DEPTH** (`0x76`)<br />-   **MD_PROPTYPE_PHYSICAL_VOLUME** (`0x77`)<br />-   **MD_PROPTYPE_PHYSICAL_DENSITY** (`0x78`)<br />-   **MD_PROPTYPE_PERSON_FULL_NAME** (`0x82`)<br />-   **MD_PROPTYPE_PERSON_FIRST_NAME** (`0x83`)<br />-   **MD_PROPTYPE_PERSON_LAST_NAME** (`0x84`)<br />-   **MD_PROPTYPE_PERSON_MIDDLE_NAME** (`0x85`)<br />-   **MD_PROPTYPE_PERSON_DEMOGRAPHIC** (`0x86`)<br />-   **MD_PROPTYPE_PERSON_CONTACT** (`0x87`)<br />-   **MD_PROPTYPE_QTY_RANGE_LOW** (`0x91`)<br />-   **MD_PROPTYPE_QTY_RANGE_HIGH** (`0x92`)<br />-   **MD_PROPTYPE_FORMATTING_COLOR** (`0xA1`)<br />-   **MD_PROPTYPE_FORMATTING_ORDER** (`0xA2`)<br />-   **MD_PROPTYPE_FORMATTING_FONT** (`0xA3`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_EFFECTS** (`0xA4`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_SIZE** (`0xA5`)<br />-   **MD_PROPTYPE_FORMATTING_SUB_TOTAL** (`0xA6`)<br />-   **MD_PROPTYPE_DATE** (`0xB1`)<br />-   **MD_PROPTYPE_DATE_START** (`0xB2`)<br />-   **MD_PROPTYPE_DATE_ENDED** (`0xB3`)<br />-   **MD_PROPTYPE_DATE_CANCELED** (`0xB4`)<br />-   **MD_PROPTYPE_DATE_MODIFIED** (`0xB5`)<br />-   **MD_PROPTYPE_DATE_DURATION** (`0xB6`)<br />-   **MD_PROPTYPE_VERSION** (`0xC1`)|  
|`SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Nom de la propriété utilisé dans les requêtes SQL de la dimension du cube ou de la base de données.|  
|`LANGUAGE`|`DBTYPE_UI2`||Traduction exprimée sous la forme d'un `LCID`. Valide uniquement pour les traductions de propriété.|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`||Identifie le type de hiérarchie auquel s'applique la propriété :<br /><br /> -   `MD_USER_DEFINED` (`1`) indique que la propriété est sur une hiérarchie définie par l’utilisateur<br />-   `MD_SYSTEM_ENABLED` (`2`) indique que la propriété est sur une hiérarchie d’attribut<br />-   `MD_SYSTEM_DISABLED` (`4`) indique que la propriété est sur une hiérarchie d’attribut qui n’est pas activée.|  
|`PROPERTY_ATTRIBUTE_HIERARCHY_NAME`|`DBTYPE_WSTR`||Nom de la hiérarchie d'attributs fournissant la source de la propriété.|  
|`PROPERTY_CARDINALITY`|`DBTYPE_WSTR`||Cardinalité de la propriété. Elle peut prendre les valeurs de chaîne suivantes :<br /><br /> -   `ONE`<br />-   `MANY`|  
|`MIME_TYPE`|`DBTYPE_WSTR`||Type MIME pour les objets BLOB.|  
|`PROPERTY_IS_VISIBLE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si la propriété est visible.<br /><br /> `TRUE` si la propriété est visible ; sinon, `FALSE`.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_PROPERTIES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Obligatoire|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`PROPERTY_TYPE`|`DBTYPE_I2`|Ce paramètre est facultatif|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`|(Facultatif) Une restriction par défaut est en place sur `MDPROP_MEMBER` OU `MDPROP_CELL`.|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`|(Facultatif) Une restriction par défaut est en place sur `MD_USER_DEFINED` OU `MD_SYSTEM_ENABLED`.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -CUBE 1<br />-DIMENSION DE 2<br /><br /> La restriction par défaut est la valeur 1.|  
|`PROPERTY_VISIBILITY`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -1 Visible<br />-2 non visible<br /><br /> La restriction par défaut est la valeur 1.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  