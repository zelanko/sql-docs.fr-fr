---
title: SQLDescribeCol | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 413e8f65cb135a46a7dd440b687beb448e15ede2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789344"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Pour les instructions exécutées, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client n’a pas besoin d’interroger le serveur pour décrire les colonnes d’un jeu de résultats. Dans ce cas, **SQLDescribeCol** n’entraîne pas l’aller-retour d’un serveur. Comme [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)et[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md), l’appel de **SQLDescribeCol** sur des instructions préparées mais non exécutées génère un aller-retour sur le serveur.  
  
 Lorsqu'une instruction ou un lot d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] retourne plusieurs ensembles de lignes de résultats, il est possible qu'une colonne, référencée par un ordinal, ait pour origine une table distincte ou référence une colonne entièrement différente dans le jeu de résultats. **SQLDescribeCol** doit être appelé pour chaque ensemble. Lorsque le jeu de résultats change, l'application doit de nouveau lier les valeurs de données avant d'extraire les résultats de ligne. Pour plus d'informations sur la gestion de plusieurs retours de jeux de résultats, consultez [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Les attributs de colonnes sont signalés uniquement pour le premier jeu de résultats lorsque plusieurs jeux de résultats sont générés par un lot préparé d'instructions SQL.  
  
 Pour les types de données de valeur élevée, la valeur retournée dans *DataTypePtr* est SQL_VARCHAR, SQL_VARBINARY ou SQL_NVARCHAR. La valeur SQL_SS_LENGTH_UNLIMITED dans *ColumnSizePtr* indique que la taille est « illimitée ».  
  
 Les améliorations apportées au moteur de base de données à partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permettent à SQLDescribeCol d’obtenir des descriptions plus précises des résultats attendus. Ces résultats plus précis peuvent différer des valeurs retournées par SQLDescribeCol dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLDescribeCol des fonctionnalités de date et heure améliorées  
 Les valeurs retournées pour les types date/heure sont les suivantes :  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|Date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>Prise en charge par SQLDescribeCol des grands types CLR définis par l'utilisateur  
 **SQLDescribeCol** prend en charge les grands types CLR définis par l’utilisateur (UDT). Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLDescribeCol](https://go.microsoft.com/fwlink/?LinkID=59338)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
