---
title: Méthode execute (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.execute (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a871917e-d286-46c3-96cf-2e8e8b22111c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 09adea323a5a2930e9c636a1b2e1b00567dbd9ce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954958"
---
# <a name="execute-method-javalangstring"></a>Méthode execute (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Exécute l'instruction SQL donnée, qui peut retourner plusieurs résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final boolean execute(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 **Chaîne** qui contient une instruction SQL.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si l’instruction retourne un jeu de résultats. **false** si elle retourne un nombre de mises à jour ou aucun résultat.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode execute est spécifiée par la méthode execute de l’interface java.sql.Statement.  
  
 Cette méthode remplace la méthode [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) qui se trouve dans la classe [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
 L’appel de cette méthode entraîne une exception, car l’instruction SQL de l’objet SQLServerPreparedStatement est spécifiée lors de la création de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [execute, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
