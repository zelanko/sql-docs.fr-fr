---
title: Fonctions de copie en bloc | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6bee3ca51a46559231242188835ff1b75624cb68
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73782057"
---
# <a name="sql-server-driver-extensions---bulk-copy-functions"></a>Extensions de pilote SQL Server - Fonctions de copie en bloc
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Open Database Connectivity (ODBC) est une interface de programmation d'applications Microsoft Win32 utilisée par les applications pour accéder aux données dans des sources de données ODBC. La référence de pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ne documente pas tous les appels de fonction ODBC. Seules les fonctions qui ont des paramètres ou des comportements spécifiques au pilote en cas d'utilisation avec le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sont discutées.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est conforme avec la spécification ODBC 3.51. Pour obtenir une référence complète sur ODBC 3,51, téléchargez le kit de développement logiciel (SDK) Microsoft Data Access Components à partir du [Centre de développement accès et stockage des données](https://go.microsoft.com/fwlink?linkid=4173), ou consultez le guide [de référence du programmeur ODBC](https://go.microsoft.com/fwlink/?LinkId=45250) en ligne.  
 
 L'extension API de copie en bloc du pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet aux applications clientes d'ajouter rapidement des lignes de données à une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'en extraire.  Lorsque vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, vous pouvez faire référence aux fonctions de copie en bloc (BCP) dans SQLNCLI11.LIB et SQLNCLI.H.  
  
 Toute application qui utilise une fonction API de copie en bloc (BCP) doit être liée à la bibliothèque (.lib) fournie avec le pilote (.dll) utilisé par l'application. Une application BCP ne doit pas être liée à plus d'une bibliothèque de pilote.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)  
  
-   [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)  
  
-   [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)  
  
-   [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)  
  
-   [bcp_colptr](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md)  
  
-   [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)  
  
-   [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)  
  
-   [bcp_getcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_gettypename](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-gettypename.md)  
  
-   [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)  
  
-   [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)  
  
-   [bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)  
  
-   [bcp_setbulkmode](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)  
  
-   [bcp_setcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
-   [bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions du pilote SQL Server](https://msdn.microsoft.com/library/1043bc93-965d-4939-bd1c-21e9d8d3e9ac)   
 [Exécution d’opérations &#40;de copie en bloc ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
