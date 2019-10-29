---
title: Modification de données à valeurs élevées (max) dans ADO.NET
description: Décrit comment utiliser les types de données de valeur élevée.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: fac55eb25f89ced173683d5ed5d4334c2fcde975
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452125"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Modification de données à valeurs élevées (max) dans ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Les types de données LOB (Large Object) sont ceux dont la taille maximale de ligne dépasse huit kilo-octets (Ko). SQL Server fournit un spécificateur `max` pour les types de données `varchar`, `nvarchar` et `varbinary` afin de permettre le stockage de valeurs pouvant atteindre 2^32 octets. Les colonnes de table et les variables Transact-SQL peuvent spécifier des types de données `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`. Dans .NET, les types de données `max` peuvent être extraits par un `DataReader` et spécifiés comme valeurs de paramètre d’entrée ou de sortie sans que cela nécessite une manipulation particulière. Pour les types de données de grande `varchar`, les données peuvent être récupérées et mises à jour de façon incrémentielle.  
  
Les types de données `max` peuvent être utilisés pour effectuer des comparaisons, en tant que variables Transact-SQL, ainsi que des concaténations. Elles peuvent également être utilisées dans les clauses distinctes, ORDER BY et GROUP BY d’une instruction SELECT, ainsi que dans les agrégats, les jointures et les sous-requêtes.

