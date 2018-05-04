---
title: Liste des bases de données existantes sur un serveur tabulaire (Analysis Services AMO-TOM) | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ab5eb4b8-6254-442d-a42e-2372c346d260
caps.latest.revision: 2
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ec4718f826815217b13c7b27acfd3b51ec148fe4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="list-existing-databases-on-a-tabular-server-analysis-services-amo-tom"></a>Liste des bases de données existantes sur un serveur tabulaire (Analysis Services AMO-TOM)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Lorsque vous avez un **Server** de l’objet qui est connecté à une instance Analysis Services, vous pouvez itérer **Server.Databases** collection pour répertorier toutes les bases de données hébergées par l’instance des Services d’analyse. 

Le **Server.Databases** collection contient un **base de données** objet pour chaque base de données hébergée sur le serveur, quel que soit le mode de serveur (multidimensionnel ou tabulaire) ou le type de base de données (multidimensionnel, tabulaire pre-1200 ou tabulaire 1200 et versions ultérieures). 

Vous pouvez vérifier le type de base de données via **Database.StorageEngineUsed** propriété.  

Bases de données tabulaires 1200 et supérieurs retourne une valeur non null **Database.Model** propriété qui donne accès à tous les objets de métadonnées tabulaires : Tables, colonnes, relations et ainsi de suite.  

Pour multidimensionnel ou tabulaire 1103 et en dessous, le Database.Model propriété sera null. Dans ce cas, les métadonnées non tabulaires seront disponibles sous propriétés multidimensionnelles (telles que Database.Cubes et Database.Dimensions), mais ces propriétés sont exposées uniquement par classe Microsoft.AnalysisServices.Database (à partir de AMO), pas par Microsoft.AnalysisServices.Tabular.Database (pour TOM). Pour plus d’informations sur la classe de base de données à utiliser, consultez [installer, de distribuer et de faire référence à la bibliothèque cliente de TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md).

Sauf si Database.StorageEngineUsed est définie avec la valeur tabularmetadata, vous ne pourrez pas utilisez d’autres classes dans l’espace de noms tabulaire accéder et de manipuler l’arborescence du modèle. 

Le tableau suivant résume les comportements attendus lorsque vous vous connectez à un serveur ou une base de données à l’aide d’une classe Microsoft.AnalysisServices.Tabular sur un serveur ou une base de données. 

mode | Database.Model | Database.StorageEngineUsed
-----|----------------|---------------------------
Tabulaire 1200, 1400 | Retourne le nom du modèle| StorageEngineUsed.TabularMetadata 
1103 tabulaires, 1100, 1050 | Retourne la valeur null | StorageEngineUsed.InMemory 
(Multidimensionnel) | Retourne la valeur null | StorageEngineUsed.Traditional 

## <a name="code-example-list-existing-databases"></a>Exemple de code : répertorier les bases de données existantes

Le code ci-dessous illustre comment se connecter aux bases de données serveur et liste hébergés par le serveur. 

```
using System; using Microsoft.AnalysisServices; 
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
                // List common properties for the databases on the server. 
                // 
                foreach (Database db in server.Databases) 
                { 
                    Console.WriteLine("Properties for database {0}:", db.Name); 
                    Console.ForegroundColor = ConsoleColor.Yellow; 
                    Console.WriteLine("Database ID:\t\t\t{0}", db.ID); 
                    Console.WriteLine("Database compatibility level:\t{0}", db.CompatibilityLevel); 
                    Console.WriteLine("Database collation:\t\t{0}", db.Collation); 
                    Console.WriteLine("Database created timestamp:\t{0}", db.CreatedTimestamp); 
                    Console.WriteLine("Database language ID:\t\t{0}", db.Language); 
                    Console.WriteLine("Database model type:\t\t{0}", db.ModelType); 
                    Console.WriteLine("Database state:\t\t\t{0}", db.State); 
                    Console.ResetColor(); 
                    Console.WriteLine(); 
                } 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```


## <a name="get-an-item-from-a-database"></a>Obtenir un élément à partir d’une base de données 

L’extrait de code suivant montre comment obtenir un tableau ou une colonne à partir d’une base de données. 


```
var db = srv.Databases.GetByName("abc"); 

Column c1 = db.Model.Tables["foo"].Columns["bar"]; 
if (c1.ObjectType == ObjectType.Column) // always true 

MetadataObject obj; 

switch(obj.ObjectType) 
{ 
 case ObjectType.Table: 
  var t1 = (Table)obj; 
  break; 
} 
```

## <a name="next-steps"></a>Étapes suivantes

Comprendre comment [créer et déployer une base de données vide](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md) à l’aide de l’API TOM.

