---
title: Spécifier des valeurs par défaut pour les colonnes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a02385a6cd12b85be1661c738488c000f810510
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68196722"
---
# <a name="specify-default-values-for-columns"></a>Spécifier des valeurs par défaut pour les colonnes
  Vous pouvez spécifier une valeur par défaut qui sera écrite dans la colonne dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)]. Si vous n'assignez aucune valeur par défaut et que l'utilisateur laisse la colonne vide, alors :  
  
-   Si vous choisissez Oui pour Nul autorisé, la valeur NULL sera insérée dans la colonne.  
  
-   Si vous n'avez pas choisi Oui pour Nul autorisé, la colonne restera vide, mais l'utilisateur ne pourra pas enregistrer la ligne avant d'avoir fourni une valeur pour la colonne.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour spécifier une valeur par défaut à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si votre entrée dans le champ **Valeur par défaut** remplace une valeur par défaut liée (qui est affichée sans parenthèses), vous êtes invité à annuler la liaison de la valeur par défaut et à la remplacer par la nouvelle valeur par défaut.  
  
-   Pour entrer une chaîne de texte, placez la valeur entre des guillemets simples (') ; n'utilisez pas de guillemets doubles ("), car ils sont réservés pour les identificateurs entre guillemets.  
  
-   Pour entrer une valeur numérique par défaut, entrez le nombre sans guillemets autour.  
  
-   Pour entrer un objet/une fonction, entrez le nom de l'objet/fonction sans guillemets autour.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>Pour spécifier une valeur par défaut pour une colonne  
  
1.  Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur la table contenant les colonnes dont vous souhaitez modifier l’échelle et cliquez sur **Conception**.  
  
2.  Sélectionnez la colonne pour laquelle vous souhaitez spécifier une valeur par défaut.  
  
3.  Sous l'onglet **Propriétés des colonnes** , entrez la nouvelle valeur par défaut dans la propriété **Valeur ou liaison par défaut** .  
  
    > [!NOTE]  
    >  Pour entrer une valeur par défaut numérique, entrez le nombre. Pour un objet ou une fonction, entrez son nom. Pour une valeur par défaut alphanumérique, entrez la valeur dans des guillemets simples.  
  
4.  Dans le menu **Fichier**, cliquez sur **Enregistrer**_nom de la table_.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>Pour spécifier une valeur par défaut pour une colonne  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
    GO  
    INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
    GO  
    ALTER TABLE dbo.doc_exz  
    ADD CONSTRAINT col_b_def  
    DEFAULT 50 FOR column_b ;  
    GO  
  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
###  <a name="TsqlExample"></a>  
