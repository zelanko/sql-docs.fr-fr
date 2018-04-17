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
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1ba90a54159f126e49148de8a8425e74d02e148d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="interoperability-of-sql-statements"></a>Interopérabilité des instructions SQL
Comme le reste d’une application, les instructions SQL puissent être interopérable ou propres au SGBD. Et comme le reste de l’application, le choix de la façon dont l’interopérables instructions SQL doivent être dépend du type d’application. Applications personnalisées sont moins susceptibles d’utiliser des instructions SQL interopérables, car elles sont généralement conçues pour exploiter les fonctionnalités d’un ou deux éventuellement SGBD. Applications génériques utilisent des instructions SQL interopérables, car ils sont conçus pour fonctionner avec un large éventail de SGBD. Et les applications verticales généralement quelque part entre les deux, en exigeant un certain niveau de fonctionnalités, mais sinon à l’aide des instructions SQL interopérables.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Choix d’une grammaire SQL](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [Construction d’instructions SQL interopérables](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
