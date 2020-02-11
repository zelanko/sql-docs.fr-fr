---
title: Afficher un travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], viewing
- viewing jobs
- SQL Server Agent jobs, viewing
- displaying jobs
ms.assetid: d2241a3f-dbcf-433c-b7bc-f96bdf0eac8c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 50ed3ac0703429f7848a7eb7b4fc9413a0f3e5cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783380"
---
# <a name="view-a-job"></a>View a Job
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cette rubrique explique comment afficher des travaux de l' [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] agent dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] à [!INCLUDE[tsql](../../includes/tsql-md.md)]l’aide de ou de.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher un travail, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Vous pouvez afficher uniquement les travaux dont vous êtes propriétaire, sauf si vous êtes membre du rôle serveur fixe **sysadmin** . Les membres de ce rôle peuvent afficher tous les travaux. Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-a-job"></a>Pour afficher un travail  
  
1.  Dans l' [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] **Explorateur d’objets,** Connectez-vous à une instance du, puis développez cette instance.  
  
2.  Développez **SQL Server Agent**, puis **Travaux**.  
  
3.  Cliquez avec le bouton droit sur un travail, puis sélectionnez **Propriétés**.  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-a-job"></a>Pour afficher un travail  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```sql
    -- lists all aspects of the information for the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_job  
        @job_name = N'NightlyBackups',  
        @job_aspect = N'ALL' ;  
    GO  
    ```  
  
##  <a name="SMO"></a>Utilisation de SQL Server Management Objects  
 **Pour afficher un travail**  
  
 Utilisez la classe `Job` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d'informations, consultez [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
