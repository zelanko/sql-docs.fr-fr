---
title: bcp_colptr | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_colptr
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab37a2522cf1c6912f15b51214d061b18bdb2914
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009115"
---
# <a name="bcp_colptr"></a>bcp_colptr
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Définit l'adresse de données de variable de programme pour la copie actuelle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_colptr (  
        HDBC hdbc,  
        LPCBYTE pData,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *pData*  
 Pointeur vers les données à copier. Si le type de données lié est un type de valeur élevée (tel que SQLTEXT ou SQLIMAGE), *pData* peut être null. Un *pData* null indique que des valeurs de données longues sont envoyées à SQL Server dans des segments à l’aide de [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Si *pData* a la valeur null et que la colonne correspondant au champ lié n’est pas de type valeur élevée, **bcp_colptr** échoue.  
  
 Pour plus d’informations sur les types de valeur élevée, consultez [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)**.**  
  
 *idxServerCol*  
 Position ordinale de la colonne dans la table de base de données vers laquelle les données sont copiées. La première colonne d'une table est la colonne 1. La position ordinale d'une colonne est indiquée par [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Remarks  
 La fonction **bcp_colptr** vous permet de modifier l’adresse des données sources pour une colonne particulière lors de la copie des données vers SQL Server avec [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
 Initialement, le pointeur vers les données utilisateur est défini par un appel à **bcp_bind**. Si l’adresse des données de variable de programme change entre les appels à **bcp_sendrow**, vous pouvez appeler **bcp_colptr** pour réinitialiser le pointeur vers les données. L’appel suivant à **bcp_sendrow** envoie les données adressées par l’appel à **bcp_colptr**.  
  
 Il doit y avoir un appel de **bcp_colptr** distinct pour chaque colonne de la table dont vous souhaitez modifier l’adresse de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
