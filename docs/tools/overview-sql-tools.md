---
title: Outils de gestion et de requête SQL pour SQL Server, SQL Azure (bases de données SQL Azure, Azure SQL Managed instances, machines virtuelles SQL) et Azure SQL Data Warehouse | Microsoft Docs
description: Outils de gestion et de requête SQL pour SQL Server, SQL Azure (Azure SQL Database, Azure SQL Managed instance, machines virtuelles SQL) et Azure SQL Data Warehouse
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 09/11/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 9c5262dfc610e62f0782b0cc6c8fe523d94d0730
ms.sourcegitcommit: c0fd28306a3b42895c2ab673734fbae2b56f9291
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096873"
---
# <a name="sql-query-and-management-tools-for-sql-server"></a>Outils de gestion et de requête SQL pour SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Pour gérer (interroger, surveiller, etc.) votre base de données, vous avez besoin d’un outil. Si vos bases de données peuvent s’exécuter dans le Cloud, sur Windows ou sur [Linux](../linux/sql-server-linux-overview.md), il n’est pas nécessaire que votre outil s’exécute sur la même plateforme que la base de données.

De nombreux outils de base de données sont disponibles. cet article fournit des descriptions et des pointeurs vers certains des outils disponibles pour utiliser vos bases de données SQL. Si vous avez besoin d’aide pour déterminer l’outil dont vous avez besoin, consultez [quel outil dois-je utiliser?](#which-tool-should-i-choose).

Pour plus d’informations et pour télécharger un outil, sélectionnez les liens dans la colonne outil dans les tableaux suivants. Pour télécharger SQL Server, consultez [installer SQL Server](../database-engine/install-windows/install-sql-server.md).

## <a name="gui-tools-to-manage-databases"></a>Outils d’interface utilisateur graphique pour gérer les bases de données

Les outils suivants fournissent une interface utilisateur graphique (GUI) :

| Outil | Description | S’exécute sur |
|:--|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)]est un outil de poids léger gratuit qui permet de gérer les bases de données où qu’elles soient. Cette version préliminaire fournit des fonctionnalités de gestion de base de données, notamment un éditeur Transact-SQL étendu et des Insights personnalisables dans l’état opérationnel de vos bases de données. | **[!INCLUDE[name-sos](../includes/name-sos-short.md)] s’exécute sur Windows, macOS et Linux**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Utilisez SQL Server Management Studio (SSMS) pour interroger, concevoir et gérer vos SQL Server, Azure SQL Database et Azure SQL Data Warehouse. | **SSMS s’exécute sur Windows**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Transformez Visual Studio en un environnement de développement puissant pour SQL Server, Azure SQL Database et Azure SQL Data Warehouse.| **SSDT s’exécute sur Windows**.|
| [Visual Studio Code](https://code.visualstudio.com/)| Après avoir installé Visual Studio Code, installez l' [extension MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) pour le développement de Microsoft SQL Server, Azure SQL Database et SQL Data Warehouse.| **Visual Studio code s’exécute sur Windows, MacOS et Linux**.|

## <a name="command-line-tools-to-manage-databases"></a>Outils en ligne de commande pour gérer les bases de données

Voici les principaux outils en ligne de commande:

| Outil | Description | S’exécute sur |
|:--|:--|:--|
|[**mssql-cli (préversion)** ](mssql-cli.md)|**MSSQL-CLI** est un outil de ligne de commande interactif pour l’interrogation de SQL Server. | Windows, macOS et Linux|
| [**sqlpackage**](sqlpackage.md) |**SqlPackage** est un utilitaire de ligne de commande qui automatise plusieurs tâches de développement de base de données. les versions macOS et Linux de SqlPackage sont actuellement en version préliminaire. | Windows, macOS et Linux|
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** fournit des applets de commande pour l’utilisation de SQL| Windows, macOS et Linux|
| [**sqlcmd**](sqlcmd-utility.md) |l’utilitaire **sqlcmd** vous permet d’entrer des instructions Transact-SQL, des procédures système et des fichiers de script à l’invite de commandes. | Windows, macOS et Linux|
|[**bcp**](https://docs.microsoft.com/sql/tools/bcp-utility?view=sql-server-2014)|L’utilitaire **b**ulk **c**opy **p**rogram (**bcp**) copie en bloc des données entre une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et un fichier de données dans un format spécifié par l’utilisateur.|Windows, macOS et Linux|
|[**mssql-scripter (préversion)** ](https://github.com/Microsoft/mssql-scripter)|**MSSQL-Scripter** est une expérience de ligne de commande multiplateforme pour l’écriture de scripts SQL Server les bases de données|Windows, macOS et Linux|
|[**mssql-conf**](../linux/sql-server-linux-configure-mssql-conf.md)|**MSSQL-conf** configure SQL Server s’exécutant sur Linux.|Linux|

## <a name="which-tool-should-i-choose"></a>Quel outil dois-je choisir ?

- Voulez-vous gérer une instance ou une base de données SQL Server, dans un éditeur léger sur Windows, Linux ou Mac? Choisissez [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md)
- Voulez-vous gérer une instance ou une base de données SQL Server sur Windows avec une prise en charge de l’interface graphique utilisateur complète? Choisissez [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- Voulez-vous créer ou gérer le code de base de données, y compris la validation au moment de la compilation, la refactorisation et la prise en charge du concepteur sur Windows? Choisissez [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- Voulez-vous interroger SQL Server avec un outil en ligne de commande qui intègre IntelliSense, la syntaxe haute, et bien plus? Choisir [MSSQL-CLI](mssql-cli.md)
- Voulez-vous écrire des scripts T-SQL dans un éditeur léger sur Windows, Linux ou Mac? Choisir [Visual Studio code](https://code.visualstudio.com/) et l' [extension MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="additional-tools"></a>Outils supplémentaires

| Outil | Description |
|:--|:--|
| [Gestionnaire de configuration](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Utilisez Gestionnaire de configuration SQL Server pour configurer les services SQL Server et configurer la connectivité réseau. Configuration Manager s’exécute sur Windows|
| [Assistant de migration SQL Server](../ssma/sql-server-migration-assistant.md) | Utilisez l’Assistant Migration SQL Server pour automatiser la migration de bases de données vers SQL Server à partir de Microsoft Access, DB2, MySQL, Oracle et Sybase.|
| [Assistant Expérimentation de base de données](../dea/database-experimentation-assistant-overview.md) | Utilisez Assistant Expérimentation de base de données pour évaluer une version ciblée de SQL pour une charge de travail donnée. |
| [Distributed Replay](../tools/distributed-replay/install-distributed-replay-overview.md) | Utilisez la fonctionnalité Distributed Replay pour vous aider à évaluer l’impact des futures mises à niveau de SQL Server. Vous pouvez également utiliser Distributed Replay pour évaluer l’impact des mises à niveau du matériel et du système d’exploitation, et SQL Server le paramétrage. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | L’utilitaire ssbdiagnose signale des problèmes dans Service Broker conversations ou dans la configuration des services Service Broker. |

Si vous recherchez des outils supplémentaires qui ne sont pas mentionnés sur cette page, consultez [utilitaires d’invite de commandes SQL](command-prompt-utility-reference-database-engine.md).