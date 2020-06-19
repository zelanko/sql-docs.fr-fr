---
title: Créer une spécification de l’audit du serveur et de la base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlaudit.dbaudit.general.f1
helpviewer_keywords:
- audits [SQL Server], creating database specification
- database audit [SQL Server]
ms.assetid: 26ee85de-6e97-4318-b526-900924d96e62
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0cad01eae45d534f0f74911ce8f57827858cc920
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063226"
---
# <a name="create-a-server-audit-and-database-audit-specification"></a>Créer une spécification de l'audit du serveur et de la base de données
  Cette rubrique explique comment créer un audit de serveur et une spécification d'audit de base de données dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 L'*audit* d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou d'une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] implique le suivi et l'enregistrement des événements qui se produisent sur le système. L’objet *Audit SQL Server* recueille une seule instance des actions et des groupes d’actions au niveau du serveur ou de la base de données à surveiller. L'audit s'effectue au niveau de l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Vous pouvez exécuter plusieurs audits par instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . L’objet *Spécification d’audit de niveau base de données* appartient à un audit. Vous pouvez créer une spécification d'audit de base de données par base de données SQL Server et par audit. Pour plus d’informations, consultez [SQL Server Audit &#40;moteur de base de données&#41;](sql-server-audit-database-engine.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer un audit de serveur et une spécification d'audit de base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
 Les spécifications d'audit de base de données sont des objets non sécurisables qui résident dans une base de données spécifiée. Lorsqu'une spécification d'audit de base de données est créée, elle se trouve dans un état désactivé.  
  
 Lorsque vous créez ou modifiez une spécification de l'audit de la base de données dans une base de données utilisateur, n'incluez pas d'actions d'audit sur des objets dans l'étendue du serveur, tels que les vues système. Sinon, l'audit est créé. Toutefois, les objets dans l'étendue du serveur ne sont pas inclus, et aucune erreur n'est retournée. Pour auditer des objets dans l'étendue du serveur, utilisez une spécification de l'audit de la base de données dans la base de données MASTER.  
  
 Les spécifications d'audit de base de données résident dans la base de données où elles sont créées, à l'exception de la base de données système `tempdb`.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
  
-   Les utilisateurs disposant de l'autorisation ALTER ANY DATABASE AUDIT peuvent créer des spécifications d'audit de base de données et les lier à un audit quelconque.  
  
-   Une fois qu’une spécification d’audit de la base de données est créée, elle peut être affichée par des principaux disposant des autorisations CONTROL SERVER, ALTER ANY DATABASE AUDIT ou du compte sysadmin.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-server-audit"></a>Pour créer un audit de serveur  
  
1.  Dans l'Explorateur d'objets, développez le dossier **Sécurité** .  
  
2.  Cliquez avec le bouton droit sur le dossier **audits** et sélectionnez **nouvel audit...**. Pour plus d’informations, consultez [créer un audit de serveur et une spécification d’audit de serveur](create-a-server-audit-and-server-audit-specification.md).  
  
3.  Lorsque vous avez fini de sélectionner les options, cliquez sur **OK**.  
  
#### <a name="to-create-a-database-level-audit-specification"></a>Pour créer une spécification d'audit de niveau base de données  
  
1.  Dans l'Explorateur d'objets, développez la base de données dans laquelle vous souhaitez créer une spécification d'audit.  
  
2.  Développez le dossier **Sécurité** .  
  
3.  Cliquez avec le bouton droit sur le dossier **spécifications de l’audit de la base de données** et sélectionnez **nouvelle spécification de l’audit de la base de données.**  
  
     Les options suivantes sont disponibles dans la boîte de dialogue **Créer la spécification de l'audit de la base de données** .  
  
     **Nom**  
     Nom de la spécification de l'audit de la base de données. Le nom est généré automatiquement lorsque vous créez une spécification d'audit du serveur, mais vous pouvez le modifier.  
  
     **Audit**  
     Nom d'un audit de base de données existant. Tapez le nom de l'audit ou sélectionnez-le dans la liste.  
  
     **Type d'action de l'audit**  
     Spécifie les groupes d'actions d'audit de niveau base de données et les actions d'audit à capturer. Pour obtenir la liste d’actions d’audit et de groupes d’actions d’audit de niveau base de données, ainsi qu’une description des événements qu’ils contiennent, consultez [Actions et groupes d’actions SQL Server Audit](sql-server-audit-action-groups-and-actions.md).  
  
     **Schéma d'objet**  
     Affiche le schéma du **Nom de l’objet**spécifié.  
  
     **Nom de l’objet**  
     Nom de l'objet à auditer. Disponible uniquement pour les actions d'audit ; ne s'applique pas aux groupes d'audit.  
  
     **Points de suspension (...)**  
     Ouvre la boîte de dialogue **Sélectionner des objets** permettant de rechercher et sélectionner un objet disponible, en fonction du **Type d'action de l'audit**spécifié.  
  
     **Nom principal**  
     Compte par lequel filtrer l'audit pour l'objet audité.  
  
     **Points de suspension (...)**  
     Ouvre la boîte de dialogue **Sélectionner des objets** permettant de rechercher et sélectionner un objet disponible, en fonction du **Nom de l'objet**spécifié.  
  
4.  Lorsque vous avez fini de sélectionner l'option, cliquez sur **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-server-audit"></a>Pour créer un audit de serveur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE master ;  
    GO  
    -- Create the server audit.   
    CREATE SERVER AUDIT Payrole_Security_Audit  
        TO FILE ( FILEPATH =   
    'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA' ) ;   
    GO  
    -- Enable the server audit.   
    ALTER SERVER AUDIT Payrole_Security_Audit   
    WITH (STATE = ON) ;  
    ```  
  
#### <a name="to-create-a-database-level-audit-specification"></a>Pour créer une spécification d'audit de niveau base de données  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple crée une spécification d'audit de base de données appelée `Audit_Pay_Tables` qui audite les instructions SELECT et INSERT par l'utilisateur `dbo` , pour la table `HumanResources.EmployeePayHistory` en fonction de l'audit de serveur défini précédemment.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    -- Create the database audit specification.   
    CREATE DATABASE AUDIT SPECIFICATION Audit_Pay_Tables  
    FOR SERVER AUDIT Payrole_Security_Audit  
    ADD (SELECT , INSERT  
         ON HumanResources.EmployeePayHistory BY dbo )   
    WITH (STATE = ON) ;   
    GO  
  
    ```  
  
 Pour plus d’informations, consultez [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) et [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql).  
  
  
