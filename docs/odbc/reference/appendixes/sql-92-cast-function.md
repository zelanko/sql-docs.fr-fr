---
title: Fonction SQL-92 CAST | Documents Microsoft
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
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7cc176bcbf4e3d4ee0e79069e21f187ac3c00770
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sql-92-cast-function"></a>SQL-92 CAST (fonction)
Le **CAST** fonction définie dans SQL-92 est équivalente à la **convertir** fonction définie dans ODBC. La syntaxe des fonctions équivalentes est comme suit :  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 Le SQL-92 **CAST** fonction exige que les types de données peuvent être convertis pour les autres types de données. (Pour plus d’informations, consultez la spécification SQL-92). Le **CAST** fonction est prise en charge au niveau de la norme FIPS transitoire.  
  
 Une application peut déterminer la prise en charge pour le **CAST** fonctionne comme suit :  
  
1.  Appelez **SQLGetInfo** avec le type d’informations SQL_SQL_CONFORMANCE. Si la valeur de retour pour le type d’informations est SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE ou SQL_SC_SQL92_FULL, le **CAST** fonction est prise en charge.  
  
2.  Si la valeur de retour du type d’informations SQL_SQL_CONFORMANCE est SQL_SC_ENTRY_LEVEL ou 0, appelez **SQLGetInfo** avec le type d’informations SQL_SQL92_VALUE_EXPRESSIONS. Si le bit SQL_SVE_CAST est défini, le **CAST** fonction est prise en charge.
