---
title: Importer et consolider les rapports d’évaluation de Data Migration Assistant (SQL Server) | Microsoft Docs
description: Apprenez à importer des rapports d’évaluation à partir de l’Assistant de Migration de données dans une base de données SQL Server et à consolider plusieurs rapports
ms.custom: ''
ms.date: 04/16/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: be9fc224093f0d5ae14372d4674a52589a2d4801
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781770"
---
# <a name="import-and-consolidate-data-migration-assistant-assessment-reports"></a>Importer et consolider les rapports d’évaluation de Data Migration Assistant

Vous pouvez utiliser la ligne de commande pour effectuer des évaluations de la migration en mode sans assistance, en commençant par v2.1 Data Migration Assistant. Cette fonctionnalité vous aide à exécuter les évaluations à l’échelle. Les résultats d’évaluation sous la forme d’un fichier CSV ou JSON.

Vous pouvez évaluer plusieurs bases de données dans une instanciation unique de l’utilitaire de ligne de commande Data Migration Assistant et exporter tous les résultats des évaluations dans un seul fichier JSON. Ou bien, vous pouvez évaluer une base de données au moment et ultérieurement consolider les résultats de ces plusieurs fichiers JSON dans une base de données SQL.

Pour plus d’informations sur la façon d’exécuter l’Assistant Migration des données à partir de la ligne de commande, consultez [exécuter Data Migration Assistant à partir de la ligne de commande](../dma/dma-commandline.md). 

## <a name="import-assessment-results-into-a-sql-server-database"></a>Importer les résultats d’évaluation dans une base de données SQL Server

Utilisez le script PowerShell disponible dans ce [référentiel Github](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant) pour importer les résultats d’évaluation à partir de fichiers JSON dans une base de données SQL Server.

> [!NOTE]
> PowerShell v5 ou version ultérieure est requis.

Lorsque vous exécutez le script, vous devez fournir les informations suivantes : 

- **nom_serveur**: nom de l’instance SQL Server que vous souhaitez importer l’évaluation des résultats à partir de fichiers JSON.

- **databaseName**: le nom de base de données importés pour les résultats.

- **jsonDirectory**: le dossier dans lequel les résultats d’évaluation enregistrées, un ou plusieurs fichiers JSON.

- **processTo**: SQLServer

Ajoutez les valeurs ci-dessus dans la section « Exécution de fonctions », comme suit.

```
dmaProcessor -serverName localhost \`\
-databaseName DMAReporting \`\
-jsonDirectory "C:\\temp\\DMACmd\\output\\" \`\
-processTo SQLServer
```

Le script PowerShell crée les objets suivants dans l’instance SQL que vous avez spécifié, si les objets n’existent pas déjà :

- **Base de données** – le nom fourni dans les paramètres PowerShell

  - Référentiel principal

- **Table** – rapports

  - Données création de rapports

- **Table** -BreakingChangeWeighting

  - Table de référence pour toutes les modifications avec rupture. Ici, vous pouvez définir vos propres valeurs de pondération pour influencer un classement de mise à niveau réussie de pourcentage (%) plus précis.

- **Vue** – UpgradeSuccessRanking\_OnPrem

  - Affichage comprenant un facteur de réussite pour chaque base de données être migrés en local.

- **Vue** – UpgradeSuccessRanking\_Azure

  - Affichage comprenant un facteur de réussite pour chaque base de données être migrés en local.

- **Procédure stockée** – JSONResults\_insérer

  - Utilisé pour importer des données à partir d’un fichier JSON dans SQL Server.

- **Procédure stockée** – AzureFeatureParityResults\_insérer

  - Utilisé pour importer les résultats de parité de fonctionnalité Azure à partir d’un fichier JSON dans SQL Server.

- **Type de table** – JSONResults

  - Utilisé pour stocker les résultats JSON pour les évaluations en local et passer à la JSONResults\_procédure stockée Insert

- **Type de table** – AzureFeatureParityResults

  - Utilisé pour stocker des résultats de parité pour les évaluations azure de la fonctionnalité Azure et passer à la AzureFeatureParityResults\_procédure stockée Insert

