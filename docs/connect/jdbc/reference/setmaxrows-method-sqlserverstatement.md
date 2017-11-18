---
title: "Méthode setMaxRows (SQLServerStatement) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.setMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cccc0667-589b-4655-8ea8-14ae8b2eb9dc
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b08d78a404c0454600072d9b227761d8c27045cc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setmaxrows-method-sqlserverstatement"></a>Méthode setMaxRows (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la limite pour le nombre maximal de lignes que tout [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet peut contenir le nombre donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setMaxRows(int max)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *max*  
  
 Un **int** qui indique le nombre maximal de lignes, ou 0 s’il n’existe aucune limite.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setMaxRows est spécifiée par la méthode setMaxRows dans l’interface java.sql.Statement.  
  
 Cette méthode setMaxRows a aucun effet sur les curseurs dynamiques permettant les défilements. L'application doit utiliser la syntaxe SQL SELECT TOP N pour limiter le nombre de lignes retournées à partir de jeux de résultats potentiellement importants.  
  
 Lorsque la méthode setMaxRows est appelée, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] exécute l’instruction SQL SET ROWCOUNT lors de l’exécution de requête de l’application. Cela entraîne le pilote JDBC à limiter le nombre maximal de lignes affectées par toutes les [!INCLUDE[tsql](../../../includes/tsql_md.md)] instructions exécutées par cette requête, et non simplement le nombre de lignes retournées par cette requête. Si l’application doit définir une limite sur le niveau supérieur [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) de l’objet, elle doit utiliser la syntaxe SELECT TOP N SQL dans la requête au lieu de la méthode setMaxRows.  
  
 Pour plus d’informations sur l’instruction SQL SET ROWCOUNT, consultez le «[SET ROWCOUNT (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=139522)« rubrique dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

