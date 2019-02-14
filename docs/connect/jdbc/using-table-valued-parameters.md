---
title: À l’aide des paramètres table | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57fa8d097b2a6cedc5bf96dc4ee75471c7d27266
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737020"
---
# <a name="using-table-valued-parameters"></a>Utilisation de paramètres table

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données. Vous pouvez utiliser des paramètres table pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique. Les lignes de données entrantes sont stockées dans une variable de table qui peut ensuite être traitée à l’aide de Transact-SQL.  
  
Les valeurs de colonne dans les paramètres table sont accessibles à l’aide d’instructions Transact-SQL SELECT standard. Paramètres table sont fortement typés et leur structure est automatiquement validée. La taille des paramètres table est limitée uniquement par la mémoire du serveur.  
  
> [!NOTE]  
> Prise en charge des paramètres table est disponible à partir de Microsoft JDBC Driver 6.0 pour SQL Server.
>
> Vous ne pouvez pas retourner des données dans un paramètre table. Paramètres table sont entrée uniquement ; le mot clé OUTPUT n’est pas pris en charge.  
  
 Pour plus d’informations sur les paramètres table, consultez les ressources suivantes.  
  
| Ressource                                                                                                             | Description                                                                         |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [Paramètres table (moteur de base de données)](https://go.microsoft.com/fwlink/?LinkId=98363) dans la documentation en ligne de SQL Server | Décrit comment créer et utiliser des paramètres table                             |
| [Types de tables définis par l’utilisateur](https://go.microsoft.com/fwlink/?LinkId=98364) dans la documentation en ligne de SQL Server                  | Décrit les types de table défini par l’utilisateur qui sont utilisés pour déclarer des paramètres table |
| Le [moteur de base de données Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=120507) section de CodePlex        | Contient des exemples qui montrent comment utiliser les fonctionnalités de SQL Server  |
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Passer plusieurs lignes dans les Versions précédentes de SQL Server  

Avant que les paramètres table ont été introduites dans SQL Server 2008, les options pour passer plusieurs lignes de données à une procédure stockée ou une commande SQL paramétrée étaient limitées. Un développeur peut choisir parmi les options suivantes pour passer plusieurs lignes pour le serveur :  
  
- Utiliser une série de paramètres individuels pour représenter les valeurs dans plusieurs colonnes et lignes de données. La quantité de données qui peuvent être passées à l’aide de cette méthode est limitée par le nombre de paramètres autorisés. Procédures SQL Server peuvent avoir au maximum 2 100 paramètres. Côté serveur logique est requise pour assembler ces valeurs individuelles dans une variable de table ou une table temporaire pour le traitement.  
  
- Regrouper plusieurs valeurs de données dans des chaînes délimitées ou des documents XML, puis transmettre ces valeurs de texte à une procédure ou une instruction. Cela requiert que la procédure ou une instruction d’inclure la logique nécessaire permettant de valider les structures de données et de dégrouper les valeurs.  
  
- Créer une série d’instructions SQL individuelles pour les modifications de données qui affectent plusieurs lignes. Modifications peuvent être envoyées au serveur individuellement ou regroupées. Toutefois, même lors de l’envoi par lots qui contiennent plusieurs instructions, chaque instruction est exécutée séparément sur le serveur.  
  
- Utilisez l’utilitaire bcp ou la [SQLServerBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy(v=vs.110).aspx) objet pour charger plusieurs lignes de données dans une table. Bien que cette technique est très efficace, il ne prend pas en charge côté serveur de traitement, sauf si les données sont chargées dans une table temporaire ou une variable de table.  
  
## <a name="creating-table-valued-parameter-types"></a>Création de Types de paramètre table  

Paramètres table sont basés sur les structures de table fortement typées qui sont définies à l’aide de Transact-SQL `CREATE TYPE` instructions. Vous devez créer un type de table et de définir la structure dans SQL Server avant de pouvoir utiliser des paramètres table dans vos applications clientes. Pour plus d’informations sur la création des types de tables, consultez [les Types de tables définis par l’utilisateur](https://go.microsoft.com/fwlink/?LinkID=98364) dans la documentation en ligne de SQL Server.  

```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```

Après avoir créé un type de table, vous pouvez déclarer des paramètres table en fonction de ce type. Le fragment de Transact-SQL suivant montre comment déclarer un paramètre table dans une définition de procédure stockée. Notez que le `READONLY` mot clé est obligatoire pour déclarer un paramètre table.  

```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```

## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modification des données avec les paramètres table (Transact-SQL)  

Paramètres table peuvent être utilisés dans les modifications de données basée sur un jeu qui affectent plusieurs lignes en exécutant une instruction unique. Par exemple, vous pouvez sélectionner toutes les lignes dans un paramètre table et les insérer dans une table de base de données, ou vous pouvez créer une instruction de mise à jour en joignant un paramètre table à la table que vous souhaitez mettre à jour.  
  
L’instruction Transact-SQL UPDATE suivante montre comment utiliser un paramètre table en le joignant à la table Categories. Lorsque vous utilisez un paramètre table avec une jointure dans une clause FROM, vous devez également créer des alias, comme indiqué ici, où le paramètre table est un alias « EC » :  

```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```

Cet exemple Transact-SQL montre comment sélectionner les lignes à partir d’un paramètre table pour effectuer une insertion dans une seule opération basée sur un jeu.

```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```

## <a name="limitations-of-table-valued-parameters"></a>Limitations des paramètres table

Il existe plusieurs limitations pour les paramètres table :  
  
- Vous ne pouvez pas passer des paramètres table pour les fonctions définies par l’utilisateur.  
  
- Paramètres table peuvent uniquement être indexés pour prendre en charge les contraintes UNIQUE ou PRIMARY KEY. SQL Server ne tient pas à jour de statistiques sur les paramètres table.  
  
- Paramètres table sont en lecture seule dans le code Transact-SQL. Vous ne pouvez pas mettre à jour les valeurs de colonne dans les lignes d’un paramètre table et que vous ne pouvez pas insérer ou supprimer des lignes. Pour modifier les données qui sont passées à une procédure stockée ou instruction paramétrée dans le paramètre table, vous devez insérer les données dans une table temporaire ou dans une variable de table.  
  
- Vous ne pouvez pas utiliser les instructions ALTER TABLE pour modifier la conception de paramètres table.

- Vous pouvez diffuser des objets volumineux dans un paramètre table.  
  
## <a name="configuring-a-table-valued-parameter"></a>Configuration d’un paramètre table

À compter du pilote Microsoft JDBC 6.0 pour SQL Server, les paramètres table sont pris en charge avec une instruction paramétrable ou une procédure stockée paramétrable. Paramètres table pouvant être remplis à partir d’un SQLServerDataTable, à partir d’un jeu de résultats ou à partir d’un utilisateur de l’implémentation de l’interface ISQLServerDataRecord. Lorsque vous définissez un paramètre table pour une requête préparée, vous devez spécifier un nom de type qui doit correspondre au nom d’un type compatible précédemment créé sur le serveur.  
  
Les fragments de deux fichiers de code suivants montrent comment configurer un paramètre table avec un SQLServerPreparedStatement et un SQLServerCallableStatement pour insérer des données. Ici, sourceTVPObject peut être un SQLServerDataTable, ou un jeu de résultats ou un objet ISQLServerDataRecord. Les exemples supposent que la connexion est un objet de connexion actif.  

```java
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =
    (SQLServerPreparedStatement) connection.prepareStatement("INSERT INTO dbo.Categories SELECT * FROM ?");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);  
pStmt.execute();  
```

```java
// Using table-valued parameter with a SQLServerCallableStatement.  
SQLServerCallableStatement pStmt =
    (SQLServerCallableStatement) connection.prepareCall("exec usp_InsertCategories ?");
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);;  
pStmt.execute();  
```

> [!NOTE]  
> Consultez la Section **API de paramètre table pour le pilote JDBC** ci-dessous pour obtenir la liste complète des API disponibles pour définir le paramètre table.  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>En passant un paramètre table en tant qu’objet SQLServerDataTable  

À compter du pilote Microsoft JDBC 6.0 pour SQL Server, la classe SQLServerDataTable représente une table en mémoire de données relationnelles. Cet exemple montre comment construire un paramètre table à partir des données en mémoire à l’aide de l’objet SQLServerDataTable. Le code tout d’abord crée un objet SQLServerDataTable, définit son schéma et remplit la table avec des données. Le code configure ensuite un SQLServerPreparedStatement qui passe de cette table de données comme un paramètre table à SQL Server.  

```java
/* Assumes connection is an active Connection object. */

// Create an in-memory data table.  
SQLServerDataTable sourceDataTable = new SQLServerDataTable();
  
// Define metadata for the data table.  
sourceDataTable.addColumnMetadata("CategoryID" ,java.sql.Types.INTEGER);
sourceDataTable.addColumnMetadata("CategoryName" ,java.sql.Types.NVARCHAR);
  
// Populate the data table.  
sourceDataTable.addRow(1, "CategoryNameValue1");
sourceDataTable.addRow(2, "CategoryNameValue2");
  
// Pass the data table as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
            "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceDataTable);  
pStmt.execute();  
```

> [!NOTE]  
> Consultez la Section **API de paramètre table pour le pilote JDBC** ci-dessous pour obtenir la liste complète des API disponibles pour définir le paramètre table.  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>En passant un paramètre table en tant qu’objet ResultSet  

Cet exemple montre comment diffuser des lignes de données à partir d’un jeu de résultats à un paramètre table. Le code récupère tout d’abord les données d’une table source dans un crée un objet SQLServerDataTable, définit son schéma et remplit la table avec des données. Le code configure ensuite un SQLServerPreparedStatement qui passe de cette table de données comme un paramètre table à SQL Server.  

```java
/* Assumes connection is an active Connection object. */

// Create the source ResultSet object. Here SourceCategories is a table defined with the same schema as Categories table.
ResultSet sourceResultSet = connection.createStatement().executeQuery("SELECT * FROM SourceCategories");  

// Pass the source result set as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceResultSet);  
pStmt.execute();  
```

> [!NOTE]  
> Consultez la Section **API de paramètre table pour le pilote JDBC** ci-dessous pour obtenir la liste complète des API disponibles pour définir le paramètre table.  

## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>En passant un paramètre table comme un objet ISQLServerDataRecord  

À compter du pilote Microsoft JDBC 6.0 pour SQL Server, une nouvelle interface ISQLServerDataRecord est disponible pour la diffusion en continu de données (selon la façon dont l’utilisateur fournit l’implémentation pour celle-ci) à l’aide d’un paramètre table. L’exemple suivant montre comment implémenter l’interface ISQLServerDataRecord et transmettre sous la forme d’un paramètre table. Par souci de simplicité, l’exemple suivant passe une seule ligne avec des valeurs codées en dur pour le paramètre table. Dans l’idéal, l’utilisateur serait implémentent cette interface pour les lignes de flux de données à partir de n’importe quelle source, par exemple des fichiers texte.  

```java
class MyRecords implements ISQLServerDataRecord  
{  
    int currentRow = 0;  
    Object[] row = new Object[2];  
  
    MyRecords(){  
        // Constructor. This implementation has just one row.
        row[0] = new Integer(1);  
        row[1] = "categoryName1";  
    }  
  
    public int getColumnCount(){  
        // Return the total number of columns, for this example it is 2.  
        return 2;  
    }  
  
    public SQLServerMetaData getColumnMetaData(int columnIndex) {  
        // Return the column metadata.  
        if (1 == columnIndex)  
            return new SQLServerMetaData("CategoryID", java.sql.Types.INTEGER);  
        else  
            return new SQLServerMetaData("CategoryName", java.sql.Types.NVARCHAR);  
    }  
  
    public Object[] getRowData(){  
        // Return the columns in the current row as an array of objects. This implementation has just one row.  
        return row;
    }  
  
    public boolean next(){  
        // Move to the next row. This implementation has just one row, after processing the first row, return false.  
        currentRow++;  
        if (1 == currentRow)  
            return true;  
        else  
            return false;  
    }
}

// Following code demonstrates how to pass MyRecords object as a table-valued parameter.  
MyRecords sourceRecords = new MyRecords();  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceRecords);  
pStmt.execute();  
```

> [!NOTE]  
> Consultez la Section **API de paramètre table pour le pilote JDBC** ci-dessous pour obtenir la liste complète des API disponibles pour définir le paramètre table.

## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>Paramètre table API pour le pilote JDBC

### <a name="sqlservermetadata"></a>SQLServerMetaData

Cette classe représente des métadonnées pour une colonne. Il est utilisé dans l’interface ISQLServerDataRecord pour passer les métadonnées de colonne pour le paramètre table. Les méthodes dans cette classe sont :  

| Créer une vue d’abonnement                                                                                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData (columnName de chaîne, int sqlType, précision de type int, int mise à l’échelle, useServerDefault booléenne, isUniqueKey booléenne, SQLServerSortOrder sortOrder, int sortOrdinal) | Initialise une nouvelle instance de SQLServerMetaData avec le nom de colonne spécifié, le type sql, la précision, la mise à l’échelle et serveur par défaut. Cette forme du constructeur prend en charge les paramètres table en vous permettant de spécifier si la colonne est unique dans le paramètre table, l’ordre de tri pour la colonne et l’ordinal de la colonne de tri. <br/><br/>useServerDefault - Spécifie si la colonne doit utiliser la valeur par défaut du serveur ; Valeur par défaut est false.<br>isUniqueKey - indique si la colonne dans le paramètre table est unique ; Valeur par défaut est false.<br>sortOrder - indique l’ordre de tri pour une colonne ; Valeur par défaut est SQLServerSortOrder.Unspecified.<br>sortOrdinal - Spécifie l’ordinal de la colonne de tri. sortOrdinal commence à 0 ; Valeur par défaut est -1. |
| public SQLServerMetaData( String columnName, int sqlType)                                                                                                                        | Initialise une nouvelle instance de SQLServerMetaData en utilisant le nom de colonne et le type sql.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| public SQLServerMetaData( String columnName, int sqlType, int length)                                                                                                                        | Initialise une nouvelle instance de SQLServerMetaData à l’aide du nom de colonne, le type sql et la longueur (pour les données de chaîne). La longueur est utilisée pour différencier les chaînes de grande taille à partir de chaînes avec une longueur inférieure à 4 000 caractères. Introduite dans la version 7.2 du pilote JDBC.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public SQLServerMetaData( String columnName, int sqlType, int precision, int scale)                                                                                              | Initialise une nouvelle instance de SQLServerMetaData à l’aide du nom de colonne, le type sql, la précision et la mise à l’échelle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Public SQLServerMetaData(SQLServerMetaData sqlServerMetaData)                                                                                                                    | Initialise une nouvelle instance de SQLServerMetaData à partir d’un autre objet SQLServerMetaData.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| public getColumName() de chaîne                                                                                                                                                     | Récupère le nom de colonne.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| public int getSqlType()                                                                                                                                                          | Récupère le Type de code java sql.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| int publique getPrecision()                                                                                                                                                        | Récupère la précision du type passé à la colonne.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| int publique getScale()                                                                                                                                                            | Récupère la mise à l’échelle du type passé à la colonne.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public SQLServerSortOrder getSortOrder()                                                                                                                                         | Récupère l’ordre de tri.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| int publique getSortOrdinal()                                                                                                                                                      | Récupère l’ordinal de tri.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public isUniqueKey() booléenne                                                                                                                                                     | Retourne si la colonne est unique.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public useServerDefault() booléenne                                                                                                                                                | Retourne si la colonne utilise la valeur par défaut du serveur.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  
### <a name="sqlserversortorder"></a>SQLServerSortOrder

Une énumération qui définit l’ordre de tri. Les valeurs possibles sont croissant, décroissant et non spécifié.
  
### <a name="sqlserverdatatable"></a>SQLServerDataTable

Cette classe représente une table de données en mémoire à utiliser avec les paramètres table. Les méthodes dans cette classe sont :  

| Créer une vue d’abonnement                                                          | Description                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| Public SQLServerDataTable()                                   | Initialise une nouvelle instance de SQLServerDataTable.    |
| Itérateur public < entrée\<entière, Object [] >> getIterator()      | Récupère un itérateur sur les lignes de la table de données. |
| public addColumnMetadata void (columnName de chaîne, int sqlType) | Ajoute des métadonnées pour la colonne spécifiée.              |
| public void addColumnMetadata(SQLServerDataColumn column)     | Ajoute des métadonnées pour la colonne spécifiée.              |
| addRow void publique (valeurs d’objet...)                          | Ajoute une ligne de données à la table de données.              |
| public Map\<Integer, SQLServerDataColumn> getColumnMetadata() | Récupère les métadonnées de colonne de cette table de données.       |
| clear() void publique                                           | Efface la table de données.                              |

### <a name="sqlserverdatacolumn"></a>SQLServerDataColumn

Cette classe représente une colonne de la table de données en mémoire représentée par SQLServerDataTable. Les méthodes dans cette classe sont :  

| Créer une vue d’abonnement                                                       | Description                                                                      |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------- |
| public SQLServerDataColumn(String columnName, int sqlType) | Initialise une nouvelle instance de SQLServerDataColumn avec le type et le nom de colonne. |
| public getColumnName() de chaîne                              | Récupère le nom de colonne.                                                       |
| int publique getColumnType()                                 | Récupère le type de colonne.                                                       |

### <a name="isqlserverdatarecord"></a>ISQLServerDataRecord

Cette classe représente une interface que les utilisateurs peuvent implémenter pour diffuser des données à un paramètre table. Les méthodes dans cette interface sont :  
  
| Créer une vue d’abonnement                                                    | Description                                                                                             |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData getColumnMetaData(int column); | Récupère les métadonnées de colonne de l’index de colonne donnée.                                               |
| public int getColumnCount();                            | Récupère le nombre total de colonnes.                                                                  |
| public Object[] getRowData();                           | Récupère les données de la ligne active sous forme de tableau d’objets.                                          |
| public boolean next();                                  | Se déplace vers la ligne suivante. Retourne la valeur True si le déplacement a réussi et qu’une ligne suivante, false sinon. |

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

Les méthodes suivantes ont été ajoutées à cette classe pour prendre en charge le passage de paramètres table.  

| Créer une vue d’abonnement                                                                                                    | Description                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| setStructured finale public void (int parameterIndex, chaîne tvpName, SQLServerDataTable tvpDataTable)    | Remplit un paramètre table avec une table de données. parameterIndex est l’index de paramètre, tvpName est le nom du paramètre de table et tvpDataTable est l’objet de table de données source.                                                                                                          |
| setStructured finale public void (int parameterIndex, chaîne tvpName, tvpResultSet du jeu de résultats)             | Remplit un paramètre table avec un jeu de résultats récupéré à partir d’une autre table. parameterIndex est l’index de paramètre, tvpName est le nom du paramètre de table et tvpResultSet est l’objet source de l’ensemble de résultats.                                                                               |
| setStructured finale public void (int parameterIndex, chaîne tvpName, ISQLServerDataRecord tvpDataRecord) | Remplit un paramètre table avec un objet ISQLServerDataRecord. ISQLServerDataRecord est utilisé pour la diffusion des données et l’utilisateur décide comment l’utiliser. parameterIndex est l’index de paramètre, tvpName est le nom du paramètre de table et tvpDataRecord est un objet ISQLServerDataRecord. |
  
### <a name="sqlservercallablestatement"></a>SQLServerCallableStatement

Les méthodes suivantes ont été ajoutées à cette classe pour prendre en charge le passage de paramètres table.  
  
| Créer une vue d’abonnement                                                                                                        | Description                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| setStructured finale public void (paratemeterName de chaîne, chaîne tvpName, SQLServerDataTable tvpDataTable)    | Remplit un paramètre table est passé à une procédure stockée avec une table de données. paratemeterName est le nom du paramètre, tvpName est le nom du type TVP et tvpDataTable est l’objet de table de données.                                                                                                                 |
| setStructured finale public void (paratemeterName de chaîne, chaîne tvpName, tvpResultSet du jeu de résultats)             | Remplit un paramètre table est passé à une procédure stockée avec un jeu de résultats récupéré à partir d’une autre table. paratemeterName est le nom du paramètre, tvpName est le nom du type TVP et tvpResultSet est l’objet source de l’ensemble de résultats.                                                                              |
| setStructured finale public void (paratemeterName de chaîne, chaîne tvpName, ISQLServerDataRecord tvpDataRecord) | Remplit un paramètre table est passé à une procédure stockée avec un objet ISQLServerDataRecord. ISQLServerDataRecord est utilisé pour la diffusion des données et l’utilisateur décide comment l’utiliser. paratemeterName est le nom du paramètre, tvpName est le nom du type TVP et tvpDataRecord est un objet ISQLServerDataRecord. |

## <a name="see-also"></a> Voir aussi

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
