---
title: Effectuer une évaluation de migration SQL Server
titleSuffix: Data Migration Assistant
description: Apprenez à utiliser Data Migration Assistant pour évaluer un serveur SQL sur place avant de migrer vers un autre serveur SQL ou vers la base de données SQL Azure
ms.date: 01/15/2020
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
ms.custom: seo-lt-2019
ms.openlocfilehash: 59dc8c96ebda5ac66fb6701d480cb6d633e83158
ms.sourcegitcommit: 48e259549f65f0433031ed6087dbd5d9c0a51398
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80809749"
---
# <a name="perform-a-sql-server-migration-assessment-with-data-migration-assistant"></a>Effectuer une évaluation de migration SQL Server avec l’assistant Migration de données

Les instructions suivantes étape par étape vous aident à effectuer votre première évaluation pour la migration vers SQL Server sur place, SQL Server fonctionnant sur une base de données Azure VM ou Azure SQL En utilisant Data Migration Assistant.

   > [!NOTE]
   > Data Migration Assistant v5.0 introduit un support pour l’analyse de la connectivité des bases de données et des requêtes SQL intégrées dans le code d’application. Pour plus d’informations, consultez le billet de blog Using Data Migration Assistant pour évaluer la [couche d’accès aux données d’une application](https://techcommunity.microsoft.com/t5/Microsoft-Data-Migration/Using-Data-Migration-Assistant-to-assess-an-application-s-data/ba-p/990430).

## <a name="create-an-assessment"></a>Créer une évaluation

1. Sélectionnez la **nouvelle** icône, puis sélectionnez le type de projet **d’évaluation.**

2. Définissez le type de serveur source et cible.

    Si vous mettez à niveau votre instance SQL Server sur place vers une instance SQL Server moderne sur place ou vers SQL Server hébergé sur un Azure VM, définissez le type de serveur source et cible à **SQL Server**. Si vous migrez vers La base de données SqL Azure, définissez plutôt le type de serveur cible à **la base de données SqL Azure**.

3. Cliquez sur **Créer**.

   ![Créer une évaluation](../dma/media/dma-assesssqlonprem/new-assessment.png)

## <a name="choose-assessment-options"></a>Choisissez des options d’évaluation

1. Sélectionnez la version cible SQL Server à laquelle vous prévoyez de migrer.

2. Sélectionnez le type de rapport.

   Lorsque vous évaluez votre exemple de serveur SQL source pour la migration vers SQL Server sur place ou vers SQL Server hébergé sur les cibles Azure VM, vous pouvez choisir l’un ou les deux types de rapports d’évaluation suivants :

    - **Questions de compatibilité**
    - **Recommandation de nouvelles fonctionnalités**

   ![Sélectionnez un type de rapport d’évaluation pour la cible SQL Server](../dma/media/dma-assesssqlonprem/assessment-types.png)

   Lors de l’évaluation de votre source SQL Server instance pour la migration vers Azure SQL Base de données, vous pouvez choisir l’un ou les deux types de rapport d’évaluation suivants:

    - **Vérifier la compatibilité de la base de données**
    - **Vérifier la parité de fonctionnalité**

    ![Sélectionner le type de rapport d’évaluation pour la cible de base de données SQL](../dma/media/dma-assesssqlonprem/assessment-types-azure.png)

## <a name="add-databases-and-extended-events-trace-to-assess"></a>Ajouter des bases de données et des événements prolongés pour évaluer

1. Sélectionnez **Ajouter des sources** pour ouvrir le menu de vol de connexion.

2. Entrez le nom d’instance du serveur SQL, choisissez le type d’authentification, définissez les propriétés de connexion correctes, puis **sélectionnez Connect**.

3. Sélectionnez les bases de données pour évaluer, puis sélectionnez **Ajouter**.

    > [!NOTE]
    > Vous pouvez supprimer plusieurs bases de données en les sélectionnant tout en maintenant la clé Shift ou Ctrl, puis en cliquant **sur Supprimer les sources**. Vous pouvez également ajouter des bases de données à partir de plusieurs instances SQL Server en sélectionnant **Add Sources**.

4. Si vous avez des requêtes SQL ad hoc ou dynamiques ou des relevés DML initiés par la couche de données d’application, entrez le chemin vers le dossier dans lequel vous avez placé tous les fichiers de session d’événements prolongés que vous avez recueillis pour capturer la charge de travail sur le serveur SQL source.

     L’exemple suivant montre comment créer une session d’événement prolongée sur votre serveur SQL source pour capturer la charge de travail de la couche de données d’application.  Capturez la charge de travail pour la durée qui représente votre charge de travail maximale.

    ```
    DROP EVENT SESSION [DatalayerSession] ON SERVER
    go
    CREATE EVENT SESSION [DatalayerSession] ON SERVER  
    ADD EVENT sqlserver.sql_batch_completed( 
        ACTION (sqlserver.sql_text,sqlserver.client_app_name,sqlserver.client_hostname,sqlserver.database_id))
    ADD TARGET package0.asynchronous_file_target(SET filename=N'C:\temp\Demos\DataLayerAppassess\DatalayerSession.xel')  
    WITH (MAX_MEMORY=2048 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=3 SECONDS,MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=OFF)
    go
    ---Start the session
    ALTER EVENT SESSION [DatalayerSession]
          ON SERVER
        STATE = START;
    ---Wait for few minutes
    
    ---Query events
        
        SELECT 
        object_name,
        CAST(event_data as xml) as event_data,
        file_name, 
        file_offset
    FROM sys.fn_xe_file_target_read_file('C:\temp\Demos\DataLayerAppassess\DatalayerSession*xel', 
                'C:\\temp\\Demos\\DataLayerAppassess\\DatalayerSession*xem', 
                null,
                null)
    ---Stop the session after capturing the peak load.
    ALTER EVENT SESSION [DatalayerSession]
          ON SERVER
        STATE = STOP;
        
        go
    ```

5. Cliquez sur **Suivant** pour démarrer l’évaluation.

    ![Ajouter des sources et commencer l’évaluation](../dma/media/dma-assesssqlonprem/select-database1.png)

> [!NOTE]
> Vous pouvez exécuter plusieurs évaluations simultanément et afficher l’état des évaluations en ouvrant la page **All Assessments** (Toutes les évaluations).

## <a name="view-results"></a>Afficher les résultats

La durée de l’évaluation dépend du nombre de bases de données ajoutées et de la taille du schéma de chaque base de données. Les résultats sont affichés pour chaque base de données dès qu’ils sont disponibles.

1. Sélectionnez la base de données qui a terminé l’évaluation, puis passez **d’un problème de compatibilité** à **des recommandations de fonctionnalités** à l’aide du commutateur.

2. Examinez les problèmes de compatibilité à travers tous les niveaux de compatibilité pris en charge par la version cible SQL Server que vous avez sélectionnée sur la page **Options.**

Vous pouvez passer en revue les problèmes de compatibilité en analysant l’objet affecté, ses détails, et potentiellement un correctif pour chaque problème identifié sous **breaking changes**, changements **de comportement**, et **les fonctionnalités dépréciées**.

![Afficher les résultats de l’évaluation](../dma/media/dma-assesssqlonprem/review-results.png)

De même, vous pouvez examiner la recommandation de fonctionnalités dans les domaines **Performance,** **Stockage**et **Sécurité.**

Les recommandations de fonctionnalités couvrent différents types de fonctionnalités telles que In-Memory OLTP, Columnstore, Stretch Database, Always Encrypted, Dynamic Data Masking et Transparent Data Encryption.

![Afficher les recommandations de fonctionnalités](../dma/media/dma-assesssqlonprem/feature-recommendations.png)

Pour Azure SQL Database, les évaluations fournissent des problèmes de blocage des migrations et des problèmes de parité des caractéristiques.Examiner les résultats pour les deux catégories en sélectionnant les options spécifiques.

- La catégorie **de parité des fonctionnalités SQL Server** fournit un ensemble complet de recommandations, d’approches alternatives disponibles en Azure et d’étapes atténuantes. Il vous aide à planifier cet effort dans vos projets de migration.

  ![Afficher les informations pour SQL Server parité fonctionnalité](../dma/media/dma-assesssqlonprem/sql-feature-parity.png)

- La catégorie **des problèmes de compatibilité** fournit des fonctionnalités partiellement prises en charge ou non soutenues qui bloquent la migration des bases de données SQL Server sur place vers les bases de données Azure SQL.Il fournit ensuite des recommandations pour vous aider à résoudre ces problèmes.

  ![Afficher les problèmes de compatibilité](../dma/media/dma-assesssqlonprem/compatibility-issues.png)

## <a name="assess-a-data-estate-for-target-readiness"></a>Évaluer une succession de données pour la préparation des cibles

Si vous souhaitez étendre davantage ces évaluations à l’ensemble de la succession de données et trouver la disponibilité relative des instances et bases de données SQL Server pour la migration vers la base de données Azure SQL, téléchargez les résultats vers le hub Azure Migrate en sélectionnant **Le téléchargement sur Azure Migrate**.

Cela vous permet de visualiser les résultats consolidés sur le projet de hub Azure Migrate.

Des directives détaillées étape par étape pour les évaluations de préparation aux cibles sont disponibles [ici](https://docs.microsoft.com/sql/dma/dma-assess-sql-data-estate-to-sqldb?view=sql-server-2017).

   ![Téléchargez les résultats sur Azure Migrate](../dma/media/dma-assesssqlonprem/upload-to-azure-migrate.png)

## <a name="export-results"></a>Exporter les résultats

Une fois que toutes les bases de données ont terminé l’évaluation, sélectionnez le **rapport Export** pour exporter les résultats soit vers un fichier JSON ou un fichier CSV. Vous pouvez ensuite analyser les données à votre convenance.

## <a name="save-and-load-assessments"></a>Enregistrer et charger des évaluations

En plus d’exporter les résultats d’une évaluation, vous pouvez enregistrer les détails de l’évaluation à un dossier et charger un dossier d’évaluation pour examen ultérieur.  Pour plus d’informations, voir l’article [Enregistrer et charger les évaluations avec Data Migration Assistant](../dma/dma-save-load-assessments.md).
