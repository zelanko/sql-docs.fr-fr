---
title: Exemple de Source de données | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b4a933ee-f2c6-4e0d-a96d-6dd061abf759
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f43f757ce9d6ea8e16f400c71e4e7f3321a6bd4b
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278780"
---
# <a name="data-source-sample"></a>Exemple de source de données
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] montre comment se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] avec un objet de source de données. Il montre également comment extraire des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] avec une procédure stockée.  
  
 Le fichier de code de cet exemple est nommé ConnectDS.java et se trouve à l’emplacement suivant :  
  
 \<*répertoire d’installation*> \sqljdbc_\<*version*>\\<*langage*> \samples\connections  
  
## <a name="requirements"></a>Spécifications  
 Pour exécuter cet exemple d’application, vous devez définir le classpath de façon à inclure le fichier jar mssql-jdbc. Vous devez également avoir accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit les fichiers de bibliothèques de classes mssql-jdbc à utiliser en fonction de vos paramètres JRE (Java Runtime Environment). Pour plus d’informations sur le fichier JAR à choisir, consultez [configuration système requise pour le pilote JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a> Exemple  
 Dans l’exemple suivant, le code définit différentes propriétés de connexion avec les méthodes setter de l’objet [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), puis appelle la méthode [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) de l’objet SQLServerDataSource pour retourner un objet [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
 Ensuite, l’exemple de code utilise la méthode [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) de l’objet SQLServerConnection pour créer un objet [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), puis la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) est appelée pour exécuter la procédure stockée.  
  
 Enfin, l’exemple utilise l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) retourné par la méthode executeQuery pour boucler dans les résultats retournés par la procédure stockée.  
  
```java
import java.sql.CallableStatement;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class ConnectDS {

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
  
## <a name="see-also"></a> Voir aussi  
 [Connexion et récupération de données](../../connect/jdbc/connecting-and-retrieving-data.md)  
  
  
