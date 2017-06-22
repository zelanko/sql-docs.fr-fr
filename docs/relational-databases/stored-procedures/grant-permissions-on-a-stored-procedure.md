---
title: "Accorder des autorisations sur une procédure stockée | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stored-Procs
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c18a425db4969c7ca75a02737c8b64e3360557c5
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="grant-permissions-on-a-stored-procedure"></a>Accorder des autorisations sur une procédure stockée
  Cette rubrique explique comment accorder des autorisations sur une procédure stockée dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)]. Les autorisations peuvent être accordées à un utilisateur existant, à un rôle de base de données ou à un rôle d'application dans la base de données.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour accorder des autorisations sur une procédure stockée à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous ne pouvez pas utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour accorder des autorisations sur des procédures ou des fonctions système. Utilisez les [Accords d'autorisations sur objet](../../t-sql/statements/grant-object-permissions-transact-sql.md) à la place.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Le fournisseur d'autorisations (ou le principal spécifié avec l'option AS) doit posséder l'autorisation elle-même avec l'option GRANT OPTION ou une autorisation plus élevée qui implique l'autorisation accordée. Exige l'autorisation ALTER sur le schéma auquel appartient la procédure ou l'autorisation CONTROL sur la procédure. Pour plus d’informations, consultez [Octroi d’autorisations d’objet &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>Pour accorder des autorisations sur une procédure stockée  
  
1.  Dans l’Explorateur d’objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure, puis développez **Programmabilité**.  
  
3.  Développez **Procédures stockées**, cliquez avec le bouton droit sur la procédure sur laquelle vous voulez accorder des autorisations, puis cliquez sur **Propriétés**.  
  
4.  Dans **Propriétés de la procédure stockée**, sélectionnez la page **Autorisations** .  
  
5.  Pour accorder des autorisations à un utilisateur, à un rôle de base de données ou à un rôle d'application, cliquez sur **Rechercher**.  
  
6.  Dans **Sélectionner des utilisateurs ou des rôles**, cliquez sur **Types d'objets** pour ajouter ou désactiver les utilisateurs et les rôles de votre choix.  
  
7.  Cliquez sur **Parcourir** pour afficher la liste des utilisateurs ou des rôles. Sélectionnez les utilisateurs ou les rôles auxquels les autorisations doivent être accordées.  
  
8.  Dans la grille **Autorisations explicites** , sélectionnez les autorisations à accorder à l'utilisateur ou au rôle spécifiés. Pour obtenir une description des autorisations, consultez [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md).  
  
 Sélectionner **Accorder** indique que le bénéficiaire recevra l'autorisation spécifiée. Sélectionner **Accorder avec** indique que le bénéficiaire de l'autorisation a également la possibilité d'accorder l'autorisation spécifiée à d'autres principaux.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>Pour accorder des autorisations sur une procédure stockée  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Dans cet exemple, l'autorisation `EXECUTE` sur la procédure stockée `HumanResources.uspUpdateEmployeeHireInfo` est accordée à un rôle d'application nommé `Recruiting11`.  
  
```tsql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [Octroi d’autorisations d’objet &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [Créer une procédure stockée](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [Modifier une procédure stockée](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [Supprimer une procédure stockée](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)   
 [Renommer une procédure stockée](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)  
  
  
