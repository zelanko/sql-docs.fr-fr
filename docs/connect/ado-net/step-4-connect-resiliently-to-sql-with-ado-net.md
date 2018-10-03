---
title: 'Étape 4 : Connexion résiliente à SQL avec ADO.NET | Microsoft Docs'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a812aacbbbd87ba8fc38479be7d62a0fc9401b6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731367"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Étape 4 : Connexion résiliente à SQL avec ADO.NET

- Article précédent : &nbsp;&nbsp;&nbsp;[Étape 3 : Preuve de concept pour la connexion à SQL à l’aide d’ADO.NET](step-3-proof-of-concept-connecting-to-sql-using-ado-net.md)  

  
Cette rubrique fournit un exemple de code c# qui illustre la logique de nouvelle tentative personnalisée. La logique de nouvelle tentative assure la fiabilité. La logique de nouvelle tentative est conçue pour traiter correctement les erreurs temporaires ou *transitoires* qui tendent à disparaître si le programme attend quelques secondes et les nouvelles tentatives.  
  
Sources d’erreurs temporaires sont les suivantes :  
  
- Un brève Échec de la connexion de réseau qui prend en charge d’Internet.  
- Un système cloud peut être l’équilibrage de charge ses ressources à l’instant, que votre requête a été envoyée.  
  
  
Les classes ADO.NET pour se connecter à votre serveur Microsoft SQL Server local peuvent également se connecter à la base de données SQL Azure. Toutefois, par eux-mêmes ADO.NET classes ne peut pas fournir toute la robustesse et la fiabilité nécessaire à la production. Votre programme client peut rencontrer des erreurs temporaires à partir de laquelle il doit normalement et en mode silencieux récupérer et continuer sur son propre.  
  
## <a name="step-1-identify-transient-errors"></a>Étape 1 : Identifier les erreurs temporaires  
  
Votre programme doit faire la distinction entre les erreurs temporaires et les erreurs persistantes. Erreurs temporaires sont des conditions d’erreur qui peuvent résoudre sur une courte période de temps, telles que des problèmes réseau temporaires.  Un exemple d’une erreur permanente lors serait, si votre programme a mal orthographié le nom de la base de données cible, dans ce cas, l’erreur « Aucune base de données trouvée » soit persistant et ne risque pas d’effacer les sur une courte période de temps.  
  
La liste des numéros d’erreur qui sont classés comme des erreurs temporaires est disponible à l’adresse à [messages d’erreur pour les applications clientes SQL Database](http://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/)  
  
## <a name="step-2-create-and-run-sample-application"></a>Étape 2 : Créer et exécuter l’exemple d’application  
  
Cet exemple part du principe que .NET Framework 4.5.1 ou version ultérieure est installé.  L’exemple de code c# se compose d’un fichier nommé Program.cs. Son code est fourni dans la section suivante.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Étape 2.a : capturer et compiler l’exemple de code  
  
Vous pouvez compiler l’exemple en procédant comme suit :  
  
1. Dans le [édition gratuite Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs), créez un projet à partir du modèle d’Application Console c#.  
    - Fichier > Nouveau > projet > installé > Modèles > Visual c# > Windows > Bureau classique > Application Console  
    - Nommez le projet **RetryAdo2**.  
2. Ouvrez le volet Explorateur de solutions.  
    - Afficher le nom de votre projet.  
    - Voir le nom du fichier Program.cs.  
3. Ouvrez le fichier Program.cs.  
4. Remplacez entièrement le contenu du fichier Program.cs par le code dans le bloc de code suivant.  
5. Cliquez sur le menu Générer > Générer la Solution.  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Étape 2.b : copier et coller des exemples de code  
  
Collez ce code dans votre **Program.cs** fichier.  
  
Ensuite, vous devez modifier les chaînes de nom de serveur, mot de passe et ainsi de suite. Vous pouvez trouver ces chaînes dans la méthode nommée **GetSqlConnectionStringBuilder**.  
  
Remarque : La chaîne de connexion pour le nom du serveur est axée sur la base de données SQL Azure, car il inclut le préfixe de quatre caractères de **tcp :**. Mais vous pouvez ajuster la chaîne de serveur pour vous connecter à votre serveur Microsoft SQL Server.  
  
  
```CSharp  
    using System;  // C#  
    using CG = System.Collections.Generic;  
    using QC = System.Data.SqlClient;  
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
  
###  <a name="step-2c-run-the-program"></a>Étape 2.c : exécutez le programme  
  
  
Le **RetryAdo2.exe** exécutable entre aucun paramètre. Pour exécuter le fichier .exe :  
  
1. Ouvrez une fenêtre de console où vous avez compilé le fichier binaire RetryAdo2.exe.  
2. Exécutez RetryAdo2.exe, sans paramètres d’entrée.  
  
  
  
```  
    database_firewall_rules_table   245575913  
    filestream_tombstone_2073058421 2073058421  
    filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Étape 3 : Comment tester votre logique de nouvelle tentative  
  
Il existe une multitude de façons, vous pouvez simuler une erreur temporaire pour tester votre logique de nouvelle tentative.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Étape 3 : lever une exception de test  
  
L’exemple de code inclut :  
  
- Une petite seconde classe nommée **TestSqlException**, avec une propriété nommée **nombre**.  
- `//throw new TestSqlException(4060);` , qui vous pouvez ne pas commenter.  
  
Si vous supprimez les commentaires de l’instruction throw et une recompilation, la prochaine exécution de **RetryAdo2.exe** génère un résultat semblable à ce qui suit.  
  
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
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>L’étape 3.b : Testez à nouveau avec une erreur persistante  
  
Pour prouver que le code gère des erreurs persistantes correctement, exécutez à nouveau le test précédent, n’utilisez pas le nombre d’une erreur temporaire réelle comme 4060. Utilisez plutôt un nombre 7654321. Le programme doit traiter ceci comme une erreur persistante et doit ignorer toute nouvelle tentative.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Étape 3.c : déconnecter du réseau  
  
1. Déconnecter votre ordinateur client à partir du réseau.  
    - Pour un ordinateur de bureau, débranchez le câble réseau.  
    - Pour un ordinateur portable, appuyez sur la combinaison de touches pour désactiver la carte réseau.  
2. Démarrez RetryAdo2.exe et attendez que la console afficher la première erreur temporaire, probablement 11001.  
3. Se reconnecter au réseau, RetryAdo2.exe continue à s’exécuter.  
4. Regardez la réussite du rapport de console sur une nouvelle tentative ultérieure.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Étape 2.d : mal orthographier temporairement le nom du serveur  
  
1. Ajoutez temporairement 40615 comme autre numéro d’erreur à **TransientErrorNumbers**, puis recompilez.  
2. Définissez un point d’arrêt sur la ligne : `new QC.SqlConnectionStringBuilder()`.  
3. Utilisez le *Modifier & Continuer* fonctionnalité pour mal orthographier volontairement le nom du serveur, deux lignes ci-dessous.  
    - Laissez le programme s’exécuter et revenez à votre point d’arrêt.  
    - L’erreur 40615 se produit.  
4. Corriger les fautes d’orthographe.  
5. Laissez le programme s’exécuter et se terminent correctement.  
6. Supprimez 40615 et recompilez.  
  
## <a name="next-steps"></a>Next Steps  
  
Pour découvrir d’autres meilleures practicies et les règles de conception, visitez [connexion à SQL Database : liens, les meilleures pratiques et les règles de conception](http://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
