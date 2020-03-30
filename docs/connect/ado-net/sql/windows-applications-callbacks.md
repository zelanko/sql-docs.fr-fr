---
title: Applications Windows utilisant des rappels
description: Fournit un exemple montrant comment exécuter une commande asynchrone en toute sécurité, en gérant correctement l’interaction avec un formulaire et son contenu à partir d’un thread distinct.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ae2ea457-0764-4b06-8977-713c77e85bd2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e8c5fbecb8892639e5e4e0cb608c3c4de0447508
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896010"
---
# <a name="windows-applications-using-callbacks"></a>Applications Windows utilisant des rappels

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Dans la plupart des scénarios de traitement asynchrone, vous souhaitez démarrer une opération de base de données et continuer à exécuter d’autres processus sans attendre la fin de l’opération de base de données. Toutefois, de nombreux scénarios requièrent une action une fois l’opération de base de données terminée. Dans une application Windows, par exemple, vous pouvez souhaiter la délégation de l’opération de longue durée à un thread d’arrière-plan permet au thread d’interface utilisateur de rester réactif. Toutefois, lorsque l’opération de base de données est terminée, vous souhaitez utiliser les résultats pour remplir le formulaire. Ce type de scénario est le mieux implémenté avec un rappel.  
  
Vous définissez un rappel en spécifiant un délégué <xref:System.AsyncCallback> dans la méthode <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> ou <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>. Le délégué est appelé une fois l’opération terminée. Vous pouvez transmettre au délégué une référence à la <xref:Microsoft.Data.SqlClient.SqlCommand> elle-même, ce qui facilite l’accès à l’objet <xref:Microsoft.Data.SqlClient.SqlCommand> et l’appel de la méthode `End` appropriée sans avoir à utiliser une variable globale.  
  
## <a name="example"></a>Exemple  
L’application Windows suivante illustre l’utilisation de la méthode <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, en exécutant une instruction Transact-SQL qui comprend un délai de quelques secondes (en émulant une commande longue).  
  
Cet exemple illustre un certain nombre de techniques importantes, notamment l’appel d’une méthode qui interagit avec le formulaire à partir d’un thread distinct. En outre, cet exemple montre comment vous devez empêcher les utilisateurs d’exécuter simultanément une commande plusieurs fois et comment vous devez vous assurer que le formulaire ne se ferme pas avant l’appel de la procédure de rappel.  
  
Pour configurer cet exemple, créez une nouvelle application Windows. Placez un contrôle <xref:System.Windows.Forms.Button> et deux contrôles <xref:System.Windows.Forms.Label> sur le formulaire (en acceptant le nom par défaut pour chaque contrôle). Ajoutez le code suivant à la classe du formulaire, en modifiant la chaîne de connexion en fonction des besoins de votre environnement.  
  
