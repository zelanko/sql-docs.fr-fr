---
title: Utilisation des paramètres table
description: Les paramètres table offrent un moyen efficace d’envoyer plusieurs lignes de données d’un client à SQL Server dans une commande paramétrée unique.
ms.custom: ''
ms.date: 11/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eac620d522408ff9fb4de5550d92cfcbd0f3ec4a
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727470"
---
# <a name="using-table-valued-parameters"></a>Utilisation des paramètres table

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données. Vous pouvez utiliser des paramètres table pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique. Les lignes de données entrantes sont stockées dans une variable de table que vous pouvez ensuite utiliser à l’aide de Transact-SQL.  
  
Les valeurs de colonne dans les paramètres table sont accessibles à l’aide d’instructions Transact-SQL SELECT standard. Les paramètres table sont fortement typés et leur structure est validée automatiquement. La taille des paramètres table est limitée uniquement par la mémoire du serveur.  
  
> [!NOTE]  
> La prise en charge des paramètres table est disponible à compter de la version 6.0 de Microsoft JDBC Driver pour SQL Server.
>
> Il n’est pas possible de retourner des données dans un paramètre table, car il prennent uniquement des valeurs d’entrée ; le mot clé OUTPUT n’est pas pris en charge.  
  
 Pour plus d’informations sur les paramètres table, consultez les ressources suivantes.  
  
| Ressource                                                                                                             | Description                                                                         |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [Paramètres table (moteur de base de données)](/previous-versions/sql/sql-server-2008/bb510489(v=sql.100)) dans la Documentation en ligne de SQL Server | Explique comment créer et utiliser des paramètres table.                             |
| [Types de tables définis par l’utilisateur](/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)) dans la Documentation en ligne de SQL Server                  | Décrit les types de tables définis par l’utilisateur qui permettent de déclarer des paramètres table. |
| Section [Moteur de base de données Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=120507) de CodePlex        | Contient des exemples qui montrent comment utiliser les fonctions et fonctionnalités de SQL Server.  |
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Transmettre plusieurs lignes dans les versions précédentes de SQL Server  

Avant l’introduction des paramètres table dans SQL Server 2008, les options permettant de passer plusieurs lignes de données à une procédure stockée ou à une commande SQL paramétrée étaient limitées. Un développeur peut choisir parmi les options suivantes pour transmettre plusieurs lignes au serveur :  
  
- Utilisez une série de paramètres individuels pour représenter les valeurs dans plusieurs colonnes et lignes de données. La quantité de données transmissibles selon cette méthode est limitée par le nombre de paramètres autorisés. Les procédures SQL Server peuvent contenir jusqu’à 2 100 paramètres. Une logique côté serveur est requise pour assembler ces différentes valeurs dans une variable de table ou une table temporaire à des fins de traitement.  
  
- Regroupez plusieurs valeurs de données dans des chaînes délimitées ou des documents XML, puis transmettez ces valeurs de texte à une procédure ou une instruction. Il faut pour cela que la procédure ou l’instruction inclue la logique nécessaire pour valider les structures de données et dissocier les valeurs.  
  
- Créez une série d’instructions SQL distinctes pour les modifications de données qui affectent plusieurs lignes. Ces modifications peuvent être envoyées individuellement au serveur ou regroupées par lots. Toutefois, même lorsqu’elles sont soumises dans des lots contenant plusieurs instructions, chacune des instructions est exécutée séparément sur le serveur.  
  
- Utilisez le programme utilitaire bcp ou l’objet [SQLServerBulkCopy](using-bulk-copy-with-the-jdbc-driver.md) pour charger de nombreuses lignes de données dans une table. Bien que cette technique soit très efficace, elle ne gère pas le traitement côté serveur à moins que les données ne soient chargées dans une table temporaire ou une variable table.
  
## <a name="creating-table-valued-parameter-types"></a>Créer des types de paramètres table  

Les paramètres table sont basés sur des structures de table fortement typées et définies à l’aide d’instructions Transact-SQL `CREATE TYPE`. Vous devez créer un type de table et définir la structure dans SQL Server avant de pouvoir utiliser les paramètres table dans vos applications clientes. Pour plus d’informations sur la création des types de table, consultez [Types de table définis par l’utilisateur](/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)) dans la Documentation en ligne de SQL Server.  

```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```

Après avoir créé un type table, vous pouvez déclarer des paramètres table basés sur ce type. Le fragment Transact-SQL suivant montre comment déclarer un paramètre table dans une définition de procédure stockée. Il est à noter que le mot clé `READONLY` est nécessaire pour déclarer un paramètre table.  

