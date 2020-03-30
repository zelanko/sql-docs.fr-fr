---
title: Modify the Target Servers for a Job
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a5300935cdbffc501996c7e68ba44b73b2964fa4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75252374"
---
# <a name="modify-the-target-servers-for-a-job"></a>Modify the Target Servers for a Job

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cet article explique comment modifier les serveurs cibles pour les travaux du service de l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="security"></a><a name="Security"></a>Sécurité  
  
#### <a name="permissions"></a><a name="Permissions"></a>Autorisations  
Par défaut, les membres du rôle serveur fixe sysadmin peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes de l'Agent SQL Server suivants dans la base de données msdb :  
  
1.  **SQLAgentUserRole**  
  
2.  **SQLAgentReaderRole**  
  
3.  SQLAgentOperatorRole  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Pour modifier les serveurs cibles pour un travail  
  
1.  Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **l’Agent SQL Server**, développez **Travaux**, cliquez avec le bouton droit sur un travail, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du travail** , sélectionnez la page **Cibles**, puis cliquez sur **Serveur cible local**ou sur **Plusieurs serveurs cibles**.  
  
    Si vous choisissez **Plusieurs serveurs cibles**, désignez les serveurs qui seront les cibles pour le travail en activant la case à cocher figurant à gauche du nom du serveur. Vérifiez que les cases à cocher correspondant aux serveurs qui ne seront pas des cibles sont désactivées.  
  
## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Pour modifier les serveurs cibles pour un travail  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple attribue le travail multiserveur Weekly Sales Backups au serveur SEATTLE2.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
```  
  
Pour plus d’informations, consultez [sp_add_jobserver (Transact-SQL)](https://msdn.microsoft.com/485252cc-0081-490a-9bd1-cbbd68eea286).  
  
## <a name="see-also"></a>Voir aussi  
[Administration automatisée à l'échelle d'une entreprise](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
