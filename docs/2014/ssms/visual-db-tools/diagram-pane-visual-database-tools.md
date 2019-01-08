---
title: Volet Schéma (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], Diagram pane
- View Designer, Diagram pane
- joins [SQL Server], Query and View Designer
- Diagram pane [Visual Database Tools]
ms.assetid: 399dfc7b-e2e7-47d3-bd11-163cbe0ce13c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 79ddfb40d33c8585b94ccc9718100e771da5e92e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52819371"
---
# <a name="diagram-pane-visual-database-tools"></a>Volet Schéma (Visual Database Tools)
  Ce volet donne une représentation graphique des tables ou des objets tables que vous avez sélectionnés dans la connexion de données. Il montre également les jointures entre ces tables et/ou ces objets.  
  
 Dans le volet Schéma, vous pouvez :  
  
-   Ajouter ou supprimer des tables et des objets table et spécifier les colonnes de données à prendre en compte dans les résultats.  
  
-   Créer ou modifier des jointures entre les tables et les objets table.  
  
 Lorsque vous apportez une modification dans le volet Schéma, elle se reflète automatiquement dans les volets Critères et SQL. Par exemple, si, dans le volet Schéma, vous sélectionnez dans une table ou un objet table une colonne à prendre en compte dans les résultats, le Concepteur de requêtes et de vues l'ajoute au volet Critères et, dans le volet SQL, à l'instruction SQL.  
  
 Chaque table ou objet table apparaît dans le volet Schéma dans une fenêtre séparée. L'icône de la barre de titre de chaque rectangle indique le type d'objet représenté par le rectangle, comme l'illustre le tableau suivant.  
  
## <a name="options"></a>Options  
 **Tables**  
 Énumère les tables que vous pouvez ajouter au volet Schéma. Pour ajouter une table, sélectionnez-la et cliquez sur **Ajouter**. Pour ajouter plusieurs tables à la fois, sélectionnez-les et cliquez sur **Ajouter**.  
  
 **Vues**  
 Énumère les vues que vous pouvez ajouter au volet Schéma. Pour ajouter une vue, sélectionnez-la et cliquez sur **Ajouter**. Pour ajouter plusieurs vues à la fois, sélectionnez-les et cliquez sur **Ajouter**.  
  
 **Fonctions**  
 Énumère les fonctions définies par l'utilisateur que vous pouvez ajouter au volet Schéma. Pour ajouter une fonction, sélectionnez-la et cliquez sur **Ajouter**. Pour ajouter plusieurs fonctions à la fois, sélectionnez-les et cliquez sur **Ajouter**.  
  
 **Tables locales**  
 Répertorie les tables créées par les requêtes plutôt que celles qui appartiennent à la base de données.  
  
 **Synonymes**  
 Énumère les synonymes que vous pouvez ajouter au volet Schéma. Pour ajouter un synonyme, sélectionnez-le et cliquez sur **Ajouter**. Pour ajouter plusieurs synonymes à la fois, sélectionnez-les et cliquez sur **Ajouter**.  
  
