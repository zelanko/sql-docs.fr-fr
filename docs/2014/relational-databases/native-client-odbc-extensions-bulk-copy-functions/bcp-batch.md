---
title: bcp_batch | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_batch
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c41e8d90adc8ff6eb2058feebe3f33c10edbfa92
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049559"
---
# <a name="bcpbatch"></a>bcp_batch
  Valide toutes les lignes précédemment copiées en bloc à partir de variables de programme et envoyées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par [bcp_sendrow](bcp-sendrow.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBINT bcp_batch (HDBC  
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *pas*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
## <a name="returns"></a>Valeur renvoyée  
 Le nombre de lignes enregistrées après le dernier appel à **bcp_batch**, ou -1 en cas d'erreur.  
  
## <a name="remarks"></a>Notes  
 Les lots de copie en bloc définissent des transactions. Lorsqu'une application utilise [bcp_bind](bcp-bind.md) et **bcp_sendrow** pour copier en bloc des lignes à partir de variables de programme dans des tables SQL Server, les lignes sont validées uniquement lorsque le programme appelle **bcp_batch** ou [bcp_done](bcp-done.md).  
  
 Vous pouvez appeler **bcp_batch** une fois chaque *n* lignes ou lorsqu'il y a une accalmie dans les données entrantes (comme dans une application de télémesure). Si une application n'appelle pas **bcp_batch** , les lignes copiées en bloc sont validées uniquement lorsque **bcp_done** est appelé.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
