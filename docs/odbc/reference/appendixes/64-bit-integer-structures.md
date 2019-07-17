---
title: Entier 64 bits en Structures | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 93d9e6fd01d6b9ef98ebb10f6728ec4ba205fbb5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996256"
---
# <a name="64-bit-integer-structures"></a>Structures d’entiers 64 bits
Le type C pour les identificateurs de type de données SQL_C_SBIGINT et SQL_C_UBIGINT sur les compilateurs Microsoft C est _int64. Lorsqu’un compilateur autre qu’un compilateur de Microsoft® C est utilisé, le type C peut être différent. Si le compilateur prend en charge les entiers 64 bits en mode natif, le pilote ou l’application doit définir ODBCINT64 comme étant le type d’entier 64 bits natif. Si le compilateur ne prend pas en charge les entiers 64 bits en mode natif, une application ou le pilote peut définir les structures suivantes pour vous assurer qu’il ait accès à ces données :  
  
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