Pour plus d’informations sur les types de données de valeur élevée, consultez [utilisation de types de données de valeur élevée](https://go.microsoft.com/fwlink/?LinkId=120498) à partir de documentation en ligne de SQL Server.
  
## <a name="large-value-type-restrictions"></a>Restrictions relatives aux types de valeur élevée  
Les restrictions suivantes s’appliquent aux types de données `max`, qui n’existent pas pour les types de données plus petits :  
  
- Un `sql_variant` ne peut pas contenir un grand `varchar` type de données.  
  
- Les colonnes de grande `varchar` ne peuvent pas être spécifiées en tant que colonne clé dans un index. Elles sont autorisées dans une colonne incluse dans un index non cluster.  
  
- Les colonnes de grande `varchar` ne peuvent pas être utilisées en tant que colonnes clés de partitionnement.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Utilisation des types de valeur élevée dans Transact-SQL  
La fonction Transact-SQL `OPENROWSET` est une méthode unique de connexion et d’accès aux données distantes. Il est possible de référencer `OPENROWSET` dans la clause FROM d’une requête comme s’il s’agissait du nom d’une table. Il est également possible de le référencer comme table cible d’une instruction INSERT, UPDATE ou DELETE.  
  
La fonction `OPENROWSET` comprend le fournisseur d’ensembles de lignes `BULK`, qui vous permet de lire les données directement à partir d’un fichier sans charger les données dans une table cible. Cela vous permet d’utiliser `OPENROWSET` dans une simple instruction INSERT SELECT.  
  
Les arguments de l’option `OPENROWSET BULK` permettent d’exercer un contrôle important sur l’emplacement où commence et se termine la lecture de données, sur la manière de gérer les erreurs et sur la façon d’interpréter les données. Vous pouvez par exemple spécifier que le fichier de données soit lu comme un ensemble d’une seule ligne et d’une seule colonne du type `varbinary`, `varchar` ou `nvarchar`. Pour obtenir la syntaxe complète et les options, consultez Documentation en ligne de SQL Server.  
  
L’exemple suivant insère une photo dans la table ProductPhoto de l’exemple de base de données AdventureWorks. Lors de l’utilisation du fournisseur `BULK OPENROWSET`, vous devez fournir la liste nommée des colonnes même si vous n’insérez pas de valeurs dans chaque colonne. Dans ce cas, la clé primaire est définie comme une colonne d’identité et peut être omise dans la liste des colonnes. Notez que vous devez également fournir un nom de corrélation à la fin de l’instruction `OPENROWSET`, dans ce cas ThumbnailPhoto. Cela correspond à la colonne de la table `ProductPhoto` dans laquelle le fichier est chargé.  
  
```sql
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>Mise à jour de données à l’aide d’UPDATE .WRITE  
L’instruction Transact-SQL UPDATE possède une nouvelle syntaxe WRITE permettant de modifier le contenu des colonnes `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`. Cela vous permet d’effectuer des mises à jour partielles des données. MISE à jour. La syntaxe d’écriture est présentée ici sous forme abrégée :  
  
UPDATE  
  
{ *\<object>* }  
  
SET  
  
{ *column_name* = {. WRITE ( *expression* , @Offset, @Length)}  
  
La méthode WRITE spécifie qu’une section de la valeur *column_name* sera modifiée. L’expression est la valeur qui sera copiée dans *column_name*, `@Offset` est le point à partir duquel l’expression sera écrite et l’argument `@Length` indique la longueur de la section dans la colonne.  
  
|Si|Alors|  
|--------|----------|  
|L’expression a la valeur NULL|`@Length` est ignoré et la valeur de *column_name* est tronquée à l’emplacement spécifié par `@Offset`.|  
|`@Offset` est NULL|L’opération de mise à jour ajoute l’expression à la fin de la valeur de *column_name* existante et `@Length` est ignoré.|  
|`@Offset` est supérieur à la longueur de la valeur column_name|SQL Server retourne une erreur.|  
|`@Length` est NULL|La mise à jour supprime toutes les données de `@Offset` jusqu’à la fin de la valeur de `column_name`.|  
  
> [!NOTE]
>  Ni `@Offset` ni `@Length` ne peut être un nombre négatif.  
  
## <a name="example"></a>Exemple  
Cet exemple Transact-SQL met à jour une valeur partielle dans DocumentSummary, une colonne `nvarchar(max)` dans la table Document de la base de données AdventureWorks. Le terme « components » est remplacé par le terme « features », en spécifiant le terme de remplacement, la position de départ (décalage) du terme à remplacer dans les données existantes et le nombre de caractères à remplacer (longueur). L’exemple comprend des instructions SELECT avant et après l’instruction UPDATE pour comparer les résultats.  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>Utilisation des types de valeur élevée dans ADO.NET  
Vous pouvez utiliser des types de valeur élevée dans ADO.NET en spécifiant des types de valeur élevée comme objets <xref:Microsoft.Data.SqlClient.SqlParameter> d’un objet <xref:Microsoft.Data.SqlClient.SqlDataReader> afin de retourner un jeu de résultats, ou en utilisant un objet <xref:Microsoft.Data.SqlClient.SqlDataAdapter> pour remplir un `DataSet`/`DataTable`. Il n’y a aucune différence entre la façon dont vous travaillez avec un type de valeur élevée et le type de données de plus petite valeur associé.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Utilisation de GetSqlBytes pour récupérer des données  
La méthode `GetSqlBytes` de la <xref:Microsoft.Data.SqlClient.SqlDataReader> peut être utilisée pour récupérer le contenu d’une colonne `varbinary(max)`. Le fragment de code suivant suppose un objet <xref:Microsoft.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne `varbinary(max)` données d’une table et un objet <xref:Microsoft.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données en tant que <xref:System.Data.SqlTypes.SqlBytes>.  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Utilisation de GetSqlChars pour récupérer des données  
La méthode `GetSqlChars` de la <xref:Microsoft.Data.SqlClient.SqlDataReader> peut être utilisée pour récupérer le contenu d’une colonne `varchar(max)` ou `nvarchar(max)`. Le fragment de code suivant suppose un objet <xref:Microsoft.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne `nvarchar(max)` données d’une table et un objet <xref:Microsoft.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données.   
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Utilisation de GetSqlBinary pour récupérer des données  
La méthode `GetSqlBinary` d’un <xref:Microsoft.Data.SqlClient.SqlDataReader> peut être utilisée pour récupérer le contenu d’une colonne `varbinary(max)`. Le fragment de code suivant suppose un objet <xref:Microsoft.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne `varbinary(max)` données d’une table et d’un objet <xref:Microsoft.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données sous la forme d’un flux de <xref:System.Data.SqlTypes.SqlBinary>.  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>Utilisation de GetBytes pour récupérer des données  
La méthode `GetBytes` d’un <xref:Microsoft.Data.SqlClient.SqlDataReader> lit un flux d’octets à partir de l’offset de colonne spécifié dans un tableau d’octets, en commençant au décalage de tableau spécifié. Le fragment de code suivant suppose un objet <xref:Microsoft.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les octets dans un tableau d’octets. Notez que, contrairement à `GetSqlBytes`, `GetBytes` nécessite une taille pour la mémoire tampon du tableau.  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>Utilisation de GetValue pour récupérer des données  
La méthode `GetValue` d’un <xref:Microsoft.Data.SqlClient.SqlDataReader> lit la valeur à partir de l’offset de colonne spécifié dans un tableau. Le fragment de code suivant suppose un objet <xref:Microsoft.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données binaires à partir de l’offset de la première colonne, puis les données de chaîne à partir du deuxième décalage de colonne.  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Conversion de types de valeur élevée en types CLR  
Vous pouvez convertir le contenu d’une colonne `varchar(max)` ou `nvarchar(max)` à l’aide de l’une des méthodes de conversion de chaînes, telles que `ToString`. Le fragment de code suivant suppose qu’un objet <xref:Microsoft.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données.  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>Exemple  
Le code suivant récupère le nom et l’objet `LargePhoto` à partir de la table `ProductPhoto` dans la base de données `AdventureWorks` et l’enregistre dans un fichier. L’assembly doit être compilé avec une référence à l’espace de noms <xref:System.Drawing>.  La méthode <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> de la <xref:Microsoft.Data.SqlClient.SqlDataReader> retourne un objet <xref:System.Data.SqlTypes.SqlBytes> qui expose une propriété `Stream`. Le code utilise celle-ci pour créer un nouvel objet `Bitmap`, puis l’enregistre dans le Gif `ImageFormat`.  
  
[!code-csharp[DataWorks SqlBytes_Stream#1](~/../sqlclient/doc/samples/SqlBytes_Stream.cs#1)]
  
## <a name="using-large-value-type-parameters"></a>paramètres de type valeurs élevées (ADO.NET)  
Les types de valeur élevée peuvent être utilisés dans les objets <xref:Microsoft.Data.SqlClient.SqlParameter> de la même façon que vous utilisez des types de valeur plus petits dans les objets <xref:Microsoft.Data.SqlClient.SqlParameter>. Vous pouvez extraire des types de valeur élevée en tant que valeurs <xref:Microsoft.Data.SqlClient.SqlParameter>, comme illustré dans l’exemple suivant. Le code suppose que la procédure stockée GetDocumentSummary suivante existe dans l’exemple de base de données AdventureWorks. La procédure stockée prend un caractère d’entrée nommé @DocumentID et retourne le contenu de la colonne DocumentSummary dans le paramètre de sortie @DocumentSummary.  
  
```sql
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>Exemple  
Le code ADO.NET crée <xref:Microsoft.Data.SqlClient.SqlConnection> et <xref:Microsoft.Data.SqlClient.SqlCommand> objets pour exécuter la procédure stockée GetDocumentSummary et récupérer le résumé du document, qui est stocké en tant que type de valeur élevée. Le code transmet une valeur pour le paramètre d’entrée @DocumentID et affiche les résultats retournés dans le paramètre de sortie @DocumentSummary dans la fenêtre de console.  
  
[!code-csharp[DataWorks SqlParameter_Value#1](~/../sqlclient/doc/samples/SqlParameter_Value.cs#1)]
  
## <a name="next-steps"></a>Étapes suivantes
- [Données binaires et à valeurs élevées SQL Server](sql-server-binary-large-value-data.md)
- [Opérations de données SQL Server dans ADO.NET](sql-server-data-operations.md)
