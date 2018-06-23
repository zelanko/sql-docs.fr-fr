---
title: Ensemble de lignes MDSCHEMA_DIMENSIONS | Documents Microsoft
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
- MDSCHEMA_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_DIMENSIONS rowset
ms.assetid: a0fd94bb-359a-4df6-93a6-d60d50223944
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b00b617adf90e1dba8eac94a9872ce07c0773e7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040760"
---
# <a name="mdschemadimensions-rowset"></a>Ensemble de lignes MDSCHEMA_DIMENSIONS
  Décrit les dimensions partagées et privées dans une base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes `MDSCHEMA_DIMENSIONS` contient les colonnes suivantes :  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom de la base de données.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nom de la dimension. Si une dimension appartient à plusieurs cubes ou groupes de mesures, il existe une ligne pour chaque combinaison unique de dimension, groupe de mesures et cube.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Le nom unique de la dimension.|  
|`DIMENSION_GUID`|`DBTYPE_GUID`||Non pris en charge.|  
|`DIMENSION_CAPTION`|`DBTYPE_WSTR`||Légende de la dimension. Celle-ci doit être utilisée lors de l'affichage du nom de la dimension à l'utilisateur, par exemple dans l'interface utilisateur ou les rapports.|  
|`DIMENSION_ORDINAL`|`DBTYPE_UI4`||Position de la dimension dans le cube.|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||Type de la dimension. Les valeurs valides sont les suivantes :<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`DIMENSION_CARDINALITY`|`DBTYPE_UI4`||Spécifie le nombre de membres dans l'attribut de clé.|  
|`DEFAULT_HIERARCHY`|`DBTYPE_WSTR`||Hiérarchie à partir de la dimension. Conservée pour la compatibilité ascendante.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description conviviale de la dimension.|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||A toujours la valeur `FALSE`.|  
|`IS_READWRITE`|`DBTYPE_BOOL`||Valeur booléenne indiquant si la dimension est activée en écriture.<br /><br /> `TRUE` si la dimension est activée en écriture.|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||Image bitmap qui spécifie quelles colonnes contiennent des valeurs uniques si la dimension ne contient que des membres possédant un nom unique. Les constantes de valeur binaire suivantes sont définies dans Msmd.pour cette image bitmap :<br /><br /> -   `MDDIMENSIONS_MEMBER_KEY_UNIQUE`|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||A toujours la valeur `NULL`.|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||A toujours la valeur `TRUE`. **Remarque :** une dimension n’est pas visible, sauf si un ou plusieurs hiérarchies de la dimension sont visibles.|  
  
 L'ensemble de lignes est trié sur `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_NAME`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_DIMENSIONS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -CUBE 1<br />-DIMENSION DE 2<br /><br /> La restriction par défaut est la valeur 1.|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -1 Visible<br />-2 non visible<br /><br /> La restriction par défaut est la valeur 1.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  