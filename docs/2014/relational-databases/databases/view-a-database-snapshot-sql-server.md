---
title: Afficher un instantané de base de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: df4ba0cc720cd7dd98addff076c1400747da3551
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188626"
---
# <a name="view-a-database-snapshot-sql-server"></a>Afficher un instantané de base de données (SQL Server)
  Cette rubrique explique comment afficher un instantané de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!NOTE]  
>  Pour créer, restaurer ou supprimer un instantané de base de données, vous devez impérativement utiliser [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Pour afficher un instantané de base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour afficher un instantané de base de données**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et développez-la.  
  
2.  Développez **Bases de données**.  
  
3.  Développez **Instantanés de base de données**et sélectionnez l’instantané que vous voulez afficher.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher un instantané de base de données**  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Pour répertorier les instantanés de base de données de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], interrogez la colonne **source_database_id** de l’affichage catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) pour les valeurs non-NULL.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Créer un instantané de base de données &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md)  
  
-   [Rétablir une base de données dans l’état d’un instantané de base de données](revert-a-database-to-a-database-snapshot.md)  
  
-   [Supprimer un instantané de base de données &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Instantanés de base de données &#40;SQL Server&#41;](database-snapshots-sql-server.md)  
  
  
