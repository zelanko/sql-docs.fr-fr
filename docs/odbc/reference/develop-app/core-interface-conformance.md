---
title: Conformité à l’interface de base (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 886ded1cd79b35488c0d47df3dbd8055dc6a8016
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302131"
---
# <a name="core-interface-conformance"></a>Conformité de l’interface principale
Tous les pilotes ODBC doivent présenter au moins la conformité à l’interface au niveau du noyau. Étant donné que les caractéristiques du niveau Core sont celles requises par la plupart des applications interopérables génériques, le conducteur peut travailler avec de telles applications. Les caractéristiques du niveau Core correspondent également aux caractéristiques définies dans la spécification ISO CLI et aux caractéristiques nonoptionnelles définies dans la spécification CLI Open Group. Un pilote ODBC conforme à l’interface au niveau central permet à l’application de faire tout ce qui suit :  
  
-   Allouer et libérer tous les types de poignées, en appelant **SQLAllocHandle** et **SQLFreeHandle**.  
  
-   Utilisez toutes les formes de la fonction **SQLFreeStmt.**  
  
-   Bind résultats définir colonnes, en appelant **SQLBindCol**.  
  
-   Gérer les paramètres dynamiques, y compris les gammes de paramètres, dans la direction de l’entrée seulement, en appelant **SQLBindParameter** et **SQLNumParams**. (Les paramètres dans la direction de sortie sont fonction 203 dans [le niveau 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Spécifier un décalage de liaison.  
  
-   Utilisez le dialogue de données à l’exécution, impliquant des appels à **SQLParamData** et **SQLPutData**.  
  
-   Gérer les curseurs et les noms de curseur, en appelant **SQLCloseCursor**, **SQLGetCursorName**, et **SQLSetCursorName**.  
  
-   Accédez à la description (métadonnées) des ensembles de résultats, en appelant **SQLColAttribute**, **SQLDescribeCol**, **SQLNumResultCols**, et **SQLRowCount**. (L’utilisation de ces fonctions sur la colonne numéro 0 pour récupérer les métadonnées signets est fonction 204 dans [le niveau 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Requête le dictionnaire de données, en appelant les fonctions catalogue **SQLColumns**, **SQLGetTypeInfo**, **SQLStatistics**, et **SQLTables**.  
  
     Le conducteur n’est pas tenu de prendre en charge les noms multipartites des tables et des vues de base de données. (Pour plus d’informations, voir la fonctionnalité 101 dans [le niveau 1 Interface Conformance](../../../odbc/reference/develop-app/level-1-interface-conformance.md) et fonctionnalité 201 dans [le niveau 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).) Cependant, certaines caractéristiques des spécifications SQL-92, telles que la qualification de colonne et les noms des index, sont syntaxiquement comparables à la dénomination multipartite. La liste actuelle des caractéristiques de l’ODBC n’a pas pour but d’introduire de nouvelles options dans ces aspects de SQL-92.  
  
-   Gérer les sources de données et les connexions, en appelant **SQLConnect**, **SQLDataSources**, **SQLDisconnect**, et **SQLDriverConnect**. Obtenir de l’information sur les conducteurs, quel que soit le niveau ODBC qu’ils soutiennent, en appelant **SQLDrivers**.  
  
-   Préparer et exécuter les déclarations SQL, en appelant **SQLExecDirect**, **SQLExecute**, et **SQLPrepare**.  
  
-   Aller chercher une rangée d’un ensemble de résultats ou plusieurs lignes, dans la direction avant seulement, en appelant **SQLFetch** ou en appelant **SQLFetchScroll** avec *l’argument FetchOrientation* mis à SQL_FETCH_NEXT.  
  
-   Obtenir une colonne non liée dans les pièces, en appelant **SQLGetData**.  
  
-   Obtenez les valeurs actuelles de tous les attributs, en appelant **SQLGetConnectAttr**, **SQLGetEnvAttr**, et **SQLGetStmtAttr**, et définir tous les attributs à leurs valeurs par défaut et définir certains attributs à des valeurs non-default en appelant **SQLSetConnectAttr**, **SQLSetEnvAttr**, et **SQLSetStmtAttr**.  
  
-   Manipulez certains champs de descripteurs, en appelant **SQLCopyDesc**, **SQLGetDescField**, **SQLGetDescRec**, **SQLSetDescField**, et **SQLSetDescRec**.  
  
-   Obtenir des informations diagnostiques, en appelant **SQLGetDiagField** et **SQLGetDiagRec**.  
  
-   Détecter les capacités du conducteur, en appelant **SQLGetFunctions** et **SQLGetInfo**. En outre, détecter le résultat de toute substitution de texte faite à une déclaration SQL avant qu’il ne soit envoyé à la source de données, en appelant **SQLNativeSql**.  
  
-   Utilisez la syntaxe de **SQLEndTran** pour commettre une transaction. Un conducteur de base n’a pas besoin de soutenir de véritables transactions; par conséquent, l’application ne peut pas spécifier SQL_ROLLBACK ni SQL_AUTOCOMMIT_OFF pour l’attribut de connexion SQL_ATTR_AUTOCOMMIT. (Pour plus d’informations, voir la fonctionnalité 109 dans [le niveau 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Appelez **SQLCancel** pour annuler le dialogue de données à l’exécution et, dans des environnements multitâlis, pour annuler une fonction ODBC exécutant dans un autre thread. La conformation de l’interface de base n’exige pas le soutien à l’exécution asynchrone des fonctions, ni l’utilisation de **SQLCancel** pour annuler une fonction ODBC exécutant asynchronement. Ni la plate-forme ni le conducteur de l’ODBC n’ont besoin d’être multithli pour que le conducteur puisse mener des activités indépendantes en même temps. Cependant, dans les environnements multitâliaux, le pilote ODBC doit être sans fil. La sérialisation des demandes de l’application est un moyen conforme de mettre en œuvre cette spécification, même si elle peut créer de graves problèmes de performances.  
  
-   Obtenez la colonne SQL_BEST_ROWID d’identification des rangées de tables, en appelant **SQLSpecialColumns**. (Support for SQL_ROWVER est fonction 208 dans [le niveau 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
    > [!IMPORTANT]  
    >  ODBC Drivers doit implémenter les fonctions dans le niveau de conformité de l’interface Core.
