---
title: Supprimer un ou plusieurs travaux | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, deleting
- dropping jobs
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 67dcdad0-57b2-431c-b77f-4ffc926af93d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0d9df271c457cb0f05f9fdfe70952b6d02224963
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783258"
---
# <a name="delete-one-or-more-jobs"></a>Supprimer un ou plusieurs travaux
  Cette rubrique explique comment supprimer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des travaux de l' [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] agent dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]à [!INCLUDE[tsql](../../includes/tsql-md.md)]l’aide de, de ou de SQL Server Management Objects.  
  
 
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Vous ne pouvez supprimer que les travaux dont vous êtes propriétaire, à moins que vous ne soyez membre du rôle de serveur fixe **sysadmin** .  
  
 
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-job"></a>Pour supprimer un travail  
  
1.  Dans l' [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] **Explorateur d’objets,** Connectez-vous à une instance du, puis développez cette instance.  
  
2.  Développez **Agent SQL Server**, développez **Travaux**, cliquez avec le bouton droit sur le travail à supprimer, puis cliquez sur **Supprimer**.  
  
3.  Dans la boîte de dialogue **Supprimer un objet** , confirmez que le travail à supprimer est sélectionné.  
  
4.  Cliquez sur **OK**.  
  
#### <a name="to-delete-multiple-jobs"></a>Pour supprimer plusieurs travaux  
  
1.  Dans l' [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] **Explorateur d’objets,** Connectez-vous à une instance du, puis développez cette instance.  
  
2.  Développez **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur **moniteur d’activité des travaux**, puis cliquez sur Afficher l’activité du **travail**.  
  
4.  Dans le moniteur d’activité des travaux, sélectionnez les travaux à supprimer, cliquez avec le bouton droit sur la sélection, puis choisissez **Supprimer les travaux**.  
  

  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-job"></a>Pour supprimer un travail  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC sp_delete_job  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql).  

##  <a name="SMO"></a>Utilisation de SQL Server Management Objects  

### <a name="to-delete-multiple-jobs"></a>Pour supprimer plusieurs travaux
  
 Utilisez la classe `JobCollection` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d'informations, consultez [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
