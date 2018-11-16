---
title: Méthode setMaxRows (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cccc0667-589b-4655-8ea8-14ae8b2eb9dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b1fe358652ed237a5e0cd3bbb235e85e937ad21
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602081"
---
# <a name="setmaxrows-method-sqlserverstatement"></a>Méthode setMaxRows (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la limite du nombre maximal de lignes que tout objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) peut contenir sur le nombre donné.  
  
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
  
 Cette méthode setMaxRows n’a pas d’effet sur les curseurs dynamiques avec défilement. L'application doit utiliser la syntaxe SQL SELECT TOP N pour limiter le nombre de lignes retournées à partir de jeux de résultats potentiellement importants.  
  
 Quand la méthode setMaxRows est appelée, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] exécute l’instruction SQL SET ROWCOUNT lors de l’exécution de la requête de l’application. Ceci a pour effet que le pilote JDBC limite le nombre maximal de lignes affectées par toutes les instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] exécutées par cette requête, et pas seulement le nombre de lignes retournées par cette requête. Si l’application doit définir une limite seulement pour l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) de plus haut niveau, elle doit utiliser la syntaxe SQL SELECT TOP N dans la requête à la place de la méthode setMaxRows.  
  
 Pour plus d’informations sur l’instruction SQL SET ROWCOUNT, consultez la rubrique [SET ROWCOUNT (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=139522) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
