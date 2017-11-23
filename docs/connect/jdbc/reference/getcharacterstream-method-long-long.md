---
title: "Méthode getCharacterStream (long, long) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef06fdd3b8a7ae46b938063d10cb688178c60ea3
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getcharacterstream-method-long-long"></a>Méthode getCharacterStream (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le **Clob** comme un objet de lecteur ou en tant que flux de caractères avec la position spécifiée et la longueur de données.  
  
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
 Un objet de lecteur qui contient le **Clob** données.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getCharacterStream est spécifiée par la méthode getCharacterStream dans l’interface java.sql.Clob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getCharacterStream &#40; SQLServerClob &#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)   
 [Méthodes SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob, membres](../../../connect/jdbc/reference/sqlserverclob-members.md)  
  
  
