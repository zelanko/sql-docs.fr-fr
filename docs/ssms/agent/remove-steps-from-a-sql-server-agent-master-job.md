---
title: Remove Steps from a SQL Server Agent Master Job
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 871e6162-1221-464d-8f7f-7e454dcd9edb
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 80ad67f6a180aaab688f38c7504c1f9338f5f4b2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75246322"
---
# <a name="remove-steps-from-a-sql-server-agent-master-job"></a>Remove Steps from a SQL Server Agent Master Job
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment supprimer des étapes d'un travail maître SQL Server Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Limitations et restrictions  
Un travail maître [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ne peut pas être ciblé sur des serveurs locaux et distants à la fois.  
  
### <a name="security"></a><a name="Security"></a>Sécurité  
  
#### <a name="permissions"></a><a name="Permissions"></a>Autorisations  
Vous pouvez modifier uniquement les travaux dont vous êtes propriétaire, à moins d'être membre du rôle de serveur fixe **sysadmin** . Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a>Pour supprimer des étapes d'un travail maître SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets** , cliquez sur le signe plus (+) pour développer le serveur qui contient le travail dont vous souhaitez supprimer les étapes.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Travaux** .  
  
4.  Cliquez avec le bouton droit sur le travail dont vous voulez supprimer les étapes, puis sélectionnez **Propriétés**.  
  
5.  Dans la boîte de dialogue **Propriétés du travail -** _nom_travail_, sous **Sélectionner une page**, sélectionnez **Étapes**.  

6.  Sous **Liste des étapes du travail**, sélectionnez l'étape du travail à supprimer et cliquez sur **Supprimer**.  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a>Pour supprimer des étapes d'un travail maître SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- removes job step 1 from the job Weekly Sales Data Backup   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1 ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_delete_jobstep (Transact-SQL)](https://msdn.microsoft.com/421ede8e-ad57-474a-9fb9-92f70a3e77e3).  
  
