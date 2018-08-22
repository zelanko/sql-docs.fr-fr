---
title: Découverte des métadonnées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d26329d11885061b01e6147f145ce42a2a8855b
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396507"
---
# <a name="metadata-discovery"></a>Découverte des métadonnées
  L’amélioration de découverte de métadonnées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] permet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les applications clientes natives pour vous assurer que les métadonnées colonne ou du paramètre retournée à partir de l’exécution d’une requête soient identique à ou compatibles avec les métadonnées que vous avez spécifié avant de mettre en forme vous avez exécuté la requête. Vous recevrez une erreur si les métadonnées retournées après l'exécution de la requête ne sont pas compatibles avec le format des métadonnées que vous avez spécifié avant l'exécution de la requête.  
  
 Dans les fonctions bcp et ODBC, et dans les interfaces IBCPSession et  IBCPSession2, vous pouvez maintenant spécifier une lecture différée (découverte des métadonnées retardée) pour éviter la découverte de métadonnées pour des opérations de requête. Cela améliore la performance et élimine les échecs de découverte des métadonnées.  
  
 Si vous développez une application à l’aide [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] mais de vous connecter à une version de serveur antérieure à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], découverte de métadonnées fonctionnalité correspondront à la version du serveur.  
  
## <a name="remarks"></a>Notes  
 Les fonctions bcp suivantes ont été améliorées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] afin de fournir une fonctionnalité améliorée de découverte des métadonnées :  
  
-   [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 Vous verrez également une amélioration des performances lors de la spécification de format de métadonnées à l’aide [bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md).  
  
 [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) dispose d’un nouveau *eOption* pour contrôler le comportement de bcp_readfmt : `BCPDELAYREADFMT`.  
  
 Les fonctions ODBC suivantes ont été améliorées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] pour fournir une fonctionnalité améliorée de découverte des métadonnées :  
  
-   [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)  
  
 Les fonctions membres OLE DB suivantes ont été améliorées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] pour fournir une fonctionnalité améliorée de découverte des métadonnées :  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (consultez [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md) pour plus d’informations)  
  
 Vous noterez également une amélioration des performances lors de la spécification du format de métadonnées avec IBCPSession::BCPSetBulkMode  
  
 La découverte améliorée des métadonnées  dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est possible grâce à l'ajout de deux procédures stockées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] :  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)  
  
  
