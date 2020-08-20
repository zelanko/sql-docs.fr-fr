---
description: Exécution directe dans ODBC
title: ODBC d’exécution directe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], direct execution
- direct execution [ODBC]
- SQL statements [ODBC], executing
ms.assetid: dd00a535-b136-494f-913b-410838e3de7e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9be03c4f20a82e134481f8fd9bb849ffd830567a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476701"
---
# <a name="direct-execution-odbc"></a>Exécution directe dans ODBC
L’exécution directe est la manière la plus simple d’exécuter une instruction. Lorsque l’instruction est soumise pour exécution, la source de données la compile dans un plan d’accès, puis exécute ce plan d’accès.  
  
 L’exécution directe est couramment utilisée par les applications génériques qui génèrent et exécutent des instructions au moment de l’exécution. Par exemple, le code suivant génère une instruction SQL et l’exécute une seule fois :  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 L’exécution directe fonctionne mieux pour les instructions qui seront exécutées une seule fois. Son inconvénient majeur est que l’instruction SQL est analysée chaque fois qu’elle est exécutée. En outre, l’application ne peut pas récupérer les informations sur le jeu de résultats créé par l’instruction (le cas échéant) tant que l’instruction n’a pas été exécutée ; Cela est possible si l’instruction est préparée et exécutée en deux étapes distinctes.  
  
 Pour exécuter directement une instruction, l’application effectue les actions suivantes :  
  
1.  Définit les valeurs de tous les paramètres. Pour plus d’informations, consultez [paramètres des instructions](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
2.  Appelle **SQLExecDirect** et lui transmet une chaîne contenant l’instruction SQL.  
  
3.  Lorsque **SQLExecDirect** est appelé, le pilote :  
  
    -   Modifie l’instruction SQL pour utiliser la grammaire SQL de la source de données sans analyser l’instruction. Cela comprend le remplacement des séquences d’échappement présentées dans [séquences d’échappement dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). L’application peut récupérer la forme modifiée d’une instruction SQL en appelant **SQLNativeSql**. Les séquences d’échappement ne sont pas remplacées si l’attribut d’instruction SQL_ATTR_NOSCAN est défini.  
  
    -   Récupère les valeurs de paramètres actuelles et les convertit si nécessaire. Pour plus d’informations, consultez [paramètres des instructions](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
    -   Envoie l’instruction et les valeurs de paramètre converties à la source de données pour l’exécution.  
  
    -   Retourne les erreurs éventuelles. Celles-ci incluent le séquencement ou les diagnostics d’État tels que SQLSTATE 24000 (état de curseur non valide), les erreurs syntaxiques telles que SQLSTATE 42000 (erreur de syntaxe ou violation d’accès) et les erreurs sémantiques telles que SQLSTATE 42S02 (table ou vue de base introuvable).
