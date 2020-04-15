---
title: Types de données paramètres (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: f29bb70937df32e03480c13c7ef739eb273f15eb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303580"
---
# <a name="parameter-data-types"></a>Types de données de paramètre
Même si chaque paramètre spécifié avec **SQLBindParameter** est défini à l’aide d’un type de données SQL, les paramètres d’une déclaration SQL n’ont pas de type de données intrinsèque. Par conséquent, les marqueurs de paramètres ne peuvent être inclus dans une déclaration SQL que si leurs types de données peuvent être déduits d’un autre opérande dans la déclaration. Par exemple, dans une expression arithmétique comme ? COLUMN1, le type de données du paramètre peut être déduit du type de données de la colonne nommée représentée par COLUMN1. Une application ne peut pas utiliser un marqueur de paramètres si le type de données ne peut pas être déterminé.  
  
 Le tableau suivant décrit comment un type de données est déterminé pour plusieurs types de paramètres, conformément à SQL-92. Pour obtenir des spécifications plus complètes sur l’infération du type de paramètre lors de l’utilisation d’autres clauses SQL, consultez les spécifications SQL-92.  
  
|Emplacement du paramètre|Type de données supposés|  
|---------------------------|-----------------------|  
|Un opéra d’un opérateur binaire d’arithmétique ou de comparaison|Comme l’autre opérande|  
|Le premier opéra dans une clause **BETWEEN**|Comme le deuxième opéra|  
|Le deuxième ou troisième opérande d’une clause **BETWEEN**|Comme le premier opéra|  
|Une expression utilisée avec **IN**|Tout comme la première valeur ou la colonne de résultat de la sous-pays|  
|Une valeur utilisée avec **IN**|Tout comme l’expression ou la première valeur s’il y a un marqueur de paramètre dans l’expression|  
|Une valeur de modèle utilisée avec **LIKE**|VARCHAR|  
|Une valeur de mise à jour utilisée avec **UPDATE**|Idem pour la colonne de mise à jour|
