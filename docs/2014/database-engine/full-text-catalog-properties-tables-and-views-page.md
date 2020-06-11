---
title: Propriétés du catalogue de texte intégral (page tables et vues) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.tablesviews.f1
ms.assetid: 2d45fcd2-0f0f-4167-9027-316d6696c106
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 205ee5d7c316c9a81e82edc0b2b6d132ed5c0ae1
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83858676"
---
# <a name="full-text-catalog-properties-tables-and-views-page"></a>Propriétés du catalogue de texte intégral (page Tables et vues)
  Utilisez cette page de dialogue pour consulter ou modifier les tables et les vues qui sont attribuées au catalogue de texte intégral.  
  
## <a name="ui-element-list"></a>Liste des éléments d’interface utilisateur  
 **Tous les objets admissibles de table ou de vue dans cette base de données**  
 Répertorie les tables et les vues sur lesquelles un index unique est défini, mais qui ne font pas déjà partie du catalogue de texte intégral. Pour sélectionner une table ou une vue et l’affecter au catalogue, sélectionnez les éléments dans la zone de liste et appuyez sur le bouton « -> ».  
  
 **Objets de table ou de vue attribués au catalogue**  
 Répertorie les tables et les vues qui sont actuellement attribuées au catalogue de texte intégral.  
  
## <a name="selected-object-properties"></a>Propriétés de l'objet sélectionné  
 **Propriétés de l'objet sélectionné**  
 Affiche les propriétés de l'objet sélectionné dans la liste des objets attribués au catalogue.  
  
 **Index unique**  
 Répertorie les index uniques de la table ou de la vue qui sont disponibles.  
  
 **Table activée pour la recherche en texte intégral**  
 Activez cette case à cocher pour activer l'indexation de texte intégral sur la table. Désactivez cette case à cocher pour désactiver l'indexation de texte intégral.  
  
## <a name="eligible-columns-grid"></a>Grille des colonnes admissibles  
  
|||  
|-|-|  
|**Colonnes disponibles**|Affiche toutes les colonnes qui sont indexées en texte intégral. Activez une case à cocher pour ajouter une colonne à l'index de texte intégral.|  
|**Langue pour l'analyseur lexical**|Affiche le langage de l'analyseur lexical.|  
|**Colonne de type de données**|Répertorie le nom de la colonne dans la table qui contient le type de document de la colonne répertoriée dans **colonnes disponibles** si la colonne est une `varbinary(max)` `image` colonne ou.|  
|**Sémantique statistique**|Sélectionnez s'il faut activer l'indexation sémantique pour la colonne sélectionnée. Pour plus d’informations, consultez [Recherche sémantique &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).<br /><br /> Si vous sélectionnez une **langue** avant de sélectionner **Sémantique statistique**, et que la langue sélectionnée n'est pas associée à un modèle linguistique sémantique, la case à cocher **Sémantique statistique** est désactivée. Si vous sélectionnez **Sémantique statistique** avant de sélectionner une **langue**, les langues disponibles dans la zone de liste déroulante sont limitées à celles pour lesquelles il existe une prise en charge de modèle linguistique sémantique.|  
  
## <a name="track-changes"></a>Suivi des modifications  
  
|||  
|-|-|  
|**Automatique**|L'index de recherche en texte intégral est automatiquement mis à jour lorsque des données sont modifiées, ajoutées ou supprimées dans la table sous-jacente.|  
|**Manuel**|Lorsque des données sont modifiées, ajoutées ou supprimées dans les données indexées, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] effectue le suivi des modifications. Lorsque le suivi **Manuel** des modifications est activé, l'index n'est pas automatiquement mis à jour. Par contre, un administrateur peut appliquer les modifications manuellement à l’aide d’une instruction [ALTER FULLTEXT INDEX ... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) .|  
|**Aucun suivi**|Lorsque cette option est activée, les modifications apportées aux données indexées du catalogue ne sont pas enregistrées. Un administrateur doit générer l'index en utilisant ALTER FULLTEXT INDEX avec FULL POPULATION ou INCREMENTAL POPULATION.|  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)   
 [Alimenter des index de recherche en texte intégral](../relational-databases/indexes/indexes.md)  
  
  
