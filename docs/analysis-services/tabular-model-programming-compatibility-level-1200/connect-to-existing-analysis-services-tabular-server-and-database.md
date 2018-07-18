---
title: Se connecter à la base de données et de serveur tabulaire Analysis Services existante | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13900e4aaad52d39a2691fb40d0e419f55f660fc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033389"
---
# <a name="connect-to-existing-analysis-services-tabular-server-and-database"></a>Se connecter à la base de données et de serveur tabulaire Analysis Services existante
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Dans SQL Server 2016, Analysis Services Management Objects (AMO) inclut plusieurs espaces de noms qui permet de configurer une connexion de serveur. Cet article explique comment établir une connexion au serveur à l’aide de l’espace de noms Microsoft.AnalysisServices.Tabular pour les modèles et les bases de données créées à 1200 ou niveau de compatibilité supérieur. 

Pour vous connecter à un serveur Analysis Services, votre code doit instancier un objet serveur et puis appelez la méthode Connect dessus. Une fois connecté, les propriétés de l’objet serveur reflète alors les paramètres de l’instance Analysis Services actuelle. 

Les classes suivantes peuvent être utilisées pour les connexions de niveau supérieur : 

* Microsoft.AnalysisServices.Server 
* Microsoft.AnalysisServices.Database 
* Microsoft.AnalysisServices.Tabular.Server 
* Microsoft.AnalysisServices.Tabular.Database 

Comme vous pouvez le voir, les deux espaces de noms fournissent une connectivité à des objets serveur et base de données : l’espace de noms Microsoft.AnalysisServices d’origine pour AMO et le nouvel espace de noms Microsoft.AnalysisServices.Tabular pour TOM.

Pourquoi deux espaces de noms pour les mêmes opérations ? La réponse se trouve en aval, au niveau base de données et de modèle, où la hiérarchie d’objets devient spécifiques au mode et l’arborescence du modèle est composé de métadonnées multidimensionnel ou tabulaire. Pour effectuer des appels dans l’arborescence du modèle, l’objet serveur ou base de données est fourni pour les deux types de modèles.

> [!NOTE]  
>  Les métadonnées utilisées pour les opérations et la définition du modèle sont complètement différente pour les deux modes. En séparant le langage de définition de données (DDL) en deux espaces de noms distincts, l’expérience de développement est simplifiée par la présentation d’uniquement l’API nécessaire pour un type de modèle spécifique. 

Bien que l’instruction DDL varie, connexions à un serveur sont les mêmes sur tous les modes, les versions et éditions. Prise en charge d’un serveur et une connexion de base de données via l’espace de noms vous permet d’écrire des outils génériques ou un script qui se connectent à n’importe quelle instance d’Analysis Services ou de base de données, sans avoir à connaître le type de modèle est hébergé sur le serveur.  

Cette flexibilité explique les dépendances entre les assemblys. Pour effectuer des appels sous le niveau de base de données (par exemple, sur un modèle dans une base de données tabulaires 1200, ou sur un Cube, Dimension ou MeasureGroup au sein d’une base de données multidimensionnelle ou tabulaire 1050-1103), AMO a une dépendance sur TOM. 

En revanche, TOM n’a pas de dépendance sur AMO. Bien que TOM ne peut pas être utilisé pour explorer des métadonnées multidimensionnelles (Cubes), AMO peut être utilisé pour Explorer les métadonnées multidimensionnelles et tabulaires. 

Pour cette raison, la première étape de configuration de votre projet nécessite l’ajout de références à tous les assemblys AMO. Consultez [installer, de référence et de distribuer la bibliothèque cliente de TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md) pour plus d’informations. 

> [!NOTE]  
>  Les connexions de serveur et base de données sont basées sur des classes AMO héritées qui héritent de MajorObject. Bien que les objets principaux et secondaires ne sont pas utilisées dans une arborescence de modèle tabulaire, la classe MajorObject est visible sous la forme d’une classe de base pour les objets serveur et base de données, quel que soit l’API qui vous permet de configurer la connexion.  

## <a name="code-example-server-connection"></a>Exemple de code : connexion au serveur 

Voici un exemple de code c# qui montre comment vous connecter à une instance Analysis Services locale et répertorier ses propriétés dans une fenêtre de console. 

Cet exemple montre uniquement certaines des propriétés d’un objet serveur, mais il existe des autres propriétés disponibles, y compris ServerMode et DefaultCompatibilityLevel.  

```
using System; 
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

 
                Console.WriteLine("Connection established successfully."); 
                Console.WriteLine(); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.WriteLine("Server name:\t\t{0}", server.Name); 
                Console.WriteLine("Server product name:\t{0}", server.ProductName); 
                Console.WriteLine("Server product level:\t{0}", server.ProductLevel); 
                Console.WriteLine("Server version:\t\t{0}", server.Version); 
                Console.ResetColor(); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```
Lorsque vous exécutez ce programme, la sortie affiche les propriétés sur l’objet serveur dans une fenêtre de console. 

## <a name="authentication-and-authorization"></a>Authentification et autorisation 

Un serveur ou une connexion de base de données à Analysis Services nécessite des autorisations administratives, utilisées pour les opérations de lecture-écriture et pour passer par une demande de connexion avec emprunt d’identité.  

Bien que l’infrastructure de sécurité Analysis Services a été étendu dans ces dernières années pour autoriser l’authentification personnalisée dans des conditions très spécifiques, la méthode d’authentification externe pris en charge uniquement est la sécurité intégrée de Windows. Principaux de sécurité sont supposées pour être Windows domaine utilisateur ou groupe de comptes valides.  

Sur Windows 2012 et versions ultérieures, délégation peut être transmise entre les domaines. Dans Analysis Services, la délégation est utilisée uniquement pour les modèles DirectQuery ; Sinon, les connexions sont directes ou avec emprunt d’identité. 

## <a name="next-steps"></a>Étapes suivantes 

Après avoir établi une connexion, une étape logique suivante consiste à deux bases de données existantes de liste déjà sur le serveur, ou peut-être créer une nouvelle base de données vide. Les liens suivants incluent des exemples de code qui illustrent les deux de ces tâches de base : 

- [Créer et déployer une base de données vide](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md)
- [Liste des bases de données existantes](../../analysis-services/tabular-model-programming-compatibility-level-1200/list-existing-databases-on-a-tabular-server-analysis-services-amo-tom.md)
