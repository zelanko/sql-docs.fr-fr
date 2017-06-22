---
title: "Créer une étape de travail de script ActiveX | Microsoft Docs"
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
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: e6c46c6b-2d61-4571-bc8e-a831cd6e6302
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0da5ce6dc85a7cb58e8852e83e125a37cfc2179f
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="create-an-activex-script-job-step"></a>Créer une étape de travail de script ActiveX
Cette rubrique explique comment créer et définir une étape de travail de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] qui exécute un script ActiveX à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]ou SQL Server Management Objects.  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour créer une étape de travail Transact-SQL, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
[!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid_md.md)]  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-an-activex-script-job-step"></a>Pour créer une étape de travail de script ActiveX  
  
1.  Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, créez un travail ou cliquez avec le bouton droit de la souris sur un travail existant, puis cliquez sur **Propriétés**. Pour plus d'informations sur la création d'un travail, consultez [Création de travaux](../../ssms/agent/create-jobs.md).  
  
3.  Dans la boîte de dialogue **Propriétés du travail** , cliquez sur la page **Étapes** , puis sur **Nouveau**.  
  
4.  Dans la boîte de dialogue **Nouvelle étape du travail** , tapez un **nom d'étape**de travail.  
  
5.  Dans la liste **Type** , cliquez sur **Script ActiveX**.  
  
6.  Dans la liste **Exécuter en tant que** , sélectionnez le compte proxy avec les informations d'identification que le travail utilisera.  
  
7.  Sélectionnez le **langage** dans lequel le script est écrit. Vous pouvez également cliquer sur **Autre** , puis taper le nom du langage de script [!INCLUDE[msCoName](../../includes/msconame_md.md)] ActiveX dans lequel le script va être écrit.  
  
8.  Dans la zone **Commande** , tapez la syntaxe du script qui sera exécuté pour l'étape de travail. Vous pouvez aussi cliquer sur **Ouvrir** et sélectionner un fichier contenant la syntaxe du script.  
  
9. Cliquez sur la page **Avancé** pour paramétrer les options suivantes pour l'étape de travail : l'action à exécuter si l'étape de travail échoue ou réussit, le nombre de tentatives d'exécution de l'étape de travail que doit effectuer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et la fréquence de ces tentatives.  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-create-an-activex-script-job-step"></a>Pour créer une étape de travail de script ActiveX  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- create an ActiveX Script job step written in VBScript that creates a restore point  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a restore point',  
        @subsystem = N'ACTIVESCRIPTING',  
        @command = N'Const RESTORE_POINT = 20  
  
    strComputer = "."  
    Set objWMIService = GetObject("winmgmts:" _  
        & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\default")  
  
    Set objItem = objWMIService.Get("SystemRestore")  
    errResults = objItem.Restore(RESTORE_POINT)',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour créer une étape de travail de script ActiveX**  
  
Utilisez la classe **JobStep** à l’aide du langage de programmation de votre choix, tel que Visual Basic, Visual C# ou PowerShell.  
  

