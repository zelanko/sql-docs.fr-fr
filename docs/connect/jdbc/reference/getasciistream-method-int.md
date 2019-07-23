---
title: Méthode getAsciiStream (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getAsciiStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1ec7e246-4b91-4420-9a4c-0ebd98e2e38b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f7bc5b4729e071f2a65670522735654e550a453
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954208"
---
# <a name="getasciistream-method-int"></a>Méthode getAsciiStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de l’index de colonne désigné dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) sous forme de flux de caractères ASCII.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.InputStream getAsciiStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 **Entier** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getAsciiStream est spécifiée par la méthode getAsciiStream dans l’interface java. Sql. ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [getAsciiStream, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
