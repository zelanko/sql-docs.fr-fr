---
title: Métadonnées de l’ensemble des résultats (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300079"
---
# <a name="result-set-metadata"></a>Métadonnées des jeux de résultats
*Les métadonnées* sont des données qui décrivent d’autres données. Par exemple, les métadonnées définies de résultat décrivent l’ensemble de résultats, tels que le nombre de colonnes dans l’ensemble de résultats, les types de données de ces colonnes, leurs noms, la précision, l’annulation, et ainsi de suite.  
  
 Les applications interopérables doivent toujours vérifier les métadonnées des colonnes définies de résultats. Les métadonnées d’une colonne dans un ensemble de résultats peuvent différer des métadonnées de la colonne telles qu’elles sont retournées par une fonction de catalogue. Supposons, par exemple, qu’une colonne updatable soit incluse dans un ensemble de résultats créé en rejoignant deux tables. Bien que **SQLColumnPrivileges** puisse indiquer qu’un utilisateur peut mettre à jour la colonne, les métadonnées définies de résultat pourraient ne pas si la colonne est du côté « nombreux » de la jointure ; de nombreuses sources de données peuvent mettre à jour les colonnes du côté « un » d’une jointure, mais pas du côté du « grand nombre ». Même les types de données ne peuvent pas être supposés être les mêmes, parce que la source de données peut promouvoir le type de données tout en créant l’ensemble de résultats.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Comment les métadonnées sont-elles utilisées ?](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol et SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)
