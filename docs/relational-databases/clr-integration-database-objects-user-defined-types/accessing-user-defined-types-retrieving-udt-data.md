---
title: Récupération de données UDT | Microsoft Docs
description: Cet article explique comment accéder aux UDT dans une base de données SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SqlDataReader object
- ADO.NET [CLR integration]
- binding UDTs [CLR integration]
- UDTs [CLR integration], ADO.NET
- assemblies [CLR integration], user-defined types
- query parameters [CLR integration]
- user-defined types [CLR integration], ADO.NET
- bytes [CLR integration]
ms.assetid: 6a98ac8c-0e69-4c03-83a4-2062cb782049
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ab209dccc53db8f1c90a5b25c6372be4af71025
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727839"
---
# <a name="accessing-user-defined-types---retrieving-udt-data"></a>Accès aux types définis par l’utilisateur - Extraction de données UDT
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Pour créer un type défini par l'utilisateur (UDT) sur le client, l'assembly enregistré comme UDT dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être accessible par l'application cliente. L'assembly de type défini par l'utilisateur (UDT) peut être placé dans le même répertoire que l'application, ou dans le Global Assembly Cache (GAC). Vous pouvez également définir une référence à l'assembly dans votre projet.  
  
## <a name="requirements-for-using-udts-in-adonet"></a>Conditions requises pour utiliser les UDT dans ADO.NET  
 L'assembly chargé dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l'assembly sur le client doivent être compatibles pour que l'UDT puisse être créé sur le client. Pour les UDT définis avec le format de sérialisation **natif** , les assemblys doivent être structurellement compatibles. Pour les assemblys définis avec le format **UserDefined** , l’assembly doit être disponible sur le client.  
  
 Vous n'avez pas besoin d'une copie de l'assembly UDT sur le client pour extraire les données brutes d'une colonne UDT d'une table.  
  
> [!NOTE]  
>  **SqlClient** peut ne pas réussir à charger un UDT en cas de versions incompatibles UDT ou d’autres problèmes. Dans ce cas, utilisez les mécanismes de résolution des problèmes traditionnels pour déterminer pourquoi l'application appelante ne peut pas trouver l'assembly contenant l'UDT. Pour plus d'informations, lisez la rubrique intitulée « Diagnostic d'erreurs avec les Assistants de débogage managés » dans la documentation du .NET Framework.  
  
## <a name="accessing-udts-with-a-sqldatareader"></a>Accès aux UDT avec un SqlDataReader  
 Un **System. Data. SqlClient. SqlDataReader** peut être utilisé à partir du code client pour récupérer un jeu de résultats qui contient une colonne UDT, qui est exposée en tant qu’instance de l’objet.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre comment utiliser la méthode **main** pour créer un nouvel objet **SqlDataReader** . Les actions suivantes se produisent dans l'exemple de code :  
  
1.  La méthode Main crée un nouvel objet **SqlDataReader** et récupère les valeurs de la table points, qui a une colonne UDT nommée point.  
  
2.  L'UDT Point expose les coordonnées X et Y définies comme entiers.  
  
3.  Le type défini par l’utilisateur définit une méthode de **distance** et une méthode **GetDistanceFromXY** .  
  
4.  L'exemple de code extrait les valeurs de la clé primaire et les colonnes UDT pour montrer les fonctions de l'UDT.  
  
5.  L’exemple de code appelle les méthodes **point. distance** et **point. GetDistanceFromXY** .  
  
6.  Les résultats s'affichent dans la fenêtre de la console.  
  
> [!NOTE]  
>  L'application doit déjà avoir une référence à l'assembly UDT.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module ReadPoints  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the value of the UDT  
                Dim pnt As Point = CType(rdr(1), Point)  
  
             ' You can also use GetSqlValue and GetValue  
             ' Dim pnt As Point = CType(rdr.GetSqlValue(1), Point)  
             ' Dim pnt As Point = CType(rdr.GetValue(1), Point)  
  
                ' Print values  
                Console.WriteLine( _  
                 "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}", _  
                  id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance())  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
         & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
