---
title: "Effectuer un « lift-and-shift » des charges de travail SQL Server Integration Services vers le cloud | Microsoft Docs"
ms.date: 10/31/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7ddfcca6408a64b2c2875aaa625c275899e8c85f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Effectuer un « lift-and-shift » des charges de travail SQL Server Integration Services vers le cloud
Vous pouvez maintenant déplacer vos packages et charges de travail SQL Server Integration Services (SSIS) vers le cloud Azure.
-   Stockez et gérez les projets et packages SSIS dans la base de données de catalogues SSIS (SSISDB) sur Azure SQL Database.
-   Exécutez des packages dans une instance du runtime d’intégration Azure SSIS, présenté dans le cadre d’Azure Data Factory version 2.
-   Utilisez des outils familiers tels que SQL Server Management Studio (SSMS) pour ces tâches courantes.

## <a name="benefits"></a>Avantages
Le déplacement de vos charges de travail SSIS locales vers Azure présente les avantages potentiels suivants :
-   **Réduisez les coûts opérationnels** et la charge de gestion de l’infrastructure quand vous exécutez SSIS localement ou sur des machines virtuelles Azure.
-   **Augmentez la haute disponibilité** pour pouvoir spécifier plusieurs nœuds par cluster, et étendez les fonctionnalités de haute disponibilité d’Azure et d’Azure SQL Database.
-   **Augmentez la scalabilité** pour pouvoir spécifier plusieurs cœurs par nœud (montée en puissance) et plusieurs nœuds par cluster (augmentation de la taille des instances).

## <a name="architecture-overview"></a>Vue d’ensemble de l’architecture
Le tableau suivant met en évidence les différences entre une instance SSIS locale et une instance SSIS sur Azure. La différence la plus importante est la séparation du stockage par rapport au calcul.

| Stockage | Runtime | Extensibilité |
|---|---|---|
| Local (SQL Server) | Runtime SSIS hébergé par SQL Server | SSIS Scale Out (dans SQL Server 2017 et versions ultérieures)<br/><br/>Solutions personnalisées (dans les versions antérieures de SQL Server) |
| Sur Azure (SQL Database) | Runtime d’intégration Azure SSIS, un composant d’Azure Data Factory version 2 | Options de montée en charge pour le runtime d’intégration SSIS |
| | | |

Azure Data Factory héberge le moteur de runtime des packages SSIS sur Azure. Le moteur de runtime est appelé runtime d’intégration Azure SSIS (runtime d’intégration SSIS).

Quand vous provisionnez le runtime d’intégration SSIS, vous pouvez effectuer une montée en puissance et augmenter la taille des instances en spécifiant les valeurs des options suivantes :
-   la taille du nœud (notamment le nombre de cœurs) et le nombre de nœuds du cluster ;
-   l’instance existante d’Azure SQL Database pour héberger la base de données de catalogues SSIS (SSISDB), et le niveau de service de la base de données ;
-   le nombre maximal d’exécutions parallèles par nœud.

Vous devez provisionner une seule fois le runtime d’intégration SSIS. Vous pouvez ensuite utiliser des outils familiers tels que SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) pour déployer, configurer, exécuter, surveiller, planifier et gérer les packages.

