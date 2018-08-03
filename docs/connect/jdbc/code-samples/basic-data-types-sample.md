---
title: Exemple de Types de données de base | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1807de415a5e9641ab431ca7fed123fb097eb90e
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279160"
---
# <a name="basic-data-types-sample"></a>Exemple de types de données de base
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] montre comment utiliser les méthodes getter du jeu de résultats pour récupérer les valeurs des types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] de base ; il montre également comment utiliser les méthodes update du jeu de résultats pour mettre à jour ces valeurs.  
  
 Le fichier de code de cet exemple est nommé BasicDT.java et se trouve à l’emplacement suivant :  
  
 \<*répertoire d’installation*> \sqljdbc_\<*version*>\\<*langage*> \samples\datatypes  
  
## <a name="requirements"></a>Spécifications  
 Pour exécuter cet exemple d’application, vous devez définir le classpath de façon à inclure le fichier jar mssql-jdbc. Vous devez également avoir accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
 Créez la table suivante et l’exemple de données dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] :  
  
```sql
use AdventureWorks  
CREATE TABLE DataTypesTable   
   (Col1 int IDENTITY,   
    Col2 char,  
    Col3 varchar(50),   
    Col4 bit,  
    Col5 decimal(18, 2),  
    Col6 money,  
    Col7 datetime,  
    Col8 date,  
    Col9 time,  
    Col10 datetime2,  
    Col11 datetimeoffset  
    );  
  
INSERT INTO DataTypesTable   
VALUES ('A', 'Some text.', 0, 15.25, 10.00, '01/01/2006 23:59:59.991', '01/01/2006', '23:59:59', '01/01/2006 23:59:59.12345', '01/01/2006 23:59:59.12345 -1:00')  
```  
  
> [!NOTE]  
>  Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fournit les fichiers de bibliothèques de classes mssql-jdbc à utiliser en fonction de vos paramètres JRE (Java Runtime Environment). Pour plus d’informations sur le fichier JAR à choisir, consultez [configuration système requise pour le pilote JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a> Exemple  
 Dans l’exemple suivant, l’exemple de code établit une connexion à la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)], puis extrait une seule ligne de données de la table de test DataTypesTable. La méthode personnalisée displayRow est alors appelée pour afficher toutes les données du jeu de résultats avec différentes méthodes get\<Type> de la classe [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 Ensuite, l’exemple utilise plusieurs méthodes update\<Type> de la classe SQLServerResultSet pour mettre à jour les données du jeu de résultats, puis il appelle la méthode [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) pour réenregistrer ces données dans la base de données.  
  
 Enfin, l’exemple actualise les données dans le jeu de résultats et appelle ensuite la méthode displayRow personnalisée pour l’afficher.  
  
```java
import java.sql.Connection;
import java.sql.Date;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.Time;
import java.sql.Timestamp;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

import microsoft.sql.DateTimeOffset;

public class BasicDT {
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);) {

            String SQL = "SELECT * FROM DataTypesTable";
            ResultSet rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("ORIGINAL DATA", rs);

            // Update the data in the result set.
            rs.updateString(2, "B");
            rs.updateString(3, "Some updated text.");
            rs.updateBoolean(4, true);
            rs.updateDouble(5, 77.89);
            rs.updateDouble(6, 1000.01);
            long timeInMillis = System.currentTimeMillis();
            Timestamp ts = new Timestamp(timeInMillis);
            rs.updateTimestamp(7, ts);
            rs.updateDate(8, new Date(timeInMillis));
            rs.updateTime(9, new Time(timeInMillis));
            rs.updateTimestamp(10, ts);

            // -480 indicates GMT - 8:00 hrs
            ((SQLServerResultSet) rs).updateDateTimeOffset(11, DateTimeOffset.valueOf(ts, -480));

            rs.updateRow();

            // Get the updated data from the database and display it.
            rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("UPDATED DATA", rs);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        System.out.println(rs.getInt(1) + " , " +                 // SQL integer type.
                rs.getString(2) + " , " +                         // SQL char type.
                rs.getString(3) + " , " +                         // SQL varchar type.
                rs.getBoolean(4) + " , " +                        // SQL bit type.
                rs.getDouble(5) + " , " +                         // SQL decimal type.
                rs.getDouble(6) + " , " +                         // SQL money type.
                rs.getTimestamp(7) + " , " +                      // SQL datetime type.
                rs.getDate(8) + " , " +                           // SQL date type.
                rs.getTime(9) + " , " +                           // SQL time type.
                rs.getTimestamp(10) + " , " +                     // SQL datetime2 type.
                ((SQLServerResultSet) rs).getDateTimeOffset(11)); // SQL datetimeoffset type.
        System.out.println();
    }
}
```  
  
## <a name="see-also"></a> Voir aussi  
 [Utilisation des types de données &#40;JDBC&#41;](../../../connect/jdbc/working-with-data-types-jdbc.md)  
  
  