namespace Microsoft.Samples.SqlServer  
{  
class ReadPoints  
{  
static void Main()  
{  
  string connectionString = GetConnectionString();  
  using (SqlConnection cnn = new SqlConnection(connectionString))  
  {  
    cnn.Open();  
    SqlCommand cmd = new SqlCommand(  
       "SELECT ID, Pnt FROM dbo.Points", cnn);  
    SqlDataReader rdr = cmd.ExecuteReader();  
  
    while (rdr.Read())  
    {  
      // Retrieve the value of the Primary Key column  
      int id = rdr.GetInt32(0);  
  
        // Retrieve the value of the UDT  
        Point pnt = (Point)rdr[1];  
  
        // You can also use GetSqlValue and GetValue  
        // Point pnt = (Point)rdr.GetSqlValue(1);  
        // Point pnt = (Point)rdr.GetValue(1);  
  
        Console.WriteLine(  
        "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}",   
        id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance());  
    }  
  rdr.Close();  
  Console.WriteLine("done");  
  }  
  static private string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,   
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="binding-udts-as-bytes"></a>Liaison des UDT comme octets  
 Dans certaines situations, vous pouvez extraire les données brutes de la colonne UDT. Peut-être le type n'est-il pas disponible localement ou ne souhaitez-vous pas instancier une instance de l'UDT. Vous pouvez lire les octets bruts dans un tableau d’octets à l’aide de la méthode **GetBytes** d’un **SqlDataReader**. Cette méthode lit un flux d'octets à partir de l'offset de colonne spécifié dans la mémoire tampon d'un tableau commençant à un offset de mémoire tampon donné. Une autre option consiste à utiliser l’une des méthodes **GetSqlBytes** ou **GetSqlBinary** et à lire tout le contenu en une seule opération. Dans l'un et l'autre cas, comme l'objet UDT n'est jamais instancié, vous n'avez pas besoin de définir une référence à l'UDT dans l'assembly client.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre comment récupérer les données de **point** en tant qu’octets bruts dans un tableau d’octets à l’aide d’un **SqlDataReader**. Le code utilise **System. Text. StringBuilder** pour convertir les octets bruts en une représentation sous forme de chaîne à afficher dans la fenêtre de la console.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the raw bytes into a byte array  
                Dim buffer(31) As Byte  
                Dim byteCount As Integer = _  
                 CInt(rdr.GetBytes(1, 0, buffer, 0, 31))  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", buffer(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
        string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand("SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Retrieve the raw bytes into a byte array  
                byte[] buffer = new byte[32];  
                long byteCount = rdr.GetBytes(1, 0, buffer, 0, 32);  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", buffer[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
### <a name="example-using-getsqlbytes"></a>Exemple utilisant GetSqlBytes  
 Cet exemple montre comment récupérer les données de **point** en tant qu’octets bruts en une seule opération à l’aide de la méthode **GetSqlBytes** . Le code utilise un **StringBuilder** pour convertir les octets bruts en une représentation sous forme de chaîne à afficher dans la fenêtre de console.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Use SqlBytes to retrieve raw bytes  
                Dim sb As SqlBytes = rdr.GetSqlBytes(1)  
                Dim byteCount As Long = sb.Length  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", sb(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
         string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Use SqlBytes to retrieve raw bytes  
                SqlBytes sb = rdr.GetSqlBytes(1);  
                long byteCount = sb.Length;  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", sb[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="working-with-udt-parameters"></a>Utilisation des paramètres UDT  
 Les paramètres UDT peuvent être utilisés comme paramètres d'entrée et de sortie dans votre code ADO.NET.  
  
## <a name="using-udts-in-query-parameters"></a>Utilisation des UDT dans les paramètres de requête  
 Les UDT peuvent être utilisés comme valeurs de paramètre lors de la configuration d’un **SqlParameter** pour un objet **System. Data. SqlClient. SqlCommand** . L’énumération **SqlDbType. UDT** d’un objet **SqlParameter** est utilisée pour indiquer que le paramètre est un type défini par l’utilisateur lors de l’appel de la méthode **Add** à la collection **Parameters** . La propriété **UdtTypeName** d’un objet **SqlCommand** est utilisée pour spécifier le nom complet de l’UDT dans la base de données à l’aide de la syntaxe *Database. schema_name. object_name* . Sans être obligatoire, l'utilisation du nom complet supprime l'ambiguïté de votre code.  
  
> [!NOTE]  
>  Une copie locale de l'assembly UDT doit être accessible par le projet client.  
  
### <a name="example"></a>Exemple  
 Le code de cet exemple crée des objets **SqlCommand** et **SqlParameter** pour insérer des données dans une colonne UDT d’une table. Le code utilise l’énumération **SqlDbType. UDT** pour spécifier le type de données, et la propriété **UdtTypeName** de l’objet **SqlParameter** pour spécifier le nom complet de l’UDT dans la base de données.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports system.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim ConnectionString As String = GetConnectionString()  
    Dim cnn As New SqlConnection(ConnectionString)  
    Using cnn  
      Dim cmd As SqlCommand = cnn.CreateCommand()  
      cmd.CommandText = "INSERT INTO dbo.Points (Pnt) VALUES (@Point)"  
      cmd.CommandType = CommandType.Text  
  
      Dim param As New SqlParameter("@Point", SqlDbType.Udt)      
      param.UdtTypeName = "TestPoint.dbo.Point"      
      param.Direction = ParameterDirection.Input      
      param.Value = New Point(5, 6)      
      cmd.Parameters.Add(param)  
  
      cnn.Open()  
      cmd.ExecuteNonQuery()  
      Console.WriteLine("done")  
    End Using  
  End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  string ConnectionString = GetConnectionString();  
     using (SqlConnection cnn = new SqlConnection(ConnectionString))  
     {  
       SqlCommand cmd = cnn.CreateCommand();  
       cmd.CommandText =   
         "INSERT INTO dbo.Points (Pnt) VALUES (@Point)";  
       cmd.CommandType = CommandType.Text;  
  
       SqlParameter param = new SqlParameter("@Point", SqlDbType.Udt);       param.UdtTypeName = "TestPoint.dbo.Point";       param.Direction = ParameterDirection.Input;       param.Value = new Point(5, 6);       cmd.Parameters.Add(param);  
  
       cnn.Open();  
       cmd.ExecuteNonQuery();  
       Console.WriteLine("done");  
     }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux types définis par l'utilisateur dans ADO.NET](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
  
  
