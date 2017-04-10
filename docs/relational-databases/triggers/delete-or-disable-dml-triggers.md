---
title: "Supprimer ou d&#233;sactiver les d&#233;clencheurs DML | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-dml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "déclencheurs DML, désactivation"
  - "suppression de déclencheurs DML"
  - "désactivation de déclencheurs DML"
  - "suppression de déclencheurs DML"
  - "suppression de déclencheurs DML"
  - "déclencheurs DML, suppression"
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Supprimer ou d&#233;sactiver les d&#233;clencheurs DML
  Cette rubrique explique comment supprimer ou désactiver un déclencheur DML dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer ou désactiver un déclencheur DML à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   La suppression d'un déclencheur entraîne sa suppression définitive de la base de données actuelle. La table et les données sur lesquelles il est basé ne sont pas affectées. La suppression d'une table supprime automatiquement les déclencheurs qui lui sont associés.  
  
-   Un déclencheur est activé par défaut lors de sa création.  
  
-   La désactivation d'un déclencheur ne le supprime pas. Le déclencheur existe toujours en tant qu'objet dans la base de données actuelle. Il ne s'activera toutefois pas lors de l'exécution d'une instruction INSERT, UPDATE ou DELETE pour laquelle il avait été programmé. Tout déclencheur désactivé peut être à nouveau réactivé. Un déclencheur n'est pas recréé par son activation. Le déclencheur est activé de la même manière que lorsqu'il a été initialement créé.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 La suppression d'un déclencheur DML nécessite une autorisation ALTER sur la table ou la vue sur laquelle le déclencheur est défini.  
  
 Pour désactiver ou activer un déclencheur DML, un utilisateur doit avoir au minimum l'autorisation ALTER pour la table ou la vue sur laquelle le déclencheur a été créé.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour supprimer un déclencheur DML  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez la base de données choisie, développez **Tables**, puis développez la table qui contient le déclencheur que vous souhaitez supprimer.  
  
3.  Développez **Déclencheurs**, cliquez avec le bouton droit sur le déclencheur à supprimer, puis cliquez sur **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer un objet** , vérifiez que le déclencheur correct est spécifié et cliquez sur **OK**.  
  
#### Pour désactiver et activer un déclencheur DML  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez la base de données choisie, développez **Tables**, puis développez la table qui contient le déclencheur que vous souhaitez désactiver.  
  
3.  Développez **Déclencheurs**, cliquez avec le bouton droit sur le déclencheur à désactiver, puis cliquez sur **Désactiver**.  
  
4.  Pour activer le déclencheur, cliquez sur **Activer**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour supprimer un déclencheur DML  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez les exemples suivants dans la fenêtre de requête. Exécutez l'instruction [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md) pour créer le déclencheur `Sales.bonus_reminder` . Pour supprimer le déclencheur, exécutez l'instruction [DROP TRIGGER](../../t-sql/statements/drop-trigger-transact-sql.md) .  
  
```tsql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### Pour désactiver et activer un déclencheur DML  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez les exemples suivants dans la fenêtre de requête. Exécutez l'instruction [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md) pour créer le déclencheur `Sales.bonus_reminder` . Pour désactiver et activer le déclencheur, exécutez les instructions [DISABLE TRIGGER](../../t-sql/statements/disable-trigger-transact-sql.md) et [ENABLE TRIGGER](../../t-sql/statements/enable-trigger-transact-sql.md) , respectivement.  
  
```tsql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```tsql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## Voir aussi  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Obtenir des informations sur les déclencheurs DML](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  