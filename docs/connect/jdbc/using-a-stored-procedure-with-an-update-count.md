---
title: Utilisation d’une procédure stockée avec un compteur de mises à jour | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d858b255d5bdd6ce74509d36f4d0497220350694
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38040817"
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>Utilisation d’une procédure stockée avec un compteur de mises à jour
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Pour modifier les données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] à l’aide d’une procédure stockée, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). La classe SQLServerCallableStatement permet d’appeler des procédures stockées qui modifient les données contenues dans la base de données et retournent le nombre de lignes affectées, également appelé nombre de mises à jour.  
  
 Une fois l’appel à la procédure stockée configuré à l’aide de la classe SQLServerCallableStatement, vous pouvez appeler la procédure stockée à l’aide de la méthode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) ou de la méthode [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md). La méthode executeUpdate retourne une valeur **int** contenant le nombre de lignes affectées par la procédure stockée, mais la méthode execute ne le fait pas. Si vous utilisez la méthode execute et souhaitez obtenir le nombre de lignes affectées, vous pouvez appeler la méthode [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) après l’exécution de la procédure stockée.  
  
> [!NOTE]  
>  Si vous souhaitez que le pilote JDBC retourne tous les nombres de mises à jour, y compris les nombres de mises à jour retournées par des déclencheurs qui ont pu se déclencher, définissez la propriété de chaîne de connexion lastUpdateCount sur « false ». Pour plus d’informations sur la propriété lastUpdateCount, consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Par exemple, créez la table et la procédure stockée suivantes, et insérez également des exemples de données dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] :  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
  
CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```  
  
 Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction, la méthode execute permet d’appeler la procédure stockée UpdateTestTable, puis la méthode getUpdateCount permet de retourner le nombre de lignes affectées par la procédure stockée.  
  
 [!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]  
  
## <a name="see-also"></a> Voir aussi  
 [Utilisation d’instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
