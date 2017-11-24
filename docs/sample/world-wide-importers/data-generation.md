---
title: "Génération de données | Documents Microsoft"
ms.custom: 
ms.date: 01/30/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.prod: world-wide-importers
ms.prod_service: sql-non-specified
ms.service: samples
ms.component: 
ms.technology: " database-engine "
ms.topic: article
ms.assetid: f387273b-8b5f-4687-b033-09499ea2d68f
caps.latest.revision: "4"
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: cb816c1d41f0f5b77aa1dd6434cf912a6fbf4592
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="wideworldimporters-data-generation"></a>Génération de données WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Les versions des bases de données WideWorldImporters et WideWorldImportersDW contient des données en commençant le 1er de janvier 2013, le jour de ces bases de données ont été générées.

Si les bases de données exemple sont utilisés à une date ultérieure, à des fins de démonstration ou illustration, il peut être utile d’inclure des exemples de données les plus récentes dans la base de données.

## <a name="data-generation-in-wideworldimporters"></a>Génération de données dans WideWorldImporters

Pour générer des exemples de données jusqu'à la date actuelle, procédez comme suit :

1. Si vous ne le n'avez pas encore fait, installez une nouvelle version de la base de données WideWorldImporters. Pour obtenir des instructions d’installation, **WideWorldImporters Installation et la Configuration**.
2. Dans la base de données, exécutez l’instruction suivante :

```
    EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
        @AverageNumberOfCustomerOrdersPerDay = 60,
        @SaturdayPercentageOfNormalWorkDay = 50,
        @SundayPercentageOfNormalWorkDay = 0,
        @IsSilentMode = 1,
        @AreDatesPrinted = 1;
```

Cette instruction ajoute des ventes de l’exemple et les données d’achat dans la base de données, jusqu'à la date actuelle. Il génère la progression des données de génération par jour. Il prendra environ 10 minutes pour chaque année qui a besoin de données. Notez qu’il existe des différences dans les données générées entre les exécutions, étant donné un facteur aléatoire dans la génération de données.

Pour augmenter ou diminuer la quantité de données générées, en termes de commandes par jour, modifiez la valeur pour le paramètre `@AverageNumberOfCustomerOrdersPerDay`. Les paramètres `@SaturdayPercentageOfNormalWorkDay` et `@SundayPercentageOfNormalWorkDay` sont utilisées pour déterminer le volume de commandes pour les jours de week-end.

## <a name="importing-generated-data-in-wideworldimportersdw"></a>L’importation des données générées dans WideWorldImportersDW

Pour importer les exemples de données jusqu'à la date actuelle dans la base de données OLAP WideWorldImportersDW, procédez comme suit :

1. Exécuter la logique de génération de données dans la base de données WideWorldImporters OLTP, à l’aide de la procédure ci-dessus.
2. Si vous ne le n'avez pas encore fait, installez une nouvelle version de la base de données WideWorldImportersDW. Pour obtenir des instructions d’installation, **WideWorldImporters Installation et la Configuration**.
3. Réamorcer la base de données OLAP en exécutant l’instruction suivante dans la base de données :

```
    EXECUTE [Application].Configuration_ReseedETL
```

4. Exécuter le package SSIS **ETL.ispac quotidienne** pour importer les données dans la base de données OLAP. Pour obtenir des instructions sur la façon d’exécuter la tâche ETL, voir **WideWorldImporters ETL Workflow**.

## <a name="generating-data-in-wideworldimportersdw-for-performance-testing"></a>Génération de données dans WideWorldImportersDW au test des performances

WideWorldImportersDW a la possibilité d’augmenter la taille des données, à des fins de tests de performances, par exemple avec columnstore cluster arbitrairement.

L’une des difficultés lors de l’expédition d’un échantillon de quatre coins du monde consiste à conserver la taille du téléchargement assez petites pour être distribuable mais suffisamment grand illustrer les fonctionnalités de performances de SQL Server. Une zone où il s’agit d’une difficulté particulière est lorsque vous travaillez avec des index columnstore. Des avantages significatifs sont fournis uniquement lorsque vous travaillez avec un plus grand nombre de lignes. 

La procédure `Application.Configuration_PopulateLargeSaleTable` peut être utilisé pour augmenter considérablement le nombre de lignes dans la `Fact.Sale` table. Notez que les lignes sont insérées dans l’année 2012 pour éviter toute collision avec les données existantes quatre coins du monde commençant le 1er janvier 2013.

### <a name="procedure-details"></a>Détails de la procédure

#### <a name="name"></a>Nom : 

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Paramètres :

  `@EstimatedRowsFor2012`**bigint** (valeur par défaut 12000000)

#### <a name="result"></a>Résultat :

Approximativement le nombre de lignes requis est inséré dans le `Fact.Sale` table dans l’année 2012. La procédure limite artificiellement le nombre de lignes par jour à 50 000. Cela a pu être modifiée mais il afin d’éviter overinflations accidentelle de la table.

En outre, la procédure s’applique l’indexation de columnstore en cluster, si elle n’a pas déjà été appliqué.
