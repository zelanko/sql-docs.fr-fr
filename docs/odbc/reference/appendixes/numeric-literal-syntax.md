---
title: Syntaxe littérale numérique (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e035e3ec53c5b5494c029d6840b9f5c836821209
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299859"
---
# <a name="numeric-literal-syntax"></a>Syntaxe des littéraux numériques
La syntaxe suivante est utilisée pour les littérals numériques dans ODBC:  
  
 *numérique-littérale* ::- *signé-numérique-littérale &#124; non signé-numérique-littérale*  
  
 *signé-numérique-littérale* ::' [*signe*] *non signé-numérique-littérale*  
  
 *non signé-numérique-littérale* ::' *exact-numérique-littérale &#124; approximative-numérique-littérale*  
  
 *exact-numérique-littérale* ::' *non signé-integer* [*période**[non signé-integer*]] *&#124;période non signée-integer*  
  
 *signe* :: *plus-signe &#124; moins-signe*  
  
 *approximative-numérique-littérale* ::mantissa *E exposant*  
  
 *mantissa* ::' *exact-numeric-littérale*  
  
 *exposant* ::- *signé-integer*  
  
 *signé-integer* ::' [*signe*] *non signé-integer*  
  
 *non signé-integer* ::' *chiffre ...*  
  
 *plus-signe* ::MD*+*  
  
 *moins-signe* ::- -  
  
 *chiffre* :: 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *période* ::MD .
