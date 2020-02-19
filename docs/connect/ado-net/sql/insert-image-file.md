---
title: Insertion d’une image à partir d’un fichier
description: Décrit comment utiliser une image à partir d’un fichier.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 613ae5b3326bc49ab25f30628ecd85e13959e2dc
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247744"
---
# <a name="inserting-an-image-from-a-file"></a>Insertion d’une image à partir d’un fichier

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Vous pouvez écrire un objet binaire large (BLOB) dans une base de données sous forme de données binaires ou de caractères, selon le type de champ de votre source de données. L’objet BLOB est un terme générique qui fait référence aux types de données `text`, `ntext` et `image`, qui contiennent généralement des documents et des images.  
  
Pour écrire une valeur blob dans votre base de données, utilisez l’instruction INSERT ou UPDATE appropriée et passez la valeur blob en tant que paramètre d’entrée. Si votre objet BLOB est stocké sous forme de texte, tel qu’un champ SQL Server `text`, vous pouvez passer l’objet BLOB comme paramètre de chaîne. Si l’objet BLOB est stocké au format binaire, tel qu’un champ SQL Server `image`, vous pouvez passer un tableau de type `byte` comme paramètre binaire.
  
## <a name="example"></a>Exemple  
L’exemple de code suivant ajoute des informations sur les employés à la table Employees de la base de données Northwind. Une photo de l’employé est lue à partir d’un fichier et ajoutée au champ photo dans la table, qui est un champ d’image.  
  
```csharp  
public static void AddEmployee(  
  string lastName,   
  string firstName,   
  string title,   
  DateTime hireDate,   
  int reportsTo,   
  string photoFilePath,   
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);   
  
  command.Parameters.Add("@LastName",    
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",   
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",       
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",   
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",   
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [Données binaires et à valeurs élevées SQL Server](sql-server-binary-large-value-data.md)
