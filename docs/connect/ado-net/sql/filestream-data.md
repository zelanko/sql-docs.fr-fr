---
title: Données FILESTREAM
description: Décrit comment utiliser les données de valeur élevée stockées dans SQL Server 2008 avec l’attribut FILESTREAM.
ms.date: 08/15/2019
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e3e26a76522d1c1a99794076c5f152e6ec1e1f7d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896739"
---
# <a name="filestream-data"></a>Données FILESTREAM

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

L'attribut de stockage FILESTREAM est destiné aux données binaires (BLOB) stockées dans une colonne varbinary(max). Avant FILESTREAM, le stockage de données binaires nécessitait un traitement spécial. Les données non structurées, telles que les documents texte, les images et les vidéos, sont souvent stockées en dehors de la base de données, ce qui rend difficile leur gestion.

> [!NOTE]
> Vous devez installer .NET Framework 3.5 SP1 (ou version ultérieure) ou .NET Core pour travailler avec des données FILESTREAM à l’aide de SqlClient.

Si vous spécifiez l’attribut FILESTREAM sur une colonne varbinary(max), SQL Server stocke les données sur le système de fichiers NTFS local plutôt que dans le fichier de base de données. Même si elles sont stockées séparément, vous pouvez utiliser les mêmes instructions Transact-SQL prises en charge pour l’utilisation des données varbinary(max) stockées dans la base de données.

## <a name="sqlclient-support-for-filestream"></a>Prise en charge de SqlClient pour FILESTREAM

Le fournisseur de données Microsoft SqlClient pour SQL Server, <xref:Microsoft.Data.SqlClient>, prend en charge la lecture et l’écriture vers les données FILESTREAM en utilisant la classe <xref:Microsoft.Data.SqlTypes.SqlFileStream> définie dans l’espace de noms <xref:System.Data.SqlTypes>. `SqlFileStream` hérite de la classe <xref:System.IO.Stream>, qui fournit des méthodes pour lire et écrire dans des flux de données. La lecture depuis un flux transfère des données du flux vers une structure de données, comme un tableau d’octets. L’écriture transfère les données de la structure de données dans un flux.

### <a name="creating-the-sql-server-table"></a>Créer la table SQL Server

L’instruction Transact-SQL suivante crée une table nommée employees et y insère une ligne de données. Une fois que vous avez activé le stockage FILESTREAM, vous pouvez utiliser ce tableau conjointement avec les exemples de code ci-après. Les liens vers les ressources dans la Documentation en ligne de SQL Server figurent à la fin de cette rubrique.

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Exemple : Lecture, remplacement et insertion de données FILESTREAM

L’exemple de code suivant montre comment lire les données à partir d'un fichier FILESTREAM. Le code obtient le chemin d’accès logique au fichier, en affectant à `FileAccess` la valeur `Read` et à `FileOptions` la valeur `SequentialScan`. Le code lit ensuite les octets de SqlFileStream dans la mémoire tampon. Les octets sont alors écrits dans la fenêtre de la console.

L’exemple montre également comment écrire des données dans un fichier FILESTREAM dans lequel toutes les données existantes sont remplacées. Le code obtient le chemin d’accès logique au fichier et crée le `SqlFileStream`, en affectant à `FileAccess` la valeur `Write` et à `FileOptions` la valeur `SequentialScan`. Un seul octet est écrit dans le `SqlFileStream`, en remplaçant toutes les données dans le fichier.

L’exemple illustre aussi comment écrire des données dans un fichier FILESTREAM en utilisant la méthode Seek pour ajouter des données à la fin du fichier. Le code obtient le chemin d’accès logique au fichier et crée le `SqlFileStream`, en affectant à `FileAccess` la valeur `ReadWrite` et à `FileOptions` la valeur `SequentialScan`. Le code utilise la méthode Seek pour rechercher jusqu’à la fin du fichier, en ajoutant un octet unique au fichier existant.

```csharp
using System;
using Microsoft.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

Pour obtenir un autre exemple, consultez [Guide pratique pour stocker et récupérer des données binaires dans une colonne de flux de fichiers](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).

## <a name="resources-in-sql-server-books-online"></a>Ressources dans la documentation en ligne de SQL Server

La documentation complète relative à FILESTREAM se trouve dans les sections suivantes de la Documentation en ligne de SQL Server.

|Rubrique|Description|
|-----------|-----------------|
|[FILESTREAM (SQL Server)](../../../relational-databases/blob/filestream-sql-server.md)|Explique quand utiliser le stockage FILESTREAM et comment il intègre le moteur de base de données SQL Server avec un système de fichiers NTFS.|
|[Créer des applications clientes pour les données FILESTREAM](../../../relational-databases/blob/create-client-applications-for-filestream-data.md)|Décrit les fonctions de l’API Windows permettant d’utiliser des données FILESTREAM.|
|[Utilisation de FILESTREAM avec d’autres fonctionnalités SQL Server](../../../relational-databases/blob/filestream-compatibility-with-other-sql-server-features.md)|Fournit des considérations, instructions et limitations pour l’utilisation des données FILESTREAM avec d’autres fonctionnalités de SQL Server.|

## <a name="next-steps"></a>Étapes suivantes
- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
- [Données binaires et à valeurs élevées SQL Server](sql-server-binary-large-value-data.md)
