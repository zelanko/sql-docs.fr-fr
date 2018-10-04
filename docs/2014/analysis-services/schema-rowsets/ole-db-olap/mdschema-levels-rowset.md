---
title: Ensemble de lignes MDSCHEMA_LEVELS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_LEVELS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_LEVELS rowset
ms.assetid: 4313e268-33f4-4e99-96d7-2ec26775c580
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9491143a33dbd68ab0f0ea9cb3745f1e784879b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191802"
---
# <a name="mdschemalevels-rowset"></a>Ensemble de lignes MDSCHEMA_LEVELS
  Décrit chaque niveau dans une hiérarchie particulière.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_LEVELS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom du catalogue auquel appartient ce niveau. Valeur `NULL` si le fournisseur ne prend pas en charge les catalogues.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Nom du schéma auquel appartient ce niveau. `NULL` si le fournisseur ne prend pas en charge les schémas.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube auquel appartient ce niveau.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique de la dimension à laquelle appartient ce niveau. Pour les fournisseurs qui produisent des noms uniques par qualification, chaque composant du nom est délimité.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique de la hiérarchie. Si le niveau appartient à plusieurs hiérarchies, il existe une ligne pour chaque hiérarchie dont il fait partie. Pour les fournisseurs qui produisent des noms uniques par qualification, chaque composant du nom est délimité.|  
