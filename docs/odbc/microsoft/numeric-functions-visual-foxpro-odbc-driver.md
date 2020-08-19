---
description: Fonctions numériques (pilote ODBC Visual FoxPro)
title: Fonctions numériques (pilote ODBC Visual FoxPro) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c8728446decd8a0ad04f08d88475ae08a7c69c5f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449371"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>Fonctions numériques (pilote ODBC Visual FoxPro)
Le tableau suivant décrit les fonctions numériques ODBC prises en charge par le pilote ODBC Visual FoxPro. Lorsque la grammaire Visual FoxPro pour la même fonction diffère de la syntaxe ODBC, l’équivalent Visual FoxPro est listé.  
  
|Grammaire ODBC|Grammaire de Visual FoxPro|  
|------------------|---------------------------|  
|ABS *(numeric_exp)*||  
|ACOS *(float_exp)*||  
|ASIN *(float_exp)*||  
|ATAN *(float_exp)*||  
|ATAN2 *(float_exp1, float_exp2)*|ATN2 (*float_exp1, float_exp2*)|  
|PLAFOND *(numeric_exp)*||  
|COS *(float_exp)*||  
|COT *(float_exp)*||  
|DEGRÉS *(numeric_exp)*|RTOD *(numeric_exp)*|  
|EXP *(float_exp)*||  
|PLANCHER *(numeric_exp)*||  
|JOURNAL *(float_exp)*||  
|LOG10 *(float_exp)*||  
|MOD *(integer_exp1, integer_exp2)*||  
|PI *()*||  
|RADIANs *(numeric_exp)*|DTOR *(numeric_exp)*|  
|RAND *([integer_exp])*||  
|ROUND *(numeric_exp, integer_exp)*||  
|SIGNE *(numeric_exp)*||  
|SIN *(float_exp)*||  
|SQRT *(float_exp)*||  
|BRUN *(float_exp)*||  
  
 Les fonctions numériques suivantes ne sont pas prises en charge :  
  
 PUISSANCE *(numeric_exp, integer_exp)*  
  
 TRUNCATE *(numeric_exp, integer_exp)*
