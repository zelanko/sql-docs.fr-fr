---
title: Fonctions numériques (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73379b769da61fe14ba18815446337d0172c2805
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654401"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>Fonctions numériques (pilote ODBC Visual FoxPro)
Le tableau suivant décrit les fonctions numériques ODBC pris en charge par le pilote ODBC Visual FoxPro ; lors de la grammaire de Visual FoxPro pour la même fonction diffère de la syntaxe ODBC, le Visual FoxPro équivalent est répertorié.  
  
|Grammaire ODBC|Grammaire de Visual FoxPro|  
|------------------|---------------------------|  
|ABS *(positions numeric_exp)*||  
|ACOS *(exp_float)*||  
|ASIN *(exp_float)*||  
|ATAN *(exp_float)*||  
|ATAN2 *(exp_float1, exp_float2)*|ATN2 (*exp_float1, exp_float2*)|  
|CEILING *(positions numeric_exp)*||  
|COS *(exp_float)*||  
|COT *(exp_float)*||  
|DEGRÉS *(positions numeric_exp)*|RTOD *(positions numeric_exp)*|  
|EXP *(exp_float)*||  
|FLOOR *(positions numeric_exp)*||  
|JOURNAL *(exp_float)*||  
|LOG10 *(exp_float)*||  
|MOD *(exp_entier1, exp_entier2)*||  
|PI *)*||  
|RADIANS *(positions numeric_exp)*|DTOR *(positions numeric_exp)*|  
|RAND *([integer_exp])*||  
|ROUND *(positions numeric_exp integer_exp)*||  
|CONNEXION *(positions numeric_exp)*||  
|SIN *(exp_float)*||  
|SQRT *(exp_float)*||  
|TAN *(exp_float)*||  
  
 Les fonctions numériques suivantes ne sont pas prises en charge :  
  
 ALIMENTATION *(positions numeric_exp integer_exp)*  
  
 TRONQUER *(positions numeric_exp integer_exp)*
