---
title: Supprimer des colonnes d’une table | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 718aeca12c90435b68fd6cedde150dfbdeb3c063
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62761652"
---
# <a name="delete-columns-from-a-table"></a>Supprimer des colonnes d'une table
  Cette rubrique explique comment supprimer des colonnes de table dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!CAUTION]  
>  Lorsque vous supprimez une colonne d'une table, toutes les données qu'elle contient sont supprimées de la base de données. Il est impossible d’annuler cette opération.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une colonne d'une table à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
 Vous ne pouvez pas supprimer une colonne qui a une contrainte CHECK. Vous devez d'abord supprimer la contrainte.  
  
 Vous ne pouvez pas supprimer une colonne qui a des contraintes PRIMARY KEY ou FOREIGN KEY ou d'autres dépendances, sauf en utilisant le Concepteur de tables. Si vous utilisez l'Explorateur d'objets ou [!INCLUDE[tsql](../../includes/tsql-md.md)], vous devez d'abord supprimer toutes les dépendances à la colonne.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-columns-by-using-object-explorer"></a>Pour supprimer des colonnes à l'aide de l'Explorateur d'objets  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur la table dans laquelle vous souhaitez supprimer des colonnes et choisissez **Supprimer**.  
  
3.  Dans la boîte de dialogue **Supprimer un objet** , cliquez sur **OK**.  
  
 Si la colonne contient des contraintes ou d'autres dépendances, un message d'erreur s'affichera dans la boîte de dialogue **Supprimer un objet** . Résolvez l'erreur en supprimant les contraintes référencées.  
  
#### <a name="to-delete-columns-by-using-table-designer"></a>Pour supprimer des colonnes à l'aide du Concepteur de tables  
  
1.  Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur la table dans laquelle vous souhaitez supprimer des colonnes et choisissez **Conception**.  
  
2.  Cliquez avec le bouton droit sur la colonne à supprimer et, dans le menu contextuel, cliquez sur **Supprimer une colonne** .  
  
3.  Si les colonnes à supprimer participent à une relation (FOREIGN KEY ou PRIMARY KEY), un message vous demande confirmation avant la suppression des colonnes sélectionnées et de leurs relations. Choisissez **Oui**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-columns"></a>Pour supprimer des colonnes  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
    ```  
  
 Si la colonne contient des contraintes ou d'autres dépendances, un message d'erreur est retourné. Résolvez l'erreur en supprimant les contraintes référencées.  
  
 Pour obtenir des exemples supplémentaires, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
##  <a name="FollowUp"></a>  
