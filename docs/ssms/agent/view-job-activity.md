---
title: Afficher l’activité du travail | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 33cf01dda6f512428090d0c12654f43e1b03c0ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65103175"
---
# <a name="view-job-activity"></a>Afficher l’activité du travail
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment afficher l'état d'exécution des travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
Lorsque le service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent démarre, une nouvelle session est créée et la table **sysjobactivity** de la base de données **msdb** est remplie avec tous les travaux définis existants. Cette table enregistre l'activité du travail en cours et son état. Vous pouvez utiliser le Moniteur d'activité des travaux dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour afficher l'état actuel des travaux. Si le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent se termine de manière inattendue, reportez-vous à la table **sysjobactivity** pour déterminer les travaux qui étaient en cours d'exécution au moment de l'interruption du service.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour afficher l'activité des travaux, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-job-activity"></a>Pour afficher l'activité des travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)], puis développez-la.  
  
2.  Développez **SQL Server Agent**.  
  
3.  Cliquez avec le bouton droit sur **Moniteur d’activité des travaux** , puis cliquez sur **Afficher l’activité du travail**.  
  
4.  Dans le **Moniteur d'activité des travaux**, vous trouverez des détails relatifs à chaque travail défini pour ce serveur.  
  
5.  Cliquez avec le bouton droit sur un travail pour le démarrer, l'arrêter, l'activer ou le désactiver, actualiser son état tel qu'il est affiché dans le Moniteur d'activité des travaux, le supprimer ou encore afficher son historique ou ses propriétés.  Pour démarrer, arrêter, activer, désactiver ou actualiser plusieurs travaux, sélectionnez plusieurs lignes dans le Moniteur d'activité des travaux et cliquez avec le bouton droit sur votre sélection.  
  
6.  Pour mettre à jour le Moniteur d'activité des travaux, cliquez sur **Actualiser**. Pour afficher moins de lignes, cliquez sur **Filtre** et saisissez les paramètres de filtre.  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-view-job-activity"></a>Pour afficher l'activité des travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_help_jobactivity (Transact-SQL)](https://msdn.microsoft.com/d344864f-b4d3-46b1-8933-b81dec71f511).  
  
