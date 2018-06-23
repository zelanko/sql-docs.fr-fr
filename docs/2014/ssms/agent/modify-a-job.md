---
title: Modifier un travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: caceadb3d1cc35bc9adb7a1ac97d03dadad76934
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153171"
---
# <a name="modify-a-job"></a>Modifier un travail
  Cette rubrique explique comment modifier les propriétés des travaux de l'Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de SQL Server Management Objects.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :** ,  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour modifier un travail, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Un travail maître [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ne peut pas être ciblé sur des serveurs locaux et distants à la fois.  
  
###  <a name="Security"></a> Sécurité  
 Vous pouvez modifier uniquement les travaux dont vous êtes propriétaire, à moins d'être membre du rôle de serveur fixe **sysadmin** . Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-a-job"></a>Pour modifier un travail  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Développez **Agent SQL Server**et **Travaux**, cliquez avec le bouton droit sur le travail à modifier, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du travail** , mettez à jour les propriétés, les étapes, la planification, les alertes et les notifications du travail en utilisant les pages correspondantes.  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-modify-a-job"></a>Pour modifier un travail  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du moteur de base de données et développez-la.  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, utilisez les procédures stockées système suivantes pour modifier un travail.  
  
    -   Exécutez [sp_update_job &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) pour modifier les attributs d’un travail.  
  
    -   Exécutez [sp_update_schedule &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) pour modifier les détails de planification d’une définition de travail.  
  
    -   Exécutez [sp_add_jobstep &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) pour ajouter de nouvelles étapes de travail.  
  
    -   Exécutez [sp_update_jobstep &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) pour modifier les étapes de travail préexistantes.  
  
    -   Exécutez [sp_delete_jobstep &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) pour supprimer une étape de travail d’un travail.  
  
    -   Procédures stockées supplémentaires pour modifier un travail maître de l'Agent SQL Server :  
  
        -   Exécutez [sp_delete_jobserver &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) pour supprimer un serveur actuellement associé à un travail.  
  
        -   Exécutez [sp_add_jobserver &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) pour associer un serveur à la tâche en cours.  
  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 **Pour modifier un travail**  
  
 Utilisez la `Job` classe à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual c# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
