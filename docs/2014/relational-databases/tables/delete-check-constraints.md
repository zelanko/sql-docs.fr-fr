---
title: Supprimer des contraintes de validation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- removing constraints
- CHECK constraints, deleting
- constraints [SQL Server], deleting
- constraints [SQL Server], check
- deleting constraints
ms.assetid: 5f86c1a6-f5fa-4e77-a892-f6ae96fc0ab3
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 70c87ea84fbf7bb506e404931450c52161628a41
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052801"
---
# <a name="delete-check-constraints"></a>Supprimer des contraintes de validation
  Vous pouvez supprimer une contrainte de validation dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. En supprimant des contraintes de validation, vous supprimez les restrictions sur les valeurs de données acceptées dans la ou les colonnes incluses dans l'expression de contrainte.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une contrainte de validation à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-check-constraint"></a>Pour supprimer une contrainte de validation  
  
1.  Dans l' **Explorateur d'objets**, développez la table avec la contrainte de validation.  
  
2.  Développez  **Contraintes**.  
  
3.  Cliquez sur la contrainte avec le bouton droit, puis sélectionnez **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer l'objet** , cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-check-constraint"></a>Pour supprimer une contrainte de validation  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT CHK_ColumnD_DocExc;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
  
