---
title: Exemple de source de données | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b4a933ee-f2c6-4e0d-a96d-6dd061abf759
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5f7abb06d02485524a6bd9e19977ba430b32a18f
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028171"
---
# <a name="data-source-sample"></a>Exemple de source de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] montre comment se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec un objet de source de données. Il montre également comment extraire des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec une procédure stockée.

Le fichier de code de cet exemple, ConnectDataSource.java, se trouve à l’emplacement suivant :

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\connections
```

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple d’application, définissez le classpath de façon à inclure le fichier jar mssql-jdbc. L’accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est également nécessaire. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit les fichiers bibliothèques de classes mssql-jdbc à utiliser en fonction des paramètres JRE (Java Runtime Environment) choisis. Pour plus d’informations sur le fichier JAR à choisir, voir [Configuration requise pour le pilote JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Exemple

Dans l’exemple suivant, le code définit différentes propriétés de connexion avec les méthodes setter de l’objet [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), puis appelle la méthode [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) de l’objet SQLServerDataSource pour retourner un objet [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

Ensuite, il utilise la méthode [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) de l’objet SQLServerConnection pour créer un objet [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) ; la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) est alors appelée pour exécuter la procédure stockée.

Pour finir, l’exemple utilise l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) retourné par la méthode executeQuery pour boucler sur les résultats retournés par la procédure stockée.

```java
import java.sql.CallableStatement;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class ConnectDataSource {

    public static void main(String[] args) {

        // Create datasource.
        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setUser("<user>");
        ds.setPassword("<password>");
        ds.setServerName("<server>");
        ds.setPortNumber(<port>);
        ds.setDatabaseName("AdventureWorks");

        try (Connection con = ds.getConnection();
                CallableStatement cstmt = con.prepareCall("{call dbo.uspGetEmployeeManagers(?)}");) {
            // Execute a stored procedure that returns some data.
            cstmt.setInt(1, 50);
            ResultSet rs = cstmt.executeQuery();

            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println("EMPLOYEE: " + rs.getString("LastName") + ", " + rs.getString("FirstName"));
                System.out.println("MANAGER: " + rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));
                System.out.println();
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

[Connexion et récupération de données](../../connect/jdbc/connecting-and-retrieving-data.md)
