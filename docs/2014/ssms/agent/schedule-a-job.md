---
title: Planifier un travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: abb84377c48778d0c7244c13620fe192b5421ad6
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53369331"
---
# <a name="schedule-a-job"></a>Schedule a Job
  Cette rubrique décrit la méthode à suivre pour planifier un travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Avant de commencer :** ,  
  
     [Sécurité](#Security)  
  
-   **Pour planifier un travail, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a>Pour créer une planification et l'attacher à un travail  
  
1.  Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Développez **Agent SQL Server**, **Travaux**, cliquez avec le bouton droit de la souris sur le travail à planifier, puis sur **Propriétés**.  
  
3.  Sélectionnez la page **Planifications** , puis cliquez sur **Nouvelle**.  
  
4.  Dans la zone **Nom** , attribuez-lui un nom.  
  
5.  Désactivez la case à cocher **Activé** si vous ne souhaitez pas que la planification entre en vigueur directement après sa création.  
  
6.  Pour **Type de planification**, sélectionnez l'une des valeurs suivantes :  
  
    -   Cliquez sur **Lancer automatiquement au démarrage de l'Agent SQL Server** pour démarrer le travail en même temps que le service Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Cliquez sur **Démarrer dès que les processeurs sont inactifs** pour démarrer le travail lorsque les processeurs se trouvent à l'état inactif.  
  
    -   Cliquez sur **Périodique** si vous voulez que la planification s'exécute de façon répétée. Pour définir la planification périodique, renseignez les groupes **Fréquence**, **Fréquence quotidienne**et **Durée** dans la boîte de dialogue.  
  
    -   Cliquez sur **Une fois** si vous voulez que la planification s'exécute une seule fois. Pour définir la planification **Une fois** , renseignez le groupe **Une seule occurrence** dans la boîte de dialogue.  
  
#### <a name="to-attach-a-schedule-to-a-job"></a>Pour attacher une planification à un travail  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Développez **Agent SQL Server**et **Travaux**, cliquez avec le bouton droit sur le travail à planifier, puis cliquez sur **Propriétés**.  
  
3.  Sélectionnez la page **Planifications** , puis cliquez sur **Choisir**.  
  
4.  Sélectionnez la planification à attacher, puis cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue **Propriétés du travail** , double-cliquez sur la planification attachée.  
  
6.  Vérifiez que le paramètre **Date de début** est défini correctement. Si ce n'est pas le cas, définissez la date de début de la planification, puis cliquez sur **OK**.  
  
7.  Dans la boîte de dialogue **Propriétés du travail** , cliquez sur **OK**.  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-schedule-a-job"></a>Pour planifier un travail  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_add_schedule &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) et [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql).  
  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 Utilisez la classe `JobSchedule` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
