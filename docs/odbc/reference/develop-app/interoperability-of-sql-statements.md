---
title: Interopérabilité des instructions SQL | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb9f4ec6fbc2e6aecff8d78ff562f35f9a546405
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="interoperability-of-sql-statements"></a>Interopérabilité des instructions SQL
Comme le reste d’une application, les instructions SQL puissent être interopérable ou propres au SGBD. Et comme le reste de l’application, le choix de la façon dont l’interopérables instructions SQL doivent être dépend du type d’application. Applications personnalisées sont moins susceptibles d’utiliser des instructions SQL interopérables, car elles sont généralement conçues pour exploiter les fonctionnalités d’un ou deux éventuellement SGBD. Applications génériques utilisent des instructions SQL interopérables, car ils sont conçus pour fonctionner avec un large éventail de SGBD. Et les applications verticales généralement quelque part entre les deux, en exigeant un certain niveau de fonctionnalités, mais sinon à l’aide des instructions SQL interopérables.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Choix d’une grammaire SQL](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [Construction d’instructions SQL interopérables](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
