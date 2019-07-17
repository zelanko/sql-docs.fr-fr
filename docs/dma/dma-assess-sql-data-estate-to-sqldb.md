---
title: Évaluer la disponibilité d’un espace de données SQL Server Migration vers Azure SQL Database | Microsoft Docs
description: Découvrez comment utiliser Data Migration Assistant pour migrer un espace de données SQL Server pour la migration vers Azure SQL Database
ms.custom: ''
ms.date: 07/16/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: jroth
ms.openlocfilehash: d317fb3f0c2227744318eeaead71514095afbdec
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269381"
---
# <a name="assess-the-readiness-of-a-sql-server-data-estate-migrating-to-azure-sql-database-using-the-data-migration-assistant"></a>Évaluer la disponibilité d’un espace de données SQL Server Migration vers Azure SQL Database à l’aide de l’Assistant Migration des données

Migration des centaines d’instances de SQL Server et des milliers de bases de données Azure SQL Database, notre offre Platform as a Service (PaaS), sont une tâche considérable. Pour rationaliser le processus autant que possible, vous devez confiant votre préparation relative pour la migration. Identification des éléments faciles d’accès, y compris les serveurs et les bases de données qui sont entièrement prêt ou qui nécessitent un minimum d’effort pour préparer la migration, facilite et accélère vos efforts.

