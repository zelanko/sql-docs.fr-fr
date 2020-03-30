---
title: setCharacterStream, méthode (int, java.io.Reader, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setCharacterStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 139a5b74-8d7d-41cf-991a-a142349c58f6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3002c3375f14eb4c33554c960c567e4a3d8526b0
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67974772"
---
# <a name="setcharacterstream-method-int-javaioreader-int"></a>Méthode setCharacterStream (int, java.io.Reader, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet Reader donné, qui correspond au nombre de caractères donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setCharacterStream(int n,  
                                     java.io.Reader reader,  
                                     int length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *n*  
  
 **int** indiquant le numéro du paramètre.  
  
 *reader*  
  
 Objet Reader.  
  
 *length*  
  
 Nombre de caractères.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setCharacterStream est spécifiée par la méthode setCharacterStream de l’interface java.sql.PreparedStatement.  
  
 Si la longueur du flux diffère de celle spécifiée dans le paramètre *length*, le pilote JDBC lève une exception lors de la mise à jour ou de l’insertion de la ligne.  
  
 Si la longueur du flux est inconnue, le paramètre *length* peut être défini sur -1 pour indiquer que le pilote doit accepter le flux, quelle que soit sa longueur. Avec sqljdbc4.jar, nous vous recommandons d’utiliser la méthode JDBC 4.0 [setCharacterStream, méthode &#40;int, java.io.Reader&#41;](../../../connect/jdbc/reference/setcharacterstream-method-int-java-io-reader.md) quand l’application veut mettre à jour la colonne à partir d’un flux de longueur inconnue.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
