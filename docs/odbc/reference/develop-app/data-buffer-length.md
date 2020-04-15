---
title: Longueur de mémoire tampon de données (en anglais) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305260"
---
# <a name="data-buffer-length"></a>Longueur du tampon de données
L’application transmet la longueur d’entrée du tampon de données au conducteur dans un argument, nommé *BufferLength* ou un nom similaire. Par exemple, dans l’appel suivant à **SQLBindCol**, l’application spécifie la longueur du tampon *ValuePtr* **(taille de (***ValuePtr***)**) :  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Un pilote retournera toujours le nombre d’octets, et non le nombre de caractères, dans l’argument de longueur tampon de toute fonction qui a un argument de chaîne de sortie.  
  
 Les longueurs tampons de données ne sont requises que pour les tampons de sortie; le conducteur les utilise pour éviter d’écrire au-delà de la fin du tampon. Toutefois, le pilote ne vérifie la longueur du tampon de données que lorsque le tampon contient des données à durée variable, telles que les données de caractère ou binaires. Si le tampon contient des données à durée fixe, telles qu’une structure d’intégrateur ou de date, le conducteur ignore la longueur du tampon de données et suppose que le tampon est suffisamment grand pour contenir les données; c’est-à-dire qu’il n’tronque jamais les données fixes. Il est donc important que l’application alloue un tampon suffisamment grand pour les données à durée fixe.  
  
 Lorsqu’une troncation des chaînes de sortie non de données se produit (comme le nom de curseur retourné pour **SQLGetCursorName**), la longueur retournée dans l’argument de longueur tampon est la longueur maximale du caractère possible.  
  
 Les longueurs de mémoire tampon de données ne sont pas nécessaires pour les tampons d’entrée parce que le conducteur n’écrit pas à ces tampons.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Utilisation des valeurs de longueur/indicateur](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Longueur des données, longueur de la mémoire tampon et troncation](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Données caractères et chaînes C](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
