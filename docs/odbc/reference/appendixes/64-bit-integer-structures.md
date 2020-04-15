---
title: Structures integer 64 bits (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1ecbe4dae4c1bd21ac3d542ee0d9b18169df0116
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307510"
---
# <a name="64-bit-integer-structures"></a>Structures d’entiers 64 bits
Le type C pour les identifiants de type SQL_C_SBIGINT et SQL_C_UBIGINT de données sur les compilateurs Microsoft C est _int64. Lorsqu’un compilateur autre qu’un compilateur Microsoft® C est utilisé, le type C peut être différent. Si le compilateur prend en charge les intégriers 64 bits natifs, le conducteur ou l’application devrait définir ODBCINT64 comme le type indigène d’intégrateur 64 bits. Si le compilateur ne prend pas en charge les intégraux 64 bits natifs, une application ou un conducteur peut définir les structures suivantes pour s’assurer qu’il a accès à ces données :  
  
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
  
 Ces structures doivent être alignées à une limite de 8-byte parce qu’un intégrisé 64 bits est aligné à la limite de 8-byte.
