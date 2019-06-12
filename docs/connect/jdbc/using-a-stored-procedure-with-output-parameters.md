---
title: Utilisation d’une procédure stockée avec des paramètres de sortie | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1c006f27-7e99-43d5-974c-7b782659290c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4af5769f5187fd70387f89aebf07625117da9a49
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790336"
---
# <a name="using-a-stored-procedure-with-output-parameters"></a>Utilisation d'une procédure stockée avec des paramètres de sortie

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Une procédure stockée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous pouvez appeler est une procédure qui retourne un ou plusieurs paramètres OUT, qui sont des paramètres utilisés par la procédure stockée pour retourner des données à l’application appelante. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), que vous pouvez utiliser pour appeler ce type de procédure stockée et traiter les données qu’elle retourne.

Quand vous appelez ce type de procédure stockée avec le pilote JDBC, vous devez utiliser la séquence d’échappement SQL `call` conjointement avec la méthode [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). La syntaxe de la séquence d’échappement `call` avec des paramètres OUT est la suivante :

`{call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Pour plus d’informations sur les séquences d’échappement SQL, consultez [à l’aide les séquences d’échappement SQL](../../connect/jdbc/using-sql-escape-sequences.md).

Quand vous construisez la séquence d’échappement `call`, spécifiez les paramètres OUT en utilisant le caractère ? (point d'interrogation). Ce caractère fait office d'espace réservé pour les valeurs de paramètre qui sont retournées par la procédure stockée. Pour spécifier une valeur pour un paramètre OUT, vous devez spécifier le type de données de chaque paramètre avec la méthode [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) de la classe SQLServerCallableStatement avant d’exécuter la procédure stockée.

La valeur que vous spécifiez pour le paramètre OUT dans la méthode registerOutParameter doit être un des types de données JDBC contenus dans java.sql.Types, qui est mappé à un des types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] natifs. Pour plus d’informations sur JDBC et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des types de données, consultez [comprendre les Types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).

Quand vous passez une valeur à la méthode registerOutParameter pour un paramètre OUT, vous devez spécifier non seulement le type de données à utiliser pour le paramètre, mais également la position ordinale du paramètre ou le nom du paramètre dans la procédure stockée. Par exemple, si votre procédure stockée contient un seul paramètre OUT, sa valeur ordinale est 1 ; si la procédure stockée contient deux paramètres, la première valeur ordinale est 1 et la seconde 2.

> [!NOTE]  
> Le pilote JDBC ne prend pas en charge l’utilisation des types de données CURSOR, SQLVARIANT, TABLE et TIMESTAMP de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que paramètres OUT.

Par exemple, créez la procédure stockée suivante dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] :

```sql
CREATE PROCEDURE GetImmediateManager  
   @employeeID INT,  
   @managerID INT OUTPUT  
AS  
BEGIN  
   SELECT @managerID = ManagerID
   FROM HumanResources.Employee
   WHERE EmployeeID = @employeeID  
END
```

Cette procédure stockée retourne un seul paramètre OUT (ManagerID), un nombre entier, basé sur le paramètre IN spécifié (EmployeeID), qui est également un nombre entier. La valeur retournée dans le paramètre OUT est le ManagerID basé sur l'EmployeeID contenu dans la table HumanResources.Employee.

Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est passée à la fonction, et la méthode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) est utilisée pour appeler la procédure stockée GetImmediateManager :

```java
public static void executeStoredProcedure(Connection con) throws SQLException {  
    try(CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}");) {  
        cstmt.setInt(1, 5);  
        cstmt.registerOutParameter(2, java.sql.Types.INTEGER);  
        cstmt.execute();  
        System.out.println("MANAGER ID: " + cstmt.getInt(2));  
    }  
}
```

Cet exemple utilise les positions ordinales pour identifier les paramètres. Vous pouvez également identifier un paramètre en utilisant son nom plutôt que sa position ordinale. L'exemple de code suivant modifie l'exemple précédent afin de démontrer comment utiliser des paramètres nommés dans une application Java. Notez que les noms des paramètres correspondent aux noms des paramètres dans la définition de la procédure stockée :

```java
public static void executeStoredProcedure(Connection con) throws SQLException {  
    try(CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}"); ) {  
        cstmt.setInt("employeeID", 5);  
        cstmt.registerOutParameter("managerID", java.sql.Types.INTEGER);  
        cstmt.execute();  
        System.out.println("MANAGER ID: " + cstmt.getInt("managerID"));  
    }  
}
```

> [!NOTE]  
> Ces exemples utilisent la méthode execute de la classe SQLServerCallableStatement pour exécuter la procédure stockée. Elle est utilisée parce que la procédure stockée n'a pas retourné de jeu de résultats. Si elle l’avait fait, la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) serait utilisée.

Les procédures stockées peuvent retourner des nombres de mises à jour et des jeux de résultats multiples. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] suit la spécification JDBC 3.0, qui stipule que les jeux de résultats et les nombres de mises à jour multiples doivent être récupérés avant les paramètres OUT. Autrement dit, l’application doit récupérer tous les objets de jeu de résultats et nombres avant de récupérer les paramètres OUT en utilisant les méthodes CallableStatement.getter de mettre à jour. Si tel n’est pas le cas, les objets ResultSet et les nombres de mises à jour qui n’ont pas encore été extraits sont perdus lors de l’extraction des paramètres OUT. Pour plus d’informations sur les mises à jour multiples et plusieurs jeux de résultats, consultez [à l’aide d’une procédure stockée avec un nombre de mettre à jour](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) et [à l’aide de plusieurs jeux de résultats](../../connect/jdbc/using-multiple-result-sets.md).

## <a name="see-also"></a>Voir aussi

[Utilisation d’instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md)
