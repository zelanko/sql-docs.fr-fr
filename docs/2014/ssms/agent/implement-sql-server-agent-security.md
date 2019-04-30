---
title: Implémenter la sécurité de SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, security
- security [SQL Server Agent], about security
- security [SQL Server Agent]
- security [SQL Server], SQL Server Agent
ms.assetid: d770d35c-c8de-4e00-9a85-7d03f45a0f0d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 52537ac126115fbde3d7d0fb1a13f61f1d25cf15
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63137518"
---
# <a name="implement-sql-server-agent-security"></a>Implémenter la sécurité de l'Agent SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent permet à l’administrateur de la base de données d’exécuter chaque étape de travail dans un contexte de sécurité qui a uniquement les autorisations requises pour effectuer cette étape, ce qui est déterminé par un proxy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Pour définir des autorisations pour une étape de travail particulière, créez un proxy possédant les autorisations requises, puis assignez ce proxy à l'étape de travail. Un proxy peut être spécifié pour plusieurs étapes de travail. Pour les étapes de travail qui requièrent les mêmes autorisations, vous utilisez le même proxy.  
  
 La section suivante explique quel rôle de base de données vous devez accorder aux utilisateurs pour qu'ils puissent créer ou exécuter des travaux à l'aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="granting-access-to-sql-server-agent"></a>Octroi de l'autorisation d'accéder à SQL Server Agent  
 Pour utiliser l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les utilisateurs doivent être membres de l'un ou de tous les rôles de base de données fixes suivants :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Ces rôles sont stockés dans la base de données **msdb** . Par défaut, aucun utilisateur n'est membre de ces rôles de base de données. L'appartenance à ces rôles doit être accordée explicitement. Les utilisateurs qui sont membres du rôle serveur fixe **sysadmin** ont un accès complet à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent et ne doivent pas nécessairement être membres de ces rôles de base de données fixes pour utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Si un utilisateur n’est pas membre de ces rôles de base de données ou du rôle **sysadmin** , le nœud de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ne leur est pas accessible quand ils se connectent à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Les membres de ces rôles de base de données peuvent afficher et exécuter les travaux dont ils sont propriétaires, et créer des étapes de travail qui s'exécutent comme un compte proxy existant. Pour en savoir plus sur les autorisations spécifiques associées à chacun de ces rôles, consultez [Rôles de base de données fixes de SQL Server Agent](sql-server-agent-fixed-database-roles.md).  
  
 Les membres du rôle serveur fixe **sysadmin** sont habilités à créer, à modifier et à supprimer des comptes proxy. Les membres du rôle **sysadmin** sont habilités à créer des étapes de travail qui ne spécifient pas un proxy, mais s’exécutent plutôt comme le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, qui est le compte utilisé pour démarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="guidelines"></a>Consignes  
 Pour améliorer la sécurité de votre implémentation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, suivez les instructions suivantes :  
  
-   Créez des comptes utilisateur dédiés spécifiquement pour les proxys et utilisez uniquement ces comptes utilisateur proxy pour exécuter les étapes de travail.  
  
-   Octroyez exclusivement les autorisations nécessaires aux comptes utilisateur proxy. Octroyez exclusivement les autorisations réellement requises pour exécuter les étapes de travail qui sont assignées à un compte proxy donné.  
  
-   N’exécutez pas le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sous un compte Microsoft Windows qui est membre du groupe **Administrateurs** de Windows.  
  
-   Les proxys sont aussi sécurisés que la banque d'informations d'identification de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Si les opérations d'écriture utilisateur peuvent écrire dans le journal des événements NT, elles peuvent déclencher des alertes par le biais de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Ne spécifiez pas le compte administrateur NT en tant que compte de service ou compte proxy.  
  
-   Notez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ont chacun accès aux ressources de l’autre. Les deux services partagent un espace de processus unique et l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un sysadmin sur le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Lorsque TSX est inscrit avec un MSX, le MSX sysadmin obtient le contrôle total sur l'instance TSX de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   ACE est une extension et ne peut pas s'appeler elle-même. ACE est appelé par le programme de chaînage ScenarioEngine.exe, également appelé Microsoft.SqlServer.Chainer.Setup.exe, ou peut être appelé par un autre processus hôte.  
  
-   ACE dépend des DLL de configuration suivantes détenues par SSDP, car ces API de DLL sont appelées par ACE :  
  
    -   **SCO** - Microsoft.SqlServer.Configuration.Sco.dll, y compris les nouvelles validations SCO pour les comptes virtuels  
  
    -   **Cluster** - Microsoft.SqlServer.Configuration.Cluster.dll  
  
    -   **SFC** - Microsoft.SqlServer.Configuration.SqlConfigBase.dll  
  
    -   **Extension** - Microsoft.SqlServer.Configuration.ConfigExtension.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles prédéfinis](../../reporting-services/security/role-definitions-predefined-roles.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)   
 [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)   
 [Centre de sécurité pour le moteur de base de données SQL Server et la base de données SQL Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