> [!NOTE]
> Pour cette préversion publique, le runtime d’intégration Azure SSIS n’est pas encore disponible dans toutes les régions. Pour plus d’informations sur les régions prises en charge, consultez [Produits disponibles par région - Microsoft Azure](https://azure.microsoft.com/regions/services/).

Data Factory prend également en charge d’autres types de runtime d’intégration. Pour plus d’informations sur le runtime d’intégration SSIS et les autres types de runtime d’intégration, consultez la section [Runtime d’intégration dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime).

## <a name="prerequisites"></a>Conditions préalables
Les fonctionnalités décrites dans cette rubrique ne nécessitent pas SQL Server 2017 ou SQL Server 2016.

Ces fonctionnalités nécessitent les versions suivantes de SQL Server Data Tools (SSDT) :
-   Pour Visual Studio 2017, version 15.3 (préversion) ou version ultérieure.
-   Pour Visual Studio 2015, version 17.2 ou version ultérieure.

> [!NOTE]
> Quand vous déployez des packages sur Azure, l’Assistant Déploiement de packages effectue toujours une mise à niveau des packages vers le dernier format de package.

Pour plus d’informations sur les prérequis dans Azure, consultez [Effectuer un « lift-and-shift » des packages SSIS (SQL Server Integration Services) vers Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

## <a name="ssis-features-on-azure"></a>Fonctionnalités SSIS sur Azure

Quand vous provisionnez une instance de SQL Database pour héberger SSISDB, le Feature Pack Azure pour SSIS et le composant redistribuable Access sont également installés. Ces composants fournissent une connectivité aux fichiers **Excel et Access** et à diverses sources de données **Azure**, en plus des sources de données prises en charge par les composants intégrés. Vous ne pouvez pas installer de **composants tiers** pour SSIS (notamment les composants tiers de Microsoft, par exemple Attunity et SAP BI) pour le moment.

Le **nom de l’instance SQL Database** qui héberge SSISDB devient la première partie du nom en quatre parties à utiliser quand vous déployez et gérez des packages à partir de SSDT et de SSMS - `<sql_database_name>.database.windows.net`.

Vous devez utiliser le **modèle de déploiement de projet**, et non le modèle de déploiement de package, pour les projets que vous déployez sur SSISDB dans Azure SQL Database.

Vous continuez à **concevoir et générer des packages** localement dans SSDT, ou dans Visual Studio avec SSDT installé.

Pour plus d’informations sur la connexion aux **sources de données locales** à partir du cloud avec l’authentification Windows, consultez [Se connecter à des sources de données locales avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).

## <a name="common-tasks"></a>Tâches courantes

### <a name="provision"></a>Approvisionner
Avant de pouvoir déployer et exécuter des packages SSIS dans Azure, vous devez provisionner la base de données de catalogues SSISDB et le runtime d’intégration Azure SSIS. Suivez les étapes de provisionnement décrites dans cet article : [Effectuer un « lift-and-shift » des packages SSIS (SQL Server Integration Services) vers Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

### <a name="deploy-and-run-packages"></a>Déployer et exécuter des packages
Pour déployer des projets et exécuter des packages sur SQL Database, vous pouvez utiliser plusieurs outils et options de script de votre choix :
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (à partir de SSMS, Visual Studio Code ou tout autre outil)
-   Un outil en ligne de commande
-   PowerShell
-   C# et le modèle objet de gestion SSIS

### <a name="monitor-packages"></a>Surveiller les packages
Pour surveiller les packages en cours d’exécution dans SSMS, vous pouvez utiliser l’un des outils de compte-rendu suivants dans SSMS.
-   Cliquez avec le bouton droit sur **SSISDB**, puis sélectionnez **Opérations actives** pour ouvrir la boîte de dialogue **Opérations actives**.
-   Sélectionnez un package dans l’Explorateur d’objets, cliquez avec le bouton droit, sélectionnez **Rapports**, **Rapports standard**, puis **Toutes les exécutions**.

### <a name="schedule-packages"></a>Planifier les packages
Pour planifier l’exécution des packages stockés dans SQL Database, vous pouvez utiliser les outils suivants :
-   SQL Server Agent (local)
-   Activité de procédure stockée SQL Server Data Factory

Pour plus d’informations, consultez [Planifier l’exécution d’un package SSIS sur Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Étapes suivantes
Pour bien démarrer avec les charges de travail SSIS sur Azure, consultez les articles suivants :
-   [Effectuer un « lift-and-shift » des packages SSIS (SQL Server Integration Services) vers Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)
-   [Déployer, exécuter et surveiller un package SSIS sur Azure](ssis-azure-deploy-run-monitor-tutorial.md)
