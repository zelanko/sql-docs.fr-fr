---
title: Générer des données - base de données exemple SQL WideWorldImporters | Documents Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
robots: noindex,nofollow
ms.openlocfilehash: 1530d3f517cc449ee77d6466904d9460483b725a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="wideworldimporters-data-generation"></a>Génération de données WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Les versions des bases de données WideWorldImporters et WideWorldImportersDW contient des données à partir de janvier 2013 1, le jour de ces bases de données ont été générées.

Lorsque vous utilisez les bases de données d’exemple, il peut être utile d’inclure des exemples de données les plus récentes.

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

Cette instruction ajoute des ventes de l’exemple et les données d’achat dans la base de données, jusqu'à la date actuelle. Il génère la progression des données de génération par jour. Il peut prendre environ 10 minutes pour chaque année qui a besoin de données. Il existe des différences dans les données générées entre les exécutions, étant donné un facteur aléatoire dans la génération de données.

Pour augmenter ou diminuer la quantité de données générées, en termes de commandes par jour, modifiez la valeur pour le paramètre `@AverageNumberOfCustomerOrdersPerDay`. Les paramètres `@SaturdayPercentageOfNormalWorkDay` et `@SundayPercentageOfNormalWorkDay` sont utilisées pour déterminer le volume de commandes pour les jours de week-end.

## <a name="importing-generated-data-in-wideworldimportersdw"></a>L’importation des données générées dans WideWorldImportersDW

Pour importer les exemples de données jusqu'à la date actuelle dans la base de données OLAP WideWorldImportersDW, procédez comme suit :

1. Exécuter la logique de génération de données dans la base de données WideWorldImporters OLTP, à l’aide de la procédure ci-dessus.
2. Si vous ne le n'avez pas encore fait, installez une nouvelle version de la base de données WideWorldImportersDW. Pour obtenir des instructions d’installation, **WideWorldImporters Installation et la Configuration**.
3. Réamorcer la base de données OLAP en exécutant l’instruction suivante dans la base de données :

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Exécuter le package SSIS **ETL.ispac quotidienne** pour importer les données dans la base de données OLAP. Pour obtenir des instructions sur la façon d’exécuter la tâche ETL, voir **WideWorldImporters ETL Workflow**.

## <a name="generating-data-in-wideworldimportersdw-for-performance-testing"></a>Génération de données dans WideWorldImportersDW au test des performances

WideWorldImportersDW a la possibilité d’augmenter la taille des données, à des fins de tests de performances, par exemple avec columnstore cluster arbitrairement.

L’une des difficultés est de conserver la taille du téléchargement assez petit pour télécharger facilement, mais suffisamment pour illustrer les fonctionnalités de performances de SQL Server. Par exemple, des avantages significatifs pour les index columnstore se produisent uniquement lorsque vous travaillez avec un plus grand nombre de lignes. 

La procédure `Application.Configuration_PopulateLargeSaleTable` peut être utilisé pour augmenter considérablement le nombre de lignes dans la `Fact.Sale` table. Notez que les lignes sont insérées dans l’année 2012 pour éviter toute collision avec les données existantes quatre coins du monde commençant le 1er janvier 2013.

### <a name="procedure-details"></a>Détails de la procédure

#### <a name="name"></a>Nom : 

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Paramètres :

  `@EstimatedRowsFor2012` **bigint** (valeur par défaut 12000000)

#### <a name="result"></a>Résultat :

Approximativement le nombre de lignes requis est inséré dans le `Fact.Sale` table dans l’année 2012. La procédure limite artificiellement le nombre de lignes par jour à 50 000. Cette limitation a pu être modifiée, mais il n’y figure afin d’éviter overinflations accidentelles de la table.

En outre, la procédure s’applique l’indexation de columnstore en cluster, si elle n’a pas déjà été appliqué.
