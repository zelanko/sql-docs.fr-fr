---
title: Sélectionner des lignes ne correspondant pas à une valeur
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 56038b9497f60c2a3275c9216d5c2252d65d81f3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86010603"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Sélectionner les lignes ne correspondant pas à une valeur (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Pour rechercher des lignes ne correspondant pas à une valeur, utilisez l'opérateur NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Pour rechercher des lignes ne correspondant pas à une valeur  
  
1.  Si ce n’est déjà fait, ajoutez les colonnes ou les expressions que vous souhaitez utiliser dans votre condition de recherche au [volet Critères](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md).  
  
2.  Localisez la ligne comportant l’expression ou la colonne de données à rechercher, puis entrez l’opérateur NOT suivi d’une valeur de recherche dans la colonne de la grille **Filtre** .  
  
Si vous souhaitez, par exemple, rechercher toutes les lignes figurant dans une table `products` dans laquelle les valeurs de la colonne des codes produits commencent par un autre caractère que « A », vous pouvez alors entrer la condition de recherche suivante :  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Voir aussi  
[Règles pour l’entrée de valeurs de recherche](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Spécifier des critères de recherche](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
