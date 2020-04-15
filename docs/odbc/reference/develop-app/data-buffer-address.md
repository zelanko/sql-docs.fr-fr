---
title: Adresse tampon de données (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 578e4e37a78818cb640d9f32e2480cec5951df63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305270"
---
# <a name="data-buffer-address"></a>Adresse du tampon de données
L’application transmet l’adresse du tampon de données au conducteur dans un argument, souvent nommé *ValuePtr* ou un nom similaire. Par exemple, dans l’appel suivant à **SQLBindCol**, l’application spécifie l’adresse de la variable *Date* :  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Comme mentionné dans la section [Allocating and Freeing Buffers,](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) l’adresse d’un tampon différé doit rester valide jusqu’à ce que le tampon ne soit pas lié.  
  
 À moins qu’il ne soit expressément interdit, l’adresse d’un tampon de données peut être un pointeur nul. Pour les tampons utilisés pour envoyer des données au conducteur, cela amène le conducteur à ignorer les informations normalement contenues dans le tampon. Pour les tampons utilisés pour récupérer les données du conducteur, cela amène le conducteur à ne pas retourner une valeur. Dans les deux cas, le conducteur ignore l’argument de longueur tampon de données correspondante.
