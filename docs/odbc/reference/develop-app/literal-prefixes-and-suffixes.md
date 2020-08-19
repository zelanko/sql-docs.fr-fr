---
description: Préfixes et suffixes de littéraux
title: Préfixes et suffixes littéraux | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], literal prefixes and suffixes
- literals [ODBC], prefixes and suffixes
ms.assetid: 29f468f2-f557-4a92-b31d-569c63cc6272
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0f658c401bfc31e69a6e5e2fc5110bc9a809f345
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424611"
---
# <a name="literal-prefixes-and-suffixes"></a>Préfixes et suffixes de littéraux
Dans une instruction SQL, un *littéral* est une représentation de caractères d’une valeur de données réelle. Par exemple, dans l’instruction suivante, ABC, FFFF et 10 sont des littéraux :  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Les littéraux pour certains types de données requièrent des préfixes et des suffixes spéciaux. Dans l’exemple précédent, le littéral de caractère (ABC) requiert un guillemet simple (') comme préfixe et suffixe, le littéral binaire (FFFF) requiert les caractères 0x comme préfixe et le littéral d’entier (10) ne requiert pas de préfixe ou de suffixe.  
  
 Pour tous les types de données, à l’exception de la date, de l’heure et des horodateurs, les applications interopérables doivent utiliser les valeurs retournées dans les colonnes LITERAL_PREFIX et LITERAL_SUFFIX dans le jeu de résultats créé par **SQLGetTypeInfo**. Pour les littéraux date, Time, timestamp et DateTime Interval, les applications interopérables doivent utiliser les séquences d’échappement présentées dans la section précédente.
