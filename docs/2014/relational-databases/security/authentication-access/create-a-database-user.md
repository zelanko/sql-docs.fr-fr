---
title: Créer un utilisateur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.GENERAL.F1
- sql12.swb.user.securables.f1
helpviewer_keywords:
- database users, creating
- creating users with Management Studio
- mapping users
- users [SQL Server], creating
- database user additions [SQL Server]
- database users, mapping
- CREATE USER [Management Studio]
- users [SQL Server], adding
- mapping database users
ms.assetid: 782798d3-9552-4514-9f58-e87be4b264e4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 97fc758c754f5fc8803e988d55147670fc3ff45b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055440"
---
# <a name="create-a-database-user"></a>Créer un utilisateur de base de données
  Cette rubrique indique comment créer un utilisateur de base de données mappé à un compte de connexion dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. L'utilisateur de base de données est l'identité du compte de connexion lorsqu'il est connecté à la base de données. Il peut utiliser le même nom que celui du compte de connexion, mais cela n'est pas obligatoire. Cette rubrique part du principe qu'il existe déjà un compte de connexion dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la création d’une connexion, consultez [créer une connexion](create-a-login.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Arrière-plan](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer un utilisateur de base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="background"></a>Informations générales sur la <a name="Restrictions"></a>  
 Un utilisateur est un principal de sécurité au niveau de la base de données. Les comptes de connexion doivent être mappés à un utilisateur de base de données pour permettre la connexion à une base de données. Un compte de connexion peut être mappé à différentes bases de données en tant qu'utilisateurs différents, mais il ne peut être mappé que comme utilisateur unique dans chaque base de données. Dans une base de données partiellement autonome, il est possible de créer un utilisateur qui ne dispose pas de compte de connexion. Pour plus d’informations sur les utilisateurs de base de données autonome, consultez [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql). Lorsque l'utilisateur invité d'une base de données est activé, un compte de connexion non mappé à un utilisateur de base de données peut accéder à la base de données en tant qu'utilisateur invité.  
  
> [!IMPORTANT]  
>  L'utilisateur invité est habituellement désactivé. Ne l'activez que lorsque cela est nécessaire.  
  
 En tant que principal de sécurité, il est possible d'accorder des autorisations à des utilisateurs. L'étendue d'un utilisateur est la base de données. Pour se connecter à une base de données spécifique sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un compte de connexion doit être mappé à un utilisateur de base de données. Les autorisations dans la base de données sont accordées et refusées à l'utilisateur de la base de données, pas au compte de connexion.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert l'autorisation `ALTER ANY USER` sur la base de données.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
##### <a name="to-create-a-database-user"></a>Pour créer un utilisateur de base de données  
  
1.  Dans l'Explorateur d'objets, développez le dossier **Bases de données** .  
  
2.  Développez la base de données où créer le nouvel utilisateur de base de données.  
  
3.  Cliquez avec le bouton droit sur le dossier **Sécurité**, pointez sur **Nouveau**, puis sélectionnez **Utilisateur...**.  
  
4.  Dans la **boîte de dialogue utilisateur de base de données-nouveau** , dans la page **général** , sélectionnez l’un des types d’utilisateur suivants dans la liste **type d’utilisateur** : **utilisateur SQL avec connexion**, **utilisateur SQL sans connexion**, **utilisateur mappé à un certificat**, **utilisateur mappé à une clé asymétrique**ou **utilisateur Windows**.  
  
5.  Dans la zone **Nom d'utilisateur** , entrez un nom pour le nouvel utilisateur. Si vous avez choisi **utilisateur Windows** dans la liste **type d’utilisateur** , vous pouvez également cliquer sur les points de suspension **(...)** pour ouvrir la boîte de dialogue **Sélectionner l’utilisateur ou le groupe** .  
  
6.  Dans la zone **Nom de connexion** , entrez l'identifiant de connexion de l'utilisateur. Vous pouvez également cliquer sur les points de suspension **(…)** pour ouvrir la boîte de dialogue **Sélectionner la connexion**. **Nom de connexion** est disponible si vous sélectionnez **Utilisateur SQL avec connexion** ou **Utilisateur Windows** dans la liste **Type d'utilisateur** .  
  
