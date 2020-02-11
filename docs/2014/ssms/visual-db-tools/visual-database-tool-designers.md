---
title: Concepteurs Visual Database Tools | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- data sources [SQL Server]
- View Designer
- Visual Database Tools [SQL Server]
- Database Diagram Designer
- Query Designer [SQL Server]
- design tools [Visual Database Tools]
- Table Designer
- Visual Database Tools [SQL Server], designers
- Properties window [Visual Database Tools]
ms.assetid: bd0ca68e-6f69-42dd-bcb5-ce511673769c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 773ceb4aedddd6a39df6487bd36b47b83f7fa9a9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63227043"
---
# <a name="visual-database-tool-designers"></a>Concepteurs Visual Database Tools
  Visual Database Tools est une combinaison d'outils de conception que vous pouvez utiliser pour traiter une source de données. Vous pouvez les utiliser pour créer des requêtes, concevoir ou modifier une structure de base de données ou mettre à jour des données. Les outils disponibles sont le Concepteur de diagrammes de base de données, le Concepteur de tables et le Concepteur de requêtes et de vues.  
  
## <a name="properties-window"></a>Fenêtre Propriétés  
 La fenêtre de propriétés n'est pas spécifique à Visual Database Tools, mais vous pouvez apporter de nombreuses modifications à cet endroit. Elle affiche les propriétés de l'élément actuellement sélectionné (sous la forme d'une table) et vous permet de modifier ces propriétés (du nom des propriétés au classement d'une colonne). Certaines propriétés peuvent être affichées dans la fenêtre de propriétés, mais doivent être modifiées dans un autre outil.  
  
## <a name="database-diagram-designer"></a>Concepteur de diagrammes de base de données  
 Le Concepteur de diagrammes de base de données fournit une fenêtre dans laquelle vous pouvez créer, modifier et afficher visuellement les tables et les relations contenues dans une base de données.  
  
 Pour afficher le Concepteur de diagrammes de base de données, ouvrez un diagramme existant ou cliquez avec le bouton droit sur le nœud Base de données dans l’Explorateur d’objets et choisissez **Nouveau diagramme de base de données** dans le menu déroulant.  
  
 Une fois le concepteur ouvert, le menu **Diagramme de base de données** apparaît dans le menu principal. Ce menu est le point d'accès aux fonctionnalités spéciales du concepteur.  
  
> [!NOTE]  
>  Ce concepteur fonctionne avec les bases de données Microsoft SQL Server.  
>   
>  Cette version de Visual Database Tools ne prend pas en charge Microsoft SQL Server versions 7 et antérieures.  
  
## <a name="table-designer"></a>Concepteur de tables  
 L'outil visuel Concepteur de tables permet de concevoir et de visualiser une table unique dans une base de données Microsoft SQL Server à laquelle vous êtes connecté.  
  
 Le Concepteur de tables se compose de deux volets. La partie supérieure affiche une grille dont chaque ligne décrit une colonne de la base de données. La grille affiche les attributs fondamentaux de chacune des colonnes de la base de données : son nom, le type de ses données et le paramétrage de sa propriété « Null autorisé ».  
  
 La partie inférieure du Concepteur de tables (onglet Propriétés des colonnes) affiche d'autres attributs relatifs à la colonne mise en surbrillance dans la partie supérieure.  
  
 Dans le Concepteur de tables, vous pouvez également cliquer avec le bouton droit dans la partie de la grille pour accéder à des pages de propriétés permettant de créer et de modifier des relations, des contraintes, des index et des clés de la table.  
  
 Pour afficher le Concepteur de tables, ouvrez une table existante ou cliquez avec le bouton droit sur le nœud **Tables** dans l’Explorateur d’objets et choisissez **Ajouter une nouvelle table** dans le menu déroulant.  
  
 Une fois le concepteur ouvert, le menu Concepteur de tables apparaît dans le menu principal. Ce menu est le point d'accès aux fonctionnalités spéciales du concepteur.  
  
> [!NOTE]  
>  Ce concepteur fonctionne avec les bases de données Microsoft SQL Server.  
>   
>  Cette version de Visual Database Tools ne prend pas en charge Microsoft SQL Server versions 7 et antérieures.  
  
## <a name="query-and-view-designer"></a>Concepteur de requêtes et de vues  
 Le Concepteur de requêtes et de vues est en réalité composé de deux outils qui fonctionnent de manière très similaire. Les principales différences sont les suivantes :  
  
-   Les vues sont enregistrées avec la base de données alors que les requêtes sont enregistrées avec un projet de base de données Visual Studio.  
  
-   Le Concepteur de requêtes fonctionne avec presque toutes les sources de données, alors que le Concepteur de vues ne fonctionne qu'avec SQL Server.  
  
-   Le Concepteur de requêtes vous permet de concevoir des instructions DML SELECT, INSERT, UPDATE et DELETE, alors que les vues ne peuvent contenir que des instructions SELECT.  
  
### <a name="view-designer"></a>Concepteur de vue  
 Le Concepteur de vues vous permet de concevoir et d'afficher une vue existante ou d'en créer une nouvelle dans une base de données Microsoft SQL Server à laquelle vous êtes connecté.  
  
 Le Concepteur de vues comprend quatre volets : le volet Schéma, le volet Critères, le volet SQL et le volet Résultats. Pour plus d’informations sur chacun de ces volets, consultez [Outils du concepteur de requêtes et de vues &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Pour afficher le Concepteur de vues, ouvrez une vue existante ou cliquez avec le bouton droit sur le nœud **Vue** dans l’Explorateur d’objets et choisissez **Ajouter une nouvelle vue** dans le menu déroulant.  
  
 Une fois le concepteur ouvert, le menu **Concepteur de requêtes** apparaît dans le menu principal. Ce menu est le point d'accès aux fonctionnalités spéciales du concepteur.  
  
> [!NOTE]  
>  Ce concepteur fonctionne avec les bases de données Microsoft SQL Server.  
>   
>  Cette version de Visual Database Tools ne prend pas en charge Microsoft SQL Server versions 7 et antérieures.  
  
## <a name="see-also"></a>Voir aussi  
 [Concevoir des schémas de base de données &#40;Visual Database Tools&#41;](design-database-diagrams-visual-database-tools.md)   
 [Concevoir des tables &#40;Visual Database Tools&#41;](design-tables-visual-database-tools.md)   
 [Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
