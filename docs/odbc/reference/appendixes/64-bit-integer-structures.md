---
title: Entier 64 bits en Structures | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e19cdf837f25d7532804780eeef6b2fdf32b3f53
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="64-bit-integer-structures"></a>Structures d’entier 64 bits
Le type C pour les identificateurs de type de données SQL_C_SBIGINT et SQL_C_UBIGINT sur les compilateurs Microsoft C est _int64. Lorsqu’un compilateur à un compilateur de Microsoft® C est utilisé, le type C peut être différent. Si le compilateur prend en charge les entiers 64 bits en mode natif, le pilote ou l’application doit définir ODBCINT64 pour être le type d’entier 64 bits natif. Si le compilateur ne prend pas en charge les entiers 64 bits en mode natif, une application ou le pilote peut définir les structures suivantes pour vous assurer qu’il a accès à ces données :  
  
```  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLUINTEGER dwHighWord;  
} SQLUBIGINT  
  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLINTEGER sdwHighWord;  
} SQLBIGINT  
```  
  
 Ces structures doivent être alignées sur une limite de 8 octets, car un entier 64 bits est aligné sur la limite de 8 octets.
