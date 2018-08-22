---
title: Prise en charge des colonnes éparses (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d50666d333a77f4a1e2188ac911d0866395b4cc9
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395051"
---
# <a name="sparse-columns-support-odbc"></a>Prise en charge des colonnes éparses (ODBC)
  Cette rubrique décrit la prise en charge ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client pour les colonnes éparses. Pour un exemple illustrant la prise en charge ODBC pour les colonnes éparses, consultez [appeler le SQLColumns sur une Table avec des colonnes éparses](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md). Pour plus d’informations sur les colonnes éparses, consultez [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Métadonnées d'instruction  
 Le champ de descripteur APD (Application Parameter Descriptor) et l'attribut d'instruction SQL_SOPT_SS_NAME_SCOPE acceptent les valeurs supplémentaires SQL_SS_NAME_SCOPE_EXTENDED et SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Ces valeurs spécifient les colonnes qui sont incluses dans le jeu de résultats retourné par [SQLColumns](../../native-client-odbc-api/sqlcolumns.md). Pour plus d’informations sur SQL_SOPT_SS_NAME_SCOPE, consultez [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).  
  
 Un nouveau descripteur de ligne d'implémentation (IRD, Implementation Row Descriptor), un champ SQLSMALLINT en lecture seule appelé SQL_CA_SS_IS_COLUMN_SET, peut être utilisé pour déterminer si une colonne est une valeur `column_set` XML. SQL_CA_SS_IS_COLUMN_SET prend les valeurs SQL_TRUE et SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Métadonnées de catalogue  
 Deux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des colonnes spécifiques (SS_IS_SPARSE et SS_IS_COLUMN_SET) ont été ajoutés au jeu de résultats pour [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>Prise en charge de fonction ODBC pour les colonnes éparses  
 Les fonctions ODBC suivantes ont été mises à jour pour prendre en charge les colonnes éparses dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :  
  
-   [SQLColAttribute](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
