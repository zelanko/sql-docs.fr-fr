---
title: Interopérabilité des instructions SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ed366acde11778342387d3bcb152a6619a6a3778
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138869"
---
# <a name="interoperability-of-sql-statements"></a>Interopérabilité des instructions SQL
Comme le reste d’une application, les instructions SQL peuvent être interopérables ou propres au SGBD. Et comme le reste de l’application, le choix du mode d’utilisation des instructions SQL interopérables dépend du type d’application. Les applications personnalisées sont moins susceptibles d’utiliser des instructions SQL interopérables, car elles sont généralement conçues pour exploiter les fonctionnalités d’un ou de deux SGBD. Les applications génériques utilisent des instructions SQL interopérables, car elles sont conçues pour fonctionner avec divers SGBD. En général, les applications verticales se situent entre elles, nécessitant un certain niveau de fonctionnalité, mais utilisant des instructions SQL interopérables.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Choix d’une grammaire SQL](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [Construction d’instructions SQL interopérables](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
