---
title: Cartographie SQLBindParam (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1df595722297c91dc75398470912188e109e278
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305439"
---
# <a name="sqlbindparam-mapping"></a>SQLBindParam, mappage
**SQLBindParam** ne peut pas vraiment être appelé déprécié parce qu’il n’a jamais été là dans ODBC; cependant, il représente toujours des fonctionnalités dupliquées - le Driver Manager doit l’exporter parce que les applications COMPATIBLEs ISO et Open Group l’utiliseront. Parce que **SQLBindParameter** contient toutes les fonctionnalités de **SQLBindParam**, **SQLBindParam** sera cartographié sur le dessus de **SQLBindParameter** (lorsque le conducteur sous-jacent est un pilote ODBC *3.x).* Un pilote ODBC *3.x* n’a pas besoin d’implémenter **SQLBindParam**.  
  
## <a name="remarks"></a>Notes  
 Lorsque l’appel suivant à **SQLBindParam** est fait:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 le gestionnaire de conducteur appelle **SQLBindParameter** dans le conducteur comme suit:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Consultez [ODBC 64-Bit Information](../../../odbc/reference/odbc-64-bit-information.md), si votre application s’exécute sur un système d’exploitation 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des fonctions dépréciées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
