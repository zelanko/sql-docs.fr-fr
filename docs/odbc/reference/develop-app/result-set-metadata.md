---
title: "Générer des métadonnées du jeu | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 6d134515-e34d-4563-96d7-8ad7714818fd
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e2270cf940fc7c9bc3ccaf50977328b3a1077bd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="result-set-metadata"></a>Métadonnées du jeu de résultats
*Métadonnées* sont des données qui décrivent d’autres données. Par exemple, les métadonnées du jeu de résultats décrivent le jeu de résultats, telles que le nombre de colonnes dans le jeu de résultats, les types de données de ces colonnes, leurs noms, précision, possibilité de valeur null et ainsi de suite.  
  
 Applications interopérables doivent toujours vérifier les métadonnées des colonnes du jeu de résultats. Les métadonnées pour une colonne dans un jeu de résultats peuvent différer de métadonnées de la colonne tel que retourné par une fonction de catalogue. Par exemple, supposons qu’une colonne d’être mise à jour est incluse dans un jeu de résultats créé en joignant deux tables. Alors que **SQLColumnPrivileges** peut indiquer qu’un utilisateur peut mettre à jour la colonne, les métadonnées du jeu de résultats peuvent pas si la colonne est sur le côté « plusieurs » de la jointure ; de nombreuses sources de données peuvent mettre à jour les colonnes sur le côté « un » d’une jointure, mais pas sur le côté « plusieurs ». Même les types de données ne peut pas considéré comme étant identiques, car la source de données peut promouvoir le type de données lors de la création du jeu de résultats.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Comment les métadonnées sont-elles utilisées ?](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol et SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)
