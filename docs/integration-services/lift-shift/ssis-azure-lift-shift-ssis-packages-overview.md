---
title: Déployer et exécuter des packages SSIS dans Azure | Microsoft Docs
description: Découvrez comment vous pouvez déplacer vos projets, packages et charges de travail SQL Server Integration Services (SSIS) vers le cloud Microsoft Azure.
ms.date: 06/07/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.suite: sql
ms.custom: ''
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0fa7a72e86f596cd0e5d18a0c0dbeb1015233f20
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35403291"
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Effectuer un « lift-and-shift » des charges de travail SQL Server Integration Services vers le cloud
Vous pouvez maintenant déplacer vos projets, packages et charges de travail SQL Server Integration Services (SSIS) vers le cloud Azure.
-   Stockez et gérez les projets et packages SSIS dans le catalogue SSIS (SSISDB) sur Azure SQL Database ou SQL Database Managed Instance (préversion).
-   Exécutez des packages dans une instance d’Azure-SSIS Integration Runtime, composant d’Azure Data Factory.
-   Utilisez des outils familiers comme SQL Server Management Studio (SSMS) pour les tâches courantes.

## <a name="benefits"></a>Avantages
Le déplacement de vos charges de travail SSIS locales vers Azure présente les avantages potentiels suivants :
-   **Réduisez les coûts opérationnels** et la charge de gestion de l’infrastructure quand vous exécutez SSIS localement ou sur des machines virtuelles Azure.
-   **Augmentez la haute disponibilité** pour pouvoir spécifier plusieurs nœuds par cluster, et étendez les fonctionnalités de haute disponibilité d’Azure et d’Azure SQL Database.
-   **Augmentez la scalabilité** pour pouvoir spécifier plusieurs cœurs par nœud (montée en puissance) et plusieurs nœuds par cluster (augmentation de la taille des instances).

## <a name="architecture-overview"></a>Vue d’ensemble de l’architecture
Le tableau suivant met en évidence les différences entre une instance SSIS locale et une instance SSIS sur Azure. La différence la plus importante est la séparation du stockage et de l’exécution. Azure Data Factory héberge le moteur de runtime des packages SSIS sur Azure. Le moteur d’exécution est appelé Azure-SSIS Integration Runtime (Azure-SSIS IR). Pour plus d’informations, consultez [Azure-SSIS Runtime Integration](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime).

| Stockage | Runtime | Extensibilité |
|---|---|---|
| Local (SQL Server) | Runtime SSIS hébergé par SQL Server | SSIS Scale Out (dans SQL Server 2017 et versions ultérieures)<br/><br/>Solutions personnalisées (dans les versions antérieures de SQL Server) |
| Dans Azure (SQL Database ou SQL Database Managed Instance (préversion)) | Azure-SSIS Integration Runtime, composant d’Azure Data Factory | Options de mise à l’échelle pour Azure-SSIS Integration Runtime |
| | | |

Il vous suffit de provisionner Azure-SSIS IR une seule fois. Vous pouvez ensuite utiliser des outils familiers tels que SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) pour déployer, configurer, exécuter, surveiller, planifier et gérer les packages.

## <a name="version-support"></a>Prise en charge de version

Vous pouvez déployer n’importe quel package créé avec l’une des versions de SSIS sur Azure. Quand vous déployez un package sur Azure sans erreur de validation, le package est automatiquement mis à niveau avec le dernier format de package. Le package est donc toujours mis à niveau avec la dernière version de SSIS.

Le processus de déploiement valide chaque package pour vérifier qu’il peut s’exécuter dans Azure SSIS Integration Runtime. Pour plus d’informations, consultez [Valider des packages SSIS déployés sur Azure](ssis-azure-validate-packages.md).

## <a name="prerequisites"></a>Conditions préalables requises

Pour déployer des packages SSIS sur Azure, vous devez avoir l’une des versions suivantes de SQL Server Data Tools (SSDT) :
-   Pour Visual Studio 2017, version 15.3 ou ultérieure.
-   Pour Visual Studio 2015, version 17.2 ou version ultérieure.

