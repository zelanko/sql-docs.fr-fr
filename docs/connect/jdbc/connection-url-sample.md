---
title: Exemple d’URL de connexion | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 96fabc42-59d1-4cc0-93c5-db00cbe55e95
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8150ae02c014d7460be10845e38d3e13be133d3
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39452553"
---
# <a name="connection-url-sample"></a>Exemple d'URL de connexion

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] montre comment se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] via une URL de connexion. Il montre également comment extraire des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] avec une instruction SQL.

Le fichier de code de cet exemple est nommé ConnectURL.java et se trouve à l’emplacement suivant :

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\connections
```

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple d’application, définissez le classpath de façon à inclure le fichier jar mssql-jdbc. L’accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est également nécessaire. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit les fichiers bibliothèques de classes mssql-jdbc à utiliser en fonction des paramètres JRE (Java Runtime Environment) choisis. Pour plus d’informations sur le fichier JAR à choisir, consultez [configuration système requise pour le pilote JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a> Exemple

Dans l’exemple suivant, le code définit différentes propriétés de connexion de l’URL de connexion, puis appelle la méthode getConnection de la classe DriverManager pour retourner un objet [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

Ensuite, l’exemple de code utilise la méthode [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) de l’objet SQLServerConnection pour créer un objet [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), puis la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) est appelée pour exécuter l’instruction SQL.

Enfin, l’exemple utilise l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) retourné par la méthode executeQuery pour boucler dans les résultats retournés par l’instruction SQL.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class ConnectURL {
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT TOP 10 * FROM Person.Contact";
            ResultSet rs = stmt.executeQuery(SQL);

            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println(rs.getString("FirstName") + " " + rs.getString("LastName"));
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## <a name="see-also"></a> Voir aussi

[Connexion et récupération de données](../../connect/jdbc/connecting-and-retrieving-data.md)
