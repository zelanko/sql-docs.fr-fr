---
title: Base de données Ajouter une table (Concepteur de base de données)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 9c005a61a742a0c589cf5ccc26f818b8479b6a14
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000763"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a>Boîte de dialogue Ajouter une table (Concepteur de bases de données)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Vous permet d'ajouter des tables dans le Concepteur de bases de données.  
  
> [!NOTE]  
> Si la table est publiée pour réplication, vous devez apporter vos modifications au schéma à l’aide de l’instruction Transact-SQL [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) ou de SMO (SQL Server Management Objects). Lorsque les modifications sont apportées au diagramme à l’aide du Concepteur de tables ou du Concepteur de diagrammes de base de données, celui-ci tente d’abandonner la table et de la recréer. Toutefois, il est impossible d'abandonner les objets publiés, par conséquent les modifications du schéma échoueront.  
  
## <a name="ui-element-list"></a>Liste d’éléments d’interface utilisateur  
**Actualiser**  
Actualise la liste des tables afin de refléter l'état actuel de la base de données.  
  
**Ajouter**  
Ajoute la ou les tables sélectionnées.  
  
> [!NOTE]  
> Si vous souhaitez ajouter plusieurs tables au schéma, vous pouvez toutes les sélectionner avant de cliquer sur **Ajouter**. Vous pouvez aussi double-cliquer sur chaque table à ajouter, puis cliquer sur **Fermer** quand vous avez terminé.  
  
**Close**  
Ferme la boîte de dialogue sans ajouter de tables supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
[Ajouter des tables à des schémas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
