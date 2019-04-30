---
title: Attribuer la propriété d’un travail à d’autres utilisateurs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f22d153d55674d5dd615ab50848e4a7fd85a6dcb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63075250"
---
# <a name="give-others-ownership-of-a-job"></a>Attribuer la propriété d’un travail à d’autres utilisateurs
  Cette rubrique explique comment réattribuer la propriété de travaux  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à un autre utilisateur.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#Restrictions), [sécurité](#Security)  
  
-   **Pour attribuer la propriété d'un travail à d'autres utilisateurs, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProc2)  
  
     [Transact-SQL](#TsqlProc2)  
  
     [SQL Server Management Objects](#SMOProc2)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Pour créer un travail, l'utilisateur doit être membre de l'un des rôles de base de données fixes de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou du rôle de serveur fixe **sysadmin** . Un travail ne peut être modifié que par son propriétaire ou par les membres du rôle **sysadmin** . Pour plus d’informations sur les rôles de base de données fixe de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consultez [Rôles de base de données fixe de SQL Server Agent](sql-server-agent-fixed-database-roles.md).  
  
 Vous devez être administrateur système pour modifier le propriétaire d'un travail.  
  
 L'attribution d'un travail à une autre connexion ne garantit pas que le nouveau propriétaire dispose des autorisations nécessaires pour exécuter le travail.  
  
###  <a name="Security"></a> Sécurité  
 Pour des raisons de sécurité, seul le propriétaire du travail ou un membre du rôle **sysadmin** peut modifier la définition du travail. Seuls les membres du rôle serveur fixe **sysadmin** peuvent attribuer la propriété du travail à d'autres utilisateurs et peuvent exécuter n'importe quel travail, quel qu'en soit le propriétaire.  
  
> [!NOTE]  
>  Si vous transférez la propriété d’un travail à un utilisateur qui n’est pas membre du rôle serveur fixe **sysadmin** et que ce travail exécute des étapes qui nécessitent des comptes proxy (par exemple l’exécution de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] ), vérifiez que l’utilisateur en question a accès à ce compte proxy, sinon le travail échouera.  
  
####  <a name="Permissions"></a> Autorisations  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMSProc2"></a> Utilisation de SQL Server Management Studio  
 **Pour attribuer la propriété d'un travail à d'autres utilisateurs**  
  
1.  Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, développez **Travaux**, cliquez avec le bouton droit de la souris sur le travail, puis cliquez sur **Propriétés**.  
  
3.  Dans la liste **Propriétaire** , sélectionnez une connexion. Vous devez être administrateur système pour modifier le propriétaire d'un travail.  
  
     L'attribution d'un travail à une autre connexion ne garantit pas que le nouveau propriétaire dispose des autorisations nécessaires pour exécuter le travail.  
  
##  <a name="TsqlProc2"></a> Utilisation de Transact-SQL  
 **Pour attribuer la propriété d'un travail à d'autres utilisateurs**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du moteur de base de données et développez-la.  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, entrez les instructions suivantes qui utilisent le [sp_manage_jobs_by_login &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql) procédure stockée système. L'exemple suivant réaffecte tous les travaux de `danw` à `fran??oisa`.  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'fran??oisa' ;  
    GO  
    ```  
  
##  <a name="SMOProc2"></a> À l’aide de SQL Server Management Objects  
 **Pour attribuer la propriété d'un travail à d'autres utilisateurs**  
  
1.  Appelez la classe `Job` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour obtenir un exemple de code, consultez [Planification des tâches administratives automatiques dans l’Agent SQL Server](sql-server-agent.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter des travaux](implement-jobs.md)   
 [Créer des travaux](create-jobs.md)  
  
  
