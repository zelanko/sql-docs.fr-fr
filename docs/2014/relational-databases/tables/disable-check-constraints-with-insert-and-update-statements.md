---
title: Désactiver des contraintes de validation avec des instructions INSERT et UPDATE | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, disabling
- constraints [SQL Server], disabling
- disabling constraints
- constraints [SQL Server], check
ms.assetid: c7287ad1-50d2-4e80-bc0c-b5570f7e5f69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2227bebe953ac9a95a643c05e9879a2b812f0376
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124169"
---
# <a name="disable-check-constraints-with-insert-and-update-statements"></a>Désactiver des contraintes de validation avec des instructions INSERT et UPDATE
  Vous pouvez désactiver une contrainte de validation pour des transactions INSERT et UPDATE dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Une fois les contraintes de validation désactivées, les insertions ou les mises à jour ultérieures sur la colonne ne sont pas validées par rapport aux conditions de la contrainte. Utilisez cette option si vous savez que de nouvelles données violeront la contrainte existante ou si la contrainte s'applique uniquement aux données déjà dans la base de données.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour désactiver une contrainte de validation pour les instructions INSERT et UPDATE à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a>Pour désactiver une contrainte de validation pour les instructions INSERT et UPDATE  
  
1.  Dans l' **Explorateur d'objets**, développez la table avec la contrainte, puis développez le dossier **Contraintes** .  
  
2.  Cliquez avec le bouton droit sur la contrainte et sélectionnez **Modifier**.  
  
3.  Dans la grille sous **Concepteur de tables**, cliquez sur **Appliquer INSERTs et UPDATEs** et sélectionnez **Non** dans le menu déroulant.  
  
4.  Cliquez sur **Fermer**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a>Pour désactiver une contrainte de validation pour les instructions INSERT et UPDATE  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez les exemples suivants dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT CK_PurchaseOrderHeader_Freight;   
    GO  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
###  <a name="TsqlExample"></a>  
