---
title: Méthode getMaxFieldSize, (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ed7bbcb8-660b-4e9b-8241-e216c42826f9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9a1700cc8bb2bfb54dd9ddee52da54899f764650
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67982101"
---
# <a name="getmaxfieldsize-method-sqlserverstatement"></a>getMaxFieldSize, méthode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal d’octets pouvant être retournés pour des valeurs de colonne de caractères ou binaire dans un objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) produit par cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getMaxFieldSize()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **Entier** qui indique le nombre maximal d’octets qu’une colonne peut contenir, ou 0 s’il n’y a aucune limite.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxFieldSize, est spécifiée par la méthode getMaxFieldSize, dans l’interface java. Sql. Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, méthodes](../../../connect/jdbc/reference/sqlserverstatement-methods.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
