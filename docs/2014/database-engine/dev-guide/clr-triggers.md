---
title: Déclencheurs CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- inserted tables
- database objects [CLR integration], triggers
- common language runtime [SQL Server], triggers
- updated columns
- building database objects [CLR integration], triggers
- triggers [CLR integration]
- deleted tables
- EventData property
- SqlTriggerContext class
- transactions [CLR integration]
ms.assetid: 302a4e4a-3172-42b6-9cc0-4a971ab49c1c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 87d822e97a75bbd08375980fe6a6f0341d8f9c60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62755254"
---
# <a name="clr-triggers"></a>Déclencheurs CLR
  En raison de l'intégration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au CLR (Common Language Runtime) [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], vous pouvez utiliser n'importe quel langage [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour créer des déclencheurs CLR. Cette section couvre des informations spécifiques aux déclencheurs implémentés avec l'intégration du CLR. Pour une description complète des déclencheurs, consultez [déclencheurs DDL](../../relational-databases/triggers/ddl-triggers.md).  
  
## <a name="what-are-triggers"></a>Que sont les déclencheurs ?  
 Un déclencheur est un type spécial de procédure stockée qui s'exécute automatiquement lorsqu'un événement de langage s'exécute. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intègre deux types généraux de déclencheurs : les déclencheurs du langage de manipulation de données (DML) et les déclencheurs du langage de définition de données (DDL). Les déclencheurs DML peuvent être utilisés lorsque des instructions `INSERT`, `UPDATE` ou `DELETE` modifient des données dans une table ou une vue spécifiée. Les déclencheurs DDL activent des procédures stockées en réponse à diverses instructions DDL, qui sont essentiellement des instructions qui commencent par `CREATE`, `ALTER` et `DROP`. Les déclencheurs DDL peuvent être utilisés dans des tâches d'administration telles que l'audit et la régulation d'opérations de base de données.  
  
## <a name="unique-capabilities-of-clr-triggers"></a>Fonctionnalités uniques des déclencheurs CLR  
 Les déclencheurs écrits en [!INCLUDE[tsql](../../includes/tsql-md.md)] peuvent déterminer les colonnes de la vue ou de la table d'activation qui ont été mises à jour à l'aide des fonctions `UPDATE(column)` et `COLUMNS_UPDATED()`.  
  
 Les déclencheurs écrits dans un langage CLR diffèrent des autres objets d'intégration du CLR par bien des aspects. Les déclencheurs CLR peuvent effectuer les tâches suivantes :  
  
-   référencer des données dans les tables `INSERTED` et `DELETED` ;  
  
-   déterminer les colonnes qui ont été modifiées suite à une opération `UPDATE` ;  
  
-   accéder aux informations sur les objets de base de données affectés par l'exécution d'instructions DDL.  
  
 Ces fonctionnalités sont fournies intrinsèquement dans le langage de requête, ou par la classe `SqlTriggerContext`. Pour plus d’informations sur les avantages de l’intégration du CLR et le [!INCLUDE[tsql](../../includes/tsql-md.md)]choix entre le code managé et, consultez [vue d’ensemble de l’intégration du CLR](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="using-the-sqltriggercontext-class"></a>Utilisation de la classe SqlTriggerContext  
 La classe `SqlTriggerContext` ne peut pas être construite publiquement et peut uniquement être obtenue en accédant à la propriété `SqlContext.TriggerContext` dans le corps d'un déclencheur CLR. La classe `SqlTriggerContext` peut être obtenue à partir du `SqlContext` actif en appelant la propriété `SqlContext.TriggerContext` :  
  
 `SqlTriggerContext myTriggerContext = SqlContext.TriggerContext;`  
  
 La classe `SqlTriggerContext` fournit des informations de contexte sur le déclencheur. Ces informations contextuelles comprennent le type d'action ayant provoqué l'activation du déclencheur, les colonnes qui ont été modifiées dans une opération UPDATE et, dans le cas d'un déclencheur DDL, une structure `EventData` XML qui décrit l'opération de déclenchement. Pour plus d’informations, consultez [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql).  
  
### <a name="determining-the-trigger-action"></a>Détermination de l'action du déclencheur  
 Une fois que vous avez obtenu un `SqlTriggerContext`, vous pouvez l'utiliser pour déterminer le type d'action ayant provoqué l'activation du déclencheur. Ces informations sont disponibles par l'intermédiaire de la propriété `TriggerAction` de la classe `SqlTriggerContext`.  
  
 Pour les déclencheurs DML, la propriété `TriggerAction` peut prendre l'une des valeurs suivantes :  
  
-   TriggerAction.Update (0x1)  
  
-   TriggerAction.Insert (0x2)  
  
-   TriggerAction.Delete (0x3)  
  
-   Pour les déclencheurs DDL, la liste de valeurs TriggerAction possibles est considérablement plus longue. Pour plus d'informations, consultez la rubrique relative à l'énumération TriggerAction dans le Kit de développement logiciel (SDK) .NET Framework.  
  
### <a name="using-the-inserted-and-deleted-tables"></a>Utilisation des tables inserted et Deleted  
 Deux tables spéciales sont utilisées dans les instructions de déclencheur DML : la table **inserted** et la table **Deleted** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée et gère automatiquement ces tables. Vous pouvez utiliser ces tables temporaires pour tester les effets de certaines modifications de données et définir des conditions pour les actions de déclencheur DML. Toutefois, vous ne pouvez pas modifier directement les données dans les tables.  
  
 Les déclencheurs CLR peuvent accéder aux tables **inserted** et **Deleted** via le fournisseur in-process du CLR. Pour cela, un objet `SqlCommand` est obtenu de l'objet SqlContext. Par exemple :  
  
 C#  
  
```  
SqlConnection connection = new SqlConnection ("context connection = true");  
connection.Open();  
SqlCommand command = connection.CreateCommand();  
command.CommandText = "SELECT * from " + "inserted";  
```  
  
 Visual Basic  
  
```  
Dim connection As New SqlConnection("context connection=true")  
Dim command As SqlCommand  
connection.Open()  
command = connection.CreateCommand()  
command.CommandText = "SELECT * FROM " + "inserted"  
```  
  
### <a name="determining-updated-columns"></a>Détermination des colonnes mises à jour  
 Vous pouvez déterminer le nombre de colonnes modifiées par une opération UPDATE en utilisant la propriété `ColumnCount` de l'objet `SqlTriggerContext`. Vous pouvez utiliser la méthode `IsUpdatedColumn`, qui prend l'ordinal de colonne comme paramètre d'entrée, pour déterminer si la colonne a été mise à jour. Une valeur `True` indique que la colonne a été mise à jour.  
  
 Par exemple, cet extrait de code (provenant du déclencheur EmailAudit traité plus loin dans cette rubrique) répertorie toutes les colonnes mises à jour :  
  
 C#  
  
```  
reader = command.ExecuteReader();  
reader.Read();  
for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
{  
   pipe.Send("Updated column "  
      + reader.GetName(columnNumber) + "? "  
   + triggContext.IsUpdatedColumn(columnNumber).ToString());  
 }  
  
 reader.Close();  
```  
  
 Visual Basic  
  
```  
reader = command.ExecuteReader()  
reader.Read()  
Dim columnNumber As Integer  
  
For columnNumber=0 To triggContext.ColumnCount-1  
  
   pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
   "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
Next  
  
reader.Close()  
```  
  
### <a name="accessing-eventdata-for-clr-ddl-triggers"></a>Accès à EventData pour les déclencheurs DDL CLR  
 Comme les autres déclencheurs, les déclencheurs DDL activent des procédures stockées en réponse à un événement. Toutefois, à la différence des déclencheurs DML, ils ne sont pas activés en réponse à des instructions UPDATE, INSERT ou DELETE sur une table ou une vue. Au lieu de cela, ils sont activés en réponse à diverses instructions DDL, qui sont essentiellement des instructions qui commencent par CREATE, ALTER et DROP. Les déclencheurs DDL peuvent être utilisés dans des tâches d'administration telles que l'audit et l'analyse des opérations de base de données et des modifications de schéma.  
  
 Les informations sur un événement qui activent un déclencheur DDL sont disponibles dans la propriété `EventData` de la classe `SqlTriggerContext`. Cette propriété contient une valeur `xml`. Le schéma xml comprend des informations sur :  
  
-   l'heure de l'événement ;  
  
-   l'ID du processus système (SPID) de la connexion au cours de laquelle le déclencheur s'est exécuté ;  
  
-   le type d'événement qui a lancé le déclencheur.  
  
 Ensuite, selon le type d'événement, le schéma inclut des informations supplémentaires, telles que la base de données dans laquelle s'est produit l'événement, l'objet sur lequel il s'est produit et la commande [!INCLUDE[tsql](../../includes/tsql-md.md)] de l'événement.  
  
 Dans l'exemple suivant, le déclencheur DDL suivant retourne la propriété `EventData` brute.  
  
> [!NOTE]  
>  L'envoi de résultats et de messages par le biais de l'objet `SqlPipe` est montré ici à titre indicatif uniquement. Cette opération est généralement déconseillée pour le code de production lors de la programmation de déclencheurs CLR. Les données supplémentaires retournées peuvent être inattendues et générer des erreurs d'application.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   public static void DropTableTrigger()  
   {  
       SqlTriggerContext triggContext = SqlContext.TriggerContext;             
  
       switch(triggContext.TriggerAction)  
       {  
           case TriggerAction.DropTable:  
           SqlContext.Pipe.Send("Table dropped! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
  
           default:  
           SqlContext.Pipe.Send("Something happened! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
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
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    Public Shared Sub DropTableTrigger()  
        Dim triggContext As SqlTriggerContext  
        triggContext = SqlContext.TriggerContext  
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.DropTable  
              SqlContext.Pipe.Send("Table dropped! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
           Case Else  
              SqlContext.Pipe.Send("Something else happened! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
        End Select  
    End Sub  
End Class     
```  
  
 L'exemple de sortie suivant est la valeur de la propriété `EventData` après l'activation d'un déclencheur DDL par un événement `CREATE TABLE` :  
  
 `<EVENT_INSTANCE><PostTime>2004-04-16T21:17:16.160</PostTime><SPID>58</SPID><EventType>CREATE_TABLE</EventType><ServerName>MACHINENAME</ServerName><LoginName>MYDOMAIN\myname</LoginName><UserName>MYDOMAIN\myname</UserName><DatabaseName>AdventureWorks</DatabaseName><SchemaName>dbo</SchemaName><ObjectName>UserName</ObjectName><ObjectType>TABLE</ObjectType><TSQLCommand><SetOptions ANSI_NULLS="ON" ANSI_NULL_DEFAULT="ON" ANSI_PADDING="ON" QUOTED_IDENTIFIER="ON" ENCRYPTED="FALSE" /><CommandText>create table dbo.UserName  
(  
 UserName varchar(50),  
 RealName varchar(50)  
)  
</CommandText></TSQLCommand></EVENT_INSTANCE>`  
  
 En plus des informations accessibles par le biais de la classe `SqlTriggerContext`, les requêtes peuvent toujours faire référence à `COLUMNS_UPDATED` et aux tables inserted/deleted dans le texte d'une commande exécutée in-process.  
  
## <a name="sample-clr-trigger"></a>Exemple de déclencheur CLR  
 Dans cet exemple, imaginez le scénario suivant : vous laissez l'utilisateur entrer l'ID de son choix, mais vous souhaitez connaître les utilisateurs qui ont spécifiquement entré une adresse de messagerie en tant qu'ID. Le déclencheur suivant détecterait cette information et l'enregistrerait dans une table d'audit.  
  
> [!NOTE]  
>  L'envoi de résultats et ds messages par le biais de l'objet `SqlPipe` est montré ici à titre indicatif uniquement. Cette opération est généralement déconseillée pour le code de production. Certaines données supplémentaires retournées peuvent être inattendues et générer des erreurs d'application.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   [SqlTrigger(Name = @"EmailAudit", Target = "[dbo].[Users]", Event = "FOR INSERT, UPDATE, DELETE")]  
   public static void EmailAudit()  
   {  
      string userName;  
      string realName;  
      SqlCommand command;  
      SqlTriggerContext triggContext = SqlContext.TriggerContext;  
      SqlPipe pipe = SqlContext.Pipe;  
      SqlDataReader reader;  
  
      switch (triggContext.TriggerAction)  
      {  
         case TriggerAction.Insert:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
            reader.Close();  
  
            if (IsValidEMailAddress(userName))  
            {  
               command = new SqlCommand(  
                  @"INSERT [dbo].[UserNameAudit] VALUES ('"  
                  + userName + @"', '" + realName + @"');",  
                  connection);  
               pipe.Send(command.CommandText);  
               command.ExecuteNonQuery();  
               pipe.Send("You inserted: " + userName);  
            }  
         }  
  
         break;  
  
         case TriggerAction.Update:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
  
            pipe.Send(@"You updated: '" + userName + @"' - '"  
               + realName + @"'");  
  
            for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
            {  
               pipe.Send("Updated column "  
                  + reader.GetName(columnNumber) + "? "  
                  + triggContext.IsUpdatedColumn(columnNumber).ToString());  
            }  
  
            reader.Close();  
         }  
  
         break;  
  
         case TriggerAction.Delete:  
            using (SqlConnection connection  
               = new SqlConnection(@"context connection=true"))  
               {  
                  connection.Open();  
                  command = new SqlCommand(@"SELECT * FROM DELETED;",  
                     connection);  
                  reader = command.ExecuteReader();  
  
                  if (reader.HasRows)  
                  {  
                     pipe.Send(@"You deleted the following rows:");  
                     while (reader.Read())  
                     {  
                        pipe.Send(@"'" + reader.GetString(0)  
                        + @"', '" + reader.GetString(1) + @"'");  
                     }  
  
                     reader.Close();  
  
                     //alternately, to just send a tabular resultset back:  
                     //pipe.ExecuteAndSend(command);  
                  }  
                  else  
                  {  
                     pipe.Send("No rows affected.");  
                  }  
               }  
  
               break;  
            }  
        }  
  
     public static bool IsValidEMailAddress(string email)  
     {  
         return Regex.IsMatch(email, @"^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$");  
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
Imports System.Text.RegularExpressions  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    <SqlTrigger(Name:="EmailAudit", Target:="[dbo].[Users]", Event:="FOR INSERT, UPDATE, DELETE")> _  
    Public Shared Sub EmailAudit()  
        Dim userName As String  
        Dim realName As String  
        Dim command As SqlCommand  
        Dim triggContext As SqlTriggerContext  
        Dim pipe As SqlPipe  
        Dim reader As SqlDataReader    
  
        triggContext = SqlContext.TriggerContext      
        pipe = SqlContext.Pipe    
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.Insert  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 reader.Close()  
  
                 If IsValidEmailAddress(userName) Then  
                     command = New SqlCommand("INSERT [dbo].[UserNameAudit] VALUES ('" & _  
                       userName & "', '" & realName & "');", connection)  
  
                    pipe.Send(command.CommandText)  
                    command.ExecuteNonQuery()  
                    pipe.Send("You inserted: " & userName)  
  
                 End If  
              End Using  
  
           Case TriggerAction.Update  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 pipe.Send("You updated: " & userName & " - " & realName)  
  
                 Dim columnNumber As Integer  
  
                 For columnNumber=0 To triggContext.ColumnCount-1  
  
                    pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
                      "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
                 Next  
  
                 reader.Close()  
              End Using  
  
           Case TriggerAction.Delete  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM DELETED;", connection)  
  
                 reader = command.ExecuteReader()  
  
                 If reader.HasRows Then  
                    pipe.Send("You deleted the following rows:")  
  
                    While reader.Read()  
  
                       pipe.Send( reader.GetString(0) & ", " & reader.GetString(1) )  
  
                    End While   
  
                    reader.Close()  
  
                    ' Alternately, just send a tabular resultset back:  
                    ' pipe.ExecuteAndSend(command)  
  
                 Else  
                   pipe.Send("No rows affected.")  
                 End If  
  
              End Using   
        End Select  
    End Sub  
  
    Public Shared Function IsValidEMailAddress(emailAddress As String) As Boolean  
  
       return Regex.IsMatch(emailAddress, "^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$")  
    End Function      
End Class  
```  
  
 Supposons que deux tables existent avec les définitions suivantes :  
  
```  
CREATE TABLE Users  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
);  
GO CREATE TABLE UserNameAudit  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
)  
```  
  
 L' [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction qui crée le déclencheur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans est la suivante et suppose que l’assembly **SQLCLRTest** est déjà inscrit dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la base de données active.  
  
```  
CREATE TRIGGER EmailAudit  
ON Users  
FOR INSERT, UPDATE, DELETE  
AS  
EXTERNAL NAME SQLCLRTest.CLRTriggers.EmailAudit  
```  
  
## <a name="validating-and-canceling-invalid-transactions"></a>Validation et annulation de transactions non valides  
 Il est courant d'utiliser des déclencheurs pour valider et annuler des transactions INSERT, UPDATE ou DELETE non valides, ou pour empêcher les modifications à votre schéma de base de données. Pour ce faire, vous pouvez incorporer une logique de validation dans votre déclencheur, puis restaurer la transaction actuelle si l'action ne répond pas aux critères de validation.  
  
 Lorsque la méthode `Transaction.Rollback` ou une commande SqlCommand avec le texte de commande « TRANSACTION ROLLBACK » est appelée dans un déclencheur, elle lève une exception avec un message d'erreur ambigu et doit être encapsulée dans un bloc try/catch. Le message d'erreur qui s'affiche est semblable au suivant :  
  
```  
Msg 6549, Level 16, State 1, Procedure trig_InsertValidator, Line 0  
A .NET Framework error occurred during execution of user defined routine or aggregate 'trig_InsertValidator':   
System.Data.SqlClient.SqlException: Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting... User transaction, if any, will be rolled back.  
```  
  
 Cette exception est attendue et le bloc try/catch est nécessaire pour que l'exécution du code continue. Lorsque l'exécution du code du déclencheur se termine, une autre exception est levée.  
  
```  
Msg 3991, Level 16, State 1, Procedure trig_InsertValidator, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate "trig_InsertValidator" has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting.  
The statement has been terminated.  
```  
  
 Cette exception est également attendue, et un bloc try/catch autour de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui effectue l'action qui active le déclencheur est nécessaire pour que l'exécution puisse continuer. Malgré les deux exceptions levées, la transaction est restaurée et les modifications ne sont pas validées dans la table. Une différence majeure entre les déclencheurs CLR et les déclencheurs [!INCLUDE[tsql](../../includes/tsql-md.md)] vient du fait que les déclencheurs [!INCLUDE[tsql](../../includes/tsql-md.md)] peuvent continuer à effectuer des tâches une fois la transaction restaurée.  
  
### <a name="example"></a>Exemple  
 Le déclencheur suivant effectue une validation simple d'instructions INSERT sur une table. Si la valeur entière insérée est égale à un, la transaction est restaurée et la valeur n'est pas insérée dans la table. Toutes les autres valeurs entières sont insérées dans la table. Notez le bloc try/catch autour de la méthode `Transaction.Rollback`. Le script [!INCLUDE[tsql](../../includes/tsql-md.md)] crée une table, un assembly et une procédure stockée managée de test. Notez que les deux instructions INSERT sont encapsulées dans un bloc try/catch pour que l'exception levée au terme de l'exécution du déclencheur soit interceptée.  
  
 C#  
  
```  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class Triggers  
{  
    // Enter existing table or view for the target and uncomment the attribute line  
    // [Microsoft.SqlServer.Server.SqlTrigger (Name="trig_InsertValidator", Target="Table1", Event="FOR INSERT")]  
    public static void trig_InsertValidator()  
    {  
        using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
        {  
            SqlCommand command;  
            SqlDataReader reader;  
            int value;  
  
            // Open the connection.  
            connection.Open();  
  
            // Get the inserted value.  
            command = new SqlCommand(@"SELECT * FROM INSERTED", connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            value = (int)reader[0];  
            reader.Close();  
  
            // Rollback the transaction if a value of 1 was inserted.  
            if (1 == value)  
            {  
                try  
                {  
                    // Get the current transaction and roll it back.  
                    Transaction trans = Transaction.Current;  
                    trans.Rollback();                      
                }  
                catch (SqlException ex)  
                {  
                    // Catch the expected exception.                      
                }  
            }  
            else  
            {  
                // Perform other actions here.  
            }  
  
            // Close the connection.  
            connection.Close();              
        }  
    }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class Triggers  
' Enter existing table or view for the target and uncomment the attribute line  
' <Microsoft.SqlServer.Server.SqlTrigger(Name:="trig_InsertValidator", Target:="Table1", Event:="FOR INSERT")> _  
Public Shared Sub  trig_InsertValidator ()  
    Using connection As New SqlConnection("context connection=true")  
  
        Dim command As SqlCommand  
        Dim reader As SqlDataReader  
        Dim value As Integer  
  
        ' Open the connection.  
        connection.Open()  
  
        ' Get the inserted value.  
        command = New SqlCommand("SELECT * FROM INSERTED", connection)  
        reader = command.ExecuteReader()  
        reader.Read()  
        value = CType(reader(0), Integer)  
        reader.Close()  
  
        ' Rollback the transaction if a value of 1 was inserted.  
        If value = 1 Then  
  
            Try  
                ' Get the current transaction and roll it back.  
                Dim trans As Transaction  
                trans = Transaction.Current  
                trans.Rollback()  
  
            Catch ex As SqlException  
  
                ' Catch the exception.                      
            End Try  
        Else  
  
            ' Perform other actions here.  
        End If  
  
        ' Close the connection.  
        connection.Close()  
    End Using  
End Sub  
End Class  
```  
  
 Transact-SQL  
  
```  
-- Create the test table, assembly, and trigger.  
CREATE TABLE Table1(c1 int);  
go  
  
CREATE ASSEMBLY ValidationTriggers from 'E:\programming\ ValidationTriggers.dll';  
go  
  
CREATE TRIGGER trig_InsertValidator  
ON Table1  
FOR INSERT  
AS EXTERNAL NAME ValidationTriggers.Triggers.trig_InsertValidator;  
go  
  
-- Use a Try/Catch block to catch the expected exception  
BEGIN TRY  
   INSERT INTO Table1 VALUES(42)  
   INSERT INTO Table1 VALUES(1)  
END TRY  
BEGIN CATCH  
  SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
END CATCH;  
  
-- Clean up.  
DROP TRIGGER trig_InsertValidator;  
DROP ASSEMBLY ValidationTriggers;  
DROP TABLE Table1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)   
 [Déclencheurs DML](../../relational-databases/triggers/dml-triggers.md)   
 [Déclencheurs DDL](../../relational-databases/triggers/ddl-triggers.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql)   
 [Génération d’objets de base de données avec Common Language Runtime &#40;l’intégration du CLR&#41;](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
