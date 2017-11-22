---
title: "Méthode setCharacterStream (java.lang.String, java.io.Reader, long) | Documents Microsoft"
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
ms.assetid: 54fb2f13-f8d8-47b5-bec1-4a5af3e86a84
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 11788cf04694341635c078ba42d11eb1bf4fc4f8
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setcharacterstream-method-javalangstring-javaioreader-long"></a>Méthode setCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné à l’objet java.io.Reader spécifié, qui est le nombre de caractères spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setCharacterStream(java.lang.String parameterName  
                        java.io.Reader reader,  
                        long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 A **chaîne** qui contient le nom du paramètre.  
  
 *lecteur*  
  
 Un objet de lecteur qui contient les données Unicode.  
  
 *length*  
  
 A **long** qui indique le nombre de caractères dans le flux de données.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setCharacterStream est spécifiée par la méthode setCharacterStream dans l’interface java.sql.CallableStatement.  
  
 Si la longueur du flux de données est différente de celui spécifié dans le *longueur* paramètre, le pilote JDBC lève une exception lorsque la ligne est mise à jour ou insérée.  
  
 Si la longueur du flux de données est inconnue, la *longueur* paramètre peut être défini sur -1 pour indiquer que le pilote doit accepter le flux, quelle que soit sa longueur. Avec sqljdbc4.jar, nous vous recommandons d’utiliser la méthode JDBC 4.0 [méthode setCharacterStream (java.lang.String, java.io.Reader)](../../../connect/jdbc/reference/setcharacterstream-method-java-lang-string-java-io-reader.md) lorsque l’application veut mettre à jour la colonne à partir d’un flux dont la longueur est inconnue.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setCharacterStream &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
