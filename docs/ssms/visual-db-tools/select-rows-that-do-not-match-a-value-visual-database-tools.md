---
title: "Sélectionner les lignes ne correspondant pas à une valeur (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3bb314f3ded0e1b02fb4f9580c1a7ed791ea0732
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Sélectionner les lignes ne correspondant pas à une valeur (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Pour rechercher des lignes ne correspondant pas à une valeur, utilisez l’opérateur NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Pour rechercher des lignes ne correspondant pas à une valeur  
  
1.  Si ce n’est déjà fait, ajoutez les colonnes ou les expressions que vous souhaitez utiliser dans votre condition de recherche au [volet Critères](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md).  
  
2.  Localisez la ligne comportant l’expression ou la colonne de données à rechercher, puis entrez l’opérateur NOT suivi d’une valeur de recherche dans la colonne de la grille **Filtre** .  
  
Si vous souhaitez, par exemple, rechercher toutes les lignes figurant dans une table `products` dans laquelle les valeurs de la colonne des codes produits commencent par un autre caractère que « A », vous pouvez alors entrer la condition de recherche suivante :  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Voir aussi  
[Règles pour l'entrée de valeurs de recherche (Visual Database Tools)](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Spécifier des critères de recherche (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
