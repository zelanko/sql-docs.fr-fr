---
title: bcp_exec | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_exec
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d5ce458ea8f5874620ea0561eeea5c6ff8e56bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62689035"
---
# <a name="bcpexec"></a>bcp_exec
  Exécute une copie en bloc complète des données entre une table de base de données et un fichier utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_exec (  
HDBC   
hdbc  
,  
LPDBINT   
pnRowsProcessed  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *pnRowsProcessed*  
 Pointeur vers un DBINT. La fonction **bcp_exec** remplit ce DBINT avec le nombre de lignes copiées avec succès. Si *pnRowsProcessed* a la valeur NULL, la fonction **bcp_exec**l'ignore.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED, SUCCEED_ASYNC ou FAIL. La fonction **bcp_exec** retourne SUCCEED si toutes les lignes sont copiées. **bcp_exec** retourne SUCCEED_ASYNC si une opération de copie en bloc asynchrone est toujours en attente. **bcp_exec** retourne FAIL en cas d'échec total ou si le nombre de lignes générant des erreurs atteint la valeur spécifiée pour BCPMAXERRS à l'aide de [bcp_control](bcp-control.md). La valeur par défaut de BCPMAXERRS est 10. L'option BCPMAXERRS affecte uniquement les erreurs de syntaxe détectées par le fournisseur lorsqu'elle lit les données du fichier de données (et non les lignes transmises au serveur). Le serveur interrompt le lot dès qu'il détecte une erreur avec une ligne. Vérifiez le paramètre *pnRowsProcessed* correspondant au nombre de lignes copiées avec succès.  
  
## <a name="remarks"></a>Notes  
 En fonction de la valeur du paramètre *eDirection* dans [bcp_init](bcp-init.md), cette fonction copie les données d'un fichier utilisateur vers une table de base de données ou inversement.  
  
 Avant d'appeler **bcp_exec**, appelez **bcp_init** avec un nom de fichier utilisateur valide. L'échec de cette opération entraîne une erreur.  
  
 **bcp_exec** est la seule fonction de copie en bloc qui est susceptible d'être en attente pendant une durée prolongée. Il s'agit par conséquent de la seule fonction de copie en bloc qui prend en charge le mode asynchrone. Pour définir le mode asynchrone, utilisez [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) pour définir SQL_ATTR_ASYNC_ENABLE to SQL_ASYNC_ENABLE_ON avant d'appeler la fonction **bcp_exec**. Pour tester son exécution en bonne et due forme, appelez la méthode **bcp_exec** avec les mêmes paramètres. Si la copie en bloc n'a pas encore été exécutée, **bcp_exec** retourne SUCCEED_ASYNC. Il retourne également dans *pnRowsProcessed* un état du nombre de lignes envoyées au serveur. Les lignes envoyées au serveur sont validées uniquement une fois la fin du lot atteinte.  
  
 Pour plus d’informations sur les importantes modifier une copie en bloc de début dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], consultez [effectuant des opérations de copie en bloc &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="example"></a>Exemple  
 L'exemple ci-après décrit comment utiliser la fonction **bcp_exec**:  
  
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
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
