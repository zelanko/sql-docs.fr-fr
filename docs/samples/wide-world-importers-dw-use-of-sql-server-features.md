---
title: Base de données OLAP de WideWorldImporters - utilisation de SQL Server | Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7c3158def05148941105867f24205b199e6c6dba
ms.sourcegitcommit: 89983916c39b1c3ecf340de6a4febb2ed33129e4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "36964261"
---
# <a name="wideworldimportersdw-use-of-sql-server-features-and-capabilities"></a>Utilisation de WideWorldImportersDW de fonctionnalités de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
WideWorldImportersDW est conçue pour présenter la plupart des principales fonctionnalités de SQL Server qui conviennent pour l’entreposage des données et d’analytique. Voici une liste des fonctionnalités de SQL Server et fonctionnalités et une description de la façon dont ils sont utilisés dans WideWorldImportersDW.

## <a name="polybase"></a>PolyBase

[S’applique à SQL Server (2016 et versions ultérieures)]

PolyBase est utilisé pour combiner les informations de vente à partir de WideWorldImportersDW avec un jeu de données publiques sur les données démographiques pour comprendre les villes peuvent présenter un intérêt pour l’expansion supplémentaire des ventes.

Pour activer l’utilisation de PolyBase dans la base de données, vérifiez qu’il est installé et exécutez la procédure stockée suivante dans la base de données :

    EXEC [Application].[Configuration_ApplyPolybase]

Cela créera une table externe `dbo.CityPopulationStatistics` qui fait référence à un jeu de données publiques qui contient les données de la population des villes aux États-Unis, hébergé dans le stockage blob Azure. Il est conseillé d’examiner le code dans la procédure stockée pour comprendre le processus de configuration. Si vous souhaitez héberger vos propres données dans stockage blob Azure et conservez-la en lieu sûr à partir de l’accès public général, vous devez effectuer les étapes de configuration supplémentaires. La requête suivante retourne les données à partir de ce jeu de données externe :

    SELECT CityID, StateProvinceCode, CityName, YearNumber, LatestRecordedPopulation FROM dbo.CityPopulationStatistics;

Pour comprendre les villes peuvent présenter un intérêt pour l’expansion supplémentaire, la requête suivante examine le taux de croissance de villes et retourne les villes de plus grande des 100 premiers avec une croissance importante, et où Wide World Importers ne dispose pas d’une présence commerciale. La requête implique une jointure entre la table distante `dbo.CityPopulationStatistics` et la table locale `Dimension.City`et un filtre de la table locale `Fact.Sales`.

    WITH PotentialCities
    AS
    (
        SELECT cps.CityName,
               cps.StateProvinceCode,
               MAX(cps.LatestRecordedPopulation) AS PopulationIn2016,
               (MAX(cps.LatestRecordedPopulation) - MIN(cps.LatestRecordedPopulation)) * 100.0
                   / MIN(cps.LatestRecordedPopulation) AS GrowthRate
        FROM dbo.CityPopulationStatistics AS cps
        WHERE cps.LatestRecordedPopulation IS NOT NULL
        AND cps.LatestRecordedPopulation <> 0
        GROUP BY cps.CityName, cps.StateProvinceCode
    ),
    InterestingCities
    AS
    (
        SELECT DISTINCT pc.CityName,
                        pc.StateProvinceCode,
                        pc.PopulationIn2016,
                        FLOOR(pc.GrowthRate) AS GrowthRate
        FROM PotentialCities AS pc
        INNER JOIN Dimension.City AS c
        ON pc.CityName = c.City
        WHERE GrowthRate > 2.0
        AND NOT EXISTS (SELECT 1 FROM Fact.Sale AS s WHERE s.[City Key] = c.[City Key])
    )
    SELECT TOP(100) CityName, StateProvinceCode, PopulationIn2016, GrowthRate
    FROM InterestingCities
    ORDER BY PopulationIn2016 DESC;

## <a name="clustered-columnstore-indexes"></a>Index columnstore cluster

(Version complète de l’exemple)

Index de Columnstore en cluster (ICC) sont utilisés avec toutes les tables de faits, pour réduire l’encombrement du stockage et améliorer les performances de requête. À l’aide de la CCI, le stockage de base pour les tables de faits utilise la compression de la colonne.

Index non cluster sont utilisés en haut de l’index columnstore en cluster, afin de faciliter la clé primaire et les contraintes de clé étrangère. Ces contraintes ont été ajoutées en dehors d’une multitude de précaution : le processus ETL des sources de données à partir de la base de données WideWorldImporters, qui a des contraintes pour appliquer l’intégrité. Suppression des contraintes de clé primaires et étrangères et leurs index prise en charge, réduit l’encombrement de stockage des tables de faits.

**Taille des données**

La base de données a limité la taille des données, afin de faciliter télécharger et installer l’exemple. Toutefois, pour voir les avantages de performances réelles des index columnstore, vous pouvez utiliser un plus grand jeu de données.

Vous pouvez exécuter l’instruction suivante pour augmenter la taille de la `Fact.Sales` table en insérant un autre 12 millions de lignes d’exemples de données. Ces lignes sont toutes insérées pour l’année 2012, qu’il n’y ait aucune interférence avec le processus ETL.

    EXECUTE [Application].[Configuration_PopulateLargeSaleTable]

Cette instruction prendra environ 5 minutes pour s’exécuter. Pour insérer plus de 12 millions de lignes, passez le nombre souhaité de lignes à insérer en tant que paramètre à cette procédure stockée.

Pour comparer les performances des requêtes avec et sans columnstore, vous pouvez supprimer ou recréez l’index columnstore en cluster.

Pour supprimer l’index :

    DROP INDEX [CCX_Fact_Order] ON [Fact].[Order]

Pour recréer :

    CREATE CLUSTERED COLUMNSTORE INDEX [CCX_Fact_Order] ON [Fact].[Order]

## <a name="partitioning"></a>Partitionnement

(Version complète de l’exemple)

Taille des données dans un entrepôt de données peut devenir très volumineux. Par conséquent, il est recommandé d’utiliser le partitionnement pour gérer le stockage des grandes tables dans la base de données.

Toutes les tables de faits plus volumineux sont partitionnés par année. La seule exception est `Fact.Stock Holdings`, qui n’est pas basée sur la date et a taille des données limitées par rapport à d’autres tables de faits.

La fonction de partition utilisée pour les tables partitionnées tout est `PF_Date`, et le schéma de partition utilisé est `PS_Date`.

## <a name="in-memory-oltp"></a>OLTP en mémoire

(Version complète de l’exemple)

WideWorldImportersDW utilise les tables optimisées en mémoire SCHEMA_ONLY pour les tables intermédiaires. Tous les `Integration.` * `_Staging` tables sont des tables optimisées en mémoire SCHEMA_ONLY.

L’avantage de tables SCHEMA_ONLY est qu’ils ne sont pas enregistrés et ne nécessitent pas d’accès disque. Cela améliore les performances du processus ETL. Étant donné que ces tables ne sont pas enregistrés, leur contenu est perdu en cas de panne. Toutefois, la source de données étant toujours disponible, le processus ETL peut simplement être redémarré si une défaillance se produit.
