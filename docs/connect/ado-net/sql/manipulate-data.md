---
title: Manipulation de données
description: Fournit des exemples de codage d’applications MARS.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: df430bbacb69e1d95d001e4f9340ca60473503cd
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452163"
---
# <a name="manipulating-data"></a>Manipulation de données

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Avant l’introduction de plusieurs jeux de résultats actifs (MARS), les développeurs devaient utiliser soit plusieurs connexions, soit des curseurs côté serveur pour résoudre certains scénarios. En outre, quand plusieurs connexions étaient utilisées dans une situation transactionnelle, des connexions liées (avec **sp_getbindtoken** et **sp_bindsession**) étaient requises. Les scénarios suivants montrent comment utiliser une connexion compatible MARS au lieu de plusieurs connexions.  
  
## <a name="using-multiple-commands-with-mars"></a>Utilisation de plusieurs commandes avec MARS  
L’application console suivante montre comment utiliser deux objets <xref:Microsoft.Data.SqlClient.SqlDataReader> avec deux objets <xref:Microsoft.Data.SqlClient.SqlCommand> et un objet <xref:Microsoft.Data.SqlClient.SqlConnection> unique avec MARS activé.  
  
### <a name="example"></a>Exemple  
L’exemple ouvre une connexion unique à la base de données **AdventureWorks**. À l’aide d’un objet <xref:Microsoft.Data.SqlClient.SqlCommand>, un <xref:Microsoft.Data.SqlClient.SqlDataReader> est créé. À mesure que le lecteur est utilisé, une deuxième <xref:Microsoft.Data.SqlClient.SqlDataReader> est ouverte, en utilisant les données du premier <xref:Microsoft.Data.SqlClient.SqlDataReader> comme entrée de la clause WHERE pour le second lecteur.  
  
> [!NOTE]
>  L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server. La chaîne de connexion fournie dans l’exemple de code suppose que la base de données est installée et disponible sur l’ordinateur local. Modifiez la chaîne de connexion en fonction des besoins de votre environnement.  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =   
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =   
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +   
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =   
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +   
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a>Lecture et mise à jour des données avec MARS  
MARS permet l’utilisation d’une connexion pour les opérations de lecture et les opérations DML (Data Manipulation Language) avec plusieurs opérations en attente. Cette fonctionnalité élimine la nécessité pour une application de traiter les erreurs de connexion. En outre, MARS peut remplacer l’utilisateur des curseurs côté serveur, qui consomme généralement davantage de ressources. Pour finir, comme plusieurs opérations peuvent opérer sur une seule connexion, elles peuvent partager le même contexte de transaction, en éliminant la nécessité d’utiliser les procédures stockées **système sp_getbindtoken** et **sp_bindsession**.  
  
### <a name="example"></a>Exemple  
L’application console suivante montre comment utiliser deux objets <xref:Microsoft.Data.SqlClient.SqlDataReader> avec trois objets <xref:Microsoft.Data.SqlClient.SqlCommand> et un objet <xref:Microsoft.Data.SqlClient.SqlConnection> unique avec MARS activé. Le premier objet de commande récupère une liste de fournisseurs dont le niveau de solvabilité est 5. Le second objet de commande utilise l’ID de fournisseur fourni par un <xref:Microsoft.Data.SqlClient.SqlDataReader> pour charger le deuxième <xref:Microsoft.Data.SqlClient.SqlDataReader> avec tous les produits du fournisseur en question. Chaque enregistrement de produit est visité par le deuxième <xref:Microsoft.Data.SqlClient.SqlDataReader>. Un calcul est effectué afin de déterminer ce que doit être le nouveau **OnOrderQty**. Le troisième objet de commande est ensuite utilisé pour mettre à jour la table **ProductVendor** avec la nouvelle valeur. Tout ce processus se déroule au sein d’une seule transaction, qui est restaurée à la fin.  
  
> [!NOTE]
>  L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server. La chaîne de connexion fournie dans l’exemple de code suppose que la base de données est installée et disponible sur l’ordinateur local. Modifiez la chaîne de connexion en fonction des besoins de votre environnement.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +   
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +   
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +   
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +   
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrieve it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +   
    "Initial Catalog=AdventureWorks;" +   
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [MARS (Multiple Active Result Sets)](multiple-active-result-sets-mars.md)
