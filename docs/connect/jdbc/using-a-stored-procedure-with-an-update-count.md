---
title: Utilisation d'une procédure stockée avec un nombre de mises à jour | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 851974955b9311efc149ecdff310bfbb1d8869fc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69026927"
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>Utilisation d'une procédure stockée avec un nombre de mises à jour

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour modifier les données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une procédure stockée, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). La classe SQLServerCallableStatement permet d’appeler des procédures stockées qui modifient les données de la base de données et retournent le nombre de lignes affectées, également appelé nombre de mises à jour.

Une fois l’appel à la procédure stockée configuré à l’aide de la classe SQLServerCallableStatement, vous pouvez appeler la procédure stockée à l’aide de la méthode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) ou de la méthode [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md). La méthode executeUpdate retourne une valeur **int** contenant le nombre de lignes affectées par la procédure stockée, au contraire de la méthode execute. Si vous utilisez la méthode execute et souhaitez obtenir le nombre de lignes affectées, vous pouvez appeler la méthode [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) après l’exécution de la procédure stockée.

> [!NOTE]  
> Si vous souhaitez que le pilote JDBC retourne tous les nombres de mises à jour, y compris les nombres de mises à jour retournées par des déclencheurs qui ont pu se déclencher, définissez la propriété de chaîne de connexion lastUpdateCount sur « false ». Pour plus d'informations sur la propriété lastUpdateCount, consultez [Paramétrage des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).

Par exemple, créez la table et la procédure stockée suivantes, et insérez également des exemples de données dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] :

```sql
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

## <a name="see-also"></a>Voir aussi

[Utilisation d'instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md)
