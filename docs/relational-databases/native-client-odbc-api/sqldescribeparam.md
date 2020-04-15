---
title: SQLDescribeParam - France Microsoft Docs
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
ms.openlocfilehash: efe1fdccbef4f5c4a393083f6eb81efee759be5c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302577"
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Pour décrire les paramètres de toute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] déclaration SQL, le conducteur de [!INCLUDE[tsql](../../includes/tsql-md.md)] Native Client ODBC construit et exécute une déclaration SELECT lorsque SQLDescribeParam est appelé sur une poignée de déclaration ODBC préparée. Les métadonnées du jeu de résultats déterminent les caractéristiques des paramètres dans l'instruction préparée. SQLDescribeParam peut retourner n’importe quel code d’erreur que SQLExecute ou SQLExecDirect pourrait retourner.  
  
 Les améliorations apportées au [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] moteur de base de données en commençant par permettent à SQLDescribeParam d’obtenir des descriptions plus précises des résultats attendus. Ces résultats plus précis peuvent différer des valeurs retournées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLDescribeParam dans les versions précédentes de . Pour plus d’informations, consultez [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Également nouveau [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]dans , *ParameterSizePtr* retourne maintenant une valeur qui correspond à la définition de la taille, en caractères, de la colonne ou de l’expression du marqueur de paramètres correspondant tel que défini dans la [spécification ODBC](https://go.microsoft.com/fwlink/?LinkId=207044). Dans les versions précédentes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de Native Client, *ParameterSizePtr* pourrait être la valeur correspondante de **SQL_DESC_OCTET_LENGTH** pour le type, ou une valeur de taille de colonne non pertinente qui a été fournie à SQLBindParameter pour un type, dont la valeur doit être ignorée **(SQL_INTEGER**, par exemple).  
  
 Le conducteur n’est pas en faveur d’appeler SQLDescribeParam dans les situations suivantes:  
  
-   Après SQLExecDirect [!INCLUDE[tsql](../../includes/tsql-md.md)] pour toute mise À JOUR ou DÉLÉT des instructions contenant la clause FROM.  
  
-   pour toute instruction ODBC ou [!INCLUDE[tsql](../../includes/tsql-md.md)] contenant un paramètre dans une clause HAVING, ou en comparaison au résultat d'une fonction SUM ;  
  
-   pour toute instruction ODBC ou [!INCLUDE[tsql](../../includes/tsql-md.md)] qui dépend d'une sous-requête contenant des paramètres ;  
  
-   pour les instructions SQL ODBC contenant des marqueurs de paramètre dans les deux expressions d'un prédicat de comparaison, like ou quantifié ;  
  
-   pour les requêtes dans lesquelles l'un des paramètres est un paramètre d'une fonction ;  
  
-   Lorsqu’il y a \*des commentaires [!INCLUDE[tsql](../../includes/tsql-md.md)] (/) dans la commande.  
  
 Lors du traitement [!INCLUDE[tsql](../../includes/tsql-md.md)] d’un lot de relevés, le conducteur n’est pas non plus en faveur d’appeler SQLDescribeParam pour les marqueurs de paramètres dans les déclarations après la première déclaration dans le lot.  
  
 Lorsqu’il décrit les paramètres des procédures stockées préparées, SQLDescribeParam utilise la procédure stockée [système sp_sproc_columns](../../relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql.md) pour récupérer les caractéristiques des paramètres. sp_sproc_columns pouvez signaler les données pour les procédures stockées dans la base de données utilisateur actuelle. La préparation d’un nom de procédure stockée entièrement qualifié permet à SQLDescribeParam de s’exécuter dans toutes les bases de données. Par exemple, la procédure stockée par le système [sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) peut être préparée et exécutée dans n’importe quelle base de données sous le titre :  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 Exécution SQLDescribeParam après une préparation réussie renvoie un ensemble de rangée vide lorsqu’il est connecté à n’importe quelle base de données, mais **maître**. Le même appel, préparé comme suit, fait réussir SQLDescribeParam quelle que soit la base de données utilisateur actuelle :  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 Pour les types de données à grande valeur, la valeur retournée dans *DataTypePtr* est SQL_VARCHAR, SQL_VARBINARY ou SQL_NVARCHAR. Pour indiquer que la taille du paramètre de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données de grande valeur est « illimitée », le pilote native Client ODBC définit *ParamètresSizePtr* à 0. Les valeurs de taille réelle sont retournées pour les paramètres **de varchar** standard.  
  
> [!NOTE]  
>  Si le paramètre a déjà été lié à une taille maximale pour les paramètres SQL_VARCHAR, SQL_VARBINARY ou SQL_WVARCHAR, la taille liée du paramètre est retournée, et non « illimitée ».  
  
 Pour lier un paramètre d'entrée de taille « illimitée », des données en cours d'exécution doivent être utilisées. Il n’est pas possible de lier un paramètre de sortie de taille « illimité » (il n’existe aucune méthode pour la diffusion des données à partir d’un paramètre de sortie, comme le fait [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) pour les ensembles de résultats).  
  
 Pour les paramètres de sortie, une mémoire tampon doit être liée et si la valeur est trop grande, la mémoire tampon est remplie et un message SQL_SUCCESS_WITH_INFO est retourné avec l'avertissement « Troncation à droite de la chaîne de données ». Les données tronquées sont alors ignorées.  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>SQLDescribeParam et paramètres table  
 Une application peut récupérer des informations de paramètres de valeur de table pour une instruction préparée avec SQLDescribeParam. Pour plus d’informations, voir [Les métadonnées paramètres de valeur de table pour les déclarations préparées](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).  
  
 Pour plus d’informations sur les paramètres de valeur de table en général, voir [Paramètres de valeur de la table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLDescribeParam pour les fonctionnalités de date et heure améliorées  
 Les valeurs retournées pour les types date/heure sont les suivantes :  
  
||*DataTypePtr (en)*|*ParamètresSizePtr*|*DécimaleDigitsPtr*|  
|-|-------------------|------------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|Date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Pour plus d’informations, voir [Les améliorations de date et d’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>Prise en charge SQLDescribeParam pour les types CLR volumineux définis par l'utilisateur  
 **SQLDescribeParam** prend en charge les grands types définis par les utilisateurs CLR (UDT). Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLDescribeParam](https://go.microsoft.com/fwlink/?LinkId=59339)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