```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```

## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modifier des données avec des paramètres table (Transact-SQL)  

Les paramètres table peuvent être utilisés dans des modifications de données par jeux qui affectent plusieurs lignes avec une seule instruction. Par exemple, vous pouvez sélectionner toutes les lignes d’un paramètre table et les insérer dans une table de base de données, ou créer une instruction de mise à jour en joignant un paramètre table à la table à mettre à jour.  
  
L’instruction Transact-SQL UPDATE suivante montre comment utiliser un paramètre table en le joignant à la table Categories. Si vous utilisez un paramètre table avec un JOIN dans une clause FROM, vous devez également créer un alias pour celui-ci (ici, le paramètre table a pour alias « ec ») :  

```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```

Cet exemple Transact-SQL montre comment sélectionner des lignes d’un paramètre table pour effectuer une insertion (INSERT) dans une opération basée sur un jeu unique.

```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```

## <a name="limitations-of-table-valued-parameters"></a>Limitations des paramètres table

Les paramètres table présentent plusieurs limitations :  
  
- Il n’est pas possible de transmettre des paramètres table à des fonctions définies par l’utilisateur.  
  
- Les paramètres table ne peuvent être indexés que pour prendre en charge les contraintes UNIQUE et PRIMARY KEY. SQL Server ne tient pas à jour de statistiques sur les paramètres table.  
  
- Les paramètres table sont en lecture seule dans le code Transact-SQL. Il n’est pas possible de mettre à jour les valeurs de colonne dans les lignes d’un paramètre table, ni d’insérer ou de supprimer des lignes. Pour modifier les données transmises à une procédure stockée ou à une instruction paramétrable dans un paramètre table, il faut les insérer dans une table temporaire ou une variable de table.  
  
- Il n’est pas possible d’utiliser des instructions ALTER TABLE pour modifier la conception de paramètres table.

- Il est possible de transmettre en continu des objets volumineux dans un paramètre table.  
  
## <a name="configuring-a-table-valued-parameter"></a>Configuration d'un paramètre table

À compter de la version 6.0 de Microsoft JDBC Driver pour SQL Server, les paramètres table sont pris en charge avec une instruction paramétrable ou une procédure stockée paramétrable. Ils peuvent être remplis à partir d’une SQLServerDataTable, d’un ResultSet ou d’une implémentation fournie par l’utilisateur de l’interface ISQLServerDataRecord. Lorsque vous définissez un paramètre table pour une requête préparée, vous devez spécifier un nom de type correspondant au nom d’un type compatible déjà créé sur le serveur.  
  
Les deux fragments de code suivants montrent comment configurer un paramètre table avec une SQLServerPreparedStatement et une SQLServerCallableStatement pour insérer des données. Ici, sourceTVPObject peut être une SQLServerDataTable, un ResultSet ou un objet ISQLServerDataRecord. Les exemples supposent que la connexion est un objet Connection actif.  

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
> Pour connaître la liste complète des API disponibles pour définir le paramètre table, consultez la section **API des paramètres table pour le pilote JDBC** ci-dessous.  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>Transmettre un paramètre table comme objet SQLServerDataTable  

À compter de la version 6.0 de Microsoft JDBC Driver pour SQL Server, la classe SQLServerDataTable représente une table en mémoire de données relationnelles. Cet exemple montre comment construire un paramètre table à partir de données en mémoire à l’aide de l’objet SQLServerDataTable. Le code crée d’abord un objet SQLServerDataTable, définit son schéma et remplit la table avec des données. Le code configure ensuite une SQLServerPreparedStatement qui transmet cette table de données sous forme de paramètre table à SQL Server.  

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
> Pour connaître la liste complète des API disponibles pour définir le paramètre table, consultez la section **API des paramètres table pour le pilote JDBC** ci-dessous.  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>Transmettre un paramètre table comme objet ResultSet  

Cet exemple montre comment transmettre en continu des lignes de données d’un ResultSet à un paramètre table. Le code récupère d’abord des données d’une table source dans un objet SQLServerDataTable, définit son schéma et remplit la table avec des données. Le code configure ensuite une SQLServerPreparedStatement qui transmet cette table de données sous forme de paramètre table à SQL Server.  

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
> Pour connaître la liste complète des API disponibles pour définir le paramètre table, consultez la section **API des paramètres table pour le pilote JDBC** ci-dessous.  

## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>Transmettre un paramètre table comme objet ISQLServerDataRecord  

