---
title: execute, méthode (java.lang.String) (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 64ac78b8-d5b3-4134-9b72-d2b0c52168a2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 98adf628c3cc84442d34d6f1f07431a3c5918a31
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922087"
---
# <a name="execute-method-javalangstring-sqlserverstatement"></a>execute, méthode (java.lang.String) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Exécute l'instruction SQL donnée, qui peut retourner plusieurs résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean execute(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 **Chaîne** contenant une instruction SQL.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le premier résultat est un jeu de résultats. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode execute est spécifiée par la méthode execute de l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode execute &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
