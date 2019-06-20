---
title: Configurer un utilisateur de manière à créer et à gérer des travaux de SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a62f6c2e1ef86a6fcd5e532b2ef413d8142698e6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63253558"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a>Configurer un utilisateur de manière à créer et à gérer des travaux de l'Agent SQL Server
  Cette rubrique explique comment configurer un compte utilisateur pour créer ou exécuter des notifications relatives à des travaux de l'Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour configurer un utilisateur de manière à créer et à gérer des travaux de SQL Server Agent, à l’aide de :**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour configurer un utilisateur de façon à ce qu’il puisse créer ou exécuter des travaux de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, vous devez d’abord ajouter un compte de connexion SQL Server ou un rôle msdb existant à l’un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données msdb : SQLAgentUserRole, SQLAgentReaderRole, ou SQLAgentOperatorRole.  
  
 Par défaut, les membres de ces rôles de base de données peuvent créer leurs propres étapes de travail qui s'exécutent de façon autonome. Si ces utilisateurs non-administrateurs souhaitent exécuter des travaux qui lancent d'autres types d'étapes de travail (par exemple, des packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] ), ils doivent disposer d'un accès à un compte proxy. Tous les membres du rôle de serveur fixe sysadmin sont habilités à créer, à modifier et à supprimer des comptes proxy. Pour plus d’informations sur les autorisations associées à ces rôles de base de données fixes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consultez [Rôles de base de données fixes de SQL Server Agent](sql-server-agent-fixed-database-roles.md).  
  
####  <a name="Permissions"></a> Autorisations  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
 **Pour ajouter une connexion SQL ou un rôle msdb à un rôle de base de données fixe de SQL Server Agent**  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur.  
  
2.  Développez **Sécurité**puis **Connexions**.  
  
3.  Cliquez avec le bouton droit sur la connexion à ajouter au rôle de base de données fixe de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, puis sélectionnez **Propriétés**.  
  
4.  Sur le **mappage de l’utilisateur** page de la **propriétés de la connexion** boîte de dialogue, sélectionnez la ligne contenant `msdb`.  
  
5.  Sous **Appartenance au rôle de base de données : msdb**, cochez le rôle de base de données fixe de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] approprié.  
  
 **Pour configurer un compte proxy de manière à créer et à gérer des étapes de travail de SQL Server Agent**  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur.  
  
2.  Développez **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit de la souris sur **Proxies** , puis sélectionnez **Nouveau proxy**.  
  
4.  Dans la page **Général** de la boîte de dialogue **Nouveau compte de proxy** , indiquez le nom de proxy, le nom d'identification et la description du nouveau proxy. Notez que vous devez créer une information d'identification avant de créer un proxy de SQL Server Agent. Pour plus d’informations sur la création d’une information d’identification, consultez [créer une information d’identification](../../relational-databases/security/authentication-access/create-a-credential.md) et [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).  
  
5.  Activez les sous-systèmes appropriés pour ce proxy.  
  
6.  Sur la page **Principaux** , ajoutez ou supprimez des connexions ou des rôles pour accorder ou refuser un accès au compte proxy.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter la sécurité de l'Agent SQL Server](implement-sql-server-agent-security.md)  
  
  
