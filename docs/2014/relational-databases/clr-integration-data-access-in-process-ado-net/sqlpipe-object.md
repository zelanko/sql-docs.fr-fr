---
title: Objet SqlPipe | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bcf462f82d7455f83bb0bee8a3b0af991ec2e7db
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920053"
---
# <a name="sqlpipe-object"></a>Objet SqlPipe
  Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il est très fréquent d'écrire une procédure stockée (ou une procédure stockée étendue) qui envoie des résultats ou des paramètres de sortie au client appelant.  
  
 Dans une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)], toute instruction `SELECT` qui retourne zéro ou plusieurs lignes envoie les résultats au « canal » de l'appelant connecté.  
  
 Pour les objets de base de données du CLR (Common Language Runtime) qui s'exécutent dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez envoyer les résultats au canal connecté à l'aide des méthodes `Send` de l'objet `SqlPipe`. Accédez à la propriété `Pipe` de l'objet `SqlContext` pour obtenir l'objet `SqlPipe`. La classe `SqlPipe` est similaire sur le plan conceptuel à la classe `Response` présente dans ASP.NET. Pour plus d'informations, consultez la documentation de référence sur la classe SqlPipe dans le kit de développement logiciel (SDK) du .NET Framework.  
  
## <a name="returning-tabular-results-and-messages"></a>Retour de résultats sous forme de tableau et de messages  
 La classe `SqlPipe` possède une méthode `Send` avec trois surcharges. Celles-ci sont les suivantes :  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 La méthode `Send` envoie des données directement au client ou à l'appelant. C'est généralement le client qui utilise la sortie de la méthode `SqlPipe`, mais dans le cas de procédures stockées CLR imbriquées, le consommateur de sortie peut également être une procédure stockée. Par exemple, Procedure1 appelle SqlCommand.ExecuteReader() avec le texte de commande "EXEC Procedure2". Procedure2 est également une procédure stockée managée. Si Procedure2 appelle maintenant SqlPipe.Send( SqlDataRecord), la ligne est envoyée au lecteur de Procedure1, pas au client.  
  
 La méthode `Send` envoie un message de chaîne qui apparaît sur le client sous forme de message d'information, équivalent à PRINT dans [!INCLUDE[tsql](../../includes/tsql-md.md)]. Elle peut également envoyer un jeu de résultats à ligne unique à l'aide de `SqlDataRecord` ou un jeu de résultats à plusieurs ligne à l'aide d'un `SqlDataReader`.  
  
 L'objet `SqlPipe` possède également une méthode `ExecuteAndSend`. Cette méthode peut être utilisée pour exécuter une commande (passée en tant qu'objet `SqlCommand`) et renvoyer les résultats directement à l'appelant. Si la commande qui a été envoyée contient des erreurs, des exceptions sont envoyées au canal, mais une copie est également envoyée au code managé appelant. Si le code appelant n'intercepte pas l'exception, elle se propage vers le haut de la pile jusqu'au code [!INCLUDE[tsql](../../includes/tsql-md.md)] et apparaît deux fois dans la sortie. Si le code appelant intercepte l'exception, le consommateur du canal continue à voir l'erreur, mais il n'y a pas d'erreur de duplication.  
  
 Elle peut uniquement accepter un `SqlCommand` associé à la connexion contextuelle ; elle ne peut pas accepter de commande associée à la connexion non contextuelle.  
  
## <a name="returning-custom-result-sets"></a>Retour de jeux de résultats personnalisés  
 Les procédures stockées managées peuvent envoyer des jeux de résultats qui ne proviennent pas d'un `SqlDataReader`. La méthode `SendResultsStart`, ainsi que `SendResultsRow` et `SendResultsEnd`, permettent aux procédures stockées d'envoyer des jeux de résultats personnalisés au client.  
  
 `SendResultsStart` accepte un `SqlDataRecord` en tant qu'entrée. Elle  marque le début d'un jeu de résultats et utilise les métadonnées d'enregistrement pour construire les métadonnées qui décrivent le jeu de résultats. Elle n'envoie pas la valeur de l'enregistrement avec `SendResultsStart`. Toutes les lignes suivantes, envoyées à l'aide de `SendResultsRow`, doivent correspondre à cette définition des métadonnées.  
  
> [!NOTE]  
>  Après l'appel de la méthode `SendResultsStart`, seules `SendResultsRow` et `SendResultsEnd` peuvent être appelées. L'appel de toute autre méthode dans la même instance de `SqlPipe` entraîne `InvalidOperationException`. `SendResultsEnd` rétablit `SqlPipe` à son état initial, dans lequel d'autres méthodes peuvent être appelées.  
  
### <a name="example"></a>Exemple  
 La procédure stockée `uspGetProductLine` retourne les nom, numéro de produit, couleur et tarif de tous les produits dans une ligne de produit spécifiée. Cette procédure stockée accepte des correspondances exactes pour *prodLine*.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 L'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante exécute la procédure `uspGetProduct`, qui retourne une liste de vélos de randonnée.  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet SqlDataRecord](sqldatarecord-object.md)   
 [Procédures stockées CLR](../../database-engine/dev-guide/clr-stored-procedures.md)   
 [Extensions spécifiques in-process de SQL Server à ADO.NET](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
