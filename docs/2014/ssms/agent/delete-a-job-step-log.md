---
title: Supprimer un journal d’étapes de travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- deleting job step logs
- logs [SQL Server], jobs
- removing job step logs
ms.assetid: ee20c6cd-0258-4550-bdb0-71e86a0fb330
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b47d1a14a02ac35ad8df661265597c26d6f41e9
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43816275"
---
# <a name="delete-a-job-step-log"></a>Supprimer un journal d'étapes de travail
  Cette rubrique explique comment supprimer un journal d'étapes de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer un journal d'étapes de travail de SQL Server Agent, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Lorsque des étapes de travail sont supprimées, leur journal de sortie est automatiquement supprimé.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Vous pouvez modifier uniquement les travaux dont vous êtes propriétaire, à moins d'être membre du rôle de serveur fixe **sysadmin** .  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>Pour supprimer un journal d'étapes de travail de SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**et **Travaux**, cliquez avec le bouton droit sur le travail à modifier, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du travail** , supprimez l'étape de travail sélectionnée.  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>Pour supprimer un journal d'étapes de travail de SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- removes the job step log for step 2 in the job Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobsteplog  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 2;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_delete_jobsteplog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql).  
  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 Utilisez les méthodes `DeleteJobStepLogs` de la classe `Job` à l'aide d'un langage de programmation tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez[SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
```  
-- Uses PowerShell to delete all job step log files that have ID values larger than 5.  
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = $srv.JobServer.Jobs["Test Job"]  
$jb.DeleteJobStepLogs(5)  
```  
  
  
