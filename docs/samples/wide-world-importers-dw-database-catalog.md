---
title: Catalogue de base de données WideWorldImporters OLAP - SQL | Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 3c329594ad6349f58c4ed910bdb1b86b040a07c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627110"
---
# <a name="wideworldimportersdw-database-catalog"></a>Catalogue de base de données WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Explications pour les schémas, les tables et les procédures stockées dans la base de données WideWorldImportersDW. 

La base de données WideWorldImportersDW est utilisé pour l’entreposage de données et le traitement analytique. Les données transactionnelles sur les achats et sont générées dans la base de données WideWorldImporters et chargées dans la base de données WideWorldImportersDW à l’aide un **processus ETL quotidien**.

Les données dans WideWorldImportersDW reflète donc les données de WideWorldImporters, mais les tables sont organisées différemment. Alors que WideWorldImporters a un schéma normalisé traditionnel, WideWorldImportersDW utilise le [schéma en étoile](https://wikipedia.org/wiki/Star_schema) approche pour sa conception de table. Outre les tables de faits et de dimension, la base de données inclut un nombre de tables intermédiaires qui sont utilisés dans le processus ETL.

## <a name="schemas"></a>Schémas

Les différents types de tables sont organisées dans trois schémas.

|schéma|Description|
|-----------------------------|---------------------|
|Dimension|Tables de dimension.|
|Fait|Tables de faits.|  
|Intégration|Tables intermédiaires et autres objets nécessaires pour ETL.|  

## <a name="tables"></a>Tables

Les tables de dimension et de faits sont répertoriées ci-dessous. Les tables dans le schéma d’intégration sont utilisés uniquement pour le processus ETL et ne sont pas répertoriées.

### <a name="dimension-tables"></a>Tables de dimension

WideWorldImportersDW a des tables de dimension suivantes. La description inclut la relation avec les tables source dans la base de données WideWorldImporters.

|Table de charge de travail|Tables source|
|-----------------------------|---------------------|
|Ville|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Customer|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|Date|Nouvelle table avec les informations sur les dates, y compris exercice (selon le 1er novembre de démarrage pour l’exercice).|
|Employee|`Application.People` .|
|StockItem|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|Fournisseur|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`.|
|PaymentMethod|`Application.PaymentMethods` .|
|TransactionType|`Application.TransactionTypes` .|

### <a name="fact-tables"></a>Tables de faits

WideWorldImportersDW a les tables de faits suivants. La description inclut la relation avec les tables source dans la base de données WideWorldImporters, ainsi que les classes de chaque table de faits est généralement utilisée avec des requêtes analytique et le reporting.

|Table de charge de travail|Tables source|Exemple Analytique|
|-----------------------------|---------------------|---------------------|
|JSON|`Sales.Orders` et `Sales.OrderLines`|Ventes aux personnes concernées, productivité sélecteur/packer et sur le temps de prélever des commandes. En outre, une faible stocks situations conduisant à commandes en différé.|
|Vente|`Sales.Invoices` et `Sales.InvoiceLines`|Dates de ventes, les dates de livraison, rentabilité au fil du temps, la rentabilité par commercial.|
|Achat|`Purchasing.PurchaseOrderLines`|Délais réel vs attendu|
|Transaction|`Sales.CustomerTransactions` et `Purchasing.SupplierTransactions`|Les dates de finalisation problème dates vs et les quantités de mesure.|
|Déplacement|`Warehouse.StockTransactions`|Mouvements au fil du temps.|
|Détention|`Warehouse.StockItemHoldings`|Les niveaux de stock disponible et la valeur.|

## <a name="stored-procedures"></a>Procédures stockées

Les procédures stockées sont utilisées principalement pour le processus ETL et à des fins de configuration.

Toutes les extensions de l’exemple sont encouragées à utiliser le `Reports` schéma pour les rapports Reporting Services et le `PowerBI` schéma pour l’accès de Power BI.

### <a name="application-schema"></a>Schéma d’application

Ces procédures sont utilisées pour configurer l’exemple. Ils sont utilisés pour appliquer les fonctionnalités d’édition entreprise vers la version Édition standard de l’exemple, ajoutez PolyBase et reseed ETL.

|Procédure|Fonction|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|S’applique à la fois le partitionnement et columnstore index pour les tables de faits.|
|Configuration_ConfigureForEnterpriseEdition|S’applique le partitionnement, columnstore d’indexation et en mémoire.|
|Configuration_EnableInMemory|Remplace les tables intermédiaires de l’intégration avec les tables optimisées en mémoire SCHEMA_ONLY pour améliorer les performances de l’ETL.|
|Configuration_ApplyPolybase|Configure une source de données externe, le format de fichier et la table.|
|Configuration_PopulateLargeSaleTable|Applique les modifications d’édition enterprise, puis remplit une plus grande quantité de données pour l’année 2012 en tant qu’historique supplémentaire.|
|Configuration_ReseedETL|Supprime les données existantes et redémarre les semences ETL. Ainsi, pour remplir à nouveau la base de données OLAP pour faire correspondre les lignes mises à jour dans la base de données OLTP.|

### <a name="integration-schema"></a>Schéma d’intégration

Procédures utilisées dans le processus ETL se répartissent dans ces catégories :
- Procédures d’assistance pour le package ETL - Get * toutes les procédures.
- Procédures utilisées par le package ETL pour migrer les données intermédiaires dans les tables d’entrepôt de données - toutes les procédures de migration *.
- `PopulateDateDimensionForYear` -Prend une année et s’assure que toutes les dates de cette année sont renseignés dans le `Dimension.Date` table.

### <a name="sequences-schema"></a>Schéma de séquences

Procédures pour configurer les séquences dans la base de données.

|Procédure|Fonction|
|-----------------------------|---------------------|
|ReseedAllSequences|Appelle la procédure `ReseedSequenceBeyondTableValue` pour toutes les séquences.|
|ReseedSequenceBeyondTableValue|Utilisé pour repositionner la valeur de la séquence suivante au-delà de la valeur dans une table qui utilise la même séquence. (Comme un `DBCC CHECKIDENT` pour l’équivalent de colonnes d’identité pour les séquences, mais potentiellement plusieurs tables.)|
