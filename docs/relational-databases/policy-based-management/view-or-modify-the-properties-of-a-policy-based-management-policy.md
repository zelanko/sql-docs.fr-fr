---
title: "Afficher ou modifier les propri&#233;t&#233;s d&#39;une strat&#233;gie de gestion bas&#233;e sur des strat&#233;gies | Microsoft Docs"
ms.custom: ""
ms.date: "10/06/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestion basée sur des stratégies, modification des stratégies"
  - "gestion basée sur des stratégies, affichage des stratégies"
ms.assetid: ba805504-5db5-4731-a8da-a0e89cb20c37
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Afficher ou modifier les propri&#233;t&#233;s d&#39;une strat&#233;gie de gestion bas&#233;e sur des strat&#233;gies
  Cette rubrique décrit comment afficher ou modifier les propriétés d'une stratégie de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour afficher les propriétés de toutes les stratégies sur un objet  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur, un objet de serveur, une base de données ou un objet de base de données, pointez sur **Stratégies** et sélectionnez **Afficher**. Pour plus d’informations sur les options disponibles dans la boîte de dialogue **Afficher les stratégies –***nom_objet*, consultez [Boîte de dialogue Afficher les stratégies](../../relational-databases/policy-based-management/view-policies-dialog-box.md).  
  
2.  Lorsque vous avez terminé, cliquez sur **Fermer**.  
  
#### Pour afficher ou modifier les propriétés d'une stratégie spécifique  
  
1.  Dans **l’Explorateur d’objets**, cliquez sur le signe plus (+) pour développer la stratégie de gestion basée sur des stratégies que vous souhaitez afficher ou modifier.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Stratégies** .  
  
5.  Cliquez avec le bouton droit sur la stratégie que vous souhaitez afficher ou modifier, puis sélectionnez **Propriétés**. Pour plus d’informations sur les options disponibles de la boîte de dialogue **Créer une nouvelle stratégie–***nom_stratégie*, consultez [Boîte de dialogue Créer une nouvelle stratégie ou Ouvrir une stratégie, page Général](../../relational-databases/policy-based-management/create-new-policy-or-open-policy-dialog-box-general-page.md) ou [Boîte de dialogue Créer une nouvelle stratégie ou Ouvrir une stratégie, page Description](../../relational-databases/policy-based-management/create-new-policy-or-open-policy-dialog-box-description-page.md).  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour afficher les propriétés d'une stratégie  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       execution_mode,  
       description,  
       is_enabled,  
       job_id  
    FROM syspolicy_policies;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [syspolicy_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syspolicy-policies-transact-sql.md).  
  
  