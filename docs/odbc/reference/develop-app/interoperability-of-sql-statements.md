---
title: Interopérabilité des déclarations SQL (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3d7a76c67096d2e76fe1cd3d4b15f73122699e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302800"
---
# <a name="interoperability-of-sql-statements"></a>Interopérabilité des instructions SQL
Comme le reste d’une application, les relevés SQL peuvent être interopérables ou spécifiques à DBMS. Et comme le reste de l’application, le choix de la façon dont les déclarations SQL interopérables doivent être dépend du type d’application. Les applications personnalisées sont moins susceptibles d’utiliser des relevés SQL interopérables parce qu’elles sont généralement conçues pour exploiter les capacités d’un ou peut-être deux DBMS. Les applications génériques utilisent des déclarations SQL interopérables parce qu’elles sont conçues pour fonctionner avec une variété de DBMS. Et les applications verticales tombent généralement quelque part entre les deux, exigeant un certain niveau de fonctionnalité, mais autrement en utilisant des déclarations SQL interopérables.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Choix d’une grammaire SQL](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [Construction d’instructions SQL interopérables](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
