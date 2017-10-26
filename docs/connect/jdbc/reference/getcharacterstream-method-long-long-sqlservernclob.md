---
title: "Méthode getCharacterStream (long, long) (SQLServerNClob) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a8028bc-c877-4668-b662-0746d462040e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e4777f2a081678a61ed8f00abbcd30f53a583cab
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getcharacterstream-method-long-long-sqlservernclob"></a>Méthode getCharacterStream (long, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le **NCLOB** données comme un **lecteur** objet ou en tant que flux de caractères avec une position spécifiée et la longueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                  long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bons de commande*  
  
 A **long** qui indique le décalage du premier caractère de la valeur partielle à récupérer.  
  
 *length*  
  
 A **long** qui indique la longueur en caractères de la valeur partielle à récupérer.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de lecteur qui contient le **NCLOB** données.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getCharacterStream est spécifiée par la méthode getCharacterStream dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getCharacterStream &#40; SQLServerNClob &#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [Méthodes SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membres de SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  

