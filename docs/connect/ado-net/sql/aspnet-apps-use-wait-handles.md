---
title: Applications ASP.NET utilisant les handles d’attente
description: Fournit un exemple montrant comment exécuter plusieurs commandes simultanées à partir d’une page ASP.NET, à l’aide de descripteurs d’attente pour gérer l’opération à l’achèvement de toutes les commandes.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: f588597a-49de-4206-8463-4ef377e112ff
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 42d5c395526ff79e24243392bb3dbfa302c8a9e7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78897071"
---
# <a name="aspnet-applications-using-wait-handles"></a>Applications ASP.NET utilisant les handles d’attente

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Les modèles de rappel et d’interrogation pour la gestion des opérations asynchrones sont utiles lorsque votre application ne traite qu’une seule opération asynchrone à la fois. Les modèles d’attente offrent un moyen plus flexible de traiter plusieurs opérations asynchrones. Il existe deux modèles d'attente nommés pour les méthodes <xref:System.Threading.WaitHandle> utilisées pour leur implémentation : le modèle d’attente (N’importe lequel) et le modèle d’attente (tous).  
  
Pour utiliser l’un ou l’autre modèle d’attente, vous devez utiliser la propriété <xref:System.IAsyncResult.AsyncWaitHandle%2A> de l’objet <xref:System.IAsyncResult> retourné par les méthodes <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> ou <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>. Les méthodes <xref:System.Threading.WaitHandle.WaitAny%2A> et <xref:System.Threading.WaitHandle.WaitAll%2A> vous obligent toutes les deux à envoyer les objets <xref:System.Threading.WaitHandle> comme un argument, rassemblés dans un tableau.  
  
Les deux méthodes d’attente analysent les opérations asynchrones, en attente de la fin de l’opération. La méthode <xref:System.Threading.WaitHandle.WaitAny%2A> attend que l’une des opérations s’achève ou expire. Une fois que vous savez qu’une opération particulière est achevée, vous pouvez traiter ses résultats puis continuer à attendre l’achèvement ou l’expiration de l’opération suivante. La méthode <xref:System.Threading.WaitHandle.WaitAll%2A> attend que tous les processus du tableau d’instances <xref:System.Threading.WaitHandle> soient achevés ou aient expiré avant de continuer.  
  
L’avantage des modèles d’attente est plus important lorsque vous devez exécuter plusieurs opérations de longue durée sur des serveurs différents ou lorsque votre serveur est suffisamment puissant pour traiter toutes les requêtes en même temps. Dans le cadre des exemples ici, trois requêtes émulent de longs processus en ajoutant des commandes WAITFOR de longueurs variées à des requêtes SELECT sans conséquence.  
  
## <a name="example-wait-any-model"></a>Exemple : Modèle d'attente (N’importe lequel)  
L’exemple suivant illustre le modèle d’attente (N’importe lequel). Après le démarrage de trois processus asynchrones, la méthode <xref:System.Threading.WaitHandle.WaitAny%2A> est appelée pour attendre l’achèvement de l’un d’eux. À mesure que chaque processus se termine, la méthode <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A> est appelée et l’objet <xref:Microsoft.Data.SqlClient.SqlDataReader> résultant est lu. À ce stade, une application réelle utiliserait probablement le <xref:Microsoft.Data.SqlClient.SqlDataReader> pour remplir une partie de la page. Dans cet exemple simple, l’heure de fin du processus est ajoutée à une zone de texte correspondant au processus. Prises ensemble, ces heures dans les zones de texte illustrent le point suivant : Le code est exécuté chaque fois qu'un processus s'achève.  
  
Pour configurer cet exemple, créez un nouveau projet de site Web ASP.NET. Placez un contrôle <xref:System.Web.UI.WebControls.Button> et quatre contrôles <xref:System.Web.UI.WebControls.TextBox> sur la page (en acceptant le nom par défaut pour chaque contrôle).  
  
