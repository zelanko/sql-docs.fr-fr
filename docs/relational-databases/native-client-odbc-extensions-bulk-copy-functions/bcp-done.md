---
title: bcp_done | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_done
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 45536578b2e8958fba356ddf67dba0712670db11
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39546759"
---
# <a name="bcpdone"></a>bcp_done
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Termine une copie en bloc réalisée avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bcp_sendrow [entre des variables de programme et](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBINT bcp_done (  
    HDBC hdbc);  
```  
  
## <a name="arguments"></a>Arguments  
 *pas*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
## <a name="returns"></a>Valeur renvoyée  
 Le nombre de lignes enregistrées de manière permanente après le dernier appel à [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) , ou -1 en cas d'erreur.  
  
## <a name="remarks"></a>Notes  
 Appelez **bcp_done** après le dernier appel à [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) ou [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md). L'échec de l'appel à **bcp_done** après la copie de toutes les données génère des erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
