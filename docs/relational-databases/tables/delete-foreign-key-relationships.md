---
title: "Supprimer les relations entre les cl&#233;s &#233;trang&#232;res | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "clés étrangères [SQL Server], suppression"
  - "retrait de clés étrangères"
  - "suppression de clés étrangères"
ms.assetid: 9c9e9ae4-9e03-4137-acb6-b18928a0c4ca
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Supprimer les relations entre les cl&#233;s &#233;trang&#232;res
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Vous pouvez supprimer une contrainte de clé étrangère dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. La suppression d'une contrainte de clé étrangère supprime l'obligation d'appliquer l'intégrité référentielle.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une contrainte de clé étrangère, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour supprimer une contrainte de clé étrangère  
  
1.  Dans l' **Explorateur d'objets**, développez la table avec la contrainte, puis développez **Clés**.  
  
2.  Cliquez avec le bouton droit sur la contrainte, puis cliquez sur **Supprimer**.  
  
3.  Dans la boîte de dialogue **Supprimer l'objet** , cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour supprimer une contrainte de clé étrangère  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.DocExe   
    DROP CONSTRAINT FK_Column_B;   
    GO  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
  