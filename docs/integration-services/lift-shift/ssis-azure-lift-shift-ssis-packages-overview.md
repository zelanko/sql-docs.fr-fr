---
title: "Déplacer des charges de travail de SQL Server Integration Services pour le cloud | Documents Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: dbe6f832d4af55ddd15e12fba17a4da490fe19ae
ms.openlocfilehash: 3d22689e440b2a498f76d43ede74ad3f6f756796
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Déplacer des charges de travail de SQL Server Integration Services vers le cloud
Vous pouvez maintenant déplacer vos packages de SQL Server Integration Services (SSIS) et les charges de travail dans le cloud Azure.
-   Stocker et gérer des projets SSIS et les packages dans la base de données de catalogue SSIS (SSISDB) sur la base de données SQL Azure.
-   Exécuter des packages dans une instance de l’exécution d’intégration Azure SSIS, introduite dans le cadre d’Azure Data Factory version 2.
-   Utilisez des outils familiers tels que SQL Server Management Studio (SSMS) pour les tâches courantes.

## <a name="benefits"></a>Avantages
Déplacement de vos charges de travail SSIS local vers Azure présente les avantages suivants :
-   **Réduire les coûts d’exploitation** en réduisant l’infrastructure locale.
-   **Augmenter la haute disponibilité** avec plusieurs nœuds par cluster, ainsi que les fonctionnalités de haute disponibilité de Azure et de base de données SQL Azure.
-   **Augmenter l’évolutivité** avec la possibilité de spécifier plusieurs noyaux par nœud (évolution verticale) et plusieurs nœuds par cluster (montée en charge).
-   **Éviter les limitations** de SSIS en cours d’exécution sur des machines virtuelles.

## <a name="architecture-overview"></a>Présentation de l’architecture
Le tableau suivant souligne les différences entre SSIS localement et SSIS sur Azure. La différence la plus importante est la séparation du stockage de calcul.

| Stockage | Runtime | Extensibilité |
|---|---|---|
| En local (SQL Server) | Runtime SSIS hébergée par SQL Server | SSIS monter en charge (dans SQL Server 2017 et versions ultérieures)<br/><br/>Solutions personnalisées (dans les versions antérieures de SQL Server) |
| Dans Azure (base de données SQL) | Exécution d’intégration Azure SSIS, un composant d’Azure Data Factory version 2 | Options de mise à l’échelle pour la réponse aux incidents de SSIS |
| | | |

Azure Data Factory héberge le moteur d’exécution de packages SSIS sur Azure. Le moteur d’exécution est appelé à l’exécution d’intégration Azure SSIS (IR SSIS).

Lorsque vous configurez la réponse aux incidents de SSIS, vous pouvez monter et montée en puissance parallèle en spécifiant des valeurs pour les options suivantes :
-   La taille du nœud (y compris le nombre de cœurs) et le nombre de nœuds du cluster.
-   L’instance existante de la base de données SQL Azure pour héberger la base de données de catalogue SSIS (SSISDB) et le niveau de service pour la base de données.
-   Les exécutions en parallèle maximales par nœud.

Il vous suffit de configurer la réponse aux incidents SSIS une seule fois. Après cela, vous pouvez utiliser des outils familiers tels que SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) pour déployer, configurer, exécuter, surveiller, planifier et gérer les packages.

Fabrique de données prend également en charge d’autres types de runtime d’intégration. Pour plus d’informations sur la réponse aux incidents de SSIS et les autres types de runtime d’intégration, voir [runtime d’intégration dans Azure Data Factory](/azure/data-factory/concepts-integration-runtime.md).

## <a name="package-features-on-azure"></a>Fonctionnalités de package sur Azure
Lorsque vous configurez une instance de base de données SQL pour héberger SSISDB, Azure Feature Pack pour SSIS et le composant redistribuable accès sont installés. Ces composants fournissent la connectivité aux fichiers Excel et Access et à diverses sources de données Azure. Vous ne pouvez pas installer les composants tiers pour SSIS pour l’instant.

Vous continuez à concevoir et créer des packages sur site dans SSDT, ou dans Visual Studio avec SSDT installé.

Vous devez utiliser le modèle de déploiement de projet, pas le modèle de déploiement de package, pour les projets que vous déployez sur SSISDB sur une base de données SQL Azure.

Le nom de la base de données SQL qui héberge SSISDB devient la première partie du nom en quatre parties à utiliser lorsque vous déployez et gérez les packages à partir de SSDT et SSMS - `<sql_database_name>.database.windows.net`.

Pour plus d’informations sur la façon de se connecter aux sources de données locale à partir du cloud avec l’authentification Windows, consultez [se connecter aux sources de données locale avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).

## <a name="common-tasks"></a>Tâches courantes

### <a name="provision"></a>Approvisionner
Avant de pouvoir déployer et exécuter des packages SSIS dans Azure, vous devez configurer la base de données de catalogue SSISDB et de l’exécution d’intégration Azure SSIS. Suivez l’approvisionnement des étapes dans cet article : [courbes d’élévation et MAJ des packages SQL Server Integration Services (SSIS) pour Azure](/azure/data-factory/quickstart-lift-shift-ssis-packages-powershell.md).

### <a name="deploy-and-run-packages"></a>Déployer et exécuter des packages
Pour déployer des projets et exécuter des packages sur la base de données SQL, vous pouvez utiliser un des différents outils familiers et les options de script :
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (à partir de SSMS, Code de Visual Studio ou un autre outil)
-   Un outil de ligne de commande
-   PowerShell
-   C# et le modèle d’objet de gestion SSIS

### <a name="monitor-packages"></a>Packages de moniteur
Pour surveiller les packages en cours d’exécution dans SSMS, vous pouvez utiliser un des outils de création de rapports suivants dans SSMS.
-   Avec le bouton droit **SSISDB**, puis sélectionnez **opérations actives** pour ouvrir le **opérations actives** boîte de dialogue.
-   Sélectionnez un package dans l’Explorateur d’objets, avec le bouton droit et sélectionnez **rapports**, puis **rapports Standard**, puis **toutes les exécutions**.

### <a name="schedule-packages"></a>Planification des packages
Pour planifier l’exécution des packages stockés dans la base de données SQL, vous pouvez utiliser les outils suivants :
-   L’Agent SQL Server sur site
-   L’activité de procédure stockée données fabrique SQL Server

Pour plus d’informations, consultez [du package SSIS de la planification d’exécution sur Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Étapes suivantes
Pour vous familiariser avec les charges de travail SSIS sur Azure, consultez les articles suivants :
-   [Déplacer des packages SQL Server Integration Services (SSIS) pour Azure](/azure/data-factory/quickstart-lift-shift-ssis-packages-powershell.md)
-   [Déployer, exécuter et surveiller un package SSIS sur Azure](ssis-azure-deploy-run-monitor-tutorial.md)

