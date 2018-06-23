---
title: Créer des requêtes de recherche en texte intégral (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3963876ce326529fd2538adc2d303d218406a924
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051200"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Créer des requêtes de recherche en texte intégral (Visual Database Tools)
  La recherche en texte intégral utilise le prédicat CONTAINS pour localiser les lignes contenant le texte spécifié dans une colonne donnée. Les recherches en texte intégral ne sont possibles que sur les colonnes possédant des index de texte intégral actifs. Si vous tentez d'utiliser la clause CONTAINS sur une colonne qui ne possède pas d'index de texte intégral actuellement actif, une erreur s'affiche. Pour plus d’informations sur les index de recherche en texte intégral et de la clause CONTAINS, consultez [recherche en texte intégral](../../relational-databases/search/full-text-search.md) et [contient &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).  
  
### <a name="to-create-a-full-text-search-query"></a>Pour créer une requête de recherche en texte intégral  
  
1.  Ouvrez une requête dans l'Explorateur de solutions ou créez-en une nouvelle.  
  
2.  Dans la clause WHERE de votre requête, utilisez la fonction CONTAINS pour rechercher une colonne de texte intégral.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des Types de requêtes &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Rubriques de procédures de requêtes et les vues de conception &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
