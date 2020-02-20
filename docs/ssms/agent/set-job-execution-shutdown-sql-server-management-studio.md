---
title: Définir l'arrêt de l'exécution d'un travail
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bc6f03f982602c65dc8acab6daa18f2ee385f889
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253220"
---
# <a name="set-job-execution-shutdown"></a>Définir l'arrêt de l'exécution d'un travail

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment définir le délai pendant lequel [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit attendre la fin de l’exécution des travaux avant la fin de l’exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent lui-même dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Autorisations  
Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent définir la durée pendant laquelle [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit attendre la fin de l’exécution des travaux avant la fin de l’exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent lui-même. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-job-execution-shutdown"></a>Pour définir l'arrêt de l'exécution d'un travail  
  
1.  Dans **l’Explorateur d'objets,** , cliquez sur le signe plus pour développer le serveur sur lequel vous souhaitez définir un intervalle d'arrêt d'exécution d'un travail.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** , puis sélectionnez **Propriétés**.  
  
3.  Sous **Sélectionner une page**, sélectionnez **Système de travaux**.  
  
4.  Définissez **l’intervalle du délai d’arrêt** en secondes pour augmenter ou réduire l’intervalle d’arrêt. Cette valeur détermine le délai d'attente pendant lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent attend la fin de l'exécution des travaux avant la fin de l'exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent lui-même.  
  
