---
title: Choisir une grammaire SQL Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2ca9911d3c88f2f540ff1332d77a2e1ebc6a4942
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299159"
---
# <a name="choosing-an-sql-grammar"></a>Choix d’une grammaire SQL
La première décision à prendre lors de la construction des déclarations SQL est la grammaire à utiliser. En plus des grammaires disponibles auprès des différents organismes de normalisation, tels que Open Group, ANSI et ISO, pratiquement tous les fournisseurs de DBMS définissent sa propre grammaire, chacune d’entre elles varie légèrement de la norme.  
  
 [Annexe C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), décrit la grammaire SQL minimale que tous les conducteurs ODBC doivent soutenir. Cette grammaire est un sous-ensemble du niveau d’entrée de SQL-92. Les conducteurs peuvent prendre en charge une grammaire supplémentaire pour se conformer aux niveaux transitoires intermédiaires, complets ou FIPS 127-2 définis par SQL-92. Pour plus d’informations, voir [SQL Minimum Grammar](../../../odbc/reference/appendixes/sql-minimum-grammar.md) à l’Annexe C: SQL Grammar, et SQL-92.  
  
 L’annexe C définit également les *séquences d’évacuation* contenant la grammaire standard pour les caractéristiques linguistiques couramment disponibles, telles que les jointures extérieures, qui ne sont pas couvertes par la grammaire SQL-92. Pour plus d’informations, voir [ODBC Escape Sequences](../../../odbc/reference/appendixes/odbc-escape-sequences.md) in Annexe C: SQL Grammar, and [Escape Sequences](../../../odbc/reference/develop-app/escape-sequences.md), plus tard dans cette section.  
  
 La grammaire choisie affecte la façon dont le pilote traite l’instruction. Les conducteurs doivent modifier SQL-92 SQL et les séquences d’évacuation définies par L’ODBC en SQL spécifique à DBMS. Étant donné que la plupart des grammaires SQL sont basées sur une ou plusieurs des différentes normes, la plupart des conducteurs font peu ou pas de travail pour répondre à cette exigence. Il s’agit souvent seulement de rechercher les séquences d’évacuation définies par ODBC et de les remplacer par une grammaire spécifique à DBMS. Lorsqu’un conducteur rencontre une grammaire qu’il ne reconnaît pas, il suppose que la grammaire est spécifique à DBMS et passe la déclaration SQL sans modification à la source de données pour l’exécution.  
  
 Par conséquent, il ya vraiment deux choix de grammaire à utiliser: la grammaire SQL-92 (et les séquences d’évasion ODBC) et une grammaire DBMS spécifique. Des deux, seule la grammaire SQL-92 est interopérable, donc toutes les applications interopérables devraient l’utiliser. Les applications qui ne sont pas interopérables peuvent utiliser la grammaire SQL-92 ou une grammaire spécifique à DBMS. Les grammaires spécifiques à DBMS ont deux avantages : elles peuvent exploiter toutes les caractéristiques non couvertes par SQL-92, et elles sont légèrement plus rapides parce que le conducteur n’a pas à les modifier. Cette dernière fonctionnalité peut être partiellement appliquée en définissant l’attribut de l’SQL_ATTR_NOSCAN, ce qui empêche le conducteur de rechercher et de remplacer les séquences d’évacuation.  
  
 Si la grammaire SQL-92 est utilisée, l’application peut découvrir comment elle est modifiée par le conducteur en appelant **SQLNativeSql**. Ceci est souvent utile lors de la débogage des applications. **SQLNativeSql** accepte une déclaration SQL et le renvoie après que le conducteur l’a modifiée. Parce que cette fonction est dans le niveau de conformité de l’interface Core, elle est prise en charge par tous les pilotes.
