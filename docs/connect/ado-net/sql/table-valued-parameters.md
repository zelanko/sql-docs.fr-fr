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
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: f51e5326d29d7edd6a518c02f7042cc9ed104b4f
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78895958"
---
# <a name="table-valued-parameters"></a>Paramètres table

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données. Vous pouvez utiliser des paramètres table pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique. Les lignes de données entrantes sont stockées dans une variable de table que vous pouvez ensuite utiliser à l’aide de Transact-SQL.  
  
Les valeurs de colonne dans les paramètres table sont accessibles à l’aide d’instructions Transact-SQL SELECT standard. Les paramètres table sont fortement typés et leur structure est validée automatiquement. La taille des paramètres table est limitée uniquement par la mémoire du serveur.  
  
> [!NOTE]
>  Vous ne pouvez pas renvoyer de données dans un paramètre table. car il prennent uniquement des valeurs d’entrée ; le mot clé OUTPUT n’est pas pris en charge.  
  
Pour plus d’informations sur les paramètres table, consultez les ressources suivantes.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Paramètres table (moteur de base de données)](https://go.microsoft.com/fwlink/?LinkId=98363) dans la Documentation en ligne de SQL Server|Décrit comment créer et utiliser des paramètres table.|  
|[Types de tables définis par l'utilisateur](https://go.microsoft.com/fwlink/?LinkId=98364) dans la Documentation en ligne de SQL Server|Décrit les types de tables définis par l’utilisateur qui permettent de déclarer des paramètres table.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Passage de plusieurs lignes dans les versions précédentes de SQL Server  
Avant l’introduction des paramètres table dans SQL Server 2008, les options permettant de passer plusieurs lignes de données à une procédure stockée ou à une commande SQL paramétrée étaient limitées. Un développeur peut choisir parmi les options suivantes pour transmettre plusieurs lignes au serveur :  
  
- Utilisez une série de paramètres individuels pour représenter les valeurs dans plusieurs colonnes et lignes de données. La quantité de données transmissibles selon cette méthode est limitée par le nombre de paramètres autorisés. Les procédures SQL Server peuvent contenir jusqu’à 2 100 paramètres. Une logique côté serveur est requise pour assembler ces différentes valeurs dans une variable de table ou une table temporaire à des fins de traitement.  
  
- Regroupez plusieurs valeurs de données dans des chaînes délimitées ou des documents XML, puis transmettez ces valeurs de texte à une procédure ou une instruction. Cela requiert que la procédure ou l’instruction inclue la logique nécessaire pour valider les structures de données et dissocier les valeurs.  
  
- Créez une série d’instructions SQL pour les modifications de données qui affectent plusieurs lignes, telles que celles créées en appelant la méthode `Update` d’un <xref:Microsoft.Data.SqlClient.SqlDataAdapter>. Les modifications peuvent être envoyées au serveur individuellement ou regroupées par lot. Toutefois, même lorsqu’elles sont soumises dans des lots contenant plusieurs instructions, chaque instruction est exécutée séparément sur le serveur.  
  
- Utilisez le programme utilitaire `bcp` ou l’objet <xref:Microsoft.Data.SqlClient.SqlBulkCopy> pour charger de nombreuses lignes de données dans une table. Bien que cette technique soit très efficace, elle ne prend pas en charge le traitement côté serveur à moins que les données ne soient chargées dans une table temporaire ou une variable table.  
  
## <a name="creating-table-valued-parameter-types"></a>Création de types de paramètre table  
Les paramètres table sont basés sur des structures de table fortement typées qui sont définies à l’aide d’instructions Transact-SQL CREATE TYPE. Vous devez créer un type de table et définir la structure dans SQL Server avant de pouvoir utiliser les paramètres table dans vos applications clientes. Pour plus d’informations sur la création des types de table, consultez [Types de table définis par l’utilisateur](https://go.microsoft.com/fwlink/?LinkID=98364) dans la Documentation en ligne de SQL Server.  
  
L’instruction suivante crée un type table nommé CategoryTableType qui se compose de colonnes CategoryID et CategoryName :  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
Après avoir créé un type table, vous pouvez déclarer des paramètres table basés sur ce type. Le fragment Transact-SQL suivant montre comment déclarer un paramètre table dans une définition de procédure stockée. Notez que le mot clé READONLY est requis pour déclarer un paramètre table.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modification de données à l’aide de paramètres table (Transact-SQL)  
Les paramètres table peuvent être utilisés dans des modifications de données basées sur des jeux qui affectent plusieurs lignes en exécutant une instruction unique. Par exemple, vous pouvez sélectionner toutes les lignes d’un paramètre table et les insérer dans une table de base de données, ou créer une instruction de mise à jour en joignant un paramètre table à la table à mettre à jour.  
  
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
  
- Vous ne pouvez pas passer de paramètres table aux [fonctions CLR définies par l’utilisateur](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md).  
  
- Les paramètres table peuvent uniquement être indexés pour prendre en charge les contraintes UNIQUE ou PRIMARY KEY. SQL Server ne tient pas à jour de statistiques sur les paramètres table.  
  
- Les paramètres table sont en lecture seule dans le code Transact-SQL. Il n’est pas possible de mettre à jour les valeurs de colonne dans les lignes d’un paramètre table, ni d’insérer ou de supprimer des lignes. Pour modifier les données transmises à une procédure stockée ou à une instruction paramétrable dans un paramètre table, il faut les insérer dans une table temporaire ou une variable de table.  
  
- Vous ne pouvez pas utiliser d’instructions ALTER TABLE pour modifier la conception de paramètres table.  
  
## <a name="configuring-a-sqlparameter-example"></a>Exemple de configuration de SqlParameter  
<xref:Microsoft.Data.SqlClient> prend en charge le remplissage des paramètres table à partir d’objets <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> ou <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.Data.SqlClient.Server.SqlDataRecord>. Vous devez spécifier un nom de type pour le paramètre table à l’aide de la propriété <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> d’un objet <xref:Microsoft.Data.SqlClient.SqlParameter>. Le `TypeName` doit correspondre au nom d’un type compatible précédemment créé sur le serveur. Le fragment de code suivant montre comment configurer <xref:Microsoft.Data.SqlClient.SqlParameter> pour insérer des données.  
 
Dans l’exemple ci-dessous, la variable `addedCategories` contient un <xref:System.Data.DataTable>. Pour voir comment la variable est remplie, consultez les exemples de la section suivante, [Passage d'un paramètre table à une procédure stockée](#passing).

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
Cet exemple montre comment passer des données de paramètre table à une procédure stockée. Le code extrait des lignes ajoutées dans une nouvelle <xref:System.Data.DataTable> à l’aide de la méthode <xref:System.Data.DataTable.GetChanges%2A>. Le code définit ensuite une <xref:Microsoft.Data.SqlClient.SqlCommand>, en définissant la propriété <xref:Microsoft.Data.SqlClient.SqlCommand.CommandType%2A> sur la valeur <xref:System.Data.CommandType.StoredProcedure>. <xref:Microsoft.Data.SqlClient.SqlParameter> est rempli à l’aide de la méthode <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> et le <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> est défini sur `Structured`. La <xref:Microsoft.Data.SqlClient.SqlCommand> est ensuite exécutée à l’aide de la méthode <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.  
  
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
 L’exemple suivant montre comment insérer des données dans la table dbo.Categories à l’aide d’une instruction INSERT avec une sous-requête SELECT qui a un paramètre table comme source de données. Lors du passage d’un paramètre table à une instruction SQL paramétrable, vous devez spécifier un nom de type pour le paramètre table à l’aide de la nouvelle propriété <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> d’un <xref:Microsoft.Data.SqlClient.SqlParameter>. Ce `TypeName` doit correspondre au nom d’un type compatible précédemment créé sur le serveur. Le code de cet exemple utilise la propriété `TypeName` pour référencer la structure de type définie dans dbo.CategoryTableType.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>Diffusion en continu de lignes avec un DataReader  
Vous pouvez également utiliser n’importe quel objet dérivé de l’objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table. Le fragment de code suivant montre comment récupérer des données d’une base de données Oracle à l’aide d’une <xref:System.Data.OracleClient.OracleCommand> et d’un <xref:System.Data.OracleClient.OracleDataReader>. Le code configure ensuite une <xref:Microsoft.Data.SqlClient.SqlCommand> pour appeler une procédure stockée avec un seul paramètre d’entrée. La propriété <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> du <xref:Microsoft.Data.SqlClient.SqlParameter> a la valeur `Structured`. <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> transmet le jeu de résultats `OracleDataReader` à la procédure stockée en tant que paramètre table.  
  
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
