---
title: Exemple de données du jeu de récupération des résultats | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1b190c36-3d38-49a2-8599-612329675851
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8fe0d97c8a8ec0f29e8a6b85542ea0627a5c6fb
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279140"
---
# <a name="retrieving-result-set-data-sample"></a>Extraction de l'exemple de données du jeu de résultats
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] montre comment récupérer un jeu de données à partir d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], puis comment afficher ces données.  
  
 Le fichier de code de cet exemple s’appelle RetrieveRS.java et se trouve à l’emplacement suivant :  
  
 \<*répertoire d’installation*> \sqljdbc_\<*version*>\\<*langage*> \samples\resultsets  
  
## <a name="requirements"></a>Spécifications  
 Pour exécuter cet exemple d’application, vous devez définir le classpath de façon à inclure le fichier jar mssql-jdbc. Vous devez également avoir accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit les fichiers de bibliothèques de classes mssql-jdbc à utiliser en fonction de vos paramètres JRE (Java Runtime Environment). Pour plus d’informations sur le fichier JAR à choisir, consultez [configuration système requise pour le pilote JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a> Exemple  
 Dans l’exemple suivant, l’exemple de code établit une connexion à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Ensuite, à l’aide d’une instruction SQL avec l’objet [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), il exécute les instructions SQL et place les données qu’il retourne dans un objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 Ensuite, l’exemple de code appelle la méthode personnalisée displayRow pour itérer au sein des lignes de données du jeu de résultats et utilise la méthode [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) pour afficher certaines des données.  
  
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class RetrieveRS {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT * FROM Production.Product;";
            ResultSet rs = stmt.executeQuery(SQL);
            displayRow("PRODUCTS", rs);
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
            System.out.println(rs.getString("ProductNumber") + " : " + rs.getString("Name"));
        }
    }
}
```  
  
## <a name="see-also"></a> Voir aussi  
 [Utilisation de jeux de résultats](../../connect/jdbc/working-with-result-sets.md)  
  
  
