---
title: Types de données de paramètre | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6c2a73aec119b7572cad93dedb2994235329cb2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826028"
---
# <a name="parameter-data-types"></a>Types de données de paramètre
Bien que chaque paramètre spécifié avec **SQLBindParameter** est définie à l’aide d’un type de données SQL, les paramètres dans une instruction SQL avoir aucun intrinsèques type de données. Par conséquent, les marqueurs de paramètres peuvent être inclus dans une instruction SQL uniquement si leurs types de données peuvent être déduits à partir d’un autre opérande dans l’instruction. Par exemple, dans une expression arithmétique, telle que ? + COLUMN1, le type de données du paramètre peut être déduit du type de données de la colonne nommée représenté par COLUMN1. Une application ne peut pas utiliser un marqueur de paramètre si le type de données ne peut pas être déterminé.  
  
 Le tableau suivant décrit la façon dont un type de données est déterminé pour plusieurs types de paramètres, conformément à SQL-92. Pour une spécification plus complète de déduire le type de paramètre lorsque d’autres clauses SQL sont utilisées, consultez la spécification de SQL-92.  
  
|Emplacement du paramètre|Considéré comme type de données|  
|---------------------------|-----------------------|  
|Un opérande d’un opérateur de comparaison ou arithmétique binaire|Identique à l’autre opérande|  
|Le premier opérande d’un **BETWEEN** clause|Même que le second opérande|  
|Le deuxième ou troisième opérande dans une **BETWEEN** clause|Identique à celui du premier opérande|  
|Une expression utilisée avec **IN**|Identique à la première valeur ou la colonne de résultat de la sous-requête|  
|Une valeur utilisée avec **IN**|Identique à l’expression ou la première valeur s’il existe un marqueur de paramètre dans l’expression|  
|Une valeur de modèle utilisée avec **comme**|VARCHAR|  
|Une valeur de mise à jour utilisée avec **mettre à jour**|La colonne de la mise à jour|
