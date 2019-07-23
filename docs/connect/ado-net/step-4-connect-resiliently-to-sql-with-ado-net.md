---
title: 'Étape 4: connexion résiliente à SQL avec ADO.NET | Microsoft Docs'
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
ms.openlocfilehash: 7a080f68497829657c60bbd96238b71123b70d87
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957595"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Étape 4 : Connexion résiliente à SQL avec ADO.NET

- Article précédent : &nbsp;&nbsp;&nbsp;[Étape 3 : Preuve de concept pour la connexion à SQL à l’aide d’ADO.NET](step-3-proof-of-concept-connecting-to-sql-using-ado-net.md)  

  
Cette rubrique fournit un C# exemple de code illustrant une logique de nouvelle tentative personnalisée. La logique de nouvelle tentative assure la fiabilité. La logique de nouvelle tentative est conçue pour traiter correctement les erreurs temporaires ou les erreurs *temporaires qui ont* tendance à disparaître si le programme attend quelques secondes et effectue de nouvelles tentatives.  
  
Les sources d’erreurs temporaires sont les suivantes:  
  
- Une brève défaillance de la mise en réseau qui prend en charge Internet.  
- Un système Cloud peut être chargé d’équilibrer la charge de ses ressources au moment où votre requête a été envoyée.  
  
  
Les classes ADO.NET pour la connexion à votre Microsoft SQL Server local peuvent également se connecter à Azure SQL Database. Toutefois, les classes ADO.NET ne peuvent pas fournir toute la robustesse et la fiabilité nécessaires en production. Votre programme client peut rencontrer des erreurs temporaires à partir desquelles il doit effectuer une récupération en mode silencieux et normal, et continuer de façon autonome.  
  
## <a name="step-1-identify-transient-errors"></a>Étape 1: identifier les erreurs temporaires  
  
Votre programme doit faire la distinction entre les erreurs temporaires et les erreurs persistantes. Les erreurs temporaires sont des conditions d’erreur qui peuvent être effacées dans un laps de temps réduit, par exemple des problèmes réseau temporaires.  Par exemple, si votre programme a une faute de frappe dans le nom de la base de données cible (dans ce cas, l’erreur «cette base de données introuvable» est conservée et n’a pas de risque d’être vidée dans un laps de temps réduit.  
  
La liste des numéros d’erreur catégorisés comme des erreurs temporaires est disponible dans les [messages d’erreur pour SQL Database les applications clientes](https://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/)  
  
## <a name="step-2-create-and-run-sample-application"></a>Étape 2: créer et exécuter un exemple d’application  
  
Cet exemple suppose que .NET Framework 4.5.1 ou version ultérieure est installé.  L' C# exemple de code se compose d’un fichier nommé Program.cs. Son code est fourni dans la section suivante.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Étape 2. a: capturer et compiler l’exemple de code  
  
Vous pouvez compiler l’exemple en procédant comme suit:  
  
1. Dans l' [édition Visual Studio Community gratuite](https://www.visualstudio.com/products/visual-studio-community-vs), créez un projet à partir du C# modèle application console.  
    - Fichier > nouveau projet de > > installé des modèles de C# > > Visual > Windows > Application console > de bureau classique  
    - Nommez le projet **RetryAdo2**.  
2. Ouvrez le volet Explorateur de solutions.  
    - Consultez le nom de votre projet.  
    - Consultez le nom du fichier Program.cs.  
3. Ouvrez le fichier Program.cs.  
4. Remplacez entièrement le contenu du fichier Program.cs par le code du bloc de code suivant.  
5. Cliquez sur le menu Générer > générer la solution.  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Étape 2. b: copier et coller l’exemple de code  
  
Collez ce code dans votre fichier **Program.cs** .  
  
Vous devez ensuite modifier les chaînes pour le nom du serveur, le mot de passe, etc. Ces chaînes sont disponibles dans la méthode nommée **GetSqlConnectionStringBuilder**.  
  
Remarque: la chaîne de connexion pour le nom du serveur est orientée vers Azure SQL Database, car elle comprend le préfixe **TCP:** . Toutefois, vous pouvez ajuster la chaîne de serveur pour vous connecter à votre Microsoft SQL Server.  
  
  
```csharp
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
  
###  <a name="step-2c-run-the-program"></a>Étape 2. c: exécuter le programme  
  
  
L’exécutable **RetryAdo2. exe** n’entre aucun paramètre. Pour exécuter le fichier. exe:  
  
1. Ouvrez une fenêtre de console à l’emplacement où vous avez compilé le binaire RetryAdo2. exe.  
2. Exécutez RetryAdo2. exe, sans paramètres d’entrée.  
  
  
  
```  
    database_firewall_rules_table   245575913  
    filestream_tombstone_2073058421 2073058421  
    filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Étape 3: méthodes de test de votre logique de nouvelle tentative  
  
Il existe plusieurs façons de simuler une erreur temporaire pour tester votre logique de nouvelle tentative.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Étape 3. a: lever une exception de test  
  
L’exemple de code comprend les éléments suivants:  
  
- Une petite seconde classe nommée **TestSqlException**, avec une propriété nommée **Number**.  
- `//throw new TestSqlException(4060);`, qui vous permet d’annuler les marques de commentaire.  
  
Si vous supprimez les marques de commentaire de l’instruction throw, puis recompilez, la prochaine exécution de **RetryAdo2. exe** génère un résultat similaire à ce qui suit.  
  
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
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Étape 3. b: retest avec une erreur persistante  
  
Pour prouver que le code gère correctement les erreurs persistantes, réexécutez le test précédent, sauf que vous n’utilisez pas le numéro d’une erreur réelle temporaire comme 4060. Utilisez à la place le numéro de non-sens 7654321. Le programme doit traiter ce problème comme une erreur persistante et doit ignorer toute nouvelle tentative.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Étape 3. c: se déconnecter du réseau  
  
1. Déconnectez votre ordinateur client du réseau.  
    - Pour un ordinateur de bureau, débranchez le câble réseau.  
    - Pour un ordinateur portable, appuyez sur la combinaison de fonctions clés pour désactiver la carte réseau.  
2. Démarrez RetryAdo2. exe et attendez que la console affiche la première erreur temporaire, probablement 11001.  
3. Reconnectez-vous au réseau pendant que RetryAdo2. exe continue de s’exécuter.  
4. Regardez la console signaler la réussite d’une nouvelle tentative.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Étape 2. d: orthographiez temporairement le nom du serveur  
  
1. Ajoutez temporairement 40615 comme autre numéro d’erreur à **TransientErrorNumbers**, puis recompilez.  
2. Définissez un point d’arrêt sur la `new QC.SqlConnectionStringBuilder()`ligne:.  
3. Utilisez la fonctionnalité *modifier & continuer* pour mal orthographier le nom du serveur, deux lignes au-dessous.  
    - Laissez le programme s’exécuter et revenez à votre point d’arrêt.  
    - L’erreur 40615 se produit.  
4. Corrigez les fautes d’orthographe.  
5. Laissez le programme s’exécuter et se terminer avec succès.  
6. Supprimez 40615, puis recompilez.  
  
## <a name="next-steps"></a>Next Steps  
  
Pour découvrir d’autres meilleures pratiques et recommandations en matière de conception, consultez [connexion à SQL Database: liens, meilleures pratiques et règles de conception](https://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
