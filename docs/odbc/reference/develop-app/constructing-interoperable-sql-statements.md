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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1eccdef63b7d06a456a07f5f1a9ccad987d2de29
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282513"
---
# <a name="constructing-interoperable-sql-statements"></a>Construction d’instructions SQL interopérables
Comme mentionné dans les sections précédentes, les applications interopérables doivent utiliser la syntaxe ODBC SQL. Toutefois, au-delà de cette grammaire, un certain nombre de problèmes supplémentaires sont rencontrés par les applications interopérables. Par exemple, que fait une application si elle souhaite utiliser une fonctionnalité, telle que les jointures externes, qui n’est pas prise en charge par toutes les sources de données ?  
  
 À ce stade, l’auteur de l’application doit prendre des décisions concernant les fonctionnalités de langage requises et celles qui sont facultatives. Dans la plupart des cas, si un pilote particulier ne prend pas en charge une fonctionnalité requise par l’application, l’application refuse simplement de s’exécuter avec ce pilote. Toutefois, si la fonctionnalité est facultative, l’application peut contourner la fonctionnalité. Par exemple, il peut désactiver les parties de l’interface qui permettent à l’utilisateur d’utiliser la fonctionnalité.  
  
 Pour déterminer les fonctionnalités prises en charge, les applications commencent en appelant **SQLGetInfo** avec l’option SQL_SQL_CONFORMANCE. Le niveau de conformité de SQL donne à l’application une vue d’ensemble des capacités de SQL prises en charge. Pour affiner cette vue, l’application appelle **SQLGetInfo** avec l’une des nombreuses autres options. Pour obtenir la liste complète de ces options, consultez la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) . Enfin, **SQLGetTypeInfo** retourne des informations sur les types de données pris en charge par la source de données. Les sections suivantes répertorient un certain nombre de facteurs pouvant être surveillés par les applications lors de la construction d’instructions SQL interopérables.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Utilisation des catalogues et des schémas](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Position du catalogue](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Identificateurs entre guillemets](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Casse des identificateurs](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Séquences d’échappement](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Préfixes et suffixes de littéraux](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Marqueurs de paramètre dans les appels de procédure](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [Instructions DDL](../../../odbc/reference/develop-app/ddl-statements.md)
