---
title: Construction d’instructions SQL interopérables | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], constructing statements
ms.assetid: dee6f7e2-bcc4-4c74-8c7c-12aeda8a90eb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc8072a6d7291a546f0f12256aa4b336da037a83
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281089"
---
# <a name="constructing-interoperable-sql-statements"></a>Construction d’instructions SQL interopérables
Comme indiqué dans les sections précédentes, les applications interopérables doivent utiliser la grammaire SQL ODBC. Au-delà, grâce à cette grammaire, toutefois, un nombre de problèmes supplémentaires est confronté à des applications interopérables. Par exemple, ce que fait une application ? si elle souhaite utiliser une fonctionnalité, telles que les jointures externes, qui n’est pas pris en charge par toutes les sources de données  
  
 À ce stade, le writer d’application doit prendre certaines décisions concernant les fonctionnalités de langage requises et facultatifs. Dans la plupart des cas, si un pilote spécifique ne prend pas en charge une fonctionnalité requise par l’application, l’application est simplement refuse d’exécuter avec ce pilote. Toutefois, si la fonctionnalité est facultative, l’application peut contourner la fonctionnalité. Par exemple, il peut désactiver les parties de l’interface qui autorise l’utilisateur à utiliser la fonctionnalité.  
  
 Pour déterminer quelles fonctionnalités sont prises en charge, les applications démarrent en appelant **SQLGetInfo** avec l’option SQL_SQL_CONFORMANCE. Le niveau de conformité SQL donne à l’application une large vue dont SQL est pris en charge. Pour affiner cette vue, l’application appelle **SQLGetInfo** avec un certain nombre d’autres options. Pour obtenir une liste complète de ces options, consultez le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description de fonction. Enfin, **SQLGetTypeInfo** retourne des informations sur les types de données pris en charge par la source de données. Les sections suivantes répertorient un certain nombre de facteurs possibles applications doivent surveiller pour lors de la construction des instructions SQL interopérables.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Utilisation des catalogues et des schémas](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Position du catalogue](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Identificateurs entre guillemets](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Casse des identificateurs](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Séquences d’échappement](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Préfixes et suffixes de littéraux](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Marqueurs de paramètre dans les appels de procédure](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [Instructions DDL](../../../odbc/reference/develop-app/ddl-statements.md)