7.  Dans la zone **Schéma par défaut** , spécifie le schéma qui possédera les objets créés par cet utilisateur. Vous pouvez également cliquer sur les points de suspension **(…)** pour ouvrir la boîte de dialogue **Sélectionner le schéma**. **Schéma par défaut** est disponible si vous sélectionnez **Utilisateur SQL avec connexion**, **Utilisateur SQL sans connexion**ou **Utilisateur Windows** dans la liste **Type d'utilisateur** .  
  
8.  Dans la zone **Nom du certificat** , entrez le certificat à utiliser pour l'utilisateur de base de données. Vous pouvez également cliquer sur les points de suspension **(…)** pour ouvrir la boîte de dialogue **Sélectionner le certificat**. **Nom du certificat** est disponible si vous sélectionnez **Utilisateur mappé à un certificat** dans la liste **Type d'utilisateur** .  
  
9. Dans la zone **Nom de la clé asymétrique**  , entrez la clé à utiliser pour l'utilisateur de base de données. Vous pouvez également cliquer sur les points de suspension **(…)** pour ouvrir la boîte de dialogue **Sélectionner la clé asymétrique**. **Nom de la clé asymétrique** est disponible si vous sélectionnez **Utilisateur mappé à une clé asymétrique** dans la liste **Type d'utilisateur** .  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>Options supplémentaires  
 La boîte de dialogue **Nouvel utilisateur de base de données** offre également des options dans quatre pages supplémentaires : **Schémas appartenant à un rôle**, **Appartenance**, **Éléments sécurisables** et **Propriétés étendues**.  
  
-   La page **Schémas appartenant à un rôle** répertorie tous les schémas possibles qui peuvent être détenus par le nouvel utilisateur de base de données. Pour ajouter des schémas à un utilisateur de base de données ou lui en supprimer, sous **Schémas appartenant à cet utilisateur**, activez ou désactivez les cases à cocher en regard de ces schémas.  
  
-   La page **Appartenance** répertorie tous les rôles possibles d'appartenance de base de données qui peuvent être détenus par le nouvel utilisateur de base de données. Pour ajouter des rôles à un utilisateur de base de données ou lui en supprimer, sous **Appartenance au rôle de base de données**, activez ou désactivez les cases à cocher en regard de ces rôles.  
  
-   La page **Éléments sécurisables** répertorie tous les éléments sécurisables possibles et les autorisations sur ces éléments sécurisables qui peuvent être accordées à la connexion.  
  
-   La page **Propriétés étendues** vous permet d'ajouter des propriétés personnalisées aux utilisateurs de base de données. Les options supplémentaires suivantes sont disponibles sur cette page.  
  
     **Sauvegarde de la base de données**  
     Affiche le nom de la base de données sélectionnée. Ce champ est en lecture seule.  
  
     **Classement**  
     Affiche le classement utilisé pour la base de données sélectionnée. Ce champ est en lecture seule.  
  
     **Propriétés**  
     Affiche ou spécifie les propriétés étendues de l'objet. Chaque propriété étendue est constituée d'une paire nom/valeur de métadonnées associées à l'objet.  
  
     **Points de suspension (...)**  
     Cliquez sur le bouton de sélection **(...)** après **valeur** pour ouvrir la boîte **de dialogue valeur de la propriété étendue** . Tapez ou affichez la valeur de la propriété étendue dans cet emplacement de plus grande taille. Pour plus d'informations, consultez [Boîte de dialogue Valeur de la propriété étendue](../../databases/value-for-extended-property-dialog-box.md).  
  
     **Supprimer**  
     Supprime la propriété étendue sélectionnée.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-database-user"></a>Pour créer un utilisateur de base de données  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Creates the login AbolrousHazem with password '340$Uuxwp7Mcxo7Khy'.  
    CREATE LOGIN AbolrousHazem   
        WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
    GO  
  
    -- Creates a database user for the login created above.  
    CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Principaux &#40;moteur de base de données&#41;](principals-database-engine.md)  
  
  