À compter de la version 6.0 de Microsoft JDBC Driver pour SQL Server, une nouvelle interface ISQLServerDataRecord est disponible pour la transmission de données en continu (selon l’implémentation fournie par l’utilisateur) avec un paramètre table. L’exemple suivant montre comment implémenter l’interface ISQLServerDataRecord et la transmettre sous forme de paramètre table. Par souci de simplicité, l’exemple suivant transmet une seule ligne comportant des valeurs codées en dur au paramètre table. Dans l’idéal, l’utilisateur implémenterait cette interface pour transmettre en continu des lignes à partir de n’importe quelle source, par exemple à partir de fichiers texte.  

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
> Pour connaître la liste complète des API disponibles pour définir le paramètre table, consultez la section **API des paramètres table pour le pilote JDBC** ci-dessous.

## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>API des paramètres table pour le pilote JDBC

### <a name="sqlservermetadata"></a>SQLServerMetaData

Cette classe représente les métadonnées d’une colonne. Elle est utilisée dans l’interface ISQLServerDataRecord pour transmettre des métadonnées de colonne au paramètre table. Elle comporte les méthodes suivantes :  

| Nom                                                                                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData(String columnName, int sqlType, int precision, int scale, boolean useServerDefault, boolean isUniqueKey, SQLServerSortOrder sortOrder, int sortOrdinal) | Initialise une nouvelle instance de SQLServerMetaData avec le nom de colonne, le type SQL, la précision, l’échelle et la valeur par défaut du serveur spécifiés. Cette forme du constructeur prend en charge les paramètres table en offrant la possibilité de spécifier si la colonne est unique dans le paramètre table, l’ordre de tri de la colonne et l’ordinal de la colonne de tri. <br/><br/>useServerDefault : spécifie si cette colonne doit utiliser la valeur de serveur par défaut (valeur par défaut : false).<br>isUniqueKey : indique si la colonne du paramètre table est unique (valeur par défaut : false).<br>sortOrder : indique l’ordre de tri d’une colonne (valeur par défaut : SQLServerSortOrder.Unspecified).<br>sortOrdinal : spécifie l’ordinal de la colonne de tri, en commençant à partir de 0 (valeur par défaut : -1). |
| public SQLServerMetaData( String columnName, int sqlType)                                                                                                                        | Initialise une nouvelle instance de SQLServerMetaData avec le nom de colonne et le type SQL.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| public SQLServerMetaData( String columnName, int sqlType, int length)                                                                                                                        | Initialise une nouvelle instance de SQLServerMetaData avec le nom de colonne, le type SQL et la longueur (pour les données String). La longueur est utilisée pour différencier les chaînes volumineuses des chaînes de moins de 4 000 caractères. Introduite dans la version 7.2 du pilote JDBC.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public SQLServerMetaData( String columnName, int sqlType, int precision, int scale)                                                                                              | Initialise une nouvelle instance de SQLServerMetaData avec le nom de colonne, le type SQL, la précision et l’échelle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Public SQLServerMetaData(SQLServerMetaData sqlServerMetaData)                                                                                                                    | Initialise une nouvelle instance de SQLServerMetaData à partir d’un autre objet SQLServerMetaData.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| public String getColumName()                                                                                                                                                     | Récupère le nom de la colonne.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| public int getSqlType()                                                                                                                                                          | Récupère le type SQL Java.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| public int getPrecision()                                                                                                                                                        | Récupère la précision du type transmis à la colonne.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| public int getScale()                                                                                                                                                            | Récupère l’échelle du type transmis à la colonne.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public SQLServerSortOrder getSortOrder()                                                                                                                                         | Récupère l’ordre de tri.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| public int getSortOrdinal()                                                                                                                                                      | Récupère l’ordinal de tri.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public boolean isUniqueKey()                                                                                                                                                     | Indique si la colonne est unique.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public boolean useServerDefault()                                                                                                                                                | Indique si la colonne utilise la valeur par défaut du serveur.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  
### <a name="sqlserversortorder"></a>SQLServerSortOrder

Enum définissant l’ordre de tri. Les valeurs possibles sont les suivantes : Ascending, Descending et Unspecified.
  
### <a name="sqlserverdatatable"></a>SQLServerDataTable

Cette classe représente une table de données en mémoire à utiliser avec des paramètres table. Elle comporte les méthodes suivantes :  

