---
title: Exécution directe dans ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73c061718dc326e43f72be369a28ad12726a3cab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242355"
---
# <a name="direct-execution-odbc"></a>Exécution directe dans ODBC
L’exécution directe est la façon la plus simple d’exécuter une instruction. Lorsque l’instruction est envoyée pour exécution, la source de données compile dans un plan d’accès, puis exécute ce plan d’accès.  
  
 L’exécution directe est couramment utilisée par les applications génériques qui créent et exécutent des instructions au moment de l’exécution. Par exemple, le code suivant génère une instruction SQL et l’exécute une seule fois :  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 L’exécution directe convient le mieux pour les instructions qui seront exécutées une seule fois. Son inconvénient majeur est que l’instruction SQL est analysée chaque fois qu’elle est exécutée. En outre, l’application ne peut pas récupérer des informations sur le jeu de résultats créé par l’instruction (le cas échéant) jusqu'à ce qu’après que l’instruction est exécutée ; Cela est possible si l’instruction est préparée et exécutée en deux étapes distinctes.  
  
 Pour exécuter une instruction directement, l’application effectue les actions suivantes :  
  
1.  Définit les valeurs des paramètres. Pour plus d’informations, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
2.  Appels **SQLExecDirect** et lui passe une chaîne contenant l’instruction SQL.  
  
3.  Lorsque **SQLExecDirect** est appelée, le pilote :  
  
    -   Modifie l’instruction SQL pour utiliser la grammaire SQL de la source de données sans l’analyse de l’instruction ; Cela inclut en remplaçant les séquences d’échappement abordées dans [les séquences d’échappement dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). L’application peut extraire la forme d’une instruction SQL modifiée en appelant **SQLNativeSql**. Séquences d’échappement ne sont pas remplacés si la valeur de l’attribut d’instruction SQL_ATTR_NOSCAN.  
  
    -   Récupère les valeurs de paramètre en cours et les convertit en fonction des besoins. Pour plus d’informations, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
    -   Envoie l’instruction et les valeurs de paramètre converti à la source de données pour l’exécution.  
  
    -   Retourne toutes les erreurs. Ceux-ci incluent le séquencement ou diagnostics d’état telles que SQLSTATE 24000 (état de curseur non valide), des erreurs syntaxiques comme SQLSTATE 42000 (syntaxe ou violation d’accès) et les erreurs sémantiques telles que 42 s 02 SQLSTATE (Base table ou vue introuvable).
