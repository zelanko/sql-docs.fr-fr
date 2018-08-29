---
title: Modification des résultats du jeu de données exemple | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b5ae54dc-2a79-4664-bb21-cacdb7d745e1
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0be9716b5b1f48d4d38a374069ba66b5f5d8b37c
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787233"
---
# <a name="modifying-result-set-data-sample"></a>Modification de l'exemple de données du jeu de résultats

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] montre comment récupérer un jeu de données pouvant être mis à jour auprès d’une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ensuite, en utilisant des méthodes de l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), il insère, puis modifie et enfin supprime une ligne de données dans l’ensemble de données.

Le fichier de code de cet exemple est nommé UpdateResultSet.java et se trouve à l’emplacement suivant :

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\resultsets
```

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple d’application, définissez le classpath de façon à inclure le fichier jar mssql-jdbc. L’accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] est également nécessaire. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fournit les fichiers bibliothèques de classes mssql-jdbc à utiliser en fonction des paramètres JRE (Java Runtime Environment) choisis. Pour plus d’informations sur le fichier JAR à choisir, consultez [configuration système requise pour le pilote JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a> Exemple

Dans l’exemple suivant, l’exemple de code établit une connexion à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Ensuite, en utilisant une instruction SQL avec l’objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), il exécute l’instruction SQL et place les données retournées dans un objet SQLServerResultSet pouvant être mis à jour.

Ensuite, l’exemple de code utilise la méthode [moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md) pour déplacer le curseur du jeu de résultats jusqu’à la ligne insérée, utilise une série de méthodes [updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) pour insérer des données dans la nouvelle ligne, puis appelle la méthode [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) pour réenregistrer la nouvelle ligne de données dans la base de données.

Après avoir inséré la nouvelle ligne de données, l’exemple de code utilise une instruction SQL pour extraire la ligne précédemment insérée, puis utilise la combinaison des méthodes updateString et [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) pour mettre à jour la ligne de données et la réenregistrer dans la base de données.

Enfin, l’exemple de code extrait la ligne de données précédemment mise à jour, puis la supprime de la base de données avec la méthode [deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md).

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class UpdateResultSet {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);) {

            // Create and execute an SQL statement, retrieving an updateable result set.
            String SQL = "SELECT * FROM HumanResources.Department;";
            ResultSet rs = stmt.executeQuery(SQL);

            // Insert a row of data.
            rs.moveToInsertRow();
            rs.updateString("Name", "Accounting");
            rs.updateString("GroupName", "Executive General and Administration");
            rs.updateString("ModifiedDate", "08/01/2006");
            rs.insertRow();

            // Retrieve the inserted row of data and display it.
            SQL = "SELECT * FROM HumanResources.Department WHERE Name = 'Accounting';";
            rs = stmt.executeQuery(SQL);
            displayRow("ADDED ROW", rs);

            // Update the row of data.
            rs.first();
            rs.updateString("GroupName", "Finance");
            rs.updateRow();

            // Retrieve the updated row of data and display it.
            rs = stmt.executeQuery(SQL);
            displayRow("UPDATED ROW", rs);

            // Delete the row of data.
            rs.first();
            rs.deleteRow();
            System.out.println("ROW DELETED");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        while (rs.next()) {
            System.out.println(rs.getString("Name") + " : " + rs.getString("GroupName"));
            System.out.println();
        }
    }
}

```

## <a name="see-also"></a> Voir aussi

[Utilisation de jeux de résultats](../../../connect/jdbc/code-samples/working-with-result-sets.md)
