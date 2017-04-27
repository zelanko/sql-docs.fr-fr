---
title: "Attribuer la propriété d’un travail à d’autres utilisateurs | Microsoft Docs"
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
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d337913274836597bbcdf26947e3884c4c5c8c2a
ms.lasthandoff: 04/11/2017

---
# <a name="give-others-ownership-of-a-job"></a>Attribuer la propriété d’un travail à d’autres utilisateurs
Cette rubrique explique comment réattribuer la propriété de travaux  [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent à un autre utilisateur.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#Restrictions), [Sécurité](#Security)  
  
-   **Pour attribuer la propriété d'un travail à d'autres utilisateurs, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProc2)  
  
    [Transact-SQL](#TsqlProc2)  
  
    [SQL Server Management Objects](#SMOProc2)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
Pour créer un travail, l'utilisateur doit être membre de l'un des rôles de base de données fixes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent ou du rôle de serveur fixe **sysadmin**. Un travail ne peut être modifié que par son propriétaire ou par les membres du rôle **sysadmin** . Pour plus d’informations sur les rôles de base de données fixe de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, consultez [Rôles de base de données fixe de SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Vous devez être administrateur système pour modifier le propriétaire d'un travail.  
  
L'attribution d'un travail à une autre connexion ne garantit pas que le nouveau propriétaire dispose des autorisations nécessaires pour exécuter le travail.  
  
### <a name="Security"></a>Sécurité  
Pour des raisons de sécurité, seul le propriétaire du travail ou un membre du rôle **sysadmin** peut modifier la définition du travail. Seuls les membres du rôle serveur fixe **sysadmin** peuvent attribuer la propriété du travail à d'autres utilisateurs et peuvent exécuter n'importe quel travail, quel qu'en soit le propriétaire.  
  
> [!NOTE]  
> Si vous transférez la propriété d’un travail à un utilisateur qui n’est pas membre du rôle serveur fixe **sysadmin** et que ce travail exécute des étapes qui nécessitent des comptes proxy (par exemple l’exécution de packages [!INCLUDE[ssIS](../../includes/ssis_md.md)] ), vérifiez que l’utilisateur en question a accès à ce compte proxy, sinon le travail échouera.  
  
#### <a name="Permissions"></a>Permissions  
Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMSProc2"></a>Utilisation de SQL Server Management Studio  
**Pour attribuer la propriété d'un travail à d'autres utilisateurs**  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, développez **Travaux**, cliquez avec le bouton droit de la souris sur le travail, puis cliquez sur **Propriétés**.  
  
3.  Dans la liste **Propriétaire** , sélectionnez une connexion. Vous devez être administrateur système pour modifier le propriétaire d'un travail.  
  
    L'attribution d'un travail à une autre connexion ne garantit pas que le nouveau propriétaire dispose des autorisations nécessaires pour exécuter le travail.  
  
## <a name="TsqlProc2"></a>Utilisation de Transact-SQL  
**Pour attribuer la propriété d'un travail à d'autres utilisateurs**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du moteur de base de données et développez-la.  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, entrez les instructions suivantes qui utilisent la procédure stockée système [sp_manage_jobs_by_login (Transact-SQL)](http://msdn.microsoft.com/en-us/832ec15a-6e92-4eb5-8c4a-af4dba79fbaa) . L'exemple suivant réaffecte tous les travaux de `danw` à `françoisa`.  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'françoisa' ;  
    GO  
    ```  
  
## <a name="SMOProc2"></a>Utilisation de SQL Server Management Objects  
**Pour attribuer la propriété d'un travail à d'autres utilisateurs**  
  
1.  Appelez la classe **Job** à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour obtenir un exemple de code, consultez [Planification des tâches administratives automatiques dans SQL Server Agent](http://msdn.microsoft.com/en-us/900242ad-d6a2-48e9-8a1b-f0eea4413c16).  
  
## <a name="see-also"></a>Voir aussi  
[Implémenter des travaux](../../ssms/agent/implement-jobs.md)  
[Créer des travaux](../../ssms/agent/create-jobs.md)  
  

