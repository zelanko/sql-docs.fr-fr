---
title: Catalogue de base de données WideWorldImporters OLTP - SQL | Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d98e87d18d76162e5bf9dcb4779a8bc7fec74385
ms.sourcegitcommit: c19696d3d67161ce78aaa5340964da3256bf602d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2018
ms.locfileid: "52617622"
---
# <a name="wideworldimporters-database-catalog"></a>Catalogue de base de données WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
La base de données WideWorldImporters contient toutes les les informations sur les transactions et quotidien des données pour les achats et, ainsi que les données de capteur de véhicules et les salles à froid.

## <a name="schemas"></a>Schémas

WideWorldImporters utilise des schémas à des fins différentes, telles que le stockage des données, définir comment les utilisateurs peuvent accéder aux données et fournissant des objets pour l’intégration et le développement de l’entrepôt de données.

### <a name="data-schemas"></a>Schémas de données

Ces schémas contiennent les données. Un nombre de tables est nécessaires à tous les autres schémas et se trouvent dans le schéma d’Application.

|schéma|Description|
|-----------------------------|---------------------|
|Application|Les utilisateurs de l’application, les contacts et les paramètres. Il contient également des tables de référence avec des données qui sont utilisées par plusieurs schémas|
|Purchasing|Élément du stock achats à partir des fournisseurs et des détails sur les fournisseurs.|  
|Ventes|Stock élément vente aux clients de vente au détail et plus d’informations sur les clients et les ventes de personnes. |  
|Warehouse|Inventaire d’élément de stock et les transactions.|  

### <a name="secure-access-schemas"></a>Schémas d’accès sécurisé

Ces schémas sont utilisés pour les applications externes qui ne sont pas autorisées à accéder directement aux tables de données. Elles contiennent des vues et procédures stockées utilisées par des applications externes.

|schéma|Description|
|-----------------------------|---------------------|
|Site Web|Tous les accès à la base de données depuis le site Web d’entreprise consiste à utiliser de ce schéma.|
|Rapports|Tous les accès à la base de données à partir de rapports Reporting Services sont à ce schéma.|
|Power BI|Tous les accès à la base de données à partir de tableaux de bord Power BI via la passerelle d’entreprise consiste à utiliser de ce schéma.|

Notez que les rapports Power BI et les schémas ne sont pas utilisés dans la version initiale de la base de données. Toutefois, les exemples de tous les Reporting Services et Power BI reposant sur cette base de données sont encouragés à utiliser ces schémas.

### <a name="development-schemas"></a>Schémas de développement

Schémas à usage spécial

|schéma|Description|
|-----------------------------|---------------------|
|Intégration|Objets et les procédures requises pour l’intégration de l’entrepôt de données (par exemple, migrer les données vers la base de données WideWorldImportersDW).|
|Séquences|Contient des séquences utilisées par toutes les tables dans l’application.|

## <a name="tables"></a>Tables

Toutes les tables dans la base de données sont dans les schémas de données.

### <a name="application-schema"></a>Schéma d’application

Détails des paramètres et des personnes (utilisateurs et contacts), ainsi que des tables de référence communes (communes à plusieurs autres schémas).

|Table de charge de travail|Description|
|-----------------------------|---------------------|
|SystemParameters|Contient des paramètres configurables de l’échelle du système.|
|Personnes|Contient les noms d’utilisateur, informations de contact, pour tous ceux qui utilisent l’application et pour les personnes gérant le Wide World Importers à des organisations clientes. Cela inclut le personnel, les clients, les fournisseurs et les autres contacts. Pour les personnes qui ont reçu l’autorisation d’utiliser le système ou un site Web, les informations comprennent des détails de connexion.|
|Villes|Il existe de nombreuses adresses stockées dans le système, pour les personnes, les adresses de livraison d’organisation de client, collecte d’adresses à des fournisseurs, etc. Chaque fois qu’une adresse est stockée, il existe une référence à une ville dans cette table. Il existe également un emplacement spatial pour chaque ville.|
|StateProvinces|Villes font partie des États ou provinces. Cette table contient des détails d'entre eux, y compris les données spatiales qui décrivent les limites de chaque état ou la province.|
|Pays|Les États ou Provinces font partie du pays. Cette table contient des détails d'entre eux, y compris les données spatiales décrit les limites de chaque pays.|
|DeliveryMethods|Choix pour assurer des articles en stock (par exemple, / van camion, post, pickup, expédition par courrier, etc.)|
|PaymentMethods|Les choix pour les modes de paiement (par exemple, en espèces, chèque, TEF, etc.)|
|TransactionTypes|Types de client, fournisseur ou les transactions boursières (par exemple, facture, note de crédit, etc.)|

