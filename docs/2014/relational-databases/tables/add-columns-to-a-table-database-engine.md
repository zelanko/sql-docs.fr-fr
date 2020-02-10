---
title: Ajouter des colonnes à une table (moteur de base de données)| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- adding columns
ms.assetid: abeb8d52-d562-4e29-9e1e-2923ae874859
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eed258c78e76c5ec3f6aeeeb6bdd647166592613
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62856134"
---
# <a name="add-columns-to-a-table-database-engine"></a>Ajouter des colonnes à une table (moteur de base de données)
  Cette rubrique explique comment ajouter des colonnes à une table dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour insérer des colonnes, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 L'instruction ALTER TABLE permettant d'ajouter des colonnes à une table, ajoute automatiquement ces colonnes à la fin de la table. Si vous souhaitez classer les colonnes dans la table dans un ordre spécifique, utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Cependant, notez que cette méthode n'est pas recommandée pour concevoir une base de données. La recommandation est de spécifier l'ordre dans lequel les colonnes sont renvoyées au niveau de l'application et de la requête. Vous ne pouvez pas compter sur l'utilisation de SELECT * pour retourner toutes les colonnes dans une commande prévue d'après l'ordre dans lequel elles sont définies dans la table. Spécifiez toujours le nom des colonnes dans vos requêtes et applications dans l'ordre dans lequel vous souhaitez qu'elles apparaissent.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-insert-columns-into-a-table-with-table-designer"></a>Pour insérer des colonnes dans une table à l'aide du Concepteur de tables  
  
1.  Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur la table dans laquelle vous souhaitez ajouter des colonnes et choisissez **Conception**.  
  
2.  Cliquez sur la première cellule vide dans la colonne **Nom de la colonne** .  
  
3.  Tapez le nom de la colonne dans la cellule. Le nom de la colonne est une valeur requise.  
  
4.  Appuyez sur la touche TAB pour passer à la cellule **Type de données** et sélectionnez le type de données dans la liste déroulante. Il s'agit également d'une valeur requise qui sera utilisée comme valeur par défaut si vous n'en choisissez pas.  
  
    > [!NOTE]  
    >  Vous pouvez modifier la valeur par défaut dans la boîte de dialogue **Options** située sous **Outils de base de données**.  
  
5.  Continuez à définir éventuellement d'autres propriétés des colonnes dans l'onglet **Propriétés des Colonnes** .  
  
    > [!NOTE]  
    >  Les valeurs par défaut des propriétés des colonnes sont ajoutées lorsque vous créez une nouvelle colonne, mais vous pouvez les modifier sous l’onglet **Propriétés de la colonne** .  
  
6.  Quand vous avez fini d’ajouter des colonnes, dans le menu **Fichier** , choisissez **Enregistrer**_nom de la table_.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-insert-columns-into-a-table"></a>Pour insérer des colonnes dans une table  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  L'exemple suivant ajoute deux colonnes à la table `dbo.doc_exa`. Copiez et collez l’exemple suivant dans la fenêtre de requête et cliquez sur **exécuter** .  
  
```  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL, column_c INT NULL ;  
```  
  
##  <a name="FollowUp"></a>Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
