---
title: Utiliser des tables dans les diagrammes de base de données
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], tables
- Table Designer, database diagrams
- tables [SQL Server], database diagrams
- database diagrams [SQL Server], Table Designer
ms.assetid: ee2c5d84-22bf-4597-ac70-a27ed8cc94f4
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 7072233d4a4d509fbb002e9951484f547396dad5
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86002561"
---
# <a name="work-with-tables-in-database-diagram-visual-database-tools"></a>Utiliser des tables dans les diagrammes de base de données (Visual Database Tools)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Vous pouvez modifier et créer des tables de base de données dans le Concepteur de tables ou dans le Concepteur de diagrammes de base de données.  
  
> [!NOTE]  
> Si la table est publiée pour réplication, vous devez apporter vos modifications au schéma à l’aide de l’instruction Transact-SQL [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) ou de SMO (SQL Server Management Objects). Lorsque les modifications sont apportées au diagramme à l’aide du Concepteur de tables ou du Concepteur de diagrammes de base de données, celui-ci tente d’abandonner la table et de la recréer. Toutefois, il est impossible d'abandonner les objets publiés, par conséquent les modifications du schéma échoueront.  
  
## <a name="in-this-section"></a>Dans cette section

[Ajouter des tables à des schémas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
[Ajouter des tables connexes à des schémas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-related-tables-to-diagrams-visual-database-tools.md)  
  
[Enregistrer des tables sélectionnées dans un schéma &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/save-selected-tables-on-a-diagram-visual-database-tools.md)  
  
[Copier des tables d’un diagramme de base de données vers un autre &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/copy-tables-from-one-database-diagrams-to-another-visual-database-tools.md)  
  
[Supprimer des tables de diagrammes de base de données &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/remove-tables-from-database-diagrams-visual-database-tools.md)  
  
[Mapper des relations plusieurs-à-plusieurs &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/map-many-to-many-relationships-visual-database-tools.md)  
  
[Établir des relations réflexives &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/draw-reflexive-relationships-visual-database-tools.md)  
  
## <a name="reference"></a>Informations de référence

[Boîte de dialogue Ajouter une table &#40;Concepteur de bases de données&#41; &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-table-dialog-box-database-designer-visual-database-tools.md)

## <a name="related-sections"></a>Sections connexes
