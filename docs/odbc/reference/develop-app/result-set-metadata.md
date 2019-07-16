---
title: Métadonnées du jeu de résultat | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1d8da8c15c861fff4767aa598e1b989d8f699c95
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020591"
---
# <a name="result-set-metadata"></a>Métadonnées des jeux de résultats
*Métadonnées* sont des données qui décrivent d’autres données. Par exemple, les métadonnées du jeu de résultats décrivent le jeu de résultats, telles que le nombre de colonnes dans le jeu de résultats, les types de données de ces colonnes, leurs noms, précision, possibilité de valeur null et ainsi de suite.  
  
 Applications interopérables doivent toujours vérifier les métadonnées des colonnes de jeu de résultats. Les métadonnées pour une colonne dans un jeu de résultats peuvent différer de métadonnées de la colonne tel que retourné par une fonction de catalogue. Par exemple, supposons qu’une colonne d’être mise à jour est incluse dans un jeu de résultats créé en joignant deux tables. Bien que **SQLColumnPrivileges** peut indiquer qu’un utilisateur peut mettre à jour la colonne, les métadonnées du jeu de résultats peuvent pas si la colonne se trouve sur le côté « plusieurs » de la jointure ; de nombreuses sources de données peuvent mettre à jour les colonnes sur le côté « un » d’une jointure, mais pas sur le » côté « plusieurs » ». Même les types de données ne peut pas supposés pour être le même, étant donné que la source de données peut promouvoir le type de données lors de la création du jeu de résultats.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Comment les métadonnées sont-elles utilisées ?](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol et SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)
