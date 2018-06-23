---
title: Procédures stockées CLR | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration], stored procedures
- stored procedures [CLR integration]
- common language runtime [SQL Server], stored procedures
- building database objects [CLR integration], stored procedures
- output parameters [CLR integration]
- tabular results
ms.assetid: bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33
caps.latest.revision: 74
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7f90cbc5e45a095225f5937864d87d336a9c95da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140089"
---
# <a name="clr-stored-procedures"></a>Procédures stockées du CLR
  Les procédures stockées sont des routines que vous ne pouvez pas utiliser dans des expressions scalaires. Contrairement aux fonctions scalaires, elles peuvent retourner des résultats scalaires et des messages au client, appeler des instructions DDL (Data Definition Language) et DML (Data Manipulation Language) et retourner des paramètres de sortie. Pour plus d’informations sur les avantages de l’intégration du CLR et en choisissant entre le code managé et [!INCLUDE[tsql](../../includes/tsql-md.md)], consultez [vue d’ensemble de l’intégration CLR](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="requirements-for-clr-stored-procedures"></a>Configuration requise pour les procédures stockées CLR  
 Dans le common language runtime (CLR), les procédures stockées sont implémentées en tant que méthodes statiques publiques sur une classe dans un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assembly. La méthode statique peut soit être déclarée de type « void », soit retourner une valeur entière. Si elle retourne une valeur entière, l'entier retourné est traité comme le code de retour de la procédure. Exemple :  
  
 `EXECUTE @return_status = procedure_name`  
  
 Le @return_status variable contient la valeur retournée par la méthode. Si la méthode est déclarée de type void, le code de retour est 0.  
  
 Si la méthode accepte des paramètres, le nombre de paramètres dans l'implémentation [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] doit être identique au nombre de paramètres employés dans la déclaration [!INCLUDE[tsql](../../includes/tsql-md.md)] de la procédure stockée.  
  
 Les paramètres passés à une procédure stockée CLR peuvent être de n'importe quel type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doté d'un équivalent en code managé. Pour que la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] crée la procédure, ces types doivent être spécifiés avec le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] natif équivalent le mieux approprié. Pour plus d’informations sur les conversions de type, consultez [de mappage de données de paramètre CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
### <a name="table-valued-parameters"></a>Paramètres table  
 Les paramètres table (types de tables définis par l'utilisateur et passés dans une procédure ou une fonction) offrent un moyen efficace pour passer plusieurs lignes de données au serveur. Paramètres table fournissent des fonctionnalités semblables aux tableaux de paramètres, mais offrent une plus grande souplesse et une intégration plus étroite avec [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ils sont également susceptibles de générer de meilleures performances. Les paramètres table aident également à réduire le nombre d'allers-retours au serveur. Au lieu d'envoyer plusieurs demandes au serveur, comme avec une liste de paramètres scalaires, les données peuvent être envoyées au serveur en tant que paramètres table. Un type de table défini par l'utilisateur ne peut pas être passé en tant que paramètre table à une fonction ou à une procédure stockée managée s'exécutant dans le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ni être retourné à partir de ces dernières. Pour plus d’informations sur les paramètres table, consultez [utiliser des paramètres &#40;moteur de base de données&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="returning-results-from-clr-stored-procedures"></a>Retour des résultats des procédures stockées CLR  
 Plusieurs moyens permettent de retourner des informations des procédures stockées [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Il peut s'agir notamment de paramètres de sortie, de résultats sous forme de tableau et de messages.  
  
### <a name="output-parameters-and-clr-stored-procedures"></a>Paramètres OUTPUT et procédures stockées CLR  
 Tout comme avec les procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)], des informations peuvent être retournées de procédures stockées [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] à l'aide de paramètres OUTPUT. La syntaxe DML [!INCLUDE[tsql](../../includes/tsql-md.md)] utilisée pour créer des procédures stockées [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] est le même que celle employée pour créer des procédures stockées écrites dans [!INCLUDE[tsql](../../includes/tsql-md.md)]. Le paramètre correspondant du code d'implémentation dans la classe [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] doit utiliser un paramètre passé par référence en guise d'argument. Notez que Visual Basic ne prend pas en charge les paramètres de sortie de la même manière que Visual C#. Vous devez spécifier le paramètre par référence et appliquer le \<Out() > attribut pour représenter un paramètre de sortie, comme suit :  
  
```  
Imports System.Runtime.InteropServices  
…  
Public Shared Sub PriceSum ( <Out()> ByRef value As SqlInt32)  
```  
  
 Le code ci-dessous présente une procédure stockée qui retourne des informations par le biais d'un paramètre OUTPUT :  
  
 C#  
  
```  
using System;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void PriceSum(out SqlInt32 value)  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         value = 0;  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT Price FROM Products", connection);  
         SqlDataReader reader = command.ExecuteReader();  
  
         using (reader)  
         {  
            while( reader.Read() )  
            {  
               value += reader.GetSqlInt32(0);  
            }  
         }           
      }  
   }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Runtime.InteropServices  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Executes a query and iterates over the results to perform a summation.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
  
        Using connection As New SqlConnection("context connection=true")  
           value = 0  
           Connection.Open()  
           Dim command As New SqlCommand("SELECT Price FROM Products", connection)  
           Dim reader As SqlDataReader  
           reader = command.ExecuteReader()  
  
           Using reader  
              While reader.Read()  
                 value += reader.GetSqlInt32(0)  
              End While  
           End Using  
        End Using          
    End Sub  
End Class  
```  
  
 Une fois que l’assembly contenant le CLR ci-dessus stockées procédure a été créée et créée sur le serveur, ce qui suit [!INCLUDE[tsql](../../includes/tsql-md.md)] est utilisée pour créer la procédure dans la base de données et spécifie *somme* comme paramètre de sortie.  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
-- if StoredProcedures class was inside a namespace, called MyNS,  
-- you would use:  
-- AS EXTERNAL NAME TestStoredProc.[MyNS.StoredProcedures].PriceSum  
```  
  
 Notez que *somme* est déclaré comme un `int` type de données SQL Server et que le *valeur* le paramètre défini dans la procédure stockée CLR est spécifié comme un `SqlInt32` type de données CLR. Lorsqu’un programme appelant exécute la procédure stockée CLR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit automatiquement le `SqlInt32` type de données CLR à un `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.  Pour plus d’informations sur le CLR des types de données peuvent et ne peut pas être convertis, consultez [de mappage de données de paramètre CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
### <a name="returning-tabular-results-and-messages"></a>Retour de résultats sous forme de tableau et de messages  
 Le retour au client de résultats sous forme de tableau et de messages s'effectue via l'objet `SqlPipe` obtenu en utilisant la propriété `Pipe` de la classe `SqlContext`. L'objet `SqlPipe` emploie une méthode `Send`. En appelant la méthode `Send`, vous pouvez transmettre des données à l'application appelante par l'intermédiaire du canal.  
  
 Il existe plusieurs surcharges de la méthode `SqlPipe.Send`. L'une d'elles permet d'envoyer un `SqlDataReader`, une autre de simplement transmettre une chaîne de texte.  
  
###### <a name="returning-messages"></a>Retour de messages  
 Utilisez `SqlPipe.Send(string)` pour envoyer des messages à l'application cliente. Le texte du message est limité à 8 000 caractères. Si le message dépasse cette limite, il sera tronqué.  
  
###### <a name="returning-tabular-results"></a>Retour de résultats sous forme de tableau  
 Pour envoyer directement les résultats d'une requête au client, appliquez l'une des surcharges de la méthode `Execute` à l'objet `SqlPipe`. C'est le moyen le plus efficace de retourner des résultats au client puisque les données sont transférées vers les tampons réseau sans être copiées dans la mémoire managée. Exemple :  
  
 [C#]  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the results to the client directly.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void ExecuteToClient()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version", connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub ExecuteToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 Pour envoyer les résultats d'une requête exécutée précédemment via le fournisseur in-process (ou pour pré-traiter les données à l'aide d'une implémentation personnalisée de `SqlDataReader`), utilisez la surcharge de la méthode `Send` qui accepte un `SqlDataReader`. Cette méthode s'avère légèrement plus lente que la méthode directe décrite ci-avant mais offre une plus grande souplesse pour manipuler les données avant qu'elles ne soient transmises au client.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the resulting reader to the client  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendReaderToClient()  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("select @@version", connection);  
         SqlDataReader r = command.ExecuteReader();  
         SqlContext.Pipe.Send(r);  
      }  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendReaderToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class  
```  
  
 Pour créer un jeu de résultats dynamique, le remplir et le transmettre au client, vous pouvez créer des enregistrements de la connexion actuelle et les envoyer à l'aide de la méthode `SqlPipe.Send`.  
  
```csharp  
using System.Data;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
using System.Data.SqlTypes;  
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Create a result set on the fly and send it to the client.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendTransientResultSet()  
   {  
      // Create a record object that represents an individual row, including it's metadata.  
      SqlDataRecord record = new SqlDataRecord(new SqlMetaData("stringcol", SqlDbType.NVarChar, 128));  
  
      // Populate the record.  
      record.SetSqlString(0, "Hello World!");  
  
      // Send the record to the client.  
      SqlContext.Pipe.Send(record);  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendTransientResultSet()  
        ' Create a record object that represents an individual row, including it's metadata.  
        Dim record As New SqlDataRecord(New SqlMetaData("stringcol", SqlDbType.NVarChar, 128) )  
  
        ' Populate the record.  
        record.SetSqlString(0, "Hello World!")  
  
        ' Send the record to the client.  
        SqlContext.Pipe.Send(record)          
    End Sub  
End Class   
```  
  
 Voici un exemple d'envoi d'un résultat sous forme de tableau et d'un message via `SqlPipe`.  
  
```csharp  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void HelloWorld()  
   {  
      SqlContext.Pipe.Send("Hello world! It's now " + System.DateTime.Now.ToString()+"\n");  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT ProductNumber FROM ProductMaster", connection);  
         SqlDataReader reader = command.ExecuteReader();  
         SqlContext.Pipe.Send(reader);  
      }  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub HelloWorld()  
        SqlContext.Pipe.Send("Hello world! It's now " & System.DateTime.Now.ToString() & "\n")  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT ProductNumber FROM ProductMaster", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class   
```  
  
 La première méthode  `Send` envoie un message au client tandis que la deuxième transmet un résultat sous forme de tableau à l'aide de `SqlDataReader`.  
  
 Notez que ces exemples sont uniquement fournis à des fins d'illustration. Pour les applications qui exigent des calculs intensifs, les fonctions CLR conviennent mieux que de simples instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. Une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] quasi équivalente de l'exemple précédent est la suivante :  
  
```  
CREATE PROCEDURE HelloWorld() AS  
BEGIN  
PRINT('Hello world!')  
SELECT ProductNumber FROM ProductMaster  
END;  
```  
  
> [!NOTE]  
>  Les messages et les jeux de résultats sont extraits différemment dans l'application cliente. Par exemple, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] jeux de résultats apparaissent dans le **résultats** vue et les messages s’affichent dans le **Messages** volet.  
  
 Si le code Visual C# ci-avant est enregistré dans un fichier MyFirstUdp.cs et compilé avec :  
  
```  
csc /t:library /out:MyFirstUdp.dll MyFirstUdp.cs   
```  
  
 Ou si le code Visual Basic ci-dessus est enregistré dans un fichier MyFirstUdp.vb et compilé avec :  
  
```  
vbc /t:library /out:MyFirstUdp.dll MyFirstUdp.vb   
```  
  
> [!NOTE]  
>  Depuis [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], les objets de base de données Visual C++ (notamment les procédures stockées) compilés avec `/clr:pure` ne sont pas pris en charge pour l'exécution.  
  
 L'assembly obtenu peut être inscrit et le point d'entrée appelé avec le DDL suivant :  
  
```  
CREATE ASSEMBLY MyFirstUdp FROM 'C:\Programming\MyFirstUdp.dll';  
CREATE PROCEDURE HelloWorld  
AS EXTERNAL NAME MyFirstUdp.StoredProcedures.HelloWorld;  
EXEC HelloWorld;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions CLR définies par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Types CLR définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Déclencheurs CLR](../../../2014/database-engine/dev-guide/clr-triggers.md)  
  
  