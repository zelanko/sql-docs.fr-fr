---
title: Dessiner des relations réflexives
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- drawing reflexive relationships
- reflexive relationships
- database diagrams [SQL Server], relationships
ms.assetid: e218363f-faec-46d5-9904-a537fbcc994d
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 02790c49db32ca45aebdc2e57e242a6dad31e597
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75247238"
---
# <a name="draw-reflexive-relationships-visual-database-tools"></a>Établir des relations réflexives (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Vous pouvez créer une relation réflexive pour relier une ou plusieurs colonnes d'une table à une ou plusieurs autres colonnes de la même table. Par exemple, supposons que la table `employee` possède une colonne `emp_id` et une colonne `mgr_id` . Dans la mesure où chaque directeur est également un employé, vous mettrez ces deux colonnes en relation en dessinant une ligne de relation de la table vers elle-même. Cette relation garantira que chaque ID de directeur ajouté à la table correspond à un ID d'employé existant.  
  
Avant de créer une relation, vous devez définir une clé primaire ou une contrainte unique pour votre table. Vous mettez ensuite la colonne de clé primaire en relation avec une colonne correspondante. À la création de la relation, la colonne correspondante devient une clé étrangère de la table.  
  
### <a name="to-draw-a-reflexive-relationship"></a>Pour dessiner une relation réflexive  
  
1.  Dans votre diagramme de base de données, cliquez sur le sélecteur de ligne correspondant à la colonne que vous voulez mettre en relation avec une autre colonne et faites glisser le pointeur à l’extérieur de la table jusqu’à ce qu’une ligne apparaisse.  
  
2.  Refaites glisser la ligne vers la table sélectionnée.  
  
3.  Relâchez le bouton de la souris. La boîte de dialogue **Tables et colonnes** s’affiche.  
  
4.  Sélectionnez la colonne de clé étrangère et la table et colonne de clé primaire avec lesquelles vous souhaitez créer une relation.  
  
5.  Cliquez deux fois sur **OK** pour créer la relation.  
  
Lorsque vous exécutez des requêtes sur une table, vous pouvez utiliser une relation réflexive pour créer une jointure réflexive. Pour plus d’informations sur l’interrogation de tables avec des jointures, consultez [Interroger avec des jointures &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
[Interroger avec des jointures &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
