---
title: 'Étape 4 : Connexion résiliente à SQL avec ADO.NET'
description: Découvrez comment utiliser une logique de nouvelles tentatives pour améliorer la résilience des connexions à une base de données SQL avec ADO.NET.
ms.custom: ''
ms.date: 08/15/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: a70b5449d1af02c3b367a204e2e32dfb32281d72
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86391764"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Étape 4 : Connexion résiliente à SQL avec ADO.NET

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

- Article précédent :&nbsp;&nbsp;&nbsp;[Étape 3 : Preuve de concept pour se connecter à SQL à l’aide d’ADO.NET](step-3-connect-sql-ado-net.md)  

  
Cette rubrique fournit un exemple de code C# illustrant une logique de nouvelle tentative personnalisée. La logique de nouvelle tentative assure la fiabilité. La logique de nouvelle tentative est conçue pour traiter de manière appropriée les erreurs temporaires ou des *défaillances transitoires* qui tendent à disparaître si le programme attend quelques secondes et effectue de nouvelles tentatives.  
  
Les sources des défaillances transitoires incluent :  
  
- Une brève défaillance de la mise en réseau qui prend en charge Internet.  
- Un système cloud peut être chargé d’équilibrer la charge de ses ressources au moment où votre requête a été envoyée.  
  
  
Les classes ADO.NET pour la connexion à votre serveur Microsoft SQL Server local peuvent également se connecter à Azure SQL Database. Toutefois, par elles-mêmes, les classes ADO.NET classes ne peuvent pas fournir toute la robustesse et la fiabilité nécessaires à la production. Votre programme client peut rencontrer des erreurs temporaires qu’il doit normalement résoudre de manière silencieuse et appropriée.  
  
## <a name="step-1-identify-transient-errors"></a>Étape 1 : Identification des erreurs temporaires  
  
Votre programme doit faire la distinction entre les erreurs temporaires et les erreurs persistantes. Les erreurs temporaires sont des conditions d’erreur qui peuvent être effacées dans un laps de temps réduit, par exemple des problèmes réseau temporaires.  Par exemple, une erreur persistante est si votre programme a une faute de frappe dans le nom de la base de données cible, dans ce cas, l’erreur « base de données introuvable » est conservée et ne risque pas d’être vidée dans un laps de temps réduit.  
  
La liste des erreurs classées comme erreurs temporaires est disponible sur [Messages d’erreur pour les applications client SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/)  
  
## <a name="step-2-create-and-run-sample-application"></a>Étape 2 : Créer et exécuter un exemple d’application  
  
L’exemple part du principe que .NET Framework 4.5.1 (ou une version ultérieure) est installé.  L’exemple de code C# se compose d’un fichier nommé Program.cs. Le code correspondant est fourni dans la section suivante.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Étape 2.a : Capturer et compiler l’exemple de code  
  
Vous pouvez compiler l'exemple en effectuant les étapes suivantes :  
  
