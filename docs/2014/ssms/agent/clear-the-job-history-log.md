---
title: Effacer le journal d’historique des travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 197ead304152598265e61a907097df051bca39ca
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820745"
---
# <a name="clear-the-job-history-log"></a>Effacer le journal d'historique des travaux
  Cette rubrique explique comment supprimer le contenu du journal d'historique des travaux de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de SQL Server Management Objects.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour effacer le journal d'historique des travaux, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-clear-the-job-history-log"></a>Pour effacer le journal d'historique des travaux  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, puis **Travaux**.  
  
3.  Cliquez avec le bouton droit sur un travail, puis cliquez sur **Afficher l’historique**.  
  
4.  Dans la **Visionneuse du fichier journal**, sélectionnez le travail pour lequel vous souhaitez effacer l'historique, puis effectuez une des opérations suivantes :  
  
    -   Cliquez sur **Supprimer**, puis sur **Supprimer tout l'historique** dans la boîte de dialogue **Supprimer l'historique** . Vous pouvez supprimer tous les historique ou uniquement celui qui est antérieur à une date donnée. Si vous souhaitez supprimer tout l'historique, cliquez sur **Supprimer tout l'historique**. Si vous souhaitez supprimer uniquement les historiques anciens, cliquez sur **Supprimer l'historique avant**et spécifiez une date.  
  
    -   Cliquez sur **État du travail** si vous souhaitez effacer l'historique d'un travail multiserveur. Cliquez sur **Travail**, puis sur un nom de travail et enfin sur **Afficher l'historique des travaux distants**.  
  
5.  Cliquez sur **Supprimer**.  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-clear-the-job-history-log"></a>Pour effacer le journal d'historique des travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 **Pour effacer le journal d'historique des travaux**  
  
 Utilisez la méthode `PurgeJobHistory` de la classe `JobServer` à l'aide d'un langage de programmation tel que Visual Basic, Visual C# ou PowerShell. Pour plus d'informations, consultez [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
