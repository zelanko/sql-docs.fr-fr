---
title: Méthode executeQuery () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeQuery ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1d90407f-16df-4ba2-b4a5-47d5751e1d7c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1f80cceb8807fc643e197d06ae737ee7347e1be1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67954764"
---
# <a name="executequery-method-"></a>Méthode executeQuery ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Exécute la requête SQL dans cet objet [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), puis retourne l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) généré par la requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet executeQuery()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet SQLServerResultSet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode executeQuery est spécifiée par la méthode executeQuery de l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [executeQuery, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
