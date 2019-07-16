---
title: ORDER BY liste d’expressions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [ODBC]
- SQL grammar [ODBC], order by clause
ms.assetid: 5ef88186-a99f-4e2c-a3f3-98a42d4f03a5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cd88673c4b5309b7463256b85df4f92d6d360b16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100793"
---
# <a name="order-by-expression-list"></a>ORDER BY, liste d’expressions
Expressions peuvent être utilisées dans la clause ORDER BY. Par exemple, dans les clauses suivantes, la table est triée par trois expressions clées : a + b, c + d et e.  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Aucun classement n’est autorisée sur les fonctions de jeu ou une expression qui contient une fonction set.
