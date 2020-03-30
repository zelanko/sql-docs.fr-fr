---
title: Méthode getStatement (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getStatement
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7dea981b-b4fd-4f8d-954f-e686124627e2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c7fca859273c5eff58cde02b98f98699307ff1b4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979584"
---
# <a name="getstatement-method-sqlserverresultset"></a>getStatement, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère l’objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverstatement-class.md) qui a produit cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Statement getStatement()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet SQLServerStatement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getStatement est spécifiée par la méthode getStatement de l’interface java.sql.ResultSet.  
  
 Si le jeu de résultats a été généré d’une autre manière, par exemple avec une méthode [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), cette méthode retourne la valeur Null.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
