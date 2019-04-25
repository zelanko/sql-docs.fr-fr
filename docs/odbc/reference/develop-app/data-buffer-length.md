---
title: Longueur du tampon de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- buffers [ODBC], data
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 7288d143-f9e5-4f90-9b31-2549df79c109
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57f4fd34cfe3896bb29ed31f02906ce675e4b854
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62640495"
---
# <a name="data-buffer-length"></a>Longueur du tampon de données
L’application transmet la longueur d’octet de la mémoire tampon de données pour le pilote dans un argument nommé *BufferLength* ou un nom similaire. Par exemple, dans l’exemple suivant appel à **SQLBindCol**, l’application spécifie la longueur de la *ValuePtr* tampon (**sizeof (***ValuePtr***)**):  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Un pilote retournera toujours le nombre d’octets, pas le nombre de caractères, dans l’argument de longueur de mémoire tampon de n’importe quelle fonction qui a un argument de chaîne de sortie.  
  
 Longueurs de mémoire tampon de données sont uniquement requises pour les mémoires tampons de sortie ; le pilote les utilise pour éviter d’écrire au-delà de la fin de la mémoire tampon. Toutefois, le pilote vérifie la longueur de mémoire tampon de données uniquement lorsque la mémoire tampon contient des données de longueur variable, telles que les données binaires ou caractères. Si la mémoire tampon contient des données de longueur fixe, comme une structure entier ou une date, le pilote ignore la longueur de mémoire tampon de données et suppose que la mémoire tampon est suffisamment grande pour contenir les données ; Autrement dit, elle tronque jamais les données de longueur fixe. Par conséquent, il est important pour l’application allouer un tampon assez grand pour les données de longueur fixe.  
  
 Lorsqu’une troncation des données non-sortie chaînes se produit (telles que le nom du curseur retourné pour **SQLGetCursorName**), la longueur retournée dans l’argument de longueur de mémoire tampon est le nombre maximal de caractères possible.  
  
 Longueurs de mémoire tampon de données ne sont pas requis pour les mémoires tampons d’entrée, car le pilote n’écrit pas dans ces mémoires tampons.  
  
 Cette section contient les rubriques suivantes.  
  
-   [À l’aide des valeurs de longueur / d’indicateur](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Longueur des données, longueur de la mémoire tampon et troncation](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Données caractères et chaînes C](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