|`LEVEL_NAME`|`DBTYPE_WSTR`||Nom du niveau.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique du niveau avec caractères d'échappement appropriés.|  
|`LEVEL_GUID`|`DBTYPE_GUID`||Non pris en charge.|  
|`LEVEL_CAPTION`|`DBTYPE_WSTR`||Étiquette ou légende associée à la hiérarchie. Principalement utilisée à des fins d'affichage. Si une légende n’existe pas, `LEVEL_NAME` est retournée.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`||Distance du niveau par rapport à la racine de la hiérarchie. Le niveau de la racine est égal à zéro (`0)`.|  
|`LEVEL_CARDINALITY`|`DBTYPE_UI4`||Nombre de membres du niveau.|  
|`LEVEL_TYPE`|`DBTYPE_I4`||Type de niveau :<br /><br /> -   `MDLEVEL_TYPE_GEO_CONTINENT` (`0x2001`)<br />-   `MDLEVEL_TYPE_GEO_REGION` (`0x2002`)<br />-   `MDLEVEL_TYPE_GEO_COUNTRY` (`0x2003`)<br />-   `MDLEVEL_TYPE_GEO_STATE_OR_PROVINCE` (`0x2004`)<br />-   `MDLEVEL_TYPE_GEO_COUNTY` (`0x2005`)<br />-   `MDLEVEL_TYPE_GEO_CITY` (`0x2006`)<br />-   `MDLEVEL_TYPE_GEO_POSTALCODE` (`0x2007`)<br />-   `MDLEVEL_TYPE_GEO_POINT` (`0x2008`)<br />-   `MDLEVEL_TYPE_ORG_UNIT` (`0x1011`)<br />-   `MDLEVEL_TYPE_BOM_RESOURCE` (`0x1012`)<br />-   **MDLEVEL_TYPE_QUANTITATIVE** (`0x1013`)<br />-   `MDLEVEL_TYPE_ACCOUNT` (`0x1014`)<br />-   `MDLEVEL_TYPE_CUSTOMER` (`0x1021`)<br />-   `MDLEVEL_TYPE_CUSTOMER_GROUP` (`0x1022`)<br />-   `MDLEVEL_TYPE_CUSTOMER_HOUSEHOLD` (`0x1023`)<br />-   `MDLEVEL_TYPE_PRODUCT` (`0x1031`)<br />-   `MDLEVEL_TYPE_PRODUCT_GROUP` (`0x1032`)<br />-   `MDLEVEL_TYPE_SCENARIO` (`0x1015`)<br />-   `MDLEVEL_TYPE_UTILITY` (`0x1016`)<br />-   `MDLEVEL_TYPE_PERSON` (`0x1041`)<br />-   `MDLEVEL_TYPE_COMPANY` (`0x1042`)<br />-   `MDLEVEL_TYPE_CURRENCY_SOURCE` (`0x1051`)<br />-   `MDLEVEL_TYPE_CURRENCY_DESTINATION` (`0x1052`)<br />-   `MDLEVEL_TYPE_CHANNEL` (`0x1061`)<br />-   `MDLEVEL_TYPE_REPRESENTATIVE` (`0x1062`)<br />-   `MDLEVEL_TYPE_PROMOTION` (`0x1071`)|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description du niveau à l'intention des utilisateurs. NULL si aucune description n'existe.|  
|`CUSTOM_ROLLUP_SETTINGS`|`DBTYPE_I4`||Bitmap qui définit les options de cumul personnalisé :<br /><br /> -   `MDLEVELS_CUSTOM_ROLLUP_EXPRESSION` (`0x01`) indique une expression existe pour ce niveau. (Déconseillé)<br />-   `MDLEVELS_CUSTOM_ROLLUP_COLUMN` (`0x02`) indique qu’il existe une colonne de cumul personnalisé pour ce niveau.<br />-   `MDLEVELS_SKIPPED_LEVELS` (`0x04`) indique qu’il existe un niveau ignoré associé avec les membres de ce niveau.<br />-   `MDLEVELS_CUSTOM_MEMBER_PROPERTIES` (`0x08`) indique que les membres du niveau ont des propriétés de membre personnalisées.<br />-   `MDLEVELS_UNARY_OPERATOR` (`0x10`) indique que les membres du niveau ont des opérateurs unaires.|  
|`LEVEL_UNIQUE_SETTINGS`|`DBTYPE_I4`||Image bitmap qui spécifie quelles colonnes contiennent des valeurs uniques, si le niveau ne contient que des membres avec des noms ou des clés uniques. Le fichier Msmd.h définit les constantes de valeur binaire suivantes pour cette image bitmap :<br /><br /> -   `MDDIMENSIONS_MEMBER_KEY_UNIQUE` (`1`)<br />-   `MDDIMENSIONS_MEMBER_NAME_UNIQUE` (`2`)<br /><br /> La clé est toujours unique dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Le nom est unique si le paramètre sur l'attribut est `UniqueInDimension` ou `UniqueInAttribute`|  
|`LEVEL_IS_VISIBLE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si le niveau est visible.<br /><br /> Renvoie toujours True. Si le niveau n'est pas visible, il n'est pas inclus dans l'ensemble de lignes du schéma.|  
|`LEVEL_ORDERING_PROPERTY`|`DBTYPE_WSTR`||ID de l'attribut sur lequel le niveau est trié.|  
|`LEVEL_DBTYPE`|`DBTYPE_I4`||Énumération `DBTYPE` de la colonne des clés de membre utilisée pour l'attribut de niveau.<br /><br /> Null si des clés concaténées sont utilisées comme colonne des clés de membre.|  
|`LEVEL_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Retourne toujours la valeur Null.|  
|`LEVEL_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Représentation SQL des noms de membre du niveau.|  
|`LEVEL_KEY_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Représentation SQL des valeurs de clé des membres du niveau.|  
|`LEVEL_UNIQUE_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Représentation SQL des noms de membre uniques.|  
|`LEVEL_ATTRIBUTE_HIERARCHY_NAME`|`DBTYPE_WSTR`||Nom de la hiérarchie d'attribut fournissant la source du niveau.|  
|`LEVEL_KEY_CARDINALITY`|`DBTYPE_UI2`||Nombre de colonnes dans la clé de niveau.|  
|`LEVEL_ORIGIN`|`DBTYPE_UI2`||Bitmap qui définit comment le niveau a été alimenté :<br /><br /> -   `MD_ORIGIN_USER_DEFINED` identifie les niveaux dans une hiérarchie définie par l’utilisateur.<br />-   `MD_ORIGIN_ATTRIBUTE` identifie les niveaux d’une hiérarchie d’attribut.<br />-   `MD_ORIGIN_KEY_ATTRIBUTE` identifie les niveaux d’une hiérarchie d’attribut de clé.<br />-   `MD_ORIGIN_INTERNAL` identifie les niveaux des hiérarchies d’attributs qui ne sont pas activés.|  
  
 L'ensemble de lignes est trié sur `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_UNIQUE_NAME`, `LEVEL_NUMBER`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_LEVELS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`LEVEL_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`LEVEL_ORIGIN`|`DBTYPE_UI2`|(Facultatif) Une restriction par défaut est appliquée sur `MD_USER_DEFINED` et `MD_SYSTEM_ENABLED`|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -CUBE 1<br />-DIMENSION DE 2<br /><br /> La restriction par défaut est la valeur 1.|  
|`LEVEL_VISIBILITY`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs suivantes :<br /><br /> -1 Visible<br />-2 non visible<br /><br /> La restriction par défaut est la valeur 1.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
