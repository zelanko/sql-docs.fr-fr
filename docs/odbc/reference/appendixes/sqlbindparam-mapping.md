---
title: SQLBindParam, mappage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57e0fe66d76f91c8cea35710e9d0245db7619628
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52544433"
---
# <a name="sqlbindparam-mapping"></a>SQLBindParam, mappage
**SQLBindParam** ne peut pas réellement être appelée déconseillé, car il n’a jamais été il dans ODBC ; Toutefois, il représente toujours les fonctionnalités en double : le Gestionnaire de pilotes doit exporter, car les applications ISO et conforme Open groupe l’utiliserez. Étant donné que **SQLBindParameter** contient toutes les fonctionnalités de **SQLBindParam**, **SQLBindParam** seront mappées sur des **SQLBindParameter** (lorsque le pilote sous-jacent est un ODBC 3 *.x* pilote). Un ODBC 3 *.x* pilote n’a pas besoin d’implémenter **SQLBindParam**.  
  
## <a name="remarks"></a>Notes  
 Lorsque l’appel suivant à **SQLBindParam** est effectuée :  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 les appels du Gestionnaire de pilotes **SQLBindParameter** dans le pilote comme suit :  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Consultez [informations sur ODBC 64 bits](../../../odbc/reference/odbc-64-bit-information.md), si votre application s’exécutera sur un système d’exploitation 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des fonctions dépréciées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
