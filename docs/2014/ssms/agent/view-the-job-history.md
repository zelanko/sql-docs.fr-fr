---
title: Afficher l’historique des travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- viewing job history
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
- displaying job history
ms.assetid: 3bbd1556-abdb-48a3-b249-546eace76343
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83c5cee010b95d18988b7139fc43b9e1214bd51e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128729"
---
# <a name="view-the-job-history"></a>Afficher l'historique des travaux
  Cette rubrique décrit comment afficher le journal d'historique des travaux de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de SQL Server Management Objects.  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher le journal d'historique des travaux, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-the-job-history-log"></a>Pour afficher le journal d'historique des travaux  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, puis **Travaux**.  
  
3.  Cliquez avec le bouton droit sur un travail, puis cliquez sur **Afficher l’historique**.  
  
4.  Dans la visionneuse du fichier journal, consultez l'historique des travaux.  
  
5.  Pour mettre à jour l'historique des travaux, cliquez sur **Actualiser**. Pour réduire le nombre de lignes affichées, cliquez sur le bouton **Filtre** , puis définissez les paramètres de filtrage.  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-the-job-history-log"></a>Pour afficher le journal d'historique des travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- lists all job information for the NightlyBackups job.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobhistory   
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_help_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql).  
  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 **Pour afficher le journal d'historique des travaux**  
  
 Appelez la méthode `EnumHistory` de la classe `Job` à l'aide d'un langage de programmation tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
