---
title: Types de requêtes pris en charge
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Delete query
- queries [SQL Server], types
- Update query
- Query Designer [SQL Server], query types
- Criteria pane
- Insert Values query
- Select query
- Make Table query
- Insert Results query
- Diagram pane [Visual Database Tools]
- View Designer, query types
ms.assetid: 72b9116c-c128-4078-a78d-257a2955a3f6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 6fa2d2e5502bc47d0631263b0b42c254fead0bfc
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008130"
---
# <a name="supported-query-types-visual-database-tools"></a>Types de requêtes pris en charge (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Voici les types de requêtes pouvant être créés dans les volets Schéma et Critères (volets graphiques) du [Concepteur de requêtes et de vues](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md):  
  
-   **Requête Select** Extrait des données d’une ou de plusieurs tables ou vues. Ce type de requête crée une instruction SQL SELECT.  
  
-   **Insert Results** Créé des lignes d’une table dans une autre, ou dans la même table en tant que nouvelles lignes. Ce type de requête crée une instruction SQL INSERT INTO...SELECT.  
  
-   **Insert Values** Crée une ligne et insère des valeurs dans des colonnes spécifiées. Ce type de requête crée une instruction SQL INSERT INTO...VALUES.  
  
-   **Requête Update** Modifie les valeurs de colonnes individuelles dans une ou plusieurs lignes existant dans une table. Ce type de requête crée une instruction SQL UPDATE...SET.  
  
-   **Requête Delete** Supprime une ou plusieurs lignes d’une table. Ce type de requête crée une instruction SQL DELETE.  
  
    > [!NOTE]  
    > Une requête Delete supprime de la table des lignes entières. Pour supprimer des valeurs dans des colonnes de données individuelles, utilisez une requête Update.  
  
-   **Requête Make Table** Copie les résultats d’une requête dans une nouvelle table. Ce type de requête crée une instruction SQL DELETE...INTO.  
  
Pour créer des requêtes, vous pouvez utiliser les volets graphiques, mais aussi entrer n'importe quelle instruction SQL dans le volet SQL, par exemple pour créer une requête Union.  
  
Si les instructions SQL que vous utilisez pour créer la requête ne peuvent pas être représentées dans les volets graphiques, le Concepteur de requêtes et de vues estompe ces volets pour indiquer qu'ils ne reflètent pas la requête en cours de création. Cependant, les volets estompés restent actifs et, dans de nombreux cas, il est possible d'apporter des modifications à la requête dans ces volets. Si les modifications que vous apportez donnent lieu à une requête que les volets graphiques peuvent représenter, ces derniers ne sont plus estompés.  
  
## <a name="see-also"></a>Voir aussi  
[Rubriques de procédures relatives au Concepteur de vues et de requêtes](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Types de requêtes](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
  
