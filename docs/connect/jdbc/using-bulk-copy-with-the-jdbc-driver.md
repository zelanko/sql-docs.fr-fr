---
title: Utilisation de la copie en bloc avec le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 21e19635-340d-49bb-b39d-4867102fb5df
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 499504d3cc238b10b62fe9dc554c77ebf72ec4b0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003997"
---
# <a name="using-bulk-copy-with-the-jdbc-driver"></a>Utilisation de la copie en bloc avec le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft SQL Server inclut un utilitaire en ligne de commande connu, **bcp**, pour rapidement copier en bloc des fichiers volumineux dans des tables ou des vues de bases de données SQL Server. La classe SQLServerBulkCopy vous permet d’écrire des solutions de code en Java, qui fournissent des fonctionnalités similaires. Il existe d’autres façons de charger des données dans une table SQL Server (instructions INSERT, par exemple) mais SQLServerBulkCopy offre de meilleures performances.  
  
La classe SQLServerBulkCopy peut être utilisée pour écrire des données uniquement dans des tables SQL Server. Toutefois, les sources de données ne sont pas limitées à SQL Server : toutes sont utilisables, tant que les données sont lisibles avec une implémentation ResultSet, RowSet ou ISQLServerBulkRecord.  
  
La classe SQLServerBulkCopy vous permet d'effectuer les opérations suivantes :  
  
- Une opération unique de copie en bloc  
  
- Plusieurs opérations de copie en bloc  
  
- Une opération de copie en bloc avec une transaction  
  
> [!NOTE]  
> Quand vous utilisez Microsoft JDBC Driver 4.1 pour SQL Server ou une version antérieure (qui ne prend pas en charge la classe SQLServerBulkCopy), vous pouvez exécuter l'instruction SQL Server Transact-SQL BULK INSERT à la place.  
  
## <a name="bulk-copy-example-setup"></a>Configuration de l'exemple de copie en bloc  

La classe SQLServerBulkCopy peut être utilisée pour écrire des données uniquement dans des tables SQL Server. Les exemples de code présentés dans cet article utilisent l'exemple de base de données SQL Server AdventureWorks. Pour éviter de modifier les exemples de code des tables existantes, écrivez les données dans des tables que vous aurez préalablement créées.  
  
Les tables BulkCopyDemoMatchingColumns et BulkCopyDemoDifferentColumns sont basées sur la table AdventureWorks Production.Products. Dans les exemples de code qui utilisent ces tables, les données sont ajoutées à partir de la table Production.Products à l'un de ces exemples de tables. La table BulkCopyDemoDifferentColumns est utilisée quand l'exemple illustre comment mapper des colonnes de données source à la table de destination. BulkCopyDemoMatchingColumns est utilisé pour la plupart des autres exemples.  
  
Certains exemples de code montrent comment utiliser une classe SQLServerBulkCopy pour écrire dans plusieurs tables. Pour ces exemples, les tables BulkCopyDemoOrderHeader et BulkCopyDemoOrderDetail sont utilisées comme tables de destination. Ces tables sont basées sur les tables Sales.SalesOrderHeader et Sales.SalesOrderDetail dans AdventureWorks.  
  
> [!NOTE]  
> Les exemples de code SQLServerBulkCopy sont fournis pour illustrer la syntaxe pour l'utilisation de SQLServerBulkCopy uniquement. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d'utiliser une instruction Transact-SQL INSERT ... SELECT pour copier les données.  

### <a name="table-setup"></a>Configuration des tables  

Pour créer les tables nécessaires à la bonne exécution des exemples de code, vous devez exécuter les instructions Transact-SQL suivantes dans une base de données SQL Server.  

```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobject
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
```

## <a name="single-bulk-copy-operations"></a>Opérations uniques de copie en bloc

L'approche la plus simple pour effectuer une opération de copie en bloc SQL Server est d'effectuer une opération unique sur une base de données. Par défaut, une opération de copie en bloc est effectuée comme une opération isolée : l'opération de copie se produit de façon non transactionnelle, sans possibilité de restauration.  
  
> [!NOTE]  
> Si vous devez restaurer tout ou partie de la copie en bloc en cas d’erreur, vous pouvez utiliser une transaction gérée par SQLServerBulkCopy ou effectuer l’opération de copie en bloc dans une transaction existante.  
> Pour plus d’informations, consultez [Transaction et opérations de copie en bloc](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#transaction-and-bulk-copy-operations).  
  
 Les étapes générales pour effectuer une opération de copie en bloc sont les suivantes :  
  
1. Connectez-vous au serveur source et obtenez les données à copier. Les données peuvent également provenir d'autres sources, si elles peuvent être récupérées à partir d'un objet ResultSet ou d'une implémentation ISQLServerBulkRecord.  
  
2. Connectez-vous au serveur de destination (sauf si vous voulez que **SQLServerBulkCopy** établisse la connexion pour vous).  
  
3. Créez un objet SQLServerBulkCopy, en définissant les propriétés requises par le biais de **setBulkCopyOptions**.  
  
4. Appelez la méthode **setDestinationTableName** afin d’indiquer la table cible pour l’opération d’insertion en bloc.  
  
5. Appelez l’une des méthodes **writeToServer**.  
  
6. Mettez éventuellement à jour les propriétés par le biais de **setBulkCopyOptions** et rappelez **writeToServer** si nécessaire.  
  
7. Appelez **close** ou insérez les opérations de copie en bloc dans une instruction try-with-resources.  
  
> [!CAUTION]  
> Il est préférable que les types de données des colonnes source et cible correspondent. Si les types de données ne correspondent pas, SQLServerBulkCopy essaie de convertir chaque valeur source en type de données cible. Les conversions peuvent affecter les performances et entraîner des erreurs inattendues. Par exemple, un type de données double peut être converti en type de données décimal la plupart du temps, mais pas toujours.  
  
### <a name="example"></a>Exemple

L'application suivante montre comment charger des données à l'aide de la classe SQLServerBulkCopy. Dans cet exemple, un ResultSet est utilisé pour copier des données de la table Production.Product de la base de données SQL Server AdventureWorks dans une table semblable de la même base de données.  
  
> [!IMPORTANT]  
> Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration des tables](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#table-setup). Ce code est fourni pour illustrer la syntaxe pour l'utilisation de SQLServerBulkCopy uniquement. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d'utiliser une instruction Transact-SQL INSERT ... SELECT pour copier les données.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;

public class BulkCopySingle {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection)) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // In real world applications you would
            // not use SQLServerBulkCopy to move data from one table to the other
            // in the same database. This is for demonstration purposes only.

            // Set up the bulk copy object.
            // Note that the column positions in the source
            // table match the column positions in
            // the destination table so there is no need to
            // map columns.
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            bulkCopy.writeToServer(rsSourceData);

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="performing-a-bulk-copy-operation-using-transact-sql"></a>Exécution d'une opération de copie en bloc à l'aide de Transact-SQL

