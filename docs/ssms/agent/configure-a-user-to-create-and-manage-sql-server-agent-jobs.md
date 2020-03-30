---
title: Configure a User to Create and Manage SQL Server Agent Jobs
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6c492a7875eed70cc58efa2dcae8ac180229e5ad
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75246495"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a>Configure a User to Create and Manage SQL Server Agent Jobs
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment configurer un utilisateur de manière à créer et à exécuter des travaux de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour configurer un utilisateur de manière à créer et à gérer des travaux de SQL Server Agent, à l’aide de :**  [SQL Server Management Studio](#SSMS)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="security"></a><a name="Security"></a>Sécurité  
Pour configurer un utilisateur de façon à ce qu’il puisse créer ou exécuter des travaux de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, vous devez d’abord ajouter un compte de connexion SQL Server ou un rôle msdb existant à l’un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données msdb : SQLAgentUserRole, SQLAgentReaderRole, ou SQLAgentOperatorRole.  
  
Par défaut, les membres de ces rôles de base de données peuvent créer leurs propres étapes de travail qui s'exécutent de façon autonome. Si ces utilisateurs non-administrateurs souhaitent exécuter des travaux qui lancent d'autres types d'étapes de travail (par exemple, des packages [!INCLUDE[ssIS](../../includes/ssis_md.md)] ), ils doivent disposer d'un accès à un compte proxy. Tous les membres du rôle de serveur fixe sysadmin sont habilités à créer, à modifier et à supprimer des comptes proxy. Pour plus d’informations sur les autorisations associées à ces rôles de base de données fixes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consultez [Rôles de base de données fixes de SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
#### <a name="permissions"></a><a name="Permissions"></a>Autorisations  
Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Utilisation de SQL Server Management Studio  
**Pour ajouter une connexion SQL ou un rôle msdb à un rôle de base de données fixe de SQL Server Agent**  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur.  
  
2.  Développez **Sécurité**puis **Connexions**.  
  
3.  Cliquez avec le bouton droit sur la connexion à ajouter au rôle de base de données fixe de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, puis sélectionnez **Propriétés**.  
  
4.  Dans la page **Mappage de l'utilisateur** de la boîte de dialogue **Propriétés de la connexion** , sélectionnez la ligne contenant **msdb**.  
  
5.  Sous **Appartenance au rôle de base de données : msdb**, cochez le rôle de base de données fixe de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] approprié.  
  
**Pour configurer un compte proxy de manière à créer et à gérer des étapes de travail de SQL Server Agent**  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur.  
  
2.  Développez **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit de la souris sur **Proxies** , puis sélectionnez **Nouveau proxy**.  
  
4.  Dans la page **Général** de la boîte de dialogue **Nouveau compte de proxy** , indiquez le nom de proxy, le nom d'identification et la description du nouveau proxy. Notez que vous devez créer une information d'identification avant de créer un proxy de SQL Server Agent. Pour plus d’informations sur la création d’une information d’identification, consultez [Procédure : Créer des informations d’identification](https://msdn.microsoft.com/c1e77e91-2a69-40d9-b8b3-97cffc710586) et [CREATE CREDENTIAL (Transact-SQL)](https://msdn.microsoft.com/d5e9ae69-41d9-4e46-b13d-404b88a32d9d).  
  
5.  Activez les sous-systèmes appropriés pour ce proxy.  
  
6.  Sur la page **Principaux** , ajoutez ou supprimez des connexions ou des rôles pour accorder ou refuser un accès au compte proxy.  
  
## <a name="see-also"></a>Voir aussi  
[Implémenter la sécurité de l'Agent SQL Server](../../ssms/agent/implement-sql-server-agent-security.md)  
  
