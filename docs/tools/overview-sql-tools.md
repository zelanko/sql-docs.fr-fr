---
title: Outils SQL et des utilitaires pour SQL Server, base de données SQL Azure et Azure SQL Data Warehouse | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 1ff16d7a8b2253fc793db00cb46282539415ff86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767367"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>Outils SQL et des utilitaires pour SQL Server, base de données SQL Azure et Azure SQL Data Warehouse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Pour gérer (requête, analyse, etc.), votre base de données que vous avez besoin d’un outil. Alors que vos bases de données peuvent être exécutés dans le cloud, sur Windows, ou sur [Linux](../linux/sql-server-linux-overview.md), votre outil n’a pas besoin d’exécuter sur la même plateforme que la base de données. 

De nombreux outils de base de données sont disponibles, par conséquent, cet article fournit des descriptions et des pointeurs vers des outils disponibles pour travailler avec vos bases de données SQL. Si vous devez déterminer quel outil que vous avez besoin, consultez [quel outil dois-je utiliser ?](#which-tool-should-i-choose).


## <a name="gui-tools-to-manage-databases"></a>Outils d’interface graphique pour gérer des bases de données  

Les outils d’interface graphique utilisateur graphique principal sont les suivantes :

| Outil | Description | S’exécute sur |
|:--|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] est un outil gratuit, léger, pour la gestion des bases de données partout où ils s’exécutent. Cette version préliminaire fournit des fonctionnalités de gestion de base de données, y compris un éditeur Transact-SQL étendue et personnalisable connaître l’état de fonctionnement de vos bases de données. | **[!INCLUDE[name-sos](../includes/name-sos-short.md)] s’exécute sur Windows, macOS et Linux**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Utilisez SQL Server Management Studio (SSMS) pour interroger, concevoir et gérer votre SQL Server, base de données SQL Azure et Azure SQL Data Warehouse. | **SSMS est exécuté sur Windows**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Transformez Visual Studio en un puissant environnement de développement pour SQL Server, base de données SQL Azure et Azure SQL Data Warehouse.| **SSDT s’exécute sur Windows**.|
| [Visual Studio Code](https://code.visualstudio.com/)| Après avoir installé Visual Studio Code, installer le [extension mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) pour le développement de Microsoft SQL Server, base de données SQL Azure et SQL Data Warehouse.| **Visual Studio Code s’exécute sur Windows, macOS et Linux**.|


## <a name="command-line-tools-to-manage-databases"></a>Outils de ligne de commande pour gérer les bases de données

Les principaux outils de ligne de commande sont les suivantes :

| Outil | Description | S’exécute sur |
|:--|:--|:--|
|[**mssql-cli (préversion)**](mssql-cli.md)|**MSSQL-cli** est un outil de ligne de commande interactif pour l’interrogation de SQL Server. | Windows, macOS et Linux|
| [**sqlpackage**](sqlpackage.md) |**Sqlpackage** est un utilitaire de ligne de commande qui automatise plusieurs tâches de développement de base de données. macOS et les versions de Linux de sqlpackage sont actuellement en version préliminaire. | Windows, macOS et Linux|
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** fournit des applets de commande pour travailler avec SQL| Windows, macOS et Linux|
| [**sqlcmd**](sqlcmd-utility.md) |**SQLCMD** utilitaire vous permet d’entrer des instructions Transact-SQL, des procédures système et des fichiers de script à l’invite de commandes. | Windows, macOS et Linux|
|[**bcp**](../2014/tools/bcp-utility.md)|L’utilitaire **b**ulk **c**opy **p**rogram (**bcp**) copie en bloc des données entre une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et un fichier de données dans un format spécifié par l’utilisateur.|Windows, macOS et Linux|
|[**MSSQL-Générateur de script (version préliminaire)**](https://github.com/Microsoft/mssql-scripter)|**MSSQL-scripter** est une expérience de ligne de commande multiplateforme pour les scripts de bases de données SQL Server|Windows, macOS et Linux|
|[**MSSQL-conf**](../linux/sql-server-linux-configure-mssql-conf.md)|**MSSQL-conf** configure SQL Server s’exécutant sur Linux.|Linux|



## <a name="which-tool-should-i-choose"></a>Quel outil dois-je choisir ?

- Vous souhaitez gérer une instance de SQL Server ou de la base de données, dans un éditeur léger sur Windows, Linux ou Mac ? Choisissez [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md)
- Vous souhaitez gérer une instance de SQL Server ou de la base de données sur Windows avec prise en charge complète de l’interface graphique utilisateur ? Choisissez [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- Vous souhaitez créer ou mettre à jour le code de base de données, y compris la validation au moment de compilation, la refactorisation et le concepteur prend en charge sur Windows ? Choisissez [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- Vous souhaitez interroger SQL Server avec un outil de ligne de commande qui propose IntelliSense, syntaxe haute-éclairage, et bien plus encore ? Choisissez [mssql-cli](mssql-cli.md)
- Vous souhaitez écrire des scripts T-SQL dans un éditeur léger sur Windows, Linux ou Mac ? Choisissez [Visual Studio Code](https://code.visualstudio.com/) et le [extension mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)



## <a name="additional-tools"></a>Outils supplémentaires

| Outil | Description |
|:--|:--|
| [Gestionnaire de configuration](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Utilisez le Gestionnaire de Configuration SQL Server pour configurer les services SQL Server et de configurer la connectivité réseau. Configuration Manager s’exécute sur Windows|
| [Assistant de migration SQL Server](../ssma/sql-server-migration-assistant.md) | Utilisez l’Assistant Migration SQL Server pour automatiser la migration de bases de données vers SQL Server à partir de Microsoft Access, DB2, MySQL, Oracle et Sybase.|
| [Distributed Replay](../tools/distributed-replay/install-distributed-replay-overview.md) | Utilisez la fonctionnalité de Distributed Replay pour vous aider à évaluer l’impact de futures mises à niveau de SQL Server. Distributed Replay permet également de vous aider à évaluer l’impact du matériel et de mises à niveau du système d’exploitation et de réglage de SQL Server. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | L’utilitaire ssbdiagnose signale des problèmes dans les conversations Service Broker ou la configuration des services de Service Broker. |

Si vous recherchez des outils supplémentaires qui ne sont pas mentionnés sur cette page, consultez [utilitaires d’invite de commandes SQL](command-prompt-utility-reference-database-engine.md).