Ajoutez le code suivant à la classe du formulaire, en modifiant la chaîne de connexion en fonction des besoins de votre environnement.  
  
```csharp  
// Add the following using statements, if they are not already there.  
using System;  
using System.Data;  
using System.Configuration;  
using System.Web;  
using System.Web.Security;  
using System.Web.UI;  
using System.Web.UI.WebControls;  
using System.Web.UI.WebControls.WebParts;  
using System.Web.UI.HtmlControls;  
using System.Threading;  
using Microsoft.Data.SqlClient;  
  
// Add this code to the page's class  
string GetConnectionString()  
     //  To avoid storing the connection string in your code,              
     //  you can retrieve it from a configuration file.   
     //  If you have not included "Asynchronous Processing=true"   
     //  in the connection string, the command will not be able  
     //  to execute asynchronously.  
{  
     return "Data Source=(local);Integrated Security=SSPI;" +  
          "Initial Catalog=AdventureWorks;" +  
          "Asynchronous Processing=true";  
}  
void Button1_Click(object sender, System.EventArgs e)  
{  
     //  In a real-world application, you might be connecting to   
     //   three different servers or databases. For the example,  
     //   we connect to only one.  
  
     SqlConnection connection1 =   
          new SqlConnection(GetConnectionString());  
     SqlConnection connection2 =   
          new SqlConnection(GetConnectionString());  
     SqlConnection connection3 =   
          new SqlConnection(GetConnectionString());  
     //  To keep the example simple, all three asynchronous   
     //  processes select a row from the same table. WAITFOR  
     //  commands are used to emulate long-running processes  
     //  that complete after different periods of time.  
  
     string commandText1 = "WAITFOR DELAY '0:0:01';" +   
          "SELECT * FROM Production.Product " +   
          "WHERE ProductNumber = 'BL-2036'";  
     string commandText2 = "WAITFOR DELAY '0:0:05';" +   
          "SELECT * FROM Production.Product " +   
          "WHERE ProductNumber = 'BL-2036'";  
     string commandText3 = "WAITFOR DELAY '0:0:10';" +   
          "SELECT * FROM Production.Product " +   
          "WHERE ProductNumber = 'BL-2036'";  
     try  
          //  For each process, open a connection and begin   
          //  execution. Use the IAsyncResult object returned by   
          //  BeginExecuteReader to add a WaitHandle for the   
          //  process to the array.  
     {  
          connection1.Open();  
          SqlCommand command1 =  
               new SqlCommand(commandText1, connection1);  
          IAsyncResult result1 = command1.BeginExecuteReader();  
          WaitHandle waitHandle1 = result1.AsyncWaitHandle;  
  
          connection2.Open();  
          SqlCommand command2 =  
               new SqlCommand(commandText2, connection2);  
          IAsyncResult result2 = command2.BeginExecuteReader();  
          WaitHandle waitHandle2 = result2.AsyncWaitHandle;  
  
          connection3.Open();  
          SqlCommand command3 =  
               new SqlCommand(commandText3, connection3);  
          IAsyncResult result3 = command3.BeginExecuteReader();  
          WaitHandle waitHandle3 = result3.AsyncWaitHandle;  
  
          WaitHandle[] waitHandles = {  
               waitHandle1, waitHandle2, waitHandle3  
          };  
  
          int index;  
          for (int countWaits = 0; countWaits <= 2; countWaits++)  
          {  
               //  WaitAny waits for any of the processes to   
               //  complete. The return value is either the index   
               //  of the array element whose process just   
               //  completed, or the WaitTimeout value.  
  
               index = WaitHandle.WaitAny(waitHandles,   
                    60000, false);  
               //  This example doesn't actually do anything with   
               //  the data returned by the processes, but the   
               //  code opens readers for each just to demonstrate       
               //  the concept.  
               //  Instead of using the returned data to fill the   
               //  controls on the page, the example adds the time  
               //  the process was completed to the corresponding  
               //  text box.  
  
               switch (index)  
               {  
                    case 0:  
                         SqlDataReader reader1;  
                         reader1 =   
                              command1.EndExecuteReader(result1);  
                         if (reader1.Read())  
                         {  
                           TextBox1.Text =   
                           "Completed " +  
                           System.DateTime.Now.ToLongTimeString();  
                         }  
                         reader1.Close();  
                         break;  
                    case 1:  
                         SqlDataReader reader2;  
                         reader2 =   
                              command2.EndExecuteReader(result2);  
                         if (reader2.Read())  
                         {  
                           TextBox2.Text =   
                           "Completed " +  
                           System.DateTime.Now.ToLongTimeString();  
                         }  
                         reader2.Close();  
                         break;  
                    case 2:  
                         SqlDataReader reader3;  
                         reader3 =   
                              command3.EndExecuteReader(result3);  
                         if (reader3.Read())  
                         {  
                           TextBox3.Text =   
                           "Completed " +  
                           System.DateTime.Now.ToLongTimeString();  
                         }  
                         reader3.Close();  
                         break;  
                    case WaitHandle.WaitTimeout:  
                         throw new Exception("Timeout");  
                         break;  
               }  
          }  
     }  
     catch (Exception ex)  
     {  
          TextBox4.Text = ex.ToString();  
     }  
     connection1.Close();  
     connection2.Close();  
     connection3.Close();  
}  
```  
  
