---
title: bcp_done | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_done
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9b0cbcc927fcd10c2d81b3c5c3d39bb80a8e9b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019584"
---
# <a name="bcp_done"></a>bcp_done
  Termine une copie en bloc réalisée avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bcp_sendrow [entre des variables de programme et](bcp-sendrow.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBINT bcp_done (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
## <a name="returns"></a>Retours  
 Le nombre de lignes enregistrées de manière permanente après le dernier appel à [bcp_batch](bcp-batch.md) , ou -1 en cas d'erreur.  
  
## <a name="remarks"></a>Remarques  
 Appelez **bcp_done** après le dernier appel à [bcp_sendrow](bcp-sendrow.md) ou [bcp_moretext](bcp-moretext.md). L'échec de l'appel à **bcp_done** après la copie de toutes les données génère des erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
