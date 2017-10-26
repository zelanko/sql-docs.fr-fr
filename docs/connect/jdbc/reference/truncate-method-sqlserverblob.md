---
title: "Méthode Truncate (SQLServerBlob) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerBlob.truncate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ef181e04-003a-442a-9b7e-0c508a7cc873
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e1e04414b9ecda98f1275846fae29f009490a53b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="truncate-method-sqlserverblob"></a>Méthode truncate (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tronque un BLOB en fonction de la longueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Len*  
  
 Nouvelle longueur pour le BLOB.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode truncate est spécifiée par la méthode truncate dans l’interface java.sql.Blob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Membres de SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  

