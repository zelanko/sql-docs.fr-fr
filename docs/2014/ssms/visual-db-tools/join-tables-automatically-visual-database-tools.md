---
title: Joindre automatiquement des tables (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- joins [SQL Server], creating
- joins [SQL Server], automatic
ms.assetid: f152af82-bcb6-49ca-af19-48cdb7fc9ac6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bab311878966087ef9b6c3f05bb3023d02fdeb20
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62711066"
---
# <a name="join-tables-automatically-visual-database-tools"></a>Joindre automatiquement des tables (Visual Database Tools)
  Quand vous ajoutez plusieurs tables à une requête, le [Concepteur de requêtes et de vues](visual-database-tools.md) tente de déterminer si elles sont liées. Si c'est le cas, le Concepteur de requêtes et de vues place automatiquement des lignes de jointure entre les rectangles représentant des tables ou des objets de type table.  
  
 Le Concepteur de requêtes et de vues identifie des tables comme étant jointes dans les cas suivants :  
  
-   La base de données contient des informations qui spécifient que les tables sont liées.  
  
-   Deux colonnes, une dans chaque table, ont les mêmes nom et type de données. La colonne doit constituer la clé primaire d'au moins une des tables. Par exemple, si vous ajoutez les tables `employee` et `jobs` , si la colonne `job_id` est la clé primaire de la table `jobs` et enfin si chaque table possède une colonne appelée `job_id` comportant le même type de données, le Concepteur de requêtes et de vues joint automatiquement les tables.  
  
    > [!NOTE]  
    >  Le Concepteur de requêtes et de vues ne crée qu'une seule jointure basée sur les colonnes présentant un nom et un type de données identiques. S'il existe plusieurs possibilités de jointure, le Concepteur de requêtes et de vues s'arrête après avoir créé une jointure fondée sur le premier jeu de colonnes correspondantes qu'il trouve.  
  
-   Le Concepteur de requêtes et de vues détecte qu'une condition de recherche (une clause WHERE) constitue en fait une condition de jointure. Par exemple, vous pouvez ajouter les tables `employee` et `jobs`, puis créer une condition de recherche qui cherche la même valeur dans la colonne `job_id` des deux tables. Dans ce cas, le Concepteur de requêtes et de vues détermine que la condition de recherche donne lieu à une jointure et crée ensuite une condition de jointure basée sur la condition de recherche.  
  
 Si le Concepteur de requêtes et de vues a créé une jointure qui n'est pas adaptée à votre requête, vous pouvez modifier cette jointure ou la supprimer. Pour plus d’informations, consultez [Modifier des opérateurs de jointure &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md) et [Supprimer des jointures &#40;Visual Database Tools&#41;](remove-joins-visual-database-tools.md).  
  
 Si le Concepteur de requêtes et de vues ne joint pas automatiquement les tables dans votre requête, vous pouvez créer vous-même une jointure. Pour plus d’informations, consultez [Joindre manuellement des tables &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment le concepteur de requêtes et de vues représente des jointures &#40;Visual Database Tools&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md)   
 [Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Interroger avec des jointures &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)  
  
  
