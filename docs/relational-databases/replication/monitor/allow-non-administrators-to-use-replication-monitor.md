---
title: "Autoriser des non-administrateurs &#224; utiliser le Moniteur de r&#233;plication | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Moniteur de réplication, accès des non-administrateurs"
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Autoriser des non-administrateurs &#224; utiliser le Moniteur de r&#233;plication
  Cette rubrique explique comment autoriser des non-administrateurs à utiliser le Moniteur de réplication dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Le moniteur de réplication est utilisable par les membres des rôles suivants :  
  
-   Rôle serveur fixe **sysadmin** .  
  
     Ces utilisateurs peuvent surveiller la réplication et avoir un contrôle total sur la modification des propriétés de réplication telles que les planifications d'agents, les profils d'agents, etc.  
  
-   Rôle de base de données **replmonitor** dans la base de données de distribution.  
  
     Ces utilisateurs peuvent surveiller la réplication mais ne peuvent pas modifier les propriétés de réplication.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour autoriser des non-administrateurs à utiliser le Moniteur de réplication à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Pour autoriser les non-administrateurs à utiliser le moniteur de réplication, un membre de la **sysadmin** rôle serveur fixe doit ajouter l’utilisateur à la base de données de distribution et attribuer à ce dernier le **replmonitor** rôle.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour autoriser des non-administrateurs à utiliser le moniteur de réplication  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur de distribution, puis développez le nœud du serveur.  
  
2.  Développez **bases de données**, développez **bases de données système**, puis développez la base de données de distribution (nommé **distribution** par défaut).  
  
3.  Développez **sécurité**, avec le bouton droit **utilisateurs**, puis cliquez sur **nouvel utilisateur**.  
  
4.  Entrez un nom d'utilisateur et une connexion pour l'utilisateur.  
  
5.  Sélectionnez un schéma par défaut de **replmonitor**.  
  
6.  Activez la case à cocher **replmonitor** dans la grille **Appartenance au rôle de base de données** .  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour ajouter un utilisateur au rôle de base de données fixe replmonitor  
  
1.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_helpuser & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md). Si l’utilisateur n’est pas répertorié dans **nom d’utilisateur** dans le jeu de résultats, l’utilisateur doit avoir accès à la base de données de distribution à l’aide de la [CREATE USER & #40 ; Transact-SQL & #41 ;](../../../t-sql/statements/create-user-transact-sql.md) instruction.  
  
2.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_helprolemember & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md), la valeur **replmonitor** pour la **@rolename** paramètre. Si l'utilisateur est répertorié dans **MemberName** dans le jeu de résultats, l'utilisateur appartient déjà à ce rôle.  
  
3.  Si l’utilisateur n’appartient pas à la **replmonitor** rôle, exécutez [sp_addrolemember & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) sur la base de données de distribution du distributeur. Spécifiez la valeur **replmonitor** pour **@rolename** et le nom de l’utilisateur de base de données ou la connexion Windows [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ajoutée pour **@membername**.  
  
#### Pour supprimer un utilisateur du rôle de base de données fixe replmonitor  
  
1.  Pour vérifier que l’utilisateur appartient à le **replmonitor** rôle, exécutez [sp_helprolemember & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md) sur la base de données de distribution, le distributeur et spécifiez la valeur **replmonitor** pour **@rolename**. Si l’utilisateur n’est pas répertorié dans **MemberName** dans le jeu de résultats, il n’appartient pas à ce rôle.  
  
2.  Si l’utilisateur n’appartient pas à la **replmonitor** rôle, exécutez [sp_droprolemember & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md) sur la base de données de distribution du distributeur. Spécifiez la valeur **replmonitor** pour **@rolename** et le nom de l’utilisateur de base de données ou la connexion Windows supprimée pour **@membername**.  
  
  