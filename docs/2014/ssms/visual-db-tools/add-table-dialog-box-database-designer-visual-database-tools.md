---
title: Ajouter une table, boîte de dialogue (Concepteur de bases de données) (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33802842eccbd6e9d50c98365cb2b9fe03391a8d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128632"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a>Boîte de dialogue Ajouter une table (Concepteur de bases de données)
  Vous permet d'ajouter des tables dans le Concepteur de bases de données.  
  
> [!NOTE]  
>  Si la table est publiée pour réplication, vous devez apporter vos modifications au schéma à l’aide de l’instruction Transact-SQL [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) ou de SMO (SQL Server Management Objects). Lorsque les modifications sont apportées au schéma à l'aide du Concepteur de tables ou du Concepteur de schémas de base de données, celui-ci tente d'abandonner la table et de la recréer. Toutefois, il est impossible d'abandonner les objets publiés, par conséquent les modifications du schéma échoueront.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Actualiser**  
 Actualise la liste des tables afin de refléter l'état actuel de la base de données.  
  
 **Ajouter**  
 Ajoute la ou les tables sélectionnées.  
  
> [!NOTE]  
>  Si vous souhaitez ajouter plusieurs tables au schéma, vous pouvez toutes les sélectionner avant de cliquer sur **Ajouter**. Vous pouvez aussi double-cliquer sur chaque table à ajouter, puis cliquer sur **Fermer** quand vous avez terminé.  
  
 **Fermer**  
 Ferme la boîte de dialogue sans ajouter de tables supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des tables à des schémas &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
