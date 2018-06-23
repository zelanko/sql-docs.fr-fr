---
title: Boîte de dialogue de Table (concepteurs de requêtes et affichage) ajouter (Visual Database Tools) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8679c4a7210297b9bbf2c7245e7ce05a01d57a40
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143629"
---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a>Boîte de dialogue Ajouter une table (Concepteurs de requêtes et de vues)
  Cette boîte de dialogue permet d'ajouter à une requête ou à une vue, des tables, des vues, des fonctions définies par l'utilisateur ou des synonymes.  
  
> [!NOTE]  
>  Si la table est publiée pour réplication, vous devez apporter vos modifications au schéma à l’aide de l’instruction Transact-SQL [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) ou de SMO (SQL Server Management Objects). Lorsque les modifications sont apportées au schéma à l'aide du Concepteur de tables ou du Concepteur de schémas de base de données, celui-ci tente d'abandonner la table et de la recréer. Toutefois, il est impossible d'abandonner les objets publiés, par conséquent les modifications du schéma échoueront.  
  
## <a name="options"></a>Options  
 **Tables**  
 Énumère les tables que vous pouvez ajouter au volet **Schéma** . Pour ajouter une table, sélectionnez-la et cliquez sur **Ajouter**. Pour ajouter plusieurs tables à la fois, sélectionnez-les et cliquez sur **Ajouter**.  
  
 **Vues**  
 Énumère les vues que vous pouvez ajouter au volet **Schéma** . Pour ajouter une vue, sélectionnez-la et cliquez sur **Ajouter**. Pour ajouter plusieurs vues à la fois, sélectionnez-les et cliquez sur **Ajouter**.  
  
 **Fonctions**  
 Énumère les fonctions définies par l’utilisateur que vous pouvez ajouter au volet **Schéma** . Pour ajouter une fonction, sélectionnez-la et cliquez sur **Ajouter**. Pour ajouter plusieurs fonctions à la fois, sélectionnez-les et cliquez sur **Ajouter**.  
  
 **Synonymes**  
 Énumère les synonymes que vous pouvez ajouter au volet **Schéma** . Pour ajouter un synonyme, sélectionnez-le et cliquez sur **Ajouter**. Pour ajouter plusieurs synonymes à la fois, sélectionnez-les et cliquez sur **Ajouter**.  
  
 **Actualiser**  
 Met à jour la liste pour ajouter toutes les modifications apportées à la base de données depuis la dernière récupération de la liste.  
  
 **Ajouter**  
 Ajoute chaque élément sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
