---
title: "Méthode Truncate (SQLServerNClob) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7e8210d-a724-4bae-832a-ae4c63031c9c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8efaadf45586f631572417a364a8009d7d41e3a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="truncate-method-sqlservernclob"></a>Méthode truncate (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tronque le **NCLOB** à la longueur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Len*  
  
 La longueur, en caractères, à laquelle le **NCLOB** valeur sera tronquée.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode truncate est spécifiée par la méthode truncate dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membres de SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
