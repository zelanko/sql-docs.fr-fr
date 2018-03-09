---
title: bcp_batch | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- bcp_batch
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b1aa705c42846b02ae67eb66eba38660e724bf2e
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="bcpbatch"></a>bcp_batch
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Valide toutes les lignes précédemment copiées en bloc à partir de variables de programme et envoyées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBINT bcp_batch (HDBC  
        hdbc);  
```  
  
## <a name="arguments"></a>Arguments  
 *pas*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
## <a name="returns"></a>Valeur renvoyée  
 Le nombre de lignes enregistrées après le dernier appel à **bcp_batch**, ou -1 en cas d'erreur.  
  
## <a name="remarks"></a>Notes  
 Les lots de copie en bloc définissent des transactions. Lorsqu'une application utilise [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) et **bcp_sendrow** pour copier en bloc des lignes à partir de variables de programme dans des tables SQL Server, les lignes sont validées uniquement lorsque le programme appelle **bcp_batch** ou [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md).  
  
 Vous pouvez appeler **bcp_batch** une fois chaque  *n*  lignes ou lorsqu’il y a une accalmie dans les données entrantes (comme dans une application de télémesure). Si une application n'appelle pas **bcp_batch** , les lignes copiées en bloc sont validées uniquement lorsque **bcp_done** est appelé.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
