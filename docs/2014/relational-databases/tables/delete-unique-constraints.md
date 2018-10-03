---
title: Supprimer des contraintes uniques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- UNIQUE constraints [SQL Server], deleting
- constraints [SQL Server], deleting
- deleting constraints
- constraints [SQL Server], unique
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d115123389777f40276fcab0487538e4569f4b64
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48115729"
---
# <a name="delete-unique-constraints"></a>Supprimer des contraintes UNIQUE
  Vous pouvez supprimer une contrainte unique dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. En supprimant une contrainte unique, vous supprimez la condition d'unicité requise pour les valeurs entrées dans la colonne ou la combinaison de colonnes incluses à l'intérieur de l'expression de contrainte et vous supprimez l'index unique correspondant.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une contrainte unique à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-unique-constraint-using-object-explorer"></a>Pour supprimer une contrainte unique à l'aide de l'Explorateur d'objets  
  
1.  Dans l'Explorateur d'objets, développez la table qui contient la contrainte unique puis développez **Contraintes**.  
  
2.  Cliquez sur la clé avec le bouton droit, puis sélectionnez **Supprimer**.  
  
3.  Dans la boîte de dialogue **Supprimer un objet** , vérifiez que la clé correcte est spécifiée et cliquez sur **OK**.  
  
#### <a name="to-delete-a-unique-constraint-using-table-designer"></a>Pour supprimer une contrainte unique à l'aide du Concepteur de tables  
  
1.  Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur la table avec la contrainte unique, puis cliquez sur **Conception**.  
  
2.  Dans le menu **Concepteur de tables** , cliquez sur **Index/Clés**.  
  
3.  Dans la boîte de dialogue **Index/Clés** , sélectionnez la clé unique dans la liste **Index ou clé unique/primaire sélectionné(e)** .  
  
4.  Cliquez sur **Supprimer**.  
  
5.  Dans le menu **Fichier**, cliquez sur **Enregistrer** *nom de la table*.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-unique-constraint"></a>Pour supprimer une contrainte unique  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Return the name of unique constraint.  
    SELECT name  
    FROM sys.objects  
    WHERE type = 'UQ' AND OBJECT_NAME(parent_object_id) = N' DocExc';  
    GO  
    -- Delete the unique constraint.  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT UNQ_ColumnB_DocExc;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) et [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).  
  
###  <a name="TsqlExample"></a>  
