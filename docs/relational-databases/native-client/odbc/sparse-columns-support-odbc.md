---
description: Prise en charge des colonnes éparses (ODBC)
title: Prise en charge des colonnes éparses (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 35d45a5520b89589633d15b302c1beee92150385
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428111"
---
# <a name="sparse-columns-support-odbc"></a>Prise en charge des colonnes éparses (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Cette rubrique décrit la prise en charge ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client pour les colonnes éparses. Pour obtenir un exemple illustrant la prise en charge d’ODBC pour les colonnes éparses, consultez [appeler SQLColumns sur une table avec des colonnes éparses](../../../relational-databases/native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md). Pour plus d’informations sur les colonnes éparses, consultez [prise en charge des colonnes éparses dans SQL Server Native Client](../../../relational-databases/native-client/features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Métadonnées d'instruction  
 Le champ de descripteur APD (Application Parameter Descriptor) et l'attribut d'instruction SQL_SOPT_SS_NAME_SCOPE acceptent les valeurs supplémentaires SQL_SS_NAME_SCOPE_EXTENDED et SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Ces valeurs spécifient les colonnes qui sont incluses dans le jeu de résultats retourné par [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md). Pour plus d'informations sur SQL_SOPT_SS_NAME_SCOPE, consultez [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Un nouveau descripteur de ligne d'implémentation (IRD, Implementation Row Descriptor), un champ SQLSMALLINT en lecture seule appelé SQL_CA_SS_IS_COLUMN_SET, peut être utilisé pour déterminer si une colonne est une valeur **column_set** XML. SQL_CA_SS_IS_COLUMN_SET prend les valeurs SQL_TRUE et SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Métadonnées de catalogue  
 Deux colonnes spécifiques à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SS_IS_SPARSE et SS_IS_COLUMN_SET) ont été ajoutées au jeu de résultats pour [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>Prise en charge de fonction ODBC pour les colonnes éparses  
 Les fonctions ODBC suivantes ont été mises à jour pour prendre en charge les colonnes éparses dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :  
  
-   [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
