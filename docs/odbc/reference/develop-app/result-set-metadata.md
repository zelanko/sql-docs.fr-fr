---
title: Métadonnées du jeu de résultats | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 6d134515-e34d-4563-96d7-8ad7714818fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b78cdeb4c8b3522f4677c0277401cd9395a36a5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300079"
---
# <a name="result-set-metadata"></a>Métadonnées des jeux de résultats
Les *métadonnées* sont des données qui décrivent d’autres données. Par exemple, les métadonnées du jeu de résultats décrivent le jeu de résultats, comme le nombre de colonnes dans le jeu de résultats, les types de données de ces colonnes, leurs noms, la précision, la possibilité de valeur null, etc.  
  
 Les applications interopérables doivent toujours vérifier les métadonnées des colonnes du jeu de résultats. Les métadonnées d’une colonne dans un jeu de résultats peuvent différer des métadonnées de la colonne, telles qu’elles sont retournées par une fonction de catalogue. Par exemple, supposons qu’une colonne pouvant être mise à jour est incluse dans un jeu de résultats créé en joignant deux tables. Alors que **SQLColumnPrivileges** peut indiquer qu’un utilisateur peut mettre à jour la colonne, les métadonnées du jeu de résultats ne peuvent pas si la colonne se trouve sur le côté « plusieurs » de la jointure. de nombreuses sources de données peuvent mettre à jour des colonnes du côté « un » d’une jointure, mais pas du côté « plusieurs ». Même les types de données ne peuvent pas être considérés comme identiques, car la source de données peut promouvoir le type de données lors de la création du jeu de résultats.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Comment les métadonnées sont-elles utilisées ?](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol et SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)
