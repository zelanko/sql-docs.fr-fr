---
title: Syntaxe littérale numérique | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 18b1c144e84bf0be5aaeb68b66660f7bc7865ade
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181280"
---
# <a name="numeric-literal-syntax"></a>Syntaxe des littéraux numériques
La syntaxe suivante est utilisée pour les littéraux numériques dans ODBC :  
  
 *numeric-literal* ::= *signed-numeric-literal &#124; unsigned-numeric-literal*  
  
 *signed-numeric-literal* ::= [*sign*] *unsigned-numeric-literal*  
  
 *unsigned-numeric-literal* ::= *exact-numeric-literal &#124; approximate-numeric-literal*  
  
 *littéral numérique exacte* :: = *entier non signé* [*période*[*entier non signé*]]  *&#124;entier non signé période*  
  
 *sign* ::= *plus-sign &#124; minus-sign*  
  
 *littéral numérique approximatif* :: = *exposant de la mantisse E*  
  
 *mantisse* :: = *littéral numérique exacte*  
  
 *exposant* :: = *entier signé*  
  
 *signed-integer* ::= [*sign*] *unsigned-integer*  
  
 *entier non signé* :: = *chiffre...*  
  
 *plus-sign* ::= *+*  
  
 *minus-sign* ::= -  
  
 *digit* ::= 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *période* :: =.
