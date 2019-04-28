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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62688667"
---
# <a name="bcpreadfmt"></a>bcp_readfmt
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
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Après avoir `bcp_readfmt` lit les valeurs de format, il effectue les appels appropriés aux [bcp_columns](bcp-columns.md) et [bcp_colfmt](bcp-colfmt.md). Vous n'avez nul besoin d'analyser un fichier de format et d'exécuter ces appels.  
  
 Pour rendre un fichier de format persistant, appelez [bcp_writefmt](bcp-writefmt.md). Les appels à `bcp_readfmt` peuvent référencer des formats enregistrés. Pour plus d'informations, consultez [bcp_init](bcp-init.md).  
  
 Vous pouvez également l’utilitaire de copie en bloc (**bcp**) peut enregistrer les formats de données défini par l’utilisateur dans les fichiers qui peuvent être référencées par `bcp_readfmt`. Pour plus d’informations sur la **bcp** utilitaire et la structure de **bcp** fichiers de format de données, consultez [importation et exportation de données &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 Le `BCPDELAYREADFMT` valeur de la *eOption* paramètre de [bcp_control](bcp-control.md) modifie le comportement de bcp_readfmt.  
  
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
 [Fonctions de copie en bloc](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
