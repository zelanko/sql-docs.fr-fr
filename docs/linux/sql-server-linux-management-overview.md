---
title: "Gérer SQL Server sur Linux | Documents Microsoft"
description: "Cette rubrique fournit des liens vers les tâches de gestion courantes et des outils pour SQL Server en cours d’exécution sur Linux."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.custom: 
ms.workload: On Demand
ms.openlocfilehash: f6710b3e7bd40a2589333cebbf94c8b07f9aaa5d
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Choisissez l’outil approprié pour gérer SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Il existe plusieurs façons de gérer 2017 du serveur SQL sur Linux. La section suivante fournit une vue d’ensemble rapide des outils d’administration différents et des techniques avec des pointeurs vers les ressources supplémentaires.

## <a name="mssql-conf"></a>mssql-conf 
Le **mssql-conf** outil configure SQL Server sur Linux. Pour plus d’informations, consultez [configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md).

## <a name="transact-sql"></a>Transact-SQL

Presque tout ce dont vous pouvez faire dans un outil client peut également être accompli avec des instructions Transact-SQL. SQL Server fournit [des vues de gestion dynamique (DMV)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) qui interroger l’état et la configuration de SQL Server. Il existe également [commandes Transact-SQL](https://msdn.microsoft.com/library/bb510741.aspx) pour les tâches de gestion de base de données. Vous pouvez exécuter ces commandes dans n’importe quel outil client qui prend en charge la connexion à SQL Server et exécuter des requêtes Transact-SQL, par exemple [sqlcmd](sql-server-linux-setup-tools.md) ou [Visual Studio Code](sql-server-linux-develop-use-vscode.md).

## <a name="sql-server-operations-studio-preview"></a>SQL Server Operations Studio (version préliminaire)

Nouveau Microsoft SQL opérations Studio (version préliminaire) est un outil d’inter-plateformes de gestion SQL Server. Pour plus d’informations, consultez [Nouveautés opérations Studio (version préliminaire) de Microsoft SQL](../sql-operations-studio/what-is.md).

## <a name="sql-server-management-studio-on-windows"></a>SQL Server Management Studio sur Windows

SQL Server Management Studio (SSMS) est une application Windows qui fournit une interface utilisateur graphique pour la gestion de SQL Server. Bien qu’il s’exécute actuellement uniquement sur Windows, vous pouvez l’utiliser pour se connecter à distance à vos instances de SQL Server de Linux. Pour plus d’informations sur l’utilisation de SSMS pour gérer SQL Server, consultez [SSMS d’utilisation pour gérer SQL Server sur Linux](sql-server-linux-manage-ssms.md).

## <a name="mssql-cli-preview"></a>mssql-cli (preview)

Microsoft a publié un nouvel outil de script inter-plateformes pour SQL Server, [mssql-cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/). Cet outil est actuellement en version préliminaire.

## <a name="powershell"></a>PowerShell

PowerShell fournit un environnement riche de ligne de commande pour gérer SQL Server sur Linux. Pour plus d’informations, consultez [utiliser PowerShell pour gérer SQL Server sur Linux](sql-server-linux-manage-powershell.md).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server sur Linux, consultez [SQL Server sur Linux](sql-server-linux-overview.md).
