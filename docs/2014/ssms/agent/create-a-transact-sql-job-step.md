---
title: Créer une étape de travail Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 79791b213f8300053e53f23a7da2acf8e92ae14f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286635"
---
# <a name="create-a-transact-sql-job-step"></a>Créer une étape de travail Transact-SQL
  Cette rubrique indique comment créer une étape de travail de l'Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui exécute des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de SQL Server Management Objects.  
  
 Ces scripts d'étape de travail peuvent appeler des procédures stockées et des procédures stockées étendues. Une même étape de travail [!INCLUDE[tsql](../../includes/tsql-md.md)] peut contenir plusieurs traitements et commandes GO incorporées. Pour plus d'informations sur la création d'un travail, consultez [Création de travaux](create-jobs.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour créer une étape de travail Transact-SQL, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Pour créer une étape de travail Transact-SQL  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, créez un travail ou cliquez avec le bouton droit de la souris sur un travail existant, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du travail** , cliquez sur la page **Étapes** , puis sur **Nouveau**.  
  
4.  Dans la boîte de dialogue **Nouvelle étape du travail** , tapez un **nom d'étape**de travail.  
  
5.  Dans la liste **Type** , cliquez sur **Script Transact-SQL (TSQL)**.  
  
6.  Dans la zone **Commande** , tapez les traitements de commandes [!INCLUDE[tsql](../../includes/tsql-md.md)] ou cliquez sur **Ouvrir** pour sélectionner un fichier [!INCLUDE[tsql](../../includes/tsql-md.md)] à utiliser comme commande.  
  
7.  Cliquez sur **Analyser** pour vérifier votre syntaxe.  
  
8.  Le message « Analyse réussie » s'affiche si votre syntaxe est correcte. Si le système trouve une erreur, corrigez la syntaxe avant de continuer.  
  
9. Cliquez sur la page **Avancé** pour définir les options d'étape de travail, telles que l'action à exécuter lorsque l'étape de travail aboutit ou échoue, le nombre de tentatives d'exécution de l'étape de travail que doit effectuer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le fichier ou la table où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut écrire la sortie de l'étape de travail. Seuls les membres du rôle de serveur fixe **sysadmin** peuvent écrire une sortie d'étape de travail dans un fichier du système d'exploitation. Tous les utilisateurs de SQL Server Agent peuvent consigner une sortie dans une table.  
  
10. Si vous êtes membre du rôle de serveur fixe **sysadmin** et voulez exécuter cette étape de travail avec une connexion SQL différente, sélectionnez la connexion SQL dans la liste **Exécuter en tant qu'utilisateur** .  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Pour créer une étape de travail Transact-SQL  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- creates a job step that that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).  
  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 **Pour créer une étape de travail Transact-SQL**  
  
 Utilisez la `JobStep` classe à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual c# ou PowerShell.  
  
  