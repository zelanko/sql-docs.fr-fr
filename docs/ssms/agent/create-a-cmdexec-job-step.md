---
title: "Créer une étape de travail CmdExec | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CmdExec jobs
ms.assetid: b48da5b4-6fe7-4eb7-bade-dc7d697c6d5c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ab55ccc01ef81dceb8658b335c33b0439aebd090
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-cmdexec-job-step"></a>Créer une étape de travail CmdExec
Cette rubrique explique comment créer et définir une étape de travail de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] qui utilise un programme exécutable ou une commande de système d'exploitation, à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)] ou de SQL Server Management Objects.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour créer une étape de travail CmdExec, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Par défaut, seuls les membres du rôle de serveur fixe **sysadmin** peuvent créer des étapes de travail CmdExec. Ces étapes de travail s'exécutent sous le contexte du compte de service SQL Server Agent à moins que l'utilisateur **sysadmin** crée un compte proxy. Les utilisateurs qui ne sont pas membres du rôle **sysadmin** peuvent créer des étapes de travail CmdExec s'ils peuvent accéder à un compte proxy CmdExec.  
  
#### <a name="Permissions"></a>Permissions  
Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-cmdexec-job-step"></a>Pour créer une étape de travail CmdExec  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, créez un travail ou cliquez avec le bouton droit de la souris sur un travail existant, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du travail** , cliquez sur la page **Étapes** , puis sur **Nouveau**.  
  
4.  Dans la boîte de dialogue **Nouvelle étape du travail** , tapez un **nom d'étape**de travail.  
  
5.  Dans la liste **Type** , choisissez **Système d’exploitation (CmdExec)**.  
  
6.  Dans la liste **Exécuter en tant que** , sélectionnez le compte proxy avec les informations d'identification que doit utiliser le travail. Par défaut, les étapes de travail CmdExec s'exécutent dans le contexte du compte de service SQL Server Agent.  
  
7.  Dans la zone **Traiter le code de sortie d'une commande réussie** , entrez une valeur comprise entre 0 et 999999.  
  
8.  Dans la zone **Commande** , saisissez la commande du système d'exploitation ou le programme exécutable. Consultez « Utilisation de Transact T-SQL » pour obtenir un exemple.  
  
9. Cliquez sur la page **Avancé** pour définir les options d'étape de travail, telles que l'action à exécuter lorsque l'étape de travail aboutit ou échoue, le nombre de tentatives d'exécution de l'étape de travail que doit effectuer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et le fichier où [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] peut écrire la sortie de l'étape de travail. Seuls les membres du rôle fixe **sysadmin** peuvent écrire la sortie d'étape de travail dans un fichier du système d'exploitation.  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-create-a-cmdexec-job-step"></a>Pour créer une étape de travail CmdExec  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- creates a job step that that uses CmdExec  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'CMDEXEC',  
        @command = C:\clickme_scripts\SQL11\PostBOLReorg GetHsX.exe',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour créer une étape de travail CmdExec**  
  
Utilisez la classe **JobStep** à l’aide du langage de programmation de votre choix, tel que Visual Basic, Visual C# ou PowerShell.  
  

