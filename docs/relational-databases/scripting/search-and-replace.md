---
title: "Recherche et remplacement | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "respect de la casse [SQL Server]"
  - "opérations d'annulation"
  - "recherches [SQL Server Management Studio]"
  - "remplacement de texte"
  - "recherche rapide et remplacement [SQL Server Management Studio]"
  - "éditeur de requêtes [SQL Server Management Studio], annuler"
  - "éditeur de requêtes [SQL Server Management Studio], recherche"
  - "expressions régulières [SQL Server Management Studio]"
  - "recherche de texte [SQL Server Management Studio]"
  - "texte [SQL Server], opérations de recherche et de remplacement"
  - "recherche [SQL Server Management Studio]"
  - "recherche de texte"
  - "éditeur de requêtes [SQL Server Management Studio], remplacement de texte"
  - "Rechercher et remplacer, boîte de dialogue"
  - "options des caractères génériques [SQL Server Management Studio]"
  - "mot entier [SQL Server]"
  - "recherches [SQL Server Management Studio], remplacement"
ms.assetid: 3641c7b3-3e3e-4ddd-af82-c15b50004f94
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Recherche et remplacement
  Il existe plusieurs méthodes différentes pour rechercher et remplacer du texte. Dans le menu **Edition**, la commande **Rechercher et remplacer** propose quatre options : **Recherche rapide**, **Remplacement rapide**, **Rechercher dans les fichiers** ou **Remplacer dans les fichiers**. Chaque option ouvre une version de la boîte de dialogue **Rechercher et remplacer**. Vous pouvez également effectuer une recherche sans l'aide de l'une de ces boîtes de dialogue. Pour ce faire, il vous suffit d'utiliser les touches de raccourci clavier de la recherche incrémentielle. Ces techniques vous permettent de contrôler la portée de l'opération de recherche et de remplacement et de choisir la méthode de révision des occurrences trouvées et des remplacements.  
  
 Tenez compte des informations suivantes lorsque vous recherchez et remplacez du texte :  
  
-   Les options définies dans la boîte de dialogue **Rechercher et remplacer** affectent toutes les recherches. Ces options comprennent **Respecter la casse**, **Mot entier**, **Rechercher vers le haut**, **Rechercher le texte masqué**, **Caractères génériques**, **Expressions régulières**, **Regarder dans tous les documents ouverts** et **Regarder dans le projet en cours**. Les options ne sont pas toutes disponibles dans toutes les versions de la boîte de dialogue **Rechercher et remplacer**.  
  
-   La commande **Annuler** est disponible uniquement pour les documents qui sont restés ouverts après une opération de remplacement.  
  
-   L’action **Annuler** pour une opération **Remplacer tout** qui s’étend sur plusieurs fichiers est considérée comme une action en bloc sur tous les fichiers affectés. Par conséquent, vous ne pouvez pas annuler des modifications dans certains fichiers et les conserver dans d'autres.  
  
 En règle générale, vous ne pouvez pas rechercher des éléments avec des vues graphiques.  
  
## Voir aussi  
 [Effectuer une recherche incrémentielle dans un document actif](../../relational-databases/scripting/search-an-active-document-incrementally.md)   
 [Effectuer une recherche de façon interactive dans des documents](../../relational-databases/scripting/search-documents-interactively.md)   
 [Effectuer une recherche dans des documents à l'aide des listes de résultats](../../relational-databases/scripting/search-documents-using-results-lists.md)   
 [Rechercher du texte avec des caractères génériques](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [Rechercher du texte avec des expressions régulières](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  