---
title: "Effacer le journal d’historique des travaux | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba8542dbff7d4dedfac9ac3e43af6ac077dc3e35
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="clear-the-job-history-log"></a>Effacer le journal d'historique des travaux
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique explique comment supprimer le contenu du journal d’historique des travaux de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)] ou SQL Server Management Objects.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour effacer le journal d'historique des travaux, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-clear-the-job-history-log"></a>Pour effacer le journal d'historique des travaux  
  
1.  Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, puis **Travaux**.  
  
3.  Cliquez avec le bouton droit sur un travail, puis cliquez sur **Afficher l’historique**.  
  
4.  Dans la **Visionneuse du fichier journal**, sélectionnez le travail pour lequel vous souhaitez effacer l'historique, puis effectuez une des opérations suivantes :  
  
    -   Cliquez sur **Supprimer**, puis sur **Supprimer tout l'historique** dans la boîte de dialogue **Supprimer l'historique** . Vous pouvez supprimer tous les historique ou uniquement celui qui est antérieur à une date donnée. Si vous souhaitez supprimer tout l'historique, cliquez sur **Supprimer tout l'historique**. Si vous souhaitez supprimer uniquement les historiques anciens, cliquez sur **Supprimer l'historique avant**et spécifiez une date.  
  
    -   Cliquez sur **État du travail** si vous souhaitez effacer l'historique d'un travail multiserveur. Cliquez sur **Travail**, puis sur un nom de travail et enfin sur **Afficher l'historique des travaux distants**.  
  
5.  Cliquez sur **Supprimer**.  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-clear-the-job-history-log"></a>Pour effacer le journal d'historique des travaux  
  
1.  Dans l'**Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour effacer le journal d'historique des travaux**  
  
Utilisez la méthode **PurgeJobHistory** de la classe **JobServer** à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
