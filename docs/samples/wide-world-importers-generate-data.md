---
title: Générer des données - base de données exemple SQL WideWorldImporters | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 38ba117051ad10d788c2357dfb70d36c2b5e50d1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091269"
---
# <a name="wideworldimporters-data-generation"></a>Génération de données WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Les versions des bases de données WideWorldImporters et WideWorldImportersDW ont des données à partir du 1er janvier 2013, jusqu'à la journée à laquelle les bases de données ont été générées.

Lorsque vous utilisez ces bases de données d’exemple, vous souhaiterez peut-être incluent des exemples de données plus récentes.

## <a name="data-generation-in-wideworldimporters"></a>Génération de données à WideWorldImporters

Pour générer les exemples de données jusqu'à la date actuelle :

1. Si vous n’avez pas fait, installez une nouvelle version de la base de données WideWorldImporters. Pour obtenir des instructions d’installation, consultez [Installation et configuration](wide-world-importers-oltp-install-configure.md).
2. Exécutez l’instruction suivante dans la base de données :

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    Cette instruction ajoute des exemples de ventes et les données d’achat de la base de données, jusqu'à la date actuelle. Il affiche la progression de la génération de données par jour. Génération de données peut prendre environ 10 minutes pour chaque année qui a besoin de données. En raison d’un facteur aléatoire dans la génération de données, il existe des différences dans les données qui sont générées entre les exécutions.

    Pour augmenter ou diminuer la quantité de données générées pour les commandes par jour, modifiez la valeur pour le paramètre `@AverageNumberOfCustomerOrdersPerDay`. Utilisez les paramètres `@SaturdayPercentageOfNormalWorkDay` et `@SundayPercentageOfNormalWorkDay` pour déterminer le volume de commandes pour les jours du week-end.

## <a name="import-generated-data-in-wideworldimportersdw"></a>Données d’importation générée dans WideWorldImportersDW

Pour importer les exemples de données jusqu'à la date actuelle dans la base de données WideWorldImportersDW OLAP :

1. Exécuter la logique de génération de données dans la base de données WideWorldImporters OLTP en suivant les étapes de la section précédente.
2. Si vous n’avez pas encore fait, installez une nouvelle version de la base de données WideWorldImportersDW. Pour obtenir des instructions d’installation, consultez [Installation et configuration](wide-world-importers-oltp-install-configure.md).
3. Réattribuer la base de données OLAP en exécutant l’instruction suivante dans la base de données :

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Exécutez le *ETL.ispac quotidienne* package SQL Server Integration Services pour importer les données dans la base de données OLAP. Pour savoir comment exécuter la tâche ETL, consultez [flux de travail ETL de WideWorldImporters](wide-world-importers-perform-etl.md).

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>Générer des données dans WideWorldImportersDW pour tester les performances

WideWorldImportersDW arbitrairement peut augmenter la taille des données pour tester les performances. Par exemple, il peut augmenter la taille des données à utiliser avec l’indexation columnstore en cluster.

Un des défis consiste à conserver la taille du téléchargement suffisamment petit pour télécharger facilement, mais suffisamment pour illustrer les fonctionnalités de performances de SQL Server. Par exemple, des avantages significatifs pour les index columnstore sont atteints uniquement lorsque vous travaillez avec un grand nombre de lignes. 

Vous pouvez utiliser la `Application.Configuration_PopulateLargeSaleTable` procédure pour augmenter le nombre de lignes dans le `Fact.Sale` table. Les lignes sont insérées dans l’année 2012 pour éviter toute collision avec les données de World Wide Importers existantes qui commence le 1er janvier 2013.

### <a name="procedure-details"></a>Détails de la procédure

#### <a name="name"></a>Nom

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Paramètres

  `@EstimatedRowsFor2012` **bigint** (valeur par défaut 12000000)

#### <a name="result"></a>Résultat

Environ le nombre requis de lignes est inséré dans la `Fact.Sale` table dans l’année 2012. La procédure limite artificiellement le nombre de lignes à 50 000 par jour. Vous pouvez modifier cette limitation, mais la limitation vous permet d’éviter les overinflations accidentelles de la table.

La procédure s’applique également à cluster columnstore, l’indexation s’il n’a pas déjà été appliqué.
