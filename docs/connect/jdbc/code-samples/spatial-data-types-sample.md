---
title: Exemple de types de données spatiales | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d2f56ed8036602357f8128b0426fbb90c0bab801
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028269"
---
# <a name="spatial-data-types-sample"></a>Exemple de types de données spatiales

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Cet [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] exemple d’application montre comment créer, insérer et récupérer des types de données spatiales (Geometry et Geography).
  
Le fichier de code de cet exemple, SpatialDataTypes.java, se trouve à l’emplacement suivant :  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes  
```

## <a name="requirements"></a>Spécifications  

Pour exécuter cet exemple d’application, définissez le classpath de façon à inclure le fichier jar mssql-jdbc. Pour plus d'informations sur la définition de l'instruction classpath, consultez [Utilisation du pilote JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  

> [!NOTE]  
> Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fournit les fichiers bibliothèques de classes mssql-jdbc à utiliser en fonction des paramètres JRE (Java Runtime Environment) choisis. Pour plus d'informations sur le fichier JAR à choisir, consultez [Configuration requise pour le pilote JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Exemple

Dans l’exemple suivant, l’exemple de code crée une table appelée SpatialDataTypesTable_JDBC_Sample qui contient les colonnes «Geometry» et «geography».

L’exemple crée d’abord des objets «Geometry» et «Geography» à partir d’un texte bien connu (WKT) représentant un POINT. Elle utilise un SQLServerPreparedStatement avec une requête paramétrable pour mapper les données à chaque colonne en conséquence.

Enfin, l’exemple insère les données dans la table et les récupère. Les données sont affichées sous la forme de WKT.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;
import com.microsoft.sqlserver.jdbc.Geography;
import com.microsoft.sqlserver.jdbc.Geometry;
import com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement;
import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

public class SpatialDataTypes {

    private static String tableName = "SpatialDataTypesTable_JDBC_Sample";

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";
        // Establish the connection.
        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            dropAndCreateTable(stmt);

            // TODO: Implement Sample code
            String geoWKT = "POINT(3 40 5 6)";
            Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
            Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);

            try (SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) con
                    .prepareStatement("insert into " + tableName + " values (?, ?)");) {
                pstmt.setGeometry(1, geomWKT);
                pstmt.setGeography(2, geogWKT);
                pstmt.execute();

                SQLServerResultSet rs = (SQLServerResultSet) stmt.executeQuery("select * from " + tableName);
                rs.next();

                System.out.println("Geometry data: " + rs.getGeometry(1));
                System.out.println("Geography data: " + rs.getGeography(2));
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    private static void dropAndCreateTable(Statement stmt) throws SQLException {
        stmt.executeUpdate("if object_id('" + tableName + "','U') is not null" + " drop table " + tableName);

        stmt.executeUpdate("Create table " + tableName + " (c1 geometry, c2 geography)");
    }
}
```

## <a name="see-also"></a>Voir aussi  

[Utilisation de types de données &#40;JDBC&#41;](../../../connect/jdbc/code-samples/working-with-data-types-jdbc.md)  
  