L'exemple suivant illustre comment utiliser la méthode executeUpdate pour exécuter l'instruction BULK INSERT.  
  
> [!NOTE]  
> Le chemin d'accès de la source de données est relatif au serveur. Le processus serveur doit avoir accès à ce chemin d'accès pour que l'opération de copie en bloc réussisse.  

```java
try (Connection con = DriverManager.getConnection(connectionUrl);
        Statement stmt = con.createStatement()) {
    // Perform the BULK INSERT
    stmt.executeUpdate(
            "BULK INSERT Northwind.dbo.[Order Details] " + "FROM 'f:\\mydata\\data.tbl' " + "WITH ( FORMATFILE='f:\\mydata\\data.fmt' )");
}
```  

## <a name="multiple-bulk-copy-operations"></a>Plusieurs opérations de copie en bloc  

Vous pouvez effectuer plusieurs opérations de copie en bloc à l'aide d'une seule instance d'une classe SQLServerBulkCopy. Si les paramètres des opérations changent entre les copies (par exemple, le nom de la table de destination), vous devez les mettre à jour avant d'appeler l'une des méthodes writeToServer, comme illustré dans l'exemple suivant. Sans modification explicite, toutes les valeurs de propriété restent identiques à celles utilisées lors de la précédente opération de copie pour une instance donnée.  

> [!NOTE]  
> L'exécution de plusieurs opérations de copie en bloc à l'aide de la même instance de SQLServerBulkCopy est généralement plus efficace que l'utilisation d'une instance distincte pour chaque opération.  
  
Si vous effectuez plusieurs opérations de copie en bloc à l'aide du même objet SQLServerBulkCopy, aucune restriction ne s'applique selon que les informations sources ou cibles sont égales ou différentes dans chaque opération. Toutefois, vous devez vous assurer que les informations d'association de colonnes sont définies correctement chaque fois que vous écrivez sur le serveur.  
  
