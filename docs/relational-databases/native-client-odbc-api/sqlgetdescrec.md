---
title: SQLGetDescRec - France Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLGetDescRec function
ms.assetid: f3389ff2-f3be-4035-9fb5-c9ebc2f15025
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 42c8a45bb50e5fda8946cc3819aa4702f5c2fb3f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299559"
---
# <a name="sqlgetdescrec"></a>SQLGetDescRec
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ce sujet traite de la fonctionnalité SQLGetDescRec qui est spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="sqlgetdescrec-and-table-valued-parameters"></a>SQLGetDescRec et paramètres table  
 SQLGetDescRec peut être utilisé pour obtenir des valeurs pour les attributs des paramètres de valeur de table et des colonnes de paramètres de valeur de table. Le paramètre *RecNumber* de SQLGetDescRec correspond au *paramètre ParameterNumber* de SQLBindParameter.  
  
 Les colonnes de paramètre table sont disponibles uniquement lorsque le champ d'en-tête de descripteur SQL_SOPT_SS_PARAM_FOCUS est défini sur l'ordinal d'un enregistrement pour lequel SQL_DESC_TYPE a la valeur SQL_SS_TABLE. Pour plus d’informations sur SQL_SOPT_SS_PARAM_FOCUS, voir [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 SQLGetDescRec renvoie les données suivantes :  
  
|Paramètre|Paramètre table|Colonnes de paramètre table et autres paramètres|  
|---------------|-----------------------------|----------------------------------------------------------|  
|*Nom*|Nom de paramètre formel pour un appel de procédure stockée ; sinon, chaîne de longueur 0.|Nom de la colonne de paramètre table.|  
|*TypePtr (typePtr)*|SQL_DESC_TYPE. Pour les paramètres table, il s'agit de SQL_SS_TABLE.|SQL_DESC_TYPE|  
|*SubTypePtr*|Indéfini|SQL_DESC_DATETIME_INTERVAL_CODE (pour les enregistrements de type SQL_DATETIME ou SQL_INTERVAL.)|  
|*LongueurPtr*|0|SQL_DESC_OCTET_LENGTH|  
|*PrecisionPtr (en)*|0|SQL_DESC_PRECISION|  
|*ScalePtr (en)*|0|SQL_DESC_SCALE|  
|*NullablePtr (nullablePtr)*|1|SQL_DESC_NULLABLE|  
  
 Pour plus d’informations sur les paramètres de valeur de table, voir [Paramètres de valeur de la table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-enhanced-date-and-time-features"></a>Prise en charge  par SQLGetDescRec des fonctionnalités de date et heure améliorées  
 Les valeurs retournées pour les types date/heure sont les suivantes :  
  
||*TypePtr (typePtr)*|*SubTypePtr*|*LongueurPtr*|*PrecisionPtr (en)*|*ScalePtr (en)*|  
|-|---------------|------------------|-----------------|--------------------|----------------|  
|DATETIME|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|Date|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Pour plus d’informations, voir [Les améliorations de date et d’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-large-clr-udts"></a>Prise en charge par SQLSetDescRec des grands types CLR définis par l'utilisateur  
 **SQLGetDescRec** prend en charge les grands types définis par les utilisateurs CLR (UDT). Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLGetDescRec](https://go.microsoft.com/fwlink/?LinkId=80707)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
