---
title: Fonction SQL-92 CAST (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09d2a2de710dafd4e744166c4219f4c903fd3321
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305060"
---
# <a name="sql-92-cast-function"></a>CAST (SQL-92), fonction
La fonction **CAST** définie dans SQL-92 est équivalente à la fonction **CONVERT** définie dans ODBC. La syntaxe des fonctions équivalentes est la suivante :  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 La fonction SQL-92 **CAST** exige quels types de données peuvent être convertis à d’autres types de données. (Pour plus d’informations, consultez les spécifications SQL-92.) La fonction **CAST** est soutenue au niveau de transition FIPS.  
  
 Une application peut déterminer le support de la fonction **CAST** comme suit :  
  
1.  Appelez **SQLGetInfo** avec le type d’information SQL_SQL_CONFORMANCE. Si la valeur de retour pour le type d’information est SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE ou SQL_SC_SQL92_FULL, la fonction **CAST** est prise en charge.  
  
2.  Si la valeur de retour du type d’information SQL_SQL_CONFORMANCE est SQL_SC_ENTRY_LEVEL ou 0, appelez **SQLGetInfo** avec le type d’information SQL_SQL92_VALUE_EXPRESSIONS. Si le SQL_SVE_CAST bit est réglé, la fonction **CAST** est prise en charge.
