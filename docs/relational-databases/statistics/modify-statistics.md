---
title: Modifier des statistiques | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-statistics
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statistics [SQL Server], modifying
- modifying statistics
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dc2ee0a2699bb9f1d2aad02e5777a208e842bef8
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="modify-statistics"></a>Modifier des statistiques
  Vous pouvez modifier des statistiques existantes dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour modifier des statistiques, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Exigences :  
  
-   L'utilisateur doit disposer de l'autorisation ALTER sur la table ou la vue.  
  
-   L’utilisateur doit être le propriétaire de la table ou de la vue indexée ou être membre d’un des rôles suivants : rôle serveur fixe **sysadmin** , rôle de base de données fixe **db_owner** ou rôle de base de données fixe **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-statistics"></a>Pour modifier des statistiques  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer la base de données dans laquelle vous souhaitez modifier une statistique.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Tables** .  
  
3.  Cliquez sur le signe plus (+) pour développer la table dans laquelle vous souhaitez modifier une statistique.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Statistiques** .  
  
5.  Cliquez avec le bouton droit sur l’objet de statistiques à modifier et sélectionnez **Propriétés**.  
  
6.  Dans la boîte de dialogue **Propriétés des statistiques** *statistics_name* dialog box, on the **General** page, click **Add**, **Remove**, **Move Up**, or **Move Down**, or any combination, to alter the properties of the statistics. Gardez à l'esprit que l'emplacement d'une colonne dans la grille **Colonnes de statistiques** peut avoir une incidence notable sur l'utilité des statistiques.  
  
7.  Cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour modifier des statistiques**  
  
 Cette tâche ne peut pas être effectuée à l'aide d'instructions Transact-SQL. Pour modifier des statistiques à l'aide de Transact-SQL, vous devez d'abord supprimer les statistiques existantes, puis les recréer avec les nouveaux attributs.  
  
 Pour plus d’informations, consultez [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md) et [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md).  
  
  

