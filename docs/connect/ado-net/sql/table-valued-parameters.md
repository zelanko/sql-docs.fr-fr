---
title: Paramètres table
description: Décrit comment utiliser les paramètres table qui ont été introduits dans SQL Server 2008.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: cb8eec87d0d36eb7deb8663e40407c0067967def
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451922"
---
# <a name="table-valued-parameters"></a>Paramètres table

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données. Vous pouvez utiliser des paramètres table pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique. Les lignes de données entrantes sont stockées dans une variable de table que vous pouvez ensuite utiliser à l’aide de Transact-SQL.  
  
Les valeurs de colonne dans les paramètres table sont accessibles à l’aide d’instructions Transact-SQL SELECT standard. Les paramètres table sont fortement typés et leur structure est validée automatiquement. La taille des paramètres table est limitée uniquement par la mémoire du serveur.  
  
> [!NOTE]
>  Vous ne pouvez pas retourner de données dans un paramètre table. Les paramètres table sont des valeurs d’entrée uniquement ; le mot clé OUTPUT n’est pas pris en charge.  
  
Pour plus d’informations sur les paramètres table, consultez les ressources suivantes.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Paramètres table (moteur de base de données)](https://go.microsoft.com/fwlink/?LinkId=98363) dans la Documentation en ligne de SQL Server|Décrit comment créer et utiliser des paramètres table.|  
|[Types de tables définis par l’utilisateur](https://go.microsoft.com/fwlink/?LinkId=98364) dans documentation en ligne de SQL Server|Décrit les types de tables définis par l’utilisateur qui permettent de déclarer des paramètres table.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Passage de plusieurs lignes dans les versions précédentes de SQL Server  
Avant l’introduction des paramètres table dans SQL Server 2008, les options permettant de passer plusieurs lignes de données à une procédure stockée ou à une commande SQL paramétrée étaient limitées. Un développeur peut choisir parmi les options suivantes pour transmettre plusieurs lignes au serveur :  
  
- Utilisez une série de paramètres individuels pour représenter les valeurs dans plusieurs colonnes et lignes de données. La quantité de données qui peuvent être passées à l’aide de cette méthode est limitée par le nombre de paramètres autorisés. Les procédures SQL Server peuvent contenir jusqu’à 2 100 paramètres. La logique côté serveur est requise pour assembler ces valeurs individuelles dans une variable de table ou une table temporaire à des fins de traitement.  
  
- Regroupez plusieurs valeurs de données dans des chaînes délimitées ou des documents XML, puis transmettez ces valeurs de texte à une procédure ou une instruction. Cela requiert que la procédure ou l’instruction inclue la logique nécessaire pour valider les structures de données et dissocier les valeurs.  
  
- Créez une série d’instructions SQL pour les modifications de données qui affectent plusieurs lignes, telles que celles créées en appelant la méthode `Update` d’un <xref:Microsoft.Data.SqlClient.SqlDataAdapter>. Les modifications peuvent être envoyées au serveur individuellement ou regroupées par lot. Toutefois, même lorsqu’elles sont soumises dans des lots contenant plusieurs instructions, chaque instruction est exécutée séparément sur le serveur.  
  
- Utilisez le programme utilitaire `bcp` ou l’objet <xref:Microsoft.Data.SqlClient.SqlBulkCopy> pour charger de nombreuses lignes de données dans une table. Bien que cette technique soit très efficace, elle ne prend pas en charge le traitement côté serveur à moins que les données ne soient chargées dans une table temporaire ou une variable de table.  
  
## <a name="creating-table-valued-parameter-types"></a>• type de paramètre table  
Les paramètres table sont basés sur des structures de table fortement typées qui sont définies à l’aide d’instructions Transact-SQL CREATE TYPE. Vous devez créer un type de table et définir la structure dans SQL Server avant de pouvoir utiliser les paramètres table dans vos applications clientes. Pour plus d’informations sur la création des types de table, consultez [Types de table définis par l’utilisateur](https://go.microsoft.com/fwlink/?LinkID=98364) dans la Documentation en ligne de SQL Server.  
  
L’instruction suivante crée un type de table nommé CategoryTableType qui se compose de colonnes CategoryID et CategoryName :  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
Après avoir créé un type de table, vous pouvez déclarer des paramètres table basés sur ce type. Le fragment Transact-SQL suivant montre comment déclarer un paramètre table dans une définition de procédure stockée. Notez que le mot clé READONLY est requis pour déclarer un paramètre table.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modification de données à l’aide de paramètres table (Transact-SQL)  
Les paramètres table peuvent être utilisés dans les modifications de données basées sur des ensembles qui affectent plusieurs lignes en exécutant une instruction unique. Par exemple, vous pouvez sélectionner toutes les lignes d’un paramètre table et les insérer dans une table de base de données, ou vous pouvez créer une instruction Update en joignant un paramètre table à la table que vous souhaitez mettre à jour.  
  
L’instruction Transact-SQL UPDATE suivante montre comment utiliser un paramètre table en le joignant à la table Categories. Lorsque vous utilisez un paramètre table avec une jointure dans une clause FROM, vous devez également créer un alias pour celui-ci, comme illustré ici, où le paramètre table est un alias avec la valeur « EC » :  
  
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
  
- Vous ne pouvez pas passer de paramètres table aux [fonctions CLR définies par l’utilisateur](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md).  
  
- Les paramètres table peuvent uniquement être indexés pour prendre en charge les contraintes de clé primaire ou UNIQUE. SQL Server ne tient pas à jour de statistiques sur les paramètres table.  
  
- Les paramètres table sont en lecture seule dans le code Transact-SQL. Vous ne pouvez pas mettre à jour les valeurs de colonne dans les lignes d’un paramètre table et vous ne pouvez pas insérer ou supprimer des lignes. Pour modifier les données qui sont passées à une procédure stockée ou à une instruction paramétrée dans un paramètre table, vous devez insérer les données dans une table temporaire ou dans une variable de table.  
  
- Vous ne pouvez pas utiliser d’instructions ALTER TABLE pour modifier la conception de paramètres table.  
  
## <a name="configuring-a-sqlparameter-example"></a>Configuration d’un exemple SqlParameter  
<xref:Microsoft.Data.SqlClient> prend en charge le remplissage des paramètres table à partir d’objets <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> ou <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.Data.SqlClient.Server.SqlDataRecord>. Vous devez spécifier un nom de type pour le paramètre table à l’aide de la propriété <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> d’un objet <xref:Microsoft.Data.SqlClient.SqlParameter>. Le `TypeName` doit correspondre au nom d’un type compatible précédemment créé sur le serveur. Le fragment de code suivant montre comment configurer <xref:Microsoft.Data.SqlClient.SqlParameter> pour insérer des données.  
 
Dans l’exemple ci-dessous, la variable `addedCategories` contient un <xref:System.Data.DataTable>. Pour voir comment la variable est remplie, consultez les exemples de la section suivante, [transmission d’un paramètre table à une procédure stockée](#passing).

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```   
  
Vous pouvez également utiliser n’importe quel objet dérivé de l’objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table, tel qu’indiqué dans ce fragment :  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
## <a name="passing"></a> Passage d’un paramètre table à une procédure stockée  
Cet exemple montre comment passer des données de paramètre table à une procédure stockée. Le code extrait des lignes ajoutées dans une nouvelle <xref:System.Data.DataTable> à l’aide de la méthode <xref:System.Data.DataTable.GetChanges%2A>. Le code définit ensuite une <xref:Microsoft.Data.SqlClient.SqlCommand>, en affectant à la propriété <xref:Microsoft.Data.SqlClient.SqlCommand.CommandType%2A> la valeur <xref:System.Data.CommandType.StoredProcedure>. La <xref:Microsoft.Data.SqlClient.SqlParameter> est remplie à l’aide de la méthode <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> et la <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> est définie sur `Structured`. Le <xref:Microsoft.Data.SqlClient.SqlCommand> est ensuite exécuté à l’aide de la méthode <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Passage d’un paramètre table à une instruction SQL paramétrable  
 L’exemple suivant montre comment insérer des données dans le dbo. Table Categories à l’aide d’une instruction INSERT avec une sous-requête SELECT qui a un paramètre table comme source de données. Lors du passage d’un paramètre table à une instruction SQL paramétrable, vous devez spécifier un nom de type pour le paramètre table à l’aide de la nouvelle propriété <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> d’un <xref:Microsoft.Data.SqlClient.SqlParameter>. Ce `TypeName` doit correspondre au nom d’un type compatible précédemment créé sur le serveur. Le code de cet exemple utilise la propriété `TypeName` pour référencer la structure de type définie dans dbo. CategoryTableType.  
  
> [!NOTE]
>  Si vous fournissez une valeur pour une colonne d’identité dans un paramètre table, vous devez émettre l’instruction SET IDENTITY_INSERT pour la session.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
## <a name="streaming-rows-with-a-datareader"></a>Streaming de lignes avec un DataReader  
Vous pouvez également utiliser n’importe quel objet dérivé de l’objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table. Le fragment de code suivant montre comment récupérer des données d’une base de données Oracle à l’aide d’un <xref:System.Data.OracleClient.OracleCommand> et d’un <xref:System.Data.OracleClient.OracleDataReader>. Le code configure ensuite une <xref:Microsoft.Data.SqlClient.SqlCommand> pour appeler une procédure stockée avec un seul paramètre d’entrée. La propriété <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> du <xref:Microsoft.Data.SqlClient.SqlParameter> a la valeur `Structured`. L' <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> transmet le jeu de résultats `OracleDataReader` à la procédure stockée en tant que paramètre table.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [Opérations de données SQL Server dans ADO.NET](sql-server-data-operations.md)
