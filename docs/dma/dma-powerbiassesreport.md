---
title: Analyser les rapports d’évaluation consolidés avec Power BI
titleSuffix: Data Migration Assistant
description: Découvrez comment utiliser Power BI pour analyser les rapports d’évaluation de la migration des données que vous avez importés et consolidés dans SQL Server
ms.custom: seo-lt-2019
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
ms.openlocfilehash: f2385914fc97fa8e118d871ddac6e0cdc9d49247
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056504"
---
# <a name="analyze-consolidated-assessment-reports-created-by-data-migration-assistant-with-power-bi"></a>Analyser les rapports d’évaluation consolidés créés par Assistant Migration de données avec Power BI

Cet article explique comment créer un rapport de Power BI pour analyser les évaluations de la migration consolidée.

Pour plus d’informations sur la consolidation des évaluations de migration créées par le Assistant Migration de données, consultez [consolider les rapports d’évaluation](../dma/dma-consolidatereports.md).

## <a name="sample-power-bi-reports"></a>Exemples de rapports de Power BI

Vous pouvez télécharger des exemples de rapports de Power BI pour les évaluations de migration consolidées à partir de ce [référentiel GitHub](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant).

Les rapports suivants sont inclus : 

- [Commandes](#dashboard-report)

  Comprend des statistiques d’instantané et un rapport détaillé.

- [Préparation à la mise à niveau locale](#on-premises-upgrade-readiness-report)

  La source de données est la vue UpgradeSuccessRanking de la base de données DMAReporting.  Ce rapport affiche le pourcentage de réussite de la mise à niveau de vos bases de données évaluées.

- [Parité des fonctionnalités locales](#on-premises-feature-parity-report)

  Affiche les recommandations relatives aux fonctionnalités pour la version de SQL Server cible.

- [Préparation à la mise à niveau d’Azure SQL DB](#azure-sql-db-upgrade-readiness-report)

  La source de données est la vue UpgradeSuccessRanking de la base de données DMAReporting.  Ce rapport affiche le pourcentage de réussite de la mise à niveau des bases de données évaluées pour les migrations de base de données SQL Azure.

- [Fonctionnalités non prises en charge d’Azure SQL DB](#azure-sql-db-unsupported-features-report)

  Affiche les fonctionnalités de vos bases de données existantes qui ne sont pas prises en charge dans Azure SQL DB (V12).

Vous pouvez modifier ces rapports pour qu’ils fonctionnent avec votre environnement en modifiant la source de données dans Power BI. 

1. Sélectionnez la flèche vers le bas en regard de **modifier les requêtes**, puis sélectionnez Paramètres de la **source de données**.

   ![Menu modifier les requêtes, paramètres de la source de données](../dma/media/DataSourceSettings.png)

1. Sélectionnez **changer la source...** , puis entrez les valeurs du serveur et de la base de données.

   ![Modifier la source, le serveur et la base de données](../dma/media/ChangeSource.png)

1. Sélectionnez **OK**, puis cliquez sur **Fermer**.

1. Actualisez vos rapports.

   ![Actualiser Power BI rapport](../dma/media/RefreshReport.png)

### <a name="dashboard-report"></a>Rapport tableau de bord

![Rapport tableau de bord](../dma/media/DashboardReport.png)

Le tableau de bord affiche des détails sur toutes vos évaluations. Vous pouvez utiliser les segments sur le côté gauche pour filtrer par instance ou par base de données. Vous pouvez utiliser le graphique à barres pour accéder à des catégories spécifiques afin de déterminer où se trouvent les problèmes.

Pour descendre dans la vue, sélectionnez le cercle avec la flèche vers le bas dans l’angle supérieur droit du graphique à barres.

![Exploration des catégories](../dma/media/CategoryDrillDown.png)

La séquence d’exploration vers le bas est définie comme indiqué dans l’image suivante (sous **Axis**). Pour modifier la séquence, faites glisser les colonnes dans l’ordre souhaité.

![Visualisations, axe de graphique à barres](../dma/media/VisualizationsAxis.png)

Cette vue devient encore plus performante lorsque vous filtrez pour la première fois par une base de données spécifique, puis explorez les problèmes de catégorie spécifiques. Dans l’exemple suivant, la base de données RH est sélectionnée par exemple **SQL01** pour afficher tous les objets qui empêchent les migrations (modifications avec rupture).

![Dernières modifications pour la base de données RH](../dma/media/BreakingChanges.png)

### <a name="on-premises-upgrade-readiness-report"></a>Rapport de disponibilité de la mise à niveau locale

![Rapport de disponibilité de la mise à niveau locale](../dma/media/OnPremisesUpgradeReadinessReport.png)

Ce rapport présente un instantané de la manière dont les bases de données sont prêtes à migrer vers une version ultérieure de SQL Server. Les données de ce rapport proviennent du dbo. UpgradeSuccessFactor\_vue local dans la base de données DMAReporting.

En filtrant par instance et par nom de base de données, et en utilisant les cartes de score en haut, vous pouvez voir la version que la base de données pourrait être migrée. Par exemple, si vous filtrez sur la base de données AdventureWorks 2012, vous pouvez voir que la base de données est prête à être déplacée vers toutes les versions de SQL Server listées dans le rapport. Cela est déterminé en s’assurant qu’il n’existe aucune modification avec rupture pour cette base de données et ce niveau de compatibilité.

![Mettre à niveau le facteur de réussite pour la base de données AdventureWorks](../dma/media/UpgradeSuccessFactor.png)

### <a name="on-premises-feature-parity-report"></a>Rapport de parité des fonctionnalités locales

![Rapport de parité des fonctionnalités locales](../dma/media/OnPremisesFeatureParityReport.png)

Utilisez ce rapport pour mettre en évidence les nouvelles fonctionnalités qui peuvent être utilisées pour la base de données dans la version cible du SQL Server.

Lorsque vous sélectionnez une fonctionnalité dans le graphique en entonnoir, les données en bas mettent en évidence les objets qui sont affectés par la fonctionnalité. Dans l’exemple suivant, la fonctionnalité **étendre la base de données pour les économies de stockage** est sélectionnée et une table qui peut tirer parti de cette fonctionnalité est affichée.

![Recommandation de fonctionnalité pour Stretch Database](../dma/media/FeatureRecommend_StretchDatabase.png)

### <a name="azure-sql-db-upgrade-readiness-report"></a>Rapport de disponibilité de la mise à niveau d’Azure SQL DB

![Rapport de disponibilité de la mise à niveau d’Azure SQL DB](../dma/media/AzureSQLDBUpgradeReadinessReport.png)

Ce rapport indique la disponibilité de la base de données à migrer vers Azure SQL Database v12. Les données de ce rapport proviennent du dbo. Affichage UpgradeSuccessRanking dans la base de données DMAReporting.

### <a name="azure-features-parity-report"></a>Rapport de parité des fonctionnalités Azure

![Rapport de parité des fonctionnalités Azure](../dma/media/AzureFeaturesParityReport.png)

Utilisez ce rapport pour mettre en évidence les *fonctionnalités de niveau d’instance* qui ne sont pas prises en charge par Azure SQL Database v12.

Lorsque vous sélectionnez une fonctionnalité dans le graphique en entonnoir, les données situées en bas répertorient les instances et les fonctionnalités de base de données qui ne sont pas prises en charge. Dans l’exemple suivant, cette fonctionnalité est sélectionnée : la configuration d’un **groupe de disponibilité Always on n’est pas prise en charge dans Azure SQL Database**.  

![Fonctionnalité de groupe de disponibilité Always on](../dma/media/Feature_AlwaysOnAvailability.png)

 
### <a name="azure-sql-db-unsupported-features-report"></a>Rapport sur les fonctionnalités non prises en charge d’Azure SQL DB

![Rapport sur les fonctionnalités non prises en charge d’Azure SQL DB](../dma/media/AzureSQLDBUnsupportedFeaturesReport.png)

Ce rapport met en évidence les fonctionnalités qui ne sont pas prises en charge pour une **base de données** donnée lorsque la cible est Azure SQL Database (V12).

En filtrant en fonction de la valeur du nom et de la fonctionnalité de la base de données dans le graphique en entonnoir, vous pouvez afficher des détails sur la fonctionnalité non prise en charge. Les détails incluent l’objet affecté et les recommandations pour résoudre le problème.

Par exemple, le filtrage par la base de données DTC et les **bases de données en lecture seule ne peuvent pas être mis à niveau**, vous pouvez voir une liste des objets affectés.

![Le problème de mise à niveau des bases de données en lecture seule ne peut pas être mis à niveau](../dma/media/ReadOnlyDatabases.png)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Assistant Migration de données](../dma/dma-overview.md)

[Télécharger Assistant Migration de données](https://www.microsoft.com/download/details.aspx?id=53595)

[Télécharger Power BI](https://powerbi.microsoft.com/)
