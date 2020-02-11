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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9daa81e2e0c2e927ee7407d4a00d5d48c333bd54
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990715"
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
