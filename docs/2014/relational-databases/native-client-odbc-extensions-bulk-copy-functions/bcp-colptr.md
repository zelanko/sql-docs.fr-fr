---
title: bcp_colptr | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colptr
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 269ab3c748557d1d2870195524310f2371b79c52
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62689151"
---
# <a name="bcp_colptr"></a>bcp_colptr
  Définit l'adresse de données de variable de programme pour la copie actuelle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_colptr (  
HDBC   
hdbc  
,  
LPCBYTE   
pData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *pData*  
 Pointeur vers les données à copier. Si le type de données lié est un type de valeur élevée (tel que SQLTEXT ou SQLIMAGE), *pData* peut être null. Un *pData* null indique que des valeurs de données longues sont envoyées à SQL Server dans des segments à l’aide de [bcp_moretext](bcp-moretext.md).  
  
 Si *pData* a la valeur null et que la colonne correspondant au champ lié n’est pas de type valeur élevée, **bcp_colptr** échoue.  
  
 Pour plus d’informations sur les types de valeur élevée, consultez [bcp_bind](bcp-bind.md)**.**  
  
 *idxServerCol*  
 Position ordinale de la colonne dans la table de base de données vers laquelle les données sont copiées. La première colonne d'une table est la colonne 1. La position ordinale d'une colonne est indiquée par [SQLColumns](../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 La fonction **bcp_colptr** vous permet de modifier l’adresse des données sources pour une colonne particulière lors de la copie des données vers SQL Server avec [bcp_sendrow](bcp-sendrow.md).  
  
 Initialement, le pointeur vers les données utilisateur est défini par un appel à **bcp_bind**. Si l’adresse des données de variable de programme change entre les appels à **bcp_sendrow**, vous pouvez appeler **bcp_colptr** pour réinitialiser le pointeur vers les données. L’appel suivant à **bcp_sendrow** envoie les données adressées par l’appel à **bcp_colptr**.  
  
 Il doit y avoir un appel de **bcp_colptr** distinct pour chaque colonne de la table dont vous souhaitez modifier l’adresse de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
