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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: efe1c815b7ed4cee971399e6b71d9d21254e10c1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922005"
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
  
  