1. Dans l’ [édition Visual Studio Community gratuite](https://www.visualstudio.com/products/visual-studio-community-vs), créez un projet à partir du modèle Application console C#.  
    - Fichier > Nouveau > Projet > Installé > Modèles > Visual C# > Windows > Bureau classique > Application console  
    - Nommez le projet **RetryAdo2**.  
2. Ouvrez le volet Explorateur de solutions.  
    - Vérifiez que le nom de votre projet est présent.  
    - Vérifiez que le nom du fichier Program.cs est présent.  
3. Ouvrez le fichier Program.cs.  
4. Remplacez entièrement le contenu du fichier Program.cs par le code du bloc de code suivant.  
5. Cliquez sur le menu Générer > Générer la solution.  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Étape 2.b : Copiez et collez l’exemple de code  
  
Collez ce code dans le fichier **Program.cs** .  
  
Vous devez ensuite modifier les chaînes de nom de serveur, de mot de passe, et ainsi de suite. Ces chaînes figurent dans la méthode nommée **GetSqlConnectionStringBuilder**.  
  
REMARQUE :  La chaîne de connexion pour le nom du serveur est orientée vers Azure SQL Database, car elle comprend le préfixe à quatre caractères de **tcp :** . Toutefois, vous pouvez ajuster la chaîne de serveur pour vous connecter à votre Microsoft SQL Server.  
  
  
```csharp
using System;  // C#  
using CG = System.Collections.Generic;  
using QC = Microsoft.Data.SqlClient;  
using TD = System.Threading;  
    
namespace RetryAdo2  
{  
  public class Program  
  {  
    static public int Main(string[] args)  
    {  
      bool succeeded = false;  
      int totalNumberOfTimesToTry = 4;  
      int retryIntervalSeconds = 10;  
    
      for (int tries = 1;  
        tries <= totalNumberOfTimesToTry;  
        tries++)  
      {  
        try  
        {  
          if (tries > 1)  
          {  
            Console.WriteLine  
              ("Transient error encountered. Will begin attempt number {0} of {1} max...",  
              tries, totalNumberOfTimesToTry  
              );  
            TD.Thread.Sleep(1000 * retryIntervalSeconds);  
            retryIntervalSeconds = Convert.ToInt32  
              (retryIntervalSeconds * 1.5);  
          }  
          AccessDatabase();  
          succeeded = true;  
          break;  
        }  
    
        catch (QC.SqlException sqlExc)  
        {  
          if (TransientErrorNumbers.Contains  
            (sqlExc.Number) == true)  
          {  
            Console.WriteLine("{0}: transient occurred.", sqlExc.Number);  
            continue;  
          }  
          else  
          {  
            Console.WriteLine(sqlExc);  
            succeeded = false;  
            break;  
          }  
        }  
    
        catch (TestSqlException sqlExc)  
        {  
          if (TransientErrorNumbers.Contains  
            (sqlExc.Number) == true)  
          {  
            Console.WriteLine("{0}: transient occurred. (TESTING.)", sqlExc.Number);  
            continue;  
          }  
          else  
          {  
            Console.WriteLine(sqlExc);  
            succeeded = false;  
            break;  
          }  
        }  
    
        catch (Exception Exc)  
        {  
          Console.WriteLine(Exc);  
          succeeded = false;  
          break;  
        }  
      }  
    
      if (succeeded == true)  
      {  
        return 0;  
      }  
      else  
      {  
        Console.WriteLine("ERROR: Unable to access the database!");  
        return 1;  
      }  
    }  
    
    /// <summary>  
    /// Connects to the database, reads,  
    /// prints results to the console.  
    /// </summary>  
    static public void AccessDatabase()  
    {  
      //throw new TestSqlException(4060); //(7654321);  // Uncomment for testing.  
    
      using (var sqlConnection = new QC.SqlConnection  
          (GetSqlConnectionString()))  
      {  
        using (var dbCommand = sqlConnection.CreateCommand())  
        {  
          dbCommand.CommandText = @"  
SELECT TOP 3  
    ob.name,  
    CAST(ob.object_id as nvarchar(32)) as [object_id]  
  FROM sys.objects as ob  
  WHERE ob.type='IT'  
  ORDER BY ob.name;";  
    
          sqlConnection.Open();  
          var dataReader = dbCommand.ExecuteReader();  
    
          while (dataReader.Read())  
          {  
            Console.WriteLine("{0}\t{1}",  
              dataReader.GetString(0),  
              dataReader.GetString(1));  
          }  
        }  
      }  
    }  
    
    /// <summary>  
    /// You must edit the four 'my' string values.  
    /// </summary>  
    /// <returns>An ADO.NET connection string.</returns>  
    static private string GetSqlConnectionString()  
    {  
      // Prepare the connection string to Azure SQL Database.  
      var sqlConnectionSB = new QC.SqlConnectionStringBuilder();  
    
      // Change these values to your values.  
      sqlConnectionSB.DataSource = "tcp:myazuresqldbserver.database.windows.net,1433"; //["Server"]  
      sqlConnectionSB.InitialCatalog = "MyDatabase"; //["Database"]  
    
      sqlConnectionSB.UserID = "MyLogin";  // "@yourservername"  as suffix sometimes.  
      sqlConnectionSB.Password = "MyPassword";  
      sqlConnectionSB.IntegratedSecurity = false;  
    
      // Adjust these values if you like. (ADO.NET 4.5.1 or later.)  
      sqlConnectionSB.ConnectRetryCount = 3;  
      sqlConnectionSB.ConnectRetryInterval = 10;  // Seconds.  
    
      // Leave these values as they are.  
      sqlConnectionSB.IntegratedSecurity = false;  
      sqlConnectionSB.Encrypt = true;  
      sqlConnectionSB.ConnectTimeout = 30;  
    
      return sqlConnectionSB.ToString();  
    }  
    
    static public CG.List<int> TransientErrorNumbers =  
      new CG.List<int> { 4060, 40197, 40501, 40613,  
      49918, 49919, 49920, 11001 };  
  }  
    
  /// <summary>  
  /// For testing retry logic, you can have method  
  /// AccessDatabase start by throwing a new  
  /// TestSqlException with a Number that does  
  /// or does not match a transient error number  
  /// present in TransientErrorNumbers.  
  /// </summary>  
  internal class TestSqlException : ApplicationException  
  {  
    internal TestSqlException(int testErrorNumber)  
    { this.Number = testErrorNumber; }  
    
    internal int Number  
    { get; set; }  
  }  
}  
```  
  
###  <a name="step-2c-run-the-program"></a>Étape 2.c : Exécuter le programme  
  
  
L’exécutable **RetryAdo2.exe** n’entre aucun paramètre. Pour exécuter l’exécutable :  
  
1. Ouvrez une fenêtre de console à l’endroit où vous avez compilé le fichier binaire RetryAdo2.exe.  
2. Exécutez RetryAdo2.exe, sans paramètres d’entrée.  
  
  
  
```  
database_firewall_rules_table   245575913  
filestream_tombstone_2073058421 2073058421  
filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Étape 3 : Méthodes pour tester votre logique de nouvelle tentative  
  
Il existe différentes façons de simuler une erreur temporaire pour tester votre logique de nouvelle tentative.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Étape 3.a : Lever une exception de test  
  
L’exemple de code inclut ce qui suit :  
  
- Une petite seconde classe nommée **TestSqlException**, avec une propriété nommée **Nombre**.  
- `//throw new TestSqlException(4060);` , dont vous pouvez supprimer les marques de commentaire.  
  
Si vous supprimez les marques de commentaire de l’instruction lancée puis que vous recompilez, la prochaine exécution de **RetryAdo2.exe** génère un résultat semblable à ce qui suit.  
  
```  
[C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
>> RetryAdo2.exe  
4060: transient occurred. (TESTING.)  
Transient error encountered. Will begin attempt number 2 of 4 max...  
4060: transient occurred. (TESTING.)  
Transient error encountered. Will begin attempt number 3 of 4 max...  
4060: transient occurred. (TESTING.)  
Transient error encountered. Will begin attempt number 4 of 4 max...  
4060: transient occurred. (TESTING.)  
ERROR: Unable to access the database!  
  
[C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
>>  
```  
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Étape 3.b : Tester à nouveau avec une erreur persistante  
  
Pour prouver que le code gère correctement les erreurs persistantes, exécutez à nouveau le test précédent, sans utiliser de numéro d’erreur temporaire réelle comme 4060. Utilisez plutôt un nombre sans signification particulière tel que 7654321. Le programme doit traiter ceci comme une erreur persistante et doit ignorer toute nouvelle tentative.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Étape 3.c : Se déconnecter du réseau  
  
1. Déconnectez votre ordinateur client du réseau.  
    - Pour un ordinateur de bureau, débranchez le câble réseau.  
    - Pour un ordinateur portable, appuyez sur la combinaison de touches permettant de désactiver la carte réseau.  
2. Démarrez RetryAdo2.exe et attendez que la console affiche la première erreur temporaire, probablement 11001.  
3. Reconnectez-vous au réseau pendant que RetryAdo2.exe continue de s’exécuter.  
4. Regardez la réussite du rapport de la console sur une nouvelle tentative ultérieure.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Étape 2.d : Mal orthographier temporairement le nom du serveur  
  
1. Ajoutez temporairement 40615 comme autre numéro d’erreur à **TransientErrorNumbers**, puis recompilez.  
2. Définissez un point d’arrêt sur la ligne : `new QC.SqlConnectionStringBuilder()`.  
3. Utilisez la fonctionnalité *Modifier et continuer* pour mal orthographier volontairement le nom du serveur, deux lignes en dessous.  
    - Laissez le programme s’exécuter et revenez à votre point d’arrêt.  
    - L’erreur 40615 se produit.  
4. Corrigez la faute d’orthographe.  
5. Laissez le programme s’exécuter et se terminer correctement.  
6. Supprimez 40615 et recompilez.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
Pour découvrir d’autres meilleures pratiques et recommandations en matière de conception, visitez [Connexion à SQL Database : liens, meilleures pratiques et règles de conception](https://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
