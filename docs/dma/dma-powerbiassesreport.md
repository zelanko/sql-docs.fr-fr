---
title: Analyser les rapports d’évaluation de Data Migration Assistant consolidées avec Power BI (SQL Server) | Microsoft Docs
description: Découvrez comment utiliser Power BI pour analyser les rapports d’évaluation de Migration de données que vous avez importé et consolidés dans SQL Server
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: c00196468b846174bb73c8d82c691f482aa8b21e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63152583"
---
# <a name="analyze-consolidated-assessment-reports-created-by-data-migration-assistant-with-power-bi"></a>Analyser les rapports d’évaluation consolidée créés par l’Assistant Migration des données avec Power BI

Cet article décrit comment créer un rapport Power BI pour analyser les évaluations de migration consolidé.

Pour plus d’informations sur la consolidation des évaluations de migration créées par l’Assistant Migration des données, consultez [consolider des rapports d’évaluation](../dma/dma-consolidatereports.md).

## <a name="sample-power-bi-reports"></a>Exemples de rapports Power BI

Vous pouvez télécharger des exemples de rapports Power BI pour les évaluations de migration consolidée à partir de ce [référentiel Github](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant).

Les rapports suivants sont inclus : 

- [Tableau de bord](#dashboard-report)

  Inclut des statistiques d’instantané et un rapport détaillé.

- [Locale mise à niveau de disponibilité](#on-premises-upgrade-readiness-report)

  La source de données est la vue UpgradeSuccessRanking dans la base de données DMAReporting.  Ce rapport affiche le pourcentage de mise à niveau réussie pour vos bases de données évaluées.

- [Parité des fonctionnalités sur site](#on-premises-feature-parity-report)

  Présente les recommandations de fonctionnalité pour la version de SQL Server cible.

- [Préparation de mise à niveau de la base de données SQL Azure](#azure-sql-db-upgrade-readiness-report)

  La source de données est la vue UpgradeSuccessRanking dans la base de données DMAReporting.  Ce rapport affiche le pourcentage de mise à niveau réussie pour les bases de données évalué pour les migrations de base de données SQL Azure.

- [Fonctionnalités de base de données SQL non pris en charge Azure](#azure-sql-db-unsupported-features-report)

  Affiche les fonctionnalités dans vos bases de données existants qui ne sont pas pris en charge dans Azure SQL Database (V12).

Vous pouvez modifier ces rapports pour travailler avec votre environnement en modifiant la source de données dans Power BI. 

1. Sélectionnez la flèche vers le bas en regard **modifier les requêtes**, puis sélectionnez **paramètres de source de données**.

   ![Modifier le menu de requêtes, les paramètres de source de données](../dma/media/DataSourceSettings.png)

1. Sélectionnez **modifier la Source...** et entrez les valeurs de serveur et base de données.

   ![Base de données, serveur et modifier la source](../dma/media/ChangeSource.png)

1. Sélectionnez **OK**, puis sélectionnez **fermer**.

1. Actualisez vos rapports.

   ![Actualiser le rapport Power BI](../dma/media/RefreshReport.png)

### <a name="dashboard-report"></a>Rapport de tableau de bord

![Rapport de tableau de bord](../dma/media/DashboardReport.png)

Le tableau de bord affiche les détails de toutes vos évaluations. Vous pouvez utiliser les segments sur le côté gauche pour filtrer par instance ou de la base de données. Vous pouvez utiliser le graphique à barres pour explorer des catégories spécifiques pour voir où se situent les problèmes.

Pour Explorer, sélectionnez le cercle avec la flèche bas en haut à droite du graphique à barres.

![Extraction de la catégorie](../dma/media/CategoryDrillDown.png)

La séquence d’exploration vers le bas est définie comme indiqué dans l’image suivante (sous **axe**). Pour modifier la séquence, faites glisser les colonnes à l’ordre souhaité.

![Axe de graphique à barres, des visualisations](../dma/media/VisualizationsAxis.png)

Cette vue est encore plus efficace lorsque vous filtrez tout d’abord par une base de données spécifique, puis Explorez les problèmes d’une catégorie spécifique. Dans l’exemple suivant, la base de données ressources humaines est sélectionné par exemple **SQL01** pour afficher tous les objets qui empêchent les migrations (modifications avec rupture).

![Dernières modifications de base de données ressources humaines](../dma/media/BreakingChanges.png)

### <a name="on-premises-upgrade-readiness-report"></a>Sur site mise à niveau de disponibilité du rapport

![Sur site mise à niveau de disponibilité du rapport](../dma/media/OnPremisesUpgradeReadinessReport.png)

Ce rapport affiche un instantané de l’état de préparation de vos bases de données sont à migrer vers une version ultérieure de SQL Server. Les données de ce rapport proviennent de dbo. UpgradeSuccessFactor\_affichage local dans la base de données DMAReporting.

Filtrage par instance et le nom de la base de données et l’utilisation de cartes de score en haut, vous pouvez afficher les version de la base de données peut être migrée en trop. Par exemple, si vous filtrez par la base de données AdventureWorks 2012, vous pouvez voir que la base de données est prêt à passer à toutes les versions de SQL Server répertoriées dans le rapport. Cela est déterminé en vous assurant qu'aucune modification avec rupture pour ce niveau de compatibilité et de la base de données.

![Facteur de réussite de mise à niveau de base de données AdventureWorks](../dma/media/UpgradeSuccessFactor.png)

### <a name="on-premises-feature-parity-report"></a>Rapport de la parité des fonctionnalités sur site

![Rapport de la parité des fonctionnalités sur site](../dma/media/OnPremisesFeatureParityReport.png)

Utilisez ce rapport pour mettre en évidence les nouvelles fonctionnalités qui peuvent être utilisées pour la base de données dans la version de SQL Server cible.

Lorsque vous sélectionnez une fonctionnalité dans le graphique en entonnoir, les données en bas met en évidence les objets qui sont affectés par la fonctionnalité. Dans l’exemple suivant, le **Stretch database pour les besoins de stockage** fonctionnalité est sélectionnée, et un tableau est répertorié qui peuvent tirer parti de cette fonctionnalité.

![Recommandation de fonctionnalité pour Stretch Database](../dma/media/FeatureRecommend_StretchDatabase.png)

### <a name="azure-sql-db-upgrade-readiness-report"></a>Rapport de disponibilité de mise à niveau de base de données SQL Azure

![Rapport de disponibilité de mise à niveau de base de données SQL Azure](../dma/media/AzureSQLDBUpgradeReadinessReport.png)

Ce rapport présente la disponibilité de base de données à migrer vers Azure SQL Database V12. Les données à partir de ce rapport proviennent de dbo. Vue UpgradeSuccessRanking dans la base de données DMAReporting.

### <a name="azure-features-parity-report"></a>Rapport de parité des fonctionnalités Azure

![Rapport de parité des fonctionnalités Azure](../dma/media/AzureFeaturesParityReport.png)

Utilisez ce rapport pour mettre en surbrillance le *fonctionnalités au niveau de l’instance* qui ne sont pas pris en charge par Azure SQL Database V12.

Lorsque vous sélectionnez une fonctionnalité dans le graphique en entonnoir, les données dans la partie inférieure répertorient les instances et les fonctionnalités de base de données qui ne sont pas pris en charge. Dans l’exemple suivant, cette fonctionnalité est sélectionnée : **Toujours sur la disponibilité de configuration du groupe n'est pas pris en charge dans Azure SQL Database**.  

![Toujours sur la fonctionnalité groupe de disponibilité](../dma/media/Feature_AlwaysOnAvailability.png)

 
### <a name="azure-sql-db-unsupported-features-report"></a>Rapport de fonctionnalités de base de données SQL non pris en charge Azure

![Rapport de fonctionnalités de base de données SQL non pris en charge Azure](../dma/media/AzureSQLDBUnsupportedFeaturesReport.png)

Ce rapport met en évidence les fonctionnalités qui ne sont pas pris en charge pour une donnée **base de données** lorsque la cible est Azure SQL Database (V12).

En filtrant par la valeur de nom et la fonctionnalité de base de données dans le graphique en entonnoir, vous pouvez voir des détails sur la fonctionnalité non prise en charge. Les détails incluent des recommandations destinées à éviter le problème et l’objet concerné.

Par exemple, le filtrage par la base de données DTC et **bases de données en lecture seule ne peut pas être mis à niveau**, vous pouvez voir une liste des objets qui sont affectés.

![Bases de données en lecture seule ne peut pas être mis à niveau du problème](../dma/media/ReadOnlyDatabases.png)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de l’Assistant Migration de données](../dma/dma-overview.md)

[Téléchargement de l’Assistant Migration de données](https://www.microsoft.com/download/details.aspx?id=53595)

[Téléchargement de Power BI](https://powerbi.microsoft.com/)