> [!IMPORTANT]  
> Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration des tables](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#table-setup). Ce code est fourni pour illustrer la syntaxe pour l'utilisation de SQLServerBulkCopy uniquement. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d'utiliser une instruction Transact-SQL INSERT ... SELECT pour copier les données.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyMultiple {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationHeaderTable = "dbo.BulkCopyDemoOrderHeader";
        String destinationDetailTable = "dbo.BulkCopyDemoOrderDetail";
        int countHeaderBefore, countDetailBefore, countHeaderAfter, countDetailAfter;
        ResultSet rsHeader, rsDetail;

        try (Connection sourceConnection1 = DriverManager.getConnection(connectionUrl);
                Connection sourceConnection2 = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection1.createStatement();
                PreparedStatement preparedStmt1 = sourceConnection1.prepareStatement(
                        "SELECT [SalesOrderID], [OrderDate], [AccountNumber] FROM [Sales].[SalesOrderHeader] WHERE [AccountNumber] = ?;");
                PreparedStatement preparedStmt2 = sourceConnection2.prepareStatement(
                        "SELECT [Sales].[SalesOrderDetail].[SalesOrderID], [SalesOrderDetailID], [OrderQty], [ProductID], [UnitPrice] FROM "
                                + "[Sales].[SalesOrderDetail] INNER JOIN [Sales].[SalesOrderHeader] ON "
                                + "[Sales].[SalesOrderDetail].[SalesOrderID] = [Sales].[SalesOrderHeader].[SalesOrderID] WHERE [AccountNumber] = ?;");
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(connectionUrl);) {

            // Empty the destination tables.
            stmt.executeUpdate("DELETE FROM " + destinationHeaderTable);
            stmt.executeUpdate("DELETE FROM " + destinationDetailTable);

            // Perform an initial count on the destination
            // table with matching columns.
            countHeaderBefore = getRowCount(stmt, destinationHeaderTable);

            // Perform an initial count on the destination
            // table with different column positions.
            countDetailBefore = getRowCount(stmt, destinationDetailTable);

            // Get data from the source table as a ResultSet.
            // The Sales.SalesOrderHeader and Sales.SalesOrderDetail
            // tables are quite large and could easily cause a timeout
            // if all data from the tables is added to the destination.
            // To keep the example simple and quick, a parameter is
            // used to select only orders for a particular account
            // as the source for the bulk insert.
            preparedStmt1.setString(1, "10-4020-000034");
            rsHeader = preparedStmt1.executeQuery();

            // Get the Detail data in a separate connection.
            preparedStmt2.setString(1, "10-4020-000034");
            rsDetail = preparedStmt2.executeQuery();

            // Create the SQLServerBulkCopySQLServerBulkCopy object.
            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setBulkCopyTimeout(100);
            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationHeaderTable);

            // Guarantee that columns are mapped correctly by
            // defining the column mappings for the order.
            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");
            bulkCopy.addColumnMapping("OrderDate", "OrderDate");
            bulkCopy.addColumnMapping("AccountNumber", "AccountNumber");

            // Write rsHeader to the destination.
            bulkCopy.writeToServer(rsHeader);

            // Set up the order details destination.
            bulkCopy.setDestinationTableName(destinationDetailTable);

            // Clear the existing column mappings
            bulkCopy.clearColumnMappings();

            // Add order detail column mappings.
            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");
            bulkCopy.addColumnMapping("SalesOrderDetailID", "SalesOrderDetailID");
            bulkCopy.addColumnMapping("OrderQty", "OrderQty");
            bulkCopy.addColumnMapping("ProductID", "ProductID");
            bulkCopy.addColumnMapping("UnitPrice", "UnitPrice");

            // Write rsDetail to the destination.
            bulkCopy.writeToServer(rsDetail);

            // Perform a final count on the destination
            // tables to see how many rows were added.
            countHeaderAfter = getRowCount(stmt, destinationHeaderTable);
            countDetailAfter = getRowCount(stmt, destinationDetailTable);

            System.out.println((countHeaderAfter - countHeaderBefore) + " rows were added to the Header table.");
            System.out.println((countDetailAfter - countDetailBefore) + " rows were added to the Detail table.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

## <a name="transaction-and-bulk-copy-operations"></a>Transaction et opérations de copie en bloc

 Les opérations de copie en bloc peuvent être effectuées comme des opérations isolées ou dans le cadre d'une transaction à plusieurs étapes. Cette dernière option permet d'effectuer plusieurs opérations de copie en bloc dans la même transaction ainsi que d'autres opérations de base de données (telles que des insertions, mises à jour et suppressions), tout en étant en mesure de valider ou restaurer toute la transaction.  
  
 Par défaut, une opération de copie en bloc est effectuée comme une opération isolée. L'opération de copie en bloc se produit de façon non transactionnelle, sans possibilité de restauration. Si vous devez restaurer tout ou partie de la copie en bloc en cas d'erreur, vous pouvez utiliser une transaction gérée par SQLServerBulkCopy ou effectuer l'opération de copie en bloc dans une transaction existante.  
  
### <a name="performing-a-non-transacted-bulk-copy-operation"></a>Exécution d'une opération de copie en bloc non transactionnelle

L'application suivante montre ce qui se passe quand une opération de copie en bloc non transactionnelle rencontre une erreur au cours de l'opération.  
  
Dans l’exemple, la table source et la table de destination incluent chacune une colonne d’identité nommée **ProductID**. Le code commence par préparer la table de destination en supprimant toutes les lignes, puis en insérant une ligne dont la colonne **ProductID** existe dans la table source. Par défaut, une nouvelle valeur pour la colonne d'identité est générée dans la table de destination pour chaque ligne ajoutée. Dans cet exemple, quand la connexion est ouverte, une option est définie qui oblige le processus de chargement en bloc à utiliser à la place les valeurs d'identité de la table source.  
  
L’opération de copie en bloc est exécutée avec la propriété **BatchSize** définie avec la valeur 10. Quand l'opération rencontre la ligne non valide, une exception est levée. Dans ce premier exemple, l'opération de copie en bloc est non transactionnel. Tous les lots copiés avant l'erreur sont validés. Le lot contenant la clé dupliquée est restauré et l'opération de copie en bloc est interrompue avant le traitement des autres lots.  
  
> [!NOTE]  
> Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration des tables](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#table-setup). Ce code est fourni pour illustrer la syntaxe pour l'utilisation de SQLServerBulkCopy uniquement. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d'utiliser une instruction Transact-SQL INSERT ... SELECT pour copier les données.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyNonTransacted {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(connectionUrl)) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Add a single row that will result in duplicate key
            // when all rows from source are bulk copied.
            // Note that this technique will only be successful in
            // illustrating the point if a row with ProductID = 446
            // exists in the AdventureWorks Production.Products table.
            // If you have made changes to the data in this table, change
            // the SQL statement in the code to add a ProductID that
            // does exist in your version of the Production.Products
            // table. Choose any ProductID in the middle of the table
            // (not first or last row) to best illustrate the result.
            stmt.executeUpdate("SET IDENTITY_INSERT " + destinationTable + " ON;" + "INSERT INTO " + destinationTable
                    + "([ProductID], [Name] ,[ProductNumber]) VALUES(446, 'Lock Nut 23','LN-3416'); SET IDENTITY_INSERT " + destinationTable
                    + " OFF");

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // Set up the bulk copy object using the KeepIdentity option and BatchSize = 10.
            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setKeepIdentity(true);
            copyOptions.setBatchSize(10);

            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            // This should fail with a duplicate key error
            // after some of the batches have been copied.
            try {
                bulkCopy.writeToServer(rsSourceData);
            }
            catch (SQLException e) {
                e.printStackTrace();
            }

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="performing-a-dedicated-build-copy-operation-in-a-transaction"></a>Exécution d'une opération de copie en bloc dédiée dans une transaction 

Par défaut, une opération de copie en bloc est sa propre transaction. Si vous voulez effectuer une opération de copie en bloc dédiée, créez une instance de SQLServerBulkCopy avec une chaîne de connexion. Dans ce scénario, l'opération de copie en bloc crée, puis valide ou restaure la transaction. Vous pouvez spécifier explicitement l’option **UseInternalTransaction** dans **SQLServerBulkCopyOptions** pour qu’une opération de copie en bloc s’exécute dans sa propre transaction, chaque lot de l’opération de copie en bloc s’exécutant alors dans une transaction distincte.  
  
> [!NOTE]  
> Puisque des lots différents sont exécutés dans différentes transactions, si une erreur se produit pendant l'opération de copie en bloc, toutes les lignes du lot actuel sont restaurées, mais les lignes des lots précédents restent dans la base de données.  
  
Quand vous spécifiez l’option **UseInternalTransaction** dans **BulkCopyNonTransacted**, l’opération de copie en bloc est incluse dans une transaction externe plus grande. Quand l'erreur de violation de clé primaire se produit, toute la transaction est restaurée et aucune ligne n'est ajoutée à la table de destination.

```java
SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
copyOptions.setKeepIdentity(true);
copyOptions.setBatchSize(10);
copyOptions.setUseInternalTransaction(true);
```

### <a name="using-existing-transactions"></a>Utilisation de transactions existantes

Vous pouvez passer un objet Connection dont les transactions sont activées en tant que paramètre dans un constructeur SQLServerBulkCopy. Dans ce cas, l'opération de copie en bloc est effectuée dans une transaction existante, et aucune modification n'est apportée à l'état de la transaction (autrement dit, elle n'est ni validée ni abandonnée). Cela permet à une application d'inclure l'opération de copie en bloc dans une transaction avec d'autres opérations de base de données. Si vous devez restaurer toute l'opération de copie en bloc en raison d'une erreur, ou si la copie en bloc doit s'exécuter dans le cadre d'un processus plus vaste pouvant être restauré, vous pouvez effectuer la restauration de l'objet Connection à tout moment après l'opération de copie en bloc.  
  
L'application suivante est similaire à **BulkCopyNonTransacted**, à une exception près : dans cet exemple, l'opération de copie en bloc est incluse dans une transaction externe plus vaste. Quand l'erreur de violation de clé primaire se produit, toute la transaction est restaurée et aucune ligne n'est ajoutée à la table de destination.

> [!NOTE]  
> Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration des tables](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#table-setup). Ce code est fourni pour illustrer la syntaxe pour l'utilisation de SQLServerBulkCopy uniquement. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d'utiliser une instruction Transact-SQL INSERT ... SELECT pour copier les données.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyExistingTransactions {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;
        SQLServerBulkCopyOptions copyOptions;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection);) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Add a single row that will result in duplicate key
            // when all rows from source are bulk copied.
            // Note that this technique will only be successful in
            // illustrating the point if a row with ProductID = 446
            // exists in the AdventureWorks Production.Products table.
            // If you have made changes to the data in this table, change
            // the SQL statement in the code to add a ProductID that
            // does exist in your version of the Production.Products
            // table. Choose any ProductID in the middle of the table
            // (not first or last row) to best illustrate the result.
            stmt.executeUpdate("SET IDENTITY_INSERT " + destinationTable + " ON;" + "INSERT INTO " + destinationTable
                    + "([ProductID], [Name] ,[ProductNumber]) VALUES(446, 'Lock Nut 23','LN-3416'); SET IDENTITY_INSERT " + destinationTable
                    + " OFF");

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // Set up the bulk copy object inside the transaction.
            destinationConnection.setAutoCommit(false);

            copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setKeepIdentity(true);
            copyOptions.setBatchSize(10);

            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            // This should fail with a duplicate key error.
            try {
                bulkCopy.writeToServer(rsSourceData);
                destinationConnection.commit();
            }
            catch (SQLException e) {
                e.printStackTrace();
            }

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        catch (Exception e) {
            // Handle any errors that may have occurred.
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="bulk-copy-from-a-csv-file"></a>Copie en bloc à partir d'un fichier CSV  

 L'application suivante montre comment charger des données à l'aide de la classe SQLServerBulkCopy. Dans cet exemple, un fichier CSV est utilisé pour copier des données exportées de la table Production.Product de la base de données SQL Server AdventureWorks dans une table semblable de la base de données.  
  
> [!IMPORTANT]  
> Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration des tables](../../ssms/download-sql-server-management-studio-ssms.md).  
  
