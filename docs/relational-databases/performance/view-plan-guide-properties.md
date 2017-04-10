---
title: "Afficher les propri&#233;t&#233;s du rep&#232;re de plan | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-plan-guides"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.planguideprop.general.f1"
helpviewer_keywords: 
  - "repères de plan [SQL Server], affichage des propriétés du repère de plan"
  - "affichage des propriétés du repère de plan"
ms.assetid: 8c0d2f39-59c1-4168-a649-65473f6a771b
caps.latest.revision: 19
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 19
---
# Afficher les propri&#233;t&#233;s du rep&#232;re de plan
  Vous pouvez afficher les propriétés des repères de plan dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher les propriétés des repères de plan, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 La visibilité des métadonnées dans les affichages catalogue est limitée aux éléments sécurisables qu'un utilisateur détient ou pour lesquels des autorisations lui ont été accordées.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour afficher les propriétés d'un repère de plan  
  
1.  Cliquez sur le signe plus (+) pour développer la base de données dans laquelle vous souhaitez afficher les propriétés d'un repère de plan, puis cliquez sur le signe plus (+) pour développer le dossier **Programmabilité** .  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Repères de plan** .  
  
3.  Cliquez avec le bouton droit sur le repère de plan dont vous voulez afficher les propriétés, puis sélectionnez **Propriétés**.  
  
     Les propriétés suivantes s'affichent dans la boîte de dialogue **Propriétés du repère de plan** .  
  
     **Indicateurs**  
     Affiche les indicateurs de requête ou le plan de requête à appliquer à l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. Lorsqu'un plan de requête est spécifié en tant qu'indicateur, la sortie du plan d'exécution XML s'affiche.  
  
     **Est désactivé**  
     Affiche l'état du repère de plan. Les valeurs possibles sont **True** et **False**.  
  
     **Nom**  
     Affiche le nom du repère de plan.  
  
     **Paramètres**  
     Lorsque le type de portée est SQL ou TEMPLATE, affiche le nom et le type de données de tous les paramètres incorporés dans l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
     **Lot de la portée**  
     Affiche le texte du lot dans lequel l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] apparaît.  
  
     **Nom d'objet de la portée**  
     Lorsque le type de portée est OBJECT, affiche le nom de la procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)], la fonction scalaire définie par l'utilisateur, la fonction table à instructions multiples ou le déclencheur DML dans lequel l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] apparaît.  
  
     **Nom de schéma de la portée**  
     Lorsque le type de portée est OBJECT, affiche le nom du schéma dans lequel l'objet est contenu.  
  
     **Type d'étendue**  
     Affiche le type de l'entité dans laquelle l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] apparaît. Ce type spécifie le contexte pour la mise en correspondance de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] avec le repère de plan. Les valeurs possibles sont **OBJECT**, **SQL**et **TEMPLATE**.  
  
     **Instruction**  
     Affiche l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] par rapport à laquelle le repère de plan est appliqué.  
  
4.  Cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour afficher les propriétés d'un repère de plan  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- If a plan guide named “Guide1” already exists in the AdventureWorks2012 database, delete it.  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID(N'Guide1') IS NOT NULL  
       EXEC sp_control_plan_guide N'DROP', N'Guide1';  
    GO  
    -- creates a plan guide named Guide1 based on a SQL statement  
    EXEC sp_create_plan_guide   
        @name = N'Guide1',   
        @stmt = N'SELECT TOP 1 *   
                  FROM Sales.SalesOrderHeader   
                  ORDER BY OrderDate DESC',   
        @type = N'SQL',  
        @module_or_batch = NULL,   
        @params = NULL,   
        @hints = N'OPTION (MAXDOP 1)';  
    GO  
    -- Gets the name, created date, and all other relevant property information on the plan guide created above.   
    SELECT name AS plan_guide_name,  
       create_date,  
       query_text,  
       scope_type_desc,  
       OBJECT_NAME(scope_object_id) AS scope_object_name,  
       scope_batch,  
       parameters,  
       hints,  
       is_disabled  
    FROM sys.plan_guides  
    WHERE name = N’Guide1’;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sys.plan_guides &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md).  
  
  