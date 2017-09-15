---
title: "Méthode updateBlob (java.lang.String, java.io.InputStream, long) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f75549-5d5a-4de3-a271-4b8f0dd7b124
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74cbd78a019980e8348016c9880d3bef9b754a5a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="updateblob-method-javalangstring-javaioinputstream-long"></a>Méthode updateBlob (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée à l'aide du flux d'entrée spécifié, qui dispose du nombre spécifié d'octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateBlob(java.lang.String columnLabel,  
                       java.io.InputStream inputStream)  
                                              long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 A **chaîne** qui contient l’étiquette de colonne.  
  
 *inputStream*  
  
 Un objet InputStream.  
  
 *length*  
  
 A **long** qui indique la longueur du flux de données.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateBlob est spécifiée par la méthode updateBlob dans l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode updateBlob &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