1. Ouvrez **SQL Server Management Studio**, puis connectez-vous à SQL Server avec la base de données AdventureWorks.  
  
2. Développez les bases de données, cliquez avec le bouton droit sur la base de données AdventureWorks, sélectionnez **Tâches** et **Exporter les données**…  
  
3. Sélectionnez la **Source de données** qui permet de vous connecter à SQL Server (par exemple, SQL Server Native Client 11.0), vérifiez la configuration, puis cliquez sur **Suivant**.  
  
4. Sélectionnez la **Destination de fichier plat** et entrez un **Nom de fichier** avec une destination telle que C:\Test\TestBulkCSVExample.csv. Vérifiez que le **Format** est délimité, que l’**Identificateur de texte** a la valeur aucun, activez **Noms de colonne dans la première ligne de données**, puis sélectionnez **Suivant**.  
  
5. Sélectionnez **Écrire une requête pour spécifier les données à transférer**, puis **Suivant**.  Entrez votre **Instruction SQL** SELECT ProductID, Name, ProductNumber FROM Production.Product et cliquez sur **Suivant**.  
  
6. Vérifiez la configuration : vous pouvez laisser la valeur {CR}{LF} comme séparateur de lignes et la virgule {,} comme séparateur de colonnes.  Sélectionnez **Modifier les mappages**... et vérifiez que le **type** de données est correct pour chaque colonne (par exemple, un entier pour ProductID et une chaîne Unicode pour les autres).  
  
