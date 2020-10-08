---
description: SQLDescribeParam
title: SQLDescribeParam | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 20463fcf61f5d9842f4e5a84814970c57d4712f3
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809268"
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Pour décrire les paramètres d’une instruction SQL, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client génère et exécute une [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction SELECT lorsque SQLDescribeParam est appelée sur un handle d’instruction ODBC préparé. Les métadonnées du jeu de résultats déterminent les caractéristiques des paramètres dans l'instruction préparée. SQLDescribeParam peut retourner tout code d’erreur que SQLExecute ou SQLExecDirect peut retourner.  
  
 Les améliorations du moteur de base de données qui commencent par [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permettent d’obtenir des descriptions plus précises des résultats attendus. Ces résultats plus précis peuvent différer des valeurs retournées par SQLDescribeParam dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Nouveauté de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , *ParameterSizePtr* retourne maintenant une valeur qui s’aligne sur la définition de la taille, en caractères, de la colonne ou de l’expression du marqueur de paramètre correspondant, tel que défini dans la [spécification ODBC](../../odbc/reference/appendixes/column-size.md). Dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, *ParameterSizePtr* pouvait être la valeur correspondante de **SQL_DESC_OCTET_LENGTH** pour le type, ou une valeur de taille de colonne non pertinente qui a été fournie à SQLBindParameter pour un type, dont la valeur doit être ignorée (**SQL_INTEGER**, par exemple).  
  
 Le pilote ne prend pas en charge l’appel de SQLDescribeParam dans les situations suivantes :  
  
-   Après SQLExecDirect pour les [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions Update ou DELETE contenant la clause from.  
  
-   pour toute instruction ODBC ou [!INCLUDE[tsql](../../includes/tsql-md.md)] contenant un paramètre dans une clause HAVING, ou en comparaison au résultat d'une fonction SUM ;  
  
-   pour toute instruction ODBC ou [!INCLUDE[tsql](../../includes/tsql-md.md)] qui dépend d'une sous-requête contenant des paramètres ;  
  
-   pour les instructions SQL ODBC contenant des marqueurs de paramètre dans les deux expressions d'un prédicat de comparaison, like ou quantifié ;  
  
-   pour les requêtes dans lesquelles l'un des paramètres est un paramètre d'une fonction ;  
  
-   En présence de commentaires (/* \* /) dans la [!INCLUDE[tsql](../../includes/tsql-md.md)] commande.  
  
 Lors du traitement d’un lot d' [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions, le pilote ne prend pas non plus en charge l’appel de SQLDescribeParam pour les marqueurs de paramètres dans les instructions après la première instruction dans le lot.  
  
 Lorsque vous décrivez les paramètres de procédures stockées préparées, SQLDescribeParam utilise la procédure stockée système [sp_sproc_columns](../../relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql.md) pour récupérer les caractéristiques des paramètres. sp_sproc_columns pouvez signaler des données pour les procédures stockées dans la base de données utilisateur active. La préparation d’un nom de procédure stockée complète permet à SQLDescribeParam de s’exécuter sur des bases de données. Par exemple, la procédure stockée système [sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) peut être préparée et exécutée dans n’importe quelle base de données en tant que :  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 L’exécution de SQLDescribeParam après une préparation réussie retourne un ensemble de lignes vide lorsqu’il est connecté à une base de données mais à une base de données **Master**. Le même appel, préparé comme suit, entraîne la aboutissement de SQLDescribeParam, quelle que soit la base de données utilisateur actuelle :  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 Pour les types de données de valeur élevée, la valeur retournée dans *DataTypePtr* est SQL_VARCHAR, SQL_VARBINARY ou SQL_NVARCHAR. Pour indiquer que la taille du paramètre de type de données de valeur élevée est « illimitée », le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC de Native Client définit *ParameterSizePtr* sur 0. Les valeurs de taille réelles sont retournées pour les paramètres **varchar** standard.  
  
> [!NOTE]  
>  Si le paramètre a déjà été lié à une taille maximale pour les paramètres SQL_VARCHAR, SQL_VARBINARY ou SQL_WVARCHAR, la taille liée du paramètre est retournée, et non « illimitée ».  
  
 Pour lier un paramètre d'entrée de taille « illimitée », des données en cours d'exécution doivent être utilisées. Il n’est pas possible de lier un paramètre de sortie de taille « illimité » (il n’existe aucune méthode pour diffuser en continu des données à partir d’un paramètre de sortie, comme [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) pour les jeux de résultats).  
  
 Pour les paramètres de sortie, une mémoire tampon doit être liée et si la valeur est trop grande, la mémoire tampon est remplie et un message SQL_SUCCESS_WITH_INFO est retourné avec l'avertissement « Troncation à droite de la chaîne de données ». Les données tronquées sont alors ignorées.  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>SQLDescribeParam et paramètres table  
 Une application peut récupérer des informations de paramètre table pour une instruction préparée avec SQLDescribeParam. Pour plus d’informations, consultez [métadonnées de paramètre table pour les instructions préparées](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).  
  
 Pour plus d’informations sur les paramètres table en général, consultez [paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLDescribeParam pour les fonctionnalités de date et heure améliorées  
 Les valeurs retournées pour les types date/heure sont les suivantes :  
  
| Attribut | *DataTypePtr* | *ParameterSizePtr* | *DecimalDigitsPtr* |  
| --------- | ------------- | ------------------ | ------------------ |  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|Date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>Prise en charge SQLDescribeParam pour les types CLR volumineux définis par l'utilisateur  
 **SQLDescribeParam** prend en charge les grands types CLR définis par l’utilisateur (UDT). Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLDescribeParam, fonction](../../odbc/reference/syntax/sqldescribeparam-function.md)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
