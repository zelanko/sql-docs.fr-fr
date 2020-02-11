---
title: Propriétés de l’index de recherche en texte intégral (page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.columns.f1
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 67b7e72e0c4b248e8951667561eaf7548bfba1b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62778854"
---
# <a name="full-text-index-properties-columns-page"></a>Propriétés d'index de texte intégral (page Colonnes)
  **Pour afficher ou modifier les propriétés d'un index de recherche en texte intégral**  
  
-   [Gérer les index de recherche en texte intégral](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Index unique**  
 Sélectionnez un index dans la liste déroulante. Cet index doit être un index unique, n'acceptant pas les valeurs Null, avec une colonne à clé unique.  
  
 **Sélectionnez les colonnes admissibles à indexer en texte intégral**  
 La grille affiche les colonnes de table qui sont disponibles pour cet index de recherche en texte intégral. Les colonnes qui sont actuellement indexées en texte intégral sont cochées. Vous pouvez si vous le souhaitez cocher des colonnes supplémentaires à indexer en texte intégral.  
  
> [!IMPORTANT]  
>  Assurez-vous qu'au moins une colonne est cochée avant de cliquer sur OK.  
  
|||  
|-|-|  
|**Colonnes disponibles**|Nom de la colonne.|  
|**Langue pour l’analyseur lexical**|Langue dans laquelle les analyseurs lexicaux et les générateurs de formes dérivées effectuent une analyse linguistique sur l'ensemble des données indexées en texte intégral.<br /><br /> Pour plus d’informations, consultez [configurer et gérer des](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) analyseurs lexicaux et des générateurs de formes dérivées pour la recherche et [choisir une langue lors de la création d’un index de recherche en texte intégral](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).|  
|**Type**|Nom de la colonne de table qui contient le type de document de la colonne sélectionnée. Il s’agit d’une propriété en lecture seule.|  
|**Sémantique statistique**|Sélectionnez s'il faut activer l'indexation sémantique pour la colonne sélectionnée. Pour plus d’informations, consultez [Recherche sémantique &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).<br /><br /> Si vous sélectionnez une **langue** avant de sélectionner **Sémantique statistique**, et que la langue sélectionnée n'est pas associée à un modèle linguistique sémantique, la case à cocher **Sémantique statistique** est désactivée. Si vous sélectionnez **Sémantique statistique** avant de sélectionner une **langue**, les langues disponibles dans la zone de liste déroulante sont limitées à celles pour lesquelles il existe une prise en charge de modèle linguistique sémantique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Alimenter des index de recherche en texte intégral](../relational-databases/search/populate-full-text-indexes.md)  
  
  
