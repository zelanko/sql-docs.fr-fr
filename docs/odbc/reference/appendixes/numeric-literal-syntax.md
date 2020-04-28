---
title: Syntaxe des littéraux numériques | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299859"
---
# <a name="numeric-literal-syntax"></a>Syntaxe des littéraux numériques
La syntaxe suivante est utilisée pour les littéraux numériques dans ODBC :  
  
 *Numeric-Literal* :: = *signed-numeric-Literal &#124; non signé-Numeric-Literal*  
  
 Signed *-Numeric-Literal* :: = [*Sign*] non *signé-Numeric-Literal*  
  
 *unsigned-Numeric-littéral* :: = *exact-numeric-Literal &#124; littéral approximatif-Numeric*  
  
 *exact-Numeric-littéral* :: = *unsigned-Integer* [*point*[*unsigned-Integer*]] *&#124;point unsigned-Integer*  
  
 *Sign* :: = signe *plus &#124; signe moins (-)*  
  
 *approximatif-Numeric-Literal* :: = *mantisse E Exponent*  
  
 *mantisse* :: = *expression-littérale exacte*  
  
 *Exponent* :: = *signed-integer*  
  
 Signed *-Integer* :: = [*Sign*] non *signé-Integer*  
  
 *unsigned-entier* :: = *digit...*  
  
 signe *plus* :: =*+*  
  
 signe *moins* :: =-  
  
 *chiffre* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *période* :: =.
