---
title: setBinaryStream, méthode (int, java.io.InputStream, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4ab2e2f3-eaf0-471a-8422-2cf98ce979cf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 34b61ba6338967945f92add5b212bfeae2458e4d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975297"
---
# <a name="setbinarystream-method-int-javaioinputstream-long"></a>Méthode setBinaryStream (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon le flux d'entrée spécifié, qui disposera du nombre spécifique d'octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setBinaryStream(int parameterIndex,  
                                 java.io.InputStream x,  
                                          long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 **Entier** qui indique le numéro du paramètre.  
  
 *x*  
  
 Objet Java. IO. InputStream.  
  
 *length*  
  
 **Valeur de type long** qui indique le nombre d’octets.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setBinaryStream est spécifiée par la méthode setBinaryStream dans l’interface java. Sql. PreparedStatement.  
  
 Si la longueur du flux diffère de ce qui est spécifié dans le paramètre *length*, le pilote JDBC lève une exception lors de la mise à jour ou de l’insertion de la ligne.  
  
 Si la longueur du flux est inconnue, le paramètre *length* peut être défini sur -1 pour indiquer que le pilote doit accepter le flux, quelle que soit sa longueur. Avec sqljdbc4.jar, nous vous recommandons d’utiliser la méthode JDBC 4.0 [setBinaryStream, méthode &#40;int, java.io.InputStream&#41;](../../../connect/jdbc/reference/setbinarystream-method-int-java-io-inputstream.md) quand l’application veut mettre à jour la colonne à partir d’un flux de longueur inconnue.  
  
## <a name="see-also"></a>Voir aussi  
 [setBinaryStream, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