| Nom                                                          | Description                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| Public SQLServerDataTable()                                   | Initialise une nouvelle instance de SQLServerDataTable.    |
| public Iterator<Entry\<Integer, Object[]>> getIterator()      | Récupère un itérateur sur les lignes de la table de données. |
| public void addColumnMetadata(String columnName, int sqlType) | Ajoute les métadonnées de la colonne spécifiée.              |
| public void addColumnMetadata(SQLServerDataColumn column)     | Ajoute les métadonnées de la colonne spécifiée.              |
| public void addRow(Object… valeurs)                          | Ajoute une ligne de données à la table de données.              |
| public Map\<Integer, SQLServerDataColumn> getColumnMetadata() | Récupère les métadonnées de colonne de cette table de données.       |
| public void clear()                                           | Efface cette table de données.                              |

### <a name="sqlserverdatacolumn"></a>SQLServerDataColumn

Cette classe représente une colonne de la table de données en mémoire représentée par SQLServerDataTable. Elle comporte les méthodes suivantes :  

| Nom                                                       | Description                                                                      |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------- |
| public SQLServerDataColumn(String columnName, int sqlType) | Initialise une nouvelle instance de SQLServerDataColumn avec le nom de colonne et le type. |
| public String getColumnName()                              | Récupère le nom de la colonne.                                                       |
| public int getColumnType()                                 | Récupère le type de la colonne.                                                       |

### <a name="isqlserverdatarecord"></a>ISQLServerDataRecord

Cette classe représente une interface que les utilisateurs peuvent implémenter pour transmettre en continu des données à un paramètre table. Les méthodes de cette interface sont les suivantes :  
  
| Nom                                                    | Description                                                                                             |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData getColumnMetaData(int column); | Récupère les métadonnées de colonne de l’index de colonne donné.                                               |
| public int getColumnCount();                            | Récupère le nombre total de colonnes.                                                                  |
| public Object[] getRowData();                           | Récupère les données de la ligne active sous forme de tableau d’objets.                                          |
| public boolean next();                                  | Passe à la ligne suivante. Retourne true si le déplacement a réussi et qu’il y a une ligne suivante ; false sinon. |

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

Les méthodes suivantes ont été ajoutées à cette classe pour permettre de transmettre des paramètres table.  

| Nom                                                                                                    | Description                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public final void setStructured(int parameterIndex, String tvpName, SQLServerDataTable tvpDataTable)    | Remplit un paramètre table avec une table de données. parameterIndex est l’index du paramètre, tvpName le nom du paramètre table et tvpDataTable l’objet table de données source.                                                                                                          |
| public final void setStructured(int parameterIndex, String tvpName, ResultSet tvpResultSet)             | Remplit un paramètre table avec un ResultSet récupéré à partir d’une autre table. parameterIndex est l’index du paramètre, tvpName le nom du paramètre table et tvpResultSet l’objet jeu de résultats source.                                                                               |
| public final void setStructured(int parameterIndex, String tvpName, ISQLServerDataRecord tvpDataRecord) | Remplit un paramètre table avec un objet ISQLServerDataRecord. ISQLServerDataRecord est utilisé pour transmettre des données en continu ; c’est l’utilisateur qui décide de leur utilisation. parameterIndex est l’index du paramètre, tvpName le nom du paramètre table et tvpDataRecord un objet ISQLServerDataRecord. |
  
### <a name="sqlservercallablestatement"></a>SQLServerCallableStatement

Les méthodes suivantes ont été ajoutées à cette classe pour permettre de transmettre des paramètres table.  
  
| Nom                                                                                                        | Description                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public final void setStructured(String paratemeterName, String tvpName, SQLServerDataTable tvpDataTable)    | Remplit un paramètre table transmis à une procédure stockée avec une table de données. paratemeterName est le nom du paramètre, tvpName le nom du type de paramètre table et tvpDataTable l’objet table de données.                                                                                                                 |
| public final void setStructured(String paratemeterName, String tvpName, ResultSet tvpResultSet)             | Remplit un paramètre table transmis à une procédure stockée avec un ResultSet récupéré à partir d’une autre table. paratemeterName est le nom du paramètre, tvpName le nom du type de paramètre table et tvpResultSet l’objet jeu de résultats source.                                                                              |
| public final void setStructured(String paratemeterName, String tvpName, ISQLServerDataRecord tvpDataRecord) | Remplit un paramètre table transmis à une procédure stockée avec un objet ISQLServerDataRecord. ISQLServerDataRecord est utilisé pour transmettre des données en continu ; c’est l’utilisateur qui décide de leur utilisation. paratemeterName est le nom du paramètre, tvpName le nom du type de paramètre table et tvpDataRecord un objet ISQLServerDataRecord. |

## <a name="see-also"></a>Voir aussi

[Présentation du pilote JDBC](overview-of-the-jdbc-driver.md)