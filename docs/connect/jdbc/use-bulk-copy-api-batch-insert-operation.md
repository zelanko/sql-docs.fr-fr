---
title: Utilisation de l’API de copie en bloc pour l’opération d’insertion de lot pour le pilote MSSQL JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3050cdf87775a67618902dfbb88b656003020769
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027106"
---
# <a name="using-bulk-copy-api-for-batch-insert-operation"></a>Utilisation de l'API de copie en bloc pour l'opération d'insertion par lot

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le pilote Microsoft JDBC 7,0 pour SQL Server prend en charge l’utilisation de l’API de copie en bloc pour les opérations d’insertion de lot pour Azure Data Warehouse. Cette fonctionnalité permet aux utilisateurs d’autoriser le pilote à effectuer une opération de copie en bloc sous-jacente lors de l’exécution des opérations d’insertion de lot. Le pilote vise à améliorer les performances lors de l’insertion des mêmes données que celles que le pilote aurait avec l’opération d’insertion de lot normale. Le pilote analyse la requête SQL de l’utilisateur, en tirant parti de l’API de copie en bloc au lieu de l’opération d’insertion de lot habituelle. Vous trouverez ci-dessous différentes façons d’activer l’API de copie en bloc pour la fonctionnalité d’insertion de lot, ainsi que la liste de ses limitations. Cette page contient également un petit exemple de code qui illustre une utilisation et l’augmentation des performances.

Cette fonctionnalité s’applique uniquement aux API de PreparedStatement et `executeBatch()` de  &  `executeLargeBatch()` CallableStatement.

## <a name="prerequisites"></a>Conditions préalables requises

Il existe deux conditions préalables à l’activation de l’API de copie en bloc pour l’insertion de lot.

* Le serveur doit être Azure Data Warehouse.
* La requête doit être une requête Insert (la requête peut contenir des commentaires, mais la requête doit commencer par le mot clé INSERT pour que cette fonctionnalité soit prise en compte).

## <a name="enabling-bulk-copy-api-for-batch-insert"></a>Activation de l’API de copie en bloc pour l’insertion de lot

Il existe trois façons d’activer l’API de copie en bloc pour l’insertion de lot.

### <a name="1-enabling-with-connection-property"></a>1. Activation avec la propriété de connexion

L’ajout de **useBulkCopyForBatchInsert = true;** à la chaîne de connexion active cette fonctionnalité.

```java
Connection connection = DriverManager.getConnection("jdbc:sqlserver://<server>:<port>;userName=<user>;password=<password>;database=<database>;useBulkCopyForBatchInsert=true;");
```

### <a name="2-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverconnection-object"></a>2. Activation avec la méthode setUseBulkCopyForBatchInsert () à partir de l’objet SQLServerConnection

L’appel **de SQLServerConnection. setUseBulkCopyForBatchInsert (true)** active cette fonctionnalité.

**SQLServerConnection. getUseBulkCopyForBatchInsert ()** récupère la valeur actuelle de la propriété de connexion **useBulkCopyForBatchInsert** .

La valeur de **useBulkCopyForBatchInsert** reste constante pour chaque PreparedStatement au moment de son initialisation. Les appels suivants à **SQLServerConnection. setUseBulkCopyForBatchInsert ()** n’affecteront pas l’PreparedStatement déjà créé en ce qui concerne sa valeur.

### <a name="3-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverdatasource-object"></a>3. Activation avec la méthode setUseBulkCopyForBatchInsert () à partir de l’objet SQLServerDataSource

Semblable à ci-dessus, mais à l’aide de SQLServerDataSource pour créer un objet SQLServerConnection. Les deux méthodes permettent d’obtenir le même résultat.

## <a name="known-limitations"></a>Limitations connues

Ces limitations s’appliquent actuellement à cette fonctionnalité.

