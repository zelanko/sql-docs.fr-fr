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
ms.openlocfilehash: 6f7bf7e77f892f10de17402b59e732523d58fbc6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036550"
---
# <a name="choosing-an-sql-grammar"></a>Choix d’une grammaire SQL
La première décision à prendre lors de la construction d’instructions SQL est la grammaire à utiliser. En plus des grammaires disponibles dans les divers organismes de normalisation, tels que Open Group, ANSI et ISO, presque tous les fournisseurs SGBD définissent leur propre grammaire, chacun d’entre eux variant légèrement de la norme.  
  
 [Annexe C : grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), décrit la grammaire SQL minimale que tous les pilotes ODBC doivent prendre en charge. Cette grammaire est un sous-ensemble du niveau d’entrée de SQL-92. Les pilotes peuvent prendre en charge une grammaire supplémentaire pour se conformer aux niveaux de transition intermédiaire, complet ou FIPS 127-2 définis par SQL-92. Pour plus d’informations, consultez [grammaire minimale SQL](../../../odbc/reference/appendixes/sql-minimum-grammar.md) dans annexe C : grammaire SQL et sql-92.  
  
 L’annexe C définit également des *séquences d’échappement* contenant la grammaire standard pour les fonctionnalités de langage couramment disponibles, telles que les jointures externes, qui ne sont pas couvertes par la syntaxe SQL-92. Pour plus d’informations, consultez [séquences d’échappement ODBC](../../../odbc/reference/appendixes/odbc-escape-sequences.md) dans l’annexe C : grammaire SQL et [séquences d’échappement](../../../odbc/reference/develop-app/escape-sequences.md), plus loin dans cette section.  
  
 La grammaire choisie affecte le mode de traitement de l’instruction par le pilote. Les pilotes doivent modifier SQL-92 SQL et les séquences d’échappement définies par ODBC en SQL spécifique au SGBD. Dans la mesure où la plupart des grammaires SQL sont basées sur une ou plusieurs des normes, la plupart des pilotes n’ont que peu ou pas de travail pour répondre à cette exigence. Elle consiste souvent uniquement à rechercher les séquences d’échappement définies par ODBC et à les remplacer par une grammaire spécifique au SGBD. Lorsqu’un pilote rencontre une grammaire qu’il ne reconnaît pas, il suppose que la grammaire est spécifique au SGBD et transmet l’instruction SQL sans modification à la source de données pour exécution.  
  
 Par conséquent, il existe en fait deux choix de grammaire à utiliser : la grammaire SQL-92 (et les séquences d’échappement ODBC) et une grammaire spécifique au SGBD. Parmi les deux, seule la grammaire SQL-92 est interopérable, de sorte que toutes les applications interopérables doivent l’utiliser. Les applications qui ne sont pas interopérables peuvent utiliser la syntaxe SQL-92 ou une grammaire spécifique au SGBD. Les grammaires spécifiques au SGBD présentent deux avantages : elles peuvent exploiter toutes les fonctionnalités non couvertes par SQL-92, et elles sont plus rapides, car le pilote n’a pas besoin de les modifier. Cette dernière fonctionnalité peut être partiellement appliquée en définissant l’attribut d’instruction SQL_ATTR_NOSCAN, ce qui empêche le pilote de rechercher et de remplacer des séquences d’échappement.  
  
 Si la syntaxe SQL-92 est utilisée, l’application peut découvrir comment elle est modifiée par le pilote en appelant **SQLNativeSql**. Cela est souvent utile lors du débogage d’applications. **SQLNativeSql** accepte une instruction SQL et la retourne une fois que le pilote l’a modifiée. Étant donné que cette fonction se trouve dans le niveau de conformité de l’interface principale, elle est prise en charge par tous les pilotes.
