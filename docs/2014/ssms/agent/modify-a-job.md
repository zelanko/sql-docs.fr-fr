---
title: Modifier un travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 614c35992be2f85ef15afd0645140746041d083d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62656372"
---
# <a name="modify-a-job"></a>Modifier un travail
  Cette rubrique explique comment modifier les propriétés des travaux [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’agent [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dans à [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]l' [!INCLUDE[tsql](../../includes/tsql-md.md)]aide de, de ou de SQL Server Management Objects.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :** ,  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour modifier un travail, utilisez :**  
  
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
  
1.  Dans l' [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] **Explorateur d’objets,** Connectez-vous à une instance du, puis développez cette instance.  
  
2.  Développez **SQL Server Agent**et **Travaux**, cliquez avec le bouton droit sur le travail à modifier, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du travail** , mettez à jour les propriétés, les étapes, la planification, les alertes et les notifications du travail en utilisant les pages correspondantes.  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-modify-a-job"></a>Pour modifier un travail  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du moteur de base de données et développez-la.  
  
2.  Dans la barre d’outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, utilisez les procédures stockées système suivantes pour modifier un travail.  
  
    -   Exécutez [sp_update_job &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) pour modifier les attributs d’un travail.  
  
    -   Exécutez [sp_update_schedule &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) pour modifier les détails de planification d’une définition de travail.  
  
    -   Exécutez [sp_add_jobstep &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) pour ajouter de nouvelles étapes de travail.  
  
    -   Exécutez [sp_update_jobstep &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) pour modifier les étapes de travail existantes.  
  
    -   Exécutez [sp_delete_jobstep &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) pour supprimer une étape d’un travail.  
  
    -   Procédures stockées supplémentaires pour modifier un travail maître de l'Agent SQL Server :  
  
        -   Exécutez [sp_delete_jobserver &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) pour supprimer un serveur actuellement associé à un travail.  
  
        -   Exécutez [sp_add_jobserver &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) pour associer un serveur au travail en cours.  
  
##  <a name="SMO"></a>Utilisation de SQL Server Management Objects  
 **Pour modifier un travail**  
  
 Utilisez la classe `Job` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d'informations, consultez [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
