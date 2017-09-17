---
title: "setUnicodeStream (méthode) (SQLServerPreparedStatement) | Documents Microsoft"
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
- SQLServerPreparedStatement.setUnicodeStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0a413e83-e0a4-41f8-9fe0-33ce4d368ee4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 342eeefd5fa5fc1dddb2687474e83b4beec6ca45
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setunicodestream-method-sqlserverpreparedstatement"></a>setUnicodeStream (méthode) (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le numéro de paramètre désigné selon le flux d'entrée donné, qui disposera du nombre spécifique d'octets.  
  
> [!NOTE]  
>  Cette méthode a été déconseillée dans la spécification JDBC et son appel entraîne la levée d'une exception « Non implémenté ».  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setUnicodeStream(int n,  
                                   java.io.InputStream x,  
                                   int length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *n*  
  
 Un **int** qui indique le nombre de paramètres.  
  
 *x*  
  
 Un objet InputStream.  
  
 *length*  
  
 Nombre d'octets.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setUnicodeStream est spécifiée par la méthode setUnicodeStream dans l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
