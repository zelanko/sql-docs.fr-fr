---
title: bcp_readfmt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_readfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76ccc4271877b81ae103a89b5df727b74017d9ab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62688667"
---
# <a name="bcp_readfmt"></a>bcp_readfmt
  Lit la définition du format du fichier de données à partir du fichier de format spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_readfmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *szFormatFile*  
 Chemin d'accès et nom du fichier contenant les valeurs de format du fichier de données.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Après `bcp_readfmt` avoir lu les valeurs de format, il effectue les appels appropriés à [bcp_columns](bcp-columns.md) et [bcp_colfmt](bcp-colfmt.md). Vous n'avez nul besoin d'analyser un fichier de format et d'exécuter ces appels.  
  
 Pour rendre un fichier de format persistant, appelez [bcp_writefmt](bcp-writefmt.md). Les appels `bcp_readfmt` à peuvent référencer des formats enregistrés. Pour plus d'informations, consultez [bcp_init](bcp-init.md).  
  
 L’utilitaire de copie en bloc (**BCP**) peut également enregistrer des formats de données définis par l’utilisateur dans des fichiers qui peuvent être `bcp_readfmt`référencés par. Pour plus d’informations sur l’utilitaire **BCP** et la structure des fichiers de format de données **BCP** , consultez [importation et exportation en bloc de données &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 La `BCPDELAYREADFMT` valeur du paramètre *eOption* de [bcp_control](bcp-control.md) modifie le comportement de bcp_readfmt.  
  
> [!NOTE]  
>  Le fichier de format a dû être produit par la version 4.2 ou version ultérieure de l'utilitaire **bcp** .  
  
## <a name="example"></a>Exemple  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
