---
title: Exemple d’URL de connexion | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
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
ms.openlocfilehash: 31a3a492c9c6405e4d7f3c8d629adca38c2a3199
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278760"
---
# <a name="connection-url-sample"></a>Exemple d'URL de connexion
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] montre comment se connecter à une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] via une URL de connexion. Il montre également comment extraire des données d’une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] avec une instruction SQL.  
  
 Le fichier de code de cet exemple est nommé ConnectURL.java et se trouve à l’emplacement suivant :  
  
 \<*répertoire d’installation*> \sqljdbc_\<*version*>\\<*langage*> \samples\connections  
  
## <a name="requirements"></a>Spécifications  
 Pour exécuter cet exemple d’application, vous devez définir le classpath de façon à inclure le fichier jar mssql-jdbc. Vous devez également avoir accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fournit les fichiers de bibliothèques de classes mssql-jdbc à utiliser en fonction de vos paramètres JRE (Java Runtime Environment). Pour plus d’informations sur le fichier JAR à choisir, consultez [configuration système requise pour le pilote JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a> Exemple  
 Dans l’exemple suivant, le code définit différentes propriétés de connexion de l’URL de connexion, puis appelle la méthode getConnection de la classe DriverManager pour retourner un objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
 Ensuite, l’exemple de code utilise la méthode [createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) de l’objet SQLServerConnection pour créer un objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), puis la méthode [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) est appelée pour exécuter l’instruction SQL.  
  
 Enfin, l’exemple utilise l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) retourné par la méthode executeQuery pour boucler dans les résultats retournés par l’instruction SQL.  
  
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
 [Connexion et récupération de données](../../../connect/jdbc/connecting-and-retrieving-data.md)
