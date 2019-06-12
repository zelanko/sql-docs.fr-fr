---
title: TRUNCATE, méthode (SQLServerClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.truncate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea3b2a03-387e-49d7-a4d6-ca6a6a354c90
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2f07f68e179dcac33a67778dd3671442d0b78b6d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66785006"
---
# <a name="truncate-method-sqlserverclob"></a>Méthode truncate (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tronque le CLOB à la longueur donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *len*  
  
 Longueur, en caractères, à laquelle le CLOB doit être tronqué.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode truncate est spécifiée par la méthode truncate dans l’interface java.sql.Clob.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerClob, méthodes](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob, membres](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
