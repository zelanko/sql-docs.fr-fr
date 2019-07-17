---
title: Modifier des contraintes uniques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying constraints
- UNIQUE constraints [SQL Server], modifying
- constraints [SQL Server], modifying
- constraints [SQL Server], unique
ms.assetid: fddbdc9e-958b-4614-8e88-6ca205d64a4e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 311862d3612760da88d62f3ab51a5ca16d554b0b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68196775"
---
# <a name="modify-unique-constraints"></a>Modifier des contraintes uniques
  Vous pouvez modifier une contrainte unique dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour modifier une contrainte unique à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-a-unique-constraint"></a>Pour modifier une contrainte unique  
  
1.  Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur la table contenant la contrainte unique, puis sélectionnez **Conception**.  
  
2.  Dans le menu **Concepteur de tables**, cliquez sur **Index/Clés...** .  
  
3.  Dans la boîte de dialogue **Index/Clés** , sous **Index ou clé unique/primaire sélectionné(e)** , sélectionnez la contrainte que vous souhaitez modifier.  
  
4.  Effectuez l'une des actions décrites dans le tableau suivant :  
  
    |Pour|Procédez comme suit|  
    |--------|------------------------|  
    |Changer les colonnes auxquelles la contrainte est associée|1) Dans la grille en dessous de **(Général)** , cliquez sur **Colonnes**, puis sur le bouton de sélection **(...)** , à droite de la propriété.<br /><br /> 2) Dans la boîte de dialogue **Colonnes d’index** , spécifiez la nouvelle colonne, l’ordre de tri, ou les deux, pour l’index.|  
    |Renommer la contrainte|Dans la grille sous **Identité**, tapez un nouveau nom dans la zone **Nom** . Assurez-vous que le nouveau nom n’existe pas déjà dans la liste **Index ou clé unique/primaire sélectionné(e)** .|  
    |Définir l'option clustered|Dans la grille sous **Concepteur de tables**, sélectionnez **Créer sous forme de cluster** et sélectionnez Oui dans la liste déroulante pour créer un index cluster et Non pour créer un index non-cluster. Il ne peut exister qu'un seul index cluster par table. Si un index cluster existe dans la table, vous devez effacer ce paramètre sur l'index d'origine.|  
    |Définir un taux de remplissage|Dans la grille sous **Concepteur de tables**, développez la catégorie **Spécification du remplissage** et tapez un entier compris entre 0 et 100 dans la zone **Facteur de remplissage** .|  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer**_nom_table_.  
  
##  <a name="TsqlProcedure"></a> **Pour modifier une contrainte unique**  
  
 Pour modifier une contrainte UNIQUE à l'aide deTransact-SQL , vous devez d'abord supprimer la contrainte UNIQUE existante, puis la recréer avec sa nouvelle définition. Pour plus d'informations, consultez [Delete Unique Constraints](delete-unique-constraints.md) et [Create Unique Constraints](create-unique-constraints.md).  
  
###  <a name="TsqlExample"></a>  
