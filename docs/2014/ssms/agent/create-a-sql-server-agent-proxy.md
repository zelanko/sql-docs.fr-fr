---
title: Créer un proxy de SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dfaba668e4f2328610656db6a61f01960814bff0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52784421"
---
# <a name="create-a-sql-server-agent-proxy"></a>Create a SQL Server Agent Proxy
  Cette rubrique explique comment créer un proxy de SQL Server Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Un compte proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définit un contexte de sécurité dans lequel une étape de travail peut être exécutée. Chaque proxy correspond à des informations d'identification de sécurité. Pour définir des autorisations pour une étape de travail particulière, créez un proxy possédant les autorisations requises pour un sous-système de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , puis assignez ce proxy à l'étape de travail.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer un proxy de SQL Server Agent, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous devez créer des informations d'identification avant de créer un proxy si elles ne sont pas disponibles.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent les informations d'identification pour stocker les informations relatives aux comptes d'utilisateur Windows. L'utilisateur spécifié dans l'information d'identification doit être habilité à ouvrir une session en tant que programme de traitement par lots sur l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d'exécution.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vérifie l'accès au sous-système pour un proxy et donne accès au proxy à chaque exécution de l'étape de travail. Si le proxy n'a plus accès au sous-système, l'étape de travail échoue. Sinon, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] emprunte l'identité de l'utilisateur spécifié dans le proxy et exécute l'étape de travail.  
  
-   La création d'un proxy ne modifie pas les autorisations de l'utilisateur spécifié dans l'information d'identification du proxy. Par exemple, vous pouvez créer un proxy pour un utilisateur qui n'est pas autorisé à se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans ce cas, les étapes de travail qui utilisent ce proxy ne sont pas en mesure de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Si la connexion de l'utilisateur a accès au proxy ou que l'utilisateur appartient à un rôle qui y a accès, l'utilisateur peut recourir au proxy dans une étape de travail.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
  
-   Seuls les membres du rôle de serveur fixe **sysadmin** ont l'autorisation de créer, modifier ou supprimer des comptes proxy. Les utilisateurs qui ne sont pas membres de la **sysadmin** rôle serveur fixe doit être ajouté à une de ces [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent de base de données fixé dans le **msdb** base de données pour utiliser des proxys : **SQLAgentUserRole**, **SQLAgentReaderRole**, ou **SQLAgentOperatorRole**.  
  
-   Requiert l'autorisation `ALTER ANY CREDENTIAL` lors de la création des informations d'identification en plus du proxy.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>Pour créer un proxy de SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez créer un proxy sur SQL Server Agent.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Proxys** et sélectionnez **Nouveau proxy**.  
  
4.  Dans la boîte de dialogue **Nouveau compte proxy** , sur la page **Général** , entrez le nom du compte proxy dans la zone **Nom du proxy** .  
  
5.  Dans la zone **Nom d'identification** , entrez le nom des informations d'identification de sécurité que le compte proxy utilisera.  
  
6.  Dans la zone **Description** , entrez une description du compte proxy  
  
7.  Sous **Actif pour les sous-systèmes suivants**, sélectionnez le ou les sous-systèmes appropriés pour ce proxy.  
  
8.  Sur la page **Principaux** , ajoutez ou supprimez des connexions ou des rôles pour accorder ou refuser un accès au compte proxy.  
  
9. Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>Pour créer un proxy de SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
 Pour plus d'informations, consultez :  
  
-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [sp_add_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-proxy-transact-sql)  
  
-   [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql)  
  
  
