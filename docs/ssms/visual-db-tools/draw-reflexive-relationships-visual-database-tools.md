---
title: "Établir des relations réflexives (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing reflexive relationships
- reflexive relationships
- database diagrams [SQL Server], relationships
ms.assetid: e218363f-faec-46d5-9904-a537fbcc994d
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a69c7bc560b19d21e2b50bf8462e72c94e6c0531
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="draw-reflexive-relationships-visual-database-tools"></a>Établir des relations réflexives (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Vous pouvez créer une relation réflexive pour relier une ou plusieurs colonnes d’une table à une ou plusieurs autres colonnes de la même table. Par exemple, supposons que la table `employee` possède une colonne `emp_id` et une colonne `mgr_id` . Dans la mesure où chaque directeur est également un employé, vous mettrez ces deux colonnes en relation en dessinant une ligne de relation de la table vers elle-même. Cette relation garantira que chaque ID de directeur ajouté à la table correspond à un ID d'employé existant.  
  
Avant de créer une relation, vous devez définir une clé primaire ou une contrainte unique pour votre table. Vous mettez ensuite la colonne de clé primaire en relation avec une colonne correspondante. À la création de la relation, la colonne correspondante devient une clé étrangère de la table.  
  
### <a name="to-draw-a-reflexive-relationship"></a>Pour dessiner une relation réflexive  
  
1.  Dans votre schéma de base de données, cliquez sur le sélecteur de ligne correspondant à la colonne que vous voulez mettre en relation avec une autre colonne et faites glisser le pointeur à l'extérieur de la table jusqu'à ce qu'une ligne apparaisse.  
  
2.  Refaites glisser la ligne vers la table sélectionnée.  
  
3.  Relâchez le bouton de la souris. La boîte de dialogue **Tables et colonnes** s’affiche.  
  
4.  Sélectionnez la colonne de clé étrangère et la table et colonne de clé primaire avec lesquelles vous souhaitez créer une relation.  
  
5.  Cliquez deux fois sur **OK** pour créer la relation.  
  
Lorsque vous exécutez des requêtes sur une table, vous pouvez utiliser une relation réflexive pour créer une jointure réflexive. Pour plus d’informations sur l’interrogation de tables avec des jointures, consultez [Interroger avec des jointures &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md).  
  
## <a name="see-also"></a> Voir aussi  
[Interroger avec des jointures &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
