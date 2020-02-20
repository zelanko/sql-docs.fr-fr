---
title: Exemple de mise en cache des données d’un jeu de résultats | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 13a95ebb-996c-4713-a1bd-5834fe22a334
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 33998300281a274067a0879775dc33c9d7635471
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028416"
---
# <a name="caching-result-set-data-sample"></a>Exemple de mise en cache des données d'un jeu de résultats

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] montre comment récupérer un grand jeu de données auprès d’une base de données et comment contrôler le nombre de lignes de données mises en cache sur le client avec la méthode [setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) de l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
> Limiter le nombre de lignes mises en cache sur le client et limiter le nombre total de lignes qu'un jeu de résultats peut contenir sont deux choses différentes. Pour contrôler le nombre total de lignes contenues dans un jeu de résultats, utilisez la méthode [setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) de l’objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), héritée par les objets [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md).  
  
Pour définir une limite du nombre de lignes mises en cache sur le client, vous devez d’abord utiliser un curseur côté serveur quand vous créez un des objets Statement en indiquant spécifiquement le type de curseur à utiliser lors de la création de l’objet Statement. Par exemple, le pilote JDBC fournit le type de curseur TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, qui est un curseur côté serveur d’avance rapide uniquement et en lecture seule, à utiliser avec les bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
> Une alternative à l'utilisation d'un type de curseur spécifique à SQL Server est l'utilisation de la propriété de chaîne de connexion selectMethod, en définissant sa valeur sur « curseur ». Pour plus d’informations sur les types de curseurs pris en charge par le pilote JDBC, consultez [Comprendre les types de curseurs](../../../connect/jdbc/understanding-cursor-types.md).  
  
Après avoir exécuté la requête de l’objet Statement et après que les données ont été retournées au client sous forme de jeu de résultats, vous pouvez appeler la méthode setFetchSize pour contrôler la quantité de données extraite de la base de données en une fois. Par exemple, si une table contient 100 lignes de données et si vous définissez la taille d’extraction à 10, seules 10 lignes de données sont mises en cache sur le client, quel que soit le moment. Même si ceci ralentit la vitesse de traitement des données, cela présente l'avantage d'utiliser moins de mémoire sur le client, ce qui peut être particulièrement utile lorsque vous devez traiter de grandes quantités de données.  
  
Le fichier de code de cet exemple est nommé CacheResultSet.java et se trouve à l’emplacement suivant :  

```bash  
\<installation directory>\sqljdbc_<version>\<language>\samples\resultsets  
```

## <a name="requirements"></a>Spécifications  

Pour exécuter cet exemple d’application, définissez le classpath de façon à inclure le fichier jar mssql-jdbc. L’accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] est également nécessaire. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
> Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fournit les fichiers bibliothèques de classes mssql-jdbc à utiliser en fonction des paramètres JRE (Java Runtime Environment) choisis. Pour plus d’informations sur le fichier JAR à choisir, voir [Configuration requise pour le pilote JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  

## <a name="example"></a>Exemple  

Dans l’exemple suivant, l’exemple de code établit une connexion à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Ensuite, il utilise des instructions SQL avec l’objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md),spécifie le type de curseur côté serveur, exécute l’instruction SQL et place les données retournées dans un objet SQLServerResultSet.  
  
Ensuite, l’exemple de code appelle la méthode personnalisée timerTest, en passant comme arguments la taille d’extraction à utiliser et le jeu de résultats. La méthode timerTest définit alors la taille d’extraction du jeu de résultats avec la méthode setFetchSize et définit l’heure de début du test, puis boucle dans le jeu de résultats avec une boucle `While`. Dès la sortie de la boucle `While`, le code définit l’heure d’arrêt du test et affiche le résultat du test, notamment la taille d’extraction, le nombre de lignes traitées et la durée d’exécution du test.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.ArrayList;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

public class CacheResultSet {

    @SuppressWarnings("serial")
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(SQLServerResultSet.TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, SQLServerResultSet.CONCUR_READ_ONLY);) {

            String SQL = "SELECT * FROM Sales.SalesOrderDetail;";

            for (int n : new ArrayList<Integer>() {
                {
                    add(1);
                    add(10);
                    add(100);
                    add(1000);
                    add(0);
                }
            }) {
                // Perform a fetch for every nth row in the result set.
                try (ResultSet rs = stmt.executeQuery(SQL)) {
                    timerTest(n, rs);
                }
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void timerTest(int fetchSize,
            ResultSet rs) throws SQLException {

        // Declare the variables for tracking the row count and elapsed time.
        int rowCount = 0;
        long startTime = 0;
        long stopTime = 0;
        long runTime = 0;

        // Set the fetch size then iterate through the result set to
        // cache the data locally.
        rs.setFetchSize(fetchSize);
        startTime = System.currentTimeMillis();
        while (rs.next()) {
            rowCount++;
        }
        stopTime = System.currentTimeMillis();
        runTime = stopTime - startTime;

        // Display the results of the timer test.
        System.out.println("FETCH SIZE: " + rs.getFetchSize());
        System.out.println("ROWS PROCESSED: " + rowCount);
        System.out.println("TIME TO EXECUTE: " + runTime);
        System.out.println();
    }
}
```

## <a name="see-also"></a>Voir aussi  

[Utilisation de jeux de résultats](../../../connect/jdbc/code-samples/working-with-result-sets.md)  