7. Sélectionnez **Terminer** et exécutez l’exportation.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCSVFileRecord;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;

public class BulkCopyCSV {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;

        // Get data from the source file by loading it into a class that implements ISQLServerBulkRecord.
        // Here we are using the SQLServerBulkCSVFileRecord implementation to import the example CSV file.
        try (Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = destinationConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection);
                SQLServerBulkCSVFileRecord fileRecord = new SQLServerBulkCSVFileRecord("C:\\Test\\TestBulkCSVExample.csv", true);) {

            // Set the metadata for each column to be copied.
            fileRecord.addColumnMetadata(1, null, java.sql.Types.INTEGER, 0, 0);
            fileRecord.addColumnMetadata(2, null, java.sql.Types.NVARCHAR, 50, 0);
            fileRecord.addColumnMetadata(3, null, java.sql.Types.NVARCHAR, 25, 0);

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Set up the bulk copy object.
            // Note that the column positions in the source
            // data reader match the column positions in
            // the destination table so there is no need to
            // map columns.
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            bulkCopy.writeToServer(fileRecord);

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```  

### <a name="bulk-copy-with-always-encrypted-columns"></a>Copie en bloc avec des colonnes Always Encrypted  

À partir de Microsoft JDBC Driver 6.0 pour SQL Server, la copie en bloc est prise en charge avec les colonnes Always Encrypted.  
  
Selon les options de copie en bloc et le type de chiffrement des tables source et de destination, le pilote JDBC peut de manière transparente déchiffrer les données, puis les chiffrer, ou il peut envoyer les données chiffrées telles quelles. Par exemple, quand il effectue une copie en bloc de données à partir d’une colonne chiffrée vers une colonne non chiffrée, le pilote déchiffre les données de manière transparente avant de les envoyer à SQL Server. De même, quand il effectue une copie en bloc de données à partir d’une colonne non chiffrée (ou d’un fichier CSV) vers une colonne chiffrée, le pilote chiffre les données de manière transparente avant de les envoyer à SQL Server. Si la source et la destination sont toutes deux chiffrées, selon l’option de copie en bloc **allowEncryptedValueModifications**, le pilote envoie les données telles quelles ou les déchiffre, puis les rechiffre avant de les envoyer à SQL Server.  
  
Pour plus d’informations, consultez l’option de copie en bloc **allowEncryptedValueModifications** ci-dessous et [Utilisation d’Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
> Limites de Microsoft JDBC Driver 6.0 pour SQL Server lors d’une copie en bloc à partir d’un fichier CSV vers des colonnes chiffrées :  
>
> Seul le format de littéral de chaîne par défaut Transact-SQL est pris en charge pour les types de date et d’heure.  
>
> Les types de données DATETIME et SMALLDATETIME ne sont pas pris en charge.  
  
## <a name="bulk-copy-api-for-jdbc-driver"></a>API de copie en bloc pour le pilote JDBC  
  
### <a name="sqlserverbulkcopy"></a>SQLServerBulkCopy 

Vous permet de charger efficacement en bloc une table SQL Server avec des données d'une autre source.  
  
Microsoft SQL Server inclut un utilitaire de ligne de commande connu nommé bcp pour transférer les données d'une table vers une autre, sur un même serveur ou entre plusieurs serveurs. La classe SQLServerBulkCopy vous permet d'écrire des solutions de code en Java, qui fournissent des fonctionnalités similaires. Il existe d'autres façons de charger des données dans une table SQL Server (instructions INSERT, par exemple) mais SQLServerBulkCopy offre de meilleures performances.  
  
La classe SQLServerBulkCopy peut être utilisée pour écrire des données uniquement dans des tables SQL Server. Toutefois, les sources de données ne sont pas limitées à SQL Server : toutes sont utilisables, tant que les données sont lisibles avec une instance ResultSet ou une implémentation ISQLServerBulkRecord.  
  
| Constructeur                             | Description                                                                                                                                                                                                                    |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| SQLServerBulkCopy(Connection)           | Initialise une nouvelle instance de la classe SQLServerBulkCopy à l’aide de l’instance ouverte spécifiée de SQLServerConnection. Si l'instance Connection a des transactions activées, les opérations de copie seront effectuées dans cette transaction. |
| SQLServerBulkCopy(String connectionURL) | Initialise et ouvre une nouvelle instance de SQLServerConnection en fonction de la valeur de connectionURL fournie. Le constructeur utilise SQLServerConnection pour initialiser une nouvelle instance de la classe SQLServerBulkCopy.                     |
  
| Propriété                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| String DestinationTableName | Nom de la table de destination sur le serveur.<br /><br /> Si DestinationTableName n'a pas été défini à l'appel de writeToServer, une exception SQLServerException est levée.<br /><br /> DestinationTableName est un nom en trois parties (\<base_de_données>.\<schéma_propriétaire>.\<nom>). Vous pouvez qualifier le nom de la table avec sa base de données et son schéma propriétaire si vous le souhaitez. Toutefois, si le nom de la table utilise un trait de soulignement (« _ ») ou d'autres caractères spéciaux, vous devez isoler le nom en le plaçant entre crochets. Pour plus d'informations, consultez « Identificateurs » dans la documentation en ligne de SQL Server. |
| ColumnMappings              | Les mappages de colonnes définissent les relations entre les colonnes dans la source de données et dans la destination.<br /><br /> Si les mappages ne sont pas définis, les colonnes sont mappées implicitement selon leur position ordinale. Pour que cela fonctionne, les schémas source et cible doivent correspondre. Si ce n’est pas le cas, une exception est levée.<br /><br /> Si les mappages ne sont pas vides, il n'est pas nécessaire de spécifier toutes les colonnes présentes dans la source de données. Celles qui ne sont pas mappées sont ignorées.<br /><br /> Vous pouvez faire référence aux colonnes source et cible par nom ou par ordinal.               |
  
| Méthode                                                                | Description                                                                                                                                                                |
| --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Void addColumnMapping((int sourceColumn, int destinationColumn)       | Ajoute un nouveau mappage de colonnes, en utilisant les numéros pour spécifier les colonnes source et de destination.                                                                                  |
| Void addColumnMapping ((int sourceColumn, String destinationColumn)   | Ajoute un nouveau mappage de colonnes, en utilisant un numéro pour la colonne source et un nom de colonne pour la colonne de destination.                                                            |
| Void addColumnMapping ((String sourceColumn, int destinationColumn)   | Ajoute un nouveau mappage de colonnes, en utilisant un nom de colonne pour décrire la colonne source et un numéro pour spécifier la colonne de destination.                                             |
| Void addColumnMapping (String sourceColumn, String destinationColumn) | Ajoute un nouveau mappage de colonnes, en utilisant les noms de colonne pour spécifier les colonnes source et de destination.                                                                              |
| Void clearColumnMappings()                                            | Supprime le contenu des mappages de colonnes.                                                                                                                                |
| Void close()                                                          | Ferme l’instance de SQLServerBulkCopy.                                                                                                                                     |
| SQLServerBulkCopyOptions getBulkCopyOptions()                         | Récupère l'ensemble actuel de SQLServerBulkCopyOptions.                                                                                                                     |
| String getDestinationTableName()                                      | Récupère le nom actuel de la table de destination.                                                                                                                               |
| Void setBulkCopyOptions(SQLServerBulkCopyOptions copyOptions)         | Met à jour le comportement de l'instance SQLServerBulkCopy en fonction des options fournies.                                                                                  |
| Void setDestinationTableName(String tableName)                        | Définit le nom de la table de destination.                                                                                                                                    |
| Void writeToServer(ResultSet sourceData)                              | Copie toutes les lignes du ResultSet fourni dans une table de destination spécifiée par la propriété DestinationTableName de l’objet SQLServerBulkCopy.                           |
| Void writeToServer(RowSet sourceData)                                 | Copie toutes les lignes du RowSet fourni dans une table de destination spécifiée par la propriété DestinationTableName de l'objet SQLServerBulkCopy.                              |
| Void writeToServer(ISQLServerBulkRecord sourceData)                   | Copie toutes les lignes de l’implémentation ISQLServerBulkRecord fournie dans une table de destination spécifiée par la propriété DestinationTableName de l’objet SQLServerBulkCopy. |
  
### <a name="sqlserverbulkcopyoptions"></a>SQLServerBulkCopyOptions  

 Collection de paramètres qui contrôlent le comportement des méthodes writeToServer dans une instance de SQLServerBulkCopy.  
  
| Constructeur                | Description                                                                                              |
| -------------------------- | -------------------------------------------------------------------------------------------------------- |
| SQLServerBulkCopyOptions() | Initialise une nouvelle instance de la classe SQLServerBulkCopyOptions à l’aide des valeurs par défaut pour tous les paramètres. |
  
 Des accesseurs Get et Set existent pour les options suivantes :  
  
| Option                                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Valeur par défaut                                                              |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Boolean CheckConstraints                 | Vérifie les contraintes pendant l'insertion des données.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | False : les contraintes ne sont pas vérifiées                                   |
| Boolean FireTriggers                     | Si spécifié, entraîne l'exécution par le serveur des déclencheurs d'insertion pour les lignes insérées dans la base de données.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | False : aucun déclencheur n'est exécuté                                        |
| Boolean KeepIdentity                     | Conserve les valeurs d'identité sources.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | False : les valeurs d'identité sont attribuées par la destination              |
| Boolean KeepNulls                        | Conserve les valeurs null dans la table de destination, indépendamment des paramètres des valeurs par défaut.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | False : les valeurs null sont remplacées par les valeurs par défaut, le cas échéant. |
| Boolean TableLock                        | Obtient un verrou de mise à jour en bloc pour la durée de l'opération de copie en bloc.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | False : les verrous de ligne sont utilisés.                                          |
| Boolean UseInternalTransaction           | Si spécifié, chaque lot de l'opération de copie en bloc se produit dans une transaction. Si SQLServerBulkCopy utilise une connexion existante (comme spécifié par le constructeur), une exception SQLServerException se produit.  Si SQLServerBulkCopy a créé une connexion dédiée, une transaction est activée.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | False : aucune transaction                                               |
| Int BatchSize                            | Nombre de lignes dans chaque lot. À la fin de chaque lot, les lignes du lot sont envoyées au serveur.<br /><br /> Un lot est terminé quand les lignes BatchSize ont été traitées ou qu'il n'y a plus de ligne à envoyer à la source de données de destination.  Si l'instance de SQLServerBulkCopy a été déclarée sans activer l'option UseInternalTransaction, une ligne BatchSize à la fois est envoyée au serveur, mais aucune action relative à la transaction n'est effectuée. Si UseInternalTransaction est activé, chaque lot de lignes est inséré comme une transaction distincte.                                                                                                                                                                                                                                                                                                                                                                                                                                           | 0 : indique que chaque opération writeToServer est un lot unique    |
| Int BulkCopyTimeout                      | Nombre de secondes pour terminer l'opération avant son expiration. La valeur 0 indique qu'il n'y a aucune limite : la copie en bloc attend indéfiniment.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 60 secondes.                                                          |
| Boolean allowEncryptedValueModifications | Cette option est disponible avec Microsoft JDBC Driver 6.0 (ou version supérieure) pour SQL Server.<br /><br /> Si elle est spécifiée, **allowEncryptedValueModifications** permet la copie en bloc de données chiffrées entre des tables ou bases de données, sans déchiffrer les données. En règle générale, une application sélectionne les données à partir de colonnes chiffrées d’une table sans déchiffrer les données (elle se connecte à la base de données avec le mot-clé de paramètre de chiffrement de colonne défini sur « Enabled »), puis utilise cette option pour insérer les données en bloc, qui sont toujours chiffrées. Pour plus d’informations, consultez [Utilisation de Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).<br /><br /> Faites attention quand vous spécifiez **allowEncryptedValueModifications**, car cela pourrait endommager la base de données. En effet, le pilote ne vérifie pas si les données sont chiffrées, ou si elles le sont avec le même type de chiffrement, le même algorithme et la même clé que la colonne cible. |
  
 Getters et setters :  
  
| Méthodes                                                                            | Description                                                                                                                                                                               |
| ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Boolean isCheckConstraints()                                                       | Indique si les contraintes doivent être vérifiées quand des données sont insérées ou non.                                                                                                      |
| Void setCheckConstraints(Boolean checkConstraints)                                 | Définit si les contraintes doivent être vérifiées quand des données sont insérées ou non.                                                                                                           |
| Boolean isFireTriggers()                                                           | Indique si le serveur doit exécuter des déclencheurs d’insertion pour les lignes insérées dans la base de données.                                                                                    |
| Void setFireTriggers(Boolean fireTriggers)                                         | Définit si le serveur doit être configuré afin d’exécuter des déclencheurs pour les lignes insérées dans la base de données.                                                                                     |
| Boolean isKeepIdentity()                                                           | Indique s’il faut conserver les valeurs d’identité sources.                                                                                                                          |
| Void setKeepIdentity(Boolean keepIdentity)                                         | Définit s’il faut conserver les valeurs d’identité.                                                                                                                                          |
| Boolean isKeepNulls()                                                              | Indique s’il faut conserver les valeurs Null dans la table de destination quels que soient les paramètres des valeurs par défaut, ou si elles doivent être remplacées par les valeurs par défaut (le cas échéant). |
| Void setKeepNulls(Boolean keepNulls)                                               | Définit s’il faut conserver les valeurs Null dans la table de destination quels que soient les paramètres des valeurs par défaut, ou si elles doivent être remplacées par les valeurs par défaut (le cas échéant).      |
| Boolean isTableLock()                                                              | Indique si SQLServerBulkCopy doit obtenir un verrou de mise à jour en bloc pour la durée de l’opération de copie en bloc.                                                                         |
| Void setTableLock(Boolean tableLock)                                               | Définit si SQLServerBulkCopy doit obtenir un verrou de mise à jour en bloc pour la durée de l’opération de copie en bloc.                                                                              |
| Boolean isUseInternalTransaction()                                                 | Indique si chaque lot de l’opération de copie en bloc se produit dans une transaction.                                                                                                  |
| Void setUseInternalTranscation(Boolean useInternalTransaction)                     | Indique si chaque lot des opérations de copie en bloc se produit ou non dans une transaction.                                                                                               |
| Int getBatchSize()                                                                 | Obtient le nombre de lignes dans chaque lot. À la fin de chaque lot, les lignes du lot sont envoyées au serveur.                                                                             |
| Void setBatchSize(int batchSize)                                                   | Définit le nombre de lignes dans chaque lot. À la fin de chaque lot, les lignes du lot sont envoyées au serveur.                                                                            |
| Int getBulkCopyTimeout()                                                           | Obtient le nombre de secondes pour terminer l’opération avant son expiration.                                                                                                             |
| Void  setBulkCopyTimeout(int timeout)                                              | Définit le nombre de secondes pour terminer l’opération avant son expiration.                                                                                                             |
| boolean isAllowEncryptedValueModifications()                                       | Indique si le paramètre allowEncryptedValueModifications est activé ou désactivé.                                                                                                        |
| void setAllowEncryptedValueModifications(boolean allowEncryptedValueModifications) | Configure le paramètre allowEncryptedValueModifications qui est utilisé pour la copie en bloc avec des colonnes Always Encrypted.                                                                         |
  
### <a name="isqlserverbulkrecord"></a>ISQLServerBulkRecord  

 L'interface ISQLServerBulkRecord peut être utilisée pour créer des classes qui lisent les données de n'importe quelle source (par exemple un fichier) et autorisent une instance de SQLServerBulkCopy à charger en bloc une table SQL Server avec ces données.  
  
| Méthodes d'interface                   | Description                                                                                                                                                                                                                                                                                            |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Set\<Integer> getColumnOrdinals()   | Obtient les ordinaux de chacune des colonnes représentées dans cet enregistrement de données.                                                                                                                                                                                                                              |
| String getColumnName(int column)    | Obtient le nom de la colonne spécifiée.                                                                                                                                                                                                                                                                      |
| Int getColumnType(int column)       | Obtient le type de données JDBC de la colonne spécifiée.                                                                                                                                                                                                                                                            |
| Int getPrecision(int column)        | Obtient la précision de la colonne spécifiée.                                                                                                                                                                                                                                                                |
| Object[] getRowData()               | Obtient les données de la ligne active en tant que tableau d'objets.<br /><br /> Chaque objet doit correspondre au type de langage Java utilisé pour représenter le type de données JDBC indiqué pour la colonne spécifiée.  Pour plus d'informations, consultez « Présentation des types de données du pilote JDBC » pour les mappages appropriés. |
| Int getScale(int column)            | Obtient l'échelle de la colonne spécifiée.                                                                                                                                                                                                                                                                    |
| Boolean isAutoIncrement(int column) | Indique si la colonne représente une colonne d'identité.                                                                                                                                                                                                                                            |
| Boolean next()                      | Accède à la ligne de données suivante.                                                                                                                                                                                                                                                                         |
  
### <a name="sqlserverbulkcsvfilerecord"></a>SQLServerBulkCSVFileRecord  

Implémentation simple de l'interface ISQLServerBulkRecord qui peut être utilisée pour lire les types de données Java de base à partir d'un fichier délimité, où chaque ligne représente une ligne de données.  
  
Notes et limitations de l'implémentation :  
  
1. la quantité maximale de données autorisées dans une ligne donnée est limitée par la mémoire disponible, car les données sont lues une ligne à la fois.  
  
2. La diffusion en continu de types de données volumineux comme varchar(max), varbinary(max), nvarchar(max), sqlxml et ntext n'est pas prise en charge.  
  
3. Le séparateur spécifié pour le fichier CSV ne doit apparaître nulle part dans les données ; il doit être placé dans une séquence d'échappement adaptée s'il s'agit d'un caractère restreint dans les expressions régulières Java.  
  
4. Dans l'implémentation de fichier CSV, les guillemets doubles sont traités comme faisant partie des données. Par exemple, la ligne hello,« world »,« hello,world » est considérée comme ayant quatre colonnes avec les valeurs hello, « world », « hello et world » si le séparateur est une virgule.  
  
5. Les caractères de nouvelle ligne sont utilisés comme indicateurs de fin de ligne ; ils ne sont autorisés nulle part dans les données.  
  
| Constructeur                                                                                                                                                                 | Description                                                                                                                                                                                                                                                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SQLServerBulkCSVFileRecord(String fileToParse, String encoding, String delimiter, Boolean firstLineIsColumnNamesSQLServerBulkCSVFileRecord(String, String, String, boolean) | Initialise une nouvelle instance de la classe SQLServerBulkCSVFileRecord qui analyse chaque ligne du fileToParse avec le séparateur et le codage fournis. Si firstLineIsColumnNames a la valeur True, la première ligne du fichier est analysée en tant que noms de colonne.  Si le codage est NULL, le codage par défaut est utilisé.            |
| SQLServerBulkCSVFileRecord(String fileToParse, String encoding, Boolean firstLineIsColumnNamesSQLServerBulkCSVFileRecord(String, String, boolean)                           | Initialise une nouvelle instance de la classe SQLServerBulkCSVFileRecord qui analyse chaque ligne de fileToParse avec une virgule comme séparateur et le codage fourni. Si firstLineIsColumnNames a la valeur True, la première ligne du fichier est analysée en tant que noms de colonne.  Si le codage est NULL, le codage par défaut est utilisé. |
| SQLServerBulkCSVFileRecord(String fileToParse, Boolean firstLineIsColumnNamesSQLServerBulkCSVFileRecord(String, boolean)                                                    | Initialise une nouvelle instance de la classe SQLServerBulkCSVFileRecord qui analyse chaque ligne de fileToParse avec une virgule comme séparateur et l'encodage par défaut. Si firstLineIsColumnNames a la valeur True, la première ligne du fichier est analysée en tant que noms de colonne.                                                           |
  
| Méthode                                                                                                 | Description                                                                                         |
| ------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| Void addColumnMetadata(int positionInFile, String columnName, int jdbcType, int precision, int scale)  | Ajoute des métadonnées pour la colonne indiquée dans le fichier.                                                     |
| Void close()                                                                                           | Libère les ressources associées au lecteur de fichier.                                             |
| Void setTimestampWithTimezoneFormat(DateTim eFormatter dateTimeFormatter                               | Définit le format pour l'analyse des données d'horodatage du fichier en tant que java.sql.Types.TIMESTAMP_WITH_TIMEZONE. |
| Void setTimestampWithTimezoneFormat(String dateTimeFormat)setTimeWithTimezoneFormat(DateTimeFormatter) | Définit le format pour l'analyse des données d'heure du fichier en tant que java.sql.Types.TIME_WITH_TIMEZONE.           |
| Void setTimeWithTimezoneFormat(DateTimeFormatter dateTimeFormatter)                                   | Définit le format pour l'analyse des données d'heure du fichier en tant que java.sql.Types.TIME_WITH_TIMEZONE.           |
| Void setTimeWithTimezoneFormat(String timeFormat)                                                      | Définit le format pour l'analyse des données d'heure du fichier en tant que java.sql.Types.TIME_WITH_TIMEZONE.           |
  
## <a name="see-also"></a>Voir aussi  

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