|Icône|Type d'objet|  
|----------|-----------------|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbi1.gif "Icône Visual Database Tools")|Table de charge de travail|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbi2.gif "Icône Visual Database Tools")|Requête ou Vue|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbi3.gif "Icône Visual Database Tools")|Table liée|  
|![Icône Visual Database Tools](../../database-engine/media//dvudficon.gif "Icône Visual Database Tools")|Fonction définie par l'utilisateur|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbi5.gif "Icône Visual Database Tools")|Vue liée|  
  
 Chaque rectangle montre les colonnes de la table ou de l'objet table. Des cases à cocher et des symboles apparaissent à côté des noms des colonnes pour indiquer la façon dont les colonnes sont utilisées dans la requête. Des info-bulles affichent des informations telles que le type de données et la taille des colonnes.  
  
 Le tableau suivant dresse la liste des cases à cocher et des symboles utilisés dans le rectangle, selon la table ou l'objet table.  
  
|Case à cocher ou symbole|Description|  
|-------------------------|-----------------|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbi7.gif "Icône Visual Database Tools")<br /><br /> ![Icône Visual Database Tools](../../database-engine/media//dv3wbi8.gif "Icône Visual Database Tools")<br /><br /> ![Icône Visual Database Tools](../../database-engine/media//dv3wbi9.gif "Icône Visual Database Tools")<br /><br /> ![Icône Visual Database Tools](../../database-engine/media//dv3wbia.gif "Icône Visual Database Tools")|Spécifie si une colonne de données apparaît dans l'ensemble des résultats de la requête (requête Select) ou si elle est utilisée dans une requête Update, Insert From, Make Table ou Insert Into. Sélectionnez la colonne pour l'ajouter aux résultats. Si **(Toutes les colonnes)** est sélectionné, toutes les colonnes de données figurent dans le résultat.<br /><br /> L'icône utilisée avec la case à cocher dépend du type de requête que vous créez. Lorsque vous créez une requête Delete, vous ne pouvez pas sélectionner des colonnes individuelles.|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbib.gif "Icône Visual Database Tools")<br /><br /> ![Icône Visual Database Tools](../../database-engine/media//dv3wbic.gif "Icône Visual Database Tools")|Indique si la colonne de données sert à trier les résultats de la requête (fait partie d'une clause ORDER BY). L'icône indique A-Z pour un ordre de tri croissant et Z-A pour un ordre de tri décroissant.|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbid.gif "Icône Visual Database Tools")|Indique si la colonne de données sert à créer un ensemble de résultats groupés (fait partie d'une clause GROUP BY) dans une requête d'agrégation.|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbie.gif "Icône Visual Database Tools")|Indique si la colonne de données est incluse dans une condition de recherche de la requête (fait partie d'une clause WHERE ou HAVING).|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbif.gif "Icône Visual Database Tools")|Indique si le contenu de la colonne de données est utilisé dans une synthèse (s'il est inclus dans une fonction d'agrégation telle que SUM ou AVG).|  
  
> [!NOTE]  
>  Le Concepteur de requêtes et de vues n'affiche pas les colonnes de données d'une table ou d'un objet table si vous ne disposez pas des droits d'accès correspondants ou si le pilote de base de données ne parvient pas à retourner des informations le concernant. Dans de tels cas, le Concepteur de requêtes et de vues n'affiche que la barre de titre de la table ou de l'objet structuré en table.  
  
## <a name="joined-tables-on-the-diagram-pane"></a>Tables jointes sur le volet Schéma  
 Si la requête implique une jointure, une ligne de jointure apparaît entre les colonnes de données impliquées dans la jointure. Si des colonnes de données jointes ne sont pas affichées (parce que, par exemple, la fenêtre de la table ou de l'objet table est réduite ou la jointure implique une expression), le Concepteur de requêtes et de vues place la ligne de jointure dans la barre de titre du rectangle représentant la table ou l'objet table. Il affiche une ligne de jointure par condition de jointure.  
  
 La forme de l'icône au milieu de la ligne de jointure indique la façon dont les tables ou les objets structurés en table sont joints. Si la clause de jointure utilise un autre opérateur que le signe égal (=), il s'affiche dans l'icône de la ligne de jointure. Le tableau suivant fait la liste des icônes qui peuvent être affichées dans une ligne de jointure.  
  
|Icône de la ligne de jointure|Description|  
|--------------------|-----------------|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbih.gif "Icône Visual Database Tools")|Jointure interne (créée avec l'opérateur « égal »).|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbii.gif "Icône Visual Database Tools")|Jointure interne basée sur l'opérateur « plus grand que ». (L'opérateur affiché dans la ligne de jointure est celui qui est utilisé pour la jointure.)|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbij.gif "Icône Visual Database Tools")|Jointure externe dans laquelle toutes les lignes de la table représentée à gauche seront incluses, même si elles n'ont pas de correspondance dans la table en relation.|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbik.gif "Icône Visual Database Tools")|Jointure externe dans laquelle toutes les lignes de la table représentée à droite seront incluses, même si elles n'ont pas de correspondance dans la table en relation.|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbil.gif "Icône Visual Database Tools")|Jointure externe entière dans laquelle toutes les lignes des deux tables seront incluses, même si elles n’ont pas de correspondance dans la table en relation.|  
  
 Les icônes présentes aux extrémités de la ligne de jointure indiquent le type de jointure. Le tableau suivant fait la liste des types de jointures et des icônes pouvant apparaître aux extrémités de la ligne de jointure.  
  
|Icône aux extrémités de la ligne de jointure|Description|  
|-------------------------------|-----------------|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbim.gif "Icône Visual Database Tools")|Jointure Un-à-un|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbin.gif "Icône Visual Database Tools")|Jointure Un-à-plusieurs|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbio.gif "Icône Visual Database Tools")|Le Concepteur de requêtes et de vues ne peut pas déterminer le type de jointure|  
  
## <a name="see-also"></a>Voir aussi  
 [Concevoir des requêtes et des vues des rubriques de procédures &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Volet Critères &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md)   
 [Trier et regrouper des résultats de requête &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)  
  
  
