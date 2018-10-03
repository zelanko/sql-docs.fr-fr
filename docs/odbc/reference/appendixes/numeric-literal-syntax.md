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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601537"
---
# <a name="numeric-literal-syntax"></a>Syntaxe des littéraux numériques
La syntaxe suivante est utilisée pour les littéraux numériques dans ODBC :  
  
 *littéral numérique* :: = *littéral numérique signé &#124; littéral numérique non signé*  
  
 *littéral numérique signé* :: = [*connexion*] *littéral numérique non signé*  
  
 *littéral numérique non signé* :: = *littéral numérique exacte &#124; littéral numérique approximatif*  
  
 *littéral numérique exacte* :: = *entier non signé* [*période*[*entier non signé*]]  *&#124;entier non signé période*  
  
 *connexion* :: = *signe &#124; -signe moins*  
  
 *littéral numérique approximatif* :: = *exposant de la mantisse E*  
  
 *mantisse* :: = *littéral numérique exacte*  
  
 *exposant* :: = *entier signé*  
  
 *entier signé* :: = [*connexion*] *entier non signé*  
  
 *entier non signé* :: = *chiffre...*  
  
 *signe* :: = *+*  
  
 *signe* :: = -  
  
 *chiffre* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *période* :: =.