Cet article fournit des instructions détaillées pour exploiter le [Data Migration Assistant](https://docs.microsoft.com/sql/dma/dma-overview?view=sql-server-2017) pour résumer les résultats de la disponibilité et de les faire apparaître sur le [Azure Migrate](https://portal.azure.com/?feature.customPortal=false#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview) hub.

## <a name="create-a-project-and-add-a-tool"></a>Créez un projet et ajouter un outil

Configurer un nouveau projet Azure Migrate dans un abonnement Azure, puis ajouter un outil.

Un projet Azure Migrate permet de stocker de découverte, d’évaluation et les métadonnées de migration collectées à partir de l’environnement ou de migration d’évaluation. Vous également utilisez un projet pour suivre les ressources découvertes et pour orchestrer la migration et évaluation.

1. Connectez-vous au portail Azure, sélectionnez **tous les services**, puis recherchez Azure Migrate.
2. Sous **Services**, sélectionnez **Azure Migrate**.

   ![Azure Migrate - Sélectionnez service](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-services.png)

3. Sur le **vue d’ensemble** page, sélectionnez **évaluer et migrer des bases de données**.

   ![Azure Migrate - évaluation de lancement](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-hub-assess.png)

4. Dans **bases de données**, sous **mise en route**, sélectionnez **ajouter intermédiaires**.

   ![Azure Migrate - ajouter des outils](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-add-tools.png)

5. Sur le **projet de migration** , sélectionnez votre groupe de ressources et des abonnements Azure (si vous ne disposez pas d’une ressource de groupe, créez-en un).
6. Sous **détails du projet**, spécifiez le nom du projet et la zone géographique dans laquelle vous souhaitez créer le projet.

    ![Azure Migrate - ajouter une boîte de dialogue Outil](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-add-tool-dialog.png)

    Vous pouvez créer un projet Azure Migrate dans un de ces zones géographiques.

    | **Geography**  | **Région d’emplacement de stockage** |
    | ------------- | ------------- |
    | Asie | Asie du Sud-est ou Asie |
    | Europe | Europe du Sud ou Europe de l’ouest |
    | Royaume-Uni | Royaume-Uni Sud ou Royaume-Uni ouest |
    | États-Unis | Centre des États-Unis ou ouest des États-Unis 2 |

    La zone géographique spécifiée pour le projet est uniquement utilisée pour stocker les métadonnées collectées à partir de machines virtuelles locales. Vous pouvez sélectionner n’importe quelle région cible pour la migration effective.

7. Sélectionnez **suivant**, puis ajoutez un outil d’évaluation.

   > [!NOTE]
   > Lorsque vous créez un projet, vous devez ajouter au moins un outil d’évaluation ou de migration.

8. Sur le **outil d’évaluation sélectionnez** onglet, **Azure Migrate : Évaluation de base de données** apparaît en tant que l’outil d’évaluation à ajouter. Si vous n’avez pas besoin un outil d’évaluation, sélectionnez le **ignorer l’ajout d’un outil d’évaluation pour l’instant** case à cocher. Sélectionnez **Suivant**.

    ![Azure Migrate - onglet de l’outil Sélection d’évaluation](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-select-assessment-tool.png)

9. Sur le **outil de migration sélectionnez** onglet, **Azure Migrate : Migration de base de données** apparaît en tant que l’outil de migration à ajouter. Si vous n’avez pas besoin un outil de migration, sélectionnez le **ignorer l’ajout d’un outil de migration pour l’instant**. Sélectionnez **Suivant**.

    ![Azure Migrate - onglet de l’outil migration Select](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-select-migration-tool.png)

10. Dans **examiner + ajouter des outils**, passez en revue les paramètres, puis sélectionnez **ajouter les outils**.

    ![Azure Migrate - révision + ajouter un onglet d’outils](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-review-tools.png)

    Après avoir créé le projet, vous pouvez sélectionner des outils supplémentaires pour la migration des serveurs et des charges de travail, des bases de données et des applications web et d’évaluation.

## <a name="assess-and-upload-assessment-results"></a>Évaluer et charger les résultats d’évaluation

Après avoir créé un projet de migration, sous **outils d’évaluation**, dans le **Azure Migrate : Évaluation de base de données** zone, les instructions de téléchargement et à l’aide de l’affichage de l’outil Assistant Migration de données.

   ![Azure Migrate - outil d’évaluation ajouté](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-assessment-tool-added.png)

1. Télécharger Data Migration Assistant, en utilisant le lien fourni, puis installez-le sur un ordinateur ayant accès à vos instances de SQL Server source.
2. Démarrer l’Assistant Migration de données.

### <a name="create-an-assessment"></a>Créer une évaluation

1. Sur la gauche, sélectionnez le **+** icône, puis sélectionnez l’évaluation **type de projet**
2. Spécifiez le nom du projet, puis sélectionnez le serveur source et les types de serveur cible.

    Si vous mettez à niveau votre instance de SQL Server locale vers une version ultérieure de SQL Server ou SQL Server hébergée sur une machine virtuelle Azure, définissez le type de serveur source et cible sur **SQL Server**. Définissez le type de serveur cible sur **Azure SQL Database Managed Instance** pour une évaluation de la disponibilité de base de données SQL Azure (PaaS) cible.

3. Sélectionnez **Créer**.

   ![Azure Migrate - interface Data Migration Assistant](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-interface.png)

### <a name="choose-assessment-options"></a>Choisissez les options d’évaluation

1. Sélectionnez le type de rapport.

    Vous pouvez choisir une ou les deux types de rapport suivants :
    * Vérifier la compatibilité de base de données
    * Vérifier la parité de fonctionnalité

   ![Écran des options Azure Migrate - Data Migration Assistant - évaluation](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-options-screen.png)

2. Sélectionnez **Suivant**.

### <a name="add-databases-to-assess"></a>Ajouter des bases de données à évaluer

1. Sélectionnez **ajouter des Sources de** pour ouvrir le menu de connexion visite.
2. Entrez le nom d’instance SQL server, choisissez le type d’authentification, définissez les propriétés de connexion correctes, puis sélectionnez **Connect**.
3. Sélectionnez les bases de données à évaluer, puis sélectionnez **ajouter**.

   > [!NOTE]
   > Vous pouvez supprimer plusieurs bases de données en les sélectionnant tout en maintenant enfoncée la touche MAJ ou Ctrl, puis en cliquant sur Supprimer les Sources. Vous pouvez également ajouter des bases de données à partir de plusieurs instances de SQL Server à l’aide du bouton Ajouter des Sources.

4. Sélectionnez **suivant** pour démarrer l’évaluation.

   ![Écran de select sources Azure Migrate - Data Migration Assistant-](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-select-sources-screen.png)

5. Une fois l’évaluation terminée, sélectionnez **charger dans Azure Migrate**.

   ![Azure Migrate - Data Migration Assistant - résultats de la section Vérification](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-review-results-screen.png)

6. Connectez-vous au portail Azure.

   ![Azure Migrate - Data Migration Assistant - résultats de la section Vérification](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-portal-signin.png)

7. Sélectionnez l’abonnement et le projet Azure Migrate dans lequel vous souhaitez télécharger les résultats d’évaluation, puis sélectionnez **télécharger**.

   Attendez la confirmation de chargement d’évaluation.

## <a name="view-target-readiness-assessment-results"></a>Afficher les résultats d’évaluation de préparation de cible

1. Se connecter dans le portail Azure, recherchez Azure migrate, puis sélectionnez **Azure Migrate**.

   ![Recherche de service Azure Migrate - portail Azure-](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-portal-search.png)

2. Sélectionnez **évaluer et migrer des bases de données** pour obtenir les résultats d’évaluation.

   ![Azure Migrate - résultats d’évaluation de révision](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-hub-assess.png)

    Vous pouvez afficher le résumé de préparation de SQL Server, assurez-vous que vous êtes sur le projet de migration adaptée, sinon, utilisez l’option pour sélectionner un projet de migration différent.

    Migrer le projet chaque fois que vous mettez à jour les résultats d’évaluation vers Azure, Azure migrate hub consolider tous les résultats et fournir le rapport de synthèse.  Vous pouvez exécuter plusieurs évaluations de l’Assistant de Migration de données en parallèle et télécharger les résultats dans le projet de migration unique pour obtenir l’état de préparation consolidé.

   ![Azure Migrate - résultats de la disponibilité](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-review-readiness.png)

    **Évaluer les instances de base de données**:  Le nombre d’instances de SQL Server évaluée jusqu'à présent.
    **Évaluation des bases de données**: Nombre total de bases de données évalué sur une ou plusieurs instances de SQL Server évalués **bases de données prête pour la base de données SQL**:  Nombre de bases de données prêts à migrer vers Azure SQL Database (PaaS).
    **Bases de données prête pour la machine virtuelle de SQL Azure**:  Nombre de bases de données composent d’un ou plusieurs bloqueurs de migration vers Azure SQL Database (PaaS), mais prêt à migrer vers les machines virtuelles Azure SQL Server.

3. Sélectionnez **évalué des instances de base de données** pour accéder à la vue d’instance SQL Server.

   ![Azure Migrate - préparation d’instance de révision](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-assessed-instances.png)

    Vous pouvez trouver l’état de préparation de pourcentage de chaque instance de SQL Server Migration vers Azure SQL Database (PaaS).

4. Sélectionnez une instance spécifique pour accéder à la vue de compatibilité de base de données.

   ![Azure Migrate - disponibilité de base de données de révision](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-assessed-databases.png)

    Vous pouvez voir le nombre de bloqueurs de migration par chaque base de données, la cible recommandée par chaque base de données dans la vue ci-dessus.

5. Passez en revue les résultats d’évaluation DMA pour obtenir plus de détails sur les bloqueurs de migration.

   ![Azure Migrate - bloqueurs de migration de révision](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-migration-blockers.png)

## <a name="see-also"></a>Voir aussi

* [Data Migration Assistant (DMA)](../dma/dma-overview.md)
* [Assistant de Migration de données : Paramètres de configuration](../dma/dma-configurationsettings.md)
* [Assistant de Migration de données : Meilleures pratiques](../dma/dma-bestpractices.md)
