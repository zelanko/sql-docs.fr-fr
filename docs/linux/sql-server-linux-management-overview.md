---
title: Gérer SQL Server sur Linux
description: Cet article fournit des liens vers les outils et les tâches courantes de gestion pour SQL Server s’exécutant sur Linux.
author: VanMSFT
ms.author: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.openlocfilehash: e38e51eb1db6c335175b2fc55636532df88ac27d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68000055"
---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Choisir l’outil approprié pour gérer SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Il existe plusieurs façons de gérer SQL Server sur Linux. La section suivante fournit une vue d’ensemble rapide des outils d’administration différents et des techniques avec des pointeurs vers d’autres ressources.

## <a name="mssql-conf"></a>mssql-conf 

Le **mssql-conf** outil configure SQL Server sur Linux. Pour plus d’informations, consultez [configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md).

## <a name="transact-sql"></a>Transact-SQL

Presque tout ce que vous pouvez faire dans un outil client également possible avec les instructions Transact-SQL. SQL Server fournit [des vues de gestion dynamique (DMV)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) qui interrogent l’état et la configuration de SQL Server. Il existe également [commandes Transact-SQL](../t-sql/language-reference.md) pour les tâches de gestion de base de données. Vous pouvez exécuter ces commandes dans n’importe quel outil client qui prend en charge la connexion à SQL Server et l’exécution des requêtes Transact-SQL, par exemple [sqlcmd](sql-server-linux-setup-tools.md) ou [Visual Studio Code](sql-server-linux-develop-use-vscode.md).

## <a name="azure-data-studio"></a>Azure Data Studio

Le nouveau Studio de données Azure est un outil multiplateforme pour la gestion de SQL Server. Pour plus d’informations, consultez [Azure Data Studio](../azure-data-studio/what-is.md).

## <a name="sql-server-management-studio-on-windows"></a>SQL Server Management Studio sur Windows

SQL Server Management Studio (SSMS) est une application Windows qui fournit une interface utilisateur graphique pour la gestion de SQL Server. Bien qu’il s’exécute actuellement uniquement sur Windows, vous pouvez l’utiliser pour se connecter à distance à vos instances Linux SQL Server. Pour plus d’informations sur l’utilisation de SSMS pour gérer SQL Server, consultez [utiliser SSMS pour gérer SQL Server sur Linux](sql-server-linux-manage-ssms.md).

## <a name="mssql-cli-preview"></a>MSSQL-cli (version préliminaire)

Microsoft a publié un nouvel outil de script inter-plateformes pour SQL Server, [mssql-cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/). Cet outil est actuellement en version préliminaire.

## <a name="powershell"></a>PowerShell

PowerShell fournit un environnement riche de ligne de commande pour gérer SQL Server sur Linux. Pour plus d’informations, consultez [utiliser PowerShell pour gérer SQL Server sur Linux](sql-server-linux-manage-powershell.md).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server sur Linux, consultez [SQL Server sur Linux](sql-server-linux-overview.md).
