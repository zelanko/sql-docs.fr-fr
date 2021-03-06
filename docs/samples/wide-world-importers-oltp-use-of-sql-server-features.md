---
title: Utilisation des fonctionnalités et fonctionnalités de SQL Server | Microsoft Docs
description: En savoir plus sur les fonctionnalités et fonctionnalités de SQL Server et leur utilisation dans l’exemple de base de données WideWorldImporters.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 01/21/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 06f89721-8478-4abc-8ada-e9c73b08bf51
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 89ba727e4fd8217cfef8a73ff341d0ed0a7359a2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85718565"
---
# <a name="use-of-sql-server-features-and-capabilities"></a>Utilisation des fonctionnalités et des fonctionnalités de SQL Server

[!INCLUDE [SQL Server Azure SQL Database](../includes/applies-to-version/sql-asdb.md)]

WideWorldImporters l’utilisation des fonctionnalités et des fonctionnalités de SQL Server dans la base de données OLTP.

WideWorldImporters est conçu pour présenter un grand nombre des principales fonctionnalités de SQL Server, notamment les dernières fonctionnalités introduites dans SQL Server 2016. Le tableau suivant répertorie les fonctionnalités et les fonctionnalités de SQL Server. Chaque ligne fournit également une description de la façon dont les fonctionnalités sont utilisées dans WideWorldImporters.  
&nbsp;

