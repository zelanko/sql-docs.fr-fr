---
title: Adresse du tampon de données | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7cd157edd6111dec29ae238a1c383879e66ac0b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067433"
---
# <a name="data-buffer-address"></a>Adresse du tampon de données
L’application transmet l’adresse du tampon de données pour le pilote dans un argument nommé souvent *ValuePtr* ou un nom similaire. Par exemple, dans l’exemple suivant appel à **SQLBindCol**, l’application spécifie l’adresse de la *Date* variable :  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Comme mentionné dans le [allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) section, l’adresse d’une mémoire tampon différée doit rester valide jusqu'à ce que la mémoire tampon est indépendante.  
  
 Sauf si elle est interdite en particulier, l’adresse d’une mémoire tampon de données peut être un pointeur null. Pour les mémoires tampons utilisés pour envoyer des données au pilote, cela entraîne le pilote ignorer les informations généralement contenues dans la mémoire tampon. Pour les mémoires tampons utilisées pour récupérer des données à partir du pilote, cela entraîne le pilote pour ne pas retourner une valeur. Dans les deux cas, le pilote ignore l’argument de longueur de mémoire tampon données correspondant.
