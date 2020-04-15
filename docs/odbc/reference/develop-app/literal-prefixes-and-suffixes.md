---
title: Préfixes et suffixes littérals Microsoft Docs
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
ms.openlocfilehash: d52ca54c329353e3d9dc67ca35d89b2d28cedf74
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287981"
---
# <a name="literal-prefixes-and-suffixes"></a>Préfixes et suffixes de littéraux
Dans une déclaration SQL, un *littéral* est une représentation de caractère d’une valeur de données réelle. Par exemple, dans la déclaration suivante, ABC, FFFF et 10 sont des littérals :  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Les littérals de certains types de données nécessitent des préfixes et des suffixes spéciaux. Dans l’exemple précédent, le personnage littéral (ABC) nécessite une seule marque de citation (') comme un préfixe et un suffixe, le binaire littéral (FFFF) nécessite les caractères 0x comme préfixe, et l’integer littéral (10) ne nécessite pas un préfixe ou un suffixe.  
  
 Pour tous les types de données, sauf date, heure et timetamps, les applications interopérables doivent utiliser les valeurs retournées dans les colonnes LITERAL_PREFIX et LITERAL_SUFFIX dans le résultat défini par **SQLGetTypeInfo**. Pour les fins de date, d’heure, d’arrêt et d’intervalles de date, les applications interopérables devraient utiliser les séquences d’évacuation discutées dans la section précédente.