|Fonctionnalité ou fonctionnalité de SQL Server|Utilisation dans WideWorldImporters|
|:-------------------------------|:------------------------|
|Tables temporelles|Il existe de nombreuses tables temporelles, notamment toutes les tables de référence de style de recherche et les entités principales telles que StockItems, les clients et les fournisseurs. L’utilisation de tables temporelles permet d’effectuer facilement le suivi de l’historique de ces entités.|
|Appels AJAX pour JSON|L’application utilise fréquemment des appels AJAX pour interroger ces tables : personnes, clients, fournisseurs et StockItems. Les appels retournent les données au format JSON. Par exemple, consultez la procédure stockée `Website.SearchForCustomers` .|
|Conteneurs de propriétés/valeurs JSON|Plusieurs tables contiennent des colonnes qui contiennent des données JSON pour étendre les données relationnelles de la table. Par exemple, `Application.SystemParameters` a une colonne pour les paramètres de l’application et `Application.People` contient une colonne pour enregistrer les préférences de l’utilisateur. Ces tables utilisent une `nvarchar(max)` colonne pour enregistrer les données JSON, ainsi qu’une contrainte de validation à l’aide de la fonction intégrée `ISJSON` pour s’assurer que les valeurs de colonne sont des données JSON valides.|
|Sécurité au niveau des lignes (SNL)|Sécurité au niveau des lignes (RLS) est utilisé pour limiter l’accès à la table Customers, en fonction de l’appartenance au rôle. Chaque secteur de vente possède un rôle et un utilisateur. Pour afficher une limite d’accès RLS en action, utilisez le script correspondant dans sample-script.zip, qui fait partie de la [version de l’exemple](https://go.microsoft.com/fwlink/?LinkID=800630).|
|analytique opérationnelle en temps réel|(Version complète de la base de données) Les principales tables transactionnelles `Sales.InvoiceLines` et `Sales.OrderLines` ont un index ColumnStore non cluster pour prendre en charge l’exécution efficace des requêtes analytiques dans la base de données transactionnelle avec un impact minimal sur la charge de travail opérationnelle. L’exécution des transactions et de l’analyse dans la même base de données est également appelée [HTAP (processus hybride transactionnel/analytique)](https://wikipedia.org/wiki/Hybrid_Transactional/Analytical_Processing_(HTAP)). Pour voir cela en action, utilisez le script correspondant dans sample-script.zip, qui fait partie de la [version de l’exemple](https://go.microsoft.com/fwlink/?LinkID=800630).|
|PolyBase|Pour voir cette Polybase en action, à l’aide d’une table externe avec un jeu de données public hébergé dans le stockage de blogs Azure, utilisez le script correspondant dans sample-script.zip, qui fait partie de la [version de l’exemple](https://go.microsoft.com/fwlink/?LinkID=800630).|
|OLTP en mémoire|(Version complète de la base de données) Les types de table sont tous optimisés en mémoire, de sorte que les paramètres table (TVP) bénéficient tous de l’optimisation de la mémoire.<br/><br/>Les deux tables d’analyse, `Warehouse.VehicleTemperatures` et `Warehouse.ColdRoomTemperatures` , sont optimisées en mémoire. L’optimisation de la mémoire permet de remplir la table ColdRoomTemperatures à une vitesse supérieure à celle d’une table sur disque traditionnelle. La table VehicleTemperatures contient la charge utile JSON et se prête à l’extension des scénarios IoT. La table VehicleTemperatures se prête davantage aux scénarios impliquant EventHubs, Stream Analytics et Power BI.<br/><br/>La procédure stockée `Website.RecordColdRoomTemperatures` est compilée en mode natif pour améliorer davantage les performances d’enregistrement des températures de la chambre froide.<br/><br/>Pour voir un exemple d’OLTP en mémoire en action, consultez le pilote de charge de travail véhicules-emplacements dans workload-drivers.zip, qui fait partie de la [version de l’exemple](https://go.microsoft.com/fwlink/?LinkID=800630).|
|Index columnstore cluster|(Version complète de la base de données) La table `Warehouse.StockItemTransactions` utilise un index cluster ColumnStore. Le nombre de lignes dans cette table est supposé croître, et l’index ColumnStore cluster réduit considérablement la taille sur disque de la table et améliore les performances des requêtes. La modification apportée à cette table est en insertion seule. il n’existe pas de mise à jour/suppression sur cette table dans la charge de travail en ligne, et l’index ColumnStore en cluster s’exécute bien pour les charges de travail d’insertion.|
|Masquage dynamique des données|Dans le schéma de base de données, le masquage des données a été appliqué aux détails bancaires détenus pour les fournisseurs, dans le tableau `Purchasing.Suppliers` . Le personnel non administrateur n’aura pas accès à ces informations.|
|Always Encrypted|Une démonstration de Always Encrypted est incluse dans le samples.zip téléchargeable, qui fait partie de la [version de l’exemple](https://go.microsoft.com/fwlink/?LinkID=800630). La démonstration crée une clé de chiffrement, une table utilisant le chiffrement pour les données sensibles et un petit exemple d’application qui insère des données dans la table.|
|Stretch Database|La `Warehouse.ColdRoomTemperatures` table a été implémentée en tant que table temporelle et est optimisée en mémoire dans la version complète de l’exemple de base de données. La table d’archive est basée sur disque et peut être étirée sur Azure.|
|Index de texte intégral|Les index de recherche en texte intégral améliorent les recherches pour les personnes, les clients et les StockItems. Les index sont appliqués aux requêtes uniquement si l’indexation de texte intégral est installée sur votre instance SQL Server. Une colonne calculée non persistante est utilisée pour créer les données qui sont indexées en texte intégral dans la table StockItems.<br/><br/>`CONCAT`est utilisé pour concaténer les champs afin de créer des SearchData qui sont indexés en texte intégral.<br/>Pour activer l’utilisation d’index de recherche en texte intégral dans l’exemple, exécutez l’instruction suivante dans la base de données :<br/><br/>`EXECUTE [Application].[Configuration_ConfigureFullTextIndexing]`<br/><br/>La procédure crée un catalogue de texte intégral par défaut s’il n’en existe pas déjà un, puis remplace les vues de recherche par des versions en texte intégral de ces vues.<br/><br/>Notez que l’utilisation d’index de recherche en texte intégral dans SQL Server nécessite la sélection de l’option de texte intégral lors de l’installation. Azure SQL Database n’a pas besoin d’une configuration spécifique pour activer les index de recherche en texte intégral.|
|Colonnes calculées persistantes indexées|Colonnes calculées persistantes indexées utilisées dans SupplierTransactions et CustomerTransactions.|
|Contraintes de validation|Une contrainte de validation relativement complexe est dans `Sales.SpecialDeals` . Cela permet de s’assurer qu’un seul DiscountAmount, DiscountPercentage et UnitPrice est configuré.|
|Contraintes uniques|Une construction de plusieurs à plusieurs (et des contraintes uniques) est configurée pour `Warehouse.StockItemStockGroups` .|
|Partitionnement de table|(Version complète de la base de données) Les tables `Sales.CustomerTransactions` et `Purchasing.SupplierTransactions` sont partitionnées par année à l’aide de la fonction de partition `PF_TransactionDate` et du schéma de partition `PS_TransactionDate` . Le partitionnement est utilisé pour améliorer la facilité de gestion des tables volumineuses.|
|Traitement de la liste|Un exemple de type de table `Website.OrderIDList` est fourni. Elle est utilisée par un exemple de procédure `Website.InvoiceCustomerOrders` . La procédure utilise des expressions de table communes (CTE), TRY/CATCH, JSON_MODIFY, XACT_ABORT, NOCOUNT, THROW et XACT_STATE pour illustrer la possibilité de traiter une liste de commandes au lieu d’une seule commande, afin de minimiser les allers-retours de l’application vers le moteur de base de données.|
|Compression GZip|Dans la `Warehouse.VehicleTemperature` vue, sa table contient des données de capteur complètes. Toutefois, lorsque ces données sont datant de plus de quelques mois, elles sont compressées pour conserver de l’espace. La fonction COMPRESS utilise la compression GZip.<br/><br/>La vue `Website.VehicleTemperatures` utilise la fonction DECOMPRESS lors de la récupération de données précédemment compressées.|
|Magasin des requêtes|Magasin des requêtes est activé sur la base de données. Après avoir exécuté quelques requêtes, procédez comme suit :<br/><br/>1. Ouvrez la base de données dans Management Studio.<br/>2. Ouvrez le nœud Magasin des requêtes, qui se trouve sous la base de données.<br/>3. Ouvrez le rapport *principales requêtes consommatrices de ressources*. Consultez les exécutions de requête et consultez les plans pour les requêtes que vous venez d’exécuter.|
|STRING_SPLIT|La colonne `DeliveryInstructions` de la table `Sales.Invoices` a une valeur délimitée par des virgules qui peut être utilisée pour illustrer STRING_SPLIT.|
|Audit|SQL Server audit peut être activé pour cet exemple de base de données en exécutant l’instruction suivante dans la base de données :<br/><br/>`EXECUTE [Application].[Configuration_ApplyAuditing]`<br/><br/>Dans Azure SQL Database, l’audit est activé via l' [portail Azure](https://portal.azure.com/).<br/><br/>Les opérations de sécurité impliquant des connexions, des rôles et des autorisations sont journalisées sur tous les systèmes où l’audit est activé (y compris les systèmes d’édition standard). L’audit est dirigé vers le journal des applications, car il est disponible sur tous les systèmes et ne nécessite pas d’autorisations supplémentaires. Un avertissement est fourni pour renforcer la sécurité, il doit être redirigé vers le journal de sécurité ou un fichier dans un dossier sécurisé. Un lien est fourni pour décrire la configuration supplémentaire requise.<br/><br/>Pour les systèmes d’évaluation/développeur/Enterprise Edition, l’accès à toutes les données transactionnelles financières est audité.|
| &nbsp; | &nbsp; |