Le script PowerShell crée un **traitées** répertoire dans le répertoire que vous avez fourni et qui contient les fichiers JSON qui doivent être traitées.

Une fois le script terminé, les résultats sont importés dans la table, les rapports.

### <a name="viewing-the-results-in-sql-server"></a>Affichage des résultats dans SQL Server

Une fois que les données ont été chargées, connectez-vous à votre instance de SQL Server. Votre écran doit apparaître comme indiqué dans le graphique suivant :

![Rapports consolidés dans la base de données SQL Server](../dma/media/DMAReportingDatabase.png)

Le dbo. Tableau de rapports contient le contenu du fichier JSON dans sa forme brute.

## <a name="on-premises-upgrade-success-ranking"></a>Local mise à niveau de classement de réussite

Pour afficher une liste des bases de données et leur classement de réussite de pourcentage (%), sélectionnez le dbo. Vue de UpgradeSuccessRanking_OnPrem :

![Afficher les données dans UpgradeSuccessRaning_OnPrem](../dma/media/UpgradeSuccessRankingView.png)

Ici, vous pouvez voir pour une base de données quelle est la probabilité de réussite de mise à niveau pour les niveaux de compatibilité. Par conséquent, par exemple, la base de données HR a été évalué par rapport à des niveaux de compatibilité 100, 110, 120 et 130. Cette évaluation vous permet de voir la quantité de travail implique la migration vers une version ultérieure de SQL Server à partir de la version actuelle par la base de données.

Généralement les mesures que vous intéressent sont les modifications avec rupture combien il pour une base de données. Dans l’exemple précédent, vous pouvez voir que la base de données HR a un facteur de réussite de mise à niveau de 50 % pour les niveaux de compatibilité 100, 110, 120 et 130.

Cette mesure peut être influencée en modifiant les valeurs de pondération dans le dbo. Table BreakingChangeWeighting.

Dans l’exemple suivant, les efforts nécessaires lors de la résolution du problème de syntaxe dans la base de données ressources humaines sont considéré comme élevé donc la valeur 3 est affectée à **Effort**. Étant donné que cela ne vous prendrait long pour résoudre le problème de syntaxe, une valeur de 1 est assignée à **FixTime**. Étant donné que certains coûts serait impliquées dans la création de la modification, une valeur de 2 est assignée à **coût**. À l’aide de cette valeur change le Changerank combinée à 2.

> [!NOTE]
> Le calcul de score est sur une échelle de 1 à 5.  1 étant faible et 5 haute. En outre, le ChangeRank est une colonne calculée.

![Effort, FixTime et le coût des valeurs pour les problème de syntaxe](../dma/media/SyntaxIssueEffort.png)

Maintenant, dans cet exemple, lorsque vous interrogez le dbo. Vue UpgradeSuccessRanking_OnPrem, la mise à niveau pour réussir la base de données HR les dernières modifications a supprimé.

![Facteur de réussite de mise à niveau de base de données ressources humaines](../dma/media/UpgradeSuccessFactor_HR.png)

## <a name="azure-upgrade-success-ranking"></a>Classement de la réussite de mise à niveau Azure

Pour afficher la liste des bases de données à migrer vers Azure SQL DB et leur classement de réussite de pourcentage, sélectionnez le dbo. Vue de UpgradeSuccessRanking_Azure.

![Afficher les données dans UpgradeSuccessRanking_Azure](../dma/media/UpgradeSuccessRankingView_Azure.png)

Ici, vous êtes intéressé par la valeur MigrationBlocker. 100,00 signifie qu’il y a un rang de 100 % de réussite pour déplacer une base de données vers la base de données SQL Azure v12.

La différence avec cette vue est qu’il n’existe actuellement aucune substitution pour modifier la pondération de règles de blocage de migration.

Pour plus d’informations sur la création de rapports sur ces données à l’aide de Power BI, consultez [créer des rapports sur vos évaluations consolidées avec Power BI](../dma/dma-powerbiassesreport.md).
