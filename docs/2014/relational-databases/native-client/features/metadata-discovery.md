---
title: Découverte des métadonnées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e808f1fc82dfe0a9fd6fa96999e6e2c5320ee452
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63162013"
---
# <a name="metadata-discovery"></a>Découverte des métadonnées
  L'amélioration de découverte des métadonnées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] permet aux applications [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client de s'assurer que les métadonnées de colonne ou de paramètre retournées par l'exécution d'une requête sont identiques ou compatibles avec le format des métadonnées que vous avez spécifié avant l'exécution de la requête. Vous recevrez une erreur si les métadonnées retournées après l'exécution de la requête ne sont pas compatibles avec le format des métadonnées que vous avez spécifié avant l'exécution de la requête.  
  
 Dans les fonctions bcp et ODBC, et dans les interfaces IBCPSession et  IBCPSession2, vous pouvez maintenant spécifier une lecture différée (découverte des métadonnées retardée) pour éviter la découverte de métadonnées pour des opérations de requête. Cela améliore la performance et élimine les échecs de découverte des métadonnées.  
  
 Si vous développez une application à l'aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , mais que vous vous connectez à une version du serveur antérieure à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], les fonctionnalités de découverte des métadonnées correspondront à la version du serveur.  
  
## <a name="remarks"></a>Notes  
 Les fonctions bcp suivantes ont été améliorées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] afin de fournir une fonctionnalité améliorée de découverte des métadonnées :  
  
-   [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 Vous noterez également une amélioration des performances lors de la spécification du format de métadonnées à l'aide de [bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md).  
  
 [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) a un nouveau *eOption* pour contrôler le comportement de bcp_readfmt : `BCPDELAYREADFMT`.  
  
 Les fonctions ODBC suivantes ont été améliorées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] pour fournir une fonctionnalité améliorée de découverte des métadonnées :  
  
-   [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)  
  
 Les fonctions membres OLE DB suivantes ont été améliorées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] pour fournir une fonctionnalité améliorée de découverte des métadonnées :  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters :: GetParameterInfo (pour plus d’informations, consultez [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md) )  
  
 Vous noterez également une amélioration des performances lors de la spécification du format de métadonnées avec IBCPSession::BCPSetBulkMode  
  
 La découverte améliorée des métadonnées  dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est possible grâce à l'ajout de deux procédures stockées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)  
  
  
