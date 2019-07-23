---
title: Méthode setMaxFieldSize (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38f7fc1d-acad-4d10-9fc8-3c0669d93b07
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8958ffe76adbea75959dd15f87db58f28f0893b2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973996"
---
# <a name="setmaxfieldsize-method-sqlserverstatement"></a>setMaxFieldSize, méthode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nombre maximal d’octets dans une colonne [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) qui stocke des valeurs de caractères ou binaires selon le nombre d’octets donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setMaxFieldSize(int max)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *max*  
  
 **Entier** qui indique le nombre maximal d’octets.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setMaxFieldSize est spécifiée par la méthode setMaxFieldSize dans l’interface java. Sql. Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
