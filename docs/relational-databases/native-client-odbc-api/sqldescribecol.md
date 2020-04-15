---
title: SQLDescribeCol - France Microsoft Docs
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
ms.openlocfilehash: e0e9a03b2e8635618afbdc615a6f77dfe05c533e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302576"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Pour les déclarations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécutées, le pilote native Client ODBC n’a pas besoin de demander au serveur de décrire des colonnes dans un ensemble de résultats. Dans ce cas, **SQLDescribeCol** ne provoque pas un aller-retour serveur. Comme [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)et[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md), appelant **SQLDescribeCol** sur des déclarations préparées mais non exécutées génère un aller-retour serveur.  
  
 Lorsqu'une instruction ou un lot d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] retourne plusieurs ensembles de lignes de résultats, il est possible qu'une colonne, référencée par un ordinal, ait pour origine une table distincte ou référence une colonne entièrement différente dans le jeu de résultats. **SQLDescribeCol** devrait être appelé pour chaque ensemble. Lorsque le jeu de résultats change, l'application doit de nouveau lier les valeurs de données avant d'extraire les résultats de ligne. Pour plus d'informations sur la gestion de plusieurs retours de jeux de résultats, consultez [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Les attributs de colonnes sont signalés uniquement pour le premier jeu de résultats lorsque plusieurs jeux de résultats sont générés par un lot préparé d'instructions SQL.  
  
 Pour les types de données à grande valeur, la valeur retournée dans *DataTypePtr* est SQL_VARCHAR, SQL_VARBINARY ou SQL_NVARCHAR. Une valeur de SQL_SS_LENGTH_UNLIMITED dans *ColumnSizePtr* indique que la taille est «illimitée».  
  
 Les améliorations apportées au [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] moteur de base de données en commençant par permettent à SQLDescribeCol d’obtenir des descriptions plus précises des résultats escomptés. Ces résultats plus précis peuvent différer des valeurs retournées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLDescribeCol dans les versions précédentes de . Pour plus d’informations, consultez [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLDescribeCol des fonctionnalités de date et heure améliorées  
 Les valeurs retournées pour les types date/heure sont les suivantes :  
  
||*DataTypePtr (en)*|*ColumnSizePtr*|*DécimaleDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|Date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Pour plus d’informations, voir [Les améliorations de date et d’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>Prise en charge par SQLDescribeCol des grands types CLR définis par l'utilisateur  
 **SQLDescribeCol** prend en charge les grands types définis par les utilisateurs CLR (UDT). Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLDescribeCol](https://go.microsoft.com/fwlink/?LinkID=59338)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
