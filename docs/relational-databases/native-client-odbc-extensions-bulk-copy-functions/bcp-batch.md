---
title: bcp_batch | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_batch
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6d43e8ca308d09e10a2f41728650a2cc0a4991d7
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009120"
---
# <a name="bcp_batch"></a>bcp_batch
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Valide toutes les lignes précédemment copiées en bloc à partir de variables de programme et envoyées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBINT bcp_batch (HDBC  
        hdbc);  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
## <a name="returns"></a>Retours  
 Le nombre de lignes enregistrées après le dernier appel à **bcp_batch**, ou -1 en cas d'erreur.  
  
## <a name="remarks"></a>Remarks  
 Les lots de copie en bloc définissent des transactions. Lorsqu'une application utilise [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) et **bcp_sendrow** pour copier en bloc des lignes à partir de variables de programme dans des tables SQL Server, les lignes sont validées uniquement lorsque le programme appelle **bcp_batch** ou [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md).  
  
 Vous pouvez appeler **bcp_batch** une fois chaque *n* lignes ou lorsqu'il y a une accalmie dans les données entrantes (comme dans une application de télémesure). Si une application n'appelle pas **bcp_batch** , les lignes copiées en bloc sont validées uniquement lorsque **bcp_done** est appelé.  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
