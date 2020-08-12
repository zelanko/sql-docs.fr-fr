---
title: Resize the Job History Log
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 988035cab9bd8fa4035337068ec15032bb702802
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85644787"
---
# <a name="resize-the-job-history-log"></a>Resize the Job History Log

[!INCLUDE[applies-to-version/_ssnoversion.md](../../includes/applies-to-version/sqlserver.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment définir des limites de taille pour les journaux d’historique des travaux de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

- **Avant de commencer :**  

    [Sécurité](#Security)  

- **Pour définir des limites de taille pour les journaux d'historique des travaux, utilisez :**  

    [SQL Server Management Studio](#SSMS)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Avant de commencer  

### <a name="security"></a><a name="Security"></a>Sécurité

Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  

## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Utilisation de SQL Server Management Studio

*Pour redimensionner l’historique des travaux, le journal basé sur la taille brute*

1. Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.

2. Cliquez avec le bouton de droite sur **SQL Server Agent**, puis sélectionnez **Propriétés**.

3. Sélectionnez la page **Historique**, puis vérifiez que la case **Limiter la taille du journal d’historique des travaux** est cochée.

4. Dans la zone **Taille maximale du journal d'historique des travaux** , entrez le nombre maximal de lignes autorisées dans le journal d'historique des travaux.

5. Dans la zone **Nombre maximal de lignes d'historique des travaux par travail** , entrez le nombre maximal de lignes d'historique des travaux autorisées pour un travail.

**Pour redimensionner l’historique des travaux, le journal basé sur le temps :**

1. Dans **l’Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)], puis développez-la.  

2. Cliquez avec le bouton de droite sur **SQL Server Agent**, puis sélectionnez **Propriétés**.

3. Sélectionnez la page **Historique**, puis sélectionnez **Supprimer l'historique de l'agent**.

4. Sélectionnez le nombre approprié de **Jours**, de **Semaines** ou de **Mois**.