Pour plus d’informations sur les prérequis du runtime d’intégration Azure-SSIS, consultez [Déployer et exécuter un package SSIS dans Azure - Prérequis](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure#prerequisites).

> [!NOTE]
> Pendant cette préversion publique, Azure-SSIS Integration Runtime n’est pas encore disponible dans toutes les régions. Pour plus d’informations sur les régions prises en charge, consultez [Produits disponibles par région - Microsoft Azure](https://azure.microsoft.com/regions/services/).

## <a name="provision-ssis-on-azure"></a>Provisionner SSIS sur Azure

**Provisionnez**. Avant de pouvoir déployer et exécuter des packages SSIS dans Azure, vous devez provisionner le catalogue SSIS (SSISDB) et le runtime d’intégration Azure-SSIS. Suivez les étapes de provisionnement de cet article : [Déployer et exécuter un package SSIS dans Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

**Effectuez une augmentation de la taille des instances et une montée en puissance parallèle**. Quand vous provisionnez Azure-SSIS IR, vous pouvez effectuer un scale up et un scale out en spécifiant des valeurs pour les options suivantes :
-   la taille du nœud (notamment le nombre de cœurs) et le nombre de nœuds du cluster ;
-   l’instance existante d’Azure SQL Database pour héberger la base de données de catalogues SSIS (SSISDB), et le niveau de service de la base de données ;
-   le nombre maximal d’exécutions parallèles par nœud.

**Améliorez les performances**. Pour plus d’informations, consultez [Configurer le runtime d’intégration Azure-SSIS pour de hautes performances](https://docs.microsoft.com/azure/data-factory/configure-azure-ssis-integration-runtime-performance).

## <a name="design-packages"></a>Concevoir des packages

Vous continuez à **concevoir et générer des packages** localement dans SSDT, ou dans Visual Studio avec SSDT installé.

### <a name="connect-to-data-sources"></a>Se connecter aux sources de données

Pour plus d’informations sur la connexion à des sources de données locales à partir du cloud avec **l’authentification Windows**, consultez [Se connecter à des données et des partages de fichiers avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).

Pour plus d’informations sur la connexion à des fichiers et des partages de fichiers, consultez [Ouvrir et enregistrer des fichiers avec des packages SSIS déployés dans Azure](ssis-azure-files-file-shares.md).

### <a name="available-ssis-components"></a>Composants SSIS disponibles

Quand vous provisionnez une instance de SQL Database pour héberger SSISDB, le Feature Pack Azure pour SSIS et le composant redistribuable Access sont également installés. Ces composants fournissent une connectivité à diverses sources de données **Azure** et aux fichiers **Excel et Access**, en plus des sources de données prises en charge par les composants intégrés.

Vous pouvez également installer des composants supplémentaires. Par exemple, vous pouvez installer un pilote qui n’est pas installé par défaut. Pour plus d’informations, consultez [Installation personnalisée pour le runtime d’intégration SSIS Azure](/azure/articles/data-factory/how-to-configure-azure-ssis-ir-custom-setup).

Si vous êtes éditeur de logiciels, vous pouvez mettre à jour l’installation de vos composants sous licence pour les rendre disponibles sur Azure. Pour plus d’informations, consultez [Développer des composants personnalisés payants ou sous licence pour le runtime d’intégration Azure-SSIS](https://docs.microsoft.com/azure/data-factory/how-to-develop-azure-ssis-ir-licensed-components).

### <a name="transaction-support"></a>Prise en charge des transactions

Avec SQL Server en local et sur des machines virtuelles Azure, vous pouvez utiliser des transactions Microsoft Distributed Transaction Coordinator (MSDTC). Pour configurer MSDTC sur chaque nœud d’Azure-SSIS IR, utilisez la fonctionnalité d’installation personnalisée. Pour plus d’informations, consultez [Installation personnalisée pour le runtime d’intégration SSIS Azure](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup).

Avec Azure SQL Database, vous pouvez utiliser uniquement des transactions élastiques. Pour plus d’informations, consultez [Transactions distribuées entre les bases de données cloud](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-transactions-overview).

## <a name="deploy-and-run-packages"></a>Déployer et exécuter des packages

Pour bien démarrer, consultez [Déployer et exécuter un package SSIS dans Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="connect-to-ssisdb"></a>Se connecter à SSISDB

Le **nom de l’instance SQL Database** qui héberge SSISDB devient la première partie du nom en quatre parties à utiliser quand vous déployez et exécutez des packages à partir de SSDT et SSMS, au format suivant : `<sql_database_name>.database.windows.net`. Pour plus d’informations sur la connexion à la base de données de catalogues SSIS dans Azure, consultez [Se connecter au catalogue SSIS (SSISDB) dans Azure](ssis-azure-connect-to-catalog-database.md).

### <a name="deploy-projects-and-packages"></a>Déployer des projets et des packages

Vous devez utiliser le **modèle de déploiement de projet**, et non le modèle de déploiement de package, quand vous déployez des projets dans SSISDB sur Azure.

Pour déployer des projets sur Azure, vous pouvez utiliser plusieurs outils et options de script de votre choix :
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (à partir de SSMS, Visual Studio Code ou tout autre outil)
-   Un outil en ligne de commande
-   PowerShell ou C# et le modèle objet de gestion SSIS

Pour obtenir un exemple de déploiement qui utilise SSMS et l’Assistant Déploiement d’Integration Services, consultez [Déployer et exécuter un package SSIS dans Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="run-packages"></a>Exécuter des packages

Pour obtenir une vue d’ensemble des méthodes que vous pouvez utiliser pour exécuter des packages SSIS déployés sur Azure, consultez [Exécuter un package SSIS dans Azure](ssis-azure-run-packages.md).

## <a name="pass-runtime-values-with-environments"></a>Passer des valeurs runtime avec des environnements

Pour passer une ou plusieurs valeurs runtime aux packages que vous exécutez dans le cadre d’un pipeline Azure Data Factory, créez des environnements d’exécution SSIS dans SSISDB avec SSMS (SQL Server Management Studio). Dans chaque environnement, créez des variables et affectez des valeurs qui correspondent aux paramètres de vos projets ou packages. Configurez vos packages SSIS dans SSMS pour associer ces variables d’environnement aux paramètres de votre projet ou package. Quand vous exécutez les packages dans un pipeline Data Factory, vous pouvez passer d’un environnement à un autre en spécifiant différents chemins d’environnement sous l’onglet Paramètres de l’interface utilisateur de l’activité Exécuter le package SSIS.

Pour plus d’informations sur les environnements SSIS, consultez [Créer et mapper un environnement serveur](../packages/deploy-integration-services-ssis-projects-and-packages.md#create-and-map-a-server-environment). Pour plus d’informations sur l’exécution d’un package dans le cadre d’un pipeline Azure Data Factory, consultez [Exécuter un package SSIS à l’aide de l’activité SSIS dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).

## <a name="monitor-packages"></a>Surveiller les packages
Pour surveiller les packages en cours d’exécution dans SSMS, vous pouvez utiliser les outils de création de rapports suivants dans SSMS.
-   Cliquez avec le bouton droit sur **SSISDB**, puis sélectionnez **Opérations actives** pour ouvrir la boîte de dialogue **Opérations actives**.
-   Sélectionnez un package dans l’Explorateur d’objets, cliquez avec le bouton droit, sélectionnez **Rapports**, **Rapports standard**, puis **Toutes les exécutions**.

Pour surveiller Azure-SSIS Integration Runtime, consultez [Surveiller le runtime d’intégration Azure-SSIS](https://docs.microsoft.com/azure/data-factory/monitor-integration-runtime#azure-ssis-integration-runtime).

## <a name="schedule-packages"></a>Planifier les packages
Pour planifier l’exécution des packages stockés dans Azure SQL Database, vous pouvez utiliser divers outils. Pour plus d’informations, consultez [Planifier des packages SSIS dans Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Étapes suivantes
Pour bien démarrer avec les charges de travail SSIS sur Azure, consultez les articles suivants :
-   [Déployer des packages SQL Server Integration Services sur Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)
-   [Déployer et exécuter un package SSIS dans Azure](ssis-azure-deploy-run-monitor-tutorial.md)
