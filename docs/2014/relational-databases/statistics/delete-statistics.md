---
title: Supprimer des statistiques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], deleting
- deleting statistics
ms.assetid: eccce0aa-591e-4a1d-bd10-373b022f8749
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0a72a030e504fca472596fd8e98faec0b98e5803
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211875"
---
# <a name="delete-statistics"></a>Supprimer des statistiques
  Vous pouvez supprimer des statistiques des tables et des vues dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer des statistiques d'une table ou d'une vue, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Soyez prudent lorsque vous supprimez des statistiques. En effet, vous risquez d'affecter le plan d'exécution choisi par l'optimiseur de requête.  
  
-   Les statistiques sur les index ne peuvent pas être supprimées à l'aide de DROP STATISTICS. Les statistiques sont conservées aussi longtemps que l'index existe.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite une autorisation ALTER sur la table ou la vue.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a>Pour supprimer des statistiques d'une table ou d'une vue  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer la base de données dans laquelle vous souhaitez supprimer une statistique.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Tables** .  
  
3.  Cliquez sur le signe plus (+) pour développer la table dans laquelle vous souhaitez supprimer une statistique.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Statistiques** .  
  
5.  Cliquez avec le bouton droit sur l’objet de statistiques à supprimer et sélectionnez **Supprimer**.  
  
6.  Dans la boîte de dialogue **Supprimer un objet** , assurez-vous d'avoir sélectionné la statistique correcte, puis cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a>Pour supprimer des statistiques d'une table ou d'une vue  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- First, create two statistics named VendorCredit and CustomerTotal  
    -- The first statistic uses a random 50% sample of information provided from the Name and CreditRating columns in the Purchasing.Vendor table.  
    CREATE STATISTICS VendorCredit  
        ON Purchasing.Vendor (Name, CreditRating)  
        WITH SAMPLE 50 PERCENT  
    -- The second statistic uses all of the information from the CustomerID and TotalDue columns in the Sales.SalesOrderHeader table  
    CREATE STATISTICS CustomerTotal  
        ON Sales.SalesOrderHeader (CustomerID, TotalDue)  
        WITH FULLSCAN;  
    GO  
    -- This next statement drops both of the statistics created above. Note that the naming convention is [table_name].[statistics_name].  
    DROP STATISTICS Purchasing.Vendor.VendorCredit, Sales.SalesOrderHeader.CustomerTotal;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql).  
  
  
