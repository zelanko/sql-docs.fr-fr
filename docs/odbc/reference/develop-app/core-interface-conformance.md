---
title: Conformité de l’interface principale | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- core-level interface conformance levels [ODBC]
ms.assetid: aaaa864a-6477-45ff-a50a-96d8db66a252
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 02e8aabf808ebf11f2e241fc7d330f794dbb0112
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002110"
---
# <a name="core-interface-conformance"></a>Conformité de l’interface principale
Tous les pilotes ODBC doivent présenter la conformité de l’interface au niveau du noyau. Étant donné que les fonctionnalités du niveau principal sont celles requises par la plupart des applications interopérables génériques, le pilote peut fonctionner avec ces applications. Les fonctionnalités du niveau principal correspondent également aux fonctionnalités définies dans la spécification de l’interface CLI ISO et aux fonctionnalités non facultatives définies dans la spécification de l’interface CLI de groupe ouverte. Un pilote ODBC conforme à l’interface de niveau principal permet à l’application d’effectuer toutes les opérations suivantes :  
  
-   Allouez et libérez tous les types de handles en appelant **SQLAllocHandle** et **SQLFreeHandle**.  
  
-   Utilisez toutes les formes de la fonction **SQLFreeStmt** .  
  
-   Liez les colonnes du jeu de résultats en appelant **SQLBindCol**.  
  
-   Gérez les paramètres dynamiques, y compris les tableaux de paramètres, dans la direction d’entrée uniquement, en appelant **SQLBindParameter** et **SQLNumParams**. (Les paramètres dans le sens de sortie sont les fonctionnalités 203 dans la conformité de l' [interface de niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Spécifiez un décalage de liaison.  
  
-   Utilisez la boîte de dialogue données en cours d’exécution, qui implique des appels à **SQLParamData** et **SQLPutData**.  
  
-   Gérez les curseurs et les noms de curseurs en appelant **SQLCloseCursor**, **SQLGetCursorName**et **SQLSetCursorName**.  
  
-   Accédez à la description (métadonnées) des jeux de résultats en appelant **SQLColAttribute**, **SQLDescribeCol**, **SQLNumResultCols**et **SQLRowCount**. (L’utilisation de ces fonctions sur le numéro de colonne 0 pour récupérer les métadonnées de signet est la fonctionnalité 204 dans la conformité de l' [interface de niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Interrogez le dictionnaire de données en appelant les fonctions de catalogue **SQLColumns**, **SQLGetTypeInfo**, **SQLStatistics**et **SQLTables**.  
  
     Le pilote n’est pas requis pour prendre en charge les noms en plusieurs parties des tables et des vues de base de données. (Pour plus d’informations, consultez la fonctionnalité 101 dans la conformité de l' [interface de niveau 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md) et la fonctionnalité 201 dans la conformité de l' [interface de niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).) Toutefois, certaines fonctionnalités de la spécification SQL-92, telles que la qualification de colonne et les noms d’index, sont syntaxiquement comparables à l’affectation de noms en plusieurs parties. La liste actuelle des fonctionnalités ODBC n’est pas destinée à introduire de nouvelles options dans ces aspects de SQL-92.  
  
-   Gérer les sources de données et les connexions, en appelant **SQLConnect**, **SQLDataSources**, **SQLDisconnect**et **SQLDriverConnect**. Obtenir des informations sur les pilotes, quel que soit le niveau ODBC pris en charge, en appelant **SQLDrivers**.  
  
-   Préparez et exécutez des instructions SQL en appelant **SQLExecDirect**, **SQLExecute**et **SQLPrepare**.  
  
-   Extraire une ligne d’un jeu de résultats ou plusieurs lignes, dans la direction avant uniquement, en appelant **SQLFetch** ou en appelant **SQLFetchScroll** avec l’argument *FetchOrientation* défini sur SQL_FETCH_NEXT.  
  
-   Obtenez une colonne indépendante en parties, en appelant **SQLGetData**.  
  
-   Obtenez les valeurs actuelles de tous les attributs, en appelant **SQLGetConnectAttr**, **SQLGetEnvAttr**et **SQLGetStmtAttr**, puis affectez à tous les attributs leurs valeurs par défaut et affectez à certains attributs des valeurs différentes de celles par défaut en appelant **SQLSetConnectAttr**, **SQLSetEnvAttr**et **SQLSetStmtAttr**.  
  
-   Manipuler certains champs de descripteurs, en appelant **SQLCopyDesc**, **SQLGetDescField**, **SQLGetDescRec**, **SQLSetDescField**et **SQLSetDescRec**.  
  
-   Obtenez des informations de diagnostic en appelant **SQLGetDiagField** et **SQLGetDiagRec**.  
  
-   Détectez les fonctionnalités des pilotes en appelant **SQLGetFunctions** et **SQLGetInfo**. En outre, détectez le résultat de toutes les substitutions de texte effectuées dans une instruction SQL avant qu’elle ne soit envoyée à la source de données, en appelant **SQLNativeSql**.  
  
-   Utilisez la syntaxe de **SQLEndTran** pour valider une transaction. Un pilote de niveau principal n’A pas besoin de prendre en charge les véritables transactions ; par conséquent, l’application ne peut pas spécifier SQL_ROLLBACK ni SQL_AUTOCOMMIT_OFF pour l’attribut de connexion SQL_ATTR_AUTOCOMMIT. (Pour plus d’informations, consultez la fonctionnalité 109 dans la conformité de l' [interface de niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Appelez **SQLCancel** pour annuler la boîte de dialogue de données en cours d’exécution et, dans les environnements multithread, pour annuler une fonction ODBC s’exécutant dans un autre thread. La conformité de l’interface au niveau du noyau n’autorise pas la prise en charge de l’exécution asynchrone des fonctions, ni l’utilisation de **SQLCancel** pour annuler une fonction ODBC s’exécutant de manière asynchrone. Ni la plateforme, ni le pilote ODBC n’ont besoin d’être multithread pour que le pilote exécute des activités indépendantes en même temps. Toutefois, dans les environnements multithread, le pilote ODBC doit être thread-safe. La sérialisation des requêtes à partir de l’application est une méthode conforme pour implémenter cette spécification, même si elle peut créer de sérieux problèmes de performances.  
  
-   Obtenez le SQL_BEST_ROWID colonne d’identification de lignes des tables en appelant **SQLSpecialColumns**. (La prise en charge de SQL_ROWVER est la fonctionnalité 208 dans la conformité de l' [interface de niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
    > [!IMPORTANT]  
    >  Les pilotes ODBC doivent implémenter les fonctions dans le niveau de conformité de l’interface principale.
