---
title: Créer des relations de clé étrangère | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], creating
ms.assetid: 867a54b8-5be4-46e6-9702-49ae6dabf67c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8b5789a277eac84d9753a180b418c05c5fd71d09
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794771"
---
# <a name="create-foreign-key-relationships"></a>Créer des relations de clé étrangère
  Cette rubrique explique comment créer des relations de clé étrangère dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Vous créez une relation entre deux tables lorsque vous voulez associer des lignes d'une table à des lignes appartenant à une autre table.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer des relations de clé étrangère à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Une contrainte de clé étrangère ne doit pas forcément être liée seulement à une contrainte de clé primaire d'une autre table. Elle peut également être définie pour référencer les colonnes d'une contrainte UNIQUE d'une autre table.  
  
-   Lorsqu'une valeur différente de NULL est entrée dans la colonne d'une contrainte FOREIGN KEY, la valeur doit exister dans la colonne référencée. Dans le cas contraire, le système retourne un message d'erreur signalant une violation de clé étrangère. Pour vous assurer que toutes les valeurs d'une contrainte de clé étrangère composite sont vérifiées, spécifiez NOT NULL pour toutes les colonnes participant à la contrainte.  
  
-   Les contraintes FOREIGN KEY ne peuvent faire référence qu'à des tables au sein de la même base de données sur le même serveur. L'intégrité référentielle inter-base de données doit être implémentée via les déclencheurs. Pour plus d’informations, consultez [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
-   Les contraintes FOREIGN KEY peuvent faire référence à une autre colonne dans la même table. On appelle habituellement ce mécanisme « auto-référence ».  
  
-   Une contrainte FOREIGN KEY spécifiée au niveau de la colonne ne peut lister qu'une colonne de référence. Cette colonne doit avoir le même type de données que la colonne pour laquelle la contrainte est définie.  
  
-   Une contrainte FOREIGN KEY spécifiée au niveau de la table doit avoir le même nombre de colonnes de référence que le nombre de colonnes de la liste des colonnes de la contrainte. Le type de données de chaque colonne de référence doit également être identique à la colonne de référence correspondante dans la liste des colonnes.  
  
-   Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n'a pas de limite prédéfinie du nombre de contraintes FOREIGN KEY qu'une table peut contenir et qui référencent d'autres tables ou du nombre de contraintes FOREIGN KEY possédées par d'autres tables qui font référence à une table spécifique. Cependant, le nombre réel de contraintes FOREIGN KEY qui peuvent être utilisées est limité par la configuration matérielle et par la conception de la base de données et de l'application. Nous vous recommandons de ne pas insérer plus de 253 contraintes FOREIGN KEY dans une table et qu'une même table ne soit pas référencée par plus de 253 contraintes FOREIGN KEY.  
  
-   Les contraintes FOREIGN KEY ne sont pas appliquées dans les tables temporaires.  
  
-   Si une clé étrangère est définie sur une colonne avec le type de données CLR défini par l'utilisateur, l'implémentation du type doit prendre en charge le tri binaire. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
-   Une colonne de type `varchar(max)` ne peut participer à une contrainte FOREIGN KEY que si la clé primaire qu'elle référence est également définie comme étant de type `varchar(max)`.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 La création d'une nouvelle table avec une clé étrangère nécessite une autorisation CREATE TABLE dans la base de données et une autorisation ALTER pour le schéma dans lequel la table a été créée.  
  
 La création d'une clé étrangère dans une table existante nécessite l'autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-foreign-key-relationship-in-table-designer"></a>Pour créer une relation de clé étrangère dans le Concepteur de tables  
  
1.  Dans l'Explorateur d'objets, cliquez avec le bouton droit sur la table qui se trouve du côté clé étrangère de la relation et cliquez sur **Conception**.  
  
     La table s'ouvre dans le **Concepteur de tables**.  
  
2.  Dans le menu **Concepteur de tables** , cliquez sur **Relations**.  
  
3.  Dans la boîte de dialogue **Relations de clé étrangère** , cliquez sur **Ajouter**.  
  
     La relation s’affiche dans la liste **Relation sélectionnée** avec un nom fourni par le système au format FK_\<*nom_table*>_\<*nom_table*>, où *nom_table* est le nom de la table de clé étrangère.  
  
4.  Cliquez sur la relation dans la liste **Relation sélectionnée** .  
  
5.  Cliquez sur **Spécification de tables et colonnes** dans la grille affichée à droite et cliquez sur le bouton de sélection (**...**), à droite de la propriété.  
  
6.  Dans la liste déroulante **Clé primaire** de la boîte de dialogue **Tables et colonnes** , choisissez la table qui sera du côté clé primaire de la relation.  
  
7.  Dans la grille située au-dessous, choisissez les colonnes qui participent à la clé primaire de la table. Dans la cellule de la grille située à gauche de chaque colonne, choisissez la colonne clé étrangère correspondante dans la table de clé étrangère.  
  
     Le**Concepteur de tables** propose un nom pour la relation. Pour changer ce nom, modifiez le contenu de la zone de texte **Nom de la relation** .  
  
8.  Choisissez **OK** pour créer la relation.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-foreign-key-in-a-new-table"></a>Pour créer une clé étrangère dans une nouvelle table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple crée une table et définit une contrainte de clé étrangère sur la colonne `TempID` qui fait référence à la colonne `SalesReasonID` dans la table `Sales.SalesReason` . Les clauses ON DELETE CASCADE et ON UPDATE CASCADE sont utilisées pour garantir que les modifications apportées à la table `Sales.SalesReason` sont automatiquement propagées dans la table `Sales.TempSalesReason` .  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Sales.TempSalesReason (TempID int NOT NULL, Name nvarchar(50),   
    CONSTRAINT PK_TempSales PRIMARY KEY NONCLUSTERED (TempID),   
    CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    );GO  
  
    ```  
  
#### <a name="to-create-a-foreign-key-in-an-existing-table"></a>Pour créer une clé étrangère dans une table existante  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple crée une clé étrangère sur la colonne `TempID` et référence la colonne `SalesReasonID` dans la table `Sales.SalesReason`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Sales.TempSalesReason   
    ADD CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    ;  
    GO  
  
    ```  
  
     Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) et [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).  
  
  
