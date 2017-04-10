---
title: "Modifier l&#39;ordre des colonnes dans une table | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "colonnes [SQL Server], modification de l’ordre d’une table"
  - "ordre des colonnes, modification"
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Modifier l&#39;ordre des colonnes dans une table
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Vous pouvez changer l'ordre des colonnes dans le Concepteur de tables dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!CAUTION]  
>  Changer l'ordre des colonnes d'une table peut avoir une incidence sur le code et les applications qui dépendent de l'ordre spécifique des colonnes. Il peut s'agir de requêtes, de vues, de procédures stockées, de fonctions définies par l'utilisateur et d'applications clientes. Prenez toutes les précautions nécessaires avant de changer l'ordre des colonnes. La recommandation est de spécifier l'ordre dans lequel les colonnes sont renvoyées au niveau de l'application et de la requête. Vous ne pouvez pas compter sur l'utilisation de SELECT * pour retourner toutes les colonnes dans une commande prévue d'après l'ordre dans lequel elles sont définies dans la table. Spécifiez toujours le nom des colonnes dans vos requêtes et applications dans l'ordre dans lequel vous souhaitez qu'elles apparaissent.  
  
 **Dans cette rubrique**  
  
-   **Pour changer l'ordre des colonnes à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour changer l'ordre des colonnes  
  
1.  Dans l’**Explorateur d’objets**, cliquez avec le bouton droit sur la table dont vous souhaitez réorganiser les colonnes et cliquez sur **Conception**.  
  
2.  Sélectionnez la case à gauche du nom de la colonne à réordonner.  
  
3.  Faites glisser la colonne vers un autre emplacement dans la table.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour changer l'ordre des colonnes**  
  
 Cette tâche ne peut pas être effectuée à l'aide d'instructions Transact-SQL.  
  
###  <a name="TsqlExample"></a>  