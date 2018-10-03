---
title: Ensemble de lignes DMSCHEMA_MINING_COLUMNS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_COLUMNS rowset
ms.assetid: ae35ccde-4438-46f4-8611-40b2b1a42fce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2f7d19a29ceb67f83742e19615d9086315b600b6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200699"
---
# <a name="dmschemaminingcolumns-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_COLUMNS
  Décrit les colonnes de tous les modèles d’exploration de données de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Cet ensemble de lignes est limité au catalogue actuel.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DMSCHEMA_MINING_COLUMNS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue. Défini d'après le nom de la base de données dont le modèle est membre.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Nom de schéma non qualifié. Cette colonne n’est pas pris en charge par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; il contient toujours `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Le nom du modèle d’exploration de données. Cette colonne contient le nom du modèle d'exploration de données auquel une colonne est associée ; elle n'est jamais vide.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Nom de la colonne.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||GUID de la colonne. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||ID de propriété de la colonne. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||La position ordinale de la colonne. Les colonnes sont numérotées à partir de 1. Cette colonne contient `NULL` s'il n'existe aucune valeur ordinale stable pour la colonne.|  
|`COLUMN_HAS_DEFAULT`|`DBTYPE_BOOL`||Valeur booléenne qui indique si la colonne possède une valeur par défaut.<br /><br /> `TRUE` si la colonne possède une valeur par défaut ; `FALSE` dans le cas contraire.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||Valeur par défaut de la colonne.<br /><br /> Si la valeur par défaut est la valeur `NULL`, `COLUMN_HASDEFAULT` contient `TRUE` et cette colonne contient `NULL`.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||Masque de bits qui décrit les caractéristiques de la colonne. Le type énuméré `DBCOLUMNFLAGS` spécifie les bits du masque de bits. Cette colonne n'est jamais vide.|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si la colonne autorise la valeur Null.<br /><br /> `FALSE` si la colonne est connue pour ne pas autoriser la valeur Null ; `TRUE` dans le cas contraire.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Indicateur du type de données de la colonne. La liste suivante contient des exemples de types d'indicateurs retournés :<br /><br /> « `TABLE` » retourne `DBTYPE_HCHAPTER`.<br /><br /> « `TEXT` » retourne `DBTYPE_WCHAR`.<br /><br /> « `LONG` » retourne `DBTYPE_I8`.<br /><br /> « `DOUBLE` » retourne `DBTYPE_R8`.<br /><br /> « `DATE` » retourne `DBTYPE_DATE`.|  
|`TYPE_GUID`|`DBTYPE_GUID`||GUID du type de données de la colonne. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `VT_NULL`.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Longueur maximale possible pour une valeur de la colonne. Pour les colonnes de type character, binary ou bit, il s'agit de l'une des valeurs suivantes :<br /><br /> -La longueur maximale de la colonne en caractères, octets ou bits, selon le type de colonne, si une longueur est définie. Par exemple, la longueur maximale d'une colonne `CHAR(5)` dans une table SQL est 5.<br />-La longueur maximale du type de données en caractères, octets ou bits, selon le type de colonne, si la colonne n’a pas une longueur définie.<br />-Zéro (0) si le type de données ni de la colonne a une longueur maximale définie.<br />-   `NULL` pour tous les autres types de colonnes|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Longueur maximale en octets de la colonne, si la colonne est de type character ou binary. La valeur zéro (0) signifie que la colonne ne possède pas de longueur maximale. Cette colonne contient `NULL` pour tous les autres types de colonnes.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Précision maximale de la colonne si son type de données est un type numérique autre que  `VARNUMERIC`.<br /><br /> `NULL` si le type de données de la colonne n'est pas numérique ou est `VARNUMERIC`.<br /><br /> La précision des colonnes dont le type de données est  `DBTYPE_DECIMAL` ou `DBTYPE_NUMERIC` dépend de la définition de la colonne.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Nombre de chiffres situés à droite de la virgule décimale si l'indicateur de type de la colonne est `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC` ou `DBTYPE_VARNUMERIC`. Sinon, cette colonne contient `VT_NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Précision de date/heure (nombre de chiffres dans la portion de fractions de secondes) de la colonne si son type de données est DateTime ou Interval ; sinon, `NULL`.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue dans lequel le jeu de caractères est défini. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Nom de schéma non qualifié dans lequel le jeu de caractères est défini. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Nom du jeu de caractères. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue dans lequel le classement est défini. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Un nom de schéma non qualifié dans lequel le classement est défini. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Nom du classement. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue dans lequel le domaine est défini. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Nom du schéma non qualifié dans lequel le domaine est défini. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Le nom de domaine. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description conviviale de la colonne. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`DISTRIBUTION_FLAG`|`DBTYPE_WSTR`||Description de la distribution statistique de la colonne. Cette colonne contient l'une des valeurs suivantes :<br /><br /> -   "`NORMAL`"<br />-   "`LOG_NORMAL`"<br />-   "`UNIFORM`"|  
|`CONTENT_TYPE`|`DBTYPE_WSTR`||Description du contenu de la colonne. Cette colonne contient l'une des valeurs suivantes :<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-«`DISCRETIZED(`[arguments]`)`»<br />-   "`ORDERED`"<br />-   "`KEY TIME`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY_VARIANCE`"<br />-   "`PROBABILITY_STDEV`"<br />-   `"KEY SEQUENCE`"|  
|`MODELING_FLAG`|`DBTYPE_WSTR`||Liste d'indicateurs délimitée par des virgules. Les indicateurs définis sont les suivants :<br /><br /> -   "`MODEL_EXISTENCE_ONLY`"<br />-   "`REGRESSOR`"<br /><br /> Des indicateurs de modélisation spécifiques des algorithmes peuvent également être contenus dans cette colonne.|  
|`IS_RELATED_TO_KEY`|`DBTYPE_BOOL`||Valeur booléenne qui indique si la colonne est associée à la clé.<br /><br /> `TRUE` si cette colonne est associée à la clé. Si la clé est une colonne unique, le champ `RELATED_ATTRIBUTE` peut éventuellement contenir son nom de colonne.|  
|`RELATED_ATTRIBUTE`|`DBTYPE_WSTR`||Le nom de la colonne cible à laquelle la colonne actuelle est liée ou est une propriété spéciale.|  
|`IS_INPUT`|`DBTYPE_BOOL`||Valeur booléenne qui indique si la colonne est une colonne d'entrée.<br /><br /> `VARIANT_TRUE` s'il s'agit d'une colonne d'entrée.|  
|`IS_PREDICTABLE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si la colonne est prédictible.<br /><br /> `TRUE` si la colonne est prédictible.|  
|`CONTAINING_COLUMN`|`DBTYPE_WSTR`||Nom de la colonne `TABLE` qui contient cette colonne. Cette colonne contient `NULL` si la colonne n'est pas contenue dans une autre colonne.|  
|`PREDICTION_SCALAR_FUNCTIONS`|`DBTYPE_WSTR`||Liste, délimitée par des virgules, de fonctions scalaires pouvant être exécutées sur la colonne.|  
|`PREDICTION_TABLE_FUNCTIONS`|`DBTYPE_WSTR`||Liste, délimitée par des virgules, de fonctions pouvant être appliquées à la colonne. Les fonctions doivent retourner une table. La liste est au format suivant :<br /><br /> `<function name>(<column1> [, <column2>], ...)`<br /><br /> Le format permet à l'application cliente de déterminer la signature (liste de paramètres) de la fonction correspondante.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Valeur booléenne qui indique si la colonne a fait l'objet d'un apprentissage d'un jeu de valeurs possibles.<br /><br /> `TRUE` si la colonne a fait l'objet d'un apprentissage d'un jeu de valeurs possibles.<br /><br /> Contient `FALSE` si la colonne n'est pas remplie.|  
|`PREDICTION_SCORE`|`DBTYPE_R8`||Score du modèle lors de la prédiction de la colonne. Le score est utilisé pour mesurer l'exactitude d'un modèle.|  
|`SOURCE_COLUMN`|`DBTYPE_WSTR`||Nom de la colonne de structure d'exploration de données source correspondant à la colonne d'exploration de données actuelle.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DMSCHEMA_MINING_COLUMNS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
