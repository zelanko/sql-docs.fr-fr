---
title: Méthode setAsciiStream pour les octets du flux d’entrée-long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6bc486cd-e432-4057-8789-9957ba23dd30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1c4e5244ba0798fdd02f30faafa3459aa801e8dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975473"
---
# <a name="setasciistream-method-javalangstring-javaioinputstream-long"></a>Méthode setAsciiStream (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon le flux d’entrée spécifié, qui aura le nombre d’octets spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setAsciiStream(java.lang.String parameterName,  
                                java.io.InputStream x,  
                                long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *x*  
  
 Objet InputStream.  
  
 *length*  
  
 **Valeur de type long** qui indique le nombre d’octets.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setAsciiStream est spécifiée par la méthode setAsciiStream dans l’interface java. Sql. PreparedStatement.  
  
 Si la longueur du flux diffère de ce qui est spécifié dans le paramètre *length*, le pilote JDBC lève une exception lors de la mise à jour ou de l’insertion de la ligne.  
  
 Si la longueur du flux est inconnue, le paramètre *length* peut être défini sur -1 pour indiquer que le pilote doit accepter le flux, quelle que soit sa longueur. Avec sqljdbc4.jar, nous recommandons d’utiliser la méthode JDBC 4.0 [setAsciiStream, méthode (java.lang.String, java.io.InputStream)](../../../connect/jdbc/reference/setasciistream-method-java-lang-string-java-io-inputstream.md) quand l’application veut mettre à jour la colonne à partir d’un flux de longueur inconnue.  
  
## <a name="see-also"></a>Voir aussi  
 [setAsciiStream &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setasciistream-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
