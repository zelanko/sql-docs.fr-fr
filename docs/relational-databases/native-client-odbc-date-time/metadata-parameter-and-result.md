---
title: Métadonnées de paramètre et de résultat | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1f8f04d699c46c654290d1badc26de246a2d9125
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783695"
---
# <a name="metadata---parameter-and-result"></a>Métadonnées - Paramètres et résultats
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette rubrique décrit ce qui est retourné dans les champs de descripteur de paramètre d'implémentation (IPD) et de descripteur de ligne d'implémentation (IRD) pour les types de données de date et d'heure.  
  
## <a name="information-returned-in-ipd-fields"></a>Informations retournées dans les champs IPD  
 Les informations suivantes sont retournées dans les champs IPD :  
  
|Type de paramètre|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**date**|**time**|**smalldatetime** dans IRD, **datetime2** dans IPD|**DateTime** dans IRD, **datetime2** dans IPD|**datetime2**|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|Néant|Néant|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|Néant|  
  
 Il y a parfois des discontinuités dans les plages de valeurs. Par exemple, 9 est manquant dans 8,10.. 6. Cela est dû à l'ajout d'une virgule décimale lorsque la précision fractionnaire est supérieure à zéro.  
  
 **datetime2** est retourné en tant que TypeName pour **smalldatetime** et **DateTime** , car le pilote l’utilise comme type commun pour transmettre toutes les valeurs de **SQL_TYPE_TIMESTAMP** au serveur.  
  
 SQL_CA_SS_VARIANT_SQL_TYPE est un nouveau champ de descripteur. Ce champ a été ajouté à IRD et IPD pour permettre aux applications de spécifier le type de valeur associé aux colonnes et aux paramètres **SQLVARIANT** (SQL_SSVARIANT).  
  
 SQL_CA_SS_SERVER_TYPE est un nouveau champ IPD uniquement destiné à permettre aux applications de contrôler la façon dont les valeurs des paramètres liés comme SQL_TYPE_TYPETIMESTAMP (ou comme SQL_SS_VARIANT avec un type C de SQL_C_TYPE_TIMESTAMP) sont envoyées au serveur. Si SQL_DESC_CONCISE_TYPE est SQL_TYPE_TIMESTAMP (ou si est SQL_SS_VARIANT et que le type C est SQL_C_TYPE_TIMESTAMP) lorsque SQLExecute ou SQLExecDirect est appelé, la valeur de SQL_CA_SS_SERVER_TYPE détermine le type de tabular data stream (TDS) de la valeur de paramètre. , comme suit :  
  
|Valeur de SQL_CA_SS_SERVER_TYPE|Valeurs valides pour SQL_DESC_PRECISION|Valeurs valides pour SQL_DESC_LENGTH|Type TDS|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19, 21..27|**datetime2**|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|**smalldatetime**|  
|SQL_SS_TYPE_DATETIME|3|23|**datetime**|  
  
 Le paramètre par défaut de SQL_CA_SS_SERVER_TYPE est SQL_SS_TYPE_DEFAULT. Les paramètres de SQL_DESC_PRECISION et SQL_DESC_LENGTH sont validés avec le paramètre de SQL_CA_SS_SERVER_TYPE comme décrit dans le tableau ci-dessus. Si cette validation échoue, SQL_ERROR est retourné et un enregistrement de diagnostic est consigné avec SQLState 07006 et le message « Violation de l'attribut de type de données restreint ». Cette erreur est également retournée si SQL_CA_SS_SERVER_TYPE a une valeur autre que SQL_SS_TYPE DEFAULT et que DESC_CONCISE_TYPE n'est pas SQL_TYPE_TIMESTAMP. Ces validations sont effectuées lorsque la validation de cohérence du descripteur a lieu, par exemple :  
  
-   Lorsque SQL_DESC_DATA_PTR est modifié.  
  
-   Au moment de la préparation ou de l'exécution (lorsque SQLExecute, SQLExecDirect, SQLSetPos ou SQLBulkOperations est appelé).  
  
-   Lorsqu’une application force une préparation non différée en appelant SQLPrepare avec la préparation différée désactivée, ou en appelant SQLNumResultCols, SQLDescribeCol ou SQLDescribeParam pour une instruction préparée mais non exécutée.  
  
 Lorsque SQL_CA_SS_SERVER_TYPE est défini par un appel à SQLSetDescField, sa valeur doit être SQL_SS_TYPE_DEFAULT, SQL_SS_TYPE_SMALLDATETIME ou SQL_SS_TYPE_DATETIME. Dans le cas contraire, SQL_ERROR est retourné et un enregistrement de diagnostic est consigné avec SQLState HY092 et le message « Identificateur d'option/attribut non valide ».  
  
 L’attribut SQL_CA_SS_SERVER_TYPE peut être utilisé par les applications qui dépendent des fonctionnalités prises en charge par **DateTime** et **smalldatetime**, mais pas pour **datetime2**. Par exemple, **datetime2** requiert l’utilisation des fonctions **DATEADD** et **datediif** , tandis que **DateTime** et **smalldatetime** autorisent également les opérateurs arithmétiques. La plupart des applications n'auront pas besoin d'utiliser cet attribut et son utilisation doit être évitée.  
  
## <a name="information-returned-in-ird-fields"></a>Informations retournées dans les champs IRD  
 Les informations suivantes sont retournées dans les champs IRD :  
  
|Type de colonne|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8, 10.. 16|16|2|19, 21..27|26, 28..34|  
|SQL_DESC_LITERAL_PREFIX|'|'|'|'|'|'|  
|SQL_DESC_LITERAL_SUFFIX|'|'|'|'|'|'|  
|SQL_DESC_LOCAL_TYPE_NAME|**date**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**date**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>Voir aussi  
 [Métadonnées &#40;ODBC&#41;](https://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
  
  
