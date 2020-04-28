---
title: SQLGetDescField | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 341a9fe5c5919093853b0c62c7148515380a0551
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299573"
---
# <a name="sqlgetdescfield"></a>SQLGetDescField
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client expose uniquement les champs de descripteur spécifiques au pilote pour le descripteur de ligne d'implémentation (IRD). Dans le descripteur IRD, les champs de descripteur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont référencés par le biais d'attributs de colonne spécifiques aux pilotes. Pour obtenir une liste complète des champs de descripteur spécifiques au pilote disponibles, consultez [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md).  
  
 Les champs de descripteur qui contiennent des chaînes d'identificateur de colonne sont souvent des chaînes de longueur nulle. Toutes les valeurs des champs de descripteur spécifiques à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sont en lecture seule.  
  
 À l’instar des attributs récupérés avec SQLColAttribute, les champs de descripteur qui signalent des attributs au niveau de la ligne (par exemple SQL_CA_SS_COMPUTE_ID) sont signalés pour toutes les colonnes du jeu de résultats.  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a>SQLGetDescField et paramètres table  
 SQLGetDescField peut être utilisé pour obtenir des valeurs pour les attributs étendus de paramètres table et les colonnes de paramètre table. Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLGetDescField des fonctionnalités de date et heure améliorées  
 Pour plus d'informations sur les champs de descripteur disponibles avec les nouveaux types date/heure, consultez [Parameter and Result Metadata](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
 À compter [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]de, SQLGetDescField peut retourner **SQL_C_SS_TIME2** (pour les types de **temps** ) ou **SQL_C_SS_TIMESTAMPOFFSET** (pour **DateTimeOffset**) au lieu de **SQL_C_BINARY**, si votre application utilise ODBC 3,8.  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a>Prise en charge par SQLGetDescField des types CLR volumineux définis par l'utilisateur  
 **SQLGetDescField** prend en charge les types CLR volumineux définis par l'utilisateur. Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a>Prise en charge par SQLGetDescField des colonnes éparses  
 SQLGetDescField peut être utilisé pour interroger le nouveau champ IRD SQL_CA_SS_IS_COLUMN_SET pour déterminer si une colonne est une colonne **column_set** .  
  
 Pour plus d’informations, consultez la rubrique [prise en charge des colonnes éparses &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="example"></a>Exemple  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQLGetDescField fonction)](https://go.microsoft.com/fwlink/?LinkId=59351)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
