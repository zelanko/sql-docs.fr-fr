---
title: Opérations uniques de copie en bloc
description: Décrit comment effectuer une seule copie en bloc de données dans une instance de SQL Server à l’aide de la classe SqlBulkCopy et comment effectuer l’opération de copie en bloc à l’aide d’instructions Transact-SQL et de la classe SqlCommand.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 1029d9a0121b23963ccfc12582bd9d9cc7fd6cd6
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896598"
---
# <a name="single-bulk-copy-operations"></a>Opérations uniques de copie en bloc

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

L'approche la plus simple pour effectuer une opération de copie en bloc SQL Server est d'effectuer une opération unique sur une base de données. Par défaut, une opération de copie en bloc est effectuée comme une opération isolée : l'opération de copie se produit de façon non transactionnelle, sans possibilité de restauration.  
  
> [!NOTE]
>  Si vous devez restaurer tout ou partie de la copie en bloc en cas d’erreur, vous pouvez utiliser une transaction gérée par <xref:Microsoft.Data.SqlClient.SqlBulkCopy> ou effectuer l’opération de copie en bloc dans une transaction existante. **SqlBulkCopy** fonctionne également avec <xref:System.Transactions> si la connexion est inscrite (implicitement ou explicitement) dans une transaction **System.Transactions**.  
>   
>  Pour plus d’informations, consultez [Transaction et opérations de copie en bloc](transaction-bulk-copy-operations.md).  
  
Les étapes générales pour effectuer une opération de copie en bloc sont les suivantes :  
  
1. Connectez-vous au serveur source et obtenez les données à copier. Les données peuvent également provenir d’autres sources, si elles peuvent être récupérées à partir d’un objet <xref:System.Data.IDataReader> ou <xref:System.Data.DataTable>.  
  
2. Connectez-vous au serveur de destination (à moins que vous souhaitiez que **SqlBulkCopy** établisse une connexion à votre place).  
  
3. Créez un objet <xref:Microsoft.Data.SqlClient.SqlBulkCopy>, en définissant les propriétés nécessaires.  
  
4. Définissez la propriété **DestinationTableName** pour indiquer la table cible pour l’opération d’insertion en bloc.  
  
5. Appelez l’une des méthodes **WriteToServer**.  
  
6. À titre facultatif, mettez à jour les propriétés et appelez de nouveau la méthode **WriteToServer** si nécessaire.  
  
7. Appelez <xref:Microsoft.Data.SqlClient.SqlBulkCopy.Close%2A> ou enveloppez les opérations de copie en bloc dans une instruction `Using`.  
  
> [!CAUTION]
>  Il est préférable que les types de données des colonnes source et cible correspondent. Si les types de données ne correspondent pas, **SqlBulkCopy** tente de convertir chaque valeur source vers le type de données cible en utilisant les règles employées par <xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>. Les conversions peuvent affecter les performances et entraîner des erreurs inattendues. Par exemple, un type de données `Double` peut être converti en type de données `Decimal` la plupart du temps, mais pas toujours.  
  
## <a name="example"></a>Exemple  
L'application de console suivante montre comment charger des données à l'aide de la classe <xref:Microsoft.Data.SqlClient.SqlBulkCopy>. Dans cet exemple, <xref:Microsoft.Data.SqlClient.SqlDataReader> est utilisé pour copier des données de la table **Production.Product** dans la base de données **AdventureWorks** SQL Server vers une table semblable dans la même base de données.  
  
> [!IMPORTANT]
>  Cet exemple ne s’exécutera pas, sauf si vous avez créé les tables de travail comme décrit dans [Configuration de l’exemple de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
[!code-csharp[DataWorks SqlBulkCopy_WriteToServer#1](~/../sqlclient/doc/samples/SqlBulkCopy_WriteToServer.cs#1)]
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Exécution d'une opération de copie en bloc à l'aide de Transact-SQL et de la classe de commande  
L’exemple suivant illustre comment utiliser la méthode <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> pour exécuter l’instruction BULK INSERT.  
  
> [!NOTE]
>  Le chemin d'accès de la source de données est relatif au serveur. Le processus serveur doit avoir accès à ce chemin d'accès pour que l'opération de copie en bloc réussisse.  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [Opérations de copie en bloc dans SQL Server](bulk-copy-operations-sql-server.md)
