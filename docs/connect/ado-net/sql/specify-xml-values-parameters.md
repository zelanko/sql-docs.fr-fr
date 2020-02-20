---
title: Spécification de valeurs XML comme paramètres
description: Montre comment passer des données XML en tant que paramètre à une commande.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 7f9893d7ac9dd83ae5212684678fc240a8d77097
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251147"
---
# <a name="specifying-xml-values-as-parameters"></a>Spécification de valeurs XML comme paramètres

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Si une requête demande un paramètre dont la valeur est une chaîne XML, les développeurs peuvent fournir cette valeur à l’aide d’une instance du type de données **SqlXml**. Il n’y a réellement pas d’astuces ; les colonnes XML dans SQL Server acceptent les valeurs de paramètres exactement de la même manière que d’autres types de données.  
  
## <a name="example"></a>Exemple  
L’application console suivante crée une table dans la base de données **AdventureWorks**. La nouvelle table inclut une colonne nommée **SalesID** et une colonne XML nommée **SalesInfo**.  
  
> [!NOTE]
>  L’exemple de base de données **AdventureWorks** n’est pas installé par défaut quand vous installez SQL Server. Vous pouvez l’installer en exécutant le programme d’installation de SQL Server.  
  
L’exemple prépare un objet <xref:Microsoft.Data.SqlClient.SqlCommand> pour insérer une ligne dans la nouvelle table. Un fichier enregistré fournit les données XML nécessaires pour la colonne **SalesInfo**.  
  
Pour créer le fichier nécessaire à l’exécution de l’exemple, créez un nouveau fichier texte dans le même dossier que votre projet. Nommez le fichier MyTestStoreData.xml. Ouvrez le fichier dans Bloc-notes, puis copiez et collez le texte suivant :  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =   
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +   
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +   
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +   
            "DROP TABLE [dbo].[XmlDataTypeSample];" +   
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +   
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +   
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =   
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =   
            "INSERT INTO [dbo].[XmlDataTypeSample] " +   
            "([SalesInfo] ) " +   
            "VALUES(@xmlParameter )";  
        SqlCommand command =   
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a   
        //  SqlXml-data typed variable.  
        SqlXml newXml =   
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- <xref:System.Data.SqlTypes.SqlXml>
- [Données XML dans SQL Server](xml-data-sql-server.md)
