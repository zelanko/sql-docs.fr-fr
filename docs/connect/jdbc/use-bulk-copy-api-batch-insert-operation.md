---
title: À l’aide des API de copie en bloc pour l’opération d’insertion de lot pour le pilote JDBC de MSSQL | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b205e27f24693a2dfaa6fcff2245cf45288a12b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696559"
---
# <a name="using-bulk-copy-api-for-batch-insert-operation"></a>Utilisation de l’API de copie en bloc pour l’opération d’insertion par lot

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC Driver 7.0 pour prend en charge de SQL Server à l’aide des API de copie en bloc pour les opérations d’insertion de lot d’Azure Data Warehouse. Cette fonctionnalité permet aux utilisateurs d’activer le pilote à effectuer l’opération de copie en bloc en dessous de l’exécution de lot lorsque les opérations d’insertion. Les objectifs du pilote pour améliorer les performances lors de l’insertion les mêmes données que le pilote aurait avec batch régulière l’opération d’insertion. Le pilote analyse la requête SQL de l’utilisateur, en tirant parti de l’API de copie en bloc à la place de l’opération d’insertion de lot habituel. Voici les différentes manières d’activer l’API de copie en bloc pour le traitement par lots insèrent la fonctionnalité, ainsi que la liste de ses limites. Cette page contient également un petit exemple de code qui illustre une utilisation et l’augmentation des performances.

Cette fonctionnalité s’applique uniquement aux PreparedStatement et de CallableStatement `executeBatch()`  &  `executeLargeBatch()` API.

## <a name="pre-requisites"></a>Conditions préalables

Il existe deux conditions préalables pour activer l’API de copie en bloc pour l’insertion de lot.

* Le serveur doit être Azure Data Warehouse.
* La requête doit être une requête insert (la requête peut contenir des commentaires, mais la requête doit commencer par le mot clé INSERT pour cette fonctionnalité entrent en vigueur).

## <a name="enabling-bulk-copy-api-for-batch-insert"></a>L’activation de l’API de copie en bloc pour l’insertion de lot

Il existe trois façons d’activer les API de copie en bloc pour l’insertion de lot.

### <a name="1-enabling-with-connection-property"></a>1. Activation de la propriété de connexion

Ajout de **useBulkCopyForBatchInsert = true ;** à la connexion chaîne Active cette fonctionnalité.

```java
Connection connection = DriverManager.getConnection("jdbc:sqlserver://<server>:<port>;userName=<user>;password=<password>;database=<database>;useBulkCopyForBatchInsert=true;");
```

### <a name="2-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverconnection-object"></a>2. Activation de la méthode setUseBulkCopyForBatchInsert() à partir de l’objet SQLServerConnection

Appel **SQLServerConnection.setUseBulkCopyForBatchInsert(true)** active cette fonctionnalité.

**SQLServerConnection.getUseBulkCopyForBatchInsert()** récupère la valeur actuelle pour **useBulkCopyForBatchInsert** propriété de connexion.

La valeur de **useBulkCopyForBatchInsert** reste constante pour chaque PreparedStatement au moment de son initialisation. Tous les appels suivants à **SQLServerConnection.setUseBulkCopyForBatchInsert()** n’affecteront pas la PreparedStatement déjà créée en ce qui concerne sa valeur.

### <a name="3-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverdatasource-object"></a>3. Activation de la méthode setUseBulkCopyForBatchInsert() à partir de l’objet SQLServerDataSource

Similaire à ci-dessus, mais à l’aide de SQLServerDataSource pour créer un objet SQLServerConnection. Les deux méthodes permettent d’obtenir le même résultat.

## <a name="known-limitations"></a>Limitations connues

Il existe actuellement ces limitations s’appliquent à cette fonctionnalité.

* Insérer des requêtes qui contiennent des valeurs non paramétrées (par exemple, `INSERT INTO TABLE VALUES (?, 2`)), ne sont pas pris en charge. Les caractères génériques ( ?) sont les seuls paramètres pris en charge pour cette fonction.
* Les requêtes qui contiennent des expressions de INSERT-SELECT Insert (par exemple, `INSERT INTO TABLE SELECT * FROM TABLE2`), ne sont pas pris en charge.
* Insérer des requêtes qui contiennent plusieurs expressions de valeur (par exemple, `INSERT INTO TABLE VALUES (1, 2) (3, 4)`), ne sont pas pris en charge.
* Requêtes INSERT qui sont suivies par la clause OPTION, jointe avec plusieurs tables ou suivies d’une autre requête, ne sont pas pris en charge.
* En raison des limitations de l’API de copie en bloc, `DATETIME`, `SMALLDATETIME`,`GEOMETRY`, et `GEOGRAPHY` des types de données, ne sont pas pris en charge pour cette fonctionnalité.

Si la requête échoue en raison de non erreurs concernant les « SQL server », le pilote enregistrera le message d’erreur et de secours à la logique d’origine pour l’insertion de lot.

## <a name="example"></a> Exemple

Voici un exemple de code qui illustre le cas d’utilisation pour une opération d’insertion par lots dans Azure DW un millier de lignes, pour les deux scénarios (régulière vs API de copie en bloc).

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

## <a name="see-also"></a> Voir aussi

[Amélioration des performances et de la fiabilité avec le pilote JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
