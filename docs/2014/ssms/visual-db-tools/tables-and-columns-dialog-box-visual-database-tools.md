---
title: Boîte de dialogue Tables et colonnes (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 056c200ec6b73cb7cf11ee4b3acf35bc331110b3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821993"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a>Boîte de dialogue Tables et colonnes (Visual Database Tools)
  Utilisez cette boîte de dialogue pour mapper une clé primaire dans une table à une clé étrangère dans une autre. Pour accéder à cette boîte de dialogue, dans le menu **Concepteur de tables** , cliquez sur **Relations**. Dans la boîte de dialogue **Relations de clé étrangère**, cliquez sur le champ **Spécification de tables et colonnes**, puis cliquez sur le bouton de sélection **(…)** situé à droite de la propriété.  
  
> [!NOTE]  
>  Si la table est publiée pour réplication, vous devez apporter vos modifications au schéma à l’aide de l’instruction Transact-SQL [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) ou de SMO (SQL Server Management Objects). Lorsque les modifications sont apportées au diagramme à l’aide du Concepteur de tables ou du Concepteur de diagrammes de base de données, celui-ci tente d’abandonner la table et de la recréer. Toutefois, il est impossible d'abandonner les objets publiés, par conséquent les modifications du schéma échoueront.  
  
## <a name="options"></a>Options  
 **Nom de la relation**  
 Indique le nom de la relation.  
  
 **Table de clé primaire**  
 Répertorie les tables contenues dans la base de données. Choisissez la table qui se trouvera du côté clé primaire de la relation.  
  
 **Table de clé étrangère**  
 Affiche la table située du côté clé étrangère de la relation. Il s'agit de la table actuellement sélectionnée dans le Concepteur de tables.  
  
 **Grille sous la table de clé primaire**  
 Répertorie les colonnes de la table sélectionnées dans la liste **Table de clé primaire** . Entrez les colonnes qui contribuent à la clé primaire de cette table.  
  
 **Grille sous la table de clé étrangère**  
 Répertorie les colonnes de la table sélectionnées dans la liste **Table de clé étrangère** . Entrez la colonne clé étrangère de la table de clé étrangère qui correspond à la colonne clé primaire.  
  
> [!NOTE]  
>  Les colonnes que vous choisissez pour la clé étrangère doivent posséder le même type de données que les colonnes primaires auxquelles elles correspondent. Il doit exister un nombre égal de colonnes dans chacune des clés. Par exemple, si la clé primaire de la table située du côté clé primaire de la relation est composée de deux colonnes, vous devez faire correspondre chacune de ces colonnes à une colonne de la table située du côté clé étrangère de la relation.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer les relations entre les clés étrangères](../../relational-databases/tables/create-foreign-key-relationships.md)  
  
  
