---
title: Sélectionner les lignes ne correspondant pas à une valeur (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe569d2b93def44db3af6c769ca975823c218a4c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169810"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Sélectionner les lignes ne correspondant pas à une valeur (Visual Database Tools)
  Pour rechercher des lignes ne correspondant pas à une valeur, utilisez l'opérateur NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Pour rechercher des lignes ne correspondant pas à une valeur  
  
1.  Si ce n’est déjà fait, ajoutez les colonnes ou les expressions que vous souhaitez utiliser dans votre condition de recherche au [volet Critères](visual-database-tools.md).  
  
2.  Localisez la ligne comportant l’expression ou la colonne de données à rechercher, puis entrez l’opérateur NOT suivi d’une valeur de recherche dans la colonne de la grille **Filtre** .  
  
 Si vous souhaitez, par exemple, rechercher toutes les lignes figurant dans une table `products` dans laquelle les valeurs de la colonne des codes produits commencent par un autre caractère que « A », vous pouvez alors entrer la condition de recherche suivante :  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Valeurs de recherche de règles pour l’entrée &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Spécifier des critères de recherche &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
