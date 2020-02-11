---
title: Joindre un rôle | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.MEMBERSHIP.F1
helpviewer_keywords:
- adding a member to a role
- join a role
ms.assetid: 05c8d10d-5823-46c6-8b1a-81722da6a42b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: d1c846f7ed60bbecac64021e9a881312e1f1f64c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63011345"
---
# <a name="join-a-role"></a>joindre un rôle
  Cette rubrique décrit comment affecter des rôles aux utilisateurs des connexions et des bases de données dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Utilisez les rôles dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour gérer efficacement les autorisations. Affectez des autorisations aux rôles, puis ajoutez et supprimez des utilisateurs et des connexions aux rôles. L'utilisation de rôles évite de devoir maintenir individuellement les autorisations pour chaque utilisateur.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge quatre types de rôle :  
  
-   Rôles serveur fixes  
  
-   Rôles de serveur définis par l'utilisateur  
  
-   Rôles de base de données fixes  
  
-   Rôles de base de données définis par l'utilisateur  
  
 Les rôles fixes sont automatiquement disponibles dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les rôles fixes ont les autorisations nécessaires pour accomplir des tâches courantes. Pour plus d'informations sur les rôles fixes, consultez les liens suivants. Les rôles définis par l'utilisateur sont créés par vous-même et peuvent être personnalisés à l'aide des autorisations que vous sélectionnez. Pour plus d'informations sur les rôles définis par l'utilisateur, consultez les liens suivants.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour assigner des rôles aux utilisateurs des connexions et des bases de données, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   La modification du nom d'un rôle de base de données ne modifie pas le numéro d'identification, le propriétaire ou les autorisations du rôle.  
  
-   Les rôles de base de données sont visibles dans les vues de catalogue sys.database_role_members et sys.database_principals.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite `ALTER ANY ROLE` l’autorisation sur la base `ALTER` de données, l’autorisation sur le rôle ou l’appartenance à **db_securityadmin**.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a>Pour ajouter un membre à un rôle serveur fixe  
  
1.  Dans l'Explorateur d'objets, développez le serveur sur lequel vous souhaitez modifier un rôle serveur fixe.  
  
2.  Développez le dossier **Sécurité** .  
  
3.  Développez le dossier **Rôles serveur** .  
  
4.  Cliquez avec le bouton droit sur le rôle à modifier, puis sélectionnez **Propriétés**.  
  
5.  Dans la boîte de dialogue **Propriétés du rôle de serveur-**_server_role_name_ , dans la page **membres** , cliquez sur **Ajouter**.  
  
6.  Dans la boîte de dialogue **Sélectionner la connexion au serveur ou le rôle de serveur** , sous **Entrez les noms des objets à sélectionner (exemples)** , entrez la connexion ou le rôle serveur à ajouter à ce rôle serveur. Vous pouvez également cliquer sur **Parcourir…** et sélectionner l’ensemble ou certains des objets disponibles dans la boîte de dialogue **Rechercher des objets**. Cliquez sur **OK** pour revenir à la boîte de dialogue **Propriétés du rôle de serveur-**_server_role_name_ .  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a>Pour ajouter un membre à un rôle de base de données défini par l'utilisateur  
  
1.  Dans l'Explorateur d'objets, développez le serveur sur lequel vous souhaitez modifier un rôle de base de données défini par l'utilisateur.  
  
2.  Développez le dossier **Bases de données** .  
  
3.  Développez la base de données dans laquelle vous souhaitez modifier un rôle de base de données défini par l'utilisateur.  
  
4.  Développez le dossier **Sécurité** .  
  
5.  Développez le dossier **Rôles** .  
  
6.  Développez le dossier **Rôles serveur** .  
  
7.  Cliquez avec le bouton droit sur le rôle à modifier, puis sélectionnez **Propriétés**.  
  
8.  Dans la boîte **de dialogue Propriétés du rôle de base de données-**_database_role_name_ , dans la page **général** , cliquez sur **Ajouter**.  
  
9. Dans la boîte de dialogue **Sélectionner l’utilisateur ou le rôle de la base de données** , sous **Entrez les noms des objets à sélectionner (exemples)** , entrez la connexion ou le rôle de base de données à ajouter à ce rôle de base de données. Vous pouvez également cliquer sur **Parcourir…** et sélectionner l’ensemble ou certains des objets disponibles dans la boîte de dialogue **Rechercher des objets**. Cliquez sur **OK** pour revenir à la boîte **de dialogue Propriétés du rôle de base de données-**_database_role_name_ .  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a>Pour ajouter un membre à un rôle serveur fixe  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    ALTER SERVER ROLE diskadmin ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql).  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a>Pour ajouter un membre à un rôle de base de données défini par l'utilisateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    ALTER ROLE Marketing ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles de niveau serveur](server-level-roles.md)   
 [Rôles au niveau de la base de données](../authentication-access/database-level-roles.md)   
 [Rôles d’application](../authentication-access/application-roles.md)  
  
  
