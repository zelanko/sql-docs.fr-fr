---
title: "Cr&#233;er des contraintes de validation | Microsoft Docs"
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
  - "contraintes de table [SQL Server]"
  - "attachement de contraintes de validation"
  - "colonnes [SQL Server], contraintes"
  - "contraintes [SQL Server], validation"
  - "contraintes de validation, attachement"
ms.assetid: b8756304-9454-4d39-996a-64516831b7df
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Cr&#233;er des contraintes de validation
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Vous pouvez créer une contrainte de validation dans une table pour spécifier les valeurs de données admises dans une ou plusieurs colonnes dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour créer une nouvelle contrainte de validation à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert des autorisations ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour créer une nouvelle contrainte de validation  
  
1.  Dans **l’Explorateur d’objets**, développez la table à laquelle vous souhaitez ajouter une contrainte de validation, cliquez avec le bouton droit sur **Contraintes**, puis cliquez sur **Nouvelle contrainte**.  
  
2.  Dans la boîte de dialogue **Vérifier les contraintes**, cliquez dans le champ **Expression**, puis cliquez sur le bouton de sélection **(…)**.  
  
3.  Dans la boîte de dialogue **Expression de contrainte de validation** , tapez l'expression SQL de la contrainte de validation. Par exemple, pour limiter les entrées dans la colonne `SellEndDate` de la table `Product` à une valeur supérieure ou égale à la date de la colonne `SellStartDate` ou à la valeur NULL, tapez :  
  
    ```  
    SellEndDate >= SellStartDate OR SellEndDate IS NULL  
    ```  
  
     Ou, pour exiger que les entrées dans la colonne `zip` comportent 5 chiffres, tapez :  
  
    ```  
    zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
    ```  
  
    > [!NOTE]  
    >  Veillez à placer toutes les valeurs de contrainte non numériques entre des guillemets simples (').  
  
4.  Cliquez sur **OK**.  
  
5.  Dans la catégorie **Identity**, vous pouvez modifier le nom de la contrainte de validation et ajouter une description (propriété étendue) pour la contrainte.  
  
6.  Dans la catégorie **Concepteur de tables** , vous pouvez définir le moment où la contrainte est appliquée.  
  
    |**S'applique à :**|**Sélectionnez Oui dans les champs suivants :**|  
    |-------------|---------------------------------------------|  
    |Tester la contrainte sur les données qui existaient avant d'avoir créé la contrainte|**Vérifier les données existantes à la création ou à l'activation**|  
    |Appliquer la contrainte lorsqu'une opération de réplication se produit sur cette table|**Appliquer la réplication**|  
    |Appliquer la contrainte lorsqu'une ligne de cette table est insérée ou mise à jour|**Appliquer INSERTs et UPDATEs**|  
  
7.  Cliquez sur **Fermer**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour créer une nouvelle contrainte de validation  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    ALTER TABLE dbo.DocExc   
       ADD ColumnD int NULL   
       CONSTRAINT CHK_ColumnD_DocExc   
       CHECK (ColumnD > 10 AND ColumnD < 50);  
    GO  
    -- Adding values that will pass the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (49);  
    GO  
    -- Adding values that will fail the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (55);  
    GO  
  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  