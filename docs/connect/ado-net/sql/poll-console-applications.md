---
title: Interrogation dans les applications console
description: Fournit un exemple illustrant l’utilisation de l’interrogation pour attendre la fin de l’exécution d’une commande asynchrone à partir d’une application console. Cette technique est également valide dans une bibliothèque de classes ou une autre application sans interface utilisateur.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 4ff084d5-5956-4db1-8e18-c5a66b000882
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 89bcaa6d6e92ccde2d1c151b493c26fe1279d89f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896647"
---
# <a name="polling-in-console-applications"></a>Interrogation dans les applications console

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Les opérations asynchrones dans ADO.NET vous permettent de lancer des opérations de base de données qui prennent du temps sur un thread tout en effectuant d’autres tâches sur un autre thread. Dans la plupart des scénarios, toutefois, vous finira par atteindre un point où votre application ne doit pas continuer jusqu’à ce que l’opération de base de données soit terminée. Dans ce cas, il est utile d’interroger l’opération asynchrone pour déterminer si l’opération est terminée ou non.  
  
Vous pouvez utiliser la propriété <xref:System.IAsyncResult.IsCompleted%2A> pour déterminer si l’opération est terminée ou non.  
  
## <a name="example"></a>Exemple  
L’application console suivante met à jour des données dans l’exemple de base de données **AdventureWorks**, en opérant de façon asynchrone. Afin d’émuler un processus de longue durée, cet exemple insère une instruction WAITFOR dans le texte de la commande. Normalement, vous ne devez pas essayer de ralentir vos commandes, mais dans ce cas, cela simplifie l’illustration du comportement asynchrone.  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Class1  
{  
    [STAThread]  
    static void Main()  
    {  
        // The WAITFOR statement simply adds enough time to   
        // prove the asynchronous nature of the command.  
  
        string commandText =  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint + 1 " +  
          "WHERE ReorderPoint Is Not Null;" +  
          "WAITFOR DELAY '0:0:3';" +  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint - 1 " +  
          "WHERE ReorderPoint Is Not Null";  
  
        RunCommandAsynchronously(  
            commandText, GetConnectionString());  
  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  
    private static void RunCommandAsynchronously(  
      string commandText, string connectionString)  
    {  
        // Given command text and connection string, asynchronously  
        // execute the specified command against the connection.   
        // For this example, the code displays an indicator as it's   
        // working, verifying the asynchronous behavior.   
        using (SqlConnection connection =  
          new SqlConnection(connectionString))  
        {  
            try  
            {  
                int count = 0;  
                SqlCommand command =   
                    new SqlCommand(commandText, connection);  
                connection.Open();  
  
                IAsyncResult result =   
                    command.BeginExecuteNonQuery();  
                while (!result.IsCompleted)  
                {  
                    Console.WriteLine(  
                                    "Waiting ({0})", count++);  
                    // Wait for 1/10 second, so the counter  
                    // doesn't consume all available   
                    // resources on the main thread.  
                    System.Threading.Thread.Sleep(100);  
                }  
                Console.WriteLine(  
                    "Command complete. Affected {0} rows.",  
                command.EndExecuteNonQuery(result));  
            }  
            catch (SqlException ex)  
            {  
                Console.WriteLine("Error ({0}): {1}",   
                    ex.Number, ex.Message);  
            }  
            catch (InvalidOperationException ex)  
            {  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
            catch (Exception ex)  
            {  
                // You might want to pass these errors  
                // back out to the caller.  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
        }  
    }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
  
        // If you have not included "Asynchronous Processing=true"  
        // in the connection string, the command will not be able  
        // to execute asynchronously.  
        return "Data Source=(local);Integrated Security=SSPI;" +  
        "Initial Catalog=AdventureWorks; " +   
        "Asynchronous Processing=true";  
    }  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [Opérations asynchrones](asynchronous-operations.md)
