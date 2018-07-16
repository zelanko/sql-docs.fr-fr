---
title: Autoriser des non-administrateurs à utiliser le moniteur de réplication | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f4a5a83c12acbe24290b28edd5c494ea988ae00f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287002"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a>Autoriser des non-administrateurs à utiliser le Moniteur de réplication
  Cette rubrique explique comment autoriser des non-administrateurs à utiliser le Moniteur de réplication dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Le moniteur de réplication est utilisable par les membres des rôles suivants :  
  
-   Rôle serveur fixe **sysadmin** .  
  
     Ces utilisateurs peuvent surveiller la réplication et avoir un contrôle total sur la modification des propriétés de réplication telles que les planifications d'agents, les profils d'agents, etc.  
  
-   Le `replmonitor` rôle de base de données dans la base de données de distribution.  
  
     Ces utilisateurs peuvent surveiller la réplication mais ne peuvent pas modifier les propriétés de réplication.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour autoriser des non-administrateurs à utiliser le Moniteur de réplication à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Pour autoriser des non-administrateurs à utiliser le moniteur de réplication, un membre de la **sysadmin** rôle serveur fixe doit ajouter l’utilisateur à la base de données de distribution et attribuer à ce dernier le `replmonitor` rôle.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a>Pour autoriser des non-administrateurs à utiliser le moniteur de réplication  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur de distribution, puis développez le nœud du serveur.  
  
2.  Développez **Bases de données**, puis **Bases de données système**et enfin la base de données de distribution (nommée **distribution** par défaut).  
  
3.  Développez **Sécurité**, cliquez avec le bouton droit sur **Utilisateurs**, puis cliquez sur **Nouvel utilisateur**.  
  
4.  Entrez un nom d'utilisateur et une connexion pour l'utilisateur.  
  
5.  Sélectionnez un schéma par défaut de `replmonitor`.  
  
6.  Sélectionnez le `replmonitor` case à cocher dans la **l’appartenance au rôle de base de données** grille.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a>Pour ajouter un utilisateur au rôle de base de données fixe replmonitor  
  
1.  Dans la base de données de distribution sur le serveur de distribution, exécutez [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql). Si l’utilisateur n’est pas répertorié dans `UserName` du jeu de résultats, l’utilisateur doit avoir accès à la base de données de distribution à l’aide de la [CREATE USER &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-user-transact-sql) instruction.  
  
2.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql), en spécifiant la valeur de `replmonitor` pour le **@rolename** paramètre. Si l’utilisateur est répertorié dans `MemberName` du jeu de résultats, l’utilisateur appartient déjà à ce rôle.  
  
3.  Si l’utilisateur n’appartient pas à la `replmonitor` rôle, exécutez [sp_addrolemember &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) sur le serveur de distribution sur la base de données de distribution. Spécifiez la valeur `replmonitor` pour **@rolename** et le nom de l’utilisateur de base de données ou le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] connexion Windows ajoutée pour **@membername**.  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a>Pour supprimer un utilisateur du rôle de base de données fixe replmonitor  
  
1.  Pour vérifier que l’utilisateur appartient à la `replmonitor` rôle, exécutez [sp_helprolemember &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) sur le serveur de distribution sur la base de données de distribution et spécifiez la valeur `replmonitor` pour **@rolename**. Si l'utilisateur n'est pas répertorié dans `MemberName` dans le jeu de résultats, l'utilisateur n'appartient pas à ce rôle.  
  
2.  Si l’utilisateur appartient à la `replmonitor` rôle, exécutez [sp_droprolemember &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) sur le serveur de distribution sur la base de données de distribution. Spécifiez la valeur `replmonitor` pour **@rolename** et le nom de l’utilisateur de base de données ou de la connexion Windows supprimée pour **@membername**.  
  
  
