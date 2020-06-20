---
title: Accorder des autorisations sur une procédure stockée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23ea130b9d2033128adc99413c053d66936e3ccc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064560"
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
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous ne pouvez pas utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour accorder des autorisations sur des procédures ou des fonctions système. Utilisez les [Accords d'autorisations sur objet](/sql/t-sql/statements/grant-object-permissions-transact-sql) à la place.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Le fournisseur d'autorisations (ou le principal spécifié avec l'option AS) doit posséder l'autorisation elle-même avec l'option GRANT OPTION ou une autorisation plus élevée qui implique l'autorisation accordée. Exige l'autorisation ALTER sur le schéma auquel appartient la procédure ou l'autorisation CONTROL sur la procédure. Pour plus d’informations, consultez [Octroi d’autorisations d’objet &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>Pour accorder des autorisations sur une procédure stockée  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure, puis développez **Programmabilité**.  
  
3.  Développez **Procédures stockées**, cliquez avec le bouton droit sur la procédure sur laquelle vous voulez accorder des autorisations, puis cliquez sur **Propriétés**.  
  
4.  Dans **Propriétés de la procédure stockée**, sélectionnez la page **Autorisations** .  
  
5.  Pour accorder des autorisations à un utilisateur, à un rôle de base de données ou à un rôle d'application, cliquez sur **Rechercher**.  
  
6.  Dans **Sélectionner des utilisateurs ou des rôles**, cliquez sur **Types d'objets** pour ajouter ou désactiver les utilisateurs et les rôles de votre choix.  
  
7.  Cliquez sur **Parcourir** pour afficher la liste des utilisateurs ou des rôles. Sélectionnez les utilisateurs ou les rôles auxquels les autorisations doivent être accordées.  
  
8.  Dans la grille **Autorisations explicites** , sélectionnez les autorisations à accorder à l'utilisateur ou au rôle spécifiés. Pour obtenir une description des autorisations, consultez [Autorisations &#40;moteur de base de données&#41;](../security/permissions-database-engine.md).  
  
 Sélectionner **Accorder** indique que le bénéficiaire recevra l'autorisation spécifiée. Sélectionner **Accorder avec** indique que le bénéficiaire de l'autorisation a également la possibilité d'accorder l'autorisation spécifiée à d'autres principaux.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>Pour accorder des autorisations sur une procédure stockée  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Dans cet exemple, l'autorisation `EXECUTE` sur la procédure stockée `HumanResources.uspUpdateEmployeeHireInfo` est accordée à un rôle d'application nommé `Recruiting11`.  
  
```sql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)   
 [GRANT – octroi d’autorisations d’objet &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)   
 [Créer une procédure stockée](../stored-procedures/create-a-stored-procedure.md)   
 [Modifier une procédure stockée](modify-a-stored-procedure.md)   
 [Supprimer une procédure stockée](../stored-procedures/delete-a-stored-procedure.md)   
 [Renommer une procédure stockée](rename-a-stored-procedure.md)  
  
  
