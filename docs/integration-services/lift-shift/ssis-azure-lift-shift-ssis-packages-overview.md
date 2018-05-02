---
title: Effectuer un « lift-and-shift » des charges de travail SQL Server Integration Services vers le cloud | Microsoft Docs
ms.date: 04/13/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: ''
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8fb064a5efe77b9b273234f8ccd4f9760a128d92
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Effectuer un « lift-and-shift » des charges de travail SQL Server Integration Services vers le cloud
Vous pouvez maintenant déplacer vos packages et charges de travail SQL Server Integration Services (SSIS) vers le cloud Azure.
-   Stockez et gérez les projets et packages SSIS dans la base de données de catalogues SSIS (SSISDB) sur Azure SQL Database ou SQL Database Managed Instance (préversion).
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
| Dans Azure (SQL Database ou SQL Database Managed Instance (préversion)) | Runtime d’intégration Azure SSIS, un composant d’Azure Data Factory version 2 | Options de montée en charge pour le runtime d’intégration SSIS |
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

## <a name="version-info"></a>Informations de version

Vous pouvez déployer n’importe quel package créé avec l’une des versions de SSIS sur Azure. Quand vous déployez un package sur Azure sans erreur de validation, le package est automatiquement mis à niveau avec le dernier format de package. Le package est donc toujours mis à niveau avec la dernière version de SSIS.

Le processus de déploiement valide chaque package pour vérifier qu’il peut s’exécuter dans Azure SSIS Integration Runtime. Pour plus d’informations, consultez [Valider des packages SSIS déployés sur Azure](ssis-azure-validate-packages.md).

## <a name="prerequisites"></a>Prerequisites

Les fonctionnalités décrites dans cet article nécessitent les versions suivantes de SQL Server Data Tools (SSDT) :
-   Pour Visual Studio 2017, version 15.3 (préversion) ou version ultérieure.
-   Pour Visual Studio 2015, version 17.2 ou version ultérieure.

Pour plus d’informations sur les prérequis dans Azure, consultez [Déployer des packages SSIS sur Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal).

## <a name="provision-ssis-on-azure"></a>Provisionner SSIS sur Azure
Avant de pouvoir déployer et exécuter des packages SSIS dans Azure, vous devez provisionner la base de données de catalogues SSIS (SSISDB) et Azure SSIS Integration Runtime. Suivez les étapes de provisionnement dans cet article : [Déployer des packages SSIS sur Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal).

Le **nom de l’instance SQL Database** qui héberge SSISDB devient la première partie du nom en quatre parties à utiliser quand vous déployez et gérez des packages à partir de SSDT et de SSMS - `<sql_database_name>.database.windows.net`.

Pour plus d’informations sur la connexion à la base de données de catalogues SSIS, consultez [Se connecter à la base de données de catalogues SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

## <a name="design-packages"></a>Concevoir des packages
Vous continuez à **concevoir et générer des packages** localement dans SSDT, ou dans Visual Studio avec SSDT installé.

Pour plus d’informations sur la connexion à des sources de données locales à partir du cloud avec **l’authentification Windows**, consultez [Se connecter à des sources de données locales et des partages de fichiers Azure avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).

Pour plus d’informations sur la connexion à des fichiers et partages de fichiers, consultez [Stocker et récupérer des fichiers sur des partages de fichiers locaux et dans Azure avec SSIS](ssis-azure-files-file-shares.md).

Quand vous provisionnez une instance de SQL Database pour héberger SSISDB, le Feature Pack Azure pour SSIS et le composant redistribuable Access sont également installés. Ces composants fournissent une connectivité à diverses sources de données **Azure** et aux fichiers **Excel et Access**, en plus des sources de données prises en charge par les composants intégrés.

Vous pouvez également installer des composants supplémentaires. Pour plus d’informations, consultez [Installation personnalisée pour le runtime d’intégration SSIS Azure](/azure/articles/data-factory/how-to-configure-azure-ssis-ir-custom-setup.md).

## <a name="deploy-and-run-packages"></a>Déployer et exécuter des packages
Vous devez utiliser le **modèle de déploiement de projet**, et non le modèle de déploiement de package, quand vous déployez des projets dans SSISDB sur Azure.

Pour déployer des projets et exécuter des packages sur Azure, vous pouvez utiliser plusieurs outils et options de script de votre choix :
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (à partir de SSMS, Visual Studio Code ou tout autre outil)
-   Un outil en ligne de commande
-   PowerShell
-   C# et le modèle objet de gestion SSIS

Pour commencer, consultez [Déployer, exécuter et surveiller un package SSIS sur Azure](ssis-azure-deploy-run-monitor-tutorial.md).

## <a name="monitor-packages"></a>Surveiller les packages
Pour surveiller les packages en cours d’exécution dans SSMS, vous pouvez utiliser l’un des outils de compte-rendu suivants dans SSMS.
-   Cliquez avec le bouton droit sur **SSISDB**, puis sélectionnez **Opérations actives** pour ouvrir la boîte de dialogue **Opérations actives**.
-   Sélectionnez un package dans l’Explorateur d’objets, cliquez avec le bouton droit, sélectionnez **Rapports**, **Rapports standard**, puis **Toutes les exécutions**.

## <a name="schedule-packages"></a>Planifier les packages
Pour planifier l’exécution des packages stockés dans SQL Database, vous pouvez utiliser les outils suivants :
-   SQL Server Agent (local)
-   Activité de procédure stockée SQL Server Data Factory

Pour plus d’informations, consultez [Planifier l’exécution d’un package SSIS sur Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Étapes suivantes
Pour bien démarrer avec les charges de travail SSIS sur Azure, consultez les articles suivants :
-   [Déployer des packages SSIS sur Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal)
-   [Déployer, exécuter et surveiller un package SSIS sur Azure](ssis-azure-deploy-run-monitor-tutorial.md)
