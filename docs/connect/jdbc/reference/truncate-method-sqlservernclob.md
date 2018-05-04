---
title: Méthode Truncate (SQLServerNClob) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b7e8210d-a724-4bae-832a-ae4c63031c9c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 79372fc2d1318c015f252c4bd8a425ab3e749fbc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="truncate-method-sqlservernclob"></a>Méthode truncate (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tronque le **NCLOB** à la longueur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *len*  
  
 La longueur, en caractères, à laquelle le **NCLOB** valeur sera tronquée.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode truncate est spécifiée par la méthode truncate dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membres de SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
