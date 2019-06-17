---
title: Choix d’une grammaire SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], SQL grammar
- SQL grammar [ODBC], selecting
ms.assetid: 4e0d189b-e407-47e0-92a9-f9982230dd0e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 670ed0adbbd5ad993af0942d492ee19f75fa9628
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026583"
---
# <a name="choosing-an-sql-grammar"></a>Choix d’une grammaire SQL
La première décision à prendre lors de la construction d’instructions SQL est quels grammaire à utiliser. Outre les grammaires disponibles à partir de divers organismes de normalisation, tels que Open Group, ANSI et ISO, pratiquement tous les fournisseurs SGBD définit sa propre syntaxe, chacun d’eux varie légèrement par rapport à la norme.  
  
 [Annexe C : Grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), décrit la grammaire SQL minimale que tous les pilotes ODBC doivent prendre en charge. Cette syntaxe est un sous-ensemble du niveau d’entrée de SQL-92. Pilotes peuvent prendre en charge la grammaire supplémentaire pour le rendre conforme à intermédiaire, complète ou FIPS 127-2 des niveaux transitoires définis par SQL-92. Pour plus d’informations, consultez [SQL Minimum grammaire](../../../odbc/reference/appendixes/sql-minimum-grammar.md) dans l’annexe c : Grammaire SQL et SQL-92.  
  
 Annexe C définit également *séquences d’échappement* contenant une syntaxe standard pour les fonctionnalités de langage généralement disponibles, telles que les jointures externes, qui non couverts par la grammaire SQL-92. Pour plus d’informations, consultez [les séquences d’échappement ODBC](../../../odbc/reference/appendixes/odbc-escape-sequences.md) dans l’annexe c : Grammaire SQL, et [séquences d’échappement](../../../odbc/reference/develop-app/escape-sequences.md), plus loin dans cette section.  
  
 La grammaire est choisie affecte la façon dont le pilote traite l’instruction. Pilotes doivent modifier SQL-92 SQL et les séquences d’échappement de définie par ODBC à SQL de SGBD spécifiques. Étant donné que la plupart des grammaires SQL reposent sur un ou plusieurs des normes différentes, la plupart des pilotes travailler peu ou pas pour répondre à cette exigence. Il se compose souvent uniquement de la recherche pour les séquences d’échappement définies par ODBC et en les remplaçant par la grammaire de SGBD spécifiques. Lorsqu’un pilote rencontre grammaire que ne reconnaît pas, il suppose que la grammaire est spécifique au SGBD et transmet l’instruction SQL sans modification à la source de données pour l’exécution.  
  
 Par conséquent, il existe en fait deux possibilités de grammaire à utiliser : la grammaire SQL-92 (et les séquences d’échappement ODBC) et une syntaxe propres au SGBD. Les deux, uniquement la grammaire SQL-92 est interopérable, afin que toutes les applications interopérables doivent l’utiliser. Les applications qui ne sont pas interopérables peuvent utiliser la syntaxe SQL-92 ou une grammaire de SGBD spécifiques. Grammaires de SGBD spécifiques ont deux avantages : Ils peuvent exploiter les fonctionnalités non couvertes par SQL-92, et elles sont légèrement plus rapides, car le pilote n’a pas de les modifier. La fonctionnalité de ce dernier peut être appliquée partiellement en définissant l’attribut d’instruction SQL_ATTR_NOSCAN, ce qui arrête le pilote à partir de la recherche et remplacement de séquences d’échappement.  
  
 Si la grammaire SQL-92 est utilisée, l’application peut découvrir la façon dont il est modifié par le pilote en appelant **SQLNativeSql**. Cela est souvent utile lors du débogage d’applications. **SQLNativeSql** accepte une instruction SQL et le retourne une fois que le pilote l’a modifié. Cette fonction se trouve dans le niveau de la conformité de l’interface de Core, il est pris en charge par tous les pilotes.
