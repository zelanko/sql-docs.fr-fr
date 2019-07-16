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
ms.openlocfilehash: 9daa81e2e0c2e927ee7407d4a00d5d48c333bd54
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67990715"
---
# <a name="numeric-literal-syntax"></a>Syntaxe des littéraux numériques
La syntaxe suivante est utilisée pour les littéraux numériques dans ODBC :  
  
 *littéral numérique* :: = *littéral numérique signé &#124; littéral numérique non signé*  
  
 *littéral numérique signé* :: = [*connexion*] *littéral numérique non signé*  
  
 *unsigned-numeric-literal* ::= *exact-numeric-literal &#124; approximate-numeric-literal*  
  
 *littéral numérique exacte* :: = *entier non signé* [*période*[*entier non signé*]]  *&#124;entier non signé période*  
  
 *sign* ::= *plus-sign &#124; minus-sign*  
  
 *littéral numérique approximatif* :: = *exposant de la mantisse E*  
  
 *mantisse* :: = *littéral numérique exacte*  
  
 *exposant* :: = *entier signé*  
  
 *entier signé* :: = [*connexion*] *entier non signé*  
  
 *entier non signé* :: = *chiffre...*  
  
 *signe* :: = *+*  
  
 *signe* :: = -  
  
 *digit* ::= 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *période* :: =.
