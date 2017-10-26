---
title: "Créer et déployer une base de données vide (Analysis Services AMO-TOM) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dcb916e9-97c5-47e0-922a-404891423b2a
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f8aafa733ba61563072e304cf77945203df7585d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-and-deploy-an-empty-database-analysis-services-amo-tom"></a>Créer et déployer une base de données vide (Analysis Services AMO-TOM)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

Un scénario courant de programmation pour AMO-TOM consiste à générer des bases de données et des modèles à la volée. Cet article vous guide tout au long des étapes de création d’une base de données. 

Pour les solutions tabulaires, il existe une correspondance univoque entre une base de données et un modèle, avec un modèle par base de données. Vous pouvez généralement spécifier un ou l’autre, et le moteur déduit l’objet manquant. 

Création et déploiement d’une base de données sont une tâche en trois parties : 

* Instancier une **base de données** de l’objet et définissez ses propriétés, y compris un nom. 

* Ajouter le **base de données** de l’objet à un **Server.Databases** collection. 

* Appeler le **mise à jour** méthode sur le **base de données** objet à enregistrer sur le **Server**. 

## <a name="code-example-create-empty-database"></a>Exemple de code : créer une base de données vide 

```
using System; 
using Microsoft.AnalysisServices; 
using Microsoft.AnalysisServices.Tabular; 
 
namespace TOMSamples 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // 
            // Connect to the local default instance of Analysis Services 
            // 
            string ConnectionString = "DataSource=localhost"; 
 
            // 
            // The using syntax ensures the correct use of the 
            // Microsoft.AnalysisServices.Tabular.Server object. 
            // 
            using (Server server = new Server()) 
            { 
                server.Connect(ConnectionString); 
 
                // 
                // Generate a new database name and use GetNewName 
                // to ensure the database name is unique. 
                // 
                string newDatabaseName = 
                    server.Databases.GetNewName("New Empty Database"); 
 
                // 
                // Instantiate a new  
                // Microsoft.AnalysisServices.Tabular.Database object. 
                // 
                var blankDatabase = new Database() 
                { 
                    Name = newDatabaseName, 
                    ID = newDatabaseName, 
                    CompatibilityLevel = 1200, 
                    StorageEngineUsed = StorageEngineUsed.TabularMetadata, 
                }; 
                // 
                // Add the new database object to the server's  
                // Databases connection and submit the changes 
                // with full expansion to the server. 
                // 
                server.Databases.Add(blankDatabase); 
                blankDatabase.Update(UpdateOptions.ExpandFull); 

                Console.Write("Database "); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.Write(blankDatabase.Name); 
                Console.ResetColor(); 
                Console.WriteLine(" created successfully."); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="next-steps"></a>Étapes suivantes 

Une fois qu’une base de données est créé, vous pouvez ajouter des objets de modèle : 

- [Ajouter une source de données à un modèle tabulaire](../../analysis-services/tabular-model-programming-compatibility-level-1200/add-a-data-source-to-tabular-model-analysis-services-amo-tom.md)
- [Créer des tables, des partitions et des colonnes dans un modèle tabulaire](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-tables-partitions-and-columns-in-a-tabular-model.md)
 

