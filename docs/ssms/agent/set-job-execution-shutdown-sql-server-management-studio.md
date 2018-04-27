---
title: Définir l’arrêt de l’exécution d’un travail (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e55f0b13dad7d10feeb174ca42c66b8ab95c6421
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Définir l'arrêt de l'exécution d'un travail (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment définir le délai pendant lequel [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent doit attendre la fin de l'exécution des travaux avant la fin de l'exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent lui-même dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour définir une heure d'arrêt pour un travail de SQL Server Agent, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Autorisations  
Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent définir la durée pendant laquelle [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent doit attendre la fin de l’exécution des travaux avant la fin de l’exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent lui-même. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-job-execution-shutdown"></a>Pour définir l'arrêt de l'exécution d'un travail  
  
1.  Dans **l’Explorateur d'objets,** , cliquez sur le signe plus pour développer le serveur sur lequel vous souhaitez définir un intervalle d'arrêt d'exécution d'un travail.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** , puis sélectionnez **Propriétés**.  
  
3.  Sous **Sélectionner une page**, sélectionnez **Système de travaux**.  
  
4.  Définissez **l’intervalle du délai d’arrêt** en secondes pour augmenter ou réduire l’intervalle d’arrêt. Cette valeur détermine le délai d'attente pendant lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent attend la fin de l'exécution des travaux avant la fin de l'exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent lui-même.  
  
