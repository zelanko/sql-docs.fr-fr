---
title: Conformité de l’Interface de base | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: e41d71cd3651e1db5d1a533159012b645b8c7764
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63043756"
---
# <a name="core-interface-conformance"></a>Conformité de l’interface principale
Tous les pilotes ODBC doivent présenter au moins au niveau du noyau conformité de l’interface. Les fonctionnalités dans le niveau principal sont celles qui sont requises par les applications interopérables plus génériques, le pilote peut travailler avec ces applications. Les fonctionnalités du niveau Core correspondent également pour les fonctionnalités définies dans la spécification ISO CLI et les fonctionnalités obligatoires définies dans la spécification CLI de groupe ouvert. Un pilote ODBC de conforme à l’interface au niveau du noyau permet à l’application effectuer toutes les conditions suivantes :  
  
-   Allouer et libérer tous les types de handles, en appelant **SQLAllocHandle** et **SQLFreeHandle**.  
  
-   Utiliser toutes les formes de la **SQLFreeStmt** (fonction).  
  
-   Lier des colonnes du jeu de résultats, en appelant **SQLBindCol**.  
  
-   Gérer des paramètres dynamiques, y compris les tableaux de paramètres, dans la direction d’entrée uniquement, en appelant **SQLBindParameter** et **SQLNumParams**. (Les paramètres dans la direction de sortie sont des fonctionnalités 203 dans [au niveau de conformité de l’Interface 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Spécifier un décalage de la liaison.  
  
-   Utilisez la boîte de dialogue data-at-execution, impliquant des appels à **SQLParamData** et **SQLPutData**.  
  
-   Gérer les curseurs et les noms de curseur, en appelant **SQLCloseCursor**, **SQLGetCursorName**, et **SQLSetCursorName**.  
  
-   Accéder à la description (métadonnées) de jeux de résultats, en appelant **SQLColAttribute**, **SQLDescribeCol**, **SQLNumResultCols**, et **SQLRowCount** . (Utilisation de ces fonctions sur la colonne numéro 0 pour récupérer les métadonnées de signet est fonctionnalité 204 dans [au niveau de conformité de l’Interface 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Interroger le dictionnaire de données, en appelant les fonctions de catalogue **SQLColumns**, **SQLGetTypeInfo**, **SQLStatistics**, et **SQLTables**.  
  
     Le pilote n’est pas requis pour prendre en charge des noms en plusieurs parties des tables de base de données et des vues. (Pour plus d’informations, consultez la fonctionnalité de 101 [au niveau de conformité de l’Interface 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md) et fonctionnalité 201 dans [au niveau de conformité de l’Interface 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).) Toutefois, certaines fonctionnalités de la spécification de SQL-92, telles que les noms d’index et de qualification de la colonne sont syntaxiquement comparables d’affectation de noms en plusieurs parties. La présente liste de fonctions ODBC n’est pas destinée à introduire de nouvelles options dans ces aspects de SQL-92.  
  
-   Gérer les sources de données et les connexions, en appelant **SQLConnect**, **SQLDataSources**, **SQLDisconnect**, et **SQLDriverConnect**. Obtenir des informations sur les pilotes, quel que soit le ODBC niveau pris en charge, en appelant **SQLDrivers**.  
  
-   Préparer et exécuter des instructions SQL, en appelant **SQLExecDirect**, **SQLExecute**, et **SQLPrepare**.  
  
-   Extraire une ligne d’un jeu de résultats ou de plusieurs lignes, dans la direction vers l’avant uniquement, en appelant **SQLFetch** ou en appelant **SQLFetchScroll** avec la *FetchOrientation* argument la valeur SQL_FETCH_NEXT.  
  
-   Obtenir une colonne indépendante en parties, en appelant **SQLGetData**.  
  
-   Obtenir les valeurs actuelles de tous les attributs, en appelant **SQLGetConnectAttr**, **SQLGetEnvAttr**, et **SQLGetStmtAttr**et définir les attributs de toutes les valeurs par défaut et définir certains attributs pour les valeurs par défaut en appelant **SQLSetConnectAttr**, **SQLSetEnvAttr**, et **SQLSetStmtAttr**.  
  
-   Manipuler certains champs de descripteurs, en appelant **SQLCopyDesc**, **SQLGetDescField**, **SQLGetDescRec**, **SQLSetDescField**, et **SQLSetDescRec**.  
  
-   Obtenir des informations de diagnostic, en appelant **SQLGetDiagField** et **SQLGetDiagRec**.  
  
-   Détecter les fonctionnalités du pilote, en appelant **SQLGetFunctions** et **SQLGetInfo**. En outre, détecter le résultat de remplacements de n’importe quel texte apportées à une instruction SQL avant leur envoi à la source de données, en appelant **SQLNativeSql**.  
  
-   Utilisez la syntaxe de **SQLEndTran** pour valider une transaction. Un pilote au niveau du noyau devez prend pas en charge les transactions réelles ; Par conséquent, l’application ne peut pas spécifier SQL_ROLLBACK ni SQL_AUTOCOMMIT_OFF pour l’attribut de connexion SQL_ATTR_AUTOCOMMIT. (Pour plus d’informations, consultez la fonctionnalité de 109 [au niveau de conformité de l’Interface 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Appelez **SQLCancel** pour annuler la boîte de dialogue data-at-execution et, dans un environnement multithread, pour annuler un ODBC en cours d’exécution dans un autre thread. Conformité de l’interface d’au niveau du noyau n’impose pas de prise en charge de l’exécution asynchrone de fonctions, ni l’utilisation de **SQLCancel** pour annuler une fonction ODBC exécuter de façon asynchrone. La plateforme, ni le pilote ODBC ne doivent être multithread pour le pilote gérer les activités indépendantes en même temps. Toutefois, dans un environnement multithread, le pilote ODBC doit être thread-safe. Sérialisation de demandes de l’application est conforme permettent d’implémenter cette spécification, même si elle peut créer de graves problèmes de performances.  
  
-   Obtenir la colonne d’identification de ligne SQL_BEST_ROWID des tables, en appelant **SQLSpecialColumns**. (Prise en charge de SQL_ROWVER est fonctionnalité 208 dans [au niveau de conformité de l’Interface 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
    > [!IMPORTANT]  
    >  Pilotes ODBC doit implémenter les fonctions dans le niveau de la conformité de l’interface Core.
