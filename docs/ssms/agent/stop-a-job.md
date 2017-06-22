---
title: "Arrêter un travail | Microsoft Docs"
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
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d27aed059ea689f726b6feaf25e22989da0639e7
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="stop-a-job"></a>Arrêter un travail
Cette rubrique explique comment arrêter un travail de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Un travail est une suite d'actions effectuées par SQL Server Agent.  
  
-   **Avant de commencer :**   
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour arrêter un travail, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   Si un travail exécute une étape de type **CmdExec** ou **PowerShell**, le processus en cours d’exécution (par exemple, MyProgram.exe) est obligé de s’arrêter prématurément. Cela peut provoquer un comportement imprévisible ; par exemple, des fichiers utilisés par le processus peuvent être laissés ouverts.  
  
-   Dans le cas d'un travail multiserveur, une instruction STOP pour le travail est envoyée à tous les serveurs cibles du travail.  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-stop-a-job"></a>Pour arrêter un travail  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, **Travaux**, cliquez avec le bouton droit sur le travail à arrêter, puis cliquez sur **Arrêter le travail**.  
  
3.  Pour arrêter plusieurs travaux, cliquez avec le bouton droit sur **Moniteur d’activité des travaux**, puis cliquez sur **Afficher l’activité du travail**. Dans le Moniteur d’activité des travaux, sélectionnez les travaux à arrêter, cliquez avec le bouton droit sur votre sélection, puis cliquez sur **Arrêter les travaux**.  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-stop-a-job"></a>Pour arrêter un travail  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_stop_job (Transact-SQL)](http://msdn.microsoft.com/en-us/64b4cc75-99a0-421e-b418-94e37595bbb0).  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour arrêter un travail**  
  
Appelez la méthode **Stop** de la classe **Job** à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  

