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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4a4e9a739201d74cfc6c4f7c18e64b91e0fabe4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305260"
---
# <a name="data-buffer-length"></a>Longueur du tampon de données
L’application transmet la longueur d’octet de la mémoire tampon de données au pilote dans un argument nommé *BufferLength* ou un nom similaire. Par exemple, dans l’appel suivant à **SQLBindCol**, l’application spécifie la longueur de la mémoire tampon *ValuePtr* (**sizeof (***ValuePtr***)**) :  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Un pilote retourne toujours le nombre d’octets, et non le nombre de caractères, dans l’argument de longueur de la mémoire tampon de toute fonction ayant un argument de chaîne de sortie.  
  
 Les longueurs de mémoire tampon de données sont requises uniquement pour les mémoires tampons de sortie. le pilote les utilise pour éviter d’écrire au-delà de la fin de la mémoire tampon. Toutefois, le pilote vérifie la longueur de la mémoire tampon de données uniquement lorsque la mémoire tampon contient des données de longueur variable, telles que des données de type caractère ou binaire. Si la mémoire tampon contient des données de longueur fixe, telles qu’un entier ou une structure de date, le pilote ignore la longueur de la mémoire tampon des données et suppose que la mémoire tampon est suffisamment grande pour contenir les données ; autrement dit, il ne tronque jamais les données de longueur fixe. Il est donc important pour l’application d’allouer une mémoire tampon suffisamment importante pour les données de longueur fixe.  
  
 Lorsqu’une troncation de chaînes de sortie non données se produit (par exemple, le nom de curseur renvoyé pour **SQLGetCursorName**), la longueur retournée dans l’argument de longueur de la mémoire tampon correspond à la longueur maximale de caractères possible.  
  
 Les longueurs de mémoire tampon de données ne sont pas requises pour les mémoires tampons d’entrée, car le pilote n’écrit pas dans ces mémoires tampons.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Utilisation des valeurs de longueur/indicateur](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Longueur des données, longueur de la mémoire tampon et troncation](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Données caractères et chaînes C](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
