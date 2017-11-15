---
title: "Créer une planification | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 25801e07842ef52c4b266865b5b5d621cdc7bfef
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-schedule"></a>Créer une planification
Vous pouvez créer une planification pour les travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], de [!INCLUDE[tsql](../../includes/tsql_md.md)]ou de SQL Server Management Objects.  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour créer une planification, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-schedule"></a>Pour créer une planification  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, cliquez avec le bouton droit sur **Travaux**, puis sélectionnez **Gérer les planifications**.  
  
3.  Dans la boîte de dialogue **Gérer les planifications** , cliquez sur **Nouvelle**.  
  
4.  Dans la zone **Nom** , attribuez-lui un nom.  
  
5.  Si vous ne souhaitez pas que la planification entre en vigueur immédiatement après sa création, désactivez la case à cocher **Activé** .  
  
6.  Pour **Type de planification**, sélectionnez l'une des valeurs suivantes :  
  
    -   Pour lancer le travail lorsque les processeurs atteignent une condition d'inactivité, cliquez sur **Démarrer dès que les processeurs sont inactifs**.  
  
    -   Si vous voulez qu'une planification s'exécute de façon répétée, cliquez sur **Périodique**. Pour définir la planification périodique, renseignez les groupes **Fréquence**, **Fréquence quotidienne**et **Durée** dans la boîte de dialogue.  
  
    -   Si vous souhaitez que la planification ne s'exécute qu'une seule fois, cliquez sur **Une fois**. Pour définir la planification **Une fois** , renseignez le groupe **Une seule occurrence** dans la boîte de dialogue.  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-create-a-schedule"></a>Pour créer une planification  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_add_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7).  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour créer une planification**  
  
Utilisez la classe **JobSchedule** à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