```csharp  
// Add these to the top of the class, if they're not already there:  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
// Hook up the form's Load event handler (you can double-click on   
// the form's design surface in Visual Studio), and then add   
// this code to the form's class:  
  
// You'll need this delegate in order to display text from a thread  
// other than the form's thread. See the HandleCallback  
// procedure for more information.  
// This same delegate matches both the DisplayStatus   
// and DisplayResults methods.  
private delegate void DisplayInfoDelegate(string Text);  
  
// This flag ensures that the user doesn't attempt  
// to restart the command or close the form while the   
// asynchronous command is executing.  
private bool isExecuting;  
  
// This example maintains the connection object   
// externally, so that it's available for closing.  
private SqlConnection connection;  
  
private static string GetConnectionString()  
{  
    // To avoid storing the connection string in your code,              
    // you can retrieve it from a configuration file.   
  
    // If you have not included "Asynchronous Processing=true" in the  
    // connection string, the command will not be able  
    // to execute asynchronously.  
    return "Data Source=(local);Integrated Security=SSPI;" +  
    "Initial Catalog=AdventureWorks; Asynchronous Processing=true";  
}  
  
private void DisplayStatus(string Text)  
{  
    this.label1.Text = Text;  
}  
  
private void DisplayResults(string Text)  
{  
    this.label1.Text = Text;  
    DisplayStatus("Ready");  
}  
  
private void Form1_FormClosing(object sender, System.Windows.Forms.FormClosingEventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Can't close the form until " +  
        "the pending asynchronous command has completed. Please " +  
        "wait...");
        e.Cancel = true;  
    }  
}  
  
private void button1_Click(object sender, System.EventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Already executing. Please wait until " +  
        "the current query has completed.");  
    }  
    else  
    {  
        SqlCommand command = null;  
        try  
        {  
            DisplayResults("");  
            DisplayStatus("Connecting...");  
            connection = new SqlConnection(GetConnectionString());  
            // To emulate a long-running query, wait for   
            // a few seconds before working with the data.  
            // This command doesn't do much, but that's the point--  
            // it doesn't change your data, in the long run.  
            string commandText =  
                "WAITFOR DELAY '0:0:05';" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint + 1 " +  
                "WHERE ReorderPoint Is Not Null;" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint - 1 " +  
                "WHERE ReorderPoint Is Not Null";  
  
            command = new SqlCommand(commandText, connection);  
            connection.Open();  
  
            DisplayStatus("Executing...");  
            isExecuting = true;  
            // Although it's not required that you pass the   
            // SqlCommand object as the second parameter in the   
            // BeginExecuteNonQuery call, doing so makes it easier  
            // to call EndExecuteNonQuery in the callback procedure.  
            AsyncCallback callback = new AsyncCallback(HandleCallback);  
  
            // Once the BeginExecuteNonQuery method is called,  
            // the code continues--and the user can interact with  
            // the form--while the server executes the query.  
            command.BeginExecuteNonQuery(callback, command);  
  
        }  
        catch (Exception ex)  
        {  
            isExecuting = false;  
            DisplayStatus($"Ready (last error: {ex.Message})");
            if (connection != null)  
            {  
                connection.Close();  
            }  
        }  
    }  
}  
  
private void HandleCallback(IAsyncResult result)  
{  
    try  
    {  
        // Retrieve the original command object, passed  
        // to this procedure in the AsyncState property  
        // of the IAsyncResult parameter.  
        SqlCommand command = (SqlCommand)result.AsyncState;  
        int rowCount = command.EndExecuteNonQuery(result);  
        string rowText = " rows affected.";  
        if (rowCount == 1)  
        {  
            rowText = " row affected.";  
        }  
        rowText = rowCount + rowText;  
  
        // You may not interact with the form and its contents  
        // from a different thread, and this callback procedure  
        // is all but guaranteed to be running from a different thread  
        // than the form. Therefore you cannot simply call code that   
        // displays the results, like this:  
        // DisplayResults(rowText)  
  
        // Instead, you must call the procedure from the form's thread.  
        // One simple way to accomplish this is to call the Invoke  
        // method of the form, which calls the delegate you supply  
        // from the form's thread.   
        DisplayInfoDelegate del =   
         new DisplayInfoDelegate(DisplayResults);  
        this.Invoke(del, rowText);  
    }  
    catch (Exception ex)  
    {  
        // Because you're now running code in a separate thread,   
        // if you don't handle the exception here, none of your other  
        // code will catch the exception. Because none of your  
        // code is on the call stack in this thread, there's nothing  
        // higher up the stack to catch the exception if you don't   
        // handle it here. You can either log the exception or   
        // invoke a delegate (as in the non-error case in this   
        // example) to display the error on the form. In no case  
        // can you simply display the error without executing a   
        // delegate as in the try block here.   
  
        // You can create the delegate instance as you   
        // invoke it, like this:  
        this.Invoke(new DisplayInfoDelegate(DisplayStatus),  
            $"Ready (last error: {ex.Message}");
    }  
    finally  
    {  
        isExecuting = false;  
        if (connection != null)  
        {  
            connection.Close();  
        }  
    }  
}  
  
private void Form1_Load(object sender, System.EventArgs e)  
{  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    this.FormClosing += new System.Windows.Forms.  
        FormClosingEventHandler(this.Form1_FormClosing);  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [Opérations asynchrones](asynchronous-operations.md)