## <a name="example-wait-all-model"></a>Exemple : Modèle d’attente (Tous)  
L’exemple suivant illustre le modèle d’attente (Tous). Après le démarrage de trois processus asynchrones, la méthode <xref:System.Threading.WaitHandle.WaitAll%2A> est appelée pour attendre l’achèvement ou l’expiration des processus.  
  
Comme dans cet exemple de modèle d’attente (N’importe lequel), l’heure de fin du processus est ajoutée à une zone de texte correspondant au processus. Là encore, ces heures dans les zones de texte illustrent le point suivant : D'après la méthode <xref:System.Threading.WaitHandle.WaitAny%2A>, le code est exécuté uniquement après l'achèvement de tous les processus.  
  
Pour configurer cet exemple, créez un nouveau projet de site Web ASP.NET. Placez un contrôle <xref:System.Web.UI.WebControls.Button> et quatre contrôles <xref:System.Web.UI.WebControls.TextBox> sur la page (en acceptant le nom par défaut pour chaque contrôle).  
  
Ajoutez le code suivant à la classe du formulaire, en modifiant la chaîne de connexion en fonction des besoins de votre environnement.  
  
```csharp  
// Add the following using statements, if they are not already there.  
using System;  
using System.Data;  
using System.Configuration;  
using System.Web;  
using System.Web.Security;  
using System.Web.UI;  
using System.Web.UI.WebControls;  
using System.Web.UI.WebControls.WebParts;  
using System.Web.UI.HtmlControls;  
using System.Threading;  
using Microsoft.Data.SqlClient;  
  
// Add this code to the page's class  
string GetConnectionString()  
    //  To avoid storing the connection string in your code,              
    //  you can retrieve it from a configuration file.   
    //  If you have not included "Asynchronous Processing=true"   
    //  in the connection string, the command will not be able  
    //  to execute asynchronously.  
{  
    return "Data Source=(local);Integrated Security=SSPI;" +  
        "Initial Catalog=AdventureWorks;" +  
        "Asynchronous Processing=true";  
}  
void Button1_Click(object sender, System.EventArgs e)  
{  
    //  In a real-world application, you might be connecting to   
    //   three different servers or databases. For the example,  
    //   we connect to only one.  
  
    SqlConnection connection1 =   
        new SqlConnection(GetConnectionString());  
    SqlConnection connection2 =   
        new SqlConnection(GetConnectionString());  
    SqlConnection connection3 =   
        new SqlConnection(GetConnectionString());  
    //  To keep the example simple, all three asynchronous   
    //  processes execute UPDATE queries that result in  
      //  no change to the data. WAITFOR  
    //  commands are used to emulate long-running processes  
    //  that complete after different periods of time.  
  
    string commandText1 =   
        "UPDATE Production.Product " +  
        "SET ReorderPoint = ReorderPoint + 1 " +  
        "WHERE ReorderPoint Is Not Null;" +  
        "WAITFOR DELAY '0:0:01';" +  
        "UPDATE Production.Product " +  
        "SET ReorderPoint = ReorderPoint - 1 " +  
        "WHERE ReorderPoint Is Not Null";  
  
    string commandText2 =   
      "UPDATE Production.Product " +  
      "SET ReorderPoint = ReorderPoint + 1 " +  
      "WHERE ReorderPoint Is Not Null;" +  
      "WAITFOR DELAY '0:0:05';" +  
      "UPDATE Production.Product " +  
      "SET ReorderPoint = ReorderPoint - 1 " +  
      "WHERE ReorderPoint Is Not Null";  
  
    string commandText3 =  
       "UPDATE Production.Product " +  
       "SET ReorderPoint = ReorderPoint + 1 " +  
       "WHERE ReorderPoint Is Not Null;" +  
       "WAITFOR DELAY '0:0:10';" +  
       "UPDATE Production.Product " +  
       "SET ReorderPoint = ReorderPoint - 1 " +  
       "WHERE ReorderPoint Is Not Null";  
    try  
        //  For each process, open a connection and begin   
        //  execution. Use the IAsyncResult object returned by   
        //  BeginExecuteReader to add a WaitHandle for the   
        //  process to the array.  
    {  
        connection1.Open();  
        SqlCommand command1 =  
            new SqlCommand(commandText1, connection1);  
        IAsyncResult result1 = command1.BeginExecuteNonQuery();  
        WaitHandle waitHandle1 = result1.AsyncWaitHandle;  
        connection2.Open();  
  
        SqlCommand command2 =  
            new SqlCommand(commandText2, connection2);  
        IAsyncResult result2 = command2.BeginExecuteNonQuery();  
        WaitHandle waitHandle2 = result2.AsyncWaitHandle;  
        connection3.Open();  
  
        SqlCommand command3 =  
            new SqlCommand(commandText3, connection3);  
        IAsyncResult result3 = command3.BeginExecuteNonQuery();  
        WaitHandle waitHandle3 = result3.AsyncWaitHandle;  
  
        WaitHandle[] waitHandles = {  
            waitHandle1, waitHandle2, waitHandle3  
        };  
  
        bool result;  
        //  WaitAll waits for all of the processes to   
        //  complete. The return value is True if the processes  
        //  all completed successfully, False if any process  
        //  timed out.  
  
        result = WaitHandle.WaitAll(waitHandles, 60000, false);  
        if(result)  
        {  
            long rowCount1 =   
                command1.EndExecuteNonQuery(result1);  
            TextBox1.Text = "Completed " +  
                System.DateTime.Now.ToLongTimeString();  
            long rowCount2 =   
                command2.EndExecuteNonQuery(result2);  
            TextBox2.Text = "Completed " +  
                System.DateTime.Now.ToLongTimeString();  
  
            long rowCount3 =   
                command3.EndExecuteNonQuery(result3);  
            TextBox3.Text = "Completed " +  
                System.DateTime.Now.ToLongTimeString();  
        }  
        else  
        {  
            throw new Exception("Timeout");  
        }  
    }  
  
    catch (Exception ex)  
    {  
        TextBox4.Text = ex.ToString();  
    }  
    connection1.Close();  
    connection2.Close();  
    connection3.Close();  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [Opérations asynchrones](asynchronous-operations.md)
