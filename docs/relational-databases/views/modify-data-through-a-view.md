---
title: "Modifier les donn&#233;es par l&#39;interm&#233;diaire d&#39;une vue | Microsoft Docs"
ms.custom: ""
ms.date: "10/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-views"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifications des données [SQL Server], vues"
  - "vues [SQL Server], modification des données via"
  - "modification des données [SQL Server], vues"
ms.assetid: 410e2812-4ebe-48b2-b95f-c7784f1c4336
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Modifier les donn&#233;es par l&#39;interm&#233;diaire d&#39;une vue
  Vous pouvez modifier les données d'une table de base sous-jacente dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Consultez la section « Vues pouvant être mises à jour » dans [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md).  
  
  
###  <a name="Permissions"></a> Permissions  
 Nécessite des autorisations UPDATE, INSERT ou DELETE sur la table cible, selon l'action effectuée.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour modifier les données de table par le biais d'une vue  
  
1.  Dans l' **Explorateur d'objets**, développez la base de données qui contient la vue, puis développez **Vues**.  
  
2.  Cliquez avec le bouton droit sur la vue et sélectionnez **Modifier les 200 lignes du haut**.  
  
3.  Vous devrez peut-être modifier l'instruction SELECT dans le volet **SQL** pour retourner les lignes à modifier.  
  
4.  Dans le volet de **résultats** , recherchez la ligne à modifier ou à supprimer. Pour supprimer la ligne, cliquez dessus avec le bouton droit et sélectionnez **Supprimer**. Pour modifier des données dans une ou plusieurs colonnes, modifiez les données dans la colonne.  
  
    > **IMPORTANT** Vous ne pouvez pas supprimer une ligne si la vue référence plusieurs table de base. Vous pouvez uniquement mettre à jour les colonnes qui appartiennent à une seule table de base.  
  
5.  Pour insérer une ligne, faites défiler les lignes jusqu'à la fin et insérez les nouvelles valeurs.  
  
    > **IMPORTANT !** Vous ne pouvez pas insérer une ligne si la vue référence plusieurs table de base.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour mettre à jour les données de table par le biais d'une vue  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple remplace la valeur des colonnes `StartDate` et `EndDate` d'un employé spécifique par les colonnes de référence dans la vue `HumanResources.vEmployeeDepartmentHistory`. Cette vue retourne des valeurs de deux tables. Cette instruction réussit car les colonnes qui sont modifiées proviennent uniquement d'une des tables de base.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    UPDATE HumanResources.vEmployeeDepartmentHistory  
    SET StartDate = '20110203', EndDate = GETDATE()   
    WHERE LastName = N'Smith' AND FirstName = 'Samantha';   
    GO  
    ```  
  
 Pour plus d’informations, consultez [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md).  
  
#### Pour insérer des données de table par le biais d'une vue  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple insère une nouvelle ligne dans la table de base `HumanResouces.Department` en spécifiant les colonnes appropriées de la vue `HumanResources.vEmployeeDepartmentHistory`. L'instruction réussit car seules les colonnes d'une même table de base sont spécifiées et les autres colonnes de la table de base utilisent des valeurs par défaut.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    INSERT INTO HumanResources.vEmployeeDepartmentHistory (Department, GroupName)   
    VALUES ('MyDepartment', 'MyGroup');   
    GO  
    ```  
  
 Pour plus d’informations, consultez [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md).  
  
  