### <a name="purchasing-schema"></a>Schéma d’achat

Détails des fournisseurs et des achats de l’élément du stock.

|Table de charge de travail|Description|
|-----------------------------|---------------------|
|Suppliers|Table de l’entité principale pour les fournisseurs (organisations)|
|SupplierCategories|Catégories pour les fournisseurs (par exemple, attrapes, jouets, vêtements, empaquetage, etc.).|
|SupplierTransactions|Toutes les transactions financières qui sont liées au fournisseur (factures, paiements)|
|PurchaseOrders|Détails du fournisseur de bons de commande|
|PurchaseOrderLines|Lignes de détails de fournisseur bons de commande|

 
### <a name="sales-schema"></a>Schéma de ventes

Détails des clients, les vendeurs et des ventes de l’élément du stock.

|Table de charge de travail|Description|
|-----------------------------|---------------------|
|Customers|Tables de l’entité principale pour les clients (entreprises ou les particuliers)|
|CustomerCategories|Catégories pour les clients (ie fantaisie magasins, supermarchés, etc.)|
|BuyingGroups|Des organisations clientes peuvent faire partie de groupes qui exercée supérieur pouvoir d’achat|
|CustomerTransactions|Toutes les transactions financières qui sont liés au client (factures, paiements)|
|SpecialDeals|Tarification spéciale. Cela peut inclure des prix fixes, de la remise en dollars ou en pourcentage de remise.|
|Orders|Détail des commandes client|
|OrderLines|Lignes de détails de commandes des clients|
|Factures|Détails des factures client|
|InvoiceLines|Lignes de détails de factures clients|

### <a name="warehouse-schema"></a>Schéma d’entrepôt

Détails de stock, leurs exploitations et aux transactions.

|Table de charge de travail|Description|
|-----------------------------|---------------------|
|StockItems|Table de l’entité principale pour les articles en stock|
|StockItemHoldings|Colonnes non temporelle pour les articles en stock. Il s’agit des colonnes mises à jour fréquemment.|
|StockGroups|Groupes pour classer des articles en stock (par exemple, attrapes, toys, attrapes alimentaires, etc.)|
|StockItemStockGroups|Les articles en stock sont dans lequel stock regroupe (plusieurs à plusieurs)|
|Couleurs|Articles en stock peuvent avoir (éventuellement) les couleurs|
|PackageTypes|Façons dont des articles en stock peut être empaqueté (par exemple, zone, carton, palettes, kg, etc.|
|StockItemTransactions|Transactions couvrant tous les mouvements de tous les éléments de stock (réception, vente, d’annulation)|
|VehicleTemperatures|Températures régulièrement enregistrées de refroidisseurs de véhicule|
|ColdRoomTemperatures|Enregistré régulièrement les températures de refroidisseurs de chambre froide|


## <a name="design-considerations"></a>Considérations de conception

Conception de base de données est subjective et il n’existe aucun moyen de bonne ou de mauvaise conception d’une base de données. Les schémas et les tables dans cette base de données montrent des idées pour comment vous pouvez concevoir votre propre base de données.

### <a name="schema-design"></a>Conception de schéma

WideWorldImporters utilise un petit nombre de schémas afin qu’il soit facile à comprendre le système de base de données et de démontrer les principes de base de données.  

Dans la mesure du possible, la base de données regroupe les tables qui sont fréquemment interrogées ensemble dans le même schéma pour réduire la complexité de la jointure.

Le schéma de base de données a été généré par le code basé sur une série de tables de métadonnées dans une autre base de données WWI_Preparation. Ainsi, WideWorldImporters un très haut niveau de cohérence de conception, la cohérence d’affectation de noms et souci d’exhaustivité. Pour plus d’informations sur la façon dont le schéma a été généré, consultez le code source : [à l’échelle du-world-Wide importers/wwi-base de données-scripts](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

### <a name="table-design"></a>Création de table

- Toutes les tables ont des clés primaires de colonne unique par souci de simplicité de jointure.
- Tous les schémas, tables, colonnes, index et contraintes de validation ont une Description de propriété qui peut être utilisée pour identifier l’objectif de l’objet ou d’une colonne étendue. Tables optimisées en mémoire sont une exception à cela dans la mesure où ils ne prennent actuellement en charge les propriétés étendues.
- Toutes les clés étrangères sont indexés automatiquement sauf s’il existe un autre index non cluster qui a le même composant de gauche.
- Numérotation automatique dans les tables est basée sur des séquences. Ces séquences sont plus faciles de travailler avec des environnements similaires à des colonnes d’identité et de serveurs liés. Tables optimisées en mémoire utilisent des colonnes d’identité dans la mesure où ils ne prennent pas en charge dans SQL Server 2016.
- Une seule séquence (TransactionID) est utilisée pour ces tables : CustomerTransactions, SupplierTransactions et StockItemTransactions. Cet exemple montre comment un ensemble de tables peut avoir une seule séquence.
- Certaines colonnes ont des valeurs par défaut appropriées.

### <a name="security-schemas"></a>Schémas de sécurité

Pour la sécurité, WideWorldImporters n’autorise pas les applications externes accéder directement aux schémas de données. Pour isoler l’accès, WideWorldImporters utilise les schémas d’accès de sécurité qui ne possèdent pas de données, mais qui contiennent des vues et procédures stockées. Applications externes utilisent les schémas de sécurité pour récupérer les données qu’ils sont autorisés à afficher.  De cette façon, les utilisateurs peuvent uniquement exécuter les procédures stockées et vues dans les schémas d’accès sécurisé

Par exemple, cet exemple inclut des tableaux de bord Power BI. Une application externe accède à ces tableaux de bord Power BI à partir de la passerelle Power BI en tant qu’utilisateur qui a l’autorisation en lecture seule sur le schéma de Power BI.  Pour une autorisation en lecture seule, l’utilisateur doit uniquement l’autorisation SELECT et EXECUTE sur le schéma de Power BI. Un administrateur de base de données au WWI affecte ces autorisations en fonction des besoins.

## <a name="stored-procedures"></a>Procédures stockées

Les procédures stockées sont organisées dans des schémas. La plupart des schémas sont utilisés pour la configuration ou à des fins d’exemple.

Le `Website` schéma contient les procédures stockées qui peuvent être utilisées par un serveur Web frontal.

Le `Reports` et `PowerBI` schémas sont conçus pour reporting services et à des fins de Power BI. Toutes les extensions de l’exemple sont encouragées à utiliser ces schémas à des fins de création de rapports.

### <a name="website-schema"></a>Schéma de site Web

Voici les procédures utilisées par une application cliente, par exemple un serveur Web frontal.

|Procédure|Objectif|
|-----------------------------|---------------------|
|ActivateWebsiteLogon|Permet à une personne (à partir de `Application.People`) d’accéder au site Web.|
|ChangePassword|Modifie un mot de passe (pour les utilisateurs qui n’utilisent pas de mécanismes d’authentification externe).|
|InsertCustomerOrders|Permet l’insertion d’une ou plusieurs commandes client (y compris les lignes de commande).|
|InvoiceCustomerOrders|Prend une liste de commandes à facturer et traite les factures.|
|RecordColdRoomTemperatures|Prend une liste de données de capteur, comme un paramètre table (TVP) et applique les données à le `Warehouse.ColdRoomTemperatures` table temporelle.|
|RecordVehicleTemperature|Prend un tableau JSON et l’utilise pour mettre à jour `Warehouse.VehicleTemperatures`.|
|SearchForCustomers|Recherche pour les clients par nom ou une partie du nom (le nom de société ou le nom de la personne).|
|SearchForPeople|Recherches de personnes par nom ou une partie du nom.|
|SearchForStockItems|Recherche des éléments de stock par nom ou une partie du nom ou de commentaires de marketing.|
|SearchForStockItemsByTags|Recherche des éléments de stock par balises.|
|SearchForSuppliers|Recherche de fournisseurs par nom ou une partie du nom (le nom de société ou le nom de la personne).|

### <a name="integration-schema"></a>Schéma d’intégration

Les procédures stockées dans ce schéma sont utilisées par le processus ETL. Ils obtiennent les données nécessaires à partir des tables différentes pour l’intervalle de temps requis par le [package ETL](wide-world-importers-perform-etl.md).

### <a name="dataloadsimulation-schema"></a>Schéma de DataLoadSimulation

Simule une charge de travail qui insère les ventes et les achats. La procédure stockée principale est `PopulateDataToCurrentDate`, qui est utilisé pour insérer des exemples de données jusqu'à la date actuelle.

|Procédure|Objectif|
|-----------------------------|---------------------|
|Configuration_ApplyDataLoadSimulationProcedures|Recrée les procédures nécessaires pour les données de simulation de charge. Cela est nécessaire pour mettre les données jusqu'à la date actuelle.|
|Configuration_RemoveDataLoadSimulationProcedures|Cette opération supprime les procédures à nouveau une fois la simulation de données est terminée.|
|DeactivateTemporalTablesBeforeDataLoad|Supprime la nature temporelle de toutes les tables temporelles et, le cas échéant, s’applique un déclencheur afin que peut être modifié comme si elles ont été appliquées à une date antérieure que ne l’autorisent les tables temporelles sys.|
|PopulateDataToCurrentDate|Utilisé pour importer les données jusqu'à la date actuelle. Doit être exécutée avant les autres options de configuration après la restauration de la base de données à partir d’une sauvegarde initiale.|
|ReactivateTemporalTablesAfterDataLoad|Rétablit les tables temporelles, y compris la vérification de cohérence des données. (Supprime les déclencheurs associés).|


### <a name="application-schema"></a>Schéma d’application

Ces procédures sont utilisées pour configurer l’exemple. Ils sont utilisés pour appliquer les fonctionnalités de l’édition enterprise à la version Édition standard de l’exemple et également ajouter l’audit et l’indexation de texte intégral.

|Procédure|Objectif|
|-----------------------------|---------------------|
|AddRoleMemberIfNonexistant|Ajoute un membre à un rôle si le membre n’est pas déjà dans le rôle|
|Configuration_ApplyAuditing|Ajoute l’audit. L’audit du serveur est appliquée pour les bases de données standard edition ; l’audit de base de données supplémentaire est ajouté pour enterprise edition.|
|Configuration_ApplyColumnstoreIndexing|S’applique à l’indexation pour columnstore `Sales.OrderLines` et `Sales.InvoiceLines` et réindexe en conséquence.|
|Configuration_ApplyFullTextIndexing|S’applique à des index de texte intégral `Application.People`, `Sales.Customers`, `Purchasing.Suppliers`, et `Warehouse.StockItems`. Remplace `Website.SearchForPeople`, `Website.SearchForSuppliers`, `Website.SearchForCustomers`, `Website.SearchForStockItems`, `Website.SearchForStockItemsByTags` avec les procédures de remplacement qui utilisent l’indexation de texte intégral.|
|Configuration_ApplyPartitioning|S’applique le partitionnement de table à `Sales.CustomerTransactions and `'Purchasing.SupplierTransactions et réorganise les index en fonction.|
|Configuration_ApplyRowLevelSecurity|S’applique la sécurité au niveau ligne pour filtrer les clients par sales territory les rôles associés.|
|Configuration_ConfigureForEnterpriseEdition|S’applique l’indexation columnstore, recherche en texte intégral, en mémoire, polybase et partitionnement.|
|Configuration_EnableInMemory|Ajoute un groupe de fichiers mémoire optimisé (lorsque vous ne travaillez pas dans Azure), remplace `Warehouse.ColdRoomTemperatures`, `Warehouse.VehicleTemperatures` avec les équivalents en mémoire et la migration des données, recrée le `Website.OrderIDList`, `Website.OrderList`, `Website.OrderLineList`, `Website.SensorDataList` types avec des tables équivalents de mémoire optimisée, supprime et recrée les procédures `Website.InvoiceCustomerOrders`, `Website.InsertCustomerOrders`, et `Website.RecordColdRoomTemperatures` qui utilise ces types de table.|
|Configuration_RemoveAuditing|Supprime la configuration de l’audit.|
|Configuration_RemoveRowLevelSecurity|Supprime la configuration de la sécurité au niveau ligne (cela est nécessaire pour les modifications apportées aux tables associées).|
|CreateRoleIfNonExistant|Crée un rôle de base de données si elle n’existe pas déjà.|


### <a name="sequences-schema"></a>Schéma de séquences

Procédures pour configurer les séquences dans la base de données.

|Procédure|Objectif|
|-----------------------------|---------------------|
|ReseedAllSequences|Appelle la procédure ReseedSequenceBeyondTableValue pour toutes les séquences.|
|ReseedSequenceBeyondTableValue|Utilisé pour repositionner la valeur de la séquence suivante au-delà de la valeur dans une table qui utilise la même séquence. (Par exemple, un DBCC CHECKIDENT pour équivalent de colonnes d’identité pour les séquences, mais potentiellement plusieurs tables).|