* Les requêtes INSERT qui contiennent des valeurs non paramétrables (par exemple `INSERT INTO TABLE VALUES (?, 2`,)) ne sont pas prises en charge. Les caractères génériques (?) sont les seuls paramètres pris en charge pour cette fonction.
* Les requêtes INSERT qui contiennent des expressions Insert-Select (par `INSERT INTO TABLE SELECT * FROM TABLE2`exemple,) ne sont pas prises en charge.
* Les requêtes INSERT qui contiennent plusieurs expressions de valeur (par `INSERT INTO TABLE VALUES (1, 2) (3, 4)`exemple,) ne sont pas prises en charge.
* Les requêtes d’insertion qui sont suivies par la clause OPTION, jointes à plusieurs tables ou suivies d’une autre requête, ne sont pas prises en charge.
* En raison des limitations de l’API de copie `MONEY`en `SMALLMONEY`bloc `DATE`, `DATETIME` `SMALLDATETIME` `DATETIMEOFFSET` `TIME`,,,,,, `GEOGRAPHY` ,, et des types de données, ne sont actuellement pas pris en charge pour ce `GEOMETRY` fonctionnalité.

Si la requête échoue en raison d’erreurs liées à «SQL Server», le pilote consigne le message d’erreur et le fait revenir à la logique d’origine pour l’insertion de lot.

## <a name="example"></a>Exemple

Voici un exemple de code qui illustre le cas d’usage d’une opération d’insertion par lot sur Azure DW d’un millier de lignes, pour les deux scénarios (API de copie en bloc et standard).

```java
    public static void main(String[] args) throws Exception
    {
        String tableName = "batchTest";
        String tableNameBulkCopyAPI = "batchTestBulk";

        String azureDWconnectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(azureDWconnectionUrl); // connects to an Azure Data Warehouse.
                Statement stmt = con.createStatement();
                PreparedStatement pstmt = con.prepareStatement("insert into " + tableName + " values (?, ?)");) {

            String dropSql = "if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[" + tableName + "]') and OBJECTPROPERTY(id, N'IsUserTable') = 1) DROP TABLE [" + tableName + "]";
            stmt.execute(dropSql);

            String createSql = "create table " + tableName + " (c1 int, c2 varchar(20))";
            stmt.execute(createSql);

            System.out.println("Starting batch operation using regular batch insert operation.");
            long start = System.currentTimeMillis();
            for (int i = 0; i < 1000; i++) {
                pstmt.setInt(1, i);
                pstmt.setString(2, "test" + i);
                pstmt.addBatch();
            }
            pstmt.executeBatch();

            long end = System.currentTimeMillis();

            System.out.println("Finished. Time taken : " + (end - start) + " milliseconds.");
        }

        try (Connection con = DriverManager.getConnection(azureDWconnectionUrl + ";useBulkCopyForBatchInsert=true"); // connects to an Azure Data Warehouse, with useBulkCopyForBatchInsert connection property set to true.
                Statement stmt = con.createStatement();
                PreparedStatement pstmt = con.prepareStatement("insert into " + tableNameBulkCopyAPI + " values (?, ?)");) {

            String dropSql = "if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[" + tableNameBulkCopyAPI + "]') and OBJECTPROPERTY(id, N'IsUserTable') = 1) DROP TABLE [" + tableNameBulkCopyAPI + "]";
            stmt.execute(dropSql);

            String createSql = "create table " + tableNameBulkCopyAPI + " (c1 int, c2 varchar(20))";
            stmt.execute(createSql);

            System.out.println("Starting batch operation using Bulk Copy API.");
            long start = System.currentTimeMillis();
            for (int i = 0; i < 1000; i++) {
                pstmt.setInt(1, i);
                pstmt.setString(2, "test" + i);
                pstmt.addBatch();
            }
            pstmt.executeBatch();

            long end = System.currentTimeMillis();

            System.out.println("Finished. Time taken : " + (end - start) + " milliseconds.");
        }
    }
```

Résultat :

```bash
Starting batch operation using regular batch insert operation.
Finished. Time taken : 104132 milliseconds.
Starting batch operation using Bulk Copy API.
Finished. Time taken : 1058 milliseconds.
```

## <a name="see-also"></a>Voir aussi

[Amélioration des performances et de la fiabilité avec le pilote JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
