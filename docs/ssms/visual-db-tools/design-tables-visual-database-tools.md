---
description: Créer et mettre à jour les tables de base de données
title: Créer et mettre à jour des tables
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Visual Database Tools [SQL Server], Table Designer
- Table Designer, designing tables
- opening tables
- opening Table Designer
- tables [SQL Server], opening
- Table Designer, opening
ms.assetid: c49e0155-5dcb-481f-9538-e1bde77105e2
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/25/2017
ms.openlocfilehash: 5a0bbc50ddef7baa1cd2f21211f692703f41b251
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491700"
---
# <a name="create-and-update-database-tables"></a>Créer et mettre à jour les tables de base de données

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Le Concepteur de tables est un outil visuel qui vous permet de concevoir et de visualiser des [tables de base de données](../../relational-databases/tables/tables.md). Utilisez le Concepteur de tables SQL Server Management Studio (SSMS) pour créer, modifier ou supprimer des tables, des colonnes, des clés, des index, des relations et des contraintes.  

## <a name="create-a-table"></a>Créer une table

1. Cliquez avec le bouton droit sur le nœud **Tables** de votre base de données et sélectionnez **Nouvelle** > **Table** :

    ![Nouvelle table](../media/design-tables/new-table.png)

2. Ajoutez des [colonnes](column-properties-visual-database-tools.md) à votre table :

    ![créer une table](../media/design-tables/new-table2.png)

3. Fermez le concepteur et enregistrez vos modifications.

## <a name="update-a-table"></a>Mettre à jour une table

1. Cliquez avec le bouton droit sur la table sous le nœud **Tables** de votre base de données et sélectionnez **Conception** :

    ![Mettre à jour une table](../media/design-tables/update-table.png)

2. Mettez à jour les paramètres de la table que vous souhaitez :

    ![Créer une table](../media/design-tables/update-table2.png)

3. Fermez le concepteur et enregistrez vos modifications.

## <a name="see-also"></a>Voir aussi

- [Tables](../../relational-databases/tables/tables.md)
- [Propriétés de la table &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/table-properties-visual-database-tools.md)
- [Propriétés de colonne](column-properties-visual-database-tools.md)
- [Ajouter des colonnes à une table](../../relational-databases/tables/add-columns-to-a-table-database-engine.md)
- [Clés primaires et étrangères](../../relational-databases/tables/primary-and-foreign-key-constraints.md)
- [Index](../../relational-databases/indexes/indexes.md)
- [Types de données (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
- [Télécharger SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md)
- [Créer une base de données et ajouter des tables dans Visual Studio](/visualstudio/data-tools/create-a-sql-database-by-using-a-designer)
