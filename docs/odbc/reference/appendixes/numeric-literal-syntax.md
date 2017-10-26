---
title: "Syntaxe de littéral numérique | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 64a772d8a04015060aa717e4153bf6f36e5b74de
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="numeric-literal-syntax"></a>Syntaxe de littéral numérique
La syntaxe suivante est utilisée pour les littéraux numériques dans ODBC :  
  
 *littéral numérique* :: = *littéral numérique signé &#124; littéral numérique non signé*  
  
 *littéral numérique signé* :: = [*signe*] *littéral numérique non signé*  
  
 *littéral numérique non signée* :: = *littéral numérique exact &#124; littéral numérique approximative*  
  
 *littéral numérique exact* :: = *entier non signé* [*période*[*entier non signé*]] *&#124; période en entier non signé*  
  
 *signe* :: = *signe &#124; signe moins*  
  
 *littéral numérique approximatif* :: = *exposant de la mantisse E*  
  
 *mantisse* :: = *littéral numérique exacte*  
  
 *exposant* :: = *entier signé*  
  
 *entier signé* :: = [*signe*] *entier non signé*  
  
 *entier non signé* :: = *chiffre...*  
  
 *signe* :: =*+*  
  
 *signe moins-* :: = -  
  
 *chiffre* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *période* :: =.

