---
title: Exécution directe ODBC ( Microsoft Docs
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
ms.openlocfilehash: bc5d942ac0c2af54168248d8e416ca233b2c69e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305160"
---
# <a name="direct-execution-odbc"></a>Exécution directe dans ODBC
L’exécution directe est le moyen le plus simple d’exécuter une déclaration. Lorsque l’instruction est soumise à l’exécution, la source de données la compile dans un plan d’accès et exécute ensuite ce plan d’accès.  
  
 L’exécution directe est couramment utilisée par les applications génériques qui construisent et exécutent des instructions au moment de l’exécution. Par exemple, le code suivant construit une déclaration SQL et l’exécute une seule fois :  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 L’exécution directe fonctionne mieux pour les déclarations qui seront exécutées une seule fois. Son principal inconvénient est que la déclaration SQL est analysée chaque fois qu’elle est exécutée. En outre, l’application ne peut pas récupérer d’informations sur l’ensemble de résultat créé par la déclaration (le cas échéant) jusqu’à ce que la déclaration soit exécutée; cela est possible si l’instruction est préparée et exécutée en deux étapes distinctes.  
  
 Pour exécuter une déclaration directement, l’application effectue les actions suivantes :  
  
1.  Définit les valeurs de tous les paramètres. Pour plus d’informations, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus tard dans cette section.  
  
2.  Appelle **SQLExecDirect** et lui passe une chaîne contenant la déclaration SQL.  
  
3.  Lorsque **SQLExecDirect** est appelé, le conducteur:  
  
    -   Modifie la déclaration SQL pour utiliser la grammaire SQL de la source de données sans analyser la déclaration; cela comprend le remplacement des séquences d’évacuation discutées dans [Escape Sequences dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). L’application peut récupérer la forme modifiée d’une déclaration SQL en appelant **SQLNativeSql**. Les séquences d’évasion ne sont pas remplacées si l’attribut de l’SQL_ATTR_NOSCAN est défini.  
  
    -   Récupère les valeurs de paramètres actuelles et les convertit au besoin. Pour plus d’informations, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus tard dans cette section.  
  
    -   Envoie l’instruction et converti les valeurs de paramètres à la source de données pour exécution.  
  
    -   Retourne toutes les erreurs. Il s’agit notamment du séquençage ou du diagnostic d’état comme SQLSTATE 24000 (État de curseur invalide), des erreurs syntaxiques telles que SQLSTATE 42000 (erreur syntaxe ou violation d’accès), et des erreurs sémantiques telles que SQLSTATE 42S02 (tableau de base ou vue non trouvée).
