---
title: Supprimer des tables (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table deletions [SQL Server]
- deleting tables
- removing tables
- dropping tables
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f040c9907574bba718827999bb9c0fbb432a0bd0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62761435"
---
# <a name="delete-tables-database-engine"></a>Supprimer des tables (moteur de base de données)
  Vous pouvez supprimer une table de votre base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!CAUTION]  
>  Ne supprimez une table qu'après mûre réflexion. En effet, s'il existe des requêtes, des vues, des fonctions définies par l'utilisateur, des procédures stockées ou des programmes qui font référence à cette table, la suppression rend tous ces objets non valides.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une table à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous ne pouvez pas supprimer une table qui est référencée par une contrainte FOREIGN KEY. Vous devez au préalable supprimer la contrainte FOREIGN KEY ou la table qui la référence. Si la table de référence et la table qui contient la clé primaire sont supprimées dans la même instruction DROP TABLE, la table de référence doit figurer en premier dans la liste.  
  
-   Lorsqu'une table est supprimée, les règles et les valeurs par défaut liées à celle-ci sont dissociées et toutes les contraintes et les déclencheurs qui lui sont associés sont automatiquement supprimés. Si vous recréez la table, vous devez réassocier les règles et valeurs par défaut appropriées, recréer les déclencheurs et ajouter les toutes les contraintes nécessaires.  
  
-   Si vous supprimez une table qui contient une colonne `varbinary (max)` avec l'attribut FILESTREAM, toutes les données stockées dans le système de fichiers ne seront pas supprimées.  
  
-   DROP TABLE et CREATE TABLE ne doivent pas être exécutés sur la même table dans le même lot. Sinon, une erreur inattendue risque de se produire.  
  
-   Toute vue ou procédure stockée faisant référence à la table supprimée doit être supprimée ou modifiée explicitement pour supprimer la référence à la table.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l’autorisation ALTER sur le schéma auquel appartient la table, l’autorisation CONTROL sur la table ou l’appartenance au rôle de base de données fixe **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-table-from-the-database"></a>Pour supprimer une table de la base de données  
  
1.  Dans l'Explorateur d'objets, sélectionnez la table à supprimer.  
  
2.  Cliquez avec le bouton droit sur la table puis, dans le menu contextuel, cliquez sur **Supprimer** .  
  
3.  Un message vous demande de confirmer la suppression. Cliquez sur **Oui**.  
  
    > [!NOTE]  
    >  La suppression d'une table entraîne automatiquement celle de toutes les relations qu'elle entretient.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-table-in-query-editor"></a>Pour supprimer une table dans l'éditeur de requête  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 Pour plus d’informations, consultez [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql).  
  
  
