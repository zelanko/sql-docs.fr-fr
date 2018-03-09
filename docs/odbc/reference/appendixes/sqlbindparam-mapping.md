---
title: Mappage de SQLBindParam | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c2ca8ae4b0b7b522259677b252e2b0d24d14b5d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlbindparam-mapping"></a>Mappage de SQLBindParam
**SQLBindParam** ne peut pas réellement être appelée déconseillée car elle n’a jamais été il dans ODBC ; Toutefois, il représente toujours une fonctionnalité en double, le Gestionnaire de pilotes doit exporter car ISO et ouvrez groupe compatibles avec les applications l’utiliserez. Étant donné que **SQLBindParameter** contient toutes les fonctionnalités de **SQLBindParam**, **SQLBindParam** sera mappé sur **SQLBindParameter** (lorsque le pilote sous-jacent est un ODBC 3*.x* pilote). Un ODBC 3*.x* pilote n’a pas besoin d’implémenter **SQLBindParam**.  
  
## <a name="remarks"></a>Notes   
 Lorsque l’appel suivant à **SQLBindParam** est effectuée :  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 les appels du Gestionnaire de pilotes **SQLBindParameter** dans le pilote comme suit :  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Consultez [informations ODBC 64 bits](../../../odbc/reference/odbc-64-bit-information.md), si votre application s’exécutera sur un système d’exploitation de 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des fonctions dépréciées